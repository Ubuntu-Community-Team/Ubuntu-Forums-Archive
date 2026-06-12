---
title: "GKsudo or Sudo?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by mikodo on 2009-07-14
Hello everyone,

I'm having trouble getting my head around when I should run gksudo or sudo in terminal(Gnome desktop). I have read numerous threads and links including the psychocats one.

Is it safe for me to run everything in terminal as gksudo, and then and only then, if it doesn't work, use sudo?

Keeping it simple like this will work for me, if it is correct.

Thank you.

---

### Post by Sidewinder1 on 2009-07-14
Gksudo is for running GUI programs (like Nautilus) and Sudo for everything else.
HTH, 
Side

---

### Post by nwadams on 2009-07-14
> **mikodo said:**
> 

Is it safe for me to run everything in terminal as gksudo, and then and only then, if it doesn't work, use sudo?



always be careful what you run in sudo or gksudo. If you don't know what the command is supposed to do i would suggest looking it up BEFORE  you run it to prevent any accidental damage to your data.

---

### Post by RoestVrijStaal on 2009-07-14
> **Sidewinder1 said:**
> Gksudo is for running GUI programs (like Nautilus) and Sudo for everything else.
HTH, 
Side
To extend:
if you use sudo for nautilus, firefox or any other GUI app, the permissions of the configuration files of those programs will be overwritten and owned by root. Thus if you run firefox with sudo, your own bookmarks will not be editable if you run firefox normally under your permissions.
You could make a hotkey for gksudo, for example like me, alt+F6 :)

> **nwadams said:**
> always be careful what you run in sudo or gksudo. If you don't know what the command is supposed to do i would suggest looking it up BEFORE you run it to prevent any accidental damage to your data.
You could indeed use ```
man <command>
``` for that :)

---

### Post by Sidewinder1 on 2009-07-14
Thanks for the extend Roe; I wasn't aware of that!
Would have to get permission to change permissions. :-)
As stated above, I only use sudo and gksudo when necessary.

---

### Post by mikodo on 2009-07-14
> **Sidewinder1 said:**
> Gksudo is for running GUI programs (like Nautilus) and Sudo for everything else.
HTH, 
Side


I guess the problem I'm having is knowing when something is a graphical application and when it is not.

---

### Post by RoestVrijStaal on 2009-07-14
Well, that of firefox was own experience :mrgreen:

I solve it thanks to [this topic]("http://ubuntuforums.org/showthread.php?t=801136") 
There is a lot of interesting links and info of it.

to find out what is grapical or not, just man it or run it without sudo or gksudo ;)
If it's graphical, most of all will pop up a window with the text "Are you root?" or "you need gksudo or similair to run this program".

---

### Post by kerry_s on 2009-07-14
> **mikodo said:**
> Hello everyone,

I'm having trouble getting my head around when I should run gksudo or sudo in terminal(Gnome desktop). I have read numerous threads and links including the psychocats one.

Is it safe for me to run everything in terminal as gksudo, and then and only then, if it doesn't work, use sudo?

Keeping it simple like this will work for me, if it is correct.

Thank you.

if your in the terminal you can use "**sudo**" for everything, gksudo should be used for gui programs, but sudo will be just fine.
just remember for things like the alt+f2 & launchers, it needs to be "gksudo" or you won't have anywhere to input the password.

---

### Post by mikodo on 2009-07-14
> **kerry_s said:**
> if your in the terminal you can use "**sudo**" for everything, gksudo should be used for gui programs, but sudo will be just fine.
just remember for things like the alt+f2 & launchers, it needs to be "gksudo" or you won't have anywhere to input the password.

Thank you; this is clear enough, even for me. Today, I did find about alt+f2 from other theads/sites. I'm not sure what launchers are though?

Can you explain what launchers are?

mikodo

Did some searching: Simple answer is to give examples of Launchers; Quick Silver and GNOME Do.

---

