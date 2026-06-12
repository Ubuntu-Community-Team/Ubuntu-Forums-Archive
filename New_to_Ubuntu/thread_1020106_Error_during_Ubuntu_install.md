---
title: "Error during Ubuntu install"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by retskrad on 2008-12-23
First I tried to burn the Ubuntu 8.10 ISO to a DVD+RW disc at the fasteest speed. I then got an error while installing. I get an error that I should clean the disc, or hardware problems or I should Use the slowest speed.

Now I tried to burn it at the slowest speed (2.4x). Now I got an error again:



What should I do?

---

### Post by halitech on 2008-12-23
burn the iso on a cd-r instead of a dvd+rw

---

### Post by retskrad on 2008-12-23
I don't have cd-r... Why cant you install it with dvd+rw``?


Also , if you burn it to a cd, can you use cd-rw or cd+rw also?

---

### Post by halitech on 2008-12-23
rewritable drives seem to give issues and a dvd rewritable isnt the best source to try and use, still burning it too fast

---

### Post by retskrad on 2008-12-23
But what about if I get an error again while using cd-r.. then I must thorw it away... the error might be too slow speed or too fast

---

### Post by halitech on 2008-12-23
you should never get a message about burning too slow and if you burn it at 4x then you should be fine.

with the cost of cd-r, if you mess one up I'll send you the 23cents that its worth

---

### Post by retskrad on 2008-12-23
Man, I live in Sweden, they are very expensive here... So CD-R... What speed? usually the highest speed is 52X.

---

### Post by halitech on 2008-12-23
you aren't worried about the higest speed,  you want the lowest speed possible. Normally 4x is best

---

### Post by Duck2006 on 2008-12-23
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by retskrad on 2008-12-23
I tried burning the iso on a cd-r disc, but the lowest speed was 10x. I burned it and at 89 I get an error and bang! I gota throw the disc away, are you ******* kidding me?  Now I must buy a new cd-r.

If I install with wine, I get no internet in uubntu. Wtf is that?

---

### Post by halitech on 2008-12-24
WINE (WINE Is Not an Emulator) is not used to install. Do you mean WUBI?

If you can't seem to burn on, order one from shipit and they'll send it to you free.

---

### Post by retskrad on 2008-12-24
Yeah I mean wubi. Dang.. I have never had so many problems with an operation systemn before.. burning installing and all that.. although ubuntu is great, it causes many problems for me.. I have already ordered  one free cd a cpupkle of days ago. it will take months before it gets here...

---

