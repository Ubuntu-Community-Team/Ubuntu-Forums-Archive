---
title: "Pretty please, help me get D-Link DWA 140 to work"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by BurKaBU on 2010-03-17
Hi, I'm excited about switching over to Ubuntu 9,10 not because my XP is not working as inteded, its actually working great for me.
But because I don't like were the road is leading when I look at Vista and company policy in general.
Also I love the community around open software and the endless possibilities. 
And if I don't take the time to learn something new now when I'm 31, I'm certainly not going to when I'm older :)

That being said, I'm having the hardest time with my Ubuntu atm.
I have a D-Link DWA 140 bought just for its supposed to work "right out of the box" and Nvidia GTX 275, just for the same reason.

I'm a quite bright guy with good general computer knowledge. But when I reboot my computer into XP to find a nice guide on how to start up my internet I'm about to quit.

Because its really easy to find that guide on how to start up your DWA 140. Step 1, download and install ndiswrapper, where and how?... and how do I install the program?

Easy!, I just find me another guide on this, here it says I just need to find the right version of my chipset in my DWA 140 and then download the appropriate driver for this and compile it with ndiswrapper, again how do I find this version and what is compiling?

Easy!, I just find me another guide on this and in this guide I find a wall of text that I'm supposed to put somewhere in my something that I don't really know what it is... but there is a dummy guide to this and...

I'm lost, it feels like a big catch 22... I need my internet to work to learn Ubuntu and to get internet to work I need to learn Ubuntu.

What I'm trying to say is, have I started in the wrong end of things? And it is quite easy to get lost in all the guides that are out there. And also when the hurdle to just get internet running, its quite easy to get lazy and stuck in XP :(


ps. if you have read this far maybe you have the time to help me find a step for step guide that even an impatient guy like me can follow? :)

---

### Post by Razorback on 2010-03-17
Have you checked out Network Manager to make sure that the card is in fact operating but has not been setup to connect to your wireless network?  There should be an icon near you date and time location on your desktop.  When opened, you can see all types of networks available.

[http://regmedia.co.uk/2008/11/03/ubuntu_network_manager_big.jpg](http://regmedia.co.uk/2008/11/03/ubuntu_network_manager_big.jpg)

---

### Post by BurKaBU on 2010-03-17
My connections there are exactly as in the picture, completely empty.
and when i run command "sudo iwconfig" it just says "no wireless found"...not sure if its not the device itself or just no wireless tbh =)

---

### Post by philinux on 2010-03-17
> **BurKaBU said:**
> My connections there are exactly as in the picture, completely empty.
and when i run command "sudo iwconfig" it just says "no wireless found"...not sure if its not the device itself or just no wireless tbh =)

If you can connect wired then use the update manager to update your system.

System>admin>update manager. Then try wireless.

---

### Post by Calash on 2010-03-17
Check out this thread

