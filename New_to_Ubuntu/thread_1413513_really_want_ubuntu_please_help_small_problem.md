---
title: "really want ubuntu please help small problem"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by balkrish999 on 2010-02-22
hello can some1 tell me the bad stuuf about using the wubi the cons, dis  advantages 
(im going to use ubuntu forvevery if i can install it on  a duall boot with wubi )

also if i use wubi 

i get a  duall boot with ubuntu and windows 7 and the ubuintu installs in the  windows partion right  or do i need to create a new partion  thanks

after this ill finally get it woooohoooo:D:D:D:):):popcorn::KS:KS  thanks

---

### Post by NightwishFan on 2010-02-22
I am not sure if Wubi works with Windows 7 yet. If you want to do a true dual boot, just create another partition for Ubuntu using the Windows disk tools. I would wait for help here concerning any new Windows 7 nuances related to boot.

To find disk tools, right click "My Computer" and hit manage.

---

### Post by cap10Ibraim on 2010-02-22
I dual boot Windows 7 and Ubuntu 
You must have an empty partition , if now you have one partition defragment it then shrink it to create a new partiotion , when you run the ubuntu live cd every thing will be easy and clear

---

### Post by balkrish999 on 2010-02-22
WTF i just found this out 

[[COLOR=#0000ff]http://www.youtube.com/watch?v=1-2DckmUPJo[/COLOR]]("http://www.youtube.com/watch?v=1-2DckmUPJo") 

 
 
i dont want to make a partion!!!!!! cant i duall boot ubuntu in the same pasrtionas windows !!!!! just like the guy did in the vidoe!!! please llok!! i dont want to make a partion.  
 
what does wub do then . please understand i dont want to partion my drive .
 
cant i install ubuntu on a dual boot in the same partion as my winodws 7 and still get a duall boot with ubuntu and windows 7

---

### Post by NightwishFan on 2010-02-22
Your drive is likely already partitioned if you bought it retail.

WUBI is like a virtual partition included in your Windows drive of choice. It is not a good permanent method for install. It leads to I/O performance loss, but I doubt many would notice. It is good for trying ubuntu or for using on a machine that you won't have forever.

Partitioning is not permanent and not difficult. Frankly the only difficult thing about partitioning is how picky Windows is. (Which I am sure is intentional to avoid someone trying to not use Windows). That can be worked around by creating free space using Windows tools to do so, then just install Ubuntu on free space automatically.

---

### Post by Tahakki on 2010-02-22
Yes, you'll want to shrink your Windows partition from within Windows 7, as I did recently. Check the 'Disc Management' tool included with Win7.

---

### Post by bodhi.zazen on 2010-02-22
You can also use VirtualBox on Windows and install Ubunt into a virtual disk.

You can then run Ubuntu without rebooting.

If you like it enough to install it, then I also advise you back up your data and partition your hard drive.

---

### Post by WubiNoob on 2010-02-22
All you have to do is tell wubi to put it on C:\ and then it dual boots when you restart.

---

### Post by shadowlands on 2010-02-22
Can you give a dummy's guide or is one already out that can help folk with this. I thought you said not to wast time with wubi?> **bodhi.zazen said:**
> You can also use VirtualBox on Windows and install Ubunt into a virtual disk.

You can then run Ubuntu without rebooting.

If you like it enough to install it, then I also advise you back up your data and partition your hard drive.

---

### Post by undecim on 2010-02-22
I'm not 100% sure (I haven't had a chance to try wubi myself yet), but I think that if you install wubi to your C: drive, it still creates a virtual partition (a large file on your hard drive that acts as the ubuntu partition), which uses up just as much space as a real partition, but will be slower and more troublesome

As for the pros and cons of Wubi, it can have a lot of problems that don't apply to a real installation, and most people here on the forums aren't very experienced with it, so you won't be able to get as much assistance with specific issues.

Unless you have a specific reason for not wishing to partition your hard drive, an installation from a CD will work out much better. It will run faster than a Wubi install (because it doesn't have to deal with Windows' cruddy filesystem), and there really is nothing to partitioning. All you have to do is determine how much room to give to Ubuntu while installing (similar to the "Installation Size" option on Wubi)

EDIT: [s]huh... looks like the video title is wrong. Take a look at 4:15 on the video.[/s] EDIT 2: nvm, a few seconds later it describes the partition as a loopback device, which is that virtual partition I described above...

---

### Post by t1nm@n on 2010-02-22
hello there ..this is only a suggestion from my side.... if you really want to experience ubuntu u have to go deeper into linux... so get virtualbox and use ubuntu from inside it...or there is something called portableubuntu which runs ubuntu from windows ...give it a try...

Virtualbox is a safe solution here as there will no damage to your computer... what so ever...
[http://portableubuntu.demonccc.com.ar/](http://portableubuntu.demonccc.com.ar/) check out this for  portableubuntu
[http://www.virtualbox.org/](http://www.virtualbox.org/) check out this for virtualbox

[http://www.vmware.com/](http://www.vmware.com/) this is also like virtualbox... but get it from softpedia.com and ask the serials from [http://www.vmware.com/](http://www.vmware.com/)

Best of luck..

---

### Post by brons2 on 2010-02-22
> **balkrish999 said:**
> 
 
i dont want to make a partion!!!!!! cant i duall boot ubuntu in the same pasrtionas windows !!!!! just like the guy did in the vidoe!!! please llok!! i dont want to make a partion.  
 


Why are you so paranoid about re-partitioning?  It isn't difficult.

---

### Post by balkrish999 on 2010-02-23
> **brons2 said:**
> Why are you so paranoid about re-partitioning?  It isn't difficult.



trust me i know how to partion a drive but i have a rubbish laptop and its already got 4 partions and wont let me create another 1 please dont help me on this as i spent 1 week trying to find out :):

---

### Post by bodhi.zazen on 2010-02-23
If you want to make additional partitions you need to remove one of the existing partitions and make an extended partition.

Basically you may only have 4 primary partitions, but extended partitions allow additional partitions.

See : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

### Post by 3rdalbum on 2010-02-23
Disadvantages of Wubi:

1. If Windows crashes, you can't boot Ubuntu until Windows has started up and shut down correctly again.
2. If Windows stops working completely, you can't boot Ubuntu until Windows works again.
3. Slight speed bottleneck
4. You're limited to 30 gigabytes of space*
5. No hibernation
6. You can't remove Windows and keep Ubuntu*.

Wubi is for people who want to try a real installed version of Ubuntu briefly, before deciding whether to take the step of partitioning their drive. If you want to keep Ubuntu, then you really should repartition your drive.

* Okay... it's possible to do these things apparently, but it takes some hacking.

---

### Post by waynefoutz on 2010-02-23
A wubi install can't be any simpler, it installs just like any other windows application. Just but the ubuntu disk in while windows is running and hit the button that says install ubuntu under windows. It's a great way to get your feet wet, but as other peole have pointed out, it has it's disadvantages. What wubi does is create a big file which fools ubuntu into thinking it is a partition. When running ubuntu, I really haven't noticed and speed loss, but because it's a big file, the ubuntu install is unstable, because if something happens to that file the wubi install is destroyed. Killing the power while ubuntu is running, for example will likely destroy the wubi install. It's really for testing purposes only. Also, that big file will interfere with Windows' defrag program, so eventually it will be a drag on your windows performance. Go ahead and give wubi a try. It's a great way to try out ubuntu. The big advantage of wubi is that it is easy to remove. Simply going into Windows' Add/Remove programs utility in the control panel and uninstalling ubuntu puts your system right back the way it was, it's a pretty clean way to try ubuntu without the commitment of partitioning your hard drive. I just wouldn't expect it to be a permanent install, it's not meant to be that.

---

### Post by balkrish999 on 2010-02-23
thanks eveyr !!!!!!!!!!!

---

