---
title: "wired connection not working"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by Olivia22 on 2011-03-15
Hello,
i am very new to Ubuntu. A friend set up my Laptop Aspire 1690 with Ubuntu 9.04
The wired network connection was working just fine. This morning there were several updates (from the Update Manager) and I accepted and they got installed.
And now my wired connection isn't working anymore.
It does say
Auto eth0 connection established but the internet is not working.
 
some more information:
```

[SIZE=2][FONT=Times New Roman]olivia@olivia-laptop:~$ cat /etc/lsb-release[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=2]DISTRIB_ID=Ubuntu[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]DISTRIB_RELEASE=9.04[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]DISTRIB_CODENAME=jaunty[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]DISTRIB_DESCRIPTION="Ubuntu 9.04"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]olivia@olivia-laptop:~$ uname -a[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]Linux olivia-laptop 2.6.28-19-generic #66-Ubuntu SMP Sat Oct 16 17:39:04 UTC 2010 i686 GNU/Linux[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]olivia@olivia-laptop:~$ lspci -nn |grep -i eth[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]06:08.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]olivia@olivia-laptop:~$ ifconfig[/SIZE][/FONT]
[SIZE=2][FONT=Times New Roman]eth1      Link encap:Ethernet  HWaddr 00:12:f0:c1:5d:95  [/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         Interrupt:17 Base address:0x6000 Memory:c8218000-c8218fff[/FONT][/SIZE]
 
[SIZE=2][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         RX packets:12 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         TX packets:12 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         RX bytes:888 (888.0 B)  TX bytes:888 (888.0 B)[/FONT][/SIZE]
 
[SIZE=2][FONT=Times New Roman]wlan0     Link encap:Ethernet  HWaddr 00:c0:9f:b3:1a:f7  [/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         inet addr:192.168.178.34  Bcast:192.168.178.255  Mask:255.255.255.0[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         inet6 addr: fe80::2c0:9fff:feb3:1af7/64 Scope:Link[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         RX packets:13 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         TX packets:32 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         RX bytes:2916 (2.9 KB)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[SIZE=2][FONT=Times New Roman]         Interrupt:16 Memory:c8200000-c8210000[/FONT][/SIZE]
 
[FONT=Times New Roman][SIZE=2]olivia@olivia-laptop:~$ lsmod[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]Module                  Size  Used by[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]binfmt_misc            16776  1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ppdev                  15620  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]radeon                342816  2[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]drm                    96424  3 radeon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]bridge                 56212  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]stp                    10500  1 bridge[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]bnep                   20224  2[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]input_polldev          11912  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]lp                     17156  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]parport                42220  2 ppdev,lp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]joydev                 18368  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]pcmcia                 44748  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_intel8x0           37532  3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_ac97_codec        112292  1 snd_intel8x0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ac97_bus                9856  1 snd_ac97_codec[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_pcm_oss            46336  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_mixer_oss          22656  1 snd_pcm_oss[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_seq_dummy          10756  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_seq_oss            37760  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_seq_midi           14336  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_rawmidi            29696  1 snd_seq_midi[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_timer              29704  2 snd_pcm,snd_seq[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]yenta_socket           32396  1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]iTCO_wdt               19108  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]iTCO_vendor_support    11652  1 iTCO_wdt[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]tifm_7xx1              13824  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ipw2200               151112  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]rsrc_nonstatic         19328  1 yenta_socket[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]intel_agp              34108  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]soundcore              15200  1 snd[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]psmouse                61972  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]tifm_core              15900  1 tifm_7xx1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ieee80211              38344  1 ipw2200[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ieee80211_crypt        13444  1 ieee80211[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ndiswrapper           193436  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]agpgart                42696  2 drm,intel_agp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]led_class              12036  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]snd_page_alloc         16904  2 snd_intel8x0,snd_pcm[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]pcspkr                 10496  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]serio_raw              13444  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]irda                  197308  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]crc_ccitt              10112  1 irda[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]video                  25872  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]output                 11008  1 video[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]usbhid                 42336  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ohci1394               38576  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ieee1394               94660  1 ohci1394[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]fbcon                  46112  0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]tileblit               10752  1 fbcon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]font                   16384  1 fbcon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]bitblit                13824  1 fbcon[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]softcursor              9984  1 bitblit[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]olivia@olivia-laptop:~$ cat /etc/network/interfaces[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]auto lo[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]iface lo inet loopback[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=2]olivia@olivia-laptop:~$ cat /etc/resolv.conf[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]# Generated by NetworkManager[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]nameserver 192.168.178.1[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]olivia@olivia-laptop:~$ cat /etc/hosts[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]127.0.0.1   localhost[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]127.0.1.1   olivia-laptop[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=2]# The following lines are desirable for IPv6 capable hosts[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]::1     localhost ip6-localhost ip6-loopback[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]fe00::0 ip6-localnet[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ff00::0 ip6-mcastprefix[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ff02::1 ip6-allnodes[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ff02::2 ip6-allrouters[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ff02::3 ip6-allhosts[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]olivia@olivia-laptop:~$ sudo route -n[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]Kernel IP routing table[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]192.168.178.0   0.0.0.0         255.255.255.0   U     1      0        0 wlan0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 wlan0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]olivia@olivia-laptop:~$ ping -c 5 www.ubuntu-forum.de[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]ping: unknown host www.ubuntu-forum.de[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=2]olivia@olivia-laptop:~$[/SIZE][/FONT]
 

```
 
 
It is probably not a very hard problem, but I just have no idea what to do...
Can anyone help??

