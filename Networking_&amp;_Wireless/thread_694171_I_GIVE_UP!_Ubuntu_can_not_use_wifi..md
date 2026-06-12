---
title: "I GIVE UP! Ubuntu can not use wifi."
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by BillB on 2008-02-11
I give up.  I would have LOVED to stop using Microsoft, but Ubuntu is worthless to anyone who isn't an experienced software engineer.

I have been jerked around by people who don't know what they are doing, and contradictory instructions here/everywhere (and in the 7.10 OS program itself) for 5 SOLID DAYS.
Many of the people here must be working for Microsoft....because they sure don't want a novice becoming successful with Ubuntu, and enjoy sending unsuspecting people on wild-goose-chases trying to connect there wifi!
 
Ubuntu, is at best, a novelty for enrineers and those w/ dual boot Microsoft systems.
I'm not RICH enough to have the drive space to waist for that (Ubuntu takes MORE space than the Microsoft 98SE I was using).


I'm cleaning/nukeing my hard drive of Ubuntu as soon as I get off here (I was trying a clean installation) and I'm going back to Microsoft.  At least it can connect to the internet with Microsoft!

Just look at all the "give up" posts here....

---

### Post by jrusso2 on 2008-02-11
I have a feeling you have a braodcom wireless?  There are other distros with much better wifi support then Ubuntu.  This is do to the silly FSF only policy.

Other linux have a more realistic policiy and are willing to include the firmware and drivers so wireless works much better.

Two examples.

PCLinuxOS and Mandriva 2008 one

---

### Post by shad0w_walker on 2008-02-11
Stop whining and go bitch at the hardware vendors. It is physically impossible to test Ubuntu with every bit of hardware and complaining and throwing a tantrum isn't going to help. Just go back to windows and stop complaining.

Also, don't compare an OS from 1998 to 2007. What the hell logic you are using for that is broken. It's a slither under TEN YEARS OLD. It will be  alot smaller, it also has alot less features. 

The problem here is very clear. You are using a Wifi card where the vendor doesn't give a crap about Linux, it's their issue not ours. We try to help you and you bitch. 

Get over yourself and realise you haven't payed a damn penny for what you have got. If you want to whine for getting free things why don't you go and shout at the trees for giving you oxygen that you had to learn how to breath all by your self.

---

### Post by BillB on 2008-02-11
I just went to 'shipit' to cancil my request, but it was sent out 56min ago.

THAT's the kind of luck I have w/ Ubuntu.
Maybe Kubuntu will turn out to be better that what I have now?
(some day)

---

### Post by BillB on 2008-02-11
I DID "pay" for my Ubuntu CD.
And asked what wifi card works best (several times) shad0w....no response, other that look it up yourself, (w/ outdated statistics).

Time to NUKE Ubuntu!

---

### Post by DUDE_2000 on 2008-02-11
Guess What my internet connection is- Broadcom Wireless

If you wanded some help I could offer it.
If you have a rare wireless card try simplymepis

---

### Post by anindya_m on 2008-02-11
Broadcom is notorious for not releasing a linux driver (if anyone is listening, this is very, VERY bad). While I personally feel such a company should be blacklisted, sometimes you don't have a choice, like laptops with built-in wireless.

Mint linux is supposed to have the broadcom firmware built in. Also most broadcom cards work fine with ndiswrapper, if the bcmxxxx driver does not work (although I find it mostly works now). I have friends for whom I have set up (one of) both drivers on Ubuntu.

You can use the lspci command to check if you have a Broadcom card.

---

### Post by Roaster on 2008-02-11
"I have been jerked around by people who don't know what they are doing, and contradictory instructions here/everywhere (and in the 7.10 OS program itself) for 5 SOLID DAYS.
Many of the people here must be working for Microsoft....because they sure don't want a novice becoming successful with Ubuntu, and enjoy sending unsuspecting people on wild-goose-chases trying to connect there wifi!"

