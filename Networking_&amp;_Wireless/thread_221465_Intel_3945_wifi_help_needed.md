---
title: "Intel 3945 wifi help needed"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by Jason Spaceman on 2006-07-23
I installed Kubuntu 6.06 on my Core Duo laptop and upgraded to the SMP kernel (sudo apt-get install linux-686-smp).  That seems to have worked fine.

Now I want to get wireless working on my laptop.  It comes with an Intel 3945 mini-PCI wireless card.  From what I understand (I'm new to Ubuntu) the ieee80211 subsystem, ipw3945 drivers, wpa supplicant, etc. were added during the Kubuntu install.  Typing 'lsmod | grep ieee' gives me:

```
ieee80211              38952  1 ipw3945
ieee80211_crypt         6528  1 ieee80211
ieee80211_1_1_13       39880  0
ieee80211_1_1_13_crypt     7040  1 ieee80211_1_1_13
```

And 'lsmod | grep ipw' gives me:

```
ipw3945               132348  1
ieee80211              38952  1 ipw3945
```

And 'ps aux | grep ipw' gives me:

```
root      3265  0.0  0.0      0     0 ?        S<   02:54   0:00 [ipw3945/0]
root      3266  0.0  0.0      0     0 ?        S<   02:54   0:00 [ipw3945/1]
root      3267  0.0  0.0      0     0 ?        S<   02:54   0:00 [ipw3945/0]
root      3268  0.0  0.0      0     0 ?        S<   02:54   0:00 [ipw3945/1]
root      3415  0.0  0.0   1616   356 ?        S<   02:54   0:00 /sbin/ipw3945d-2.6.15-26-686 --quiet
```

As well, I also have the 'ipw3945.ucode' file in /lib/firmware/2.6.15-26-686

I have a Netgear WAG302 access point, connected via ethernet cable to a Netgear FVS318 router.  The router acts as my DHCP server.

Running 'iwlist scan' shows my access point.  But I can't seem to connect to it.  'sudo ifconfig eth1 up' brings up the wifi card, but my access point's logs don't show anything connecting.  The other night I seemed to get connected, however for some reason I couldn't ping anything.  My router didn't seem to give my wifi card an IP address.  What am I doing wrong?

---

### Post by ahallubuntu on 2006-07-23
I had the same problem.  I found the solution and it worked immediately, it was just a matter of installing a package - something like this:

apt-get install linux-restricted-modules-686

to get the wireless driver.  But I think I had to backup from 
2.6.15-26-686 to 2.6.15-23-686 for some reason.  I wish I could find the reference page I found this on, but it worked smoothly and easily, didn't have to change anything else after I did the update.  I just installed Ubuntu on my E1505 Core Duo with the 3945 and it works well for me, by the way.

---

### Post by ahallubuntu on 2006-07-23
Wait - this is where I found the solution:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/52302](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/52302)

I think after all I simply followed the very last line:

sudo apt-get install linux-686

and re-booted and that was that.

---

### Post by Jason Spaceman on 2006-07-23
I think Kubuntu has been detecting my wireless card from the start.  The problem seems to be getting an IP address from my router/DHCP server.  When I run 'sudo dhclient eth1' I get:

```
Listening on LPF/eth1/00:13:02:1f:ce:1d
Sending on   LPF/eth1/00:13:02:1f:ce:1d
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.0.5
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.292/0.292/0.292/0.000 ms
bound: renewal in 132592 seconds.
```

The wireless card never seems to get an IP address.  It can see my access point, 'iwlist scan' gives me:

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:B5:92:D3:AD
                    ESSID:"Boozin_and_Pranks_11g"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54
                    Quality=37/100  Signal level=-87 dBm  Noise level=-87 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 9992ms ago

sit0      Interface doesn't support scanning.
```

Is something configured wrong with my card?  Perhaps the problem has to do with my card sending out mangled DHCP requests and my router doesn't acknowledge them?

---

### Post by ltmon on 2006-07-24
I had the same problem: wireless stopped working after upgrading to linux-686-smp.

It turned out to be because the linux-restricted-modules for that kernel was in a repository that was not in my sources.list.

Make sure you have the following entry enabled:
```