### Post by mikodo on 2009-07-14
[QUOTE=RoestVrijStaal;7616138]To extend:
if you use sudo for nautilus, firefox or any other GUI app, the permissions of the configuration files of those programs will be overwritten and owned by root. Thus if you run firefox with sudo, your own bookmarks will not be editable if you run firefox normally under your permissions.
You could make a hotkey for gksudo, for example like me, alt+F6 :)


You could indeed use ```
man <command>
``` for that :)[/QUOTE

Thank you, the manual page command is going to be a useful tool. I'll try to use it before running any unknown commands!

---

### Post by mikodo on 2009-07-14
> **RoestVrijStaal said:**
> Well, that of firefox was own experience :mrgreen:

I solve it thanks to [this topic]("http://ubuntuforums.org/showthread.php?t=801136") 
There is a lot of interesting links and info of it.

to find out what is grapical or not, just man it or run it without sudo or gksudo ;)
If it's graphical, most of all will pop up a window with the text "Are you root?" or "you need gksudo or similair to run this program".

This works too! Thanks for this direction also!

mikodo

---

### Post by CatKiller on 2009-07-14
> **mikodo said:**
>  Can you explain what launchers are?

Did some searching: Simple answer is to give examples of Launchers; Quick Silver and GNOME Do.

Things on the Desktop or panel and entries in the menu would also be launchers. Any graphical thing that starts another program would be a launcher.

A pretty simple test for whether something should count as a "graphical application" or not is whether, when it is run, you get a new window. If you do, it's a graphical application :)

---

### Post by lavinog on 2009-07-14
> **mikodo said:**
> 
Is it safe for me to run everything in terminal as gksudo, and then and only then, if it doesn't work, use sudo?


I just want to clarify:
You do not want to run everything as sudo or gksudo. Both commands remove all security restrictions that protect your system.
There should not be any reason to run firefox as superuser either.
It is common to have to run nautilus as a super user to fix a permission issue the gui way, but after you no longer need super user permission you should close nautilus and re-launch it if you want to continue to use it.

---

### Post by Jeff250 on 2009-07-14
For any advanced users, so that you don't have to accept the difference between sudo and gksudo as magic, consider these commands and their outputs:

```
$ gksudo -- sh -c 'echo $HOME'
/root
$ sudo -- sh -c 'echo $HOME'
/home/jeffrey
$ sudo -H -- sh -c 'echo $HOME'
/root
```

sudo -H will set your home directory to root's, which gksudo does by default, but bare sudo will keep your home directory even when running as root.  A lot of gui programs (and even some console programs) write files to the home directory, so if you run a program as root and don't want root-owned files in your personal home directory, the home directory needs to be set to root's.

---

### Post by aysiu on 2009-07-14
> **mikodo said:**
> Is it safe for me to run everything in terminal as gksudo, and then and only then, if it doesn't work, use sudo? No, you don't run *gksudo* for everything--only for graphical applications.

*sudo* is for terminal applications.

If you don't believe me, try running ```
gksudo nano /etc/apt/sources.list
``` (it'll freeze and you won't be able to save or exit or do anything) or ```
sudo firefox
``` (your Firefox profile may become corrupt or inaccessible)

If you don't know whether an application is a terminal application or a graphical application, then you should not be running it with root privileges.

---

### Post by mikodo on 2009-07-14
> **aysiu said:**
> No, you don't run *gksudo* for everything--only for graphical applications.

*sudo* is for terminal applications.

If you don't believe me, try running ```
gksudo nano /etc/apt/sources.list
``` (it'll freeze and you won't be able to save or exit or do anything) or ```
sudo firefox
``` (your Firefox profile may become corrupt or inaccessible)

If you don't know whether an application is a terminal application or a graphical application, then you should not be running it with root privileges.

No, I am not going to run these codes! Why would I not believe an Ubuntu Forums Staff Member aysiu? I'm the Newbie right? I read and follow advice from others. (Just not in the case of running these codes, because of the warnings you posted). It's all a moot point!

Anyways, thank you all, for the time and advice.

mikodo

---

