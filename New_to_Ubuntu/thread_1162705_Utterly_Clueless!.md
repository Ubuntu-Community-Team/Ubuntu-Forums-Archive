---
title: "Utterly Clueless!"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by hellothere2 on 2009-05-18
From this thread:

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

Here's what I'm getting:

ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper , it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist , it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 4: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 7: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 8: ignoring bad line starting with 'lsusb'
WARNING: /etc/modprobe.d/blacklist line 9: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 10: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 11: ignoring bad line starting with 'lsusb'
rt2870 : driver installed  
            device (1737:0077) present

Should I worry about the warnings?  At this point, I ignored them and kept going.  The link said to then do this:

uname -m
i686

So I have 32 bit.  But how do I know if the driver I installed is 32 bit or 64?


I just installed Ubuntu, but I have literally no clue how to use it.  One of the first things I NEED to do is connect to the internet, but, to do this, I connect to a router with a wireless networking adapter: WUSB54GC .  The thing works fine on Windows, but not on Ubuntu.  This is so frustrating!  How do I get it to work?  I found threads like this:  [http://ubuntuforums.org/showthread.php?t=279447](http://ubuntuforums.org/showthread.php?t=279447)   But I have no clue how to do that stuff.  Would anyone be kind enough to help?  Thanks!

---

### Post by juancarlospaco on 2009-05-18
Try an ethernet cable until you are more confortable with the new system.

---

### Post by hellothere2 on 2009-05-18
> **juancarlospaco said:**
> Try an ethernet cable until you are more confortable with the new system.

 Thanks, but I can't do that.  There is the problem; I need to connect to the internet to properly learn how to use Ubuntu; but I can't learn until I connect.  That's why I'm hoping someone can tell me exactly what to do THIS ONE TIME, and I will then properly learn how to use Ubuntu.

---

### Post by Game Over on 2009-05-18
Ok... what are your system specs and the version you are using??
I may be able to help.
And don't feel like you can only get help just this once, this community is here to help with everything!

---

### Post by pulpinator on 2009-05-18
Looks like the problem is that there is no driver for that Linksys USB Wi-Fi dongle. So you'll have to use the Windows driver with ndiswrapper.

See this documentation on how to do that:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by hellothere2 on 2009-05-18
> **Game Over said:**
> Ok... what are your system specs and the version you are using??
I may be able to help.
And don't feel like you can only get help just this once, this community is here to help with everything!

I'm using 9.04 ...specs?  I'll get back to you in a few min...also, here's the thing.  Don't I somehow need to be connected to the internet in order to get this thing working?  B/c all the links I found seemed to involve websites and downloads but how in the world can you use those to install a freaking networking adapter?  so frustrating!

thank you so much btw.

---

### Post by Game Over on 2009-05-18
Even better! Wish I would have had that resource.
I had no idea it was so straight forward.

---

### Post by pulpinator on 2009-05-18
> **hellothere2 said:**
> I'm using 9.04 ...specs?  I'll get back to you in a few min...also, here's the thing.  Don't I somehow need to be connected to the internet in order to get this thing working?  B/c all the links I found seemed to involve websites and downloads but how in the world can you use those to install a freaking networking adapter?  so frustrating!

thank you so much btw.

Hopefully you have a second computer you can access those files from (like the one you're posting from, unless it's a phone!).

---

### Post by Bradtek on 2009-05-18
> **hellothere2 said:**
> The thing works fine on Windows, but not on Ubuntu. 

That would be because Ubuntu Linux is not some free version of windows.
Researching before you go and change Operating system is usually a good idea.
Did you check out if all worked ok using the Live CD before installing ?

---

### Post by Carl Hamlin on 2009-05-18
Why can't you use an ethernet cable?

---

### Post by hellothere2 on 2009-05-18
> **pulpinator said:**
> Looks like the problem is that there is no driver for that Linksys USB Wi-Fi dongle. So you'll have to use the Windows driver with ndiswrapper.

See this documentation on how to do that:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

 thanks!  I suppose I'd be in this category:  nstalling Packages (With Internet access on another computer)  only problem is, I don't see 9.04.  What do i do?

---

### Post by Game Over on 2009-05-18
As long as you read through that link and follow the steps, version does not matter. But I could be mistaken. Anyone...?

---

### Post by hellothere2 on 2009-05-18
> **hellothere2 said:**
> thanks!  I suppose I'd be in this category:  nstalling Packages (With Internet access on another computer)  only problem is, I don't see 9.04.  What do i do?

 Also, how can I view this instructions and type the codes in at the same time? Seeing as I'm not connected to the internet on ubunutu.

---

### Post by Bradtek on 2009-05-18
> **hellothere2 said:**
> What do i do?

Probably save you time and frustration if you just purchased a 
WiFi USB dongle that is supported in Linux.

---

### Post by StooJ on 2009-05-18
> **hellothere2 said:**
> Also, how can I view this instructions and type the codes in at the same time? Seeing as I'm not connected to the internet on ubunutu.

Print the instructions out? Save them as a file (like a pdf/ps etc) and put them on a USB key? Write them on a bit of paper? :D

---

### Post by hellothere2 on 2009-05-18
> **Bradtek said:**
> Probably save you time and frustration if you just purchased a 
WiFi USB dongle that is supported in Linux.

 Just to make sure I'm getting this straight...even though I have 9.04 I can still just download the file on that page from 8.10?  Also, 8.10 seems to have 3 files (a,b,c) do i need to download them all?  Or just one?  Thanks!

---

### Post by hellothere2 on 2009-05-18
> **StooJ said:**
> Print the instructions out? Save them as a file (like a pdf/ps etc) and put them on a USB key? Write them on a bit of paper? :D

I guess I'll just have to print it (though I think it's long).  Because I'm afraid that if I write it to a DVD/USB/whatever, I won't know how to open it once I get back on Ubuntu.

