---
title: "just installed Ubuntu"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by Gary00 on 2010-04-17
took about 4 hours or so to install, i am also running windows 7. here is the problem, at start up where i can choose windows 7 or Ubuntu, when i choose Ubuntu it doesn't quite come up, some code comes up. what do i do? Thanks

---

### Post by undecim on 2010-04-17
What error do you get?

Did you install Ubuntu with Wubi or by booting the CD?

Wubi is prone to startup problems like this.

---

### Post by steveneddy on 2010-04-17
Partition the drive and give Ubuntu it's own partition or use a virtual machine like VirtualBox.

Wubi is just asking for trouble.

---

### Post by Gary00 on 2010-04-17
i made a cd with the new ubuntu on it. installed it, worked fine, set up worked fine. Now when i boot it with the cd it saids error, then when i try to boot it without cd it saids 

[CENTER]GNU GRUB Version 1.97~beta4

[LEFT][ Minimal BASH-like line editing is supported. For the  first word, TAB lists possible command completions. Anywhere else TAB  lists possible device/file completions. ]

sh:grub>
[/LEFT]
[/CENTER]

---

### Post by Gary00 on 2010-04-17
also, i installed Ubuntu while i was in window 7 OS, then just reboot, dont know if that matters. but i would assume because i did that, Ubuntu should have its own partition

---

### Post by ajgreeny on 2010-04-17
No, I'm afraid not.  You used the wubi installation system if you did it from within windows; OK as a testbed of the OS, but not really meant as a long-term use system.

Boot to windows and uninstall the wubi install, then having made sure that the CD-ROM is first boot device in your BIOS, reboot the computer with the Live CD in the drive.  It should boot to the gnome desktop and show you a button to double click to install the system.  Use that and follow the prompts for a full partitioned install.

See [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) for a lot more detail.

---

### Post by Gary00 on 2010-04-17
hmm, i just removed Ubuntu, rebooted, Ubuntu pops up once i start my laptop, but then when i go to install it, it saids error with disk, lol getting on my nerves now...

---

### Post by ajgreeny on 2010-04-17
What errors with disk?  More info needed to help, so tell us in more detail.

---

### Post by IndyGunFreak on 2010-04-17
> **Gary00 said:**
> hmm, i just removed Ubuntu, rebooted, Ubuntu pops up once i start my laptop, but then when i go to install it, it saids error with disk, lol getting on my nerves now...

I'd say there's your problem... Try burning the CD again, burn it SLOW, and let it do its thing...

Also, does anyone else think its time that Wubi become a separate download, as opposed to being part of a Live CD download?  I've addressed this problem before w/ lots of new users.  They think they are actually installing, turns out, they are using Wubi because after they burned the CD, it had an "install now" button.

They have Live CD, Alternate CD, why not have a Wubi ISO?

---

### Post by undecim on 2010-04-17
> **IndyGUnFreak said:**
> I'd say there's your problem... Try burning the CD again, burn it SLOW, and let it do its thing...

Also, does anyone else think its time that Wubi become a separate download, as opposed to being part of a Live CD download?  I've addressed this problem before w/ lots of new users.  They think they are actually installing, turns out, they are using Wubi because after they burned the CD, it had an "install now" button.

They have Live CD, Alternate CD, why not have a Wubi ISO?

I agree. Wubi is just confusing when new users install it and then come to ask for support.

---

### Post by grifonas on 2010-04-17
> **IndyGUnFreak said:**
> 
Also, does anyone else think its time that Wubi become a separate download, as opposed to being part of a Live CD download? 
They have Live CD, Alternate CD, why not have a Wubi ISO?
  
Excellent idea! It should definitely be done as a separate download.

---

### Post by Gary00 on 2010-04-17
ok ok so i got ubuntu running, and its awesome, love it....i ah kinda made it my main OS, meaning Ubuntu is the only OS on my laptop, ok, heres the only problem i have atm, i have no internet, my gear is an HP Entertainment laptop 1117nr, came with windows Vista. Also, with windows downloading and installing games are a breeze, am i going to enjoy that luxury with ubuntu? And Thank You for the idea of reburning the CD then doing it again, worked awesome! Thanks

