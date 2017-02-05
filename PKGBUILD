# Maintainer: Franklyn Tackitt <franklyn@tackitt.net>

# Editing these should update the package
_postgres_ver=9.6
_v8_ver=3.14

pkgname=plv8-bin
pkgver=1.4.8
pkgrel=1
pkgdesc="plv8js is a procedural language add-on for PostgreSQL"
url="https://code.google.com/p/plv8js/"
arch=('i686' 'x86_64')
license=('BSD new')
depends=("postgresql>=${_postgres_ver}"
         "v8-${_v8_ver}")
makedepends=('git')
conflicts=('plv8js-git' 'plv8-9.4-bin')
provides=('plv8')

source_i686=("http://apt.postgresql.org/pub/repos/apt/pool/main/p/plv8/postgresql-${_postgres_ver}-plv8_${pkgver}.ds-1.pgdg16.04+1_i386.deb")
source_x86_64=("http://apt.postgresql.org/pub/repos/apt/pool/main/p/plv8/postgresql-${_postgres_ver}-plv8_${pkgver}.ds-2.pgdg16.04+1_amd64.deb")
md5sums_i686=('f96af74bf76a9f5c4e27f54a330b0c0a')
md5sums_x86_64=('55cf968759015d2c4fdfe37eab6fc387')

package() {
  msg2 "Unpacking data.tar.xz (Ubuntu package files)"
  tar -xf data.tar.xz

  install -Dm644 ${srcdir}/usr/lib/postgresql/${_postgres_ver}/lib/plv8.so ${pkgdir}/usr/lib/postgresql/plv8.so
  install -Dm644 ${srcdir}/usr/share/postgresql/${_postgres_ver}/extension/plv8--${pkgver}.sql ${pkgdir}/usr/share/postgresql/extension/plv8--${pkgver}.sql
  install -Dm644 ${srcdir}/usr/share/postgresql/${_postgres_ver}/extension/plv8.control ${pkgdir}/usr/share/postgresql/extension/plv8.control
  install -dDm644 ${srcdir}/usr/share/doc/postgresql-${_postgres_ver}-plv8/ ${pkgdir}/usr/share/doc/postgresql-plv8/

  msg2 "Fixing permissions differences between Ubuntu and Arch"
  find ${pkgdir} -type d -exec chmod -cR 755 "{}" \;
  find ${pkgdir}/usr/{lib,share} -type f -exec chmod -cR 644 "{}" \;
}
