---
title: "RTL8185, Ndiswrapper and Gutsy"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by Igzilla on 2007-11-03
Hi All, I am rapidly running out of things to do. I had a working RTL8185 wireless card connecting through ndiswrapper under Feisty, but now I've upgraded to Gutsy, I cannot connect to the network. I can see it, but have got 0% signal strength. I am convinced that ndiswrapper is loading the driver properly too.

I have tried doing everything in [http://ubuntuforums.org/showthread.php?t=585712]("http://ubuntuforums.org/showthread.php?t=585712") but still nothing.

Have I missed something somewhere? If I can get this working easily, I'll be able to convince the missus to make the jump to Ubuntu!

Many thanks if you can help me!

---

### Post by ddrichardson on 2007-11-03
Is there another kernel module for RTL8185 in Gutsy that needs blacklisting?

---

### Post by kevdog on 2007-11-03
Can you post the following:

modinfo ndiswrapper
ndiswrapper -l
lsmod | grep ndiswrapper
lshw -C network
iwlist scan

---

### Post by Intel D805 on 2007-11-03
I know how you feel and it is frustrating....

I just posted on a solution on how to take care of that r8180 Linux driver that needs to be blacklisted permanently.

[http://ubuntuforums.org/showthread.php?t=422557](http://ubuntuforums.org/showthread.php?t=422557)

> Whatever you are doing just stop. I went through the same problem.

If you are not using 7.10 Gusty. I recommend you do so simply because it works better on the internet,

You will have to blacklist the linux driver called r8180.

Bring up terminal. How to access terminal? Look up to the left of the screen and see the word Application...click....then Accessories....click then Terminal...click.

The terminal window should pop up.

Type in these commands...after the commands hit enter on keyboard:

sudo su

Terminal asks you for password...type in your password and hit enter.

gksudo gedit /etc/modprobe.d/blacklist

Hit enter

By the time you hit enter on keyboard the file should pop up and show you the list of items that are blacklisted drivers.

Scroll down and see if you see any file related to your wireless card...if not then scroll down to the bottom type this

# Bad r8180 linux driver
blacklist r8180

Then you should see in the upper of that window and click save. Once you have saved it then reboot by shutting the computer off entirely not a simple reboot.,..I mean dead...no power. Then go ahead and power your PC up by time you are in the linux desktop the r8180 driver should be dead.

Use ndiswrapper to install your windows driver by finding the .INF for windows XP on your driver CD that came with your wireless card.

If you don't know how to use ndiswrapper or know how to install it...let me know.

I am using 7.10 and my airlink 101 3028 with R8185L driver is working flawless with the help of ndiswrapper 1.45 version.


As for experienced users please type your directions more clearly. The steps have I outlined above are few weeks of research I had to commit to find the answers.

Enjoy!

---

### Post by evets on 2007-11-05
> **Intel D805 said:**
> I know how you feel and it is frustrating....

I just posted on a solution on how to take care of that r8180 Linux driver that needs to be blacklisted permanently.

[http://ubuntuforums.org/showthread.php?t=422557](http://ubuntuforums.org/showthread.php?t=422557)

I have an Encore "G" wireless PCI card. I went to the [ [COLOR="Blue"]Encore[/COLOR]](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_4&pid=285) site and d/l'd the [ [COLOR="Blue"]Linux driver pkg[/COLOR]](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_4&pid=285#DOWNLOAD) for my card, the [COLOR="Red"]ENLWI-G2[/COLOR] which **[COLOR="Red"]uses RTL8185L chipset[/COLOR]**. I installed the card thinking there might be a way for it to be discovered by Gutsy, but my system just froze after the initial Ubuntu Splash screen with the progress bar had completed. I removed the card. and the system operates fine.

I've tried to install nothing else. Since I'm new to all this, I was hoping an experienced Ubuntu-ian would help explain it to me.

I suppose I'm expected to "make" the drivers, but haven't done so yet, as I don't know how yet. After reading some posts here, I'm not sure I should do anything until someone more experienced succeeds. 

BTW, does "blacklisting" do what the name implies? If so, are you blacklisting them because they don't work and Ubuntu would attempt to use them if you didn't?


Thanks

---

### Post by charonn0 on 2008-03-09
> **Intel D805 said:**
> I know how you feel and it is frustrating....

I just posted on a solution on how to take care of that r8180 Linux driver that needs to be blacklisted permanently.

[http://ubuntuforums.org/showthread.php?t=422557](http://ubuntuforums.org/showthread.php?t=422557)

Thanks, this worked perfectly for me! (PS, you were especially right about shutting down completely!)

> **evets said:**
> I have an Encore "G" wireless PCI card. I went to the [ [COLOR="Blue"]Encore[/COLOR]](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_4&pid=285) site and d/l'd the [ [COLOR="Blue"]Linux driver pkg[/COLOR]](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_4&pid=285#DOWNLOAD) for my card, the [COLOR="Red"]ENLWI-G2[/COLOR] which **[COLOR="Red"]uses RTL8185L chipset[/COLOR]**. I installed the card thinking there might be a way for it to be discovered by Gutsy, but my system just froze after the initial Ubuntu Splash screen with the progress bar had completed. I removed the card. and the system operates fine.

I've tried to install nothing else. Since I'm new to all this, I was hoping an experienced Ubuntu-ian would help explain it to me.

I suppose I'm expected to "make" the drivers, but haven't done so yet, as I don't know how yet. After reading some posts here, I'm not sure I should do anything until someone more experienced succeeds. 

BTW, does "blacklisting" do what the name implies? If so, are you blacklisting them because they don't work and Ubuntu would attempt to use them if you didn't?


Thanks

I have the same card. Blacklisting the Ubuntu driver, shutting down completely, and then using ndiswrapper to install the Windows driver worked wonderfully.

Your interpretation of blacklisting is right on the money!

---

