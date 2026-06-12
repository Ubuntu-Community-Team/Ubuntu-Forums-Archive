---
title: "How to get windows back?"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by MaximoMilkman on 2009-01-06
Hey i am using xubuntu and i think when i installed it i wiped out my windows OS... im not sure.. or maybe i am dumb and dont know how to boot back in to WINDOWS.. i do remember when installing it sayed i needed to partition disc space and it said xubuntu 100% which makes me believe i wiped out windows.. if i did can i reinstall windows somehow?? this linux stuff is TOO Much for me..  having to use terminal to install adobe flash took me about 30 minutes because i didnt know you couldnt just double click the installer and it does magic.. this linux is so complex i would like to have windows back with linux as a second option i still want to learn how to use linux but i need windows back..so how can i have them both?? i have the emergency installition disc for window they give you when you buy a new computer still.. When i boot my computer i hit F12 and hit normal boot up and it automatically boots to LINUX which makes me think linux is my Only OS idk i need major help guys!! i have been up all night and i have school tommorrow im so dang tired help me please.

---

### Post by Michael.Godawski on 2009-01-06
hi,

when you are in Ubuntu run this command in terminal and post the output here:

```
sudo fdisk -l
```this will help us to see if there is a Winodws partition on your system, but I fear there is none.

Double-booting is a good solution. If you have a Windows CD/DVD have a look at this article, there is a link to a very good dual-booting guide site.:


[LIST]
[*][http://godawski.oxyhost.com/switch.html](http://godawski.oxyhost.com/switch.html)
[/LIST]
Do not get discouraged by the complexity of Linux. Everyone was at your point. the learning curve is steep, but the benefits are great.

---

### Post by MaximoMilkman on 2009-01-06
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9634    77385073+  83  Linux
/dev/sda2            9635        9726      738990    5  Extended
/dev/sda5            9635        9726      738958+  82  Linux swap / Solaris
joseph@Josephs-Computer:~$ 




Also is there a way i can pop in my windows disc and set it to dual boot with xunbuntu or will i  have to reinstall windows and reinstall xunbuntu again afterwards??

---

### Post by Michael.Godawski on 2009-01-06
What version of Windows are you using?

i do not see nay windows partition so it is nuked.sry.

---

### Post by MaximoMilkman on 2009-01-06
Well i have a windows xp service pack 2 reinstallation disc that dell gave me like 4 years ago this pc is pretty old.. thats the reason why i wanted xunbuntu.. also does wubi support xunbuntu because unbuntu will probably be extremly laggt with my 256mb ram.

---

### Post by Michael.Godawski on 2009-01-06
Here is a guide for dual-booting 
windows xp and ubuntu, where ubuntu (read xubuntu) is installed first.


[LIST]
[*][http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)
[/LIST]
I guess you can use this guide also with a xubuntu disc.

As far as I know wubi is for Ubuntu only, but I can err.

---

### Post by sanderd17 on 2009-01-06
Hi, I have a perfect solution for everyone who wants to prevent whipping out their windows OS: 

you can install ubuntu (I don't know about Ubuntu variants like Xubuntu and Kubuntu) by running the [WUBI]("http://wubi-installer.org/") as a windows program, I am now using this and it works just great: no need to repartition your HDD and it works better than the ubuntu I had installed before (although not faster). 

for some extra information : see [wikipedia]("http://en.wikipedia.org/wiki/Wubi_(Ubuntu)").

this post is ment for people who want to begin with ubuntu.

---

### Post by ms2756 on 2009-01-06
You can get the operational system back, but my guess is you have WindowsXP 2003 - not a bad version, but you will have to install a lot of updates. It worked fine for me - reinstalled Windows myself recently.

So what you can do:
1. Pop in your Windows CD/DVD and at restart boot from that CD/DVD.
2. Install Windows (like 2 hours at least). Important: make sure you install the drivers properly.
3. Reboot.
4. Pop an Ubuntu Live CD/DVD into your drive.
5. Boot from the CD/DVD and install Ubuntu.
6. It will prompt you if you wish to partition the hard drive. That's a very important step - how much space would you allocate for Windows and Ubuntu? My suggestion is about 5G - 15G for Ubuntu, if you are using it just to work. Otherwise, make it equal between Windows and Ubuntu.
7. At bootup, you will have about 10sec to choose whether you want to boot Windows or Ubuntu.

Side note: your Windows information is lost forever.
Just a pointer: Always back up your hard drive. You have following options:
1. Flash - take it anywhere, safe, fast.
2. Portable hard drive - more space but not too portable.
3. DVD's - can't add stuff but can't erase stuff either, so it is very safe.

Regarding suggestion of getting WUBI. Why would you ever install Ubuntu on Windows? Only if you want to try it out, but then you can just boot from Ubuntu Live CD - all changes will be erased, so it's totally safe. We all move away from Windows 'cause it sucks - it freezes, it is slow, it has viruses. Regardless of how careful you are, sooner or later your Windows will die a natural death. If your old PC survives the virus onslaught for more than 6 months, I take my hat off to you. But maybe I just don't understand something :)

Toodles

---

### Post by MaximoMilkman on 2009-01-06
Thanks a bunch guys !! i love this community.. defintaley going to reinstall xunbuntu once i reinstall windows.. i will get use to linux with the help of this cool community here.. i really need to learn these weird commands im not use to having to do everthing with terminal its so weird...and difficult i wish i knew someone who knew linux in real life to teach me.. but i guess thats what forums are for.. WELL im off to reinstall windows and go to school!

---

### Post by ms2756 on 2009-01-06
Also thanks to sanderd17. Useful to know :)
I can't thank you for some reason - what's up with that?

---

### Post by Sef on 2009-01-06
> once i reinstall windows

Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  It can restore deleted partitions.

For a pictoral howto of dual booting, read [Psychocats]("http://psychocats.net/ubuntu").

---

### Post by rjmoerland on 2009-01-06
> **sanderd17 said:**
> you can install ubuntu (I don't know about Ubuntu variants like Xubuntu and Kubuntu) by running the [WUBI]("http://wubi-installer.org/") as a windows program

Yep, WUBI does xubuntu, kubuntu and mythbuntu as well :) I've used it to install Xubuntu on a windows machine, and after I had verified everyting was running OK I (intentionally) wiped Windows afterwards.

8)

---

