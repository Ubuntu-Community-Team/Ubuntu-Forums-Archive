---
title: "Dual boot install questions"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by pelee98 on 2010-01-15
Hi everyone.  I'm looking for advice.

At home we currently have two machines.  One runs Ubuntu 9.10.  The other runs Windows XP home.  Both are stand alone machines.

The Ubuntu machine is the source of marital strife as it's always freezing.  I won't get into reasons why as it's an old machine and it's probably on it's way to being a boat anchor soon.

Anyway, we are thinking of a new laptop.  It will run windows 7 because it's so readily available and to appease aforementioned marital strife ;o).  I also need to run Autocad (windows only folks).  However, that leaves our current dell laptop open to my experiments.  It's a dell inspiron e1705.  The link below shows the specs.  My machine has the most basic specs (no upgrades).

[http://www.dell.com/us/en/dfh/notebooks/inspn_e1705/pd.aspx?refid=inspn_e1705&cs=22&s=dfh](http://www.dell.com/us/en/dfh/notebooks/inspn_e1705/pd.aspx?refid=inspn_e1705&cs=22&s=dfh)

I'm thinking I'd like to set it up as a dual boot machine.  But I've never done this.  I have never even partitioned a drive.  I will list my thought below and I'd like your comments.  My apologies if they are stupid questions.

1.  I understand it's easier to install the windows first followed by Ubuntu.  Is that correct?

2.  I believe the Dell can run 64 bit Ubuntu.  I'm too much of a newbie to know.  Can anyone confirm?  It has a core 2 duo processor.

3.  Does Ubuntu 64 run flash any better than 32 bit Ubuntu?  It sounds like there is potential there. I am convinced that flash causes my frequent freeze-ups and I still need flash player.  Anyone with experience on both?

4.  Can I dual boot with a 32 bit version of windows and a 64 bit Ubuntu?

5.  Can two different operating systems share non-program fires (i.e. music files, family pictures, etc) or does the partition get in the way.  It would be horribly wasteful to have to put that stuff on the disk twice.

6.  When I power up, which OS comes up first?  Is there some kind of selection screen that pops up or something?  Do I have to hit some F-whatever key during boot-up?

7.  Lastly, can anyone point me to a tutorial on dual boot installation?

Thanks for your thoughts.

---

### Post by wirate on 2010-01-15
1. Yes
2. Yes
3. Dont know
4. Yes
5. Ubuntu can read files in your Windows partition but Windows cant read those of Ubuntu
6. You will be given choice on boot without pressing any keys. After a certain timeout the default OS will be chosen. You can change the default OS
7. I cant :)

---

### Post by northern lights on 2010-01-15
> **pelee98 said:**
> 1.  I understand it's easier to install the windows first followed by Ubuntu.  Is that correct?
Correct. Will save you the hassle of setting up the bootloader manually.

> **pelee98 said:**
> 2.  I believe the Dell can run 64 bit Ubuntu.  I'm too much of a newbie to know.  Can anyone confirm?  It has a core 2 duo processor.Yes it can.

> **pelee98 said:**
> 3.  Does Ubuntu 64 run flash any better than 32 bit Ubuntu?Potentially you're right. But on your hardware a 32bit will handle flash as smoothly.

> **pelee98 said:**
> 4.  Can I dual boot with a 32 bit version of windows and a 64 bit Ubuntu?Yes.

> **pelee98 said:**
> 5.  Can two different operating systems share non-program fires (i.e. music files, family pictures, etc) or does the partition get in the way.This is dependent on the filesystem. Ubuntu reads from and writes to ntfs and fat, whereas Windows does not read ext2,3,4 natively.

> **pelee98 said:**
> 6.  When I power up, which OS comes up first?  Is there some kind of selection screen that pops up or something?  Do I have to hit some F-whatever key during boot-up?You can define the order and/or the default boot option of the bootloader's menu.

> **pelee98 said:**
> 7.  Lastly, can anyone point me to a tutorial on dual boot installation?[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by Sidewinder1 on 2010-01-15
> **pelee98 said:**
> Hi everyone.  I'm looking for advice.

At home we currently have two machines.  One runs Ubuntu 9.10.  The other runs Windows XP home.  Both are stand alone machines.

The Ubuntu machine is the source of marital strife as it's always freezing.  I won't get into reasons why as it's an old machine and it's probably on it's way to being a boat anchor soon.

Anyway, we are thinking of a new laptop.  It will run windows 7 because it's so readily available and to appease aforementioned marital strife ;o).  I also need to run Autocad (windows only folks).  However, that leaves our current dell laptop open to my experiments.  It's a dell inspiron e1705.  The link below shows the specs.  My machine has the most basic specs (no upgrades).

[http://www.dell.com/us/en/dfh/notebooks/inspn_e1705/pd.aspx?refid=inspn_e1705&cs=22&s=dfh](http://www.dell.com/us/en/dfh/notebooks/inspn_e1705/pd.aspx?refid=inspn_e1705&cs=22&s=dfh)

I'm thinking I'd like to set it up as a dual boot machine.  But I've never done this.  I have never even partitioned a drive.  I will list my thought below and I'd like your comments.  My apologies if they are stupid questions.

Questions are rarely 'stupid'; sorry I can't answer all of your intelligent questions but I'll share what I know. :-)

1.  I understand it's easier to install the windows first followed by Ubuntu.  Is that correct?

Yes, you're correct, win first because windows is totally intolerant of other OSs and will destroy GRUB.

2.  I believe the Dell can run 64 bit Ubuntu.  I'm too much of a newbie to know.  Can anyone confirm?  It has a core 2 duo processor.

3.  Does Ubuntu 64 run flash any better than 32 bit Ubuntu?  It sounds like there is potential there. I am convinced that flash causes my frequent freeze-ups and I still need flash player.  Anyone with experience on both?

4.  Can I dual boot with a 32 bit version of windows and a 64 bit Ubuntu?

5.  Can two different operating systems share non-program fires (i.e. music files, family pictures, etc) or does the partition get in the way.  It would be horribly wasteful to have to put that stuff on the disk twice.

Absolutely, ubuntu will be able to see, manipulate, copy, play anything in either partition; not so with windows unless you install specific drivers in that OS.

6.  When I power up, which OS comes up first?  Is there some kind of selection screen that pops up or something?  Do I have to hit some F-whatever key during boot-up?

Yes, you'll be presented with a screen that will allow you to highlite whatever OS in which you would like to boot.

7.  Lastly, can anyone point me to a tutorial on dual boot installation?

I have found the below link to be invaluable:
[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu)

Thanks for your thoughts.
Enjoy!

HTH, 
Side

---

### Post by oldfred on 2010-01-15
Some info on dual booting the version of windows only makes minor difference. XP can use gparted to repartition, Vista & 7 should use their internal tools to resize their partition.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by pelee98 on 2010-01-26
Thanks for all the help guys.

---