---

### Post by Game Over on 2009-05-18
> **hellothere2 said:**
> Just to make sure I'm getting this straight...even though I have 9.04 I can still just download the file on that page from 8.10?  Also, 8.10 seems to have 3 files (a,b,c) do i need to download them all?  Or just one?  Thanks!

If you could upgrade from 8.10 to 9.04, the driver should just be there.

---

### Post by hellothere2 on 2009-05-18
> **Game Over said:**
> If you could upgrade from 8.10 to 9.04, the driver should just be there.

What do you mean by that?  If I could upgrade?  I have 9.04 already.  Are you saying that I don't need to go through all the steps listed on that website if I have 9.04?  Because that would be great

---

### Post by Game Over on 2009-05-18
Okay, I misunderstood... I though you had Intrepid.

Try this:
Reboot Ubuntu
Systems >Administration>Hardware Drivers>Activate your modem/wlan/card/driver/etc.

You'll then need to go into 
System > Preferences>Network Connections 
Configure your IP, Gateway, etc.

That should work maybe? I hope.

I would still recommend this link
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I would bet my bottom dollar it's the ndiswrapper, you need to take care of that.

---

### Post by hellothere2 on 2009-05-18
> **Game Over said:**
> Okay, I misunderstood... I though you had Intrepid.

Try this:
Reboot Ubuntu
Systems >Administration>Hardware Drivers>Activate your modem/wlan/card/driver/etc.

You'll then need to go into 
System > Preferences>Network Connections 
Configure your IP, Gateway, etc.

That should work maybe? I hope.

I would still recommend this link
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I would bet my bottom dollar it's the ndiswrapper, you need to take care of that.

thanks  It sucks though that I have do all this without being connected.  How do I do this part?  Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order:      *          sudo dpkg -i ndiswrapper-utils_*.deb          sudo dpkg -i ndisgtk_*.deb

---

### Post by SunnyRabbiera on 2009-05-18
> **hellothere2 said:**
> Just to make sure I'm getting this straight...even though I have 9.04 I can still just download the file on that page from 8.10?  Also, 8.10 seems to have 3 files (a,b,c) do i need to download them all?  Or just one?  Thanks!