This is a valid statement about this forum! While there are many people that are knowledgeable about Linux and are more that willing to help noobies, there are also, a lot of people giving advice and answers that really do not know what the hell they are talking about! If you do not know the answers to peoples' questions Please don't post just to up your bean count! All I can say, as, I DO NOT have the answers is, Don't Give Up! You will learn and when you do you WILL like Ubuntu or whatever flavor of Linux you settle on. It takes a while. Just keep tryin'!  JMO.

---

### Post by digitalhillbilly on 2008-02-11
Hey Bill.... Don't give up! Linux is much more useful than an engineers hobby. I set up ubuntu for many people and have helped many others switch over to it completely. Lots of excellent things about it and I bet nearly everything you expect to do with your computer you can do in Linux. Plus it's free, plus the support is unmatched, plus you will be able to use modern software on older hardware (try that in win98 or OS9), plus, plus, 

I had a bitch or a time getting an old linksys pci wifi (broadcom) going but did in the end. I think I used madwifi and wicd on that machine. The thing to remember about Linux is you'll spend more time setting it up in the beginning but less time maintaining it over time. Also us newbies will spen more time doing something just because of lack of experience. You'll lean a lot about hardware and software just by getting your computer going. The next computer you set it up on will benefit from this. Once you get your wifi going build a system back-up and if your machine bombs you just restore from your back up and everything is working. 

whatever.... just thought I'd post to maybe give a little inspiration.

dh

---

### Post by sir4taye on 2008-02-12
Ok bill, get a grip on yourself! I have just got a wierd configuration to work and it took a day or so to search it out. If you have a 4300 series broadcom wireless card check this out....
everything inbetween # signs (without the #signs themselves) needs to be typed into a terminal screen (under applications then accessories then terminal -this is the command line, somewhat like dos)

1)you must uninstall ndiswrapper & bcm43xx-fwcutter

#sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9#
#sudo apt-get remove bcm43xx-fwcutter#

2)Add bcm43xx to the /etc/modprobe.d/blacklist file

#sudo vim /etc/modprobe.d/blacklist#
a text editor will activate add this line "blacklist bcm43xx" (without "") by hitting i once and moving to the bottom and typing the new line then hit escape then enter ":wq" (without the "")

3)Reboot
#sudo reboot#

Download driver for BCM94311MCG wlan mini-PCI here:
http://www.stosha.net/WLANBroadcom.tar.gz or
http://stosha.stylet-software.com/WLANBroadcom.tar.gz

#cd ~/home/(yourusername)/Desktop#

#tar -xzvf WLANBroadcom.tar.gz#

4)move the folder WLANBroadcom to your home directory

#mv WLANBroadcom/ /home/(yourusername)/#

5)Install ndiswrapper from source :

#sudo apt-get update#
#sudo apt-get install build-essential#
#sudo apt-get install linux-headers-`uname -r`#
#sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build#
#mkdir -p ~/bcm43xx/ndiswrapper#
#cd ~/bcm43xx/ndiswrapper#
#sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz?modtime=1193538074&big_mirror=0#
#tar -xvzf ndiswrapper-1.49.tar.gz#
#cd ndiswrapper-1.49#
#make distclean#
#make#
#sudo make install#

6)Install windows driver (BCM94311MCG wlan mini-PCI) with ndiswrapper

#cd /home/yourname/WLANBroadcom/#

#sudo ndiswrapper -i bcmwl5.inf#

#ndiswrapper -l#

#sudo vim /etc/modules#
an editor will activate add this line "ndiswrapper" (without "")

#sudo modprobe ndiswrapper#

#sudo ndiswrapper -m#

7)Reboot
#sudo reboot#

I thought I'd never get my model working, but.....
:guitar:
Try eating a sandwich. It sounds like your brokendown bloodsugar is low.

Compaq f700 (f730us), athlon 64x2, nvidia chipset nic and video, broadcom 4311 mini-pci wlan w/external switch, tri-boot (though I can finally use Ubuntu fulltime now that the wireless works!!!!!)

---

