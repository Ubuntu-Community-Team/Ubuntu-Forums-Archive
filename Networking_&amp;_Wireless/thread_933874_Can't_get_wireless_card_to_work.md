---
title: "Can't get wireless card to work"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by jpete on 2008-09-29
Any help would be greatly appreciated.

I am trying to use madwifi with my Linksys WMP110 pci card.

I can get it to install the module, modprobe shows ath_pci is installed, but I can't get anything to work after that. I am following the how to the madwifi site.

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo#LoadingtheMadWifiModule](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo#LoadingtheMadWifiModule)

I had tried to use ndiswrapper but that didn't seem to work either.

This is really making want to pitch Linux and go back to Windows so if someone can help, I'd really appreciate it.

---

### Post by pytheas22 on 2008-09-30
Sorry no one responded till now.  If you could please open a terminal, run the following commands and post the output here, I'll try to find instructions on getting your card working:
```

lshw -C Network
lspci -nn
uname -m
dmesg | grep -e ath -e wlan
```

madwifi is going through a lot of changes lately (switching to ath5k/ath9k) that make it confusing to understand which version you need to install, but with the above information I'll look it up and give you instructions.

---

### Post by jpete on 2008-09-30
Thanks for the help. Here are the results.

lshw -C Network
```
jeff@jeff-desktop:~$ sudo lshw -C Network
[sudo] password for jeff:
  *-network:0 UNCLAIMED
       description: Network controller
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d4:8e:9a:36
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
```

lspci -nn
```
jeff@jeff-desktop:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:0282]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:1282]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:2282]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:3282]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:4282]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. K8T800Pro Host Bridge [1106:7282]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188]
00:0e.0 Network controller [0280]: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter [168c:0023] (rev 01)
00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV34 [GeForce FX 5500] [10de:0326] (rev a1)
```

uname -m
```
x86_64
```

dmesg | grep -e ath -e wlan didn't return any result.(???)

---

### Post by pytheas22 on 2008-09-30
I think (according to [this thread]("http://forums.opensuse.org/network-internet/wireless/391991-atheros-wireless-device-not-yet-supported.html")) that your card will work using madwifi (ath_pci), but needs a later version than the one that ships with Ubuntu 8.04 (support for your wireless card seems to have been added in August, but Ubuntu 8.04 was released in April, and uses the version of madwifi available then).  So you need to compile the latest madwifi release from source.

In [this thread]("http://ubuntuforums.org/showthread.php?t=798485") there's a script and instructions that will allow you to compile the latest madwifi very easily.  Please try following them and let us know the results.

If after running that script things still don't work, please post the output (in the following order) of:
```

modinfo ath_pci
sudo modprobe ath_pci
lshw -C Network
```

---

### Post by jpete on 2008-09-30
Thanks! It seems to have advanced things along. Is there someplace I need to put in a security key, or something?

Here is the output you were looking for.
modinfo ath_pci
```
jeff@jeff-desktop:~/WiFi/madwifi-0.9.4$ modinfo ath_pci
filename:       /lib/modules/2.6.24-19-generic/net/ath_pci.ko
license:        Dual BSD/GPL
version:        svn r3867
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     616AE27CB2B255045A8CB61
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-19-generic SMP mod_unload
parm:           beacon_cal:int
parm:           countrycode:Override default country code.  Default is 0. (int)
parm:           maxvaps:Maximum VAPs.  Default is 4. (int)
parm:           outdoor:Enable/disable outdoor use.  Default is 0. (int)
parm:           xchanmode:Enable/disable extended channel mode. (int)
parm:           rfkill:Enable/disable RFKILL capability.  Default is 0. (int)
parm:           hal_tpc:Disables manual per-packet transmit power control and lets this be managed by the HAL.  Default is OFF. (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           intmit:Enable interference mitigation by default.  Default is 0. (int)
parm:           ath_debug:Load-time driver debug output enable (int)
parm:           ieee80211_debug:Load-time 802.11 debug output enable (int)
```

sudo modprobe ath_pci doesn't return much except a bunch of stray entries I made while trying to unblacklist the ath_pci module. :D One of these days, I'll ask you how to get them out of there! :D

lshw -C Network
```
jeff@jeff-desktop:~/WiFi/madwifi-0.9.4$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wifi0
       version: 01
       serial: 00:1e:e5:fb:5a:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d4:8e:9a:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.2 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
```

It looks like it picked up the wireless card. I am using KWiFiManager/KDE3 to try to pick up the wifi signal without any luck yet.  Is there something else I need to use or do?

I seriously want to thank you again. I've been pulling my hair out all weekend trying to get this to go. I was just about ready to uninstall the OS and do a fresh install. Something I hated doing with Windows and was really disappointed that I was going to have to start doing it with Linux too.

---

### Post by jpete on 2008-09-30
Well, it was working after I did what you said but after a reboot, it seems like it's off again. Is this script something that has to be done every time?

lshw -C Network returns "unclaimed" again for network 0.

---

### Post by jpete on 2008-09-30
Well, I got it back. I followed that thread you posted to the end and there was another script which loads the original script every time.

But I'm back to my original problem. It shows the wifi connection, but I still can't connect.

Any suggestions?

---

### Post by pytheas22 on 2008-10-01
Were you ever able to connect and load web pages?  Can you connect if you turn encryption off on your router?

Also, what do you mean when you say, "It shows the wifi connection, but I still can't connect?"  Can you see wireless networks but just not manage to connect to them?  Or do you just mean that a wireless interface is detected, but you can't even see networks with it?

Please also do a fresh reboot, then (before doing anything else) post the output of:
```

lsmod | grep ath
sudo modprobe ath_pci
lshw -C Network
sudo iwlist scan
```

In any case, I think you are a lot closer now than you were before...at least the interface is definitely being recognized.

---

### Post by jpete on 2008-10-01
> **pytheas22 said:**
> Were you ever able to connect and load web pages?  Can you connect if you turn encryption off on your router?

Also, what do you mean when you say, "It shows the wifi connection, but I still can't connect?"  Can you see wireless networks but just not manage to connect to them?  Or do you just mean that a wireless interface is detected, but you can't even see networks with it?

Please also do a fresh reboot, then (before doing anything else) post the output of:
```

lsmod | grep ath
sudo modprobe ath_pci
lshw -C Network
sudo iwlist scan
```

In any case, I think you are a lot closer now than you were before...at least the interface is definitely being recognized.

What I mean is that KWiFiManager used to show a big red "X" and say "Disabled". Now the icon is of a computer and says "Out of range" even though the router is sitting on top of the computer. I have Verizon FiOS so I don't know how to turn encryption off.

Here is the output you requested.

```
jeff@jeff-desktop:~$ lsmod | grep ath
ath_rate_sample        17024  1
ath_pci               251072  0
wlan                  253472  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               280320  3 ath_rate_sample,ath_pci
```

sudo modprobe ath_pci doesn't return anything except some bad entries I got in there while trying to unblacklist the ath_pci module. I don't know how to get the bad entries out.

```
jeff@jeff-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wifi0
       version: 01
       serial: 00:1e:e5:fb:5a:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d4:8e:9a:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.2 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
```

```
jeff@jeff-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:18:01:EF:D2:70
                    ESSID:"VLLZ2"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-41 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101020003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f010100200000
```

Thanks again for all the help.

---

### Post by pytheas22 on 2008-10-01
It looks like things should work, so I'm not positive why you can't get online.  Let's try connecting manually from the command-line to see if that helps.  If you run:
```

sudo iwconfig ath0 mode managed channel 1 essid "VLLZ2" key "your WEP key in quotes without colons"
sudo dhclient ath0
```

what happens?