deb http://security.ubuntu.com/ubuntu dapper-security restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security restricted

```

And apt-get update then apt-get upgrade

L.

---

### Post by Jason Spaceman on 2006-07-24
I don't think the problem is with either the SMP or the 386 kernel.  Either way I can't seem to get an IP address from my router.  

The card is detected, 'dmesg | grep 3945 gives me:

```
snozzy@laptop:/etc$ dmesg | grep 3945
[17179590.336000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.0.5m
[17179590.336000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179591.064000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179591.980000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
```

But when I run 'sudo dhclient eth1' I get:

```
snozzy@laptop:/etc$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:13:02:1f:ce:1d
Sending on   LPF/eth1/00:13:02:1f:ce:1d
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
Trying recorded lease 192.168.0.5
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.302/0.302/0.302/0.000 ms
bound: renewal in 108846 seconds.
```

Am I missing a step?  Is there a website someplace that walks you through the wifi setup in Ubuntu, step by step?

---

### Post by Jason Spaceman on 2006-07-24
I should also note that after attempting to get an IP address from my router I did a 'dmesg' and got this:

```
[17181046.664000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17181189.248000] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

---

### Post by ahallubuntu on 2006-07-24
Can you set a static IP address as a test in your subnet range and will that work then?

---

### Post by Jason Spaceman on 2006-07-24
> **ahallubuntu said:**
> Can you set a static IP address as a test in your subnet range and will that work then?

No, even with a static IP it still doesn't work.  The wifi card will take the IP, but I still can't ping anything on my LAN.  

I DID manage to get wifi working, briefly, last night.  I'm not sure what I did to make it work.  The only thing I changed was my /etc/iftab file, I added an entry in there for my wifi card (eth1), as it only had an entry for my ethernet port (eth0).

I'm not sure if the wireless was working completely proper, however; as I could surf the net, ping machines on my LAN, etc., but I noticed my router's log wasn't listing my laptop's hostname.  It just listed the IP address and MAC address of eth1.  Usually when my router does that it means something aint right.

---

### Post by Jason Spaceman on 2006-07-24
It sounds as though I'm having the same problem that [this guy did](http://www.ubuntuforums.org/showthread.php?t=185149).  He mentioned that he solved his problem though, by tinkering with some configuration utilites.  Unfortunately he doesn't say what changes he made.  Stefanr, where are you?!

---

### Post by Jason Spaceman on 2006-07-25
An update, I manually assigned an IP address to my wifi port:

```
sudo ifconfig eth1 192.168.0.11
```

And I manually set a default gateway:

```
sudo route add default gw 192.168.0.1
```

And now my wireless card works, sort of:

```
snozzy@laptop:~$ ping ubuntuforums.org
PING ubuntuforums.org (82.211.81.186) 56(84) bytes of data.
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=1 ttl=44 time=122 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=2 ttl=44 time=121 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=3 ttl=44 time=121 ms
```

However if I bring down the card and bringing it back up again (using ifdown/ifup) I have to manually reset the laptop's  IP address and default gateway again.  I'd prefer to have DHCP provide all that info.

---

### Post by smolko on 2006-07-25
I have the same wireless card as Jason - ipw3945. My problem is, that I don't have any wifi router at home but I would like to test, whether my notebook is  ready to be used elsewhere (cafe, school...).
I've tried all commands from the first post. The outputs were the same, despite this one:
```
smolko@smolko-laptop:~$ sudo iwlist eth1 scan
eth1      No scan results
```

I guess something is wrong with my setup, so please have a look at it

```
smolko@smolko-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Powerha:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

sit0      no wireless extensions.
```

Thanks a lot

---

### Post by Jason Spaceman on 2006-07-25
I think I may have solved the problem.  I edited /etc/network/interfaces and added a 'gateway 192.168.0.1' entry below my wifi card info:

```
# Wireless network interface
auto eth1
iface eth1 inet dhcp
gateway 192.168.0.1
```

I also added an entry for eth1 to /etc/iftab:

```
eth1 mac 00:13:02:1F:CE:1D arp 1
```

Although I'm not sure editing /etc/iftab is really necessary.  

I then edited my /etc/wpa_supplicant/wpa_supplicant.conf file:

```
network={
        ssid="Boozin_and_Pranks_11g"
        proto=WPA
        key_mgmt=WPA-PSK
        #psk="my password in plain text"
        psk=ThatPre-SharedKeyHexThingeeGeneratedByWpa_passphrase
}
```

And I started the wpasupplicant with:

```
sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dwext -w
```

And the wpasupplicant connected me to my access point:

```
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:0f:b5:92:d3:ad (SSID='Boozin_and_Pranks_11g' freq=0 MHz)
Associated with 00:0f:b5:92:d3:ad
WPA: Key negotiation completed with 00:0f:b5:92:d3:ad [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:0f:b5:92:d3:ad completed (auth)
```

And then I got an IP address from my router:

```
snozzy@ubuntulaptop:/etc/network/if-pre-up.d$sudo dhclient eth1
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:13:02:1f:ce:1d
Sending on   LPF/eth1/00:13:02:1f:ce:1d
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.6 -- renewal in 150457 seconds.
```

And after that I was connected.  I'm pretty sure I did everything correctly.  If I forgot a step then somebody let me know.

Also, what is the best way to automate all of the above?  There is a thread [here](https://help.ubuntu.com/community/WifiDocs/WPAHowTo), but it looks like parts of it are deprecated and aren't necessary in Dapper.

---

### Post by Jason Spaceman on 2006-07-26
Hmmmm, now it doesn't work.  When I boot Ubuntu back up the 'gateway' entry I added to /etc/network/interfaces is gone.  It should read:

```
# Wireless network interface
auto eth1
iface eth1 inet dhcp
gateway 192.168.0.1
pre-up /sbin/wpa_supplicant -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dwext -Bw
post-down killall -q wpa_supplicant
```

But after rebooting it reads:

```
# Wireless network interface
auto eth1
iface eth1 inet dhcp
pre-up /sbin/wpa_supplicant -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf -Dwext -Bw
post-down killall -q wpa_supplicant
```

How do I get the 'gateway 192.168.0.1' entry to stay?

---

### Post by jakamo on 2006-07-26
Try looking at the linux forum in notebookforums.
There's a couple people there who have gotten the
ipw 3945 adaptors to work out of the box. (with
ubuntu 6.06)
I'm looking to get a new laptop with linux only
as the os, but am nervous about trying to configure it
on my own; since I've never done that kind of thing
before, it sounds like it could be a daunting task. 
But after reading your post and a couple others,
I'm considering having emperor linux setting evth.
up for me. I've been using Linux for awhile, but
only in a school setting, so my experience in setting
things up is not very much.

---

### Post by ahallubuntu on 2006-07-26
I installed Ubuntu Dapper Drake (6.06) on my Dell E1505/6400 laptop over the weekend.  It has the Intel 3945 in it.  Although I was pleasantly surprised that the wireless card was detected and working right out of the box without doing anything, after the install I realized it wasn't a very friendly interface; I had to go into the network config each time I wanted to change to a different network (going from home to coffee shops etc.).  

So I installed something that most people use called Network Manager - a windows-like Gui WiFi connection tool that adds a little icon to the toolbar and lets you monitor/change the network.  But THIS didn't work out of the box!  It couldn't detect my wireless card even though the card was already working and connected to a network!  I spent over an hour Googling to figure that out but now it does work pretty well.  The only real problem I have with it is in the case of repeaters/multiple access points with the same SSID.  In one office setting, where all the Windows and Mac computers work just fine in this setting, my laptop with Ubuntu kept dropping the network, constantly.  I assumed it had to do with the multiple APs; I'll see if I can disconnect one of them to test out that theory.

My only other real problem at this moment is getting the laptop to hibernate and come out successfully, but I think that may be because my swap partition isn't big enough - so I may have to wipe it and completely re-install Ubuntu!

If you are having trouble with the 3945, I do have to ask:  did you boot the Desktop cd in "live" mode first to see if the wireless card is detected immediately, as mine is?  I wound up having an issue doing the install from the Desktop CD; Grub install failed at the end.  I wound up re-installing from the Alternate CD and that worked better.

---

### Post by Gamebeavis on 2006-07-26
Ok, I also have the same card, and basicaly the same laptop "e1505". I am having a similar problem. Funny thing is, I actualy got SOOOO #*$*#$ with my original wifi card (the Broadcom 1390) after about a month of trying to get it to work, going through forums, posts, old blogs etc. I actualy went on Ebay and bought this card because I found a forum that said it worked out of the box. Well, yes and no. Kubuntu does recognize the card, but 2 problems exist. 1. My wifi light dosnt stay constant, it blinks, like a Nic card sending data, when I was using XP it simply stayed lit, when on. Not sure if that is a problem or not. 2. Even using knetworkmanager I can "see" the networks, but when I try to connect it hangs up on the "configuring" adapter step. I dont think its getting an IP address. I already have the linux-restricted-modules-686 installed, as well as 2 different kerenels, 23, and 26, but neither make a diff. Now what??

---

### Post by Jason Spaceman on 2006-07-27
Ubuntu seems to detect my wifi card, and load the proper modules, drivers, etc.  And I can associate it with my access point.   But I'm just unable to get an IP address from my router.  Whenever I type 'sudo dhclient eth1' I get:

```
snozzy@ubuntulaptop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:13:02:1f:ce:1d
Sending on   LPF/eth1/00:13:02:1f:ce:1d
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
Trying recorded lease 192.168.0.6
```

It never receives a DHCP offer from my router and uses a recorded lease.  The recorded lease doesn't work, I can't ping anything on my LAN.

I thought I fixed the problem by adding the entry 'gateway 192.168.0.1' (my router's IP address) to /etc/network/interfaces.
But that didn't seem to fix it, as that entry gets erased when I reboot Ubuntu.

---

### Post by Jason Spaceman on 2006-07-27
OK, I had it working again but then it stopped working.  I can associate with my access point using wpa_supplicant, I can get an IP address from my router using 'dhclient'; but I still can't ping anything on my LAN, nor can I resolve hostnames, etc.  I'm not sure why, as /etc/resolv.conf looks fine, and my wired ethernet (eth0) works fine; but the wireless doesn't, even when it gets an IP address.

Is there some issue with Ubuntu and DNS?

---

### Post by NewDisciple on 2006-07-27
I had a similar problem on my Dell E1705.  I discovered that the IP address had changed and I did not know what it was.  I was using a cheapo Belkin 54G router.  Last week excessive heat finished it off so I bought a Linksys router and after hooking it up I had my wireless up and running in about a minute.  I am also using 686-smp.  So if all else fail don't rule out a router problem.

---

### Post by Jason Spaceman on 2006-07-29
Just for the record, I installed a beta copy of Edgy Eft (Ubuntu 6.10) and I get the same problem.  I can associate with my AP, I can get an IP address from my router; but I can't ping anything on the network nor get any internet connectivity.

Could the problem be with the ipw3945 driver?  Something not compiled in the kernel that should be there?

---

### Post by Gamebeavis on 2006-07-31
Ok, I found this websight

[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

It seems to have some instructions about getting this thing up and running. But I must admit I am a little scared to try it myself for fear of #%$#ing up my system. If anyone is willing to give it a shot and let me know how it went, please by all means.

---

### Post by pixel34 on 2006-08-05
I was having a similar problem. My wifi worked for weeks then simply didn't exist. My settings for the intel wifi controller in my dell 1505 magically disappeared. It happened after my computer hibernated. I got an error that eth1 didnt exist when I tried to 'ifconfig eth1'

An interesting thing I found when inspecting the /var/log/syslog

Aug  5 09:44:04 localhost gnome-power-manager: Hibernating computer because the DBUS method Hibernate() was invoked

I reinstalled the gnome-power-manager package and my problem went away! I can now use my eth1 wi-fi connection. I am not sure if the hibernation was the cause but I do know this worked for me. 

Let me know if it worked for you!

---

### Post by lalus on 2007-06-07
I had the same problem with ipw2200 and ipw3945. The solution found with g was to install a lower version of wpasupplicant (0.5.5 is ok) 

I don't know if ubuntu has a lower version of this package. 

See [http://packages.debian.org/cgi-bin/search_packages.pl?keywords=wpasupplicant&searchon=names&subword=1&version=all&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=wpasupplicant&searchon=names&subword=1&version=all&release=all)

---

