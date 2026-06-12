---
title: "Ubuntu 9.04 internet not working?"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by marcelluspye on 2009-11-20
I posted this a while ago, people asked me for information, I gave it, they didn't reply. I assume this is because it took me a couple of days to check the forum, so I have this question unanswered. This is the original text of my question:

I am dual-booting Windows XP and Ubuntu 9.04 on my circa 2003 Dell Dimension 2350. If I run Windows, I can connect to my WEP-protected Wireless network. If I go onto my Netbook, which runs Ubuntu 8.04, I can connect. However, no matter what I do in Ubuntu 9.04 I cannot get it to connect. I have it set with the exact same network settings as the Netbook, but it will not connect. Every time it tries to connect and I enter in either of the two passwords (the first two WEP indexes) it only asks for the password again and again. I have tried everything I can think of as an experienced Windows User and a newbie Ubuntu User, and I can not get anything to work. What do I do?

They asked me to post the contents of the command line when I entered certain things. Here they are: (the command I entered comes first with a colon after it)

IWCONFIG:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"6Windmill"  Nickname:"6Windmill"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:25:9C:72:45:32   
          Bit Rate:11 Mb/s   Tx-Power:8 dBm   
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Link Quality=65/100  Signal level=-61 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sudo lshw -C network:
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:08:74:c0:76:58
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:a3:8d:0e:aa:aa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:f0:93:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-b

I have a computer with Ubuntu but no internet. It's like buying that new Bugati car and finding out you don't have an engine. Can anyone help?

---

### Post by bodhi.zazen on 2009-11-20
It appears your wireless card is working, it just needs to be configured.

What settings are your using on your wireless network ?

Normally one manages network settings in network manager, the little icon in your tool bar at the top ;)

---

### Post by pbateman on 2009-11-20
Is your SSID hidden?
If so try broadcasting it...i had one hell of a time time trying to get my laptop to connect with 9.04 and had similar issues as you. Turns out Ubuntu 9.04 does not play well with many hidden networks. As soon as I broadcasted the SSID i had no more issues...

---

### Post by marcelluspye on 2009-11-21
My SSID is not hidden, and I am connecting on my Dell Insiron Mini 10v (running Ubuntu 8.04) right now, with the same settings. I've configured everything a while ago, so it looks just like my laptop. But it still refuses to connect. If it's of any help, the same commands put into the command line on my laptop:

lo        no wireless extensions.

eth0      no wireless extensions.

sms       no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:4  Signal level:195  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

nicholas@nicholas:~$ sudo lshw -C network
[sudo] password for nicholas: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:49:86:a9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.1.100 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:b3:12:60
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: sms
       serial: 00:53:49:41:4e:4f
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


Is there any other way to configure my settings? I think I read a post about a guy using Xubuntu who found another network-manager-like app.

---

### Post by Iowan on 2009-11-21
Doubt [this]("http://ubuntuforums.org/showthread.php?t=1156441") will help - but just in case...

---

### Post by bodhi.zazen on 2009-11-22
Do you not use network manager to connect ?

Left click the network manager icon, select your network, and connect.

Otherwise, as I said, your hardware is working, so listing your hardware is not helpful. You need to configure your network.

So are you connecting with WEP / WPA ? tell us about your network.

I find network manager does not work so well in Ubuntu 8.04, particularly with WPA, so you may try wicd:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It is easy to install, instructions on the wicd web site.

---

### Post by marcelluspye on 2009-11-22
I am using the Network Manager, I have configured my settings,(I did this long ago,) and while they are all what I assume to be correct it still does not connect. Screenshots:
[IMG]http://images.roflcopter.net/image/2830.jpeg[/IMG]
[IMG]http://images.roflcopter.net/image/2831.jpeg[/IMG]
[IMG]http://images.roflcopter.net/image/2832.jpeg[/IMG]
NOTE: These settings are identical on my 8.04 netbook remix Dell Mini, so I assume they are good.

---

### Post by bodhi.zazen on 2009-11-22
Thank you for the screen shots. Hopefully someone can answer why it does not work.

I have a very similar problem with 8.04 and wireless. No matter what I do, I can not get network manager to work on my wireless WAP. It works just fine with 8.10 + (9.04 and 9.10), but not 8.04.

My only solution has been to use wicd on 8.04. Even with wicd I have problems from time to time. If Ubuntu 8.04 does not connect when it boots, I can no manually connect no matter what I do, the only solution that has ever worked is to reboot. Sometimes this means I have to reboot 5+ times.

The very same hardware works flawlessly with Ubuntu 8.10 or higher as well as Fedora 10 +.

So I suggest you either try another version of Ubuntu or perhaps wicd.

My only other suggestions would be to :

1. Click the box to show your password and confirm that it is correct.

2. Turn off WEP and try either no encryption or perhaps WPA.

---

### Post by marcelluspye on 2009-12-02
So I connected via wired connection, installed wicd, and it still isn't working. [IMG]http://images.roflcopter.net/image/2923.jpeg[/IMG]

[IMG]http://images.roflcopter.net/image/2924.jpeg[/IMG]

---

### Post by bodhi.zazen on 2009-12-02
For WEP, are you entering a password or a hex key ?

What you entered looks way too short for a hex key ;)

---

### Post by k3lt01 on 2009-12-02
Try following the instructions in [this]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") post. Let us know how you go.

---

### Post by bodhi.zazen on 2009-12-02
> **k3lt01 said:**
> Try following the instructions in [this]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5") post. Let us know how you go.

Are you sure that is the post you intended ?

---

### Post by k3lt01 on 2009-12-02
> **bodhi.zazen said:**
> Are you sure that is the post you intended ?Yep.

I like to keep to the old KISS adage.

I would have gone even further and suggested he start all over again as Wicd is a poor excuse for Network Manager. Once Network Manager has been removed it often takes a complete fresh re-install to get Network Manager back again (and working properly). However having said that with all else being equal the issue isn't hardware related, going to Wicd does complicate things but hey it happened. If it isn't hardware related, as you yourself have already said it must be settings related. I have come across this same problem a few times, one version of Ubuntu works ootb, another doesn't, the ones that don't get this modification to the dhclient.conf file and after a network restart as per the instructions I get my internet back.

Its simple, sweet and works without changing the default Ubuntu install to much.

---

### Post by bodhi.zazen on 2009-12-02
OK, that is a new one on me and I would not expect that change to make a difference as it is using the OpenDNS nameservers and I would not expect that to be related to connecting to his router.

I also have to disagree with you and wicd. It is simple to re-install network manager if you wish and does not, in my experience, require re-installing Ubuntu.

I find sometimes wicd works better then network manager, especially with WPA, and especially with Ubuntu 8.04.

@marcelluspye your options are:

1. Connect to your wireless router and turn off encryption. At least then we can see that your hardware is working.

2. When you turn WEP back on, get the **HEX Key** from your wireless router and enter that in wicd (rather then a password).

---

### Post by k3lt01 on 2009-12-03
It is simply something else for him to try.

As for Wicd, for me at least it is well named wicd is as wicked does, it stuffed me around no end the 2 times I tried it. I have never been able to reinstall NM after installing Wicd and get to work easily, both times I had to reinstall Ubuntu.

---

