---
title: "My First Taste of Ubuntu"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by Zach D on 2011-08-08
Hi all, I had spent enough time reading about wubi to make sure it was safe so I decided to go for it. It took me a while and I had to go through the APCI workarounds to get it installed, but I'm liking it so far. One thing that I'm feeling weird about is that I get this feeling that using wubi isn't a 'true' dual-boot. I mean, I'm not even sure if I can create and save documents with LibreOffice, or if I can download other applications onto my Ubuntu . . . can anyone clear that up for me?

One of the main reasons I am trying out Ubuntu is that I've been told by several Computer Science guys that anyone who has a desire to be a 'real' Computer Science guy should be pretty familiar with Linux. Along this vein is the idea that I'd like to get much more comfortable with the terminal, does anyone know of some links that will show me how to use the terminal in my day-to-day activities? Thank you all in advance!

---

### Post by whatthefunk on 2011-08-08
I cant answer your questions about Wubi, but I can point you to some links.

You should learn basic bash commands:
A tutorial:
[http://www.arachnoid.com/linux/shell_programming.html](http://www.arachnoid.com/linux/shell_programming.html)

A command dictionary:
[http://ss64.com/bash/](http://ss64.com/bash/)

There are several other good bash command indexes out there.

You should learn about the file structure:
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

---

### Post by imortalninja161 on 2011-08-08
> **Zach D said:**
> Hi all, I had spent enough time reading about wubi to make sure it was safe so I decided to go for it. It took me a while and I had to go through the APCI workarounds to get it installed, but I'm liking it so far. One thing that I'm feeling weird about is that I get this feeling that using wubi isn't a 'true' dual-boot. I mean, I'm not even sure if I can create and save documents with LibreOffice, or if I can download other applications onto my Ubuntu . . . can anyone clear that up for me?

One of the main reasons I am trying out Ubuntu is that I've been told by several Computer Science guys that anyone who has a desire to be a 'real' Computer Science guy should be pretty familiar with Linux. Along this vein is the idea that I'd like to get much more comfortable with the terminal, does anyone know of some links that will show me how to use the terminal in my day-to-day activities? Thank you all in advance!

Hay man im not to sure what wubi is lol :/ but i know ya can save libreoffice files and you can download other applications on ubuntu.

As for learning about terminal man your best bet is to have a little look in some of the sticked post in the beginners threads there are also some good sites that give you a list of commands and there syntax. im not sure about computer science but i am in my second year of networking and i have just started my linux course. And linux is very very important for the top 10 super computers run Linux man
Also including Google and face book server. what i have learnt is linux distros make ok desktops but they make frikin Awesome industrial grade stuff.

---

### Post by realzippy on 2011-08-08
Wubi is as real as real ubuntu.Of course you can save files aso....
The performance is different.For some tasks it is a bit slower,for
others it is even faster.
Problem is,if Windows gets corrupted,wubi is also dead  ...

---

### Post by jmszr on 2011-08-08
Zach D,

Welcome aboard!

Here are some Terminal resources: 

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338)  (Newbie Terminal Intro)/
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)   (Terminal for Beginners) 

