---
title: "network missing package and no access to internet"
date: 2016-02-11
forum: Networking &amp; Wireless
---

### Post by ali131 on 2016-02-11
I installed kubuntu 15.10 and it doesn't support any internet access method (wifi,ethernet,hotspot) I downloaded the network packages from ubuntu archives with all their dependencies manually but still can't install some packages to complete that dependency tree, I tried also Keryx on windows but it requires python & pyGTK, i run windows on 64 architecture so i couldn't find pyGTK for 64 bit.
when entering the following commands :


```
ali@ali-Inspiron-3543:~$ dmesg | grep Ethernet

[    0.718776] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded

[   14.252769] Bluetooth: BNEP (Ethernet Emulation) ver 1.3




ali@ali-Inspiron-3543:~$ dmesg | grep Wireless


[    7.389994] input: DELL Wireless hotkeys as /devices/virtual/input/input9




ali@ali-Inspiron-3543:~$ iwconfig

enp7s0    no wireless extensions.


lo        no wireless extensions.


```
the packages i need :

firmware-b43-installer

bcmwl-kernel-source 6


when i try to install the packages using dpkg :


firmware-b43-installer :

```
ali@ali-Inspiron-3543:~/repo$ sudo dpkg -i firmware-b43-installer_015-9_all.deb

[sudo] password for ali: 

(Reading database ... 161011 files and directories currently installed.)

Preparing to unpack firmware-b43-installer_015-9_all.deb ...

Unpacking firmware-b43-installer (1:015-9) over (1:015-9) ...

Setting up firmware-b43-installer (1:015-9) ...

No chroot environment found. Starting normal installation
```

bcmwl-kernel-source-6 :

```
ali@ali-Inspiron-3543:~/repo$ sudo dpkg -i bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb 

Selecting previously unselected package bcmwl-kernel-source.

(Reading database ... 161011 files and directories currently installed.)

Preparing to unpack bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb ...

Unpacking bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...

dpkg: dependency problems prevent configuration of bcmwl-kernel-source:

 bcmwl-kernel-source depends on dkms; however:

  Package dkms is not installed.

 bcmwl-kernel-source depends on libc6-dev; however:

  Package libc6-dev is not installed.


dpkg: error processing package bcmwl-kernel-source (--install):

 dependency problems - leaving unconfigured

Errors were encountered while processing:

 bcmwl-kernel-source

```

is there a way to install a package with all its dependencies without doing it manually and with no internet ?
i tried to install another distro ubuntu gnome 15.10 and the driver for ethernet exist so i can have internet access so is it possible to change linux distribution to another (ubuntu to kubuntu or mint) but without changing the kernel and all its configuration (network packages and settings, ...etc) ?

---

### Post by Hadaka on 2016-02-11
Hi, if you load the iso image correctly you should not need to do anything
to the dependency tree. I suspect you had a corrupt image or in your haste
to fix a problem with the wireless,a bad situation became worse. Let's take
a quick look at your wired and wireless cards.Please open a terminal and 
enter this one line of code.
```
lspci -n | awk '/14e/{print$3}'
```
post the output
thanks.

---

