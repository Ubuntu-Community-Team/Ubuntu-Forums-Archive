---
title: "Super Noob needs some help"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by brentdavis29 on 2009-02-21
I've been wanting to try out Linux for years, but I dare not just uninstall XP and start cold on Linux. I want to ease into it I finally have my chance, because I was given an extra machine that can I can run Ubuntu while I keep XP on the laptop.
 
Here's what I want to do:

I don't want to clutter my desk with an additional monitor/keyboard/mouse that interfaces with my Ubuntu desktop. I'd like to make it so that I can somehow "switch" to the Ubuntu desktop while still using my laptop monitor/keyboard/mouse.

I have looked through the forums to see if I could help myself, but the answers just haven't been simple enough for a Ubuntu virgin such as myself. 

Thanks for any help in advance.

---

### Post by Doug11 on 2009-02-21
> **brentdavis29 said:**
> I've been wanting to try out Linux for years, but I dare not just uninstall XP and start cold on Linux. I want to ease into it I finally have my chance, because I was given an extra machine that can I can run Ubuntu while I keep XP on the laptop.
 
Here's what I want to do:

I don't want to clutter my desk with an additional monitor/keyboard/mouse that interfaces with my Ubuntu desktop. I'd like to make it so that I can somehow "switch" to the Ubuntu desktop while still using my laptop monitor/keyboard/mouse.

I have looked through the forums to see if I could help myself, but the answers just haven't been simple enough for a Ubuntu virgin such as myself. 

Thanks for any help in advance.
You could always dual boot. There are many how-tos out there. Try a quick search on it. Should have many returns. I'll see if i can find the howto I first used.

---

### Post by Bigbob22 on 2009-02-21
You should try Wubi.

---

### Post by rafac24 on 2009-02-21
Dual-Boot would be the best option so that you can keep your Windows XP and still be able to try Linux on the laptop without losing any data.
Once you familiarize yourself with the dual-boot process, you will find it to be very easy.

You would basically partition your hard drive to run both Windows and Ubuntu. I used to own a Dell Laptop with only 30 GB of hard disk space and  I partitioned the drive 'half and half'. (15 GB for Windows and 15 GB for Ubuntu)

---

### Post by jmszr on 2009-02-21
brentdavis29,
             I would suggest that you check out this: [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) . This is listed in that guide and I would recommend it: [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

For the two computer-one keyboard/mouse issue try this:[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

---

### Post by cariboo on 2009-02-21
You are going to need a keybaord, mouse and monitor, you could use a [USB KVM]("http://www.tigerdirect.ca/applications/category/category_slc.asp?CatId=202") to switch between your laptop and desktop. About the only way you could do what you want is with remote desktop viewing which is not optimal.

Jim

---

### Post by rafac24 on 2009-02-21
Here's a pretty simple dual-boot process:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

Be sure to back up all your files in Windows in the case of a problem.

---

### Post by Sealbhach on 2009-02-21
The nearest thing to what you're looking for is Wubi.

[http://wubi-installer.org/](http://wubi-installer.org/)

As mentioned by someone else in this post.

You could also run Ubuntu in a virtual machine, like VM Ware or Openbox.

.

---

### Post by chen74 on 2009-02-21
try wubi that should do the trick for you :O) 

[http://wubi-installer.org/](http://wubi-installer.org/) 

its straight forward :D

---

### Post by al_ex on 2009-02-21
> **chen74 said:**
> try wubi that should do the trick for you :O) 

[http://wubi-installer.org/](http://wubi-installer.org/) 

its straight forward :D

wish i knew about this 12 hours ago:(

ah well, i've learnt alot by diving in at the deepend:p

---

### Post by paydaydaddy on 2009-02-21
I have a 4 port KVM switch that usually has 1 windows computer and 2 linux computers connected using 1 keyboard, 1 mouse, and 1 monitor. I can switch between computers simply by pushing a button on the KVM switch or by using a keyboard shortcut. My setup is getting a bit long in the tooth these days as the mouse and keyboard are ps2. Newer switches are available in usb format and usb/ps2 combo format. You can get switches that include audio switching as well. If this is the kind of thing that you are looking for, search for KVM switches in the online stores such as Newegg, Tigerdirect, Directron, etc. The "laptop" may be the fly in the ointment for the KVM. I don't know if there is a way to share the monitor on the laptop. Most laptops to allow for using an external monitor. You may have to buy a monitor to go the KVM route.

---

### Post by brentdavis29 on 2009-02-22
Wow... Thanks for the great suggestions. However, after seeing the responses, I realized that I should have clarified that I would like to find a way to connect to the Linux desktop from my laptop running XP and control it remotely. The reason for this is a) in addition to getting my feet wet with Linux, I would also like to use the hard drive space to start storing photos/music/etc, and b) I don't have enough empty space on my hard drive to dedicate to using Wubi (though I loved this suggestion, and will definitely try on my new laptop).

So, ideally, I would still like to keep the Linux installation on a separate machine while interfacing with it through my XP laptop.

Thanks again!

---

### Post by 3rdalbum on 2009-02-22
For command-line access, you should install the "ssh" client onto the Ubuntu machine and PuTTY onto the Windows machine. (somebody correct me if PuTTY can't connect to ssh - I don't use Windows)

To actually use the mouse and type on your Linux machine as though you were sitting at it, you will need to set up VNC. A VNC server on the Linux machine and a VNC client on the Windows one.

---

### Post by wilcan34 on 2009-04-04
Have the combo KVM switch from which I was hoping to run 2 PC's,one Ubuntu 8.10 and one win xp.
All pluggen in and KVM sees 2 pc,Switch between both but no screen,blank??
Can anyone help?

PS. Am a Ubuntu person though have a cnc programme,VCarve Pro that only runs on win.
Lorraine uses the Ubuntu for work and I the winxp for the cnc,which I unplug and take to the shed.
Regards
GG

---

### Post by hyper_ch on 2009-04-05
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

