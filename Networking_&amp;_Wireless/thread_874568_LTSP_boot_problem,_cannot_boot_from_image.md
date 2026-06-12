---
title: "LTSP boot problem, cannot boot from image"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by mixersoft on 2008-07-30
I installed the ltsp server from the 8.04.1 alternate CD. PXE boot works fine over dhcp, but i'm getting this error when the client tries to actually boot from the ltsp image:

ipconfig: eth0: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
/init: .: 1: Can't open /tmp/net-eth0.conf

From reading other posts, I suspect that the sky2 driver for the Marvell ethernet adapter is not in the boot image. But how do I add it? 

The ltsp-server also uses the sky2/Marvell driver and it works just fine -- when does it get loaded?

---

### Post by Dr John on 2008-08-20
I too have this problem.  I'm booting from an Intel D945GCLF motherboard which I know has had problems with network device drivers, but which runs the most recent versions of Hardy without difficulty (including the network interface).  I note that /opt/ltsp/i386/etc/interfaces has no entry for eth0.  Is this the problem, or has it to do with the lack of an appropriate driver as suspected by mixersoft?

Any help would be very much appreciated.

Dr John

---

### Post by mixersoft on 2008-09-09
Still having the same problem.

Here's what I've tried so far:

[LIST]
[*]my ltsp server and client box have identical configs
[*]using Hardy 8.04.1 alternate, with ltsp server installed from the CD

[*]I followed this post to ensure both the ltsp-server and ltsp chroot are up-to-date:  
[INDENT]   [http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/ltsp-updates.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/ltsp-updates.html)[/INDENT]
[*]on the ltsp server, eth0 seems to work just fine:
[INDENT]   sudo lsmod    ==> lists the sky2 driver on the ltsp server
   sudo modprobe sky2 ==> shows nothing. but no errors. so the driver is fine, right? [/INDENT]

[*]/opt/ltsp/i386/boot/pxelinux.cfg/default edited as follows:
[INDENT]    DEFAULT vmlinuz ro initrd=initrd.img
    # DEFAULT vmlinuz ro initrd=initrd.img quiet splash[/INDENT]

[*]on the theory that eth0 was being reset in the middle of PXE Boot
     see  [https://help.ubuntu.com/community/DisklessUbuntuHowto#head-320eeefb87afe42faa400af457bd455bec59d7ef](https://help.ubuntu.com/community/DisklessUbuntuHowto#head-320eeefb87afe42faa400af457bd455bec59d7ef) 
  /opt/ltsp/i386/etc/network/interfaces was edited for eth0 as follows (each config was tested to the same result): 
  

[INDENT]   # This file describes the network interfaces available on your system
   # and how to activate them. For more information, see interfaces(5).

   # The loopback network interface
   auto lo
   iface lo inet loopback

   # The primary network interface for PXE Boot
   #auto eth0
   #iface eth0 inet dhcp
   iface eth0 inet manual[/INDENT]

[*]each time, I ran these commands to make sure the ltsp image is updated
[INDENT]    sudo ltsp-update-kernels
    sudo ltsp-update-image
    sudo ltsp-update-sshkeys[/INDENT]

[/LIST]

In all cases, I get the PXE boot image, get past the ubuntu splash screen, and then halfway through boot, it crashes with this message:

[INDENT]  ipconfig: eth0: SIOCGIFINDEX: No such device
  ipconfig: no devices to configure
  /init: .: 1: Can't open /tmp/net-eth0.conf
  [] Kernel panic - not syncing: Attempted to kill init![/INDENT]

Can someone offer any additional suggestions???

m.

---

### Post by mixersoft on 2008-09-11
Here's an interesting twist. 

I put in a 2nd PCI ethernet controller in the client which uses the Realtek chip/drivers. This is in addition to the onboard Marvell/sky2 ethernet controller.

Then I observe the following behavior:
[LIST]
[*]It will only PXE Boot from the onboard Marvell controller (sky2 driver)
[*]where it used to crash (see above) it actually loads the drivers for the Realtek controller
[*]if I move the ethernet plug from the Marvell to the Realtek controller, it re-establishes the ethernet connection
[*]and lo-and-behold, a successful boot.
[/LIST]

Here is the term output on boot where it continues with the Realtek controller:
[INDENT]
[] eth0: RTL8169sb/8110sb at 0xf8828000, [mac addr], XID 10000000 IRQ 17
Done.
[] NET: Registered protocol family 17
IP-Config: eth0 hardware address [mac addr] mtu 1500 DHCP RARP
[] r8169: eth0: link down
( ... then I move the ethernet plug from the Marvell to the Realtek PCI card... )
[] r8169: eth0: link up
( ... then some fast scrolling to the LTSP DHCP settings... and done!)[/INDENT]

So it seems like it is definitely a problem somewhere with the Marvell controller and how it dies somewhere in the boot of the PXE boot image, but I have no idea how to fix this. 

FYI - If I plug in a different ethernet cable to the Realtek controller, then it doesn't complete the PXE boot.

Any ideas????

---

### Post by mixersoft on 2008-09-16
The good people at IRC #ltsp helped me solve the problem

here's what I did to get PXE boot to work with the marvell/sky2 driver
[LIST=1]
[*]sudo nano /opt/ltsp/i386/etc/initramfs-tools/modules and add "sky2"
[*]sudo nano /opt/ltsp/i386/usr/share/initramfs-tools/hook-functions and
add "sky2" at the end of this line: 
[INDENT]r8169 s2io sis900 skge slhc smc911x starfire sky2 \[/INDENT]
[*]sudo chroot /opt/ltsp/i386 update-initramfs -u
[*]sudo ltsp-update-kernels
[*]and problem solved!
[/LIST]

---

### Post by the_transltr on 2008-09-29
I still have this problem. My NIC is Attansic for the server and Realtek for the client.

---

