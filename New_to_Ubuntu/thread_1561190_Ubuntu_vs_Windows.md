---
title: "Ubuntu vs Windows"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by neeraj.jadhav on 2010-08-25
Hey,

I want to install Ubuntu in my laptop, however I got Windows 7 already running. Is there any way i can install Ubuntu in my laptop without affecting my resident OS?

---

### Post by Maverick_Meerkat on 2010-08-25
Absolutely! You can install Ubuntu side by side with Windows. without complications. You do not even need to partition your HDD. Although, it is generally recommended to install Ubuntu on a separate partition for numerous reasons.

The WUBI installer is probably the easiest method for a beginner to accomplish that task.

---

### Post by Chris1274 on 2010-08-25
You have the option to install them side by side during the installation process.

---

### Post by Jerry N on 2010-08-25
> **Chris1274 said:**
> You have the option to install them side by side during the installation process.

Before doing a side-by-side install, be sure to shrink the Win 7 partition using the partition manager inside Win 7.  I don't know what this is called because I haven't done it but Win 7 provides great help and it should be easy to find.  Personally, I would do a manual install of Ubuntu after Win 7 shrinks its partition.

Jerry

---

### Post by Col.Krumpet on 2010-08-25
You betcha. Ubuntu can even partition your HDD for you. When you start the install disk one of the questions it'll ask you is if you want to partition your Hard Drive and allow you to allocate however much HDD space you want to devote to the new OS (in this case Ubuntu) the only limitation is that you have to at least leave enough HDD space for the native OS (windows) also you may want to take Jerry N's advise about shrinking the Win7 partition first. I don't know if NOT doing it will effect the Ubuntu installation but it may be worth looking into just in case. 
Its way more simple than it sounds but trust me when you get to that part of the installation you'll see exactly what I'm talking about.

Hope that helps, good luck :)

---

### Post by M93 on 2010-08-26
u can use 'wubi' its very simple and easy to use
its like u are installing a programe and it allows u how much space do u want to dedicate for ubuntu, make a user'adminstrator"name and a password.
restart computer and its done
u can even uninstall it as easy as installing
u just open 'wubi' again and it asks u if u want to uninstall :)

---

### Post by -kg- on 2010-08-26
Alternatively, you can install Ubuntu to a USB external hard drive.  That way, everything on your internal drive is left pristine, and when you want to boot into Ubuntu, you just select the USB drive in your "Boot Device Selection" menu at startup (on my laptop, it is "F-12", with "F-2" for BIOS).

You have to be careful with this method, however.  You want to make sure to install it to the right drive, and you want to install GRUB in the MBR of your external drive...***_NOT_*** the default (your internal hard drive...I just helped a person out with this very problem).

If you would prefer this method, I can walk you through it.

---

### Post by Guilden_NL on 2010-08-26
My two cents is that I recommend -kg-'s method using a USB drive to try out Ubuntu.  If you like it after a couple of weeks, then install it on your hard drive.

Check out how much empty space you have on your hard drive before re-partitioning your Win7 space - that sucker needs GBs up the wazoo.  If you shrink it much and don't leave much space for Win7, you're going to run into problems later with your Win7 installation.

I personally don't recommend Wubi; I've seen way too many problems going that route and IMHO it is the lazy way to install that causes you more pain and time later.  That's just my opinion and others will certainly disagree with me.

In any case, once you have Ubuntu installed, there are a couple of routes to take: big eye candy that makes Win7 look like your Grandpa's OS, or the lightweight super fast route that makes Win7 oink like the pig that it is.

I have many Ubuntu installs on my home network and have more lightweight than Eye Candy.  But for my wife and son's main laptops (very fast CPUs, 16GB memory on both) we went the Eye Candy route.  I went super Eye Candy for my main desktop in my office, I won't go into details because it sounds like bragging, but it's mind blowing fast.  

I am writing this on a heavy duty business laptop in "ZING!" extreme light and fast mode.  From when I press the power button to sign in page is 7 secs, from sign in to ready to launch Firefox is 9 seconds. I've optimized Firefox too so a 300 millisecond delay on this middle of the road CPU and only 8GB RAM laptop would make me angry.

Plenty of tweaking to do, loads of fun and reliability is great.  I think you'll like Ubuntu if you like to tweak your system to get it just the way you like it.

Try any of that with Win7!

---

### Post by mastablasta on 2010-08-26
1. back up data
2. defrag the disk
3. insert ubuntu CD, boot from it and start instalation
4. during instalation slide the slider to give the ubuntu space on your windows disk. depending how much disk you want to dedicate to Ubuntu. just slide it arround until the size you want.
5. continue with instalation. when it's done reboot and voila.
 
you now have two systems side by side.
 
oh make sure Ubuntu works well with your laptop by using live session first...
 
Read more here in the manual:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
 
Or this one for a bit older vesion but still valid i believe:
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by Mark Phelps on 2010-08-26
> **mastablasta said:**
> ...
4. during instalation slide the slider to give the ubuntu space on your windows disk. depending how much disk you want to dedicate to Ubuntu. just slide it arround until the size you want.[
Using this approach runs the risk of corrupting the Win7 partition.

A much BETTER approach is to use the Win7 Disk Management utility to shrink the partition from inside MS Windows.

Then, when you go to install Ubuntu,  use the "largest free space" option to allow it to partition that space and install.

---

### Post by mastablasta on 2010-08-27
> **Mark Phelps said:**
> Using this approach runs the risk of corrupting the Win7 partition.
 

 
I don't know about Win7, but if this is true why does this option exists?

---

