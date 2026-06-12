---
title: "Virtualbox or WUBI"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Rabcnesbit on 2010-03-27
Hello all.

Please forgive me if I have posted this in the wrong category. I want to install Ubuntu 9.10 (got the CD) on my Windows PC, mainly to use for internet surfing, as Linux based OSs are generally considered to be less vulnerable to malware than Windows based OSs. I do not want to go via the 'dual boot' way, and have heard of Virtualbox (which allows you to install  another OS as a 'guest' on the 'host' PC OS), and WUBI. I just wondered what are the pros and cons between the two methods (Virtualbox and WUBI) if anybody knows please, so I could make an informed judgement as to which one to go for, or if there are other suggestions I am not aware of?

Many thanks.
Dan

PS. Before anyone mentions it, I am keeping the Windows OS because I have got quite a few apps that I use regularly, but only run on Windows.

---

### Post by stmiller on 2010-03-27
Virtualbox route is the best - but you need 2GB of ram or more for it to work well. You can virtualize with less ram, but it can bog down your machine.

---

### Post by lotharmat on 2010-03-27
Personally, I'd go for a dual boot (not wubi)

---

### Post by tica vun on 2010-03-27
Wubi still installs a dualboot system, it just keeps your ubuntu partitions in a virtual FS that's actually a file inside your windows partition. So if you don't want to dual boot, virtualisation is the only way to go.

Since you mentioned there are only a few windows-only applications keeping you from switching, you might want to look up if there are any suitable open source alternatives, here: [http://www.osalt.com/](http://www.osalt.com/) .

---

### Post by NightwishFan on 2010-03-27
The biggest part of security is not the OS but the user. You should be fine browsing the web using Windows if you have good habits. As said, I advise a dual boot.

If you do not want to dual boot and yet run a high performing native Linux kernel go with Wubi. It should perform nearly like a real install and be much easier to remove. Read the FAQ:
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

For Virtalbox if you go this route remember you will need to install vbox guest additions to be able to use higher resolution such as fullscreen. It has the advantage of being able to switch between both OS at will. Again another disadvantage is Windows will perform worse as it manages the virtual machine, and Ubuntu will perform worse because it *is* a virtual machine.

If you want, you can use a live CD to install ubuntu on a USB flash drive. It will perform well and you can choose to have it retain settings and files. If you like this idea, please note your machine must be able to boot from USB to use it. I can help you with whatever path you choose.

---

### Post by Rabcnesbit on 2010-03-27
> **NightwishFan said:**
> ...If you want, you can use a live CD to install ubuntu on a USB flash drive. It will perform well and you can choose to have it retain settings and files. If you like this idea, please note your machine must be able to boot from USB to use it. I can help you with whatever path you choose.

Firstly, thank you everyone for your advice, very much appreciated. 

NightwishFan, you suggestion with the live CD via a USB flash seems like a good idea, as all I really need it for is surfing the net. Could you advise me please how to go about this? 

Many thanks
Dan

---

### Post by sixthwheel on 2010-03-27
> You should be fine browsing the web using Windows if you have good habits.
And enough RAM and patience to run your  anti whatever crap in the background 24/7, while surfing.

The MAIN reason I left Windows was just because of that.
Good habits while surfing on Windows=don't click on anything.

Now with Ubuntu, I'm surfing without fear, and it doesn't cost me a dime, in anti whatever crap, nor it costs me any of my time or patience.

---

### Post by NightwishFan on 2010-03-27
You can use Unetbootin for Windows, but I am unsure if it allows you to save data such as bookmarks between boots.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

A way I know is to boot into an Ubuntu live CD, and use the ubuntu live usb creator while on there. It is under System -> Administration. You can choose to use the space at the end of the flash drive to store files and settings. One downside is that this tool take a long time on some systems.

---

### Post by mike555 on 2010-03-27
you might look into "puppy" linux , it is very fast and you can just boot it from a cd or usb drive .......

---

### Post by NightwishFan on 2010-03-27
I second puppy.
[http://www.pendrivelinux.com/puppy-linux-on-usb/](http://www.pendrivelinux.com/puppy-linux-on-usb/)

---

### Post by theozzlives on 2010-03-27
For awhile, when I first got Ubuntu, I ran Ubuntu as host and Windows in a VirtualBox. It worked fine and when I was done with Windows, I backed up the "file" and just deleted it. Now my laptop is pure Ubuntu.

---

### Post by C.S.Cameron on 2010-03-28
A good alternative to wubi and dual booting is to install Ubuntu, (or any other Linux), to a thumbdrive.
This will not mess with your hard disk and is reasonably fast.
Use usb-creator that comes with Ubuntu to make a persistent install, (2GB drive required), or do a normal install to the thumbdrive, (4GB drive required).

---

### Post by underquark on 2010-03-28
I used DOS and ubuntu (Dapper Drake) and BeOS and Windows and OS2 and various other OSs many years ago. I got lazy and used Windows because it came with the machine but I was forever running virus-scan programs -  especially in the past two years - and I found that the Windows Registry got bloated and everything slowed down a lot and so I switched back to ubuntu.  I'd suggest you try the dual-boot route as it really is very easy. I started (again) by stubbornly trying to use ubuntu over Windows but now I find that I rarely need to boot into Windows and rather like the   30-second boot-up of ubuntu.

---

### Post by Rabcnesbit on 2010-03-28
> **mike555 said:**
> you might look into "puppy" linux , it is very fast and you can just boot it from a cd or usb drive .......

Ok, many thanks everyone for all your advice/suggestions. I have tried the 'puppy linux' way suggested above, and it's not bad so far. Anyway, I have decided to go the 'dual boot' way and installed ubuntu 9.10 side-by-side with Windows. :)

---

