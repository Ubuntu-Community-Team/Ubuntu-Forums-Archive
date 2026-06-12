---
title: "tv on ubuntu 10.o4"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by m3t3ors on 2010-10-08
i have a pc in my workshop and want to watch tv on it, i bought a dvb mini digital tv stick of ebay and no matter what i try cant get it to run.
ive tried myth tv and others
now when i run hardware drivers it tells me theres a driver or it which i installed but still nothing happens.
any ideas guys

---

### Post by Locke_99GS on 2010-10-08
Try metv, xawtv, or tvtime. 

I used, I believe, tvtime for the Encore TV PCI card i have. I haven't actually used it in years, but it worked a couple of years ago.

Use one of those applications, and try selecting different available v4l devices. You're likely just not looking at the correct device.

---

### Post by m3t3ors on 2010-10-08
in software not got 
just get a flash on screen then nothing

---

### Post by sikander3786 on 2010-10-08
> **m3t3ors said:**
> in software not got 
just get a flash on screen then nothing
What have you installed? TVTime I assume? Start it by typing

```
tvtime
```

in a terminal and post back the error message.

---

### Post by m3t3ors on 2010-10-08
john@john-shed:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/john/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory
Segmentation fault
john@john-shed:~$ 

yes installed tv time and dependencies

---

### Post by fatality_uk on 2010-10-08
Firstly what type (Brand) of DVB-T USB stick is it?
Secondly, there is a fantastic application called Kaffeine which will allow you to view TV on Ubuntu. But until we know what card, it might be hard to get it up and running.

---

