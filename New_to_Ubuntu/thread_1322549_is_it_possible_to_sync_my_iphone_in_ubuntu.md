---
title: "is it possible to sync my iphone in ubuntu?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by dudz1976 on 2009-11-11
that's it.  is there a way to sync my iphone & itunes in ubuntu.  i do have the latest release of ubuntu, but am fairly new to it.  i would like to eliminate having to log onto windows just for the purpose of my iphone.  any help is appreciated...

---

### Post by snowman12 on 2009-11-11
Someone correct me if I'm wrong or missed anything, but as far as I know these are the only way to run window programs in ubuntu

1) try out wine, [www.winehq.org](www.winehq.org) but dont expect it to work fully

or

2)  you could install virtualbox, put windows on it then install iTunes on that, this will work, but most likely will be rather slow

hope this helps

---

### Post by jbrown96 on 2009-11-11
Unfortunately there's no way to do it. Apple has encrypted the device, so only itunes can control it. I have an iphone, and I've found that the best way to run itunes is in Virtualbox. Add the repository from [virtualbox.org]("http://virtualbox.org"). It's fairly easy to set up. 

Be sure to install the guest additions after installing XP; it really improves the usability. When XP is shutdown, go into the settings for it. There's a section for USB click on it. With the iphone plugged in, click the green plus sign and click on the iphone label. This will allow XP to have complete control over the device. Now you will be able to sync your iphone. 
WARNING: DO NOT UPDATE THE IPHONE OS SOFTWARE IN VIRTUALBOX!!!! IT WILL CAUSE THE DECIVE TO GET STUCK IN A REBOOT LOOP
You might want to try Vmware; I've heard it is at least as good as Virtualbox, but I've always had trouble installing it. [http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04]("http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-9.04") This seems to be a good guide to get you started if you want to try it. THE IPHONE UPDATE BUG MAY EXIST IN VMWARE. 

The great thing about Virtualization with Virtualbox or Vmware is that you don't need to reboot the machine just to sync a few songs. Syncing music isn't something that done for significant amounts of time, so rebooting the computer is not usually worthwhile.

---

### Post by rich97 on 2009-11-11
> **jbrown96 said:**
> Unfortunately there's no way to do it. Apple has encrypted the device, so only itunes can control it. I have an iphone, and I've found that the best way to run itunes is in Virtualbox. Add the repository from [virtualbox.org]("http://virtualbox.org"). It's fairly easy to set up.

There is a way, but it's still under heavy development. This is not an option for a newbie. Just letting you know, they plan to package it soon, so fingers crossed for the next release!

But yeah, at the moment VirtualBox is the way to go! :(

---

### Post by dudz1976 on 2009-11-11
thank you for the help.  i will begin messing around with these options and wait for further developments.  cheers!

---

### Post by aeon.flux on 2010-01-07
hm, if you want just sync music, you could try Rhythmbox, it can sync songs with ipods, (edit/plugins/portable players - ipod) and iphone could work too, cause it use os version same as ipod touch. but if you want to install iTunes, you could look at Alien, it can rebuild install files like rpm into deb or ubuntu packages, and it can (maybe) work with mac osx install files. i'm not sure about this, but you could try to google it :) ...good luck

---

### Post by speedwell68 on 2010-01-07
IIRC there is an application called iFuse that allows you to mount an iPhone or iPod Touch in Linux.

---

