---
title: "How a Ubuntu newbie got his WMP54GS to work."
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by siciliancasanova on 2007-03-11
I was searching around for a couple of days to get my WMP54GS PCI card to work.

As a completely new user it was not as easy as it ended up being, however in the end, it was really easy to install this card.

I am using Ubuntu 6.10 Edgy

1) Go to the [Linksys website]("http://www.linksys.com/servlet/Satellite?c=L_Product_C1&childpagename=US%2FLayout&cid=1115416939789&pagename=Linksys%2FCommon%2FVisitorWrapper") and download the latest driver for your card.

2)Go to **System > Administration > Synaptic Package Manager** and search for the program called WINE.  Once you have installed WINE, open the driver which is in .exe format and extract it with WINE.

3)Go to **System > Administration > Synaptic Package Manager** and search for NDISGTK and install this program.  It is the GUI for NDISWRAPPER.

4)Go to **System > Administration > Windows Wireless Drivers** and click "Install New Driver".  From there browse the recently extracted driver on your desktop or whatever location you extracted it to and find and open the .inf file

5)Go to **System > Administration > Networking** and enable and configure your wireless device.

---

### Post by HumbleGod on 2007-03-11
I'm a newbie who's taking the plunge next week, so this will come in handy for me. Many thanks!

---

### Post by siciliancasanova on 2007-03-11
I'm glad it helped.  I figured I'd give something back for all the help I got in the forums when getting set up.  This is a really nice community.

---

### Post by VeniceCA on 2007-03-12
Wow, it worked. It's so easy. For anyone else who is reading this post I will add that I had two .inf files - WMP54GS.inf & WMP54GSa.inf in the driver folder when I extracted it. I chose the WMP54GS.inf. I have been screwing around with this for days and was on my second wireless card. Here's a bit more info about my specific card: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller rev2.

Now I can get back to building my mythtv with wireless internet access.

Dude - U :guitar:

---

### Post by HumbleGod on 2007-03-15
Okay, so I gave this a shot...so far, no good. (And it seemed so plausible!) Though actually, I had to run it slightly differently--I don't have a wired connection, but my wireless connection through my Windows boot is still working, and I have a FAT32 partition for transferring files. So here's what I did to compensate:

1. I couldn't find a downloadable package ready for WINE, so I just downloaded the driver for my card from the Linksys website and unzipped it in Windows, moving the results to the FAT32 partition.

2. Found a package for NDISGTK, downloaded it to the FAT32 partition, then rebooted into Ubuntu and installed it.

3. I followed the steps for going to System > Administration > Windows Wireless Drivers and clicked "Install New Driver," then navigated to the Drivers folder in the Linksys files and picked one of the two .inf files.

However, this didn't do the trick--the light on my wireless card remains off, and I still can't make a connection. This is true for installing EITHER .inf file as the driver through NDISGTK.

Does anyone have any advice you could share? I'm not getting any responses in [my other thread]("http://www.ubuntuforums.org/showthread.php?t=384663") on the topic....

Thanks!

---

### Post by siciliancasanova on 2007-03-15
Ha ha, and actually I'm going to be editing this for reasons of stupidity I was messing around with my xorg file and the easiest way was to just reinstall, so I did.  Now my own instructions won't work for myself.  I haven't done ANYTHING different than last time, same driver, same process.  So when I get it figured out I will make the change.  Sorry :(

---

### Post by HumbleGod on 2007-03-15
Ack! Well, best of luck with that. The good news is, judging from the above posts, your method has worked for at least one person!

I'm seriously *this* close to ripping the wireless card out of my PC and throwing it into the street....

---

### Post by HumbleGod on 2007-03-16
Okay, it took two days, but I finally got mine to work thanks to _[some patient help]("http://ubuntuforums.org/showthread.php?t=384185")_ from **teaker1s**. Maybe what worked for me will work for you, so here goes. It only worked for me on a fresh install, so no guarantees otherwise:

1. Make sure you have a wired internet connection. Barring that, have the 6.10 alternate cd handy--the 386 cd has most of the packages you'll need, but the alt cd apparently has ALL the ones I needed. If you can't manage that, use another computer to browse [_here_]("http://packages.ubuntu.com/") to get any packages that you need, then move the packages to your Ubuntu system.

