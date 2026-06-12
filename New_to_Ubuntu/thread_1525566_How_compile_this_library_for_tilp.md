---
title: "How compile this library for tilp"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by nene7 on 2010-07-06
hi i need to install a tiusb library i download from ticalc page but i dont understand well what i have to do. i have install ubuntu 10.04 lts in dell mini10
> Release notes for tiglusb
=========================

What's new ?
------------

This driver support the DevFS (Device File System) capability which was
introduced in 2.4 kernels but superseded by udev starting at 2.6.18.
This module has an official device number.


Summary
-------

This driver allows you to use a TI-GRAPH LINK USB (aka SilverLink) cable 
under Linux as well as DirectLink (TI84+/USB & Titanium/USB).
 
To compile the module, you will need USB support. Either compiled in 
your kernel, either as a module.
This driver supports the new device hierarchy (devfs) so you may activate it 
in your kernel (currently experimental).

The module has been tested with UHCI and OHCI motherboard hubs.

The latest tiglusb version is available here:
    [http://lpg.ticalc.org/prj_usb/](http://lpg.ticalc.org/prj_usb/)


Before compiling tiglusb
------------------------

You should know where the kernel headers are located as well as your kernel
version. If you have a 'vanilia' kernel, the path is '/usr/src/linux'.
It may change with some other distributions or packaged kernels.

So, you may have to edit the Makefile for the right location. There are only
1 variables to edit: KDIR := /usr/src/linux for instance. That's all !

So that installation work properly, you must be running the kernel for which
you attempt the installation. Else, you will have to manually copy tiglusb.ko.


Compile tiglusb
---------------

You need configured kernel sources to compile the tiglusb driver.  
The driver uses some Makefile magic to compile the modules with your kernel's 
configuration (wrt. module-versions, SMP, ...).  If you already have compiled 
the kernel at least once, you probably don't have do worry about this.  If
not, go to /usr/src/linux and run at least "make (x)config".  Even
better, compile your own kernel, you'll never become a real hacker
else ;-)

Note that you have to turn on USB support (CONFIG_USB=y or m).
You may also turn on devfs support (CONFIG_DEVFS_FS).
For compiling tiglusb.o, simply type 'make clean' and next 'make'.


Installing tiglusb
------------------

Once compiled, you need to install the module: type "make clean; make; make 
install" for this. 
This will copy the module (tiglusb.o) to the correct modules directory, 
and will creates the special device files in /dev as well as links for
insuring compatibility with 'tidev' nodes. 

You may then load the module by typing the command "insmod tiser.o"
as root or by typing 'make load'.
You may have to adjust permissions on character devices...

Nodes are assigned as follow (independantly of their hardware address):
/dev/tiusb0              first link cable
/dev/tiusb1              second link cable
...            up to 16 link cables !

If you have enabled the automount support, the module can be automagically
loaded by the kernel whenever a program try to use it. For this, simply
add the following line in your /etc/modules.conf or /etc/modutils/arch/i386
(depending on your Linux distribution):

        alias char-major-61             tipar
        alias char-major-62             tiser
    alias char-major-180-225    tiglusb

Until I fix it, you will have to recreate the nodes in /dev/ whenever you
restart your machine. Simply do a 'make devices'.
If you have enabled devfs, you don't have to worry about this.


Options
-------

See module/Insmod-options


Limitations
-----------

You can not load simultaneously more than 1 module between tipar/tiser/tiglusb.
You can write more than 32 bytes at a time!

--
Romain Lievin, 2001-2004, <roms@tilp.info>
Julien Blache, 2001-2002, <jb@jblache.org>




---

