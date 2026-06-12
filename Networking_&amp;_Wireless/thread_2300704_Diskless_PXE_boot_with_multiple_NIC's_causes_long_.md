---
title: "Diskless PXE boot with multiple NIC's causes long delay with DHCP"
date: 2015-10-27
forum: Networking &amp; Wireless
---

### Post by Chris on 2015-10-27
I have a diskless client that has two network cards in it. Most of the time only one of the interfaces is active on a network (this is the interface the iscsi boot disk is on). When this machine boots it will hang for a long time waiting for network configuration (IP-Config: no response for x seconds, giving up). I see the machine sending DHCP requests over and over again on the primary interface and it *is* getting DHCP responses but they seem to be ignored. This continues until the script ipconfig loop count is finished after many minutes then finally it says it got the DHCP address and continues to boot.

If I disable the second network card then it boots quick like normal. So it seems if the secondary NIC is not connected to a network this breaks the initial network config for some reason even though that interface is not used for anything.

I have tested 14.04 and 15.10, they both do the same thing.

---

### Post by Chris on 2015-10-28
I'm using iPXE to sanboot to GRUB which is then loading the kernel. I  could of course hard-code a parameter to the kernel that sets the  interface to use but this iSCSI image is used for multiple clients, most  of which only have one interface anyway.

I'm using ISCSI_AUTO in  the iscsi.initramdisk. I wish this would cause the use of iBFT  information (or whatever iSCSI parameter) to determine which interface is the boot NIC and then just  configure that one. From looking at the script (functions:  configure_networking which is called by local-top/iscsi) it does not appear to do this. Instead it's  looking for BOOTIF to be set by pxelinux or kernel param (who uses  pxelinux to boot raw kernels with iSCSI?!). I'm surprised this is still an issue even in 15.10.

Am I missing something? Is there some option somewhere that will cause it to use the iBFT/iPXE boot information to pick the active iSCSI network interface?

---

### Post by Chris on 2015-10-29
Seems the only way to "fix" this is to "net.ifnames=0 biosdevname=0" kernel options then set the device in /etc/initramfs-tools/initramfs.conf

That's not really a proper fix though because it relies on all clients always using that same interface (eg. eth0).

I believe a proper fix would be to modify the configure_networking script function.

---

### Post by MACscr on 2015-12-14
Is this really the case? I have 4 nics on each server and there are no guarantees on what their assignment is going to be. Stinks we cant assign ip information to a specific interface by mac address with the APPEND line in PXE. hmm.

---

