---
title: "After 8.10 upgrade lost lan and wireless"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by warwon on 2008-11-06
I've been able to get the wireless turned on again, but when it runs the whole system slows right down and take 20+ mins to boot.

Lan does not gt a connect.

Dell Inspiron 1720, with a broad com wireless.

Kernel 2.6.27-3-rt

I've tried the official drivers, to windows drivers no luck.

Help!?

---

### Post by warwon on 2008-11-07
Sighs.

I spent about ten hours working on this nothing so far.

I've tried the fcwcutter deb files, I've tried a ndiswrapper.

Nuttin will work, as soon I get the wireless card working the entire system slows down, when the driver is disable the system boots normally.

I've lost my lan interfaces, and my wireless.

I have to much data on this laptop and with no means to backup it up I'm screwed.

I'm not seeing any better solutions then formatting, but then we'll lose data that is too crtical.

Any ideas?

---

### Post by Riqz on 2008-11-07
there's a lot of howto's all around the web so google you card model + ubuntu 8.10 and you should be alright.

Unless ofcourse you have a broadcom 4318 like me... then you're screwed... I've been trying for a few weeks now... and nothing yet...

---

### Post by puppy on 2008-11-07
This is a *new* problem - kernel updates on 6 November and now have no wireless interface listed in network manager or elsewhere in the network tools... it's gone

---

### Post by MewRS on 2008-11-07
Same problem here...
I just got a fresh install of Kubuntu 8.10.

It was working perfectly until yesterday night...
Kubuntu prompted me to update and then I said yes...

Today I've started my computer and "eth1" (which was my wireless card) suddenly disappeared.

I was using the Restricted Driver of Broadcom 43xx.
It was perfect but now it disappeared!

Here I'm using an HP Pavilion dv9000 (dv9317cl) and I spent all of my day working on that and nothing seems to work...

I read a lot of forums and saw a guy saying that when he booted up the pc only with AC cord, without the battery, the wireless turned on.
I tried the same here and it worked!
But after another reboot, it went back to nothing...

Tried then the ndiswrapper... Nothing...
It doesn't even shows my adapter on ifconfig...

WHAT CAN WE DO?!

---

### Post by Ferrat on 2008-11-07
> **puppy said:**
> This is a *new* problem - kernel updates on 6 November and now have no wireless interface listed in network manager or elsewhere in the network tools... it's gone

yeah the latest kernel update seems to have broken many wireless, my own is very very unstable =/ 


btw love your signature ;D

---

### Post by MewRS on 2008-11-07
> **puppy said:**
> This is a *new* problem - kernel updates on 6 November and now have no wireless interface listed in network manager or elsewhere in the network tools... it's gone
Can we revert this?

---

