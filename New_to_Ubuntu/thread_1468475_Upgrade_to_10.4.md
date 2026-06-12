---
title: "Upgrade to 10.4"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by huzefa_from_kuwait on 2010-05-01
Hello people,

I have 9.10 on my laptop installed, however since last two three months the gdm service simply wont start. During boot up it would try to start but as it couldn't it goes into loop of starting and stopping and keeps retrying.

Despite of a lot of troubleshooting I couldn't get it running however I can use my laptop in recovery mode. Now I suppose with the new version once I upgrade my problems might be solved. 

I have both the new CD as well as the alternate installation CD, is there a way to do distribution upgrade from the recovery mode using any of these CD's.

Thanks.

---

### Post by arnab_das on 2010-05-01
you might want to reinstall once uve tried all options.

---

### Post by huzefa_from_kuwait on 2010-05-02
I need that 9.10 , it has a long history from being updated from 8.04 and has a lot of my settings !

I dont want to lose them :(

I want to know if there is an alternate way to get in xterm and just run update like by VNC or something.

---

### Post by FoxMcCloudwp on 2010-05-02
> **huzefa_from_kuwait said:**
> I need that 9.10 , it has a long history from being updated from 8.04 and has a lot of my settings !

I dont want to lose them :(

I want to know if there is an alternate way to get in xterm and just run update like by VNC or something.

You might need to back those settings and files up, and reinstall Ubuntu.

---

### Post by WinterRain on 2010-05-02
Just do Ctrl-H in your home folder to show your hidden config files and save the ones you want. After reinstall, plug them back in, and you will have all your settings back.

---

### Post by nhasian on 2010-05-02
yeah a fresh install would give you grub2 and the ext4 filesystem.  also it will allow you to put your /home into a separate partition if you havent already done so.

you can backup your /home directory, wipe the drive and create new ext4 partitions.  Then copy your /home directory back and do a fresh install on top of it.  be sure not to format the partition your /home is during install.  that should keep most of your settings like desktop background, firefox bookmarks, passwords, etc.

---

### Post by Absolut Newbee on 2010-05-02
hej
not that I disagree with the rest in the thread, but how have you tried to update/upgrade your system?

can you get online in recovery mode?, 
to get wireless on try typing:

   sudo ifconfig wlan0 up

if this works try:

  sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

if you can't online have you mounted the cd drive?
if so try adding the cd to the source list for updates

   sudo apt-cdrom add

hope you can use this

---

### Post by huzefa_from_kuwait on 2010-05-02
Yeah, thanks for the reply guys, i will reinstall and restore the files, however if i could just upgrade the system i can get my xterm fixed.

The problem is i have banged my head quite much in getting sound work , specially in skype, I dont want to lose it ;)

Also i have apache (php), bind9 and mysql ( i take the hell out of my pentium M processor ;) )

I have tried apt-get update, upgrade, dist-upgrade ( in recovery mode ) but it outputted no results.

If i can get xterm to work anyhow (not gdm) i can run cdromupgrade from the alternate cd.

I have tried VNC but haven't succeded yet.

I have thought of barring gdm from starting itself at run-level 3 ( I have been trying since three months but havent succeded in this too .. LOL ), Once I am in , I can start VNC, and run upgrade (this is what i think should work).

I have tried to forward the display by SSH but that also won't work :(

I will try all I can before I finally dump the whole file-system and do a fresh installation ;)

If you have any ideas do let me know,

Thanks Again.

---

### Post by Absolut Newbee on 2010-05-02
stuppied question, but have you tried

the comand:

dpkg --configure -a

or maybee see this:

[http://ubuntuforums.org/showthread.php?t=709578&page=2](http://ubuntuforums.org/showthread.php?t=709578&page=2)

or 

[http://www.dharwadkar.com/weblog/ubuntu06](http://www.dharwadkar.com/weblog/ubuntu06)

---

