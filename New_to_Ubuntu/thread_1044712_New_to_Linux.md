---
title: "New to Linux"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by holdencaulfield on 2009-01-19
Hello,

My name is Holden, and I've used Linux a few times before, however I recently went over to my friends house, and he is using Gentoo with the Fluxbox environment, and I thought it was really cool, so I wanted to give Linux a try again. I have used Ubuntu, openSUSE, and KNOPPIX with varied results. My main problem has always been configuring my wireless network card. I have an old Dell (Inspiron B120) and an equally old wireless network card, although I am unsure which one it is. 

So basically I would really like to learn how to use Linux, and although I'm starting out as a beginner, maybe at some point I may be experienced enough to try using distros like Gentoo, that my friend was using. I don't know a ton about computers, or Linux, so I was thinking about installing the new Ubuntu, or perhaps Linux Mint. 

I feel like there was something about Linux Mint if you live in a region with software patents that makes it hard to use (legally), so I was trying to decide between one of those two, and I was hoping that I might be able to get some input right here. One of the things I would like to do is use the Fluxbox desktop environment, but I'm not sure how difficult that is to do on Ubuntu, my friend said it was hard to change with Ubuntu, because he said it wasn't as customizable, but that's one of the appealing things to me, is customizing my system, so thoughts, about what I should do

Holden

---

### Post by inspriation26 on 2009-01-19
Well, first you need to find out what kind of card you have. If you currently still using Windows its under the Device Manager and it should tell you. If your using Linux open a terminal and lshw -C network and it should tell you. Post the out put here and we will try to help you further.

---

### Post by diablo75 on 2009-01-19
There are a few different flavors of Ubuntu you should look into.  Fluxbuntu would probably be the best place for you to start since that's the desktop environment you want to use.  The standard version of Ubuntu uses GNOME, Kubuntu uses KDE, Xubuntu uses xfce... I've used icewm before with good results.  You could even install all of these environments onto the same machines and switch between them by changing your session settings at the login screen so you can try them all out and see which one you like the most.

---

### Post by Rabidmonkey1 on 2009-01-19
Mint is a very nice version based off Ubuntu.  It comes with several enhancements out of the box that make it particularly user friendly, such as the mint installer, which allows you to install things like google earth and skype very easily.  As far as playing media, you'll probably need to download codecs at some point anyways (from the medibuntu repository), but mint has the edge on plain vanilla ubuntu, out of the box, anyways.

As far as your card is concerned - this is the most important thing: Googling the make of your card will generally work to see if it is compatible with ubuntu, but there's also the Ubuntu Hardware Compatibility list at [http://www.ubuntuhcl.org/]("http://www.ubuntuhcl.org/")

But yes, I'd say give mint a whirl.  I think you'll be pleasantly surprised.

---

### Post by albinootje on 2009-01-19
> **holdencaulfield said:**
> My main problem has always been configuring my wireless network card. I have an old Dell (Inspiron B120) and an equally old wireless network card, although I am unsure which one it is. 

Please boot from your Ubuntu installation cdrom, choose the "try without installing" live session.
Fire up a terminal, and post the output of the following :
```

sudo lshw -C network
lspci
lsusb

```

Then we can tell you whether this wifi card is gonna work or not, and how much effort it is gonna take to make it work.

---

### Post by Montblanc_Kupo on 2009-01-19
I can't see any legality issues with Mint, not sure what you're getting at.

Personally, I would suggest Ubuntu to get started. It's well supported and easy to use. The add / remove function makes installing and uninstalling software pretty easy and it's very stable in My experience.

If you want a new window manager, it's really simple to add them using synaptic or apt-get. I used apt-get to install kde, xfce, fluxbox, and englightenment to play with... all it really took was a couple terminal commands and it did the rest.

I'm not sure what you're friend is getting at... but Ubunutu is very customizable... it is a linux distro after all. 

Wireless networking is a little trick to get working on pretty much all linux from what I have seen... but not impossible.

---

### Post by Sealbhach on 2009-01-19
Ubuntu doesn't ship certain proprietary codecs because there's some issue that it might not be legal to *distribute* them in some countries. They leave it to the user to decide to download them - or muddle along without them.

I don't think it's anything to worry about though.


.

---

### Post by holdencaulfield on 2009-01-19
> **albinootje said:**
> 
Then we can tell you whether this wifi card is gonna work or not, and how much effort it is gonna take to make it work.

