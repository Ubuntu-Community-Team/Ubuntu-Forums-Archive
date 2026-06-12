---
title: "USB device recognition"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by jeth32 on 2010-11-03
I'm so new that I am amazed when something I try actually works!:)

My question has to do with recognition of USB devices when trying to run a program under WINE.  I "think" I installed the application properly under WINE but I'm not 100% sure. 

I couldn't get WINE to recognize my CD drive, so I copied the contents to a folder on the desktop.  Then within WINE I moved to that folder and installed the Windows application.  In this case it is a medical application that accepts data from a heart monitor. 

But I ended up with an desktop object for the program as well as an entry under the WINE programs menu.  Both start the program normally. 

But now the program can't see the device when I plug it in, so I am unable to upload the data to the program.

It looks like I do have automatic detection of USB devices turned on because outside of WINE, if I plug in a USB flash drive I see it pop up on the desktop right away and can access the files on it.

But nothing appears on the desktop and nothing shows as available to the application when I plug in the heart monitor.

---

### Post by P4man on 2010-11-03
Wine doesnt directly support USB devices (yet?). But you should be able to access a USB drive by browsing from the windows app to the ubuntu mountpoint ( /media/someuniquenumber ).

---

### Post by robsoles on 2010-11-03
I expect the heart monitoring device won't mount as a storage device.

I think you have the best chance of accessing this through [www.virtualbox.org]("http://www.virtualbox.org") - last time I checked the version you get from the repositories still doesn't do USB so good so I go for VirtualBox closed source from virtualbox.org.

You will need to install Windows into a VM in VirtualBox and search google for using USB in VirtualBox under Ubuntu. [www.google.com/search?q=virtualbox+usb+under+ubuntu]("http://www.google.com/search?q=virtualbox+usb+under+ubuntu")

If you have trouble with it and can't find a solution by Googling you will probably be best off making a new thread, although a post in this one to point it out to anybody subscribed to this one isn't against the rules :)

---

### Post by P4man on 2010-11-03
oops, yeah you are right. I thought he had trouble with usb drives, but that heart monitor likely wont be usable with wine. 

Before jumping in to virtualbox, Id check if there isnt any native software that supports that particular heart monitor. Have a look here:

[http://www.linux.com/archive/articles/60528](http://www.linux.com/archive/articles/60528)
and
[http://sourceforge.net/projects/polarscope/](http://sourceforge.net/projects/polarscope/)

I guess it all depends what hearmonitor you have.

---

### Post by robsoles on 2010-11-03
> **P4man said:**
> ...

Before jumping in to virtualbox, Id check if there isnt any native software that supports that particular heart monitor. Have a look here:

[http://www.linux.com/archive/articles/60528](http://www.linux.com/archive/articles/60528)
and
[http://sourceforge.net/projects/polarscope/](http://sourceforge.net/projects/polarscope/)

I guess it all depends what hearmonitor you have.

+1 :) #-oyes, heaps better if there is native support/apps for it!

---

### Post by jeth32 on 2010-11-03
> **robsoles said:**
> +1 :) #-oyes, heaps better if there is native support/apps for it!

Thanks to all the responders.....it will give me something to do on a rainy day. :popcorn:

Re. VirtualBox.....I hadn't thought of that from a Ubuntu standpoint.  I have both that and the VMWare Player installed on my Vista partition. 

I actually have a second device, a Uniden cordless phone that has a customization tool that runs only under Windows.  But it is no longer supported by them and the only way I can run it is under XP running under either VMBox or VMWare Player.   I tried that under WINE as well, and it also is unable to recognize when the device is plugged in. 

BTW for both installations, I hadn't figured out how to get to the CD drive from WINE so I simply copied the disk to the desktop in Ubuntu, an then accessed that image from WINE. 

As for WINE not supporting USB yet, my guess would be it will before I learn what I am doing over here in Ubuntu. :):P:):P:)

Thanks again for the responses.

---

### Post by P4man on 2010-11-03
> **jeth32 said:**
> 

As for WINE not supporting USB yet, my guess would be it will before I learn what I am doing over here in Ubuntu. :)

Hehe.. dont be too sure. First things I read about wine implementing native USB support date back from.. 2005 or so. Still doesnt look like a lot has been done in that regard.

BTW, if you'd ever feel compelled to go the virtual machine route, this here is an interesting tool:
[http://blog.paragon-software.com/?p=439](http://blog.paragon-software.com/?p=439)

It lets you create a VM from your current windows install, that you can import in virtualbox (or vmware) so you can boot your "old" windows install from your new OS. Quite neat for anyone transitioning from windows to ubuntu, provided you have sufficient disk space and ram.

---

### Post by jeth32 on 2010-11-03
> **P4man said:**
> Hehe.. dont be too sure. First things I read about wine implementing native USB support date back from.. 2005 or so. Still doesnt look like a lot has been done in that regard.

BTW, if you'd ever feel compelled to go the virtual machine route, this here is an interesting tool:
[http://blog.paragon-software.com/?p=439](http://blog.paragon-software.com/?p=439)

It lets you create a VM from your current windows install, that you can import in virtualbox (or vmware) so you can boot your "old" windows install from your new OS. Quite neat for anyone transitioning from windows to ubuntu, provided you have sufficient disk space and ram.

I actually do have both VMBox and VMWare Player installed in the Vista desktop machine.

I even managed top clone my XP laptop and imported that image to VMWare.   This does allow me to run those two apps there.  

I like that approach too and even eliminated one of my partitions and added it's space back into the Vista one.   I have kept one partition available for running Ubuntu natively even though I even have a virtual one installed under VMWare.  It is a pretty convenient way to try things out.

---