any files and instructions you find for older versions of Ubuntu will probably work for your newer one.
Most commands are universal for Ubuntu, so if you cant find instructions/files for Ubuntu Jaunty 9.04 you can use ones for Ubuntu 8.10 and 8.04.
If you cant find a installer for jaunty dont panic, as mostly that kind of stuff is backwards compatible.

> **hellothere2 said:**
> thanks  It sucks though that I have do all this without being connected.  How do I do this part?  Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order:      *          sudo dpkg -i ndiswrapper-utils_*.deb          sudo dpkg -i ndisgtk_*.deb

Yeh sadly there is not much to do, again this is no fault of Linux, Ubuntu or anything...
But it is fault of the network device, as most of that crap is made for windows.
There is always a workaround though, but its not that easy sometimes.
But it is improving believe me, the hardware support in linux has gotten much better over the years.

---

### Post by Game Over on 2009-05-18
Sunny for the win!

---

### Post by hellothere2 on 2009-05-18
> **Game Over said:**
> Sunny for the win!

thanks but how do I copy it from Windows to my home directory on Ubuntu?

---

### Post by SunnyRabbiera on 2009-05-18
> **hellothere2 said:**
> thanks but how do I copy it from Windows to my home directory on Ubuntu?

Well do you have an external HD?
Burning CD's?
DVD's?
Heck even a small 1GB MP3 player might suit you here.

---

### Post by hellothere2 on 2009-05-18
> **SunnyRabbiera said:**
> Well do you have an external HD?
Burning CD's?
DVD's?
Heck even a small 1GB MP3 player might suit you here.

But this is what the site says:  Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order:

---

### Post by SunnyRabbiera on 2009-05-18
> **hellothere2 said:**
> But this is what the site says:  Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order:

You can still drag and drop, just burn ndiswrapper, ndis-gtk and whatever else is listed as a dependency (there are quite a few but most of them should be pre installed anyhow)
I would just burn the files to a disk, then just copy the files to your home.
It should be simple at least when concerning drag and drop

---

### Post by Game Over on 2009-05-18
> **hellothere2 said:**
> But this is what the site says:  Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order:

Yes, it does. Do you have a way to do that, such as a CD/DVD burner, USB flash drive, floppy, any type of media?? Or maybe place it in a shared folder?

Also...
> **superprash2003 said:**
> if you still face problems , post output of **lshw -C network** from the ubuntu terminal
 
Maybe? I found that in another thread like this. I had the same problem...

Hope this is helping you :)

---

### Post by hellothere2 on 2009-05-18
Damn.  this is so frustrating.  I guess I'll just have to stick with windows.

---

### Post by SunnyRabbiera on 2009-05-18
> **hellothere2 said:**
> Damn.  this is so frustrating.  I guess I'll just have to stick with windows.

Well dont give up just yet!
please let us try to help you to the best of our abilities.

Look this is not our fault, Microsoft has the market share because it pays off the right people, we are not owned by microsoft so the world just ignores us.
Try other distros, Ubuntu is not the end all of linuxes.
Wireless drivers can be frustrating but if you had a more direct connection then maybe your issue might be better solved.
In terms of wireless Linux is just getting there, its not perfect but its getting better.
Give everything a try first before giving up.

---

### Post by hellothere2 on 2009-05-18
> **SunnyRabbiera said:**
> Well dont give up just yet!
please let us try to help you to the best of our abilities.

Look this is not our fault, Microsoft has the market share because it pays off the right people, we are not owned by microsoft so the world just ignores us.
Try other distros, Ubuntu is not the end all of linuxes.
Wireless drivers can be frustrating but if you had a more direct connection then maybe your issue might be better solved.
In terms of wireless Linux is just getting there, its not perfect but its getting better.
Give everything a try first before giving up.

thanks.  what would you recommend other than ubuntu?  b/c I've always heard that was the best

---

### Post by SunnyRabbiera on 2009-05-18
> **hellothere2 said:**
> thanks.  what would you recommend other than ubuntu?  b/c I've always heard that was the best