Okay, I will try that out, and then post my findings. 

> **Montblanc_Kupo said:**
> 
I'm not sure what you're friend is getting at... but Ubunutu is very customizable... it is a linux distro after all. 

He said that GNOME was built into Ubuntu so it's hard to change, but maybe he was wrong. He's really good with computers though, so it may have just been his unbiased opinion.

---

### Post by Montblanc_Kupo on 2009-01-19
> **Sealbhach said:**
> Ubuntu doesn't ship certain proprietary codecs because there's some issue that it might not be legal to *distribute* them in some countries.

My understanding was that it wasn't because of a legality issue for distribution, but the fact that they weren't free, open source codecs more than anything.

Regardless, to install all of them in Ubuntu after the fact takes one apt-get line :)

> He said that GNOME was built into Ubuntu so it's hard to change, but maybe he was wrong. He's really good with computers though, so it may have just been his unbiased opinion.

Well.. Gnome is **pre-installed** with Ubuntu... KDE with Kubuntu... and XFCE with Xubuntu. I don't find Gnome all that hard to configure, personally. I believe the default install for gentoo (which you said he was using) is xfce. Regardless... installing and using different desktop environments is pretty easy to do if you want... although, I have very little issue with Gnome so far.

---

### Post by holdencaulfield on 2009-01-19
I'm downloading Ubuntu 8.10 as we speak right now. It looks like it's going to take a little while, for it to download though. I assume that it's possible to change GNOME to Fluxbox after everything is up and running?

Okay, if you say it's easy, then it shouldn't be too difficult, I guess I should worry about seeing if I can get it working first. But that's something I really want to do, is have an amazing looking desktop, it's fickle, but I'm into ascetics.

---

### Post by Terl on 2009-01-19
Sure, you can download fluxbox via synaptic package manager once you are set up and ready to go.

---

### Post by Sealbhach on 2009-01-19
You can have lots of different desktops installed, just choose the desktop you want to use when you login.


.

---

### Post by albinootje on 2009-01-19
> **holdencaulfield said:**
>  He said that GNOME was built into Ubuntu so it's hard to change, but maybe he was wrong. He's really good with computers though, so it may have just been his unbiased opinion.

He's wrong. ;-) 
It's very easy to use something else than Gnome in Ubuntu, it's just a matter of installing other software, and then choosing another session at the Display Manager login.

See here :
[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

and see also the titles at the left of this article, like :
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde) etc.

---

### Post by holdencaulfield on 2009-01-19
> **Terl said:**
> 
Sure, you can download fluxbox via synaptic package manager once you are set up and ready to go.

Cool

> **albinootje said:**
> 
He's wrong. ;-) 
It's very easy to use something else than Gnome in Ubuntu, it's just a matter of installing other software, and then choosing another session at the Display Manager login.

Well maybe i just misunderstood him, but regardless, he showed me his Gentoo OS on his system, and it was pretty sweet. 
-------------------------------------------------
Well it's taking longer than I thought to download this, maybe it's my internet, but regardless how easy is it to have one of those amazing desktop appearances like you see on the screenshots on the internet sometimes? Do you have to be good with photoshop, or can you just find them on the internet?

It looks like according to that, you can make a different desktop environment your default too? Does it work for fluxbox too, because I don't think there is an "official" Ubuntu fluxbox environment?

---

### Post by Montblanc_Kupo on 2009-01-19
> **holdencaulfield said:**
> I'm downloading Ubuntu 8.10 as we speak right now. It looks like it's going to take a little while, for it to download though. I assume that it's possible to change GNOME to Fluxbox after everything is up and running?

Either using synaptic or from the terminal with:

```
sudo apt-get install fluxbox
```

> Okay, if you say it's easy, then it shouldn't be too difficult, I guess I should worry about seeing if I can get it working first.

You can always play around with the live cd before you install as well to get a taste for the OS and it won't affect your currently installed OS at all.

> But that's something I really want to do, is have an amazing looking desktop, it's fickle, but I'm into ascetics.

In My experience... fluxbox is the most aesthetically unappealing window manager ever. It's designed to be very lightweight. Gnome starts out kinda bland, IMO, but it's easy to tweak it and make it pretty slick. Also, coming from using either mac or windows, gnome will be easier to use than things like fluxbox I think.

