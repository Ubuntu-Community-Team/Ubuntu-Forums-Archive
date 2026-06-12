---
title: "WUSB100v2 Driver with ndiswrapper not working"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by dolphin194 on 2010-04-11
I have just installed the latest version of Ubuntu using the windows installer. Everything works, except for one thing, the wireless card. I have 3 versions of Windows installed, along with Ubuntu.

Now here's the case. I tried to install ndiswrapper from sourceforge, and it installed the driver, but the thing is, Ubuntu doesn't let it work.

---

### Post by RedSingularity on 2010-04-11
Are you sure you need ndiswrapper?  Post the output of 

lspci

---

### Post by readycarpenter on 2010-04-11
as of 9.10 wireless is easy to install, if you can connect wired just long enough to run >system>administration>hardware drivers

here is another article about it and why
[http://ubuntuforums.org/showthread.php?t=1446467](http://ubuntuforums.org/showthread.php?t=1446467)

---

### Post by dolphin194 on 2010-04-11
Oh so sorry about that, i had to go to bed. Well, when I input lspci, I get this:
```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Radeon X1650 Pro (Secondary) (rev 9e)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:0c.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
02:0c.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
02:0c.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
02:0d.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)

```

---

### Post by dolphin194 on 2010-04-11
> **readycarpenter said:**
> as of 9.10 wireless is easy to install, if you can connect wired just long enough to run >system>administration>hardware drivers

here is another article about it and why
[http://ubuntuforums.org/showthread.php?t=1446467](http://ubuntuforums.org/showthread.php?t=1446467)

Well the thing is, THERE AREN'T ANY THERE. It's all blank, see:
[IMG]http://medievalcrusade.webs.com/None.png

---

### Post by RedSingularity on 2010-04-11
Is it a USB adapter?

---

### Post by dolphin194 on 2010-04-11
Yes, its a USB

---

### Post by RedSingularity on 2010-04-11
With it plugged in post the output of 

lsusb

---

### Post by dolphin194 on 2010-04-11
Hang on, gotta restart and boot ubuntu

---

### Post by dolphin194 on 2010-04-11
It gives me:

```
Bus 001 Device 002: ID 0dbf:0300 Quik Tech Solutions Storage Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 002: ID 04cc:1122 Philips Semiconductors Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by RedSingularity on 2010-04-11
And thats with the adapter connected?

---

### Post by dolphin194 on 2010-04-11
I could try plugging it in to a different port and trying that command again, would that help?

---

### Post by dolphin194 on 2010-04-11
Yeah that is with it plugged in. It should be on bus 2

---

### Post by RedSingularity on 2010-04-11
Probably not.....you can try it though.

---

### Post by dolphin194 on 2010-04-11
So what do you think the problem might be?

---

### Post by RedSingularity on 2010-04-11
Do you have a CD with the windows driver on it?

---

### Post by dolphin194 on 2010-04-11
Yes, Windows 2000, XP, Vista and 7.

---

### Post by RedSingularity on 2010-04-11
> **dolphin194 said:**
> So what do you think the problem might be?

I am not sure but we can try troubleshooting it.

---

### Post by RedSingularity on 2010-04-11
Ok, did you ever extract a .inf file from the windows .exe?

---

### Post by dolphin194 on 2010-04-11
Yes. I use 7zip rite?

---

### Post by RedSingularity on 2010-04-11
You can use that.  Where is the proper .inf file located?

---

### Post by dolphin194 on 2010-04-11
Well actually its stored on the CD directly

---

### Post by RedSingularity on 2010-04-11
Ok, put in the CD and extract the windows driver .exe file to your ubuntu desktop.

---

### Post by dolphin194 on 2010-04-11
Windows Directory would be H:\PureInstaller\adapter\xp\x86\rt2870.inf, but thats windows because thats what im using, Windows 7

---

### Post by dolphin194 on 2010-04-11
Then after that?

---

### Post by RedSingularity on 2010-04-11
You are in Ubuntu by the way correct?

---

### Post by dolphin194 on 2010-04-11
No, my windows 7 is what im using. I gotta reboot, but i can use my laptop in the forums if you need... My ubuntu cant connect with my wireless, but win can

---

### Post by RedSingularity on 2010-04-11
Yeah you need to be in Ubuntu.  Can you be in Ubuntu and the forums at the same time?

---

### Post by dolphin194 on 2010-04-11
> **RedSingularity said:**
> Yeah you need to be in Ubuntu.  Can you be in Ubuntu and the forums at the same time?
Well, sort of. I can be in Ubuntu on my desktop, and be in the forums with my Dell Inspiron Mini 10v

---

### Post by RedSingularity on 2010-04-11
Ok thats fine.  Boot Ubuntu on the computer we are trying to get working.

---

### Post by dolphin194 on 2010-04-11
Alright, my desktop is restarting. Itll take a while to boot unfortunately... This is my laptop.

---

### Post by RedSingularity on 2010-04-11
Where is the website with the needed driver?  Do you know?

---

### Post by dolphin194 on 2010-04-11
Yes i do. The driver is located on the CD and also at [http://homesupport.cisco.com/en-us/wireless/lbc/WUSB100/download?referrer=www.linksysbycisco.com](http://homesupport.cisco.com/en-us/wireless/lbc/WUSB100/download?referrer=www.linksysbycisco.com) and **my hardware version is version 2.0**

---

### Post by dolphin194 on 2010-04-11
sorry forgot to say my desktop is booted up. If well need it wine is already installed

---

### Post by RedSingularity on 2010-04-11
So we are on the same page, we are going to use the 32 bit file from windows XP.  Extract that one to your ubuntu desktop.

---

### Post by dolphin194 on 2010-04-11
all files are in a folder on my desktop. Including the .inf and .sys

---

### Post by RedSingularity on 2010-04-11
Ok extract the .inf file to your desktop.

---

### Post by dolphin194 on 2010-04-11
yea it is. It is called rt2870.inf its extracted

---

### Post by RedSingularity on 2010-04-11
Yeah thats the one, good.  Ok, now we need to install ndiswrapper to the Ubuntu computer some how.  Unless you did already.........?

---

### Post by dolphin194 on 2010-04-11
Yes it is installed. We have a router and while my mom was gone i plugged my computer in where hers is. Its hard wired so thats how i did it.

---

### Post by RedSingularity on 2010-04-11
Great.  Now do the following in a terminal.......

ndiswrapper -i ~/Desktop/rt2870.inf

and post the output of it when its done.

---

### Post by dolphin194 on 2010-04-11
```
kevin@ubuntu:~$ ndiswrapper -i ~/desktop/rt2870.inf
driver rt2870 is already installed
kevin@ubuntu:~$
```

---

### Post by RedSingularity on 2010-04-11
Now post the output of 

ndiswrapper -l

---

### Post by dolphin194 on 2010-04-11
```
kevin@ubuntu:~$ ndiswrapper -l
rt2870 : driver installed
device (1737:0078) present
```

---

### Post by RedSingularity on 2010-04-11
Great, so far so good.

Now do this......
 
sudo modprobe ndiswrapper

Then see if you can find wireless networks.

---

### Post by dolphin194 on 2010-04-11
```
kevin@ubuntu:~$ sudo modprobe ndiswrapper
[sudo] password for kevin:
kevin@ubuntu:~$ 
```

---

### Post by dolphin194 on 2010-04-11
When I click on the connection icon, it should show then, right? 
All it says is
Wired Network
disconnected
then VPN Connections

---

### Post by RedSingularity on 2010-04-11
Are you copying and pasting from the terminal?  If so paste the output of 

lsmod

---

### Post by dolphin194 on 2010-04-11
```
kevin@ubuntu:~$ lsmod
Module                  Size  Used by
ndiswrapper           185532  0 
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
nls_utf8                1568  1 
isofs                  31620  1 
binfmt_misc             8356  1 
snd_ens1371            22016  2 
gameport               11368  1 snd_ens1371
snd_ac97_codec        101216  1 snd_ens1371
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  2 snd_ens1371,snd_seq_midi
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
ppdev                   6688  0 
psmouse                56500  0 
serio_raw               5280  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  1 snd_pcm
parport_pc             31940  1 
shpchp                 32272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
usb_storage            52768  2 
r8169                  32064  0 
mii                     5212  1 r8169
radeon                636000  2 
ttm                    36212  1 radeon
drm                   160032  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
intel_agp              27676  1 
agpgart                34988  3 ttm,drm,intel_agp
kevin@ubuntu:~$ 


```

---

### Post by RedSingularity on 2010-04-11
Post the output of 

iwconfig

---

### Post by dolphin194 on 2010-04-11
```
lo no wireless extensions.
eth0 no wireless extensions
```

---

### Post by RedSingularity on 2010-04-11
Ahhh it doesnt look like its going to work after all.  Sorry buddy.  :(

I had a look at the "working" adapters on the NDIS web site and yours, the WUSB100, is not listed there.  Look [here](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS&from=Hamlet+HNW254CI) under linksys.

---

### Post by dolphin194 on 2010-04-11
So what should I do about it?

---

### Post by RedSingularity on 2010-04-11
Not much you can do.  I am sure in later kernel releases there will be support for your adapter but as of now there is none.  If possible, return it and try another model.  With linux its a good idea to buy hardware that has been out for a while.  That way there is a much better chance of it being built into the Kernel.

---

### Post by dolphin194 on 2010-04-11
Well, I cant return it ive had it for like half a year so i cant return. Well thanks anyway, i guess i might have to just give up on ubuntu. no internet means you cant do anything

---

### Post by RedSingularity on 2010-04-11
Just out of curiosity, are you running 32bit ubuntu?

---

### Post by dolphin194 on 2010-04-11
Yes. Intel Pentium 4 2.00 GHz

---

### Post by RedSingularity on 2010-04-11
Ok so we did use the correct windows driver.  Before you give up you can repeat what we did with the VISTA driver and the WINDOWS 7 driver.  Maybe you will get lucky.  If you decide to try it let me know the results.  That way I can edit the "working" devices on their site and add yours to the correct category.   

One last thing.  DO this in a terminal and then reboot the computer with the device still plugged in.

ndiswrapper -m

Then Reboot and see if you can get any networks.

---

### Post by dolphin194 on 2010-04-11
Ok, i will try.

---

### Post by dolphin194 on 2010-04-11
Nope, well i guess thats the end of it.

---

