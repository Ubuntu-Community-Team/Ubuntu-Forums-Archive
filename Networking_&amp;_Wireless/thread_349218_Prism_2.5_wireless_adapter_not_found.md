---
title: "Prism 2.5 wireless adapter not found"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by jstrauss on 2007-01-29
Hi,

I have an IBM Thinkpad A30, I'm running 6.10 ubuntu LiveCD.  I have a 

root@ubuntu:~# lspci | grep Prism
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

wireless card.  When I ifconfig I have no entry for the card, even though it's being seen by lspci.  

I have been googling, and reading the forums and archives to no avail.  The card is seen, configured, and usable (with some messing around) when using the 6.06 LiveCD.

It does not matter if I run the LiveCD or I install, I have the same issues.  Below are some command outputs

Anyone have any idea why the card is not seen, and how to get it seen?

Thanks
Jay

root@ubuntu:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:59:83:5F:D2
          inet addr:192.168.28.119  Bcast:192.168.28.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe83:5fd2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4243 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8222962 (7.8 MiB)  TX bytes:362890 (354.3 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

root@ubuntu:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.

root@ubuntu:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by job2600 on 2007-01-29
I'm having a similar issue being discussed in another posting?

What is the output of `sudo lshw -C Network` for you?

My Prism 2.5 card is showing disabled there for some reason, although it worked just fine during the installation from the alternate cd.

```

*-network DISABLED      
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 link=no multicast=yes
       resources: iomemory:e8010000-e8010fff irq:9


```

---

### Post by koshari on 2007-01-29
in edgy i had to blacklist the following modules to get my prism pci adapter to load the orinco drivers , and then it was happy, 

see

[http://www.ubuntuforums.org/showthread.php?t=288649](http://www.ubuntuforums.org/showthread.php?t=288649)

---

### Post by job2600 on 2007-01-29
> **koshari said:**
> in edgy i had to blacklist the following modules to get my prism pci adapter to load the orinco drivers , and then it was happy, 

see

[http://www.ubuntuforums.org/showthread.php?t=288649](http://www.ubuntuforums.org/showthread.php?t=288649)

Awesome. That worked for me. Many thanks!

---

### Post by jstrauss on 2007-01-29
Except, in order to use WPA/WPA2 you need to use the hostap drivers and NOT the orinoco.  Under 6.06 I had to blacklist the orinoco, and orinoco_pci to get it working

Jay

---

### Post by jstrauss on 2007-01-29
Also, How do you blacklist when running a LiveCD?

Thanks
Jay

---

### Post by msak007 on 2007-02-25
> **job2600 said:**
> I'm having a similar issue being discussed in another posting?

What is the output of `sudo lshw -C Network` for you?

My Prism 2.5 card is showing disabled there for some reason, although it worked just fine during the installation from the alternate cd.

```

*-network DISABLED      
       description: Ethernet interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 12
       bus info: pci@00:12.0
       logical name: wlan0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_pci driverversion=0.2.5 link=no multicast=yes
       resources: iomemory:e8010000-e8010fff irq:9


```
That's exactly the output I get! I had an old computer which had Kubuntu Dapper on it, and I wanted to upgrade to Edgy. At the same I did the dist-upgrade I was messing around with /etc/iftab to rename the interface to "wlan0" instead of "eth0" and after the reboot it would no longer work. ifconfig showed no outputs other than "lo", lshw showed the same exact output you got, and multiple attempts to bring up the interface all failed. I thought I did something wrong with renaming the interface, so I formatted and reinstalled Xubuntu Edgy and even though it detected the card and connected (in the alternate CD installer environment), after it rebooted the card couldn't be found. I blacklisted the orinoco and prism2 modules and now after the reboot everything works! Thanks for tip.

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