> Well it's taking longer than I thought to download this, maybe it's my internet, but regardless how easy is it to have one of those amazing desktop appearances like you see on the screenshots on the internet sometimes? Do you have to be good with photoshop, or can you just find them on the internet?

There are tons of places to just download things. Check out [http://www.gnome-look.org](http://www.gnome-look.org)

> It looks like according to that, you can make a different desktop environment your default too? Does it work for fluxbox too, because I don't think there is an "official" Ubuntu fluxbox environment?

Yes. Or you can choose which one you want as you login.

---

### Post by holdencaulfield on 2009-01-19
Well I will play around with it, that's the fun part, but first I have to see if I will actually be able to install it with my computer!

---

### Post by holdencaulfield on 2009-01-19
You're right some of those are very interesting, they hardly even look like the bland basic GNOME that is installed with Ubuntu. Is it as easy as just downloading some one elses work that they have put up on the internet, to change the layout?

---

### Post by albinootje on 2009-01-19
> **holdencaulfield said:**
>  Well maybe i just misunderstood him, but regardless, he showed me his Gentoo OS on his system, and it was pretty sweet. 

Good! :)

Concerning Gentoo Linux, a little warning.. only try Gentoo when you really have way too much time on your hands.
I've used Gentoo Linux in the past, and I consider it to be *very* good, if only for their cool documentation, but you will need *time* (to read and "adapt") even if you try to use stage3 and packages only.

Here's some geeky comic serie about Gentoo :
[http://www.ubersoft.net/comic/kp/storyline/installing-gentoo](http://www.ubersoft.net/comic/kp/storyline/installing-gentoo)
Scroll down till the very end of that page.

---

### Post by holdencaulfield on 2009-01-19
Okay I entered all of those things on the terminal on Ubuntu, and I saved them on OpenOffice on my flashdrive, but I can't figure out how to open them on Windows now, so that I can post them. Is there a way?

---

### Post by Rabidmonkey1 on 2009-01-20
> **holdencaulfield said:**
> Okay I entered all of those things on the terminal on Ubuntu, and I saved them on OpenOffice on my flashdrive, but I can't figure out how to open them on Windows now, so that I can post them. Is there a way?

I'm assuming you're referencing the terminal commands from before to find out your wifi card info?  No, there is no way to get that info if you saved it on a live CD session - they aren't persistent - that is, once you end a live CD session, nothing is saved.  

What I would suggest is starting up the live CD again, re-running the commands, and then saving to elsewhere, like on a mounted USB disk, or even emailing it to yourself if you can.  Firefox will work on the live CD - you just need a connection  Otherwise, you might have to end up writing the info down with a pen and paper.  If you have no wifi when you boot up the live cd, can you hook up your computer to your router directly via Ethernet cable?  If you can, you'll have a connection and be able to email it to yourself.

---

### Post by Montblanc_Kupo on 2009-01-20
> **holdencaulfield said:**
> Okay I entered all of those things on the terminal on Ubuntu, and I saved them on OpenOffice on my flashdrive, but I can't figure out how to open them on Windows now, so that I can post them. Is there a way?

Crazy thought here... but maybe try opening them in the same program that you used to save them? :)

---

### Post by Sealbhach on 2009-01-20
> **Montblanc_Kupo said:**
> Crazy thought here... but maybe try opening them in the same program that you used to save them? :)

You can save documents in Word format in Open Office by using "Save As" and choosing the Word file format.


.

---

### Post by albinootje on 2009-01-20
> **holdencaulfield said:**
> Okay I entered all of those things on the terminal on Ubuntu, and I saved them on OpenOffice on my flashdrive, but I can't figure out how to open them on Windows now, so that I can post them. Is there a way?