Also, I assume that your network uses WEP encryption (and from the information you posted, it seems like it does).  If it uses WPA, please let me know, as the commands need to connect are very different in that case.  If you use WEP, your encryption key should look something like 'A4F6G7E2D1'  If you use WPA, your key would more likely be a dictionary word.

You may also want to try installing [wicd]("http://wicd.sourceforge.net") and using it to connect; many people have better luck with it.

---

### Post by jpete on 2008-10-01
I have no idea what my WEP key is. Where would I get that information?

---

### Post by pytheas22 on 2008-10-01
It may say on the outside of the router what the key is, but probably not; otherwise, it should have told you what it is somewhere in the documentation that came with the router.  Otherwise, take a look at [this page]("http://answers.yahoo.com/question/index?qid=20080602114503AARabuu"), which explains one way of finding it.  Another way is to look at the registry key at Software\Microsoft\WZCSVC\Parameters\Interfaces, or use [this utility]("http://www.wirelessdefence.org/Contents/Aircrack-ng_WinWzcook.htm") to automatically extract it.

---

### Post by jpete on 2008-10-01
I found the WEP key on the bottom of the router. The first command you gave where I entered the key didn't return a result.

Thia is what I got with the second command.

```
jeff@jeff-desktop:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1e:e5:fb:5a:38
Sending on   LPF/ath0/00:1e:e5:fb:5a:38
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by jpete on 2008-10-01
After doing that, I checked KWiFiManager and it is showing 4 green bars and claims the signal is "ultimate"

Don't know what happened there???  Maybe I should "cut the cord" and see what I get?

---

### Post by jpete on 2008-10-01
I unplugged the ethernet cable and I still had internet access so there was a bit of success.  But I rebooted and now I lost the wifi connection again.

---

### Post by jpete on 2008-10-01
I went back and did the previous commands that worked and now they don't seem to work.

This is getting nuts....

---

### Post by jpete on 2008-10-01
I downloade wicd. I think I got it installed right but I can't get it to start up. I get an icon on the task bar, and a little antenna icon bounces by the mouse pointer for a minute but then it disappears.

---

### Post by pytheas22 on 2008-10-01
So you were definitely online via the wireless at some point?  That's a good sign; at least we know that your card will actually work--so it's probably not a driver issue, but just a problem with trying to make the connection.

Try starting wicd by typing:
```

sudo /opt/wicd/gui.py
```

or:
```

sudo /opt/wicd/tray.py
```

Does it start then?

---

### Post by jpete on 2008-10-02
Nothing with either of them.

```
jeff@jeff-desktop:~/WiFi/wicd-1.5.3$ sudo /opt/wicd/gui.py
sudo: /opt/wicd/gui.py: command not found
jeff@jeff-desktop:~/WiFi/wicd-1.5.3$ sudo /opt/wicd/tray.py
sudo: /opt/wicd/tray.py: command not found
```

But I was able to get a GUI like this.

```
jeff@jeff-desktop:~/WiFi/wicd-1.5.3/scripts$ sudo wicd-client
Loading...
Attempting to connect tray to daemon...
Success.
Done.
```

What settings do you think I should use? I set the wifi connection to "WEP(passphrase)" and entered the WEP key I found. What is the "WPA supplicant driver" or doesn't that have anything to do with me?

After all that, it still says it can't find a network.

---

### Post by pytheas22 on 2008-10-02
At least you got a GUI now...not sure what was wrong before.

The wpa_supplicant stuff only applies to WPA connections, so you can ignore that.

In wicd, there's really not much that you should have to change from the default settings.  Just be sure that in preferences, the interface that it's configured for is 'ath0'.  You should also be using the 'wext' supplicant driver, although I don't think that even matters for WEP.

You say that you got online before using the command line.  Can you reproduce that?  These were the commands, I think:
```

sudo iwconfig ath0 mode managed channel 1 essid "VLLZ2" key "your WEP key in quotes without colons"
sudo dhclient ath0
```

---

### Post by jpete on 2008-10-02
This is what I got.
```
jeff@jeff-desktop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 6363
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1e:e5:fb:5a:38
Sending on   LPF/ath0/00:1e:e5:fb:5a:38
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

But when I check KWiFiManager, I have a good signal. But I know when I reboot, it will be gone.

---

### Post by pytheas22 on 2008-10-03
> But when I check KWiFiManager, I have a good signal. But I know when I reboot, it will be gone.