Well its one of the best, but there are others.
For the beginner there is always Linux mint with NDIS-GTK pre installed, I dont use it anymore because of personal reasons but if you are getting started its good for what it is and it is based on Ubuntu so any support you need we can give.
OpenSuse can be good too

Linux is not under one roof like windows, as each distro is suited for a different need.
A good place to look is distrowatch, where many linux flavors are featured.

---

### Post by hellothere2 on 2009-05-18
> **SunnyRabbiera said:**
> Well its one of the best, but there are others.
For the beginner there is always Linux mint with NDIS-GTK pre installed, I dont use it anymore because of personal reasons but if you are getting started its good for what it is and it is based on Ubuntu so any support you need we can give.
OpenSuse can be good too

Linux is not under one roof like windows, as each distro is suited for a different need.
A good place to look is distrowatch, where many linux flavors are featured.

thanks, but are these good for what I'm looking for (easy setup of wireless networking adapter)?

---

### Post by cariboo on 2009-05-18
You don't need internet access to install ndiswrapper, it is on the Livecd. Go to System-->Administration-->Software Sources, and make sure there is a check mark beside the cdrom, this assumes that you have the cd in your cd drive. Next go to System-->Administration-->Synaptic Package Manager and search for ndiswrapper, there should be two files to install, I would also suggest you install ndisgtk, as it is a gui frontend for installing the Windows wireless drivers.

Once you have ndiswrapper installed, get the driver disk that came with your usb device and look for the .inf file in the XP directory. Once you have found the .inf file you should be able to install the Windows drivers and start up your wireless device.

The upcoming Tutorial Of The Week is all about using ndiswrapper and troubleshooting any problems you may have, it should be out in a day or two.

---

### Post by hellothere2 on 2009-05-18
> **cariboo907 said:**
> You don't need internet access to install ndiswrapper, it is on the Livecd. Go to System-->Administration-->Software Sources, and make sure there is a check mark beside the cdrom, this assumes that you have the cd in your cd drive. Next go to System-->Administration-->Synaptic Package Manager and search for ndiswrapper, there should be two files to install, I would also suggest you install ndisgtk, as it is a gui frontend for installing the Windows wireless drivers.

Once you have ndiswrapper installed, get the driver disk that came with your usb device and look for the .inf file in the XP directory. Once you have found the .inf file you should be able to install the Windows drivers and start up your wireless device.

The upcoming Tutorial Of The Week is all about using ndiswrapper and troubleshooting any problems you may have, it should be out in a day or two.

thanks so much!  i will try this.  but what do you mean by get "the driver disk" that came with my usb device?  what is this?

---

### Post by SunnyRabbiera on 2009-05-18
> **hellothere2 said:**
> thanks, but are these good for what I'm looking for (easy setup of wireless networking adapter)?

Mint might suit the bill here, the only thing you might need is cabextract for your wireless driver.
But once again, burn CD whatever for that.
You can get cabextract for ubuntu as it will work with mint.
I have not had to deal with manual network adapter crap in a while so excuse my rustiness.
But if you had the driver on windows you could transfer it to Linux mint.
I think its under linksys or some crap like that, I have not done it in ages though.

---

### Post by hellothere2 on 2009-05-18
> **cariboo907 said:**
> You don't need internet access to install ndiswrapper, it is on the Livecd. Go to System-->Administration-->Software Sources, and make sure there is a check mark beside the cdrom, this assumes that you have the cd in your cd drive. Next go to System-->Administration-->Synaptic Package Manager and search for ndiswrapper, there should be two files to install, I would also suggest you install ndisgtk, as it is a gui frontend for installing the Windows wireless drivers.

Once you have ndiswrapper installed, get the driver disk that came with your usb device and look for the .inf file in the XP directory. Once you have found the .inf file you should be able to install the Windows drivers and start up your wireless device.

The upcoming Tutorial Of The Week is all about using ndiswrapper and troubleshooting any problems you may have, it should be out in a day or two.