2. Download the latest driver for the WMP54GS. As of right now it's available [_here_]("http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1115416826820&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0993426820B03"). If you have a dual-boot system like me, expand the exe in Windows and move the DRIVERS folder to your Ubuntu system one way or the other. (Expanding with WINE per above probably works too, or put the folder on a USB drive. I created a FAT32 partition before installing Ubuntu, so I just dragged the folder there in Windows, then rebooted into Ubuntu.)

3. Get the latest ndiswrapper [_here_]("http://sourceforge.net/projects/ndiswrapper/"). Currently 1.38.

4. Follow [_this guide_]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show") by **frodoB**. Yeah, it says it's for BCM4311 drivers, but don't let that throw you off. Some tips:
[LIST]
[*]If you used NDISGTK prior to this, be sure to go to System ->Admin -> Windows Wireless Drivers and remove ALL drivers before starting Step 1. Then be sure to remove NDISGTK when removing ndiswrapper in Step 1.
[*]Newbie tip: To get the necessary packages off the install CD, type [FONT="Courier New"]sudo synaptic[/FONT] into the terminal, and when Synaptic opens up, go to Edit -> Add CD-ROM, and go from there.
[*] When you get to the parts on sp33008.exe and cabextract in Step 5, just remember that you've already extracted the drivers folder from your linksys exe. Move THAT folder to Home instead of making a new one called bcm4311, and replace all instances of 'bcmwl5.inf' in the guide with 'wmp54gs.inf.'
[*] When you get to the Testing portion (Step 7), don't panic if [FONT="Courier New"]iwconfig[/FONT] doesn't show a connection to your ESSID. Just finish up Steps 7 and 8, then follow the directions on installing Network Manager.
[/LIST]
Viola! All should be well after you install Network Manage (gnome) and reboot.

---

### Post by siciliancasanova on 2007-03-16
Looks good, I will be trying this later :)

---

### Post by HumbleGod on 2007-03-17
One word of advice: when you get the connection working, don't make the same mistake that I did and upgrade your kernel to 2.6.17.11. Everything's working well with 2.6.17.10, but the new kernel throws me (and others) for a loop....

---

### Post by siciliancasanova on 2007-03-17
Yeah I just posted a new topic (in beginner talk, better chance of getting help) describing what I've done, what my outputs are and how great some help would be.  I followed your guide, and some other guides that were quite similar, none of them have worked for me.  :(  Someone must know.

---

### Post by VeniceCA on 2007-03-17
I posted earlier in this thread and wanted to make notes since I see that it's still being added to (although it looks like you guys are going elsewhere for answers). These instructions are still working for me. Thought however I would add a few notes.

#1 When I used these instructions it was on a very fresh install. A number of postings regarding wireless troubleshooting suggested this. Although I hated to do it I think it was critical. I had done so much work getting wireless to work I could have easily gunked up something along the way.  It may have been the first or second thing I did after installing a fresh version of 6.10 and then doing the upgrades (to be clear I let Ubuntu do it's thing and right after the install I let it upgrade everything - whatever that may have been). So I was at kernel 2.6.17.11 when I followed the first set of instructions in this post.

#2 I see notes about installing 1.38 of ndiswrapper, but I got it though Synaptic and is says it's 1.8. Dunno what's up with that, maybe I don't know how to read the version numbers, but I do know that I had worked with 1.1 at one time and that definitely didn't help me. Maybe this is something to follow up on.

#3 Now that it's working I must say it isn't flawless. On some startups, let's say as high as 25%,  I don't have a wireless connection. I power down everything - computer, broadband modem & wireless router - and restart. One time had to do it twice, but it's never been more of a hiccup than that. So, after a power cycling all works again.

For what it's worth I am also running WPA and that is working too.

After I got wireless working I then did my various other installs (Nvidia, Beryl, Amarok, blah blah blah)

---

### Post by HumbleGod on 2007-03-17
> #2 I see notes about installing 1.38 of ndiswrapper, but I got it though Synaptic and is says it's 1.8. Dunno what's up with that, maybe I don't know how to read the version numbers, but I do know that I had worked with 1.1 at one time and that definitely didn't help me. Maybe this is something to follow up on.