But can you actually load web pages at that point using the wireless connection (and if so, are you sure you're not working offline)?  I haven't used KDE in a long time and don't remember how KWiFiManager reports things, so I'm not sure whether a good signal means that you're actually connected to the Internet with an IP address, or something else.

---

### Post by jpete on 2008-10-03
Well, I was able to unplug the ethernet cable and go to a few different sites. But that was the one and only time.

---

### Post by pytheas22 on 2008-10-03
If you have the time and resources, could you please try burning an Intrepid live CD (you can download the ISO [here]("http://releases.ubuntu.com/releases/kubuntu/8.10/")), booting to it and seeing if you can connect to your wireless network there?  I can't really think of anything else to try...

---

### Post by jpete on 2008-10-05
I burned the 64 bit version of Intrepid but all I got was a half pink/half scrambled desktop. It went through and seemed like it was going to boot but maybe the display drivers aren't right?

I am using a live CD of Kubuntu 8.04.1 64 bit right now. KNetworkManager doesn't recognize the wireless card. Maybe I should try something else?

Would a 32 bit OS be better? I'm just wondering if the 64 bit drivers or lack of, is the issue.

I'll try the alternate version .iso of Intrepid and see what happens with that.

---

### Post by jpete on 2008-10-05
Just tried the x86 version of Intrepid and I got the same thing as the AMD64 version. It seems to load normally but instead of a desktop, I get a half pink, half scrambled screen.

On the "alternate" version of the AMD64 version, it doesn't give the option of running from the CD. Just to install it. I didn't really want to do that, especially with a beta version.

8.04.1 looks nice, but I don't know if it will help my situation.

---

### Post by pytheas22 on 2008-10-05
Both Kubuntu and Ubuntu 8.10 have the same underlying kernel and wireless drivers, so if you tested Kubuntu 8.10 and your wireless card didn't work there, Ubuntu 8.10 won't be any better.  You could try using the 32-bit version of Kubuntu 8.10, but it's very unlikely that you'll have any better luck there with regards to the wireless card.

At this point, there's only one last thing that I can think of to try, which is to use ndiswrapper, which will allow you to drive your card using Windows drivers.  Please let me know if you have the 64-bit Windows driver for your card, either on a CD, on an installation of Windows or from somewhere on the Internet.  Once we locate this driver, we can get ndiswrapper configured.

---

### Post by jpete on 2008-10-06
On the CD provided with the wifi card had an "x64" folder in the "Drivers/Vista" folder. The only thing I see in there that might work is "netathrx.inf". The other files are "athrx.sys" and "athrextx.cat". These same files appear in the "Drivers/Vista/x86" folder. In the XP folder, there are totally different files.

I have tried ndiswrapper but there is nothing saying I did it right. :D

---

### Post by pytheas22 on 2008-10-06
The netathrx.inf, athrx.sys and athrextx.cat files are probably the ones you need.  Please copy them to your desktop on Ubuntu, then run these commands to get them installed in ndiswrapper:
```

sudo apt-get install ndiswrapper*
cd ~/Desktop
sudo ndiswrapper -i netathrx.inf
echo ndiswrapper | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modprobe.d/blacklist
echo ath9k | sudo tee -a /etc/modprobe.d/blacklist
```

Then reboot.  If the wireless doesn't work, please post the output of:
```

lshw -C Network
ndiswrapper -l
dmesg | grep -e ndis -e wlan
lsmod | grep -e ath -e ndis
```

I've heard of some people having issues with ndiswrapper and your chipset on 64-bit (32-bit is supposed to work fine), so if you already installed ndiswrapper, that could be what's wrong.  Or maybe some other part of the configuration was just not right.  Either way, in a worst case, your card should work on 32-bit Linux using ndiswrapper with no problem.

---

### Post by jpete on 2008-10-06
Here is the output you asked about. Needless to say, I still don't have wifi.

```
jeff@jeff-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wifi0
       version: 01
       serial: 00:1e:e5:fb:5a:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d4:8e:9a:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
```

This seems odd as I did the install as you described.

```
jeff@jeff-desktop:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
```

dmesg | grep -e ndis -e wlan doesn't return any result.

```
jeff@jeff-desktop:~$ lsmod | grep -e ath -e ndis
ath_rate_sample        17024  1
ath_pci               251072  0
wlan                  253472  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               280320  3 ath_rate_sample,ath_pci
```

---

### Post by pytheas22 on 2008-10-06
hmmmm, please try running these commands:

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
cd ~/Desktop
sudo ndiswrapper -i netathrx.inf
echo ndiswrapper | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modprobe.d/blacklist
echo ath9k | sudo tee -a /etc/modprobe.d/blacklist
```

Then reboot, and post the output of these commands (in this order):
```

ndiswrapper -l
uname -m
lshw -C Network
sudo modprobe -r ath_pci ath9k ndiswrapper
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
sudo iwlist scan
```

---

### Post by jpete on 2008-10-06
I got stuck here

> sudo ndiswrapper -i netathrx.inf

```
jeff@jeff-desktop:~/Desktop$ sudo ndiswrapper -i netathrx.inf
couldn't open netathrx.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
```

---

### Post by pytheas22 on 2008-10-06
Was the netathrx.inf file on your desktop when you ran that command?  It looks like it wasn't.  Please make sure it's there (along with the other two files from the Windows driver), and that you're cd'd to your desktop (which you do by typing 'cd ~/Desktop'), and the command should work.

---

### Post by jpete on 2008-10-07
> **pytheas22 said:**
> Was the netathrx.inf file on your desktop when you ran that command?  It looks like it wasn't.  Please make sure it's there (along with the other two files from the Windows driver), and that you're cd'd to your desktop (which you do by typing 'cd ~/Desktop'), and the command should work.

Files are definitely there

```
jeff@jeff-desktop:~/Desktop$ dir
athrextx.cat  kubuntu-8.04.1-desktop-amd64.iso     netathrx.inf      rar
athrx.sys     kubuntu-8.10-beta-desktop-amd64.iso  radF91FC.tmp.pdf  rarlinux-x64-3.8.b4.tar.gz
```

I'll try again.

---

### Post by jpete on 2008-10-07
Now I get a message saying it's already installed!?

```
jeff@jeff-desktop:~/Desktop$ sudo ndiswrapper -i netathrx.inf
[sudo] password for jeff:
driver netathrx is already installed
jeff@jeff-desktop:~/Desktop$ echo ndiswrapper | sudo tee -a /etc/modules
ndiswrapper
jeff@jeff-desktop:~/Desktop$ echo ath_pci | sudo tee -a /etc/modprobe.d/blacklist
ath_pci
jeff@jeff-desktop:~/Desktop$ echo ath9k | sudo tee -a /etc/modprobe.d/blacklist
ath9k
```

---

### Post by jpete on 2008-10-07
Here's the output after reboot. I warn you, my blacklist file is a little messed up. I was trying to edit it and got a bunch of info in there that I have no idea how to get out. :D

```
jeff@jeff-desktop:~$ ndiswrapper -l
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 44: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 45: ignoring bad line starting with 'C'
WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 49: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 50: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 51: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 52: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 53: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 54: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 55: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 56: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 57: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 58: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 59: ignoring bad line starting with 'C'
WARNING: /etc/modprobe.d/blacklist line 60: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 61: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 62: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 63: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 64: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 65: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 67: ignoring bad line starting with 'ath_pci'
WARNING: /etc/modprobe.d/blacklist line 68: ignoring bad line starting with 'ath9k'
WARNING: /etc/modprobe.d/blacklist line 69: ignoring bad line starting with 'ath_pci'
WARNING: /etc/modprobe.d/blacklist line 70: ignoring bad line starting with 'ath9k'
net5416 : driver installed
        device (168C:0023) present (alternate driver: ath_pci)
netathrx : invalid driver!
```

```
jeff@jeff-desktop:~$ uname -m
x86_64
```

```
jeff@jeff-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wifi0
       version: 01
       serial: 00:1e:e5:fb:5a:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d4:8e:9a:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
```

```
jeff@jeff-desktop:~$ sudo modprobe -r ath_pci ath9k ndiswrapper
[sudo] password for jeff:
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 44: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 45: ignoring bad line starting with 'C'
WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 49: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 50: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 51: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 52: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 53: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 54: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 55: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 56: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 57: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 58: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 59: ignoring bad line starting with 'C'
WARNING: /etc/modprobe.d/blacklist line 60: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 61: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 62: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 63: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 64: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 65: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 67: ignoring bad line starting with 'ath_pci'
WARNING: /etc/modprobe.d/blacklist line 68: ignoring bad line starting with 'ath9k'
WARNING: /etc/modprobe.d/blacklist line 69: ignoring bad line starting with 'ath_pci'
WARNING: /etc/modprobe.d/blacklist line 70: ignoring bad line starting with 'ath9k'
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 44: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 45: ignoring bad line starting with 'C'
WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 49: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 50: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 51: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 52: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 53: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 54: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 55: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 56: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 57: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 58: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 59: ignoring bad line starting with 'C'
WARNING: /etc/modprobe.d/blacklist line 60: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 61: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 62: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 63: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 64: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 65: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 67: ignoring bad line starting with 'ath_pci'
WARNING: /etc/modprobe.d/blacklist line 68: ignoring bad line starting with 'ath9k'
WARNING: /etc/modprobe.d/blacklist line 69: ignoring bad line starting with 'ath_pci'
WARNING: /etc/modprobe.d/blacklist line 70: ignoring bad line starting with 'ath9k'
FATAL: Module ath9k not found.
```

```
jeff@jeff-desktop:~$ sudo modprobe ndiswrapper
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 44: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 45: ignoring bad line starting with 'C'
WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 49: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 50: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 51: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 52: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 53: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 54: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 55: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 56: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 57: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 58: ignoring bad line starting with 'D'
WARNING: /etc/modprobe.d/blacklist line 59: ignoring bad line starting with 'C'
WARNING: /etc/modprobe.d/blacklist line 60: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 61: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 62: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 63: ignoring bad line starting with 'A'
WARNING: /etc/modprobe.d/blacklist line 64: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 65: ignoring bad line starting with 'B'
WARNING: /etc/modprobe.d/blacklist line 67: ignoring bad line starting with 'ath_pci'
WARNING: /etc/modprobe.d/blacklist line 68: ignoring bad line starting with 'ath9k'
WARNING: /etc/modprobe.d/blacklist line 69: ignoring bad line starting with 'ath_pci'
WARNING: /etc/modprobe.d/blacklist line 70: ignoring bad line starting with 'ath9k'
FATAL: Module ndiswrapper not found.
```

dmesg | grep -e ndis -e wlan returns no result. Nothing. Like it had no effect whatsoever.

```
jeff@jeff-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

Hope you can make heads or tails of this.  Thanks again.

---

### Post by pytheas22 on 2008-10-07
Yeah, your blacklist file seems pretty messed up.  I'm not sure that it's actually hurting anything, but try opening it by typing:
```

sudo gedit /etc/modprobe.d/blacklist
```

Then erase it all and change it to this, which is a clean Hardy blacklist file, with ath_pci and ath9k also blacklisted:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ath9k
blacklist ath_pci
```

Then save and close the file, and please run the following commands (again, in this order) and post their output:

```
sudo ndiswrapper -r netathrx
sudo modprobe -r ath9k ath_pci ndiswrapper
sudo modprobe ndiswrapper
lshw -C Network
dmesg | grep -e ndis -e wlan
```

---

### Post by jpete on 2008-10-07
Sorry, no dice.

```
jeff@jeff-desktop:~$ sudo gedit /etc/modprobe.d/blacklist
[sudo] password for jeff:
sudo: gedit: command not found
```

---

### Post by pytheas22 on 2008-10-07
Try replacing 'gedit' with 'kate' (sorry, I forgot that you were running KDE...gedit is the editor in Gnome; kate is for KDE).  Please make that substitution and run the rest of the commands from my last post, and post the output here.

---

### Post by jpete on 2008-10-07
I got it to edit using "sudo nano -w" so here's the output

sudo ndiswrapper -r netathrx didn't seem to do anything.

```
jeff@jeff-desktop:~$ sudo modprobe -r ath9k ath_pci ndiswrapper
FATAL: Module ath9k not found.
```

```
jeff@jeff-desktop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
```

```
jeff@jeff-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED
       description: Network controller
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=96
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d4:8e:9a:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
```

dmesg | grep -e ndis -e wlan still doesn't seem to do anything.

---

### Post by jpete on 2008-10-07
I went back and did all that other stuff again, so here's the output.

sudo ndiswrapper -r netathrx doesn't return any result.

```
jeff@jeff-desktop:~$ sudo modprobe -r ath9k ath_pci ndiswrapper
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'ath_pci'
WARNING: /etc/modprobe.d/blacklist line 44: ignoring bad line starting with 'ath9k'
FATAL: Module ath9k not found.
```

```
jeff@jeff-desktop:~$ sudo modprobe ndiswrapper
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'ath_pci'
WARNING: /etc/modprobe.d/blacklist line 44: ignoring bad line starting with 'ath9k'
FATAL: Module ndiswrapper not found.
```

```
jeff@jeff-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wifi0
       version: 01
       serial: 00:1e:e5:fb:5a:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=96 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d4:8e:9a:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
```

And, as usual, dmesg | grep -e ndis -e wlan still doesn't return a result.

---

### Post by pytheas22 on 2008-10-07
```
jeff@jeff-desktop:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
```

This is not good...there's something seriously wrong with your ndiswrapper installation if it thinks that the module doesn't exist.  I've seen this once before but after several days of trying to fix it, the only solution ended up being a reinstallation.

So at this point, the only good advice I can think of is to reinstall Ubuntu.  If you install 32-bit, I promise that we can get the wireless working quickly (64-bit might also work, depending on how much the Windows driver cooperates, but I'm not encouraged by what I've seen so far...I think ndiswrapper might not like the 64-bit Windows drivers that you have, and I can't find any other ones on the Internet), as I've done it before with the exact same card.

Otherwise, we can keep on working here to figure out what's wrong with ndiswrapper, although as I said, I'm not optimistic about succeeding.  But if you want to try, please post the output of:
```

locate ndiswrapper
```

Sorry this is not going smoothly at all, but thanks for remaining positive...

---

### Post by jpete on 2008-10-07
A reinstall wouldn't hurt my feelings. It would give me a chance(excuse) to go to 8.04.1 or 8.10, if it works.

Here is the output of the command

```
jeff@jeff-desktop:~$ locate ndiswrapper
/etc/ndiswrapper
/etc/modprobe.d/ndiswrapper
/etc/ndiswrapper/net5416
/etc/ndiswrapper/netathrx
/etc/ndiswrapper/net5416/168C:0023.5.conf
/etc/ndiswrapper/net5416/168C:0023:0072:1737.5.conf
/etc/ndiswrapper/net5416/net5416.inf
/etc/ndiswrapper/net5416/wmp110.sys
/home/jeff/.kde4/share/apps/RecentDocuments/ndiswrapper.desktop
/home/jeff/WiFi/ndiswrapper-1.50
/home/jeff/WiFi/ndiswrapper_1.50.orig.tar.gz
/home/jeff/WiFi/ndiswrapper-1.50/AUTHORS
/home/jeff/WiFi/ndiswrapper-1.50/ChangeLog
/home/jeff/WiFi/ndiswrapper-1.50/INSTALL
/home/jeff/WiFi/ndiswrapper-1.50/Makefile
/home/jeff/WiFi/ndiswrapper-1.50/README
/home/jeff/WiFi/ndiswrapper-1.50/driver
/home/jeff/WiFi/ndiswrapper-1.50/loadndisdriver.8
/home/jeff/WiFi/ndiswrapper-1.50/ndiswrapper.8
/home/jeff/WiFi/ndiswrapper-1.50/ndiswrapper.spec
/home/jeff/WiFi/ndiswrapper-1.50/utils
/home/jeff/WiFi/ndiswrapper-1.50/driver/.built-in.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.crt.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.hal.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.iw_ndis.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.loader.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.ndis.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.ndiswrapper.ko.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.ndiswrapper.mod.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.ndiswrapper.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.ntoskernel.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.ntoskernel_io.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.pe_linker.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.pnp.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.proc.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.rtl.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.usb.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.win2lin_stubs.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.wrapmem.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.wrapndis.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/.wrapper.o.cmd
/home/jeff/WiFi/ndiswrapper-1.50/driver/Makefile
/home/jeff/WiFi/ndiswrapper-1.50/driver/Module.symvers
/home/jeff/WiFi/ndiswrapper-1.50/driver/built-in.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/compat.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/crt.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/crt.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/crt_exports.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/divdi3.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/hal.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/hal.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/hal_exports.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/iw_ndis.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/iw_ndis.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/iw_ndis.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/lin2win.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/loader.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/loader.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/loader.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/longlong.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/ndis.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/ndis.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/ndis.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/ndis_exports.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/ndiswrapper.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/ndiswrapper.ko
/home/jeff/WiFi/ndiswrapper-1.50/driver/ndiswrapper.mod.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/ndiswrapper.mod.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/ndiswrapper.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/ntoskernel.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/ntoskernel.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/ntoskernel.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/ntoskernel_exports.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/ntoskernel_io.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/ntoskernel_io.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/ntoskernel_io_exports.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/pe_linker.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/pe_linker.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/pe_linker.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/pnp.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/pnp.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/pnp.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/proc.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/proc.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/rtl.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/rtl.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/rtl_exports.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/usb.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/usb.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/usb.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/usb_exports.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/win2lin_stubs.S
/home/jeff/WiFi/ndiswrapper-1.50/driver/win2lin_stubs.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/win2lin_stubs.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/winnt_types.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/workqueue.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/wrapmem.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/wrapmem.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/wrapmem.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/wrapndis.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/wrapndis.h
/home/jeff/WiFi/ndiswrapper-1.50/driver/wrapndis.o
/home/jeff/WiFi/ndiswrapper-1.50/driver/wrapper.c
/home/jeff/WiFi/ndiswrapper-1.50/driver/wrapper.o
/home/jeff/WiFi/ndiswrapper-1.50/utils/Makefile
/home/jeff/WiFi/ndiswrapper-1.50/utils/loadndisdriver
/home/jeff/WiFi/ndiswrapper-1.50/utils/loadndisdriver.c
/home/jeff/WiFi/ndiswrapper-1.50/utils/ndiswrapper
/home/jeff/WiFi/ndiswrapper-1.50/utils/ndiswrapper-buginfo
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper
/usr/sbin/ndiswrapper
/usr/sbin/ndiswrapper-1.9
/usr/share/doc/ndiswrapper-common
/usr/share/doc/ndiswrapper-utils-1.9
/usr/share/doc/ndiswrapper-common/AUTHORS
/usr/share/doc/ndiswrapper-common/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-common/README
/usr/share/doc/ndiswrapper-common/README.Debian
/usr/share/doc/ndiswrapper-common/changelog.Debian.gz
/usr/share/doc/ndiswrapper-common/copyright
/usr/share/doc/ndiswrapper-utils-1.9/AUTHORS
/usr/share/doc/ndiswrapper-utils-1.9/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-utils-1.9/README
/usr/share/doc/ndiswrapper-utils-1.9/changelog.Debian.gz
/usr/share/doc/ndiswrapper-utils-1.9/copyright
/usr/share/man/man8/ndiswrapper-1.9.8.gz
/usr/share/man/man8/ndiswrapper.8
/usr/share/man/man8/ndiswrapper.8.gz
/var/cache/apt/archives/ndiswrapper-common_1.50-1ubuntu1_all.deb
/var/cache/apt/archives/ndiswrapper-utils-1.9_1.50-1ubuntu1_amd64.deb
/var/lib/dpkg/info/ndiswrapper-common.list
/var/lib/dpkg/info/ndiswrapper-common.md5sums
/var/lib/dpkg/info/ndiswrapper-utils-1.9.list
/var/lib/dpkg/info/ndiswrapper-utils-1.9.md5sums
```

---

### Post by pytheas22 on 2008-10-07
It might work to insert the ndiswrapper module by using the command:
```

sudo insmod /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
```

which would give it the full and exact path to the module.  Hopefully it would not have trouble finding it then.

But as I said, the simplest/fastest solution will likely to be to do a fresh install of Ubuntu (8.10 should be stable enough to install now if you like), then install ndiswrapper there (and again, 32-bit would be easier than 64, although if you take a lot of pride in your 64-bit processor, I can understand if you want to try for ndiswrapper on 64-bit).

---

### Post by jpete on 2008-10-08
Looks like I'll try 8.10(32 bit this time)

```
jeff@jeff-desktop:~$ sudo insmod /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
[sudo] password for jeff:
insmod: error inserting '/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': -1 Invalid module format
```

---

### Post by jpete on 2008-10-08
Well, I'm running now on the 8.04.1 CD. Is there anyway to try the wifi before I switch?

---

### Post by pytheas22 on 2008-10-08
Sure, if you want to test getting the wireless going on the live CD before installing it on the real system (a good idea), run these commands (you will need to be connected via ethernet first):
```

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://burnthesorbonne.com/files/168c_0023_win32.tar.gz
tar -xzvf 168c*
cd 168c*
sudo ndiswrapper -i net5416.inf
sudo modprobe -r ath_pci ath9k ndiswrapper
sudo modprobe ndiswrapper
```

Now you should be able to connect.  Please let me know.  If not and you want to try to troubleshoot it in the live session, please post the output of:
```

dmesg | grep -e ndis -e wlan
lshw -C Network
```

---

### Post by jpete on 2008-10-08
Don't know if it's because of the live cd or what but this is what I get.

```
ubuntu@ubuntu:~$ http://burnthesorbonne.com/files/168c_0023_win32.tar.gz
bash: http://burnthesorbonne.com/files/168c_0023_win32.tar.gz: No such file or directory
```

---

### Post by pytheas22 on 2008-10-08
Sorry, sorry, my fault again...typo in the command (should have been a 'wget' in front of that URL).  I fixed it now; please try following the instructions in my last post again.

---

### Post by jpete on 2008-10-09
Almost made it.....

```
ubuntu@ubuntu:~/168c_0023_win32$ sudo modprobe -r ath_pci ath9k ndiswrapper
FATAL: Module ath9k not found.
```

I kept going and got this.

```
ubuntu@ubuntu:~/168c_0023_win32$ dmesg | grep -e ndis -e wlan
[  626.908690] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  626.928923] ndiswrapper: driver net5416 (,05/26/2006,6.0.0.180) loaded
[  627.378563] ndiswrapper: using IRQ 20
[  627.591720] wlan0: ethernet device 00:1e:e5:fb:5a:38 using serialized NDIS driver: net5416, version: 0x60000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0023.5.conf
[  627.712527] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  627.713006] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  627.727642] usbcore: registered new interface driver ndiswrapper
```

```
ubuntu@ubuntu:~/168c_0023_win32$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wlan0
       version: 01
       serial: 00:1e:e5:fb:5a:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,05/26/2006,6.0.0.180 latency=128 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d4:8e:9a:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
