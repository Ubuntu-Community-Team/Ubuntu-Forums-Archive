---
title: "n00b+ubunto=NO WIRELESS...help?"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by hoboken on 2007-05-24
hey there guys. I just installed FF on my laptop (LG LS50, for the record) and it works fantastically.

Except the wireless internet.

lspci in the terminal tells me I have this: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04). I've googled and DAFS, promise, but everything just completely confuses me. Downloaded wifi-radar, but there's no connect button. I tried. See? So is there any hope? Go easy, it's my first day with linux.

Any help for the poor little newb..?;)

---

### Post by hoboken on 2007-05-25
Bump. Anyone help?

iwconfig gets me this:

eth1      no wireless extensions.

eth0      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:16 dBm   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by hoboken on 2007-05-25
anyone?

---

### Post by handaxe on 2007-05-25
No promises...

```
cat /proc/modules | grep ipw
```

Is the driver loaded?

HA

---

### Post by handaxe on 2007-05-25
More info here

[http://ubuntuforums.org/showthread.php?t=444093](http://ubuntuforums.org/showthread.php?t=444093)

[http://ubuntuforums.org/showthread.php?t=422789](http://ubuntuforums.org/showthread.php?t=422789)

Should be enough info to get you going.  Pay attention to what chili555 writes.

HA

---

### Post by hoboken on 2007-05-25
Hey Handaxe, thanks for taking the time to reply. Your code (where do you learn all these codes, anyway? lol) gave me this back:

ipw2100 72244 0 - Live 0xcfb49000
ieee80211 34760 1 ipw2100, Live 0xcfb28000

What's the diagnosis?

edit: I'll check the links out. Cheers.

---

### Post by handaxe on 2007-05-25
The driver is loaded so the initial condition for success is met.

The links should then help as the issues read similarly to yours.

HA

---

### Post by hoboken on 2007-05-25
Handaxe... I'm afraid nothing is working. Been following this page's instructions: [http://www.debianadmin.com/enable-wp...ntu-linux.html](http://www.debianadmin.com/enable-wp...ntu-linux.html)
And I can click on the network icon in the taskbar to drop down all the networks. I can see mine. I click on it, and it requests a wireless network key. The password we have for this network is "putisimamadre", so no hexadecimal stuff... I need to put in a WEP 128 bit passphrase..? It doesn't work. It takes the key, correct or not, thinks for a bit, then sends out the same request for a key again. The problem may lie in the etc/network/interfaces file. It says in the guide to "Comment out everything other than &#8220;lo&#8221; entries in that file and save the file", but I didn't know that comment out meant to put a # by it, so I deleted the first bits by mistake. They were already #'d, so no harm done..? What is left in the file is this:

auto lo
iface lo inet loopback

Which seems a bit iffy. So, it seems like this is my problem. Can anyone give me any ideas as to what I need to put in this file to get things working?

*sigh* If I can't get this working, it's back to windows...

---

### Post by MeeMaw on 2007-05-25
No, not the passphrase.... the actual hexidecimal number - it  looks like 9dd0f2224jj...... or something similar (if it's 128 bit it's 26 digits long.) Try that and see what you get.....

Don't give up!!!! (Especially to go back to Windows!!!!)   
I'm a n00b myself and I got mine running.   ;)

---

### Post by hoboken on 2007-05-25
Ah. And how do I get that? To be honest, I didn't even know I had one :p

Thanks for the encouragement, MeeMaw! I'll keep trying, and ubuntu is fantastic, just slightly lame without wireless...

---

### Post by hoboken on 2007-05-25
Oh, and I forgot to mention that I don't think the issue is with the passcode (well, maybe, seeing as I don´t know the hex one), because I can´t connect to "open" networks, either!

Thanks, guys.

edit: found this page. [http://ipw2100.sourceforge.net/INSTALL](http://ipw2100.sourceforge.net/INSTALL) it seems to concern my issue, but I sadly cannot understand a word.

Is it always this hard to get wireless working in linux?

---

### Post by hoboken on 2007-05-25
Bump. I'm using the NDIS wrapper. I found the windows drivers for my card. Good idea?

Ohy yeah, and will it work if I install Dapper Drake? What about PCLOS?

---

### Post by handaxe on 2007-05-25
Hi,

I have no personal experience of this card, first off.

Secondly, there do seem to be issues with Feisty and some wireless cards, so it is possible that dapper or even Edgy might do you better. And no reason not to try Ndiswrapper tho' the ipw2100 drivers have been part of the linux kernel since 2.6.14.

One thing, if you are back to trying the linux driver module you can ```
sudo dmesg | grep ipw2100
``` to see if there are any errors relating to the loading of the firmware.

HA

---

### Post by hoboken on 2007-05-27
FIXED.

I'm such a moron, it could have worked from the start...

Turns out that instead of entering a 128 bit passphrase, I had to enter a 64 bit ASCII code. Strange, as the wireless password is actually a phrase, but there you go.

Thanks for all your help, HA and MM!

---

### Post by Go99an on 2007-05-27
Hi Guys,

Another noob with WiFi problems. I have been trying for over a week to get wifi working and this thread seemed to be similar to my problem. I have installed KWiFiManager and when I try to enable the wifi, nothing happens.

Here is a list of the results of several of the tests/ commands
duncan@Go99U:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"GoggyNet"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

duncan@Go99U:~$ sudo lshw -C network
Password:
  *-network:0
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:9e:e9:58
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100b                                     t 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=                                     3.72 duplex=full firmware=5705-v3.16 ip=192.168.0.3 latency=32 link=yes mingnt=6                                     4 multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:faff0000-faffffff irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:35:e4:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmw                                     are=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 multicast=yes w                                     ireless=unassociated
       resources: iomemory:fafef000-fafeffff irq:5
duncan@Go99U:~$
duncan@Go99U:~$ sudo dmesg | grep ipw2100
[   18.408000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   18.408000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   18.604000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
duncan@Go99U:~$


Can anyone point me in the right direction please?
Many Thanks,
Duncan.

---

### Post by handaxe on 2007-05-27
```
sudo iwconfig eth1

sudo iwlist eth1 scan
```

Note the use of sudo before iwconfig.  That will reveal the encryption key you are sending, which it will not without root privileges.

I am betting an encryption / passkey-phrase problem.

HA

---

