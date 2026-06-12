---
title: "system repair"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by gil.rito on 2011-02-22
Hi all,

I've made a mistake that I don't know where I did it. 
Anyway I can't get the login screen. I got a blue screen with the message
system configuration
welcome
Please selected the language used for the instalation process
I can go to the terminal type typing,
CTRL + ALT+ F2
What I've to do to get my gnome back?

Thanks

GRG

---

### Post by rvchari on 2011-02-22
if you can safeguard the data then best way would be to re-install ubuntu. i guess that your home partition must be seperate from /. so better re-install if you cant recollect what you did... you can get your gnome back that much faster instead of worrying on what you did...

---

### Post by yeats on 2011-02-22
Looks like you're in the alternate installer, which means you probably booted with an install CD in the drive (or on a USB attached to your computer).  Can you verify this?

---

### Post by gil.rito on 2011-02-22
Thanks,

The system is working, I mean that the ubuntu 10.10 is loaded, but i've not the graphical part.
If I type CTRL+ALT+F2 i got my ~$:
The problem arrives because I've tried to install a package LIBLAS with a /.config (I guess).

---

### Post by yeats on 2011-02-22
> **rvchari said:**
> if you can safeguard the data then best way would be to re-install ubuntu. i guess that your home partition must be seperate from /. so better re-install if you cant recollect what you did... you can get your gnome back that much faster instead of worrying on what you did...

Reinstalling is a solution that works and one that I advise sometimes, but in general, I think it's better to 1) actually see what the problem is before recommending it and 2) especially if the problem is a common one use it as an opportunity to learn something about your system.  GNOME doesn't "just disappear" - there has to be a reason something has changed.

To the OP: it's best to keep track of any steps you take (tutorials you followed, commands you tried) when making changes to your system.  That way you can use the forums to their full advantage ;-).

---

### Post by yeats on 2011-02-22
> **gil.rito said:**
> Thanks,

The system is working, I mean that the ubuntu 10.10 is loaded, but i've not the graphical part.
If I type CTRL+ALT+F2 i got my ~$:



I mention the installer because you said:

>  I got a blue screen with the message
system configuration
welcome
Please selected the language used for the instalation process

and that is the start screen for the alternate installer.  You can access alternate TTYs with Alt-F[2-6] during that process.  So I ask again, can you confirm that you did not boot into the installer?

> The problem arrives because I've tried to install a package LIBLAS with a /.config (I guess).

What steps did you take to install this program?

---

### Post by gil.rito on 2011-02-22
Thanks again,

Yes I didn't boot into the installer.
I've followed the steps given in

[http://sourceforge.net/apps/trac/saga-gis/wiki/Compiling%20a%20Linux%20Unicode%20version](http://sourceforge.net/apps/trac/saga-gis/wiki/Compiling%20a%20Linux%20Unicode%20version)

GRG

---

### Post by yeats on 2011-02-22
> **gil.rito said:**
> Thanks again,

Yes I didn't boot into the installer.

Okay - then are you still seeing the blue screen with the language selection for the install process (When you do Alt-F1)?  If so, I will need more information about why you're seeing that before being able to advise you.

> I've followed the steps given in

[http://sourceforge.net/apps/trac/saga-gis/wiki/Compiling%20a%20Linux%20Unicode%20version](http://sourceforge.net/apps/trac/saga-gis/wiki/Compiling%20a%20Linux%20Unicode%20version)

You might view this thread: [http://ubuntuforums.org/showthread.php?t=89208](http://ubuntuforums.org/showthread.php?t=89208)

which might give you some direction (once your blue installer screen issue is sorted out).

---

### Post by gil.rito on 2011-02-22
When I do ALT-F1 nothing happens...
I've booted with a live CD and typed
[B]sudo su
fsck -fyv /dev/sda[COLOR=red]1[/COLOR]
reboot[/B]
but the problem remains the same.

---

### Post by gil.rito on 2011-02-22
Any help, please.
GRG

---

### Post by yeats on 2011-02-22
So as I understand it, you are booting up and getting to a screen that looks like this?:

[IMG]http://www.ubuntu.com/sites/default/files/active/text-installer.png[/IMG]

If that's not the problem, please clarify what you're experiencing.

---

### Post by gil.rito on 2011-02-22
Yes.
But I've found a work-around. If I type 
startx
I got the system back.
But for each login I've have to:
1. type ALT+F2,
2. type my login and password
3. type startx
4. type again password

Gil

---

### Post by JKyleOKC on 2011-02-22
From the fact that startx works properly, I suspect that somehow in the process of installing from source, the startup instructions to load and run the Gnome display manager "gdm" got wiped out. You could verify this by going into the /etc/rc.local file via "sudo $EDITOR" and inserting the line "service gdm start" immediately before the existing "exit 0" line, then saving the file and re-booting.

The "sudo" line will ask for your password but won't echo anything as you type it, and will then launch your default text editor. The rc.local file is a script that is the very last thing executed during the boot-up sequence. The "service" line starts the gdm service; since rc.local runs as root, it does not need the "sudo" prefix.

The gdm service handles the login screen for GNOME, and launches the GUI. It's normally started somewhat earlier in the boot sequence, but doing so through rc.local is a quick and dirty way to deal with its absence.

If that works, you can search the forums for "gdm" and find other ways to restore it more conventionally. Using the BootUp Manager program "bum" is the usual approach.

Hope this helps.

---