### Post by iancvt55 on 2008-02-12
I had 5 attempts with Ubuntu and WiFi before I got it to work but stick with it. My wifi card has a ralink driver and cost less then $20. As others have said the amount of support you get through these forums is amazing.

---

### Post by BillB on 2008-02-12
It's all over now, I wiped out my HD and installed XP.

---

### Post by dca on 2008-02-12
...and I just added a bean! :D

---

### Post by lespaul_rentals on 2008-02-12
Bye!

---

### Post by tewest99 on 2008-05-01
I'm still trying to figure out the Broadcom thing for my wireless.  If it doesn;t work then perhaps I can get a USB wireless adapter that comes with a driver CD and use ndiswrapper to load it.  Seems like a simple solution and it beats whining at everyone.

---

### Post by tewest99 on 2008-05-01
> **BillB said:**
> It's all over now, I wiped out my HD and installed XP.

Probably a better solution for the impatient ...

---

### Post by spawnywhippet on 2008-05-04
I'm having a lot of the same issues and thoughts as Bill. I have 2 identical Thinkpad T40's, installed in the same way using the same 8.04 CD, one works with WPA wifi, the other one won't run USB hard drives or WiFi. Its not a hardware problem because if I swap drives, the problems move to the other machine. I cannot find a single difference in the config though.

---

### Post by GavinZac on 2008-05-04
> **spawnywhippet said:**
> I'm having a lot of the same issues and thoughts as Bill. I have 2 identical Thinkpad T40's, installed in the same way using the same 8.04 CD, one works with WPA wifi, the other one won't run USB hard drives or WiFi. Its not a hardware problem because if I swap drives, the problems move to the other machine. I cannot find a single difference in the config though.

Re-install? Sounds like a bad installation, a corrupted file or something.

---

### Post by Twitch6000 on 2008-05-04
> **BillB said:**
> It's all over now, I wiped out my HD and installed XP.

Wow you think just cause ubuntu didn't work you had to go back to windows.
When your only problem was wifi,well PClinucOS has great support for that as do alot of others you do Belize ubuntu is not the only one right?Oh wait no you don't cause you think we work for microsoft LOL.Although if you hate them why use them <.<?Why not use a mac or freebsd?Or solaris.OR even reactos.I mean come on never give up lol.

---

### Post by spawnywhippet on 2008-05-04
> **GavinZac said:**
> Re-install? Sounds like a bad installation, a corrupted file or something.

I have reinstalled it already, get the same problems still. I am 100% convinced its a driver or config issue, but after spending perhaps 40 hours trying to track down the difference, I am no closer.

---

### Post by GavinZac on 2008-05-04
> **spawnywhippet said:**
> I have reinstalled it already, get the same problems still. I am 100% convinced its a driver or config issue, but after spending perhaps 40 hours trying to track down the difference, I am no closer.
Maybe this is one of those "so  crazy it might just work" ideas: copy every file from the working one to the broken one, via an external hard drive or something?

---

### Post by spawnywhippet on 2008-05-04
I already thought of that, but the second problem is that I can't get it to recognise USB drives. 

An alternative is that I can remove the drive and put it in an enclosure, but I don't know what needs to be copied over.

---

### Post by steveneddy on 2008-05-04
> **BillB said:**
> It's all over now, I wiped out my HD and installed XP.

I thought you were gonna install 98?

I wonder how many times you looked at Google?

Many people use Broadcom wifi chips here and you may not have followed the directions correctly.

It has been my experience on these forums that people who post threads that start like this one 

either fail to follow directions properly or in the correct sequence, or maybe not every step.

I just hope that he downloaded the drivers for his machine for XP before he started looking for

any wireless drivers.

There are successful people that can run Linux and those that can't.

Those that can't usually buy Ubuntu preinstalled or go back to Windows.

I say go with whatever works for you.

---

### Post by MasterNetra on 2008-05-04
I've had no problems with Wifi with Ubuntu or Kubuntu (Hardy) Prehaps he/she should upgrade to 8.04.. and convert his system to Kubuntu. Not much lag over here :p

---