### Post by puppy on 2008-11-07
Btw for info my wireless card is the Intel 3945ABG so it seems to affect cards across the board, and sorry for being so snappy with that last post - very dissapointing this morning to switch on and to have no wireless :(

I think it was a kernel backports update yesterday evening that did it, but I can't be sure. Fortunately Network Manager continues to recognise the usb 3g dongle that I have (introduced in 0.7) as a modem interface (ppp0) so that behaviour hasn't changed, and I can still get onto the 'net. I haven't had the opportunity to test wired ethernet behaviour yet...

---

### Post by gmstalk on 2008-11-07
I am in the same bucket. Wireless worked great on 2.6.24-19. It broke in 2.6.24-21 and 2.6.27-7 (8.10) only made it worse because I cannot go back to 2.6.24-19. I am pretty frustrated. 

I tried all the voodoo posts like many of you. Blacklist this and that, rmmod this, but a bag on my head and cluck like a chicken, and I got nothing (but my hiccups stopped).

I am on a Dell Inspiron 1521 with 
lspci: 0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
lshw -C Network:  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

Ifconfig shows no wlan0 any more.

This ethernet cable is a leash! A leash I tell you! Set me free!

---

### Post by MewRS on 2008-11-07
Maybe if we can downgrade the kernel via synaptics, we can handle that...

---

### Post by MewRS on 2008-11-07
Very weird...

I booted up again without any change..
The wireless switch was off...

I don't know why, but I turned it on and the light went blue!
eth1 is alive again...

** Booted under following circunstances
* Wireless switch off
* Battery on
* Power cord on
* Without any USB component pluged in
* Without pressing the button to enter at GRUB (sometimes it changes the boot behavior, LOL)

But probably if I reboot it will lose eth1 again!

Strange... Very strange... 
Tonight I will try an kernel downgrade.

If I can make it, i'll leave a reply!

**EDIT**

Just as I expected...

Rebooted the PC and then wireless did not come again...
I'm getting tired of this...

I'll wait fot the laptop to cool down and retry...

---

### Post by gmstalk on 2008-11-07
> **gmstalk said:**
> I am in the same bucket. Wireless worked great on 2.6.24-19. It broke in 2.6.24-21 and 2.6.27-7 (8.10) only made it worse because I cannot go back to 2.6.24-19. I am pretty frustrated. 

I tried all the voodoo posts like many of you. Blacklist this and that, rmmod this, but a bag on my head and cluck like a chicken, and I got nothing (but my hiccups stopped).

I am on a Dell Inspiron 1521 with 
lspci: 0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
lshw -C Network:  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

Ifconfig shows no wlan0 any more.

This ethernet cable is a leash! A leash I tell you! Set me free!

I now have wireless working. I am not sure what combination did the trick, but I think the solution was very simple. 

I use ndiswrapper for my wireless driver. I used the GUI for gnome (sudo apt-get install ndisgtk). I removed the driver. Then I installed the driver again. 

I did do many other things like black listing wl and ssb, but I think that made no difference since I do not have the wl module and ssb loads by the kernel. 

Now I just cannot get the wired connection working. I cannot load B44 because of ssb.

---

### Post by warwon on 2008-11-07
Like I said this is really messed me up.

I can't even access my lan now.

If I boot into recovery mode I can down updates etc.. thats about it.

Anyways I get the driver to install for the wireless, and I shutdown the machine.

If I leave the wireless off, the light comes on. It shouldn't since it off, when I turn it on I the light goes off.

Then I can see wireless network, but doesn't connect and just locks up.

I've tried the fcwcuttter, ndiswrapper, I've done everything I have done in the past to make this machine work since the old 6.04 but this 8.10 just wants me to smash it.

My wife getting upset as she can't use her laptop now. As it keeps locking up non-stop with that wireless driver. when I disabled it works fine, but with no lan whats the point of it.

---

### Post by warwon on 2008-11-07
Now I known the old kernal *.24 worked well.

How would I do a downgrade on the kernel back to a older version in recovery mode, or using debs.

remeber I can access usb only in the gui, or the lan only in reocvery.

I need to recover this laptop

---

### Post by MewRS on 2008-11-07
I'm getting crazy!

This is an intermittent problem..

Right now I'm writing via wireless :(

Sometimes it starts, sometimes not.


But, looking in the forums I found this topic talking about the kernel downgrade...

[http://ubuntuforums.org/showthread.php?t=261289](http://ubuntuforums.org/showthread.php?t=261289)

I'll try this one too!

Hope it works for us!
(I'll do it right now... I just have to do some backups! :P)

G'luck!

---

### Post by warwon on 2008-11-07
Thats what I thought for down-grading a kernal. Should've remeber that duh.

Well into recovery mode I go, hopefully i can rebuild the machine without backing up the data.

---

### Post by MewRS on 2008-11-07
Uh-oh...
Tried the downgrade but the downgraded kernel did not start the X, because of the driver...

Time to format and start again...

LOL! =P

---

### Post by hclaire on 2008-11-08
I had the same problem. 

I searched around and did the following several things, and it works for me now!!!

Download linux-firmware_1.2_all.deb to get my network configuration back

sudo gedit /etc/NetworkManager/nm-system-settings.conf
under [ifupdown], change managed=true
reboot

And then follow this website
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
to remove and reinstall the windows driver

---

### Post by warwon on 2008-11-08
I downgraded the kernel last night.

I got the lan working, wireless is working but being fussy.

I can get the wireless working but it's doesn't seem to connect.

Might fiddle with it tonight.

My sound is broken now to, yah wondering how to fix that.

:guitar:

---

### Post by MewRS on 2008-11-08
Bad news...

Unfortunately I made a fresh install and even in that wireless doesn't pop out...

Man... It was working so well (out-of-the-box) in the 8.04...
I downgraded the kernel to 2.6.27-3-rt (faster) and nothing happened...

So I'll try to figure out what to do... Try the ndiswrapper again and if that doesn't works...

Probably going to Kubuntu 8.04 Remix...

Boo-hoo....

---

### Post by hennessy99 on 2008-11-08
Having similar issues with a twist.  I installed 8.10 with no problems.  Network was working with no problem.  Spent some time personalizing the system.  I start the computer last night and no network with Ubuntu.  The night before I applied a few updates with update manager.  Now for the twist, I cannot get back the lan with any Ubuntu.  I tried running from live CD and even reinstalled Ubuntu . . . nothing.  It's not the card, because I dual boot with Windows and network works with Windows.  I have a Realtek RTL8186/8111 integrated card.

---

### Post by warwon on 2008-11-08
I manually pulled down *.deb files for linux-image-2.6.24-16-rt

With the headers, etc of course.

I was able to get everything working asap (Minus the wireless lol, it's working but cranky)

---

### Post by warwon on 2008-11-08
This new 8.10 update seems very broken.

Even from Ubuntu blah to 8.04 was never this bad.

Very unhappy

---

### Post by hennessy99 on 2008-11-08
> **hennessy99 said:**
> Having similar issues with a twist.  I installed 8.10 with no problems.  Network was working with no problem.  Spent some time personalizing the system.  I start the computer last night and no network with Ubuntu.  The night before I applied a few updates with update manager.  Now for the twist, I cannot get back the lan with any Ubuntu.  I tried running from live CD and even reinstalled Ubuntu . . . nothing.  It's not the card, because I dual boot with Windows and network works with Windows.  I have a Realtek RTL8186/8111 integrated card.
Fixed my issue using with this
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

Turns out my problem had to do with me dual booting and Windows disabling the network card.

---

### Post by warwon on 2008-11-09
Anyone got any ideas on how to rebuild the audio stuff, as I get a gstreamer error can't connect, when trying to get the audio on.:confused:

---

### Post by rynyeager on 2008-11-09
I am a very green n00b and am having this issue as well. I have Vista and hardy heron dual booting on an acer aspire 7520. I have a n Atheros WLAN 802.1g card. I cannot find any support to make this work. Any ideas?

---

### Post by nephish on 2008-11-09
i am in the same boat, dell laptop, ubuntu-update-manager said reboot, no lan. Ok, so i am re-installing the OS. 8.10, just will disable the update-manager till this gets resolved.

will keep posted.

---

### Post by MewRS on 2008-11-10
I heard that in Acer with Atheros you can solve the problem with the MadWifi...
I dunno if it works on Broadcoms, but...

We already tried everything! :P

---

### Post by warwon on 2008-11-15
Nice I have no way to backup the hard-drive

It has data that can't be just dropped

I can't fix a issue with this machine.

8.10 is da-bomb, going to take me weeks to fix this.

---

### Post by warwon on 2008-11-16
So yah...

Last night I fixed everything.

I pushed out a genetric kernel and bam done.

Linux-image-2.6.27-8

Somthing like that, and got rid of the RT kernels.

From there the wireless started to work naturally, and I was able to rebuild AWN, and get open office 3.0 fixed.

Not a single help from community but it's solved.

Stupid 8.10

---

### Post by sadjack on 2008-11-16
Is this really a kernel problem? Could it be Network Manager is at fault?

I have 2 hdd, one with 8.04 which works perfectly, and one with 8.10 which will not let me connect my wireless, even though both are configured the same.

Looking for a guide to remove network manager and installing wireless setting at the command line. Anyone know of one?

---

### Post by gmstalk on 2008-11-30
The LAN part is fixed in 2.6.27-8. I went to system> administration> software sources, on the updates tab, I chose pre-released updates (intrepid-proposed). Then I ran the update manager and let it rip. 

Wireless is still janky for me, but I had success in by going to system > administration > windows wireless drivers (I use ndiswrapper) and removed my wireless driver. Then I installed it once more. It still fails with many WPA2 sites, but at least I have wired LAN again.

---