---

### Post by wishyjr on 2011-03-15
looking at your info, it looks like the wireless adapter has an IP address assigned. 

How does your network manager look? if you click on the network icon in the top-right corner, what does the drop-down menu display? (i'm working on the assumption that you're running a generic ubuntu desktop theme)

---

### Post by Olivia22 on 2011-03-15
Hello wishyjr,
thanks for helping me!
 
I made a screenshot.
The strange thing is that I didn't change anything but letting the Update Manager install the recommended files...

---

### Post by Eiji Takanaka on 2011-03-15
Hi Oliivia,

One thing that jumped out at me was that the ifconfig showed eth1 as wired connection,

but in your settings it shows eth0.

Perhaps this might be a reason its not functioning correctly?

---

### Post by Olivia22 on 2011-03-15
HI Eiji Takanaka,
 
i was wondering bout that too, but since i have no clue on how things work in ubuntu I assumed it must be right:confused:
 
Can u help me how to change that?!

---

### Post by Eiji Takanaka on 2011-03-15
I can try i've never experienced that problem though....hmm what about if you try...

sudo ifconfig eth1 down

and then

sudo ifconfig eth0 up

see if that helps.....

---

### Post by Olivia22 on 2011-03-15
the first command works
when i type: sudo ifconfig eth0 up     it shows:
eth0: ERROR while getting interface flags: No such device

---

### Post by smurphy_it on 2011-03-15
what happens with an

```
sudo ifconfig eth1 up
```

Post the contents of "ifconfig" afterwords please.

---

### Post by Olivia22 on 2011-03-15
```

[FONT=Times New Roman][SIZE=3]olivia@olivia-laptop:~$ ifconfig[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]eth1      Link encap:Ethernet  HWaddr 00:12:f0:c1:5d:95  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Interrupt:17 Base address:0x2000 Memory:c8218000-c8218fff[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:4 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]olivia@olivia-laptop:~$[/SIZE][/FONT]

```

---

### Post by Eiji Takanaka on 2011-03-15
hmm o.k so it certainly seems something as simple as a wrongly named network device.  It is strange how its suddenly seemed to switch from eth0 to eth1. Have you tried a reboot since updating the packages?

---

### Post by Olivia22 on 2011-03-15
just rebooted, still not working.
But now I cant establish the eth0 connection either:confused:

---

### Post by Eiji Takanaka on 2011-03-15
o.k so what do you get with an ifconfig now?

---

### Post by Olivia22 on 2011-03-15
```

[FONT=Times New Roman][SIZE=3]olivia@olivia-laptop:~$ ifconfig[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]eth1      Link encap:Ethernet  HWaddr 00:12:f0:c1:5d:95  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          Interrupt:17 Base address:0xc000 Memory:c8218000-c8218fff[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX packets:4 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]olivia@olivia-laptop:~$[/SIZE][/FONT]

```

---

### Post by Eiji Takanaka on 2011-03-15
so what exactly happens with the internet icon in network manager applet? Does it show as 'connected' but not allow any internet?

You've left the wireless interface down whilst attemnpting to connect to ethernet.

I know it sounds daft and im not sure if it would help but have you tried changing eth0 to eth1 in the edit connections tab? Might be a short term fix.

---

### Post by Eiji Takanaka on 2011-03-15
a couple minutes of research brought this up...


[http://ubuntuforums.org/showthread.php?t=771981](http://ubuntuforums.org/showthread.php?t=771981)

perhaps this thread might help with your situation. But i'd see if you can get away with the whole alter simpler things before changing the name of your network interface.

Is there anyway you can 'roll-back' the update?

I'm not aware of how to do this, but perhaps someone else on these forums might be more helpful...as i said to start i've never experienced the problem so any suggestions would probably only have limited potency. 

Hope this helps anyways ;)