```

---

### Post by Vander Jagt on 2008-10-09
I am not an Ubuntu user, but I have several of these cards, and I would like to help as much as I can to make it work.

I am somewhat surprised that support for this chip is so poor since it's the chip used in the now extremely popular Acer 5315 laptop.  (A surprisingly high quality laptop often used as a promotional item for big box stores like MicroCenter and Wal-Mart, often around $350.  The hardware really is top-notch, but the low price and the company's history leads people to search for something wrong with it.)

I'm a SuSE user, and there was a SuSE user who made it work by recompiling the kernel with 4k stacks disabled, rebuilding and reinstalling ndiswrapper 1.47, and installing the driver "as normal".  Unfortunately I can't find his more detailed instructions, and attempting to do just what I described doesn't seem to be enough.

Also, the very newest Madwifi driver, 0.10.5.6, is reported to work with this chip.  0.9.4 does see the chip, and doing iwlist wlan0 scan does show some wireless networks, but it doesn't seem to actually transmit anything.  I'm about to try the 0.10.5.6 driver, but I don't expect it to work, and I do plan to watch this forum to come up with a solution...

This card seems to be VERY hard to make work, but it DOES work, so I'm determined to find out how to do it, and I want to help as much as I can.

---

### Post by Vander Jagt on 2008-10-09
Again, new encouraging results but no success.  )-:  Now using ath_pci again, the wireless device is called ath0.  It doesn't seem to connect manually, and since iwlist reports that the device is unable to scan, I would doubt that the device is transmitting anything.

I'm now trying madwifi-trunk-r3867.

---

### Post by pytheas22 on 2008-10-09
jpete,

Could you connect after running those commands from your last post?  It looks like everything should be working (for once).  The error about ath9k not being found can be ignored.

Vander Jagt,

If you end up having success with this card under madwifi, please let us know.  I couldn't find anyone on Google who had gotten it to work in any distribution, but maybe that's changed by now.  I don't think that recompiling the kernel is going to be a real solution for many people though...I have no idea how to compile a kernel myself and I've used Linux for years.

---

### Post by Vander Jagt on 2008-10-10
pytheas22,

Sure, I'll gladly report any successes I have to this forum.  To update my previous post, I must add that the newest snapshot didn't even make a wireless device at all.  )-:

I sorta get the feeling that the existence of the madwifi, ath5k, and ath9k drivers has had some inadvertent effect of splitting development effort.  On the other hand, the fact that Atheros themselves have released their drivers under the ISC license means that the native driver should be very thorough sometime soon (such as by 2.6.28).  I'm not waiting that long, so instead I'm spending days trying to make it work.  (-:

By the way pytheas22, I lived in Baltimore for years!  I lived there in the early 90's, before the Panamanian gangs.  Now I live in Winchester, VA, so I hardly visit anymore.  *stands on his roof and waves eastward*

As for the wireless driver, my current step is that I have downloaded the git checkout for the wireless-testing development.  This is, as I understand it, a section of kernel development with emphasis on wireless drivers.  It's basically kernel 2.6.27-rc8.  -IF- it works, I'll let you know more about how to do it yourself, but unfortunately it's a process that takes some time.  Also, if it works, it should be rather distribution-independent, but since you'd be compiling it from scratch you would have to recompile any other separate kernel drivers, too, so it could mean a bit of extra work.

---

### Post by Vander Jagt on 2008-10-10
Well, I can't get the new wireless-testing kernel to work properly with my hard drive controller, so I installed the latest 2.6.27-rc7 kernel from Factory (the development build service), which also sees the chip right and also scans wireless networks but still doesn't transmit.

So now, I'm going to try ndiswrapper once more the way that the other user said it -should- work.

For what it's worth, I can't even get Windows wireless working on these laptops unless it's a 32-bit OS.

---

### Post by Vander Jagt on 2008-10-10
Oh my freaking gourd!  I'm sitting on the porch in front of the shop and have no wires connected to this laptop!

I knew I would eventually, but what is really surprising is that it wasn't through ndiswrapper, which other users said would work.  It wasn't through the new ath_pci (madwifi) snapshot, which is reported as functional.  It wasn't through ath9k, the new open source driver from Atheros.  Nope, it's through the ath5k driver, which specifically said it wouldn't work with this chip!

Here's what's different: I have the 2.6.27-rc7 kernel running, but I'm not convinced that it's necessary.  I currently have ath5k blacklisted, ath_pci and ath9k are NOT blacklisted.  (Heh, go figure.  Again, I'm not convinced that has anything to do with it.)  I then "rmmod ath_pci" and "modprobe ath5k".  However, what seems to actually be the important factor is that I turned OFF NetworkManager (switched to ifup, also disabled ipv6), rebooted, then ran "iwconfig wlan0 essid winchesterpc" and then "dhclient wlan0".

I will probably reinstall SuSE 11 on my computer and see how few steps I can use to make it work.

---

### Post by jpete on 2008-10-10
> **pytheas22 said:**
> 
Now you should be able to connect.  Please let me know.  If not and you want to try to troubleshoot it in the live session, please post the output of:
```