[http://ubuntuforums.org/showthread.php?t=1333255](http://ubuntuforums.org/showthread.php?t=1333255)


The relevant part to try is

> 
This is quite easy to fix. Add the following line to /etc/modprobe.d/blacklist.conf file and then reboot:

blacklist rt2800usb

This file is owned by root, but you can usually edit it using sudo program to run an editor as a root user:

sudo nano /etc/modprobe.d/blacklist.conf

I hope this helps.


I noticed that on some hardware it can take a minute to start up the wireless, so be patient after you reboot.

Once you are on the network do any updates that it asks you for, then check the hardware Drivers section under System/Administration.  It "should" list the Nvidia drivers for you at that point.  If everything works right you can activate them, reboot, and be up and running.

---

### Post by J_Stanton on 2010-03-17
sudo gedit /etc/modprobe.d/blacklist.conf would be better for a noob.

---

### Post by Calash on 2010-03-17
> **J_Stanton said:**
> sudo gedit /etc/modprobe.d/blacklist.conf would be better for a noob.

Your right, thanks for the correction.  I spend way to much time in the terminal.

---

### Post by BurKaBU on 2010-03-17
> **philinux said:**
> If you can connect wired then use the update manager to update your system.

System>admin>update manager. Then try wireless.

Unfortunately I only have the wireless as an option =/

> Check out this thread

[http://ubuntuforums.org/showthread.php?t=1333255](http://ubuntuforums.org/showthread.php?t=1333255)


The relevant part to try is

Quote:
This is quite easy to fix. Add the following line to /etc/modprobe.d/blacklist.conf file and then reboot:

blacklist rt2800usb

This file is owned by root, but you can usually edit it using sudo program to run an editor as a root user:

sudo nano /etc/modprobe.d/blacklist.conf

I hope this helps.
I noticed that on some hardware it can take a minute to start up the wireless, so be patient after you reboot.

Once you are on the network do any updates that it asks you for, then check the hardware Drivers section under System/Administration. It "should" list the Nvidia drivers for you at that point. If everything works right you can activate them, reboot, and be up and running. 

I'll try that tnx.

---

### Post by halitech on 2010-03-17
for a graphical app you should actually use gksudo and not sudo

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

---

### Post by Doctor Mike on 2010-03-17
> **BurKaBU said:**
> Hi, I'm excited about switching over to Ubuntu 9,10 not because my XP is not working as inteded, its actually working great for me.
But because I don't like were the road is leading when I look at Vista and company policy in general.
Also I love the community around open software and the endless possibilities. 
And if I don't take the time to learn something new now when I'm 31, I'm certainly not going to when I'm older :)

That being said, I'm having the hardest time with my Ubuntu atm.
I have a D-Link DWA 140 bought just for its supposed to work "right out of the box" and Nvidia GTX 275, just for the same reason.

I'm a quite bright guy with good general computer knowledge. But when I reboot my computer into XP to find a nice guide on how to start up my internet I'm about to quit.

Because its really easy to find that guide on how to start up your DWA 140. Step 1, download and install ndiswrapper, where and how?... and how do I install the program?

Easy!, I just find me another guide on this, here it says I just need to find the right version of my chipset in my DWA 140 and then download the appropriate driver for this and compile it with ndiswrapper, again how do I find this version and what is compiling?

Easy!, I just find me another guide on this and in this guide I find a wall of text that I'm supposed to put somewhere in my something that I don't really know what it is... but there is a dummy guide to this and...

I'm lost, it feels like a big catch 22... I need my internet to work to learn Ubuntu and to get internet to work I need to learn Ubuntu.

What I'm trying to say is, have I started in the wrong end of things? And it is quite easy to get lost in all the guides that are out there. And also when the hurdle to just get internet running, its quite easy to get lazy and stuck in XP :(


ps. if you have read this far maybe you have the time to help me find a step for step guide that even an impatient guy like me can follow? :)Yes' am nearly 45 and until last year have not really used one as my own (installed many for others), as long as that potential remains a refection of the users and contributors. Either way I'm like to always have at least one Ubuntu distro running.

---

### Post by BurKaBU on 2010-03-17
Ive now added the blacklist rt2800usb and waited a few minutes and no sign of a connection.

Another thing i just noticed is that my wireless usb does not shine with its usual orange light that it does in XP.

Ive tried reconnect it and switch usb ports with my mouse (the mouse works in all usb ports) but no sign of life...

---

### Post by achase79 on 2010-03-17
you can use [keryx]("http://keryxproject.org") to download programs and updates in windows, mac, or linux for Ubuntu or other debian based linux distros.

---

### Post by BurKaBU on 2010-03-17
> **achase79 said:**
> you can use [keryx]("http://keryxproject.org") to download programs and updates in windows, mac, or linux for Ubuntu or other debian based linux distros.

I downloaded it and read the tutorial, when i press the buttons I'm supposed to it just gives error message that I have to create project.. .

---

### Post by Calash on 2010-03-17
> **BurKaBU said:**
> Ive now added the blacklist rt2800usb and waited a few minutes and no sign of a connection.

