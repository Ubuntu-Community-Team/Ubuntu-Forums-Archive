---
title: "Virtualizing Windows"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by ZhaphodBeebleBrox on 2009-05-21
Hi 


I have successfully installed ubuntu and got my laptop to dual boot windows and ubuntu


Is it possible to boot up my Windows installation from withing Ubuntu via a Virtualization Solution ?

If so what solutions / threads / forums should I take a look at 

thanks

Rupinder

---

### Post by Therion on 2009-05-21
Yes.  You can use Virtual Box or VMWare Workstation.  Here's one guide for configuring VirtualBox:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

There's also the Virtualization subforum:  [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by rcayea on 2009-05-21
I am wondering, do you mean can you create a virtual machine out of your windows or ubuntu (whichever OS you want) so that it can later be run in a virtual machine?

Would this be what you are looking to do?

Randy

---

### Post by stefangr1 on 2009-05-21
> **Therion said:**
> Yes.  You can use Virtual Box or VMWare Workstation.  Here's one guide for configuring VirtualBox:

[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

There's also the Virtualization subforum:  [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)



Not vmware workstation. You should use vmware server 2.

And this runs windows like a program, you can't run your regular dual boot install from it. Also, you need proper hardware: at least a dual core with enough ram to support two operating sytems.

---

### Post by Therion on 2009-05-21
> **stefangr1 said:**
> Not vmware workstation. You should use vmware server 2.
VMWare Workstation is a perfectly viable solution;  I've used it extensively.  

I find it a better solution, really, than VirtualBox.

---

### Post by Sable683 on 2009-05-21
VMWare has VMware vCenter Converter, it is a program that you can download and install into windows. This will create a virtual version of your physical windows machine.

Things to consider, you should use a USB drive for your target drive for the virtual machine because it will duplicate your whole hard drive with windows on it. Then you can copy the files into your Ubuntu partition and install either VMware server 2 or Virtual Box. Just my opinion, Virtual Box seems to work much better.

~Sable

---

### Post by stefangr1 on 2009-05-21
I also prefer vmware over virtual box, though I compared a long time ago and I have heard that virtual box has also improved a lot.

wmware workstation is nonfree and prides only some small advantages over vmware server.

---

### Post by Cypher on 2009-05-21
VirtualBox has surely come a very long way in the past year or so with Sun's blessings..it's really become a VERY competent alternative to the paid VMServer.

It's just that the OSE (open source edition) that comes from the Ubuntu repository is missing USB support. So you have to grab the closed-source edition from Virtualbox.org to get that. For regular users, this is a perfectly acceptable thing.

---

### Post by ZhaphodBeebleBrox on 2009-05-21
Hi Randy


I  had a laptop running xp only ,

I installed ubuntu 

I would like to run the exisiting XP installation on the HDD as a XP VM  on ubuntu

I donot want to create another XP installation , as there will be problem with joining my workplace windows domain , and getting access to network shares and devices





> **rcayea said:**
> I am wondering, do you mean can you create a virtual machine out of your windows or ubuntu (whichever OS you want) so that it can later be run in a virtual machine?

Would this be what you are looking to do?

Randy

---

### Post by Cypher on 2009-05-21
You cannot just point VirtualBox/VMWare to your exting Windows installation and expect it to virtualize it.

You will have to re-install it, but it might be possible for you to save everything on your Windows installation as it is today, configuration and all, and install that customized version into the virtual instance within Ubuntu, that should retain everything and allow you to connect to your existing domains and so on.

You might want to google this and see if it's possible.

The traditional scheme of using virtualizatio is to create a brand new virtual machine and then do a fresh install of the OS you wish to use in that virtual environment.

---

### Post by ZhaphodBeebleBrox on 2009-05-21
this is what i was afraid of , 

making a new installation defeats my purpose of launching a windows VM  in ubuntu


i guess its time to explore Wine or the like and run my windows app from ubuntu


its just the file and device shares that worry me more ,since the by device i mean more then just printer or faxes 







> **Cypher said:**
> You cannot just point VirtualBox/VMWare to your exting Windows installation and expect it to virtualize it.

You will have to re-install it, but it might be possible for you to save everything on your Windows installation as it is today, configuration and all, and install that customized version into the virtual instance within Ubuntu, that should retain everything and allow you to connect to your existing domains and so on.


---

### Post by Sable683 on 2009-05-21
Despite what Cypher has said, you DO NOT have to re-install your Windows XP as long as you have a usb drive or network drive with enough free space to duplicate your whole windows partition from your laptop.

VMware vCenter Converter WILL virtualize your XP Laptop by creating a virtual hard disk that is an exact duplicate of your physical machine. This file may be 20 GB or whatever your XP partition size is, but it can be done relatively easily. You will retain all of your files network and domain settings and all. This file can be opened in either VMware or Virtual Box.

hope this helps

~Sable

---

### Post by Cypher on 2009-05-21
I imagine that there was a way of convering a physical installation into a virtual one, that's very cool. Something to bookmark..

---

