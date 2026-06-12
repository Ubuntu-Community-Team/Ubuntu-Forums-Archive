---
title: "Start-up disk won't run - shuts down monitor"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by dondiego2 on 2010-07-21
I have seen this problem before but have found no solutions.  I been starting to have issues with Ubuntu 10.04 on my computer so I thought I would do a fresh install because I had just done the upgrade from 9.04.

The problem is when I boot from the disk, it starts (showing the little human logo on the bottom) and then it shuts down my monitor and nothing happens.  I booted from the disc last night and went to bed and this morning it was the same, the computer on but the monitor shut down in sleep mode.  

I had this same problem a while ago when I was checking out a Peppermint disc.  It did the same thing to my computer.

Any ideas on how to get around this?  I really don't want to or can't afford to get a new computer right now and if I can;t get this to work - I hate to say it - but I will have to go back to Windows XP for a while.  I am taking some classes on the computer and I can't fall behind.  So I need to fix my issues in a day or two.

---

### Post by mike555 on 2010-07-21
I guess you have tried this;

* At install screen press F6 and select nomodeset and install Ubuntu as usual.
* On first boot after install, press e on getting the GRUB bootloader.
* Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
* Press Ctrl and X to boot
* You should now be able to login to your Ubuntu as usual

For those of you who do not know what to do next, in the taskbar click on System->Administration->Hardware drivers, and select and activate the nvidia current driver if you have an nvidia card like I do. The driver will be downloaded and activated automatically, and you will be prompted for a reboot.

---

### Post by dondiego2 on 2010-07-21
> **mike555 said:**
> I guess you have tried this;

* At install screen press F6 and select nomodeset and install Ubuntu as usual.
* On first boot after install, press e on getting the GRUB bootloader.
* Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
* Press Ctrl and X to boot
* You should now be able to login to your Ubuntu as usual

For those of you who do not know what to do next, in the taskbar click on System->Administration->Hardware drivers, and select and activate the nvidia current driver if you have an nvidia card like I do. The driver will be downloaded and activated automatically, and you will be prompted for a reboot.


I don't get to the install screen - that is the problem.  It starts up with the little human figure at the bottom and than the monitor goes to sleep and nothing else happens except the disc drive working for a while.

---

### Post by mike555 on 2010-07-21
what is the resolution of your monitor?

---

### Post by dondiego2 on 2010-07-22
> **mike555 said:**
> what is the resolution of your monitor?

I have an hp pavilion f1503 monitor and Ubuntu uses NVIDIA X Server Settings to control the monitor.  When I open that in Ubuntu it says it is set at 1024 x 768.  Is that what you are looking for?  What would that have to do with running an ISO disk????

---

### Post by mike555 on 2010-07-22
I have had problems installing Ubuntu to computers with less then 1280 , you might try adding [ --vga=771  ] to the boot screen (not the install screen)... hope that helps

---

### Post by confused57 on 2010-07-22
> **dondiego2 said:**
> I don't get to the install screen - that is the problem.  It starts up with the little human figure at the bottom and than the monitor goes to sleep and nothing else happens except the disc drive working for a while.

I think when you get the "little human figure", quickly press any key(I think this screen is up only a short time), you should get a screen to select your language, then follow mike555's directions for  pressing F6 & entering nomodeset.  
You might try pressing F6 as soon as the human stick figure-keyboard screen appears.

See this post by oldfred:
[http://ubuntuforums.org/showpost.php?p=9586925&postcount=7](http://ubuntuforums.org/showpost.php?p=9586925&postcount=7)

---

### Post by dondiego2 on 2010-07-22
> **confused57 said:**
> I think when you get the "little human figure", quickly press any key(I think this screen is up only a short time), you should get a screen to select your language, then follow mike555's directions for  pressing F6 & entering nomodeset.  
You might try pressing F6 as soon as the human stick figure-keyboard screen appears.


Thanks.  I did that and got Ubuntu screen after selecting English, pressed F6 and selected nomodset.  I then selected "install Ubuntu" .  But it did not install, it just booted from the ISO disk instead.  After it booted from that disk it also had a crash report but I couldn't figure out what it was for.

So I double clicked on install 10.04 LTS and it started the install.  When it came to the partitioning section it did not find my Ubuntu drive.  I have two drives installed, a 320 drive with Windows XP on it and a 250 drive with Ubuntu 10.04 on it.  It wanted to install Ubuntu on the same drive as Windows and I didn't even have a choice for the other drive so I cancelled it.

Is my HD going bad?

---

### Post by mike555 on 2010-07-22
perhaps when it showed your drive it had a little arrow beside it? clicking that arrow might have shown the other drive...

---

