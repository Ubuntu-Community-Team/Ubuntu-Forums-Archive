---
title: "Admin priviledges"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by byeutter on 2009-11-06
I am hoping someone can help me with terminal. I am trying to access terminal so that I can edit the dual boot menu so that the system defaults to windows for my wife's convenience.

In terminal I have tried to type sudo su and get the command line that says:
root@brad-desktop:/home/brad#

I am using Ubuntu 9.10

I have tried typing sudo su with my password and it comes back that the first part of my password is a unrecognized user. I have tried to login to the root account from the upper right most menu and keep getting the message that the authentication fails. 

I am new to Ubuntu, just trying to get my bearings still. 

Thanks in advance for your help!

---

### Post by ranch hand on 2009-11-06
Ok, is this a clean install (from disk) or an upgrade from 9.04?

Please run;
```

gksudo gedit /etc/default/grub

```
and copy paste the results here.

You will be asked for your password after you enter that command.  Use the same one you log in with.  Make sure that your CapLock is OFF.

---

### Post by byeutter on 2009-11-06
It was a clean install of 9.10 from disk. I installed it beside my vista install

It did not ask me for a password, it just placed the following in a separate window:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

Can I actually edit it from this new pop up if I type update grub after it?

---

### Post by sgosnell on 2009-11-06
I'm not sure I understand your problem.  

root@brad-desktop:/home/brad#

is what you should see when you log into the terminal as root.  That's all you get, you have to type in whatever commands you want to run.

---

### Post by sisco311 on 2009-11-06
You can set the default OS in startupmanager: [https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

Click [here]("apt://startupmanager") to install it(<- apturl link). (Or install it via Synaptic or Software Center)
To open it go to: System > Administration > StartUp-Manager.

---

### Post by ranch hand on 2009-11-06
The reason for the external login is because you are working in a terminal controlled graphic environment.  That is what gksudo is for instead of sudo.

I am glad that this is a clean install.

The line "GRUB_DEFAULT=0" is the line you need to edit.  Counting starts at 0.  You need to change the 0 to what ever number is right for where your MS entry is in the menu.  If you are not sure where this is and what to count the bugger do, in another terminal;
```

gksudo gedit /boot/grub/grub.cfg

```
that will pull up the file that makes the menu you see.  Just count every menuentry, starting with 0, to your MS entry.  Use that numcer in the " GRUB_DEFAULT=0" line.

Then yes, you need to run;
```

sudo update-grub

```
You may want to look at the post linked in my sig.  It is basic and simple.  The links on it are great.  The first 3 are in depth on grub2.

Grub2 is FUN.

---

### Post by byeutter on 2009-11-06
Thank You! The problem is solved. I appreciate the help from you all. Not sure how to mark this thread as closed So I am just going to say that it is.

---

### Post by sisco311 on 2009-11-06
> **byeutter said:**
> Thank You! The problem is solved. I appreciate the help from you all. Not sure how to mark this thread as closed So I am just going to say that it is.

Cool!!!

You can mark this thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].
(see the link in my signature)

---

