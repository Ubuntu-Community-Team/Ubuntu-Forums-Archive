---
title: "{LTSP } Linux Terminal Server Project, multiboot from hd"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by ubu_dynamite on 2008-10-10
I have LTSP working on my laptop as a test running hardy
booting through PXE works now but i need to find a way to multiboot some older machines whitout erasing the existing ubuntu or windows install on it.

Does annyone know how to do this?

[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPMultiboot](https://help.ubuntu.com/community/UbuntuLTSP/LTSPMultiboot)
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe](https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe)

boot LILO/GRUB/SYSLINUX image .zlilo, (To add to the grub bootlaoder menu)

thanks in advance.


I did a clean install on my server with 2 network cards using Hardy server
[COLOR="SandyBrown"][SIZE="5"]Work in progress PXE and multiboot ubuntu ltsp with grub working but has no desktop yet!![/SIZE][/COLOR]


Install Ubuntu server
After the install login to the server
Edit the sources.list
```
sudo nano /etc/apt/sources.list
```

```
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse
```

Save the sources.list
Update ubuntu server
```
sudo aptitude update
sudo aptitude dist-upgrade
```
Reboot

Install openssh-server
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)
[https://help.ubuntu.com/community/SSHHowto#Installing%20the%20SSH%20Server](https://help.ubuntu.com/community/SSHHowto#Installing%20the%20SSH%20Server)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
```
sudo aptitude install openssh-server
```

Install LTSP
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
```
sudo aptitude install ltsp-server-standalone
```

Create a static interface i used eth0
```

sudo nano /etc/network/interfaces

```
```

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
name ltsp
address 192.168.100.1
netmask 255.255.255.0
gateway 192.168.100.0

auto eth1
iface eth1 inet dhcp
name internet

```
```
sudo /etc/init.d/networking restart
```

Ad the default dhcp server interface
```
sudo nano /etc/default/dhcp3-server
```
```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"
```
Save the file

Edit ltsp dhcp.conf
```
sudo nano /etc/ltsp/dhcpd.conf
```
```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.100.0 netmask 255.255.255.0 {
   range 192.168.100.20 192.168.100.250;
#    option domain-name "example.com";
   option domain-name-servers 192.168.100.1;
   option broadcast-address 192.168.100.255;
   option routers 192.168.100.1;
#    next-server 192.168.100.1;
#    get-lease-hostnames true;
   option subnet-mask 255.255.255.0;
   option root-path "/opt/ltsp/i386";
   if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
       filename "/ltsp/i386/pxelinux.0";
   } else {
       filename "/ltsp/i386/nbi.img";
   }
}

```
```
sudo /etc/init.d/dhcp3-server start
```

Now create your Thin Client environment on the server.
If you are on a 64-bit system but your clients have another architecture use the --arch option eg. sudo ltsp-build-client --arch i386 
```
sudo ltsp-build-client
```


At some point in the future, updates will become available for your LTSP server.
You must remember that altough you may have applied all the updates to
the server itself, as in the instructions....
HERE it is likely that the LTSP chroot will also need updating. To do
this you must open up a terminal and use the following commands.
```
sudo cp /etc/apt/sources.list /opt/ltsp/i386/etc/apt/
sudo chroot /opt/ltsp/i386
aptitude update
aptitude dist-upgrade
exit

sudo ltsp-update-kernels
```

All of your clients will now use the latest kernel upon their next reboot.

Edit tftpd-hpa 
```
sudo nano /etc/default/tftpd-hpa
```
```
#Defaults for tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot"
```
```
sudo /etc/init.d/tftpd-hpa start
```

Add some client network card drivers
On the client find out the driver your network card is using
```
lshw -C network
```

on the server
```
sudo nano /opt/ltsp/i386/etc/initramfs-tools/modules
```
and add your drivers"
```
e1000
e1000e
via-rhine
sis900
```
etc."
```
sudo chroot /opt/ltsp/i386 update-initramfs -u
sudo ltsp-update-kernels

```

```
sudo ltsp-update-sshkeys
sudo ltsp-update-image

```

Network booting with grub 
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

If you use LTSP or Edubuntu, you may want to boot from your network card.
Specific network cards need a specifc rom to boot from.
Go to [www.rom-o-matic.com](www.rom-o-matic.com) and get the appropriate rom.
Edit /boot/grub/menu.lst and add the following before ### BEGIN AUTOMAGIC KERNELS LIST
or after ### END DEBIAN AUTOMAGIC KERNELS LIST, otherwise your changes will be wiped out by security updates, etc. 

I already have a pc running ubuntu they already have a grub so i did
Download a rom I downloaded gpxe:all-drivers LILO/GRUB/SYSLINUX loadable Linux kernel format (.lkrn)
[http://www.rom-o-matic.net/](http://www.rom-o-matic.net/)
```
sudo cp gpxe-git-gpxe.lkrn /boot
```
```
sudo nano /boot/grub/menu.lst
```

```
title		Linux terminal server:
root

title 		LTSP
root 		(hd0,4) ## Change to your root
kernel 		/boot/gpxe-git-gpxe.lkrn
```

---