Yes. Install OpenOffice on your MS-Windows installation.
[http://www.openoffice.org/](http://www.openoffice.org/)

After that open the openoffice document from your flashdrive.
Next time it's easier to use "gedit", a text editor, during the live session, and save as plain text (.txt).

---

### Post by hyper_ch on 2009-01-20
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Montblanc_Kupo on 2009-01-20
> **Sealbhach said:**
> You can save documents in Word format in Open Office by using "Save As" and choosing the Word file format..

Yeah... I'm well aware... but then, I wasn't the one having the problem opening the files.

---

### Post by holdencaulfield on 2009-01-20
Alright, I'm going to get home soon, and copy those entries again from just booting Ubuntu and save them as text, and then I will post my results back here. I hope that someone can help me figure out how to get the wireless network card working. Will I be able to connect to the internet if I just plug in my ethernet cable from the modem?

---

### Post by holdencaulfield on 2009-01-20
Here are my results: 

sudo lshw -C network
```

*-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:90:98:b0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:3e:16:2e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 52:a0:de:ff:7a:5a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

lsusb
```

Bus 005 Device 002: ID 13fe:1a00 Kingston Technology Company Inc. 512MB/1GB Flash Drive
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by Sealbhach on 2009-01-20
Hi, perhaps try this method here:

[http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html](http://www.sampbar.com/2008/11/broadcom-bcm4318-ubuntu-intrepid.html)

It looks a little messy but you might enjoy the process of discovery. Keep asking here if you get stuck.;)


.

---

### Post by holdencaulfield on 2009-01-20
> **Sealbhach said:**
> 
Hi, perhaps try this method here:

Should that presumably work with what I'm trying to do, and my specific problems?

---

### Post by Sealbhach on 2009-01-20
> **holdencaulfield said:**
> Should that presumably work with what I'm trying to do, and my specific problems?

Your lshw is showing

```

product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
```

as your wireless card so yes, it seems to be what you need to do.


.

---

### Post by holdencaulfield on 2009-01-21
I encountered a problem during installation. I was fine until I got to the part when it asked me to partition the hard drive, and I chose 10gigs for the Ubuntu partition, and it began to do this, but I received an error message saying that there was a problem with the partition editor, and I couldn't go any further.

---

### Post by Dwarkesh on 2009-01-21
Hi,
I am not sure if this is the right forum to ask this question. Please redirect me to other forum if this is not correct place.
I am new to Ubuntu Linux. I have installed Ubuntu 8.10 and the installation went fine. But the problem now is that the audio and videos are not working properly. When I open any video file or audio file the sound comes as if its sticking and moving very slow. It seems like the video or audio is moving in too low speed and due to which I am not able to hear and see it properly. Can you please help me know the cause of this problem.

Thanking You,
Dwarkesh Marakna

---

### Post by yobird42 on 2009-01-21
> **holdencaulfield said:**
> I encountered a problem during installation. I was fine until I got to the part when it asked me to partition the hard drive, and I chose 10gigs for the Ubuntu partition, and it began to do this, but I received an error message saying that there was a problem with the partition editor, and I couldn't go any further.

you could try partitioning your hard drive before installing ubuntu. Gparted is a live cd that will partition it. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Dwarkesh on 2009-01-21
Can anyone help me for my previous post....

---

### Post by holdencaulfield on 2009-01-21
> **Dwarkesh said:**
> 
Can anyone help me for my previous post....

Try opening up your own thread with a title of what you need help with. That should get you some responses. 

> **yobird42 said:**
> 
you could try partitioning your hard drive before installing ubuntu. Gparted is a live cd that will partition it. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Yes, I think that I could do that. I'm not really sure I know how to use that program though. Do you think there is a way for me to get it done with the Ubuntu installation disk, or should I go ahead with that. Could there possibly something wrong with my disc? I checked it for errors, and it didn't have any. I know that one time I installed Ubuntu before I had no problems with partitioning.

---

### Post by yobird42 on 2009-01-21
> **holdencaulfield said:**
> Try opening up your own thread with a title of what you need help with. That should get you some responses. 


Yes, I think that I could do that. I'm not really sure I know how to use that program though. Do you think there is a way for me to get it done with the Ubuntu installation disk, or should I go ahead with that. Could there possibly something wrong with my disc? I checked it for errors, and it didn't have any. I know that one time I installed Ubuntu before I had no problems with partitioning.

Can you be more specific with your problem? When does it occur and what happens? 

you can try to install again, download a new cd, or partition it with another program.

---

### Post by holdencaulfield on 2009-01-21
> **yobird42 said:**
> 
Can you be more specific with your problem? When does it occur and what happens? 

you can try to install again, download a new cd, or partition it with another program.

Well I just don't exactly know what the problem is, so it's hard to be very specific with what the problem is. Basically just when I go to partition the hard drive it won't do it, and says that there has been an error. That's really all I know.

---