dmesg | grep -e ndis -e wlan
lshw -C Network
```

I went to "K-menu-->System Settings-->Network Settings" and put in the essid and WEP key and it doesn't seem like KNetworkManager sees it.

```
ubuntu@ubuntu:~/168c_0023_win32$ dmesg | grep -e ndis -e wlan
[  592.068895] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  592.088229] ndiswrapper: driver net5416 (,05/26/2006,6.0.0.180) loaded
[  592.536578] ndiswrapper: using IRQ 20
[  592.746884] wlan0: ethernet device 00:1e:e5:fb:5a:38 using serialized NDIS driver: net5416, version: 0x60000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0023.5.conf
[  592.864621] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  592.865120] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  592.877921] usbcore: registered new interface driver ndiswrapper
[  815.652475] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  836.370439] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1015.628850] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1047.460006] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1047.560182] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```


```
ubuntu@ubuntu:~/168c_0023_win32$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wlan0
       version: 01
       serial: 00:1e:e5:fb:5a:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5416 driverversion=1.52+,05/26/2006,6.0.0.180 latency=128 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d4:8e:9a:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
```

---

### Post by pytheas22 on 2008-10-11
Vander Jagt: glad you got it working!  Thanks for reporting back.

jpete: can you connect if you use wicd?  I think you had installed it at some point but I guess you are still using KNetworkManager?  Also, try re-enabling Roaming Mode; it may help.

Sorry for not responding sooner--I've been away all day--but I should be able to provide better help tomorrow.
> 
By the way pytheas22, I lived in Baltimore for years! I lived there in the early 90's, before the Panamanian gangs. Now I live in Winchester, VA, so I hardly visit anymore. *stands on his roof and waves eastward*

I only moved here a little more than a month ago, to start graduate school at JHU.  It can sure be a bit scary in the wrong neighborhoods :) although maybe I'll get used to it over time...

---

### Post by jpete on 2008-10-11
I'll have to reinstall wicd when I'm using the live cd. I'l be away all day today myself. hate to do it on a Saturday, but 10 hours of overtime at work is too good to pass up.

---

### Post by Vander Jagt on 2008-10-11
> **pytheas22 said:**
> Vander Jagt: glad you got it working!  Thanks for reporting back.

jpete: can you connect if you use wicd?  I think you had installed it at some point but I guess you are still using KNetworkManager?  Also, try re-enabling Roaming Mode; it may help.

Sorry for not responding sooner--I've been away all day--but I should be able to provide better help tomorrow.


I only moved here a little more than a month ago, to start graduate school at JHU.  It can sure be a bit scary in the wrong neighborhoods :) although maybe I'll get used to it over time...

I would have had SuSE 11 reinstalled on my laptop by now, except there was a big power outage in Nuremberg, Germany, and the power company got everything back up except Novell's office last night.  They left that for this morning.

When I was there last, Baltimore kept some small-town charm, with everyone greeting everyone else.  We locked our doors and traveled in groups, but we always smiled and asked "How's it going?" of perfect strangers.

---

### Post by Vander Jagt on 2008-10-11
I'm not trying to convert Ubuntu users to SuSE.  I'm just saying how I finally got it to work, since the steps will probably be simple with Ubuntu, and if you have access to SuSE 11 64-bit then you can use it as a regression test for this driver.

Simplest steps for SuSE 11 64-bit:

Install, activate extra repositories, and run update.  I installed the package "madwifi", but I don't think it's necessary.  Then, add Factory repository, update kernel to 2.6.27-12.1 (A.K.A. 2.6.27-rc7).  Reboot.  Connect using KNetworkManager.

Aside from using the 2.6.27 kernel from Factory, it was extremely straightforward.  I didn't even need to set up any network devices in YaST (the SuSE administration tool).

According to DistroWatch.com the newest kernel available for Ubuntu is in Intrepid and is 2.6.27.  If possible, I would try that kernel and see if the built-in ath5k driver is working right out-of-the-box.  Also remember that if you have pressed/switched the WiFi radio switch (if you have one) then it may stay off after rebooting.

Good luck!  Tell me how it goes!

---

### Post by pytheas22 on 2008-10-11
jpete:

I think you already tried using the Intrepid live CD and it didn't work out-of-the-box, right?  Intrepid does use the 2.6.27, which Vander Jagt says worked for him, so the support should be there, and maybe burning a more recent live CD would make a difference for you--they rebuild the kernel package frequently before the stable release and one build may work with your wireless whereas another doesn't.

Or, of course, you could give Suse a shot.  I prefer Ubuntu because it's more community-based and I trust Canonical more than Novell, but to each his own.

---

### Post by Vander Jagt on 2008-10-11
> **pytheas22 said:**
> jpete:

I think you already tried using the Intrepid live CD and it didn't work out-of-the-box, right?  Intrepid does use the 2.6.27, which Vander Jagt says worked for him, so the support should be there, and maybe burning a more recent live CD would make a difference for you--they rebuild the kernel package frequently before the stable release and one build may work with your wireless whereas another doesn't.

Or, of course, you could give Suse a shot.  I prefer Ubuntu because it's more community-based and I trust Canonical more than Novell, but to each his own.

It could well be a -very- recent fix in the kernel, since it didn't work the first time yet worked the second and each time after.

I'm downloading Ubuntu Intrepid to try it out.  I'll let you know my results.

Also, if you don't have any success, and if you don't have anything else to try, you can see if SuSE 11 + the Factory repository (available from the [www.opensuse.org](www.opensuse.org) site, or tell me if you need help) version of 2.6.27 kernel works for you.  At least if that works, then you'll know it's just a matter of getting the newest ath5k module.

---

### Post by jpete on 2008-10-12
Should I be concerned about this?

> Due to an unresolved bug in the Linux kernel included in Alpha 6, it should not be used on Intel ethernet hardware handled by the e1000e driver (Intel GigE). Doing so may render your network hardware permanently inoperable. 

And can I just do this?

> To upgrade from Ubuntu 8.04, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions. 

Or would a fresh install be a better bet to "undo" all the things we've done?

---

### Post by pytheas22 on 2008-10-12
You don't have an Intel ethernet card (yours is VIA), so no worries about the e1000e issue.

You can upgrade using the update manager--it will give you the new kernel containing the new wireless stack.  But it would be better to do a clean install of Intrepid from CD if you can; it depends on how willing you are to wipe out your current system.

---

### Post by jpete on 2008-10-13
Alright, I'm running on the  Ubuntu 8.10 live DVD. I used the x86 version instead of the 64bit.

I ran the "Test Hardware" wizard and it recognized the wireless card so that's a plus. I don't have time right now to fool around with it, but is there anything I should do first?

Or is there something you want to look at?

Thanks to both of you again.

---

### Post by pytheas22 on 2008-10-13
I'm not familiar with the "Test Hardware" wizard (maybe it's a new Intrepid thing) but I suppose it would help for us to see the output in Intrepid of:
```

