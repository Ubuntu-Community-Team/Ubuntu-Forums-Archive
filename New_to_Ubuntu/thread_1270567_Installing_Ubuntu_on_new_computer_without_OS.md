---
title: "Installing Ubuntu on new computer without OS"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by ophansom on 2009-09-19
I've been using Ubuntu on my laptop for a while. I have it alongside Vista. I now need to replace my desktop and want to use Ubuntu on that too but on its own.

I'm thinking of getting a machine with Intel Core 2 Quad Q8200 processor, Asus P5KPL-AM (Intel G31 chipset) motherboard and ATI Radeon HD 3450 512MB graphics card. This can be supplied without an operating system installed.

I still have the Ubuntu 9.04 CD I used on my laptop but I could easily get an up-to-date one. My existing one may have been intended mainly for double-booting but I don't want this on the desktop. There did seem to be an option to do a simple Ubuntu install. 

I'm thinking that it should be straightforward to boot with the CD drive as first choice device but past experience of doing something for the first time raises the fear that there may be something I'm not appreciating. Existing threads all seem to be about installing Ubuntu along with Windows.

Can anyone reassure me or tell me what I may be missing!

---

### Post by VastOne on 2009-09-19
> **ophansom said:**
> I've been using Ubuntu on my laptop for a while. I have it alongside Vista. I now need to replace my desktop and want to use Ubuntu on that too but on its own.

I'm thinking of getting a machine with Intel Core 2 Quad Q8200 processor, Asus P5KPL-AM (Intel G31 chipset) motherboard and ATI Radeon HD 3450 512MB graphics card. This can be supplied without an operating system installed.

I still have the Ubuntu 9.04 CD I used on my laptop but I could easily get an up-to-date one. My existing one may have been intended mainly for double-booting but I don't want this on the desktop. There did seem to be an option to do a simple Ubuntu install. 

I'm thinking that it should be straightforward to boot with the CD drive as first choice device but past experience of doing something for the first time raises the fear that there may be something I'm not appreciating. Existing threads all seem to be about installing Ubuntu along with Windows.

Can anyone reassure me or tell me what I may be missing!

Use the disk you have and let it rip...

You are set with all you need.  I setup new computer builds all the time with the same disks.  You have the opportunity to set it up with /home on a separate partition, I would highly recommend that

---

### Post by Garrovick on 2009-09-19
Just put the disc in the drive, boot up, set the bios to read the CD/DVD as boot and have at it.

---

### Post by themusicalduck on 2009-09-19
Just on another note, mightn't you want to get an Nvidia card instead of ATI? Simply because the Nvidia drivers apparently work so much better than ATI at the moment.

---

### Post by VastOne on 2009-09-19
> **themusicalduck said:**
> Just on another note, mightn't you want to get an Nvidia card instead of ATI? Simply because the Nvidia drivers apparently work so much better than ATI at the moment.

+1

I tried an ATI one time and that was enough....

within 5 minutes I was ready for the nvidia

---

### Post by jmszr on 2009-09-19
ophansom,