### Post by halitech on 2008-12-24
it shouldn't take that long, I've ordered from them before and had it in less then a month (I'm in Canada)

---

### Post by retskrad on 2008-12-24
I will try to burn it again, with the slowest speed again. if that doesn't work, ill try with the fastest. if that doeasn't work, I gota wait for the CD. It's very strange. When I install it Wubi, I get no internet connection in ubuntu but I have it in windows. LAst time I tried to start it from the CD, I got internet working, but I didnt have the OS on my HDD.

It sucks mna, its christmas and every possible store is closed.. :(

---

### Post by halitech on 2008-12-24
is it wireless or wired? if it works in the live cd then it should work when its installed.

---

### Post by retskrad on 2008-12-24
It is Wired. When I install with ubuntu, I get no connection..

---

### Post by halitech on 2008-12-24
you don't have it installed at the moment do you?

---

### Post by retskrad on 2008-12-24
No, I formated the computer.. I got no files, nothing. Just firefox lol.

---

### Post by halitech on 2008-12-24
> **retskrad said:**
> No, I formated the computer.. I got no files, nothing. Just firefox lol.

what do you mean? ^^^

---

### Post by retskrad on 2008-12-24
I did a fresh windows install, no files, nothing left.

---

### Post by halitech on 2008-12-24
ok, wasn't sure what you meant by only firefox.

you could try to set up a dual boot with wubi and then we could try to get your internet going, if you are interested.

---

### Post by retskrad on 2008-12-24
I just tried to remove both windows xp and ubuntu. Then I installed ubuntu with my dvd disc that I burned ubuntu on, with slowest speed. Install went fine, but still internet isnt working....

I tried to use ubuntu direct from the CD, still no internet. I have tried from wubi before in windows to install ubuntu, still I get no internet... Whats going on?

---

### Post by halitech on 2008-12-24
are you or can you boot into ubuntu? if you can, open a terminal and post the output of
```
lspci
```and```
lshw-C network
```and```
ifconfig
```

if you are dual booting or need to copy the info to a thumbdrive to post it, use
```
> lspci.txt
``` etc to get text files you can copy to thumbdrive

---

### Post by retskrad on 2008-12-24
Ok man thanks for answearing. Don't go away, Ill do what you told me :)

1 sec!

---

### Post by retskrad on 2008-12-24
bump

---

### Post by halitech on 2008-12-24
I'm here, waiting for the info :)

---

### Post by retskrad on 2008-12-24
Man, "lshw-C network" doesnt work...

Its very wird.. now when I log into winodws, it says local disc "H" instead of C.

it says 60gb is free of 70gb stll I cant download anything?

I got another problem now.. I cant even start the desktop with live cd or even install it.. 

Everytime I use install or live cd, itt akes me to a brown screen with the cursor and nothing happens, then sometimes it gets blacka nd Is ee the desktop but not the whole desk, only the cursor and the background image.. wtf is wrong with ubutnu? 2 hours ago I could install it and now I cant...

---

### Post by halitech on 2008-12-24
sorry, it should have been
```
lshw -C network
```

hmmmm, sounds like something is going on with the partitions in windows

not sure why it was working and now its now

---

### Post by retskrad on 2008-12-24
Man I really appreciate your patience with me. Please stay around, Ill remove windows and try to install ubuntu again. Can you do that? :)

---

### Post by halitech on 2008-12-24
I'll be around off and on, almost supper time here so might take me a bit to get back to you

---

### Post by scorp123 on 2008-12-24
> **retskrad said:**
> I burned it and at 89 I get an error and bang! If I had to guess I'd say you have defective RAM.

> **retskrad said:**
>  I gota throw the disc away, are you ******* kidding me?  Now I must buy a new cd-r. Big deal :lolflag:

---

### Post by retskrad on 2008-12-24
Do you have MSN?

---

### Post by retskrad on 2008-12-24
i HAVE 760MB ram... before install and everything worked now it doesnt..

---

### Post by halitech on 2008-12-24
things can suddenly stop working, maybe try booting the live cd and run memtester and see what it tells you. give it 20-30 minutes at least

---

### Post by retskrad on 2008-12-24
Man I need more of your help !

Do you have MSN?

---

### Post by halitech on 2008-12-24
just post questions here, that way if I'm not around someone will be able to help you

---

### Post by retskrad on 2008-12-24
Man, nobody answears its jsut you, come on man... its way faster if we participate... what email program do you use?

---

### Post by scorp123 on 2008-12-24
> **retskrad said:**
> i HAVE 760MB ram...  Use the "Memory Test" from the Live CD.

I bet it's defective RAM. That's why uncompressing the kernel during boot fails and you get the error. I had that too on an older system.

---

### Post by scorp123 on 2008-12-24
> **retskrad said:**
> Man, nobody answears its jsut you  It's Christmas Eve ... and some of us have families and kids and other obligations ;)

---

### Post by theozzlives on 2008-12-24
After your memtest, if no bad memory try wiping your drive again. Install Windows on half of the drive, then install Ubuntu... choose "Guided, use free space". See how that does for you.

---

### Post by halitech on 2008-12-24
> **retskrad said:**
> Man, nobody answears its jsut you, come on man... its way faster if we participate... what email program do you use?

I use thunderbird

> **retskrad said:**
> Man I need more of your help !

Do you have MSN?

no I don't

> **scorp123 said:**
> It's Christmas Eve ... and some of us have families and kids and other obligations ;)

yeah, families and kids and mouths to feed and gifts to wrap and kids to put to bed and beer (or Glenfidditch) to drink :D

---

### Post by scorp123 on 2008-12-24
> **halitech said:**
> (or Glenfidditch) to drink :DI like Dalwhinnie ... :D

---

### Post by halitech on 2008-12-24
> **scorp123 said:**
> I like Dalwhinnie ... :D

can't say I've had it but after looking it up and finding its from the highlands of Scotland, I'm going to be looking it up :D

---

### Post by scorp123 on 2008-12-24
> **halitech said:**
> can't say I've had it but after looking it up and finding its from the highlands of Scotland, I'm going to be looking it up :D I like the 15 year old Dalwhinnie ... round smooth taste, almost like caramel, not too peaty, but still no too sweet, very pleasant stuff. 

[http://www.slowreview.com/index.php/Dalwhinnie-whisky/Page-2.html](http://www.slowreview.com/index.php/Dalwhinnie-whisky/Page-2.html)
[http://www.humiblog.com/great-drinks/dalwhinnie-15-year/](http://www.humiblog.com/great-drinks/dalwhinnie-15-year/)

---

### Post by halitech on 2008-12-24
> **scorp123 said:**
> I like the 15 year old Dalwhinnie ... round smooth taste, almost like caramel, not too peaty, but still no too sweet, very pleasant stuff. 

[http://www.slowreview.com/index.php/Dalwhinnie-whisky/Page-2.html](http://www.slowreview.com/index.php/Dalwhinnie-whisky/Page-2.html)
[http://www.humiblog.com/great-drinks/dalwhinnie-15-year/](http://www.humiblog.com/great-drinks/dalwhinnie-15-year/)

I'll look it up for New Years Eve, too bad the liquor stores are already closed tonight

---

### Post by retskrad on 2008-12-27
**[COLOR="Red"]I did what you told me,[/COLOR]**

> **halitech said:**
> are you or can you boot into ubuntu? if you can, open a terminal and post the output of
```
lspci
```and```
lshw-C network
```and```
ifconfig
```

if you are dual booting or need to copy the info to a thumbdrive to post it, use
```
> lspci.txt
``` etc to get text files you can copy to thumbdrive

**[COLOR="Red"]here is what I get in ubuntu:[/COLOR]**

> **[COLOR="Red"]admin2@ubuntu:~$ lspci[/COLOR]**
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
01:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
[COLOR="Red"]**admin2@ubuntu:~$ lshw -c network**[/COLOR]
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 10
       serial: 00:11:09:6c:cd:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:fa:b6:ef:51:06
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
**[COLOR="Red"]admin2@ubuntu:~$ ifconfig[/COLOR]**
eth0      Link encap:Ethernet  HWaddr 00:11:09:6c:cd:5e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17720 (17.7 KB)  TX bytes:17720 (17.7 KB)

admin2@ubuntu:~$ 



[COLOR="Red"][SIZE="6"]if you see this, halitech, please send me a PM.[/SIZE][/COLOR]

---

### Post by retskrad on 2008-12-27
bump

---

### Post by halitech on 2008-12-27
ok, from what I'm seeing here:
[color=red]02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)[/color]
you have a wired connection that should be working

[color=red]eth0 Link encap:Ethernet HWaddr 00:11:09:6c:cd:5e
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:23 Base address:0xa000 [/color]
but looks like its either not connected to a router/modem or the device did not give out an IP address

also looks like you have some other device (USB maybe?) that is not getting a driver installed
[color=red]*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: da:fa:b6:ef:51:06
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/color]
but is being seen as having network capabilites (maybe the firewire?)

---

### Post by retskrad on 2008-12-27
I'm having a usb cabel, its to my nokia phone always connected to the computer, but not to the phone. I also got anotherUSB, its my mouse.

But its weird, internet works in windows... what should I do?

---

### Post by halitech on 2008-12-27
> I'm having a usb cabel, its to my nokia phone always connected to the computer, but not to the phone.

so was the phone plugged in when you ran the commands?

> But its weird, internet works in windows..

how do you connect in windows? wireless or wired connection?

---

### Post by retskrad on 2008-12-27
itrs the same computer.. I don't know what its called.. when I start the computer, I can choose between ubuntu and windows. if I choose  ubuntu, it will log in to ubuntu OS, same with windows.

Yes, I had that usb cabel when I ran these comamnds...


[COLOR="Red"]**[Thanks fort aking your time to help me man, appreciated it But please don't go ;)]**[/COLOR]

---

### Post by halitech on 2008-12-27
ok so you are dual booting but that didn't answer the question on how you connect to the internet in windows.

ok, so the cable was plugged in, was the phone connected as well?

---

### Post by retskrad on 2008-12-27
Nah, it wasnt. But wait, I'll run these commands again, without the USB cabel, the one assocated with the phone, ok?

Also, I'm using the same internet, wired, in both ubuntu and windows.

---

### Post by halitech on 2008-12-27
ok, then while you are in ubuntu, run this command and post the output as well

```
sudo dhclient eth0
```

---

### Post by retskrad on 2008-12-27
Yes man, of course. But please don't go, ok? Only yuo can help me? :( I really don't wanna be in windows anymore... So please don't go ;).

---

### Post by halitech on 2008-12-27
I'll be here for a bit, watching a movie as well so dont be alarmed if I'm a few minutes coming back

---

### Post by retskrad on 2008-12-27
Will there be a difference if I'm using these commands, while being on Live-CD?

---

### Post by halitech on 2008-12-27
possibly

---

### Post by retskrad on 2008-12-27
[COLOR="Red"]**Ok, here it is, on live-cd.**[/COLOR]

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

**ubuntu@ubuntu:~$ lspci**
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
01:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
**ubuntu@ubuntu:~$ lshw -c network**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 10
       serial: 00:11:09:6c:cd:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:c9:60:1a:d5:2d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
**ubuntu@ubuntu:~$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:11:09:6c:cd:5e  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)

**ubuntu@ubuntu:~$ sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:09:6c:cd:5e
Sending on   LPF/eth0/00:11:09:6c:cd:5e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ubuntu@ubuntu:~$ 



---

### Post by retskrad on 2008-12-27
bump

---

### Post by halitech on 2008-12-27
this card is about the most widely supported card on the planet by linux so not sure why its not working.

try this in the terminal
```
sudo modprobe 8139too
```
then
```
sudo lsmod
```

post the output please

---

### Post by retskrad on 2008-12-27
Ok, but please don't go away ;=)

---

### Post by mkvnmtr on 2008-12-27
Have you gone to network settings in System/adm/Network settings?

---

### Post by retskrad on 2008-12-27
**[COLOR="Red"]here it is:[/COLOR]**

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

**ubuntu@ubuntu:~$ sudo modprobe**
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
**ubuntu@ubuntu:~$ sudo lsmod**
Module                  Size  Used by
ipv6                  263972  8 
af_packet              25728  0 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,rfcomm,sco,l2cap
ppdev                  15620  0 
parport_pc             39204  1 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
apm                    26332  2 
speedstep_lib          12676  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    14600  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
pcspkr                 10624  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
evdev                  17696  4 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
iTCO_wdt               18596  0 
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
iTCO_vendor_support    11652  1 iTCO_wdt
intel_agp              33724  1 
agpgart                42184  2 drm,intel_agp
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
squashfs               46600  1 
aufs                  169892  1 
exportfs               12544  1 aufs
nls_cp437              13696  1 
isofs                  40100  2 
loop                   23180  4 
vfat                   18816  0 
fat                    57376  1 vfat
jfs                   188900  0 
xfs                   558376  0 
reiserfs              238848  0 
ext3                  133256  0 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usb_storage            81728  0 
libusual               27156  1 usb_storage
usbhid                 35840  0 
hid                    50560  1 usbhid
sr_mod                 22212  1 
cdrom                  43168  1 sr_mod
sd_mod                 42264  2 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
pata_acpi              12160  0 
8139too                31616  0 
ata_generic            12932  0 
libata                177312  3 ata_piix,pata_acpi,ata_generic
ohci1394               37936  0 
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ieee1394               96324  1 ohci1394
8139cp                 27520  0 
mii                    13440  2 8139too,8139cp
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 
ubuntu@ubuntu:~$ 




---

### Post by retskrad on 2008-12-27
I'm a ubuntu beginner, what am i supposed to do there?

---

### Post by retskrad on 2008-12-27
bump

---

### Post by halitech on 2008-12-27
according to this
[color=red]8139too 31616 0 [/color]
the module is loaded

the first command you were supposed to modprobe 8139too but thats fine, dont worry about it as the module is showing loaded. 

are you in windows right now?

and you don't need to bump after 5-6 minutes, I told you I was doing other things as well but I will be back.

---

### Post by Duck2006 on 2008-12-27
"halitech" Has it got any thing to do with the phone that he has pluged in to the USB port?

---

### Post by halitech on 2008-12-27
> **Duck2006 said:**
> "halitech" Has it got any thing to do with the phone that he has pluged in to the USB port?

I don't know, I'm still a little confused over the pan0 that is showing up in the network info but I think he said the phone was not plugged in when he ran the commands.

---

### Post by retskrad on 2008-12-27
When I gave you these latest output, I removed the usb associated with my phone and ran these commands...

---

### Post by retskrad on 2008-12-27
Yes, I'm in windows now.

---

### Post by halitech on 2008-12-27
ok, click on start - run and type in ```
ipconfig /all
```
post that info here

also, right click My Network Places - properties then right click your connection - properties. Highlight Internet Protocal and go to properties
is it set to obtain an IP address and DNS server addresses automatically?

---

### Post by retskrad on 2008-12-27
When I wreite in ipconfig /all in start, The black box comes up, it displays text, and then directly dissapears...

---

### Post by halitech on 2008-12-27
crap sorry, in the run box type in cmd and hit enter, then in the command prompt window type in ipconfig /all

---

### Post by retskrad on 2008-12-27
Yes, it says obtain it automatically.

---

### Post by retskrad on 2008-12-27
Wait man, I'm from sweden, I'll use google translate to translate my output of ipconfig/al in cmd ok?

---

### Post by retskrad on 2008-12-27
Hetre it is, in english:

> Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corporation

C: \ Documents and Settings \ Administrator> ipconfig / all

IP Configuration for Windows

         Host Name. . . . . . . . . . : User-0786700aa3
         Primary DNS Suffix. . . . . . . :
         Nodtyp. . . . . . . . . . . . . : Unknown
         IP routing enabled. . . . . . : No
         WINS Proxy Enabled. . . . . . : No

Ethernet card the Local Area Connection:

         Connection-specific DNS Suffix. :
         Description. . . . . . . . . . . : Realtek RTL8139/810x Family Houses
ernet NIC
         Physical Address. . . . . . . . . . : 00-11-09-6C-CD-5E
         DHCP enabled. . . . . . . . . : Yes
         Auto Configuration enabled. . . : Yes
         IP address. . . . . . . . . . . . : 83.255.63.166
         Subnet Mask. . . . . . . . . . . . . : 255.255.240.0
         Default Gateway. . . . . . . . : 83.255.48.1
         DHCP server. . . . . . . . . . . : 10.125.1.11
         DNS servers. . . . . . . . . . . : 83.255.245.10
                                             83.255.249.10
         The loan was obtained. . . . . . . . . . : December 28, 2008 03:48:10
         The loan expires. . . . . . . . . . : December 28, 2008 08:17:55

C: \ Documents and Settings \ Administrator>/

---

### Post by halitech on 2008-12-27
ok, so you aren't using a router but a connection direct to the modem. what type of modem do you have?

---

### Post by retskrad on 2008-12-27
It's A BLACK BOX.. here isa  pic, its not this model, but its shaoped like this.

---

### Post by halitech on 2008-12-27
ok, a motorola

it should have the model right on the front down at the bottom. just check the model for and also, on the back, what cables are plugged in?

---

### Post by retskrad on 2008-12-27
No no its not motorola its Webstar.

---

### Post by retskrad on 2008-12-27
Here it is:

[IMG]http://www.perecom.com/DPC2100.jpg[/IMG]

---

### Post by halitech on 2008-12-27
ok, how many computers are hooked up to it and what cables on the back?

anyway, its 12:30am here and I have 2 small kids that will be up in about 7 hours so I'm out.

---

### Post by retskrad on 2008-12-27
Its 6 here and I must sleep. I hope you could help me tomorrow.

---

### Post by retskrad on 2008-12-27
Only this computer is connected to it.

I gota sleep now. Tomorrow I'll tel you hich cabels its connected to.

---

### Post by retskrad on 2008-12-28
bump

---

### Post by Coder543 on 2008-12-28
What happens if you go to the top and left click on the symbol of the computers that has an exclamation point on it (the networking applet) then click on Auto eth0?

---

### Post by retskrad on 2008-12-28
Its 2 round things, then something is going in circles, like loading.. then after  while , like 30 sec it says disconnected.

---

### Post by halitech on 2008-12-28
try this, power everything (and I do mean everything) then power up the modem, wait about 1 minute then power on the computer and boot into ubuntu. I've had cases before where 1 system had trouble connecting unless the router was rebooted.

---

### Post by retskrad on 2008-12-28
I'm not having a router... I'm using wired.

Plus, now Iäm installing ubuntu ultimate edition 2, lets see how that works out...

Uts very weird, like a couple of months ago, I had ubuntu and windows, I was dual booting ubuntu and internet worked there too, I ahve the same internet like today.

---

### Post by halitech on 2008-12-28
there are also wired routers and I was referring to me having trouble with one computer not getting an IP without rebooting my router.

---

### Post by retskrad on 2008-12-28
ah ok =p

I just installed Uubntu ultimate edition 2 and still internet didin't work... its very very strange..

---

### Post by halitech on 2008-12-28
did you try rebooting the modem?

---

### Post by retskrad on 2008-12-28
am I suppose to:

1. turn off the computer.
2. Remove the wires connected to the modem and the computer
3. wait a couple of minutes
4. Then what?

---

### Post by halitech on 2008-12-28
1. shut down the computer and unplug the power to the modem
2. power on just the modem
3. wait about 1 minute then plug the power into the modem
4. start up the computer

shouldn't need to disconnect any other wires except the power to the modem

---

### Post by retskrad on 2008-12-28
When I start the computer, am I supposed to log in to windows or ubumntu?

---

### Post by retskrad on 2008-12-28
One other thing that I don't udnerstand...

> 2. power on just the modem
Am I supposed to unplug the modem wire, that connects to the computer, am I suppose to unplug that one and the power to the modem?

> 3. wait about 1 minute then plug the power into the modem

Am I suppose to that, tot he one connected to the computer ALSO? The modem wire, connected to the computer.

---

### Post by halitech on 2008-12-28
sorry, 2 and 3 are the same, was thinking about a router being in there as well.

power everythign down, power on the modem, wait a minute then boot the computer into ubuntu and see if you can connect

---

### Post by retskrad on 2008-12-28
So, I don't need to unplug anything, just poweroff?

---

### Post by halitech on 2008-12-28
if your modem has a power switch, then turn it off, if it doesn't then unplug just the power cord.

---

### Post by retskrad on 2008-12-28
No, still the internet didin't work.

1. I turned of the computer (I just clicked on turn off)
2. I then unpluged a blackwire, the modem turned off and I plugged it again, and the modem was on.
3. I waited 1 minute
4. Then I started the computer, and logged in to ubuntu. Still no internet..

---

### Post by Duck2006 on 2008-12-28
> 2. I then unpluged a blue wire, the modem turned off and I plugged it again, and the modem was on.

Unplug from the wall (the outlet)

---

### Post by retskrad on 2008-12-28
Unplug the modems wire from the wall, AND the computers?

---

### Post by halitech on 2008-12-28
leave the power off for a minute or so just to allow it time to reset and ideally, unplug it from the wall (as Duck2006 says)

---

### Post by retskrad on 2008-12-28
Unplug the modems wire from the wall, AND the computers??

---

### Post by halitech on 2008-12-28
just the modem should be fine

---

### Post by retskrad on 2008-12-28
I did what you told me... but still internet is not working...

For a couple of minutes the modem, other lights were glowing... some lights that it never glowed before

But then suddenly internet worked again but not in ubuntu..

Dang I'm really getting pissed, I love ubuntu man, but it pisses me off this thing with internet

---

### Post by retskrad on 2008-12-28
I did, I meant a black wire.

---

### Post by linux_tech on 2008-12-28
unplug everything, router, hub, pc plugin router, then start pc

---

### Post by retskrad on 2008-12-28
I have a wired modem.

---

### Post by retskrad on 2008-12-28
Bump

---

### Post by retskrad on 2008-12-28
bump

---

### Post by albinootje on 2008-12-29
> **retskrad said:**
> 
8139too 31616 0
8139cp 27520 0


You have two different modules loaded for your NIC, and both show 0 which means unused.
I think it's not good that both are loaded at the same time.

Can you do the following :
```

sudo gedit /etc/modprobe.d/blacklist

```

And add this line :

blacklist 8139cp

Save the file, and reboot.

---

### Post by sharon.gmc on 2008-12-29
This is one error that make me think about changing my system. . .

---

