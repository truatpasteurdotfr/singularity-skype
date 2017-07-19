#!/bin/bash
#
# Tru Huynh <tru@pasteur.fr>

BootStrap: debootstrap
OSVersion: stretch
MirrorURL: http://ftp.us.debian.org/debian/
Include: wget curl libcanberra-gtk-module packagekit-gtk3-module ca-certificates gnupg

%runscript
echo "Starting skype in the container"
/usr/bin/skypeforlinux "$@"

%post
curl https://repo.skype.com/data/SKYPE-GPG-KEY | apt-key add -

wget https://repo.skype.com/latest/skypeforlinux-64.deb && \
  dpkg -i skypeforlinux-64.deb && /bin/rm skypeforlinux-64.deb
apt-get update

# install missing requirements if any
apt-get -y install -f
# update all packages
apt-get -y upgrade

%labels
MAINTAINER truatpasteurdotfr
