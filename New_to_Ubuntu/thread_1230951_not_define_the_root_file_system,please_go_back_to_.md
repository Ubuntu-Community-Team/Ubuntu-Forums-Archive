---
title: "not define the root file system,please go back to partition menu to solve the problem"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by MacHsu on 2009-08-04
[FONT=Arial Narrow][SIZE=4][COLOR=red]not [/COLOR][COLOR=red]define the root file system,please go back to partition menu to solve the problem[/COLOR][/SIZE][/FONT]


[FONT=Arial Narrow][SIZE=4]when i use wubi.exe to install Ubantu after i reboot the computer and choose Ubantu to start my computer,the Ubantu began to finishing the installation and after a while there poped up a new window with the warning[/SIZE][/FONT]
[FONT=Arial Narrow][SIZE=4]"[/SIZE][/FONT][FONT=Arial Narrow][SIZE=4]not define the root file system,please go back to partition menu to solve the problem[/SIZE][/FONT][FONT=Arial Narrow][SIZE=4]"[/SIZE][/FONT]


[SIZE=4]Anybody know how to solve the problem?I'm anxiously waiting for ur solution!!![/SIZE]

---

### Post by TeoBigusGeekus on 2009-08-04
Never done a wubi installation, but when you install Ubuntu you are supposed to give a root partition, i.e. the point from where all the linux filesystem tree will start. The root partition is designated with /.

---

### Post by MacHsu on 2009-08-04
[IMG]http://image.rayli.com.cn/0020/2007-04-02/images/200742104319764.jpg[/IMG]not solving my problem,dude!

---

### Post by THGIC on 2011-03-02
When I did this whole partitioning part for installing Ubuntu, I set up my main (primary) partition for all of my data, then I gave a little bit of space as what is called a "swap area". This "swap area" is recommended, because when physical hard drive space becomes very limited, it acts as a backup drive in a way. Finally, I left about 5-10GB of space for my OS. For my primary partition, I used the ext4 filesystem with "/home" as my mounting point. Then for my "swap area" partition, I could not choose a filesystem or mounting point. My OS partition, I used the same ext4 filesystem, only this time, I used "/" as my mounting point. Using just "/" (the quotations are never part of what you are supposed to type, just fyi) means that you now have "defined" or created a "root" filesystem. From there, you should be able to follow the rest of the installation. 

Enjoy!

---