Another thing i just noticed is that my wireless usb does not shine with its usual orange light that it does in XP.

Ive tried reconnect it and switch usb ports with my mouse (the mouse works in all usb ports) but no sign of life...

Probably a silly question but it is better to ask.

Did you reboot after adding the item to the blacklist?  If not, try that.

---

### Post by BurKaBU on 2010-03-17
Yeah i did reboot. And ive managed to get that updateprogram working trough XP but now improvements, my adapter is still not working.

Now ive moved on to ndiswrapper and managed to get that installed... found the XP driver and got ndiswrapper to apparently do something nice with those drivers... but still no progress =(

ive now spent 3h two evenings in a row just to get my internet to work... should it be this hard or is it just me that keeps messing things up? :(

---

### Post by nothingspecial on 2010-03-17
Post the output of 
```

lsmod
```

```
cat /etc/modules
```

```
cat /etc/modprobe.d/blacklist.conf
```

To see where you are up to. The problem with being new and having a major issue, is that you follow all these guides and what have you on the internet, and may do something, that unwittingly, stops the correct solution from working, if you see what I mean.

oh, and

```
sudo lshw -C network
``` aswell

---

### Post by BurKaBU on 2010-03-18
peter@peter-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
serio_raw               5280  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
led_class               4096  1 rt2x00lib
input_polldev           3716  1 rt2x00lib
lp                      8964  0 
snd_hda_codec_realtek   203328  1 
ppdev                   6688  0 
parport_pc             31940  1 
parport                35340  3 lp,ppdev,parport_pc
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
mac80211              181236  2 rt2x00usb,rt2x00lib
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
cfg80211               93052  2 rt2x00lib,mac80211
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
crc_ccitt               1852  1 rt2800usb
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
hid_logitech            8412  0 
ff_memless              5188  1 hid_logitech
usbhid                 38208  1 hid_logitech
ohci1394               29900  0 
usb_storage            52544  1 
ieee1394               86596  1 ohci1394
r8169                  32064  0 
mii                     5212  1 r8169
intel_agp              27484  0 
agpgart                34988  1 intel_agp
floppy                 54916  0 
peter@peter-desktop:~$ cat /etc/modules 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
peter@
peter-desktop:~$ cat /etc/modprobe.d/blacklist.conf
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

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

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

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

Sorry about a late reply, but it took a surprisingly long time to find a way to export the output to a .txt file in the proper format:) (since I don't have internet in Ubuntu and only in XP... )

---

### Post by nothingspecial on 2010-03-18
Ok, I`m in the mood atm.

First, a short explanation in (hopefully) beginners terms, of modules.

The lovely linux kernel comes jam packed with them.

They are drivers that linux developers have written to make stuff work.

They are the reason you can plug in **""most""** printers, usb wireless thingys, etc, etc, etc (hardware basically (even your graphics and sound cards)), and they just work ------ no need for that silly cd that comes in the box.

Linux, at boot, (although it looks for new stuff every few seconds) will try and see what you`ve got and load the correct module (driver) to work it.

Unfortunately, this is not foolproof. Sometimes, linux will load what it thinks is the correct module but it isn`t. Or connects the wrong module with the wrong hardware.

In this situation we have to "blacklist" the module. On Ubuntu we do this by adding the module to /etc/modprobe.d/blacklist.conf. I`m not sure which happens first but in the boot process, linux reads that file and doesn`t load it.

On the other hand /etc/modules is the file that linux reads to know which modules we definately want to load.

So, if we have a problem caused by linux loading the wrong module (driver), we have to tell it to not load the bad one and/or to load the good one. This is what you have been trying to do. 

Looking at what you have posted you haven`t actually added the module to /etc/modprobe.d/blacklist.conf.

To explain that last bit, when you typed lsmod, it told you the modules you are using. If you look, you can see rt2800usb 6 lines down - so it has loaded (not been blacklisted). Also there is no line in /etc/modprobe.d/blacklist.conf that says blacklist rt2800usb.

So, in your menu, go applications > accessories > terminal and copy and paste this in

```
gksudo gedit /etc/modprobe.d/blacklist.conf 
```

Go right to the bottom of that page (file) and copy and paste this (so it is the last line).


```
blacklist rt2800usb
```

Save it then reboot.

That will accomplish what you are trying to do.........

......weather it will work or not, I don`t know. I don`t have that device.

---

### Post by BurKaBU on 2010-03-19
Hello, thanks for the explanation now I know what I'm trying! to do :)

The thing is that I actually HAVE blacklisted that device, when I edit the blacklist.conf I have a line in the bottom that says "blacklist rt2800usb".

I have tried running a bunch of other diagnostic commands, that I forgot the name of, and it keept prompting about blacklist.conf.save. And when I opened up that file it seemed identical to the original blacklist.conf.

I then took a shot in the dark and added "blacklist rt2800ubs" to that one aswell, but no improvement.

---

### Post by J V on 2010-03-19
> **BurKaBU said:**
> I have a D-Link DWA 140 bought just for its supposed to work "right out of the box"Well it apparently wants ndiswrapper so whoever said that was full of it (lol)

If you want HW to work out of the box on linux, theres nothing better than to try it out yourself, can you still return the wireless and get a different one? (from what I remember, dlink is especially crap on linux...)

---

### Post by BurKaBU on 2010-03-19
> **J V said:**
> Well it apparently wants ndiswrapper so whoever said that was full of it (lol)

If you want HW to work out of the box on linux, theres nothing better than to try it out yourself, can you still return the wireless and get a different one? (from what I remember, dlink is especially crap on linux...)

Unfortunately not, I bought it about 3-4 month ago and have been using XP up until now :/

---

### Post by leandromartinez98 on 2010-03-19
In this case I would suggest you to get a LiveCD of the Lucid-Beta1 that
is coming today and see if your network card works with it. If it does, wait until April to install the new ubuntu version and everything will be much easier.

---

### Post by 3rdalbum on 2010-03-19
> **leandromartinez98 said:**
> In this case I would suggest you to get a LiveCD of the Lucid-Beta1 that
is coming today and see if your network card works with it. If it does, wait until April to install the new ubuntu version and everything will be much easier.

April Schmapril - if you get the live CD of the Lucid Beta 1, why wait for the final release? I'm now running Lucid on two computers and it's very good.

---

### Post by leandromartinez98 on 2010-03-19
Yes, I thougt that, but he is new to this, I wouldn't recomend him to use a beta now, but of course he could.

---

### Post by 3rdalbum on 2010-03-19
> **leandromartinez98 said:**
> Yes, I thougt that, but he is new to this, I wouldn't recomend him to use a beta now, but of course he could.

And of course your opinion on this is as valid as mine :-)

BurkaBu, I'm sorry that this has been complicated. Unfortunately that's the reality with hardware where the manufacturer has not written a Linux driver or released specifications to the open-source community. It may be cold comfort to you, but the majority of wireless cards do work on Ubuntu either 'out-of-the-box' or with a download from the Hardware Drivers program.

If you look on eBay for the D-Link DWL-G122 (H/W Ver C1), you should be able to find one on there for $10 or so. I own one and it is well supported on Linux. It's a USB wifi adapter, not especially fast but it does the job. It works out-of-the-box on Ubuntu; by that, I mean that you don't need to blacklist anything and you don't need to install anything, it just works straight off.

---

### Post by BurKaBU on 2010-03-19
Well I guess I can try and see if Lucid will fix the problem for me, because I don't think things can get much worse :)

---

### Post by teward on 2010-03-19
Your D-Link card **will not work** without using ndiswrapper, and as such, you're stuck.  D-Link doesn't use any generic drivers, they're all for Windows systems.

I wouldn't trust the Lucid beta, as its still quite buggy.

[SIZE=1][COLOR=White]<offtopic>400th post for me</offtopic>[/COLOR][/SIZE]

---

### Post by BurKaBU on 2010-03-19
> **TrekCaptainUSA said:**
> Your D-Link card **will not work** without using ndiswrapper, and as such, you're stuck.  D-Link doesn't use any generic drivers, they're all for Windows systems.

I wouldn't trust the Lucid beta, as its still quite buggy.

[SIZE=1][COLOR=White]<offtopic>400th post for me</offtopic>[/COLOR][/SIZE]

That hurts, how do I get moving now then... I've now spent 8h on tring to get this to work, and it feels like I'm not one step closer to a solution :(

This is starting to feel quite hopeless...

---

### Post by nothingspecial on 2010-03-19
Try ndisgtk

```
sudo apt-get install ndisgtk
```

Then you need to get the windows driver on your machine somehow. Download it or get it of the cd if there is one.

Then you launch ndisgtk and import the .inf file into it then reboot.

The inf file will be in the windows driver.

Not used ndiswrapper for years, sorry I can`t be more specific than that.

---

### Post by BurKaBU on 2010-03-19
> **nothingspecial said:**
> Try ndisgtk

```
sudo apt-get install ndisgtk
```

Then you need to get the windows driver on your machine somehow. Download it or get it of the cd if there is one.

Then you launch ndisgtk and import the .inf file into it then reboot.

The inf file will be in the windows driver.

Not used ndiswrapper for years, sorry I can`t be more specific than that.

Ive now found what i think is a good .inf file and put it in ndis map and run the suggested comman, nwo what? =)

---

### Post by nothingspecial on 2010-03-19
You need to put ndiswrapper in /etc/modules and restart.

To test it you can load it manually

```
sudo modprobe ndiswrapper
```

Read [[COLOR="Magenta"]this[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by BurKaBU on 2010-03-19
> **nothingspecial said:**
> Try ndisgtk

```
sudo apt-get install ndisgtk
```

Then you need to get the windows driver on your machine somehow. Download it or get it of the cd if there is one.

Then you launch ndisgtk and import the .inf file into it then reboot.

The inf file will be in the windows driver.

Not used ndiswrapper for years, sorry I can`t be more specific than that.

> **nothingspecial said:**
> You need to put ndiswrapper in /etc/modules and restart.

To test it you can load it manually

```
sudo modprobe ndiswrapper
```

Read [[COLOR="Magenta"]this[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Tnx, I started to read at the link you just posted... and ofc its a great tutorial on how and what to install, its just its liked to about 10 other tutorials that I have to first read to be able to do that one... Is Ubuntu really this complicated or am I just lazy/stupid to think so...?

---

### Post by nothingspecial on 2010-03-19
Ubuntu is really easy aslong as everything works.

If you`re unlucky and have to get something working it can seem a little daunting.

---

### Post by leandromartinez98 on 2010-03-19
> **BurKaBU said:**
> Tnx, I started to read at the link you just posted... and ofc its a great tutorial on how and what to install, its just its liked to about 10 other tutorials that I have to first read to be able to do that one... Is Ubuntu really this complicated or am I just lazy/stupid to think so...?

No, you just had the bad luck of having an incompatible hardware. This things are getting less and less frequent, happily, but I've been there
to. I still would test Lucid.

---

### Post by BurKaBU on 2010-03-20
> **leandromartinez98 said:**
> No, you just had the bad luck of having an incompatible hardware. This things are getting less and less frequent, happily, but I've been there
to. I still would test Lucid.

Ive now tried Lucid, but it wont even boot :(

---

### Post by BurKaBU on 2010-03-20
I've set my mind on switching over to Ubuntu 9.10 from windows XP but I'm having major issues with my D-Link DWA 140.

I have now spent the better part of my evenings trying to get it to work but with no luck.
I've read so many guides on how to make it work, but I just cannot get it to work.
I'm a real rookie when it comes to Ubuntu and its been a pain logging in and out of XP to post on the forums for help.

I've now borrowed a laptop from a friend so I can stay online while still in Ubuntu.
Thats why it would be amazing if someone could take time to maby add me on messenger and help me out in this matter.
Because one of the problems with getting help from many different guides and people is that it seems that everyone have a different approach on how to fix it. A
nd it seems like mixing it up just makes things worse :)

---

### Post by yeats on 2010-03-20
> I've set my mind on switching over to Ubuntu 9.10 from windows XP but I'm having major issues with my D-Link DWA 140.

Can you be more specific about what the problem is and what steps you have taken to try to fix it?

---

### Post by coffeecat on 2010-03-20
> **chrissharp123 said:**
> Can you be more specific about what the problem is and what steps you have taken to try to fix it?

It's all in this thread:

[http://ubuntuforums.org/showthread.php?t=1432183](http://ubuntuforums.org/showthread.php?t=1432183)

@BurKaBU, why are you starting a new thread on the same topic?

---

### Post by BurKaBU on 2010-03-20
Yeah as you can read in the link coffeecat posted I'm kinda stuck with Ndiswrapper not working =/

And I started a new one because the topic didn't specify the problem, and it seemed abandoned.

---

### Post by coffeecat on 2010-03-20
> **BurKaBU said:**
> And I started a new one because the topic didn't specify the problem, and it seemed abandoned.

Yes, but it's only polite to link back to your original thread, otherwise people will be wasting time suggesting exactly the same things - which is a sure way of annoying people trying to help you.

Reading your earlier thread I notice that blacklisting rt2800usb in blacklist.conf didn't work for you, yet it worked for others. But you didn't post any details of exactly what you did. My guess is that you may have made a simple typo in your edit of blacklist.conf or some other error. I think you need to revisit that fix.

Unfortunately, the issue is now complicated by trying ndiswrapper. I have no experience of ndiswrapper so I have nothing to add except that the answer almost certainly lies in blacklisting rt2800usb.

---

### Post by leandromartinez98 on 2010-03-20
Are you booting from a LiveCD? Have you tested the cd for defects? You have no luck at all....

---

### Post by BurKaBU on 2010-03-20
> **coffeecat said:**
> Yes, but it's only polite to link back to your original thread, otherwise people will be wasting time suggesting exactly the same things - which is a sure way of annoying people trying to help you.

Reading your earlier thread I notice that blacklisting rt2800usb in blacklist.conf didn't work for you, yet it worked for others. But you didn't post any details of exactly what you did. My guess is that you may have made a simple typo in your edit of blacklist.conf or some other error. I think you need to revisit that fix.

Unfortunately, the issue is now complicated by trying ndiswrapper. I have no experience of ndiswrapper so I have nothing to add except that the answer almost certainly lies in blacklisting rt2800usb.

Well I have checked the spelling several times, but when I run the command that types out my blacklist.conf it does not show up... yet when I do a sudo gedit /etc/xxx/blacklist.conf the last line is blacklist rt2800usb.

---

### Post by bkratz on 2010-03-20
> **BurKaBU said:**
> Well I have checked the spelling several times, but when I run the command that types out my blacklist.conf it does not show up... yet when I do a sudo gedit /etc/xxx/blacklist.conf the last line is blacklist rt2800usb.

Could you take a moment and just look at posts 15 and 16 of this long thread?

[http://ubuntuforums.org/showthread.php?t=1333255&highlight=dwa-140&page=2](http://ubuntuforums.org/showthread.php?t=1333255&highlight=dwa-140&page=2)

You might want to do a

lsusb

(Lsusb) and see which you have.

---

### Post by bkratz on 2010-03-20
Also here are directions for either version

[http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&ei=zjhAS7OxJIfEsQPYg9nGBA&sa=X&oi=translate&ct=result&resnum=6&ved=0CBgQ7gEwBQ&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den](http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&ei=zjhAS7OxJIfEsQPYg9nGBA&sa=X&oi=translate&ct=result&resnum=6&ved=0CBgQ7gEwBQ&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den)

---

### Post by BurKaBU on 2010-03-20
Cheers, Ill take a look there and swee what i can find =)

---

### Post by cariboo on 2010-03-20
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by BurKaBU on 2010-03-21
Well I've given up on getting this card to work so I'm gonna buy me a new one.
The lokal store stocks TP-Link TL-WN821N, and from what I can gather at [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB) it should work right out of the box. 
The only concern I have is that in the comments it says "Tested on Ubuntu Karmic Koala 64-bit version with linux kernel 2.6.31-19-generic. Works perfectly with airmon-ng, airodump-ng and aireplay-ng."
Does that mean that it will work just as well in 32-bit version, or are the 32- and 64-bit very different in what hardware they support?

---

### Post by nothingspecial on 2010-03-21
There should be no difference. However I`m not going to stick my neck out and say absolutely, definitely 100%.

I would take your machine to the shop and ask if you can test it. I have in the past.

I admire your pereverence.

---

### Post by BurKaBU on 2010-03-22
> **nothingspecial said:**
> There should be no difference. However I`m not going to stick my neck out and say absolutely, definitely 100%.

I would take your machine to the shop and ask if you can test it. I have in the past.

I admire your pereverence.

The card is to my stationary* so the testing is kina out of the question, but you seem sure enough for me to try :)

*I'm not sure why I'm buying and USB version, its just that in the past my pci cards have not performed as well as USB ones when it comes to signal strength.


tnx to everyone that have tried to help me in this matter

---

### Post by BurKaBU on 2010-03-22
I just have one more question about network cards, when it says "work out of the box"... do I have to do something to get it to work?

Because I have now bought and plugged in my new network card:TP-Link TL-WN821N and still no sign of a network connection :(

---

### Post by nothingspecial on 2010-03-23
You`re kidding me ](*,)

Where did you read that this works out of the box. I just googled "TP-Link TL-WN821N ubuntu" and can see nothing but problems.

Take it back and say it doesn`t work and get something else.

Other wise we`re going to have to start modprobing and sudo gediting and ndiswrapping all over again.

Never had a problem with netgear usb wireless thingys btw.

---

### Post by BurKaBU on 2010-03-23
> **bkratz said:**
> Also here are directions for either version

[http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&ei=zjhAS7OxJIfEsQPYg9nGBA&sa=X&oi=translate&ct=result&resnum=6&ved=0CBgQ7gEwBQ&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den](http://translate.google.com/translate?hl=en&sl=fr&u=http://doc.ubuntu-fr.org/dwa-140&ei=zjhAS7OxJIfEsQPYg9nGBA&sa=X&oi=translate&ct=result&resnum=6&ved=0CBgQ7gEwBQ&prev=/search%3Fq%3D07d1:3c0a%26hl%3Den)

> **nothingspecial said:**
> You`re kidding me ](*,)

Where did you read that this works out of the box. I just googled "TP-Link TL-WN821N ubuntu" and can see nothing but problems.

Take it back and say it doesn`t work and get something else.

Other wise we`re going to have to start modprobing and sudo gediting and ndiswrapping all over again.

Never had a problem with netgear usb wireless thingys btw.

Well I looked it up here [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link#USB), I guess that I have to try and return the card then :(

---

### Post by nothingspecial on 2010-03-23
What kernel do you have?

Post the output of

```
uname -a
```

---

### Post by BurKaBU on 2010-03-24
> **nothingspecial said:**
> What kernel do you have?

Post the output of

```
uname -a
```

I finally got it to work after reinstalling Ubuntu.

I'm currently at work and don't know what kernel I have.
All I know is that it's the ubuntu 9.10 install CD I have used and updated 238mb with the "update-button"

But now the problem is speed and constant disconnects (took me almoust 4h to DL 328mb, when it should take 10min ), maby I should start a new tread concerning this particular card (could't return it since I had broken the plastic around the box :( )?

---

### Post by nothingspecial on 2010-03-24
At least you`re connected :D

Yes start a new thread.

---

