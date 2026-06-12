---
title: "I have killed Ubuntu"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by fly_boy on 2010-04-22
Hi, 
 
I have killed ubuntu, :icon_frown:
 
I was using the Compiz config manager, I selected reflection fom the avialbale options and the whole thing stopped working, I have rebooted, it allows me to log in, but then at the next stage where you see the ubuntu logo and a strobing progress bar, well.... it stops progressing and hangs at that point...
 
I can reboot to a command line, has anyone any idea on how I can recover my installation?:confused:
 
Help

---

### Post by chrisxuk on 2010-04-22
Reinstall Ubuntu.

---

### Post by fly_boy on 2010-04-22
But I will lose all of my cool setup and apps and stuff... Won't I?

---

### Post by Jguy on 2010-04-22
> **chrisxuk said:**
> Reinstall Ubuntu.

that isn't exactly the best answer. there is probably additional stuff to try.

If you can boot to a command line, it's something in X that is starting up and hanging the system. You may not have to reinstall Ubuntu, but I would try purging compiz first and see where that gets you.

---

### Post by fly_boy on 2010-04-22
OK, coool how do I do that????
 
Total Unix numpty here!

---

### Post by Calash on 2010-04-22
A reinstall should not be necessary, especially when you have terminal access.

For the command line, are you going in via recovery mode?

You may have luck with some of the following instructions.

[http://ubuntuforums.org/showthread.php?t=980835](http://ubuntuforums.org/showthread.php?t=980835)
[http://ubuntuforums.org/showthread.php?t=787251](http://ubuntuforums.org/showthread.php?t=787251)

Look for instructions on disabling, not removing, and you should be fine.

---

### Post by empty_spaces on 2010-04-22
You could try reconfiguring the xorg.conf file.
See link:
[http://www.youtube.com/watch?v=WmP72OW4eD4](http://www.youtube.com/watch?v=WmP72OW4eD4)

Edit: Just saw that you are able to get to the logon screen, so xorg is probably fine. Follow some of the other suggestions in this thread, I don't think you need to mess with xorg.

---

### Post by Ravernomina on 2010-04-22
> **fly_boy said:**
> But I will lose all of my cool setup and apps and stuff... Won't I?

Dnt do that this is just a compiz problem. Nothing major, Just underly annoying  

This Page will tell you what do to :D Gl :D

[http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html]("http://www.linuxforums.org/forum/ubuntu-help/116239-how-earth-do-you-reset-compiz-defaults-command-line.html")

---

### Post by fly_boy on 2010-04-22
Brilliant guys, 
 
Muchas Gracias, i will try that and report back!

---

### Post by gangstafoo! on 2010-04-22
Or you can do the reset compiz command.. i forget what it is but it worked for me before

---

### Post by pastalavista on 2010-04-22
Boot a live CD, open a terminal and run 'sudo fdisk -l' to find the drive you need to check and then run 'sudo fsck /dev/sda1' ... only replace 'sda1' with the actual number of your root (/) partition.

---

### Post by proxess on 2010-04-22
just go to a vtty (ctrl alt 1 to 6), log in, and delete .compiz or is it .config/compiz. Re-configuring compiz is a breeze with CCSM anyway.

---

### Post by realzippy on 2010-04-22
> **proxess said:**
> just go to a vtty (ctrl alt 1 to 6), log in, and delete .compiz or is it .config/compiz. Re-configuring compiz is a breeze with CCSM anyway.

+1.
In other words:

```
rm -rf ~/.config/compiz
```

---

### Post by fly_boy on 2010-04-22
I used the following
 
gconftool-2 --recursive-unset /apps/compiz
 
Restarted, and up popped my desktop...
 
Cool! :popcorn:popcorn all round I think

---