lshw -C Network
sudo iwlist scan
modinfo ath_pci
modinfo ath9k
```

in order to figure out which driver it's using, etc.

---

### Post by jpete on 2008-10-13
```
ubuntu@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: wmaster0
       version: 01
       serial: 00:1e:e5:fb:5a:38
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:13:d4:8e:9a:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a2:90:5e:2a:f1:1b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

```
ubuntu@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:01:EF:D2:70
                    ESSID:"VLLZ2"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=95/100  Signal level:-34 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000022206e9181
                    Extra: Last beacon: 100ms ago

pan0      Interface doesn't support scanning.
```

```
ubuntu@ubuntu:~$ modinfo ath_pci
filename:       /lib/modules/2.6.27-4-generic/volatile/ath_pci.ko
srcversion:     D3FD3BD11169A96DBCFF8DE
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.27-4-generic SMP mod_unload modversions 586 
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)
```

```
ubuntu@ubuntu:~$ modinfo ath9k
filename:       /lib/modules/2.6.27-4-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     40F3EA320C8A43465F21E95
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        mac80211
vermagic:       2.6.27-4-generic SMP mod_unload modversions 586
```

Hope that means something to you.

---

### Post by jpete on 2008-10-13
I tried the network connection wizard and it sees the router "VLLZ2" but when I put in the WEP key, it can't connect.

