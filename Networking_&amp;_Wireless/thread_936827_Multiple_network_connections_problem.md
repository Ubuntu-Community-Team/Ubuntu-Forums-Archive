---
title: "Multiple network connections problem"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by zenkaon on 2008-10-03
Hello,

Currently I have a 3G GSM usb modem which works fine under ubuntu. I can connect using either nm-applet 0.7 or wvdial. No problems there. This is my internet connection (Not going to be getting "regular" broadband until mid 2009 - don't ask, it's a long story that boils down to BT are arseholes)

I also have a wireless router (running OpenWRT 7.09) which would normally connect my PC, laptops and NAS drive to the internet.

Currently I can be either:
1.) Online via 3G with no access to my NAS drive or PCs
2.) Access my internal LAN, PCs and NAS drive, but not internet

Clearly I would like to be able to do both at the same time, internet sharing would be a nice bonus as well, but not essential.

I believe this comes down to a problem with subnets and getting the configuration correction in /etc/resolv.conf but I don't know enough networking to figure it out.

My 3G connection will give me an IP on a ppp device and put it's nameservers into /etc/resolv.conf. My router will also give me an IP via dhcp on eth0/1 and put it's nameservers into /etc/resolv.conf. What I need to know is how to get them to coexist.

Can anybody help me out?

---

### Post by superprash2003 on 2008-10-03
well you can make your pc do the internet connection sharing.. for this you need two lan cards.. one LAN card from your usb modem to pc and then one from pc to router.. then enable internet connection sharing in your ubuntu pc.. and share internet..[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by iponeverything on 2008-10-03
> **zenkaon said:**
> Hello,

Currently I have a 3G GSM usb modem which works fine under ubuntu. I can connect using either nm-applet 0.7 or wvdial. No problems there. This is my internet connection (Not going to be getting "regular" broadband until mid 2009 - don't ask, it's a long story that boils down to BT are arseholes)

I also have a wireless router (running OpenWRT 7.09) which would normally connect my PC, laptops and NAS drive to the internet.

Currently I can be either:
1.) Online via 3G with no access to my NAS drive or PCs
2.) Access my internal LAN, PCs and NAS drive, but not internet

Clearly I would like to be able to do both at the same time, internet sharing would be a nice bonus as well, but not essential.

I believe this comes down to a problem with subnets and getting the configuration correction in /etc/resolv.conf but I don't know enough networking to figure it out.

My 3G connection will give me an IP on a ppp device and put it's nameservers into /etc/resolv.conf. My router will also give me an IP via dhcp on eth0/1 and put it's nameservers into /etc/resolv.conf. What I need to know is how to get them to coexist.

Can anybody help me out?


Its very strait forward --

what is the ip and netmask for your 3G and what is the ip and netmask for for your wifi router?

lets pretend that your ppp0 is 172.16.1.5 with a netmask of 255.255.255.0
and that your wifi eth0 is 192.168.1.5 with a netmask of 255.255.255.0

Add a static dhcp entry on your OpenWRT for your 3G connected machine
It might look something like this (with your MAC Address):

host mybox {
  hardware ethernet 00:44:3C:3C:B1:33;
  fixed-address 192.168.1.5;
  }

Set the default route on the OpenWRT router to be 172.16.1.5
and have its dhcpd hand out itself as the default-router.
Have DHCP hand out nameservers that you usually get from 3G.

you can do something like this in dhcpd.conf to insure that your not handing out a the default route to your 3G machine:
 
subnet 192.168.1.0 netmask 255.255.255.0 {range 192.168.0.110 192.168.0.200 options routers 192.168.0.1;}

On your 3G machine:

add something like this to your rc.local:

iptables -t nat -A POSTROUTING -s 192.168.1.0/24  -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

Then anything connecting to OpenWRT router will be routed out through your 3G connected machine.

Post back when you start playing with it, it is not that hard.

---

### Post by GuruX on 2008-11-21
I have kind of the same problem. Connect with my phone and wvdial (ppp0) to internet and connect with my wireless (ath1) to my wireless AP, which is set to static DHCP.

I have to make sure I connect with wvdial after connecting to the AP, otherwise internet won't work. My wireless is a bit unstable, and sometimes it disconnects, and then I have to reconnect my phone aswell. It's a little bit of a pain in the ***.

The difference with me is that I don't want internet connection sharing.

So, what is the solution for me?

---

### Post by GuruX on 2008-11-21
ooops, double post

---

