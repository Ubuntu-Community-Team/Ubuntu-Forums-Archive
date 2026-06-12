---
title: "Lucid Lynx installation problems"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by highflie on 2010-12-15
Hi all,
 I tried to install Lucid lynx (32 bit) from a pen-drive following the instructions given in the site. When I boot my laptop with the pen-drive, it goes upto the stage where there are options to 
1.) Install ubuntu
2.) Run from CD etc.

When I chose option 1, the purple screen comes on but there's a window saying INSTALL which does not load fully, i.e, the contents are not displayed. 

I tried 3 or 4 times, and the same problem occurs every time.

Thanks in Advance.

---

### Post by amjjawad on 2010-12-15
> **highflie said:**
> Hi all,
 I tried to install Lucid lynx (32 bit) from a pen-drive following the instructions given in the site. When I boot my laptop with the pen-drive, it goes upto the stage where there are options to 
1.) Install ubuntu
2.) Run from CD etc.

When I chose option 1, the purple screen comes on but there's a window saying INSTALL which does not load fully, i.e, the contents are not displayed. 

I tried 3 or 4 times, and the same problem occurs every time.

Thanks in Advance.

Most likely it's the Graphics Card.

However, there are many steps you need to do/follow before anything else:

1) After you downloaded the iso file, did you check the md5sum?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2) Have you tried to choose "Try Ubuntu without installationg"? 
This option is very helpful to find out whether Ubuntu will work perfectly on your machine or not?

3) Could you please list your hardware specifications?

---

### Post by highflie on 2010-12-15
This time, I created the USB stick from an Ubuntu computer using the Create Startup Disk option. I repeated the installation procedure and once again faced the same problem.
However, when I tried the same USB stick on another desktop, the installation window loaded properly so it cant be a problem with the ISO file.

Also, this time the screen showing options to run Ubuntu directly didnt even  load. 

Specifications:
Notebook PC,
3GB RAM, 320GB Hard-disk
512 MB nVIDIA graphics card (8200M)

---

### Post by Hawkoon on 2010-12-15
Are you using a persistent live stick version (allows you to save changes you make to the live system during a session and documents - it the option where you reserve extra space for storage when creating the USB stick)? I had a lot of problems with those, installing from standard live stick versions (non-persistent) on the other hand has always worked for me on my EeePC.

---

### Post by highflie on 2010-12-15
I created it using the default settings in Ubuntu Startup disk creator. As I said earlier, the pendrive worked fine on another desktop. It's causing problems only on my laptop. So, I think it has something to do with my computer only and nothing to do with the USB stick.

@amjjawad: You said it might be a problem with the graphics card. What should I do in that case?

---

### Post by mastablasta on 2010-12-15
> **highflie said:**
> I created it using the default settings in Ubuntu Startup disk creator. As I said earlier, the pendrive worked fine on another desktop. It's causing problems only on my laptop. So, I think it has something to do with my computer only and nothing to do with the USB stick.

 
OK but what happens if you try run the live session (try without installing) on the same computer where install is giving you issues?
 
> 
@amjjawad: You said it might be a problem with the graphics card. What should I do in that case?
 
 
you can use alternate install disk. it will use a text base install. once it's done you can load propper graphics drivers and voila....

---

### Post by amjjawad on 2010-12-15
> **highflie said:**
> @amjjawad: You said it might be a problem with the graphics card. What should I do in that case?

You have nvidia Graphics Card. There are tons of threads on this forum about that. Quite honestly, I don't have any link because I don't have nvidia, I have intel and I have no problem with it. Just try to search the forum and you'll find lots of threads.

Really sorry but at least you know what's wrong now.

---

### Post by cleverbubbles123 on 2010-12-15
Alterante install was a bit more advanced, are you sure you can do it?

---

### Post by highflie on 2010-12-15
> **mastablasta said:**
> OK but what happens if you try run the live session (try without installing) on the same computer where install is giving you issues?
 

 
 
you can use alternate install disk. it will use a text base install. once it's done you can load propper graphics drivers and voila....

1.) When the computer boots, the install window does not even load. So, I cant choose the option of trying to run the live session.

2.) What's alternate install disk?

---

### Post by owiknowi on 2010-12-15
2.) What's alternate install disk?

with an alternate installation disk the installation is more or less in text mode.
also you have more options available during the installation.

boot form the cd and press a Fx at the bottom to choose what you want.
select option by pressing the space bar and esc to leave that menu.

a low resolution may help and the expert mode F6 as well.

see: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by NCLI on 2010-12-15
> **highflie said:**
> 1.) When the computer boots, the install window does not even load. So, I cant choose the option of trying to run the live session.

2.) What's alternate install disk?

When the first purple screen appears, press any key on your keyboard to get to a menu. Select "Try Ubuntu without installing" from that menu.

---

### Post by Hawkoon on 2010-12-15
> **highflie said:**
> ... As I said earlier, the pendrive worked fine on another desktop. It's causing problems only on my laptop. So, I think it has something to do with my computer only and nothing to do with the USB stick.

From my experience, your conclusion is not valid. It is the combination of software and hardware that make or break your deal. I had persistent live sticks working on my desktop, but somehow (depending on the Ubuntu version) my laptops (ATI and Intel graphics) usually only work with the non-persistent versions.

> **highflie said:**
> I created it using the default settings in Ubuntu Startup disk creator. 

When you create a live stick in Lucid, the default setting is to reserve storage space (persistent). Set one up without that extra storage space and give it a try. Also, since it is a laptop you are having problems with, you could try  the netbook version ISO to build the live stick, rather than the standard desktop version. And again, go for the non-persistent install, it is working more reliably.

---