This is what I get for my version number:
```
brad@brad-ubuntu:~$ ndiswrapper -v

utils version: 1.9
driver version:        1.38
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
```
Maybe you're thinking of the utils version?

I would have to agree with you that working on the wireless card is probably best on a fresh install--not that I have much experience with this, but just out of common sense.  Having a bunch of drivers or misc settings remaining from previous attempts to get wireless to work have thrown me off in the past, even when I followed the guide that eventually worked for me. As for the success rate, I haven't had *any* problems with my card coming on since I followed the method I mentioned earlier, at least not on the 2.6.17.10 kernel.

---

### Post by vgopal on 2007-03-25
This is my first experiment with Linux and i'm liking it so far. And now thanks to this thread I got Wireless adapter (WMP54GS) working flawlessly on my system ... Thanks a ton:guitar:

---

### Post by Joshua on 2007-04-12
This is just my two cents, but there are a couple specifics that seem to be getting left out.

First off, I'm using a basic installation of Edgy (6.10).  In Edgy, there are a couple versions of ndiswrapper-utils (ndiswrapper-utils-1.1 and ndiswrapper-utils-1.8, [from repositories]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndis&searchon=names&subword=1&version=edgy&release=all")).  I installed the 1.8 version before I got everything to work, but I don't think it automatically removed the 1.1 version.

I'm also using the WMP54GS card from Linksys.  Most people appear to have the the Broadcom Chip BCM4306 but there are at least two chips in this card because when I do lspci it says mine is BCM4318 (or something like that.  I'll confirm when I get home, but it definately does NOT say BCM4306).  There are also different *.inf files available from the Linksys website AND different dates for the zipped driver files.  (See the Linksys [ftp site]("ftp://ftp.linksys.com/pub/network/").)  The most recent file includes drivers called WMP54GS.inf and WMP54GSa.inf.  The older ones, I think, name them based on the chipset - more like bcm4306.inf.  I used the WMP54GS.inf.

In the end a lot of that stuff may not matter.  I think the most important thing may be that, in Edgy anyway, my system will automatically boot up with the "bmc43xx" module loaded.  You can check by running lsmod.  I think this is an [open source attempt]("http://bcm43xx.berlios.de/") at drivers for the chips we are interrested in.  But as far as I can tell, they don't work for my card.  So you MUST remove it by running:
```
sudo rmmod bcm43xx
```
If you don't, ndiswrapper won't work.
You also need to make sure ndiswrapper is not loaded before you install the drivers that you choose.  You do this in a similar manner:
```
sudo rmmod ndiswrapper
```
Then you can use the gui to load the driver, or you can run commands like:
```
sudo ndiswrapper -i WMP54GS.inf
```
To load drivers. Or:
```
sudo ndiswrapper -e wmp54gs
```
To unload drivers.  Or:
```
sudo ndiswrapper -l
```
To list installed drivers.
After you have the driver installed, you run
```
sudo modprobe ndiswrapper
```
There should be some output in a log somewhere that says the driver you chose was loaded.  If nothing else you can run wpconfig and there should be an entry for wlan0.

Also, as a thought.  It might be useful to set up an Ubuntu Wiki that describes the success people have had with various chipsets and various drivers and various Ubuntu releases.  Something really specific to a person can figure out exactly what setup they have and have the exact commands to run to get the card working.  Like the [ubuntuguide]("http://www.ubuntuguide.org").

---

### Post by Joshua on 2007-04-12
One last thing I should note - ndiswrapper can be pretty easy, but according to some other websites, ([like this]("http://linux-wless.passys.nl/query_chipset.php?chipset=Broadcom")), the bcm43xx module should work with the WMP54GS.  There are procedures for using that module [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"), but like I said, I haven't been able to get it to work.

---

### Post by phan on 2008-02-12
Hi there,

Just to let know those who might be interested that I installed a WMP54GS card on Unbuntu Feisty Fawn (7.04) via another approche (the native drivers) after I tried the apprach with NDISWRAPPER and had no success.

I followed the instructions on [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty#head-e11c3138afb4f9fb637d8f0a6d234add934830cc") and it worked for me.

I've got a WMP54GS-FR with Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller chip. I just installed the lastest kernel version available via synaptic update: 2.6.20-16 (I have no idea if it matters or not).

Thanks to the Ubuntu community !

---