Thanks!  I was able to install ndiswrapper like you said.  Now what? Do I proceed as instructed in that confusing (for a newb like me :) link posted early on?  Or is what you're saying easier/different?  You said to get the driver disk, but I'm not sure exactly what you mean by that.  And, once I get it, you say I should be able to install the Windows drivers? But how?  I'm a total newb.

---

### Post by hellothere2 on 2009-05-18
Can anyone help me do this?  I found this site:  [http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide)  Now I've got ndiswrapper, but now I can't locate device manager!!  Why is this so difficult?

---

### Post by emeraldgirl08 on 2009-05-18
Is there a CD that came with your wireless USB??? That CD is your driver CD.

---

### Post by hellothere2 on 2009-05-18
> **emeraldgirl08 said:**
> Is there a CD that came with your wireless USB??? That CD is your driver CD.
Yes!  There is.  What do I need to do with the CD?

---

### Post by cariboo on 2009-05-18
If you had paid attetion to my post, I said look for an .inf file in the windows xp directory of your driver disk. If there isn't an .inf file there extract the .exe file to your hard drive and copy it to your ubuntu installation.

---

### Post by hellothere2 on 2009-05-18
I just typed in lsusb and I got the code.  It's 1737:0077.  Now what?

---

### Post by hellothere2 on 2009-05-18
> **cariboo907 said:**
> If you had paid attetion to my post, I said look for an .inf file in the windows xp directory of your driver disk. If there isn't an .inf file there extract the .exe file to your hard drive and copy it to your ubuntu installation.
Yes, but what is a driver disk?  Also, how to I get something from windows onto ubuntu?  is there a way to save a windows file so it can be acessed from uuntu?

---

### Post by sloggerkhan on 2009-05-18
The instructions are simple. What is happening is that because in linux there are 50 different ways to do things depending on which distro and what wireless card and a host of other factors you are googling and finding things that make your situation more confusing and complicated then it really is.