[http://www.linuxcommand.org/](http://www.linuxcommand.org/) (Terminal Commands)

Edit: This comes in handy: [http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/).

Edit2: Almost forgot about this one - quite useful HowTo: [http://ubuntuforums.org/showthread.php?t=842307](http://ubuntuforums.org/showthread.php?t=842307)

---

### Post by Paqman on 2011-08-08
> **Zach D said:**
> One thing that I'm feeling weird about is that I get this feeling that using wubi isn't a 'true' dual-boot. I mean, I'm not even sure if I can create and save documents with LibreOffice, or if I can download other applications onto my Ubuntu . . . can anyone clear that up for me?


The only difference is that instead of installing into a seperate partition on the drive it creates a virtual partition on the Windows partition, and installs into that. It works exactly the same as a normal dual boot except:
[LIST=1]
[*]You cannot use hibernation, RAID or disk encryption.
[*]Disk access is very, very slightly slower. You probably wouldn't even notice this.
[*]It really, really doesn't like interruptions to the power supply. Don't use it on a desktop if your area is prone to power cuts. Laptops are fine, since they have batteries.
[/LIST]

---

### Post by Frogs Hair on 2011-08-08
Wubi  was my introduction  to Ubuntu / Linux and for me  It  served its purpose  as trial application . I know people using it on Win 7 without any problem .  Here are some links I have found useful .

(Command Line)

[http://linuxcommand.org/](http://linuxcommand.org/)

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)

---

### Post by Rex Bouwense on 2011-08-08
A WUBI install is not intended for long term use.  If after installing, you decide that you like the OS you should delete the WUBI install (after saving important documents) and install along side of your Windows (or if you are really brave instead of your Windows).  Enjoy.

---

### Post by amjjawad on 2011-08-08
> **Zach D said:**
> One thing that I'm feeling weird about is that I get this feeling that using wubi isn't a 'true' dual-boot. 


Your feeling is undoubtedly right. It's NOT a "real" Dual-Booting System.
Wubi installation is just a file inside your Windows Installation, not even a partition. 

> I mean, I'm not even sure if I can create and save documents with LibreOffice, or if I can download other applications onto my Ubuntu . . . can anyone clear that up for me?

Sorry, can't help here. I have never used Wubi and don't recommend to use it but that's my personal opinion and I know many will disagree with me.

I prefer another approach, **either **to install Ubuntu on USB Drive or External HDD **or** just go a head with a real installation and learn from my mistakes, etc. That's how I would do it :)


> One of the main reasons I am trying out Ubuntu is that I've been told by several Computer Science guys that anyone who has a desire to be a 'real' Computer Science guy should be pretty familiar with Linux. 

Then you need to do it Linux Way NOT Windows Way ;)

Wubi is:

> Wubi is an officially supported installer for [COLOR=Red]**Windows **[/COLOR]users that allows  Ubuntu to be installed and uninstalled in a safe, easy way as with any  other **[COLOR=Red]Windows [/COLOR]**application.   


Linux? I can't see "Linux" in that :)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29)

> does anyone know of some links that will show me how to use the terminal in my day-to-day activities? Thank you all in advance!
Everything related to "Terminal", I have learned it and still learning it from here (Forum) or when I do some searches on Google or [www.googlubuntu.com](www.googlubuntu.com)

---

### Post by The Cog on 2011-08-08
I suppose it's a matter of opinion to an extent. In my opinion, wubi **is** real dual-booting. hen you boot Ubuntu in wubi, windows is not running (some people think wubi is ubuntu running as a windows app). My understanding is that wubi does two things diferent to a standard Linux install:

1: Instead of formatting a disk partition to install linux in, it creates a virtual disk inside a large file in the windows partition. This means you avoid the pitfalls of disk partitioning, but it means you are dependent on the existence of the windows filesystem and there is a small (probably insignificant) performance hit. 

2: Instead of installing its own bootloaded that asks whether you want to boot linux or windows, it configures the existing windows bootloaded to ask the question.

I think wubi is good for evaluating linux, but I wouldn't want to use it that way all the time - the continued dependence on windows existence would bother me. Bear in mind that with wubi, all your linux files are inside that virtual disk, and may not be easy to get at if your wubi won't boot for some reason. With a proper install, the files are all there on disk and can be seen/rescued from a live CD if your OS gets mangled and won't boot (yes that can happen to linux as well as to windows).

I would also add that linux is not all about the command line. Some tasks are vastly better suited to doing in the command line and I think windows is deficient in not having a useable one, but that's not all there is to linux. I spend 90-95 percent of my time in a GUI, and only change to the command line when I think that will be faster than the GUI to do what I want.

---

