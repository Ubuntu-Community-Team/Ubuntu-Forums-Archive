---
title: "Ethernet and Wireless not working, Dell Inspiron 5100"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by why789 on 2013-10-05
Hello all!!

     Well here I am, a happy user of Ubuntu on my personal computer :) I am now working on an older laptop (Dell Inspiron 5100), attempting to give it new life with Ubuntu! However I have had some slight hiccups and I'm not quite sure what to do at the moment :( 

     Process: For some reason the laptop won't recognize any CD's in the CDROM, therefore I installed Lubuntu via a USB made with UNetBootin. No problem there :) Started up the alternate installer, no problem until we get to the networking step, when asking for the primary network interface i choose eth0 (and make sure the ethernet is plugged in correctly), checks the link and gives me some DHCP problems, can't remember the exact wording. Anyway the end result is that it can't connect via DHCP and that I must try again or manually configure the network... Since I don't know how to "manually configure" the network I tried again but this time with the wlan0 as my "primary interface". I put in the ESSID of my router that is 1 foot away from the laptop, same story :/ 
 
     So, I simply ignored the error and continued on with the installation, all went okay, partitioned my hard drive placing lubuntu as the sole OS and removing pesky windows once and for all ... I than get to the final stretch of the installation and that's installing "additional packages", so I choose the LXDE desktop environment and the Lubuntu minimal installation... I than get a red error saying there is an error with the network (no surprise there....) so I continue on, boot up into my "lubuntu" and, as expected, I load up into the ubuntu command line login :) 

     So now I feel as if I'm officially stuck because I can not ping anything, I can not use apt-get (no internet...), I also can not insert the lubuntu CD to install "lubuntu-desktop"... What do I do?

     After much "googling" I find a lot of "troubleshooting" but not many solutions... Here are some outputs of some "troubleshooting" commands, I hope they are useful and that somebody can help me out here!!

```

$ifconfig 
lo     link encap:Local Loopback
       inet addr:127.0.0.1     Mask:255.0.0.0
       inet6 addr:  ::1/128    Scope:Host
       UP LOOPBACK RUNNING    MTU:16436    Metric:1

etc... etc... nothing else real interesting there.... 


$lspci | grep Ethernet
Ethernet Controller: Broadcom Corporation BCM4401 100Base-T (rev-01)
Ethernet Controller: Atheros Communications Inc. AR5211 Wireless Network Adapter [AR5001X 802.11ab] (rev 01)

$dmesg | grep eth0
b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:0d:56:34:39:08
ADDRCONF(NETDEV_UP): eth0: link is not ready

$sudo dhclient -v eth0
Listening on   LPF/eth0/00:0d:56:34:39:08
Sending on   LPF/eth0/00:0d:56:34:39:08
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15

etc. etc...
continues in this manner until I ctrl+c it....

$cat /etc/network/interfaces
#The loopback network interface
auto lo
iface lo inet loopback

```

I would appreciate any wisdom from any of the Ubuntu gurus/geniuses that I know lurk (for lack of a better work) this forum!!

Thank you in advance!
why789

---

### Post by 7182818 on 2013-10-08
Does 'ifconfig' show anything for eth0?  If not, try running 'ifconfig -a'?

---

### Post by zKhtdyX on 2013-10-25
heyho!
What is the content of your "/etc/udev/rules.d/70-persistent-net.rules" ?

Please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```

---

