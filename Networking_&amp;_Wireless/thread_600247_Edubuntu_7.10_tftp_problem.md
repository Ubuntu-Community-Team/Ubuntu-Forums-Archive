---
title: "Edubuntu 7.10 tftp problem"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by Pärez on 2007-11-02
I'm having a problem booting my thin client. My client gets the IP and all, but when the edubuntu logo and progress bar comes out it freezes totally. The keyboard doesn't work either. Is there a way do disable the splash screen and see if there's something going on in the background? Any help will be most appreciated.

The specs of my hardware are the following:
  
The computer I'm using as a server is: Dell Poweredge 2500, it has two 1 Gigahertz processors, about 2 Gigabits of memory and two network cards. The cards are: Intel Corporation 82557/8/9 Ethernet pro 100 and 3Com 3c905B 100BaseTX [Cyclone].
I'm using 3Com's card to connect to internet and Intel to share ip's for thin clients through a switch.

My server has Edubuntu 7.10 classroom server installed.

Here's my dhcpd.conf file:

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
#    next-server 192.168.0.254;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}


The thin client has: 2,5 Gigahertz AMD processor and 1,024 memory. The motherboard is ASUS A8N SLI with integrated NIC, NIC is NVidias nForce Networking controller.

The switch is Hewlett Packard Procurve Switch 212M.

I'm still quite an amateur with Ubuntu, I've worked with it only for a couple of months so please, make your explanation as simple as possible. Thanks!

---

### Post by SpiritIsReality on 2007-11-09
howdy
zless /usr/share/doc/upstart/README.Debian.gz
> 
Where are the boot messages logged?
-----------------------------------

Messages output by the rc scripts can be found in /var/log/boot, if
you have the upstart-logd package installed.


How can I see boot messages on the console?
-------------------------------------------

This is nothing to do with upstart, but I'll answer this anyway.
Remove "quiet" from the kernel command-line.

To make this permanent, edit /boot/grub/menu.lst and edit the line
that begins "# defoptions=" (yes, it looks like a comment).

This will change both usplash and the LSB init logging.

I have removed splash and quiet from the servers /boot/grub/menu.lst kernel line,
and the client shows boot messages on the screen.
Linux Logging [http://www.ibm.com/developerworks/linux/library/l-roadmap5/](http://www.ibm.com/developerworks/linux/library/l-roadmap5/)
trails

---

