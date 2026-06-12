---
title: "Installing Ubuntu - My experience and questions"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by niranjan_rao on 2009-01-26
I had a old Windows 2000 PC that I decided to convert to Ubuntu. I have almost no experience of linux so the stuff I did could have been wrong or I was biased based on my windows experience. I am still trying to set my Ubuntu machine the way I want and I suspect my aging PC (around 7 years old) is adding to my woes. I started with burning a CD from latest distribution from Ubuntu download site as of two days ago. I apologize for the long post but hope that other users can benefit based on answers I get here.

1. PC had USB mouse and keyword combination. Both working for Windows 2000. When I booted the PC from installation CD burned from latest distribution, only keyboard was detected. I was forced to remove mouse from existing port and connect it different port and reboot before mouse was recognized. No idea why windows detected the mouse and not Ubuntu.

2. It's very hard to navigate default installation screen if you don't have mouse. It can be done, but very cumbersome. Try setting time zone information to different default or hard drive partition information. For time zone information, the drop down of the cities does not respond to letter keystroke and you have to press down/up arrow many times until you find the time zone you are interested in. Some help suggestions after googling the problem ask you to go to terminal window which is almost impossible (at least I could not figure out) to open if you don't have mouse.

3. Consistency - Paste in some applications is Ctrl-V (Firefox) and in some applications it's Shift-Ctrl-V (I think it was shell prompt)

3. My biggest trouble was/is setting up my hard drives. I had two hard IDE based hard drives - one 30 GB and other one 10 GB (this is more like 12 years old drive removed from even older PC). Windows was booting from 30 GB drive. I added a PCI card to support SATA drive which apparently adds another BIOS and 180 GB hard disk. My BIOS setup that I get with <DEL> key does not show this drive. 
   
   Default installation process selected this drive to install but did not set up boot mechanism correctly. Installation process went smoothly but I could not boot machine after the installation. I tried changing to other drives with no luck. Even tried manual setup but got confused with all the options that show up and did not which one to pick up.

   Finally I disconnected hard drives - 180 GB and 30 GB. The latter was accidental as I could not determine which drive was which. Look like Ubuntu is installed on 10 GB drive and is working fine.

  Ideally speaking, I want my default OS installation on 30 GB drive and use the 10 GB drive as swap space drive and use the 180 GB drive to save media files or other user data. I also want to format all the drives and start with clean slate. Alternatively I can stay with current install, but want to install applications (emacs or other applications I'll download) that did not get installed, on 30 GB drive.

Can you please help me doing this.

Thanks for the help and looking towards setting my Ubuntu.

---

### Post by cotcot on 2009-01-26
You can get a view on your partitions with ```
sudo gparted
```
I suggest to keep your installation on the 10GB. This is enough for the operating system (i have 6GB used on a 15 GB partition for a system with a lot of applications). Move your /home partition to the 30 GB. You can see how with google on 'move /home to its own partition'. [[COLOR="Red"]Here[/COLOR]]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") is an example. 
The swap does not need to be 10 GB. It is generally recommended to install a swap of 2x your ram memory. If you hesitate take 1 GB on the 10 GB drive.

---

### Post by ugm6hr on 2009-01-26
Sorry about the USB mouse issue - I think I have heard that before.

I suggest - install Ubuntu to 10GB HD with up to 1GB swap (or 1.5-2x RAM).

And use 180GB HD as /home (user files).

You could use the 30GB as a separate directory within /home if you want by creating a link to it.

---

### Post by billgoldberg on 2009-01-26
About the ctrl+v thing:

highlight (copy) + middle click (paste)

---