On an unrelated topic, the spellcheck on FireFox seems to work opposite. It underlines all the words, not just the misspelled ones.

---

### Post by pytheas22 on 2008-10-13
Please try turning encryption off on your router, reboot your router, then run the following commands and post the output:
```

sudo iwconfig wlan0 mode managed channel 11 essid "VLLZ2"
sudo dhclient wlan0
```

If you can't or really don't want to turn off security on your router, we can try other things, but right now I think that the above is the best thing to try (turning the security off would only be temporary to see if you can actually connect that way; if it works, we can figure out what's wrong with WEP).

Things do look better here than they did in Hardy.

As for the Firefox spellcheck issue, hopefully that will be worked out before October 30th...

---

### Post by jpete on 2008-10-13
I really don't know how to turn the security off. It's the router that I got with my Verizon FiOS so I don't know much about it. I can maybe call tech support and try to find an answer but I'm in the middle of moving right now so I don't have time to sit on the phone with them.

---

### Post by pytheas22 on 2008-10-13
That's alright.  The point of turning off encryption was to make it easier to connect manually from the command line, but we can still try to do that even with the WEP key.  To do so, you'd run a command like:
```

sudo iwconfig wlan0 mode managed channel 11 essid "VLLZ2" **key YOUR WEP KEY, WITHOUT COLONS, NOT IN QUOTES**
sudo dhclient wlan0
```

For example:
```

sudo iwconfig wlan0 mode managed channel 11 essid "VLLZ2" **key A1B2C3D4E5**
sudo dhclient wlan0
```

Obviously, substitute your WEP key into the command as needed.  Also, these commands assume that your WEP key is a standard hex key and that you use open authentication.  Most WEP keys are hex, meaning that they contain only the letters A-G combined with numbers.  If you're not sure what your key is, let me know.

If you use special authentication on your router or have an ASCII WEP key, you need to change the commands a bit to connect.  [This page]("http://ubuntuforums.org/showthread.php?t=571188") explains it all.

Please let me know the output of the commands above.

You can also try using wicd again (if you're not completely sick of installing it by now); it may make a difference on this new install.

---

### Post by jpete on 2008-10-13
I tried it a couple times with the same result. I changed the WEP key because I didn't think that is something I should post here. Don't know if it makes a difference though. Just paranoid I guess. :D

```
ubuntu@ubuntu:~$ sudo iwconfig wlan0 mode managed channel 11 essid "VLLZ2" key xxxxxxxxx
ubuntu@ubuntu:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 23051
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1e:e5:fb:5a:38
Sending on   LPF/wlan0/00:1e:e5:fb:5a:38
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by pytheas22 on 2008-10-13
hmmmm, that's not good that it still doesn't want to work.  Do you have better luck with wicd?

Also, your WEP key can be [cracked in a few minutes]("http://www.aircrack-ng.org/doku.php?id=simple_wep_crack") these days by anyone with a Linux machine and a decent wireless card, FYI :)

---

### Post by jpete on 2008-10-13
I tried to add wicd using Synaptic but I got this error.

```
Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Beta i386 (20081002)]/dists/intrepid/Release  Unable to find expected entry  main/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```

Not sure what that's all about.

---

### Post by pytheas22 on 2008-10-13
That error just means that it thinks your CD should be used as a repository but it can't find the CD or something...it's not serious.  If you added wicd to your /etc/apt/sources.list file and ran 'sudo apt-get update' (even if you got that error), you should now be able to type:
```

sudo apt-get install wicd
```

to install wicd.

You can also just download the [wicd .deb]("http://downloads.sourceforge.net/wicd/wicd_1.5.3_all.deb?modtime=1222631284&big_mirror=0") to your desktop and double-click it to install.  If it whines about Network Manager being installed but isn't smart enough to auto-uninstall it, you can manually remove NM first by using Synaptic or by typing:
```

sudo apt-get remove network-manager
```

---

### Post by jpete on 2008-10-13
No luck there.

```
ubuntu@ubuntu:~$ sudo apt-get install wicd
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ sudo apt-get remove network-manager
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by jpete on 2008-10-13
OK, I got wicd to install but even after putting the WEP key in, it just searches for a signal but never finds one.

---

### Post by pytheas22 on 2008-10-13
I read through the entire thread again to recall what we've already tried.  Unfortunately, I'm not sure that I have any more good suggestions.  I have written to Vander Jagt however to figure out exactly which driver and module version he's using to get this card working.  I've also found plenty of threads online saying that this card works variously with madwifi, ath9k and ndiswrapper (all of which we've tried, but without success), and moreover that it has been working at least since Ubuntu 7.10.  Checkout [this thread]("http://ubuntuforums.org/showthread.php?t=668272") and [this thread]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=915909") for instance.

I do wonder if the problem might be simply on your router's end.  Did you try rebooting it (just unplug it, wait a minute, then plug it in again)?  You could also try [resetting the router]("http://cbuck03.wordpress.com/2007/05/22/verizon-fios-default-login-trouble/")--if you do that, you will probably need to reconfigure your DSL connection, so make sure you know your DSL username and password; if you don't know it, ask Verizon.  This might do the trick, and is the only other thing I can think to try, because by all indications, your wireless card is detected and working now.

You could also simply try turning off the WEP key.  I know we had discussed this earlier today and a few days ago, but I don't think you ever tried, right?  It actually should not be hard to do if you have a FiOS router: if you open Firefox on a computer in your house that's connected to the Internet and put '192.168.1.1' in the address bar, you should be able to login to the router configuration page, where you can disable security.  If it asks you for a password, try 'admin' + 'password1' for username/password.

---

### Post by jpete on 2008-10-14
OK< I was able to turn WEP off. I'll have to go restart with the 8.10 live DVD later.  Thanks for that little tip on the routers settings.

---

### Post by jpete on 2008-10-14
I'm working now on the live dvd and I ran the wireless connection configuration wizard. Even though I turn WEP off in the router, I still put the WEP key in and after a few seconds, a box poped up and said "You are now connected to the wireless network" I haven't tried to unplug the ethernet cable yet. I've been here before and I'm nervous about being disappointed again. :D

Well, here goes......

---

### Post by jpete on 2008-10-14
Nope, no luck.

---

### Post by jpete on 2008-10-14
And, once again, I can't install wicd. I'm starting to see why everyone sucks it up and pays Bill Gates. :(

---

### Post by pytheas22 on 2008-10-14
Sorry to hear that it's still the same outcome...

When you're connected, what is the output of:
```

lshw -c Network
iwconfig
ifconfig
```

Also, did it prompt you to enter the WEP key even though security is disabled?  Or did you click 'Connect to other wireless network' or something and enter the WEP key explicitly?

And have you rebooted your router?

---

### Post by jpete on 2008-10-15
> **pytheas22 said:**
> Sorry to hear that it's still the same outcome...

When you're connected, what is the output of:
```

lshw -c Network
iwconfig
ifconfig
```

Also, did it prompt you to enter the WEP key even though security is disabled?  Or did you click 'Connect to other wireless network' or something and enter the WEP key explicitly?

And have you rebooted your router?

To enter the WEP key, I clicked on the icon for the network.  A box pops up showing the wired and wireless connections(2 each for some reason) I click on the wireless connection and a box pops up asking for the WEP key.

If there is some other way to do it, I haven't figured out how. I'll try rebooting the router. If I have time tonight, I'll call Verizon support. Now that I think about it, I added a DVR box and couldn't get it to work until Verizon renewed the lease on my router. Maybe we're bumping into the same problem?

---

### Post by pytheas22 on 2008-10-15
It's quite strange that it's still asking you for a WEP key even though you're sure that security is disabled on the router.  I haven't heard of that before--either your wireless drive/Network Manager is seriously messed up (which I don't think is the case based on all of the command-line output you've provided) or something weird is going on with the router.

I'm not personally familiar with FiOS routers, but it could well be the case that they won't accept a new device onto the network until you do something manually...

---

### Post by jpete on 2008-10-15
OK, I think he just told me I'm SOL. :D

Verizon doesn't support Linux so the best he could do for me was to tell me that if the "Wireless" light was on, then I should have a signal.

He claims that I might have some interference even though the router is sitting next to the computer.

I don't know what to do at this point. I wish I had another computer to try this on. I haven't ruled out the possibility that the wireless card is DOA.

---

### Post by pytheas22 on 2008-10-16
Yes, it would be nice to know if the wireless card works under any operating system.  I suppose you could install Windows to test, although that would be some work.

Your other option I guess is to buy a cheap wireless card.  You can get USB dongles for $20 that will be plug-and-play in Linux.

---

### Post by jpete on 2008-10-16
> **pytheas22 said:**
> Yes, it would be nice to know if the wireless card works under any operating system.  I suppose you could install Windows to test, although that would be some work.

Your other option I guess is to buy a cheap wireless card.  You can get USB dongles for $20 that will be plug-and-play in Linux.

Well, I'm wanting to do a dual boot. I have 2- 250G SATA drives so I was thinking of setting up an OS on each. Or use the SATA drives for the Windows and use my old 80G IDE drive for Linux.

Also, can you suggest a USB dongle that you think would work? I have to lose the money on the card, it was $60 or so but at this point, I'd just like to have the wifi working.

---

### Post by pytheas22 on 2008-10-16
Since you want to do a dual-boot, then you may as well install Windows and see if the wireless works there...

In terms of good wireless cards: I have [this one]("http://www.amazon.com/DWL-G122-Compact-Wireless-Adapter-802-11g/dp/B0002DQUHC/ref=sr_1_1?ie=UTF8&s=electronics&qid=1224201421&sr=8-1") (rev C1), which works well.  There's also a list [here]("http://www.amazon.com/DWL-G122-Compact-Wireless-Adapter-802-11g/dp/B0002DQUHC/ref=sr_1_1?ie=UTF8&s=electronics&qid=1224201421&sr=8-1") of recommended cards, including many USB ones.

However, a big problem when purchasing wireless cards is that sometimes manufacturers change the insides of the card (the 'chipset', which is the only part that matters to Linux) without changing the name of the device.  Consequently, you might find two wireless cards that look identical and that have the exact same names on the store shelf, but are actually completely different as far as Linux is concerned.

For example, the device I have, the DWL-G122, comes in four revisions: A1, B1, C1 and D1.  C1 (my version) and I think B1 have Ralink chipsets, which means out-of-the-box Linux support (because Ralink has GPL'd drivers and has cooperated with Linux developers for a long time).  A1 and D1 I think have completely different chipsets (or so I've read) and may or may not work so painlessly with Linux.

Unfortunately, the box or website where you buy wireless cards rarely specifies which chipset is inside (I'm not sure which DWL-G122 Amazon would ship to you if you bought from the link I provided above, because it doesn't say anywhere which revision # it is)--so your best bet is to contact the vendor and request the information, or buy from somewhere where you can return the product easily if it turns out not to work well with Linux (of course, I've never met a wireless card that I couldn't get working in Linux if I tried hard enough, but I'd imagine you'd just as soon return it if it doesn't 'just work' for you).

---

### Post by jpete on 2008-10-18
> **pytheas22 said:**
> Since you want to do a dual-boot, then you may as well install Windows and see if the wireless works there...

In terms of good wireless cards: I have [this one]("http://www.amazon.com/DWL-G122-Compact-Wireless-Adapter-802-11g/dp/B0002DQUHC/ref=sr_1_1?ie=UTF8&s=electronics&qid=1224201421&sr=8-1") (rev C1), which works well.  There's also a list [here]("http://www.amazon.com/DWL-G122-Compact-Wireless-Adapter-802-11g/dp/B0002DQUHC/ref=sr_1_1?ie=UTF8&s=electronics&qid=1224201421&sr=8-1") of recommended cards, including many USB ones.

However, a big problem when purchasing wireless cards is that sometimes manufacturers change the insides of the card (the 'chipset', which is the only part that matters to Linux) without changing the name of the device.  Consequently, you might find two wireless cards that look identical and that have the exact same names on the store shelf, but are actually completely different as far as Linux is concerned.

For example, the device I have, the DWL-G122, comes in four revisions: A1, B1, C1 and D1.  C1 (my version) and I think B1 have Ralink chipsets, which means out-of-the-box Linux support (because Ralink has GPL'd drivers and has cooperated with Linux developers for a long time).  A1 and D1 I think have completely different chipsets (or so I've read) and may or may not work so painlessly with Linux.

Unfortunately, the box or website where you buy wireless cards rarely specifies which chipset is inside (I'm not sure which DWL-G122 Amazon would ship to you if you bought from the link I provided above, because it doesn't say anywhere which revision # it is)--so your best bet is to contact the vendor and request the information, or buy from somewhere where you can return the product easily if it turns out not to work well with Linux (of course, I've never met a wireless card that I couldn't get working in Linux if I tried hard enough, but I'd imagine you'd just as soon return it if it doesn't 'just work' for you).

Well, we can't get this one working so I'm a little gunshy.  I may wait until after Halloween and the "official" 8.10 release. Then I'll make a decision on which way I'm going. The problem with XP is that it won't recognize the SATA drives. And I haven't had much luck with slipstreaming, and I don't have a floppy drive on this system so it's your basic PITA.

As soon as I get a minute, I'll get all this done.  

For now, I'll say thank you again for all your help.

---