---

### Post by Georgia boy on 2010-04-18
There a quite a few games that are in the repros ie: Open Arena, Alien Arena and much more. However from what I read in the games forums a lot of people use Wine to play some of their games. Here is the link for the game forum: [http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)
You might go there to read what others are playing and to also ask questions as they arise for you on games.
Glad you got your Ubuntu up and running.Welcome. Enjoy!! This is a great forum for helping when a person runs into a brick wall.

Tom

---

### Post by Gary00 on 2010-04-18
there are quite a few things i dont understand just yet, like the Terminal....what exactly and how exactly do i use the terminal? like now im having a wireless problem, is the terminal going to help me at all?

---

### Post by Paqman on 2010-04-18
> **IndyGUnFreak said:**
> 
They have Live CD, Alternate CD, why not have a Wubi ISO?

What for? It fits on the regular LiveCD. It's only about 4MB.

You can actually install Wubi  by downloading the wubi.exe from the website, it'll pull down an Ubuntu image and do the whole install diskless.

Wubi rocks IMO. Half the problem noobs have with it on this forum is that people don't know how to give good support for it.

---

### Post by ajgreeny on 2010-04-18
> **Paqman said:**
> What for? It fits on the regular LiveCD. It's only about 4MB.

You can actually install Wubi  by downloading the wubi.exe from the website, it'll pull down an Ubuntu image and do the whole install diskless.

[COLOR=Red]Wubi rocks IMO. Half the problem noobs have with it on this forum is that people don't know how to give good support for it.[/COLOR]
Mainly because at least half the time we don't even know we are dealing with a wubi install, so a lot of the information we need is not given and we give entirely the wrong answers back to the OP.

I agree; keep wubi as a separate system entirely and it will lead to a lot less confusion.

---

### Post by Paqman on 2010-04-18
> **ajgreeny said:**
> Mainly because at least half the time we don't even know we are dealing with a wubi install, so a lot of the information we need is not given and we give entirely the wrong answers back to the OP.


True, but getting a poorly-defined problem in the OP is pretty much the lay of the land in Absolute Beginners. Good support is about asking the right questions as much as giving the right answers.

---

### Post by undecim on 2010-04-18
> **Gary00 said:**
> there are quite a few things i dont understand just yet, like the Terminal....what exactly and how exactly do i use the terminal? like now im having a wireless problem, is the terminal going to help me at all?

the terminal is an amazingly powerful tool. But like most powerful tools, it takes some learning to use it effectively. With the terminal you can run commands and write scripts to automate mundane processes or control your computer with precision. When you get support from the forums, other will ask you to run commands in the terminal.

As for your wireless problem, the easiest way to fix it is usually to connect directly to your router via an ethernet cable and check for your wireless drivers in System -> Administration -> Hardware Drivers. Enable the driver, reboot, and you should have wireless.

If that's not an option, I need info on your wireless card. Open a terminal and paste one of these commands and press enter: 

for an internal wireless card:
```
lspci
```

for a USB wireless card:
```
lsusb
```

In the output of one of those two commands will be a line that describes your wireless card. Paste that line here. If you don't know which line it is, just post them all.

---

### Post by Gary00 on 2010-04-18
Ubuntu is working great! and i just got the internet working yesterday, and its awesome, Thanks a lot for the tech support.  There are a few more things i would like to do, like update my java, video, sound, firewall, but it seems to be an easy thing so no worries...

---

### Post by Paqman on 2010-04-19
> **Gary00 said:**
> Ubuntu is working great! and i just got the internet working yesterday, and its awesome, Thanks a lot for the tech support.  There are a few more things i would like to do, like update my java, video, sound, firewall, but it seems to be an easy thing so no worries...

Easiest way to sort Java, codecs, Flash, etc is to install the restricted extras package. Pick either:

[ubuntu-restricted-extras](apt:ubuntu-restricted-extras)
[kubuntu-restricted-extras](apt:kubuntu-restricted-extras)
[xubuntu-restricted-extras](apt:xubuntu-restricted-extras)

...depending which version you've got installed. You don't need to worry too much about your firewall unless you've got some kind of server software installed. The default setup is secure for desktop apps.

---

