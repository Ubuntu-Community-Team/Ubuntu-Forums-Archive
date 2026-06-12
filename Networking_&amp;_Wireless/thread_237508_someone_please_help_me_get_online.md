---
title: "someone please help me get online"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by Daboo on 2006-08-16
A couple of months ago I struggled and struggled trying to get internet to work in Dapper. It used to work fine in Breezy. I never did get it working, now I'd like to try once more. I have a gigabit brand mobo (I'm not sure of the model) thats got onboard ethernet (nforce2?). I just tried installing the nvnet driver, but pretty much ran into depedency hell. I could not simply do a apt-get install whatever, because I had no connection. I must have rebooted about 20 times downloading crap in windows to try and install it. Once I did finally get all the dependencies worked out, the installer for nvnet complained about cc missing or something (I had  all the build-essential stuff installed). 

So I said screw that, and threw in another NIC (3com) I had laying around. This comes up as eth1, but doesn't work either. 

I don't have a router, and I'm plugged directly into the broadband modem. 

I'm pretty much at my wits end here with this, so if anyone could help me through getting this worked out, I'd really appreciate it!

---

### Post by dmizer on 2006-08-16
the 3comm nic should work.

if you are connected directly to your modem and do not have a router, this will cause problems when switching back and forth between multiple computers (this problem also applies to multiple os' when using only one computer and dual booting).

your modem is still trying to hand an ip to your windows box.  it doesn't have router logic which realizes that there is a different computer attached now.

try this (with your 3comm card attached): unplug your modem, leave it unpluged for about 5 or 10 seconds, and plug it back in.  once the modem has completely rebooted (shows sync), run this command in ubuntu shell:
> sudo /etc/init.d/networking restart
then do ifconfig and see if you show that you've retrieved an ip.  if so, you should be able to surf.

---

### Post by Daboo on 2006-08-16
Here's what I get afer /etc/init.d/networking restart:

Listening on LPF/eth1/00:10:5a:18:f9:01
Sending on   LPF/eth1/00:10:5a:18:f9:01
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 10.38.232.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.38.232.1
subnet_number():inet.c:56: Addr/mask length mismatch.
Failed to bring up eth1.

:-k

---

### Post by hogski on 2006-08-16
I've been looking about on other forum threads regarding internet connection and a common problem seems to be that Ubuntu has IPv6 enabled which affects internet connection. 

Taken from Ubuntu forums>Support & Resources>Previous
Ubuntu releases>Breezy Badger 5.10>Ubuntu 5.10
Hardware Help>Networking
To disable use

Code:

sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak 

sudo depmod -a

then reboot

Go to the above forum which has a great page on Wired ethernet troubleshooting

Hope this helps:-k

---

### Post by Daboo on 2006-08-16
Thanks, I'll give that a shot. Although, it used to work fine in Breezy.

---

### Post by Daboo on 2006-08-16
Well, it looks like ipv6 was disabled, but no joy. Here's some more info:

**ifconfig eth1**
eth1      Link encap:Ethernet  HWaddr 00:10:5A:18:F9:01
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4372 (4.2 KiB)  TX bytes:2736 (2.6 KiB)
          Interrupt:201 Base address:0x8000


**lspci | grep Eth**
0000:00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
0000:02:08.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)


**lsmod | grep mii**
mii                     5888  1 3c59x

---

### Post by dmizer on 2006-08-16
how about posting all of ifconfig (not just ifconfig for eth1), and post the contents of /etc/network/interfaces

looks like you have a bridge in place.  are you using vmware or some other kind of virtual envronment?

---

### Post by Daboo on 2006-08-17
Success!

Well, for whatever reason DHCP will not work. I simply tried manually setting the IP / gateway / DNS servers.

Although I was directly plugged into the modem, I assumed I didn't have an internal ip or anything. But I guess the BPL modem I'm using acts as a mini router of sorts, and assigned me a seprate IP. I'm not sure what the point of that is... For anyone wondering, it's made by Asoka. 

I just got the gateway and dns servers from ipconfig in XP, then set them using the network admin tool in Ubuntu. Dmizer, thanks for your help.

---

