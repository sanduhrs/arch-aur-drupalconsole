# Maintainer: Stefan Auditor <stefan.auditor@erdfisch.de>

_pkgname=drupalconsole
pkgname=${_pkgname}
pkgver=0.10.5
pkgrel=1
pkgdesc="The Drupal Console is a suite of tools that you run on a command line interface (CLI) to generate boilerplate code and interact with a Drupal 8 installation."
arch=('any')
url="http://drupalconsole.com/"
license=('GPL')
depends=('php')
makedepends=("php-box" "php-composer" "git")
install=("${_pkgname}.install")
source=("${_pkgname}-${pkgver}"::"git+https://github.com/hechoendrupal/DrupalConsole.git")
sha512sums=('SKIP')

pkgver() {
  cd "${_pkgname}-${pkgver}"
  git describe --abbrev=0 --tags
}

build() {
  cd "${srcdir}/${_pkgname}-${pkgver}"
  ulimit -n 3072
  php /usr/bin/composer install --no-dev
  php -d phar.readonly=Off /usr/bin/php-box build
}

package() {
  cd "${srcdir}/${_pkgname}-${pkgver}"
  install -D -m755 "drupal.phar" "${pkgdir}/usr/bin/drupal"
}
