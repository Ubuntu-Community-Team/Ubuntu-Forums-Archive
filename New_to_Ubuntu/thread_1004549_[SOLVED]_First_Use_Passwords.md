---
title: "[SOLVED] First Use Passwords?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by slocumkaroff on 2008-12-07
Okay, I played with Ubuntu via Live CD and it looks friendly enough and exciting.  Closed down system.  Then a few hours later, went to run Live CD again but somehow now Ubuntu ended-up getting installed on my system instead.  Still, no major problems in that it looks like it partitioned itself nicely along side Windows XP so that I can access either OS.  HOWEVER,to run Ubuntu it is now asking for a username and password, neither of which I recall setting-up.  Obviously this has me effectively frozen out of Ubuntu.  How do I fix this mess?

---

### Post by cartisdm on 2008-12-07
it got installed on it's own?  Something unusual must have happened.  You can try to log in as root and not enter a password but it's generally not recommended to log in as the root user.  Try that and see what users are installed on the system

---

### Post by slocumkaroff on 2008-12-07
> **cartisdm said:**
> it got installed on it's own?  Something unusual must have happened.  You can try to log in as root and not enter a password but it's generally not recommended to log in as the root user.  Try that and see what users are installed on the system

I need a bit more guidance in how to do log in as the root user.  When I reboot the machine, what should I do differently when I choose Ubuntu (vs. XP)?

---

### Post by Michael.Godawski on 2008-12-07
>  Then a few hours later, went to run Live CD again but somehow now Ubuntu ended-up getting installed on my system instead.

Do you recall the installation steps like partitioning, setting the time zone or the mentioned setting of the user name and password ?
 If no, then it is rather unlikely that Ubuntu installed on your machine on its own...but perhaps... never say never.

As default Ubuntu has no password set for the root user.
Can you give us more info?

---

### Post by taurus on 2008-12-07
Sounds like it has it own partition.  Boot into recovery mode from GRUB menu and look to see what is your login name--username.

```
ls -la /home
```
Assuming it is karoff, change the password with

```
passwd karoff
```
Then, reboot and see if you can log in with karoff and the new password.

```
shutdown -r now
```

---

### Post by dracayr on 2008-12-07
1. try user "ubuntu", as thats the user which is installed on the liveCD (I don't know which password though, so try leaving it blank or try the password "ubuntu)

2. boot in recovery mode (If you have a dual boot, there should be that option too), then choose "resume normal boot" from the menu that appears, and you won't be asked for a password. You can now set your password from System&#8594;Administration&#8594;Users and groups

dracayr

---

### Post by slocumkaroff on 2008-12-07
> **Michael.Godawski said:**
> Do you recall the installation steps like partitioning, setting the time zone or the mentioned setting of the user name and password ?
 If no, then it is rather unlikely that Ubuntu installed on your machine on its own...but perhaps... never say never.

As default Ubuntu has no password set for the root user.
Can you give us more info?

Part of problem was that as Ubuntu was installing I was called away from computer for about 2 hrs, so it went through installation all on its own. If it wanted any info, it must have defaulted to its own values and proceeded on its merry way. When I returned and powered-up the computer it began automatically resumed in Windows, not Ubuntu.  So I rebooted, chose Ubuntu option and found the screen requesting user name and password.

---

### Post by CatKiller on 2008-12-07
> **slocumkaroff said:**
> Part of problem was that as Ubuntu was installing I was called away from computer for about 2 hrs, so it went through installation all on its own. If it wanted any info, it must have defaulted to its own values and proceeded on its merry way.

I don't think it does this. I suspect that someone else has put in values here. As far as I know, the installer will just sit there waiting for information indefinitely. That's certainly how updates work.

---

### Post by slocumkaroff on 2008-12-07
> **CatKiller said:**
> I don't think it does this. I suspect that someone else has put in values here. As far as I know, the installer will just sit there waiting for information indefinitely. That's certainly how updates work.

Problem still not solved and no one else was in home while ubuntu was installing, so mischievious fingers can't be blamed for current problems. I've tried rebooting as advised, but always end up with same screen requesting user name and password.  I've also tried entering "unbuntu" as user name, password, etc., still with no luck.  Do I need to uninstall Ubuntu and start all over again?

---

### Post by CatKiller on 2008-12-07
> **slocumkaroff said:**
> Do I need to uninstall Ubuntu and start all over again?

Well, you haven't used it, so there isn't anything that you'll want to keep, and a re-install doesn't take long, so it's not like you'll lose anything. Out of interest, did you try the username/password from Windows? I know that the Ubuntu installer has been capable of retrieving things from Windows for some time. I find it very unlikely that any partitioning scheme would be widely-applicable enough to ever be used unattended though.

But you don't have to re-install. Taurus' instructions are sufficient to find out the username and set the password. Enter the GRUB menu and select the Recovery option (single user mode). This will automatically take you to a console screen logged in as root.

---

### Post by slocumkaroff on 2008-12-07
> **CatKiller said:**
> 
But you don't have to re-install. Taurus' instructions are sufficient to find out the username and set the password. Enter the GRUB menu and select the Recovery option (single user mode). This will automatically take you to a console screen logged in as root.

I've attempted to reboot using Recovery option, but it proceeds through this automatically until  I get to choose if I want to proceed in normal.  Sorry for being so slow here, but I don't seem to "get" how to use Taurus' instructions.  Can you clarify?

---

### Post by CatKiller on 2008-12-07
> **slocumkaroff said:**
> I've attempted to reboot using Recovery option, but it proceeds through this automatically until  I get to choose if I want to proceed in normal.  Sorry for being so slow here, but I don't seem to "get" how to use Taurus' instructions.  Can you clarify?

Ah. I've not seen that before. The only times I had to use single user mode were when I was at a very early stage in my Linux learning, and such conveniences weren't available. You get an ncurses menu, with some options. Go to the *root* option. This corresponds to the old behaviour. You'll then get a prompt that says ```
root@*hostname*:~#
``` Then you can follow taurus' instructions.

---

### Post by slocumkaroff on 2008-12-07
> **CatKiller said:**
> Ah. I've not seen that before. The only times I had to use single user mode were when I was at a very early stage in my Linux learning, and such conveniences weren't available. You get an ncurses menu, with some options. Go to the *root* option. This corresponds to the old behaviour. You'll then get a prompt that says ```
root@*hostname*:~#
``` Then you can follow taurus' instructions.

Finally!!!! Many thansk. Problem solved. Now to figure out how to get th system to recognize my dsl wirelessm

---

