---
title: "Cannot run or find app that I installed"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by JerryI on 2009-03-14
Last night I tried to install my first app under Hardy, VMWare Server.  Following is an excerpt from my install log.  My problem is that I now have no idea how to make the program run.  Someone said to type f2 vmware.  Someone else said click Applications System.  There is no System folder in Applications.  Is there more to do before I really have the application installed?  F2 does not show it as a known application.

------------------------------------------------------------------
Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.27-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config0/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config0/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config0/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config0/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config0/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config0/vmnet-only/smac.o
  CC [M]  /tmp/vmware-config0/vmnet-only/vnetEvent.o
  CC [M]  /tmp/vmware-config0/vmnet-only/vnetUserListener.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The vmnet module loads perfectly into the running kernel.

Please specify a port for remote connections to use [902] 

Please specify a port for standard http connections to use [8222] 

Please specify a port for secure http (https) connections to use [8333] 

The current administrative user for VMware Server  is ''.  Would you like to 
specify a different administrator? [no] 

Using root as the VMware Server administrator.

In which directory do you want to keep your virtual machine files? 
[/var/lib/vmware/Virtual Machines] 

The path "/var/lib/vmware/Virtual Machines" does not exist currently. This 
program is going to create it, including needed parent directories. Is this 
what you want? [yes] 

Please enter your 20-character serial number.

Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  entered code here

Creating a new VMware VIX API installer database using the tar4 format.

Installing VMware VIX API.

In which directory do you want to install the VMware VIX API binary files? 
[/usr/bin] 

In which directory do you want to install the VMware VIX API library files? 
[/usr/lib/vmware-vix/lib] 

The path "/usr/lib/vmware-vix/lib" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

In which directory do you want to install the VMware VIX API document pages? 
[/usr/share/doc/vmware-vix] 

The path "/usr/share/doc/vmware-vix" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

The installation of VMware VIX API 1.6.0 build-122956 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-vix.pl".

Enjoy,
cd ~

--the VMware team
---------------------------------------------------------------
I

---

### Post by taurus on 2009-03-14
Someone told you to press <Alt>F2 to bring up a dialog and then type in **vmware** to run it.

---

### Post by JerryI on 2009-03-15
And when I do that, the web browser opens and hangs with the message 'loading.......'

---

### Post by teamcoltra on 2009-03-15
There are 2 ways to load an app... in termianl just type out the name of the app...

or go /usr/bin and select the program

---

### Post by Cheesemill on 2009-03-15
VMware Server runs automatically on boot. If you're running 2.0 which it looks like from your post then there isn't a frontend application as such, it is all web based. Just type either of the following 2 URL's into Firefox and you should be away.

[http://localhost:8222/ui]("http://localhost:8222/ui")
[https://localhost:8333/ui]("https://localhost:8333/ui")

If you're running VMware on a headless server like I do then obviously fire up Firefox on a different machine and substitute localhost for the correct IP / hostname.

Cheesemill

---

