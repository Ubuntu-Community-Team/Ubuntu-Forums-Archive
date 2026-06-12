---
title: "Networking problem with the Realtek 8139"
date: 2005-11-17
forum: Networking &amp; Wireless
---

### Post by ShaneJ on 2005-11-17
Hi people, my first post on the forum so go easy;) 
I'm a fairly new user to Linux but I can normally get myself out of trouble by searching forums etc, but this issue has me stumped.
At the moment I'm just experimenting on a "test" machine assembled from old parts found in the bottom of the wash basket. PII 333, 512mb Ram, 4gig hdd and the Realtek 8139 nic. Installed on the system is Ubuntu Sever 5.10.
The problem I am having is the network is very unstable/slow. If I ping a server on the network, the ping times can vary wildly and I get random packet loss. I'll try and post as much information about the system, what I have tried and what is happening.
During boot it takes takes two cups of coffee to receive an ip from the DHCP server. 
Doing an ifdown and then an ifup to renew the ip, I got No DHCPOFFERS received. No working leases in persistent database - sleeping. Trying ifdown and ifup again, I get an ip but renewal took 2911 seconds.
I have read on this forum about issues with ipv6 so I have edited /etc/modprobe.d/aliases alias net-pf-10 ipv6 to alias net-pf-10 off #ipv6
This appeared to have no effect. The ifdown and ifup resulted in ip renewal in 3020 seconds.

lspci reports ths card being a RTL-8139/8139C/8139C+ (rev 10)
I dont fully understand the module list, but lsmod  | grep 8139 reports:
8139too   25504   0
8139cp    19744   0 
mii            5696    2    8139too,8139cp

dmesg | grep 8139 reports:
8139cp: 10/100 PCI Ethernet driver v1.2
8139cp: pci dev 0000:00:0d.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
8139cp: Try the "8139too" driver instead.
8139too Fast Ethernet driver 0.9.27
eth0: Realtek RTL8139 at 0xe400, 00:40:c7:**.**.**, IRQ 10
eth0:    Identified 8139 chip type 'RTL-8139C'
This appears that the wrong driver is being loaded first?
I tried the following:
ifdown eth0
rmmod 8139cp
ifup eth0
No DHCPOFFERS received. No working leases in persistent database - sleeping
I tried again just for interest sake:
ifdown etho
ifup eth0
Ip bound to 172.30.*.* ip renewal in 3012 seconds.

So I setup eth0 for static ip.
Ifconfig reports the ip address I specified.
I ping a server on the network, 14 packets transmitted, 7 received, 50% packet loss, time 12997ms
Shes not happy!

Windoze, Mandriva and Fedora work fine on this system with this network card. It just appears to be a problem with Debian based distros as Knoppix has the same problem.
So I’m now lost for ideas. Can anyone point me toward a fix for this? I know I could easily just exchange the NIC for another type, but I wouldn’t learn anything if I kept sidestepping a problem.
Thanks

---

### Post by rstewartmailacct on 2005-11-21
Hi,

Did you get this worked out?  I have same problem.  Looks like Ubuntu is loading both 8139cp and 8139too.  I can make it work by removing both modules and running modprobe with media=0x01 in 8139too.modprobe file in etc/modprobe.d.  I would like this to work without manual intervention.  

I hate to complain but FC4 ran this OK.  This is really annoying.

Thanks

---

### Post by mips on 2005-11-22
Try adding **acpi=off** to the linux boot line in GRUB and see if it makes a difference. Be carefull

Alternatively look at these posts:
[http://www.ubuntuforums.org/showthread.php?p=377332#post377332](http://www.ubuntuforums.org/showthread.php?p=377332#post377332)
[http://ubuntuforums.org/showthread.php?t=87336&highlight=8139](http://ubuntuforums.org/showthread.php?t=87336&highlight=8139)
[http://ubuntuforums.org/showthread.php?t=87968&highlight=8139](http://ubuntuforums.org/showthread.php?t=87968&highlight=8139)

Maybe also look into **noapic**, **pnpbios=off**

---

### Post by ShaneJ on 2005-11-22
I still haven't fixed the actual problem.
I did however replace the 8139C NIC with an 8139B and everything works fine. I still get the following error in dmesge, but everything is working:
8139cp: 10/100 PCI Ethernet driver v1.2
8139cp: pci dev 0000:00:0d.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
8139cp: Try the "8139too" driver instead.
8139too Fast Ethernet driver 0.9.27
eth0: Realtek RTL8139 at 0xe400, 00:40:c7:**.**.**, IRQ 10
eth0: Identified 8139 chip type 'RTL-8139C'

mips, I studied the 3 threads you mention for a good 8 hours before I made this thread.
When I installed ubuntu for the 416th time I did "linux acpi=off" but it didnt seem to make any difference. I'm not near the machine at the moment, but when I boot it I get an error about "unable to load acpi fan module" or something similar. The machine in question would in real life be a server. so I would think that any acpi control is not required. Or am I wrong?
Can I easily check grub to see if the acpi line is there? I'm still struggling to learn the structure of Debian based distros :(

---

### Post by Gaylord Focker on 2005-11-26
[http://ubuntuforums.org/showthread.php?p=522773#post522773](http://ubuntuforums.org/showthread.php?p=522773#post522773)
adding grub lines --> It worked for me.

But I think this should be corrected in 2.6.12 kernels.... More info:
"rtl8139 (8139too) net problem in linux 2.6.10"
[http://www.ussg.iu.edu/hypermail/lin...02.0/1404.html](http://www.ussg.iu.edu/hypermail/lin...02.0/1404.html)

---

