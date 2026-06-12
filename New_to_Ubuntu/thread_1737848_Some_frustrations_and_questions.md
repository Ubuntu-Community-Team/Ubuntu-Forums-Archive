---
title: "Some frustrations and questions"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by IHeequ5i on 2011-04-23
I'm running into some issues with Maverick that I don't REMEMBER hitting with Jaunty or Lucid. I'm also not sure exactly where this post belongs, because some of it has to do with wine.

1: Recently I tried switching to kubuntu because I'd read several things that sounded intriguing. I got KDE installed after a couple of false starts and then ran smack into having to reinstall my video-card drivers. Got that done, and then found that none of the applications I'd installed through wine would run. "Not worth it," says I, and back I go to Ubuntu and gnome. I had to reinstall the video drivers again, but at least my wine apps worked once that was done. So - why does switching desktops break my video, and why won't my wine apps run under kubuntu?

2: Related to item #1 - is there an easy way to clean out all the gump that kubuntu insisted on installing? I wound up going through everything I had installed and removing packages I didn't want manually. Painful and slow, and there should be a better way.

3: When I'm installing games in wine, I'm running into an issue lately where the windows part of the install wizard is "masked" by the wine terminal window. I launch the setup.exe from terminal using "wine path/to/setup.exe and the installer starts. It puts up a screen where I have to input the serial # off the CD case and here's where I get in trouble. The actual window for the installer never comes "active"; I can't type in it. I can't alt-tab and get to it either. It's like it's a sub-window of the terminal session, if that makes any sense. If I launch the setup.exe by doing a right-click and open with wine, I get into a similar mess. The installer window comes up, I click on it, and it vanishes leaving me with no way to recover.

4: Is there any Lightscribe software available for Linux?

5: I have two physical hard-drives in my desktop. The 500 GB is Windows 7 and the 320 GB is Ubuntu. The Ubuntu drive is set as the default boot device in BIOS, and Grub sees the drive with Windows on it, so I can dual-boot painlessly. Anyways... I'm considering getting rid of Windows completely and using VirtualBox for those few applications that I can't get to run under wine... so I've some more questions:
    a -  Can I move my /home folder to the 500 GB drive? Should I? If so, how do I do it? Is there any advantage to so doing? Any gotchas to avoid?
    b -  Would it be better to completely reinstall Ubuntu? If so, what would be the best way to organize my partitions?
    c - For purposes of backing up my data, does Ubuntu store program settings anywhere other than in the /home folder?

And one final small request.  If y'all ask me to run commands from terminal, please provide a brief explanation of what they do. I'd prefer to learn more about what I'm doing rather than blindly follow instructions.

---

### Post by frup on 2011-04-24
If you're going to move the 500gb folder to the home folder, remember to back up everything in your current home folder to it first, that includes the hidden directories beginning with a .

A few years ago I basically did what you're about to do but forgot to do that, the system didn't like it but luckily I hadn't updated fstab and it reset at reboot.

I don't know what you're planning to do, but I'd probably mount the 500gb drive as /home/user/data/ or something. The reason being is that I just wouldn't end up using any of the 320gb drive unless I partitioned that and mounted it somewhere inside the home dir instead.

With your kubuntu problems, I don't know what is wrong with the drivers, I would have removed the meta package (and installed that way) kubuntu-desktop. When you remove that through purge it takes away everything kubuntu related, though in the past I remember once being left with kdm which I didn't appreciate. 

Can't help you with the wine stuff, I don't really use it.

---

### Post by Paddy Landau on 2011-04-24
Quite a number of questions. It might be easier in future to create different threads.

**Q.1**

I don't know. Something must have gone wrong. I've never used Kubuntu, so sorry, I can't help.

**Q.2**

Run the following two commands in a terminal to clean out old installation packages.
```
sudo apt-get autoremove
sudo apt-get clean
```The first command automatically removes any packages that are no longer needed; i.e. packages that were installed to satisfy dependencies, but those dependencies no longer exist (because you uninstalled something).

The second command removes archives that were downloaded in order to install. They are no longer needed.

To find out more about a command in terminal, use the *man* command. In this case:
```
man apt-get
```Note that 'sudo' allows you to run the system as *root* (an *administrator* in Windows terminology). Again, you can find out more about it:
```
man sudo
```**Q.3**

I have never used Wine directly; I find it too complicated. Instead, I use [PlayOnLinux]("http://playonlinux.com/"), which is a front-end for Wine. Try it; it may help. (Install from the repositories.)

**Q.4**

Yes, there is. Free software is available from the official website (I've used it, so I know it works). You can also get paid-for software, but use the free software first to ensure that it works.

**Q.5**

**a)**

Where you put your home directory is entirely your personal preference. Ubuntu needs no more than 20Gb (20Gb is more than enough space). So, my suggestion is as follows, but of course you may disagree:

[LIST]
[*]Create a partition of 20Gb on your 500Gb drive, and install Ubuntu there (that's your root (/) directory).
[*]Create a partition equal to your RAM size on the same 500Gb drive, and format that as swap.
[*]Create a partition filling the entirety of your 320Gb drive, and format  that as /home.
[*]Create a partition filling the remainder of your 500Gb drive, and format that as, say, /data, where you keep large files that don't often change.
[/LIST]
That way, you have two separate drives for normal access, reducing access time. (Unless... you really have a single drive that is split into two partitions, 500Gb and 320Gb.)

However...

Why don't you keep Windows? With such a large amount of space, you can reduce Windows to (say) 100Gb for the few times you need to dual-boot. Trying to install Windows in a virtual box may be problematic if your license is for the OEM.

**b)**

A clean installation is always good. Just be sure you've made full backups first.

**c)**

Under normal circumstances, Ubuntu cannot change anything outside your home directory. Therefore, all settings are within /home.

The only exception is system changes, e.g. when you run update manager (and then you have to type your password, which is a clue that something is happening outside your home directory).

---

### Post by Paddy Landau on 2011-04-26
Regarding Q5 a): I have just come across [Logical Volume Management]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29") (LVM).

With this, you create your root on your 320Gb drive in a partition of, say, 20Gb. Place your swap partition there, too. Then use the remainder of the 320Gb drive, and the entirety of your 500Gb drive, as a single "logical" volume for /home.

I've never used LVM (obviously; I've only just come across it), but it looks like the perfect solution for you, if you can find out how to set it up.

---

