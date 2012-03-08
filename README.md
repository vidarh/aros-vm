
# Building a Debian based AROS / AmigaOS cross development system #

**This script is in very early stages. Be aware that if I get
anything wrong in any commit, such as missing out "chroot" 
commands, this is VERY likely to mess up your machine**

Tools to build an AROS rootfs suitable for chroot and/or an OpenVz VM suitable
to do AROS development.

## Usage ##

### Building the cached root filesystem ###

    ./buildroot

This will create:

  1. A basic Debian root in /var/cache/aros-vm/rootfs; this is used as a cache so you don't have to re-download all the packages all the time.
  2. A somewhat more AROS specific root in /var/cache/aros-vm/aros; this is also a cache, but contains packages specific to this setup, drawn from packages.txt in this repository as well as other VM-type independent changes.

This should be sufficient if you want an environment to chroot into. You can "cp -Rap /var/cache/aros-vm/aros my-destination" to create a "my-destination" directory that's a pristine Debian environment to work in, and blow it away when you're done.

**THE DOCUMENTATION BELOW OUTLINE PLANS. THIS SCRIPT HAS NOT YET BEEN ADDED**

 * A script to assist with configuring, building, compile, update and start AROS hosted will be put in /home/aros/bin/aros. 
 * /home/aros/bin will be in the path of the "aros" user so the "aros" command can be used directly if you run as this user. Run "/home/aros/bin/aros help" for usage.
 * A separate directory /home/aros/build will be created as the intended target for builds
 * a symlink will be created from /home/aros/build/bin/linux-i386/AROS to /home/aros/aros, to refer to the root of the compiled AROS subsystem.
 * The AROS SVN checkout will be in /home/aros/svn. 


## Caching SVN ##

**THE DOCUMENTATION BELOW OUTLINE PLANS. THIS SCRIPT HAS NOT YET BEEN ADDED**

   ./cachearossvn [username]

This creates a third cached image, if none already exist, and then proceeds to chroot and run the /home/aros/bin/aros command to do a svn checkout from the AROS repository. This so you can build your VM images with a clean AROS svn checkout already configured so you don't have to download all of it for every new VM.

It will prompt you for your SVN password. This password *may be cached in the template*.


### Creating an OpenVZ template ##

**THE DOCUMENTATION BELOW OUTLINE PLANS. THIS SCRIPT HAS NOT YET BEEN ADDED**

This creates an OpenVZ template that you can use to subsequently create OpenVZ containers with. The upside is it
gives you full flexibility to have a self-contained AROS environment (or multiple) complete with a configured
VNC setup, UAE pretty much ready to go (apart from AmigaOS ROMs)

