# Udoo xbmc BSP
(based on freescale's community yocto bsp)

This BSP use freescale's one and add support for udoo board and xbmc 
It's forked from the work of Wolfgar (https://github.com/wolfgar) and Rehsack (https://github.com/rehsack)

To get the BSP you need to have `repo` installed and use it as:

Install the `repo` utility:

``` 
mkdir ~/bin
curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
``` 

Download the BSP source:

``` 
PATH=${PATH}:~/bin
mkdir udoo-xbmc-bsp
cd udoo-xbmc-bsp
repo init -u https://github.com/tidalf/udoo-xbmc-bsp -b dizzy
repo sync
``` 

Once this has complete, you will have all you need. To start a build, do:
we remove the original bblayers.conf so the one in meta-tid/conf is used

``` 
rm sources/base/conf/bblayers.conf                 
TEMPLATECONF=`pwd`/sources/meta-tid/conf MACHINE=udoo-quad source setup-environment build
bitbake xbmc-image-nodev-nodaemon # nothing but xbmc
bitbake xbmc-image-nodev # with p2p services 
bitbake xbmc-image-full # with services and devtools
``` 

You can use any directory to host your build.

The source code will be checked out at fsl-community-bsp/sources.

# Contributing

Contributions are welcome (use github fork and PR)