---

### Post by Eiji Takanaka on 2011-03-15
if you do go down the threads route, make sure you make a list of all the nwtork settings first maybe :) as it does say you need to re-enter the variables again once the network interface is back up.

---

### Post by Olivia22 on 2011-03-15
i'm sorry, but would you help me once again?!
 
Thats the content in the  /etc/udev/rules.d/70-persistent-net.rules    file:
```

[FONT=Times New Roman][SIZE=3]# This file maintains persistent names for network interfaces.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# See udev(7) for syntax.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# Entries are automatically added by the 75-persistent-net-generator.rules[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]# file; however you are also free to add your own entries.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]# PCI device 0x14e4:0x169c (tg3)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:c0:9f:b3:1a:f7", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]# PCI device 0x8086:0x4220 (ipw2200)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:f0:c1:5d:95", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]# PCI device 0x14e4:0x169c (ndiswrapper)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:c0:9f:b3:1a:f7", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0[/SIZE][/FONT]

```
 
 
Do I just have to rename "eth0" to eth"1" ? and how can I do that with sudo?
Sorry, but i dont know the commands jet....
 
THANKS for the help so far!!

---

### Post by Olivia22 on 2011-03-15
I fuguered it out how to change those names with sudo.
But its still not working:(

---

### Post by Eiji Takanaka on 2011-03-15
o.k so your eth0 and eth1 are using a different mac address, which did you rename? if you renamed eth1 to eth0 you would probably have to erase the old eth0 entry. 

typing 'sudo nautilus' is a good way of getting a superuser gui shell with which to browse and rename any files that require superuser priviledges i find.

Before you make any severe changes it sometimes pays to back the file up so that you have something to return to should things go **** up.

---

### Post by Eiji Takanaka on 2011-03-15
i just checked my 70-persistent rules thingy on mine and it seems the macaddress for ether and wlan arent the same. Now i would think for some reason your wlan0 mac has been transcribed over your eth0 mac address resulting in a conflict. 

the mac you want to retain is more than likely the one ending 5d:95.

So i would suggest maybe (*disclaimer this is but a maybe)....eep actually hang on...

o.k so looking at your details you have two seperate drivers for eth1 and eth0 :- tg3 and ipw2200.

So we know you more than likely want the macaddress that is..

00:12:f0:c1:5d:95 as it is more than likely the hardwired mac address of your ethernet network interface. So that probably wants to be on the line of eth0 but the question is which PCI device line is the correct one...

Make a back up copy of the file....and then.........

---

### Post by Eiji Takanaka on 2011-03-15
[FONT=Times New Roman][SIZE=3]so try renaming the eth1 to eth0 and then deleting the previous eth0 entirely see if that helps. 

Back up the file first though! ;)
[/SIZE][/FONT][FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

---

### Post by Ozitraveller on 2011-03-15
Would it be worth install HardInfo to sort out the macaddresses before you change anything? :) Just a thought.

---

### Post by Eiji Takanaka on 2011-03-15
actually yeh that might be an idea, you need to find the hard macadress of your nic. 

run sudo lshw

see what that brings up, i think a quick check of mine suggests, ya can find the hard mac from there. 

good shout ozitraveller.

---

### Post by Ozitraveller on 2011-03-15
ifconfig -a | grep eth
sudo lshw -class network

---

### Post by smurphy_it on 2011-03-16
After issueing the "sudo ifconfig eth1 up" it appears that the interface came up no problem, but I don't see an ip.  Try this:

```
sudo dhclient eth1
```

---

### Post by Ozitraveller on 2011-03-19
Hi

I have similar problem on my nieces netbook.

Any ideas how to fix this?

aaa@aaa-laptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:23:4e:8e:38:6c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 00:60:64:10:99:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=192.168.1.4 link=yes multicast=yes

aaaa@aaaa-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:60:64:10:99:86  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::260:64ff:fe10:9986/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:785341 (785.3 KB)  TX bytes:164914 (164.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20816 (20.8 KB)  TX bytes:20816 (20.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4e:8e:38:6c  
          inet6 addr: fe80::223:4eff:fe8e:386c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:86 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6493 (6.4 KB)  TX bytes:4028 (4.0 KB)

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:64:73:70:1b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:23:4e:8e:38:6c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x0451:0x6060 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:60:64:10:99:86", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

---

### Post by Olivia22 on 2011-03-21
Hello,
 
sorry for responding that late. I had a friend come over and help me. The automatic update changed something with the kernel. He fixed it. Sorry, but I can't give a good explanation of the solution, I was kinda lost...
But Thanks anyway for the help! I am sure I'll come up with some more questions:p

---