To simplify what cariboo907 has said:
You need
[LIST]
[*]windows driver cd for your wireless dongle (if you don't have one, download the windows driver for it from somewhere)
[*] ubuntu live CD
[/LIST]

From the ubuntu live CD, install ndisgtk. Once it's installed, you no longer need the ubuntu CD.
Insert the media (flash drive, cd, etc) with the windows driver for the wireless dongle into your computer.
From System > Admin open Windows Wireless Drivers
Click install new driver.
Browse through your windows driver CD (or downloaded driver) until you find the .inf file for the driver. 
Select and choose that driver, and start using it.

A possible bottleneck is that you may not find the inf file in the CD or installer because it's located in some sort of .exe/msi archive. In that case, either find the .inf file on your windows computer or extract the .exe/msi and find it that way.

Anyhow, at the begining Linux/Ubuntu can be weird and overwhelming because things are so different, people often pass on instructions in command line form even when they're for stuff that can be done via gui because it's generally a lot simpler to past a command than spell out how to navigate menus and such. 

It's smart to get a feel for things with the live cd before jumping right in. If there's a hardware problem, you can notice it and diagnose and correct it before installing so you aren't left in an awkward spot.

---

### Post by hellothere2 on 2009-05-18
> **sloggerkhan said:**
> The instructions are simple. What is happening is that because in linux there are 50 different ways to do things depending on which distro and what wireless card and a host of other factors you are googling and finding things that make your situation more confusing and complicated then it really is.

To simplify what cariboo907 has said:
You need
[LIST]
[*]windows driver cd for your wireless dongle (if you don't have one, download the windows driver for it from somewhere)
[*] ubuntu live CD
[/LIST]

From the ubuntu live CD, install ndisgtk. Once it's installed, you no longer need the ubuntu CD.
Insert the media (flash drive, cd, etc) with the windows driver for the wireless dongle into your computer.
From System > Admin open Windows Wireless Drivers
Click install new driver.
Browse through your windows driver CD (or downloaded driver) until you find the .inf file for the driver. 
Select and choose that driver, and start using it.

A possible bottleneck is that you may not find the inf file in the CD or installer because it's located in some sort of .exe/msi archive. In that case, either find the .inf file on your windows computer or extract the .exe/msi and find it that way.

Anyhow, at the begining Linux/Ubuntu can be weird and overwhelming because things are so different, people often pass on instructions in command line form even when they're for stuff that can be done via gui because it's generally a lot simpler to past a command than spell out how to navigate menus and such. 

It's smart to get a feel for things with the live cd before jumping right in. If there's a hardware problem, you can notice it and diagnose and correct it before installing so you aren't left in an awkward spot.

Thank you so much!  I followed your instructions and installed rt2870.  Next  to Hardware Present: it says yes. Now you said select and choose this driver and start using it?  How?  Thanks!

---

### Post by hellothere2 on 2009-05-18
One other thing.  My ubuntu version is 32-bit.  When I type uname -m I get i686.  However, I located the driver through x86.  Is this ok?

---

### Post by hellothere2 on 2009-05-18
From this thread:

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

Here's what I'm getting:

ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper , it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist , it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 4: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 7: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 8: ignoring bad line starting with 'lsusb'
WARNING: /etc/modprobe.d/blacklist line 9: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 10: ignoring bad line starting with 'lspci'
WARNING: /etc/modprobe.d/blacklist line 11: ignoring bad line starting with 'lsusb'
rt2870 : driver installed  
            device (1737:0077) present

Should I worry about the warnings?  At this point, I ignored them and kept going.  The link said to then do this:

uname -m
i686

So I have 32 bit.  But how do I know if the driver I installed is 32 bit or 64?

---

### Post by hellothere2 on 2009-05-18
If I installed the 64-bit driver, I'm not sure what to do.  The link says to find the right one and install again, but I don't see another one that will work.

If I installed 32-bit, should ubuntu automatically be recognizing my adapter at this point?  Because it doesn't seem to be.  The green light is not on and it's definitely not connected to the internet.

---

### Post by pricetech on 2009-05-18
If you told us, I didn't catch it;  is your computer a desktop or a laptop ??  If I give you a wired NIC that I know works under Linux, would you be willing to pay the freight ??  I have PCI and PCMCIA both.  I'll be glad to send you one to get you connected, then you can sort out the rest.

---

### Post by hellothere2 on 2009-05-18
> **pricetech said:**
> If you told us, I didn't catch it;  is your computer a desktop or a laptop ??  If I give you a wired NIC that I know works under Linux, would you be willing to pay the freight ??  I have PCI and PCMCIA both.  I'll be glad to send you one to get you connected, then you can sort out the rest.
It's a desktop, and thanks, but I'd rather not.

---

### Post by sim-value on 2009-05-18
> **hellothere2 said:**
> If I installed the 64-bit driver, I'm not sure what to do.  The link says to find the right one and install again, but I don't see another one that will work.

If I installed 32-bit, should ubuntu automatically be recognizing my adapter at this point?  Because it doesn't seem to be.  The green light is not on and it's definitely not connected to the internet.
i686 x86 32 Bit is all the same so you need the 64 Bit driver

And yes as far as i know after installing the driver Ubuntu should recognize it ...

---

### Post by hellothere2 on 2009-05-18
> **sim-value said:**
> i686 x86 32 Bit is all the same so you need the 64 Bit driver

And yes as far as i know after installing the driver Ubuntu should recognize it ...

So you're saying that, from what I've indicated, my computer should in some way be automatically recognizing the adapter?  Do I need to click anywhere in particular to check this?

---

### Post by hellothere2 on 2009-05-18
Hmm....I typed this in:

dmesg | grep -e ndis -e wlan

and got:

ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
ndiswrapper (import:242): unknown symbol: ntoskrnl.exe: 'MmGetSystemRoutineAddress'
ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
usbcore: registered new interface driver ndiswrapper
usbcore: deregisterting interface driver ndiswrapper
ndiswrapper (ntoskernel_exit:2671): object ede63a20(2) was not freed, freeing it now
ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
ndiswrapper (import:242): unknown symbol: ntoskrnl.exe: 'MmGetSystemRoutineAddress'
ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
usbcore: registered new interface driver ndiswrapper

Now what>?

---

