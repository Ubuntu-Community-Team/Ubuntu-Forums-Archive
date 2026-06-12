---
title: "Wubi vs. Normal install"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by rideburton56 on 2009-07-10
Hi All,

I am planning on turning the main computer in our house to a dual boot box.  I was thinking of maybe Xubuntu because its an older system (but not too bad, enough to run ubuntu) and also for fun.  In my research today I stumbled across wubi.  Although it seems like its not avaialable for xubuntu, it intrigued me.

What does it do?  does it actually set up the OS on a new partition or does it just run it as a VM?  As a user with ubuntu on my laptop for over a year now (and only ubuntu) will i be making tradeoffs with wubi?

Thanks in advance!

---

### Post by LewRockwell on 2009-07-10
my vote is against wubi

.

---

### Post by Cheesemill on 2009-07-10
Wubi runs just like a normal install except it uses a special file on your Windows drive as its filesystem, thus no need to mess about with partitioning.

The downside is that you are reliant on the Windows NTFS partition, if it becomes corrupt you lose your Wubi install as well.

---

### Post by issih on 2009-07-10
My understanding is that wubi works by allocating a large file inside windows own filesystem, which it basically assigns as space for linux. It creates something called a loop filesystem within that file, and then creates  partitions within it and installs ubuntu into them. The whole linux filesystem is wrapped up and virtualised inside a file within windows file system, there are no actual partitions on the hard drive, but the loop filesystem behaves as if there are.

You boot ubuntu by selecting it when you boot the computer (the install modifies the windows boot loader) you are then running linux directly on the hardware aceessing the loop filesystem as if it was a real partition on the hard drive. It is not running in a VM, windows is not running, it is very similar to a normal dual boot install.

The main advantage of wubi is that you don't need to do any partitioning of your hard drive, and it is possible to uninstall ubuntu merely by going to windows add/remove utility and removing it like any other program.

The principal disadvantage is that you can't suspend the pc if you are using wubi (or at least it used to be, I've not checked in a while), I'd be surprised if the performance wasn't slightly affected by the added complexity too, but I have nothing to back that up, its just a hunch.

Wubi is be a fine way to try things out and see how you get on, you can always uninstall it and do a full dual boot install later on.

Hope that helps

---

### Post by rideburton56 on 2009-07-10
Being that ive experienced ubuntu alreadty and am comfortable with the normal partitioned approach, i think i will go that way.  as always you guys are so helpful, thanks!

PS i havent been on in a while, is there no more thanking??

---

### Post by issih on 2009-07-10
Thanking went the way of the dodo...apparently it was doing nasty things to the servers.

---

### Post by superprash2003 on 2009-07-10
if you have a choice then normal install any day!!

---

### Post by clonne4crw on 2009-07-10
I would recommend NOT using Wubi, and instead do a normal install. While Wubi seems like a better idea, trust me, it has hosed more Ubuntu + Windows installations for me than you could ever guess. 

Maybe if/when Wubi can install to a seperate partition I'd try it again.

---

### Post by kansasnoob on 2009-07-10
IMHO the worst thing about Wubi is:

> Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.

So one power outage can result in the need to reinstall!

From "Any gotcha?" here:

[http://www.wubi-installer.org/faq.php](http://www.wubi-installer.org/faq.php)

---

### Post by LowSky on 2009-07-10
wubi isn't worth it... normal partition install is the way to go.

---

### Post by QIII on 2009-07-10
Wubi sounds like "woobie" and you don't need a binkie or a blankie if you really want to use Ubuntu.  

Wubi Ubuntu has to fight its way out of the Windows prison to get to anything useful...

---

### Post by Paddy Landau on 2009-07-10
As someone who started out with Wubi, let me give you my experience.

I used Wubi to experiment and get the feel of Ubuntu. Once I had a good feel for Ubuntu, I uninstalled Wubi and did a full native installation.

Wubi does have its limitations (it can't hibernate), but nothing serious.

[LIST]
[*]Wubi is slower than a native install, but still faster than Windows.
[*]Wubi is a fantastic way for a Windows user to experiment. The newbie doesn't have to worry about partitions and the installation.
[/LIST]
If you want to experiment, go for Wubi.

If you want to use Ubuntu properly, go for the native installation.

---