### Post by m3t3ors on 2010-10-08
[http://cgi.ebay.co.uk/DVB-T-Digital-USB-TV-CARD-TUNER-Freeview-Laptop-PC-/110595649533?pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item19c003affd](http://cgi.ebay.co.uk/DVB-T-Digital-USB-TV-CARD-TUNER-Freeview-Laptop-PC-/110595649533?pt=UK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW&hash=item19c003affd)

on the card it says digital energy?

---

### Post by sikander3786 on 2010-10-08
Does Ubuntu detect your card when the card is inserted.

```
lsusb
```

---

### Post by m3t3ors on 2010-10-08
> **sikander3786 said:**
> Does Ubuntu detect your card when the card is inserted.

```
lsusb
```

john@john-shed:~$ lsusb
Bus 003 Device 002: ID 0e6a:6001 Megawin Technology Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 15d9:0a4c Dexon 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
john@john-shed:~$

---

### Post by sikander3786 on 2010-10-08
I can't see your manufacturer here.

[http://www.linuxtv.org/wiki/index.php/Afatech_AF9015](http://www.linuxtv.org/wiki/index.php/Afatech_AF9015)

But the chip is same I believe.

---

### Post by m3t3ors on 2010-10-08
> **sikander3786 said:**
> I can't see your manufacturer here.

[http://www.linuxtv.org/wiki/index.php/Afatech_AF9015](http://www.linuxtv.org/wiki/index.php/Afatech_AF9015)

But the chip is same I believe.


yes i too saw that on linuxtv.
apparently the 9015 replaced the older one but kept the same chipset

---

### Post by m3t3ors on 2010-10-09
just looked at the download section on linux tv but im not sure what downloads i need

---

### Post by dinoj on 2010-10-09
Check this 
[http://ubuntuforums.org/showthread.php?t=606487&highlight=af9015+tda18218&page=14](http://ubuntuforums.org/showthread.php?t=606487&highlight=af9015+tda18218&page=14) 
You can try script from post #133 . This works perfect for me.

---

### Post by m3t3ors on 2010-10-09
thanks will try next time im in workshop

---

### Post by m3t3ors on 2010-10-11
was in my workshop today but didnt have much time to do much on my linux box, but i did read the link posted.
but here i got confused?
on post 133 theres a link to some script?
im unsure if i need to download a script?
and if i do which one or is it all 3?

also he links to linuxtv regarding to drivers?
one is the 9015 and the other is tda18218
do i need these as well or just 1 of them

---

### Post by anewguy on 2010-10-11
According to this link, that USB manufacturer/device id (15a4:9016) has been supported in the kernel since 2.6.28 unless Ubuntu is different.  This is for Linux TV.

[http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices_ListData/Helper]("http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices_ListData/Helper")

I would like to see the output of:

lsmod

and the contents of the /etc/modprobe.d/blacklist.conf file

As perhaps there is a kernel module (driver) that just isn't being loaded.

Dave ;)

---

### Post by m3t3ors on 2010-10-12
john@john-shed:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_intel8x0           25588  4 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  35102  71 
tileblit                2031  1 fbcon
snd_timer              19098  2 snd_pcm,snd_seq
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
softcursor              1189  1 bitblit
dvb_usb_af9015         23159  0 
nvidia               9961216  38 
dvb_usb                14457  1 dvb_usb_af9015
vga16fb                11385  1 
snd                    54148  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vgastate                8961  1 vga16fb
dvb_core               86142  1 dvb_usb
joydev                  8708  0 
psmouse                63245  0 
serio_raw               3978  0 
sis_agp                 4047  1 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
shpchp                 28820  0 
i2c_sis96x              3024  0 
agpgart                31724  2 nvidia,sis_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
sis900                 17048  0 
usbhid                 36110  0 
mii                     4381  1 sis900
hid                    67032  1 usbhid
floppy                 53016  0 
john@john-shed:~$

---

### Post by TopEnder on 2010-10-13
G'day, I have the same USB stick as you have according to lsusb.  In Ubuntu 10.04 & 9.10 (I think) I just pluged the USB stick in and install the firmware from: System/Administration/Hardware Drivers and install the driver shown for "Firmware for DVB cards".  I opened either me-tv or VLC installed a channels.conf file and was able to view all available TV an digital radio stations in my local area.

---

### Post by m3t3ors on 2010-10-13
> **TopEnder said:**
> G'day, I have the same USB stick as you have according to lsusb.  In Ubuntu 10.04 & 9.10 (I think) I just pluged the USB stick in and install the firmware from: System/Administration/Hardware Drivers and install the driver shown for "Firmware for DVB cards".  I opened either me-tv or VLC installed a channels.conf file and was able to view all available TV an digital radio stations in my local area.

you installed a channel conf file???

sorry but i dont know how or what you mean?

kafine doesnt see my dvb card as it wont let me scan for channels

mythtv just asks if i want to join a group then nothing else>
metv just asks me to add channels from a file>

---

### Post by m3t3ors on 2010-10-13
just installed vlc and get he following error

Your input can't be opened:
VLC is unable to open the MRL 'dvb://frequency=0'. Check the log for details.

got mythtv to run but it still dont see my dvb card

---

### Post by Zill on 2010-10-13
> **m3t3ors said:**
> you installed a channel conf file???
sorry but i dont know how or what you mean?
kafine doesnt see my dvb card as it wont let me scan for channels
mythtv just asks if i want to join a group then nothing else>
metv just asks me to add channels from a file>
The [Me TV User Manual]("me-tv.sourceforge.net/me-tv.pdf") discusses the channels &#64257;le (~/.me-tv/channels.conf) in Section 4.

ps.  Have you installed *all* the dependencies recommended for me-tv?

---

### Post by TopEnder on 2010-10-14
According to launchpad.net the channel.conf DB is now located at: ~/.local/share/me-tv/


[COLOR="Blue"][I]Channel DB location < me-tv 1.0.1
Me TV Questions FAQ #1170
Created by Scott Evans on on 2010-06-13
Keywords:
Channel DB channel conf
Last updated by:
Scott Evans on on 2010-06-13
From version 1.0.1 of Me TV the channel DB location has changed from ~/.me-tv to ~/.local/share/me-tv/
[/I][/COLOR]

---

### Post by m3t3ors on 2010-10-17
solved everything working but still one question
in metv how do i rescan for more channels? its found some but i want to rescan

---

### Post by Zill on 2010-10-17
> **m3t3ors said:**
> solved everything working...
I am pleased that you have now got everything working but it will help other users if you would explain exactly what resolved the problem.

It would also be useful to mark the thread as "Solved" by selecting this option from the "Thread Tools" menu at the top of this page.

---

### Post by m3t3ors on 2010-10-17
sorry but i didnt se page 3 of the thread.but it seems that metv was working from the start and mythtv was being picky as what device it used.
but i would still like to know how to scan for extra chanels

---

### Post by Zill on 2010-10-17
> **m3t3ors said:**
> ...but i would still like to know how to scan for extra chanels
If metv shows *some* channels after scanning then it may just be that the signal strength on some multiplexes is insufficient to find the extra channels.

It may be worth rescanning with a better antenna connected.

---

### Post by m3t3ors on 2010-10-18
all sorted, i rebooted my machine and ran metv and it must have automatically found more channels as i had bout 20 more channels.
thanks for all the help. much appreciated

---

