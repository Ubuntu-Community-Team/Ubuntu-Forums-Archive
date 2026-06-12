---
title: "The War On Wireless, and other wacky misadventures"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by aqua mew on 2010-05-15
Now, I'm very new to the world of Linux.  I've got Ubuntu 10.04 dual-booting with Windows XP.  Why am I dual-booting instead of running Ubuntu from the CD?  Well, not that I didn't want to dual-boot anyway, but I didn't really have a choice.  I already borked at least three CDs trying to burn the ISO, and the fourth did better, but I don't think everything's there that needs to be.  "My Computer" seems to know it's there, and I can still bring up the menu that asks how I want to install it, but if I pick "Demo and full installation", and then reboot, nothing happens.  So I had to "Install inside Windows".  I don't even quite remember if I used the CD for that or the flash drive my dad let me use when he said the file was too big for a CD.

The other problem with this CD... I've been trying to find a way to make Ubuntu recognize my wireless adapter (WUSB54CG v3) so I can get on the internet.  I can't download ndiswrapper with the terminal because, obviously, that requires an internet connection.  So I downloaded it on Windows and saved it to my own flash drive.  Then I found this thread: [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)  It looked like what I was looking for... but guess what?  Ubuntu doesn't want to recognize the CD!  Is there a way to make the other flash drive work like the CD is supposed to here?

Oh, and to complicate things even further... from what I've gotten from my searches, apparently things are easier if you can connect wired.  But I can't; my dad doesn't want to go through the trouble, and he's the only one who knows how to do anything with the router more than just unplugging and replugging, and that's why I need an adapter in the first place.

---

### Post by sasaenator on 2010-05-15
If I understood correctly you can´t boot from a live CD.Perhaps your BIOS is not set up to do that.If you don´t know,here is how:when you turn on your PC press a button to go to BIOS,the button varies,it can be F8,Delete,ESC,try to read on the first screen.Then in BIOS go to boot options and line up boot priorities.when done press F10 and save settings.Hope this helps.Or maybe you didn´t burn your cd correctly,there was a how-to on the ubuntu wiki about that I believe.Good luck!7

---

### Post by ugm6hr on 2010-05-15
Let's start from the beginning:

1. You are not strictly dual-booting if you installed inside Windows - that is a Wubi install.

2. It would be helpful to know what the problem was with the CD, and how you installed. It is possible that there was, in fact, an error on the installation CD, and hence your final install is not perfect.  The standard process to go through is: check md5sum, check CD burn integrity, then install.

3. I can't work out what chipset your device has - there are a few similarly named wifi adapters, and I can't find anything related to your specifically - can you check the spelling etc?  Also - go to the Wifi help link below and answer as many questions as possible to help us out.  Essentially, we need to know the chipset.

---

### Post by anewguy on 2010-05-15
Also, for others who may be in need:

ndiswrapper and the ndiswrapper utilities are on the LiveCD you install from in the /pool/main/n/ndiswrapper folder -> install ndiswrapper common first then install the utilities (both are required, just click on them to start the installer)

the gui'd front end (which makes life a lot easier) to ndiswrapper is ndisgtk, and it is also on the CD in the /pool/main/n/ndisgtk folder.

So, *if* you need to use ndiswrapper (and hence have no connection to the internet yet) you can install it from the installation CD.  In addition, it is highly recommended (at least in my opinion) to install ndisgtk also - after installing it go to system/adminstration/windows/wireless drivers, then add and point to the .inf file for your driver.

Dave ;)

---

### Post by 3rdalbum on 2010-05-15
You don't need your father to fiddle with the router at all. Just plug an Ethernet cable into it and into your computer and you'll immediately get a connection.

Then go to System > Administration > Synaptic Package Manager and hit the Reload button. After that's done, quit Synaptic and go to System > Administration > Hardware Drivers; you might be offered a driver to download for your wireless card.

If you can see wireless networks in Ubuntu and can connect to yours, but Firefox can't find any websites, then this might be the solution for you: [http://www.chrislees.info/ubuntu/opendns.shtml](http://www.chrislees.info/ubuntu/opendns.shtml)

---

### Post by aqua mew on 2010-05-15
Well, this looks like somewhat of a predicament.  It was showing me as connected, but wouldn't let me actually do anything requiring a connection.  So I tried the instructions in 3rdalbum's link, and all that did was put the network icon into a perpetual trying-to-connect state, so I tried to put it back how it was, and now I have [this]("http://i302.photobucket.com/albums/nn95/shiney-mew/opendnscreenshot.png").  I'm pretty sure I don't even have that many networks, and even if I did, I certainly wouldn't want to name them random things that aren't even on my keyboard.

I can't use an ethernet cable because my computer is all the way across the house from the router, and my dad would rather not string a cable through the entire length of the house.  As my computer is a desktop, moving it to a temporary location closer to the router would be an incredible hassle.

> **ugm6hr said:**
> 3. I can't work out what chipset your device has - there are a few similarly named wifi adapters, and I can't find anything related to your specifically - can you check the spelling etc?  Also - go to the Wifi help link below and answer as many questions as possible to help us out.  Essentially, we need to know the chipset.

Sorry, looks like I typo'd.  It should be "GC" at the end, not "CG".  Sorry about that.  Anyway, my dad just found [this page]("file:///F:/Linksys%20WUSB54GC%20v3%20on%20Linux%20%C2%AB%20_home_jos_blog.html"), which maybe I might be able to so something with...

To get the exact details of my CD problem, I'll have to screenshot that during my next Ubuntu session when I try once again to play around with stuff.  I'm guessing I'll probably have to make another CD and reinstall, but I'd like to not do that if I can avoid it...

---

### Post by confused57 on 2010-05-15
I had the same sort of problem when I installed pclinuxos, but with Ubuntu you might want to try
```
sudo ifdown wlan0
```
then
```
sudo ifup wlan0
```

This enabled a wireless connection, I then installed wicd, which automatically connects my wireless at startup.

This is my only experience with wireless, but might be worth a try & it assumes your wireless is wlan0.

---