This may be of help: [http://www.ubuntugeek.com/step-by-step-ubuntu-904-jaunty-desktop-installation-guide.html](http://www.ubuntugeek.com/step-by-step-ubuntu-904-jaunty-desktop-installation-guide.html) .

+1 for Nvidia and /home partition.

---

### Post by halitech on 2009-09-19
the ATI Radeon HD 3450 is currently supported by ATI but if you can substitute for an Nvidia I would go for it.

Other then that, any Live cd can be used to install Ubuntu as th eonly OS on a system or set it up for dual booting.

---

### Post by sandyd on 2009-09-19
> **halitech said:**
> the ATI Radeon HD 3450 is currently supported by ATI but if you can substitute for an Nvidia I would go for it.

Other then that, any Live cd can be used to install Ubuntu as th eonly OS on a system or set it up for dual booting.
a side note - don't install the ATI driver from the ATI site. Install the one that ubuntu suggests. tried the one from the site and it didn't give full functionality. ended up removing it and running jockey-gtk to get the drivers.

---

### Post by AgentZ86 on 2009-09-19
> **ophansom said:**
> I've been using Ubuntu on my laptop for a while. I have it alongside Vista. I now need to replace my desktop and want to use Ubuntu on that too but on its own.

I'm thinking of getting a machine with Intel Core 2 Quad Q8200 processor, Asus P5KPL-AM (Intel G31 chipset) motherboard and ATI Radeon HD 3450 512MB graphics card. This can be supplied without an operating system installed.

I still have the Ubuntu 9.04 CD I used on my laptop but I could easily get an up-to-date one. My existing one may have been intended mainly for double-booting but I don't want this on the desktop. There did seem to be an option to do a simple Ubuntu install. 

I'm thinking that it should be straightforward to boot with the CD drive as first choice device but past experience of doing something for the first time raises the fear that there may be something I'm not appreciating. Existing threads all seem to be about installing Ubuntu along with Windows.

Can anyone reassure me or tell me what I may be missing!

You should have not problem doing a fresh install, I personally would just select the option to let ubuntu use the entire hard drive. And if you are using dual core I'm assuming your using 64 bit processors so you'll probably want to install the 64 bit version.

Then you may have a few tweeks to get the flash and java installed thats the main thing to setup perhaps you could do that after the install, and the upgrades.

I've had most luck installing, then restarting, then upgrading the restarting.

Then install flash and java. I typically just install the version in the applications/add-remove and just type java in the search and install only one and some of the others will install on their own, I select the one that says webstart 6 or something like that which includes java and a few other things.

Then install flash for mozilla plugin thats the only one I use.

That seems to be the simple and quick setup you should be all setup in less then 20 min. once you pop the CD in the drive

Anyhow thats about all I know and I've never had any problem installing it's the simplest thing to do really.

And if you need video third party driver install the system usually tells you this too, but you could go to the the System/Preferences/Hardware driver section to install third party driver for your vid card if needed.

But likely the install will pick it up for you.

Anyhow should be nothing to it really, and you can't really ruin anything. 
You could always re-install from CD if you mess something up.

Happy hacking

---

### Post by halitech on 2009-09-19
> **carlee said:**
> a side note - don't install the ATI driver from the ATI site. Install the one that ubuntu suggests. tried the one from the site and it didn't give full functionality. ended up removing it and running jockey-gtk to get the drivers.

guess I was more pointing out that if ATI is supporting it then there should be an Ubuntu driver but yeah, go with the Ubuntu driver instead of the ATI driver.

---

### Post by Jazzy_Jeff on 2009-09-19
I would go with nVidia as well. They work so much better and some games will only play with nVidia.

---

### Post by Soley on 2009-09-19
> **jmszr said:**
> ophansom,

This may be of help: [http://www.ubuntugeek.com/step-by-step-ubuntu-904-jaunty-desktop-installation-guide.html](http://www.ubuntugeek.com/step-by-step-ubuntu-904-jaunty-desktop-installation-guide.html) .

+1 for Nvidia and /home partition.

Another vote for nVidia here, too. I'll never use ATI again until they get their drivers in Linux sorted out. 

/home partition ftw. I used to not run with one of those, but it makes everything sooooooooo nice if you run into an issue with your OS.

---

### Post by oldfred on 2009-09-20
You did not mention drive(s). +1 on separate /home, but if you have a large drive or more you may want a separate /data also. When you have lots of space you get the urge to try other systems. I current have Ubuntu32, but have also installed Ubuntu64 to try out as I will convert to 64 bit for Karmic, and I installed Karmic just to see what the alpha has to offer.
I set up a separate partition just for testing other distributions and with a separate /data it is easy to access all your data. Yes you can easily mount your standard install and /home but you should not share home with different distributions as some configs may be different.

---

