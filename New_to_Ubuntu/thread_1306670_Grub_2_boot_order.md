---
title: "Grub 2 boot order"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by championboxes on 2009-10-30
Ok I have scanned over these two posts [Grub 2 Introduction]("http://ubuntuforums.org/showthread.php?t=1285897&highlight=change+boot+order") and [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=change+boot+order")
and haven't been able to find the answer im looking for...

I need to make windows the default boot... as far as I can understand I have to edit /etc/grub.d/00_header to boot windows first but I do not know exactly what to change anybody know exactly what to do?

---

### Post by bgeraghty on 2009-10-30
The configuration file you are looking for will be one of the following:
```
/boot/grub/menu.lst
/boot/grub/grub.conf
/etc/grub.conf
```
Most likely, it will be the first one.

This will contain a list of the choices you have in the grub menu.

Look for the line:```
default=0
```
This is the line that dictates which choice to have selected in the grub boot menu.  

So scroll down until you see the first instance of the setting called 'title'. (usually this is your normal Ubuntu boot choice) This being option '0', scroll down and add 1 to that every time you hit a new 'title' ID. When you arrive at the OS you want, change the default=0 to default=(whatever number you ended up with). You can also change the countdown time with the 'timeout=10' line to however many seconds you want it to wait for you to change the choice.

---

### Post by ranch hand on 2009-10-30
The boot order is set in /etc/default/grub.

---

### Post by championboxes on 2009-10-30
> **ranch hand said:**
> The boot order is set in /etc/default/grub.

Thanks that solved my problem

---

### Post by specialk1st on 2009-11-05
Thanks so much!  I'm a newbie and this solved my problem too.

---

### Post by dbell1969 on 2009-11-10
Hi I am still confused.  How do I change the boot order?  This is the output of /etc/default/grub:

[I]# If you change this file, run 'update-grub' afterwards to update
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
#GRUB_DISABLE_LINUX_RECOVERY="true"[/I]

---

### Post by Tholley on 2009-11-10
> **dbell1969 said:**
> Hi I am still confused.  How do I change the boot order?  This is the output of /etc/default/grub:

[I]# If you change this file, run 'update-grub' afterwards to update
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
#GRUB_DISABLE_LINUX_RECOVERY="true"[/I]

You can use Startup Manager. that is what I like to use.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by philinux on 2009-11-10
GRUB_DEFAULT=0 is the entry you need to modify.

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

Or use startupmanager if this is a bit daunting.

---

### Post by dbell1969 on 2009-11-16
[I]GRUB_DEFAULT=0 is the entry you need to modify.

[/I][[COLOR=#444444]*https://help.ubuntu.com/community/Gr...ing%20GRUB%202*[/COLOR]]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")

*Or use startupmanager if this is a bit daunting.*
 
 
Thanks Philinux, that took care of it.

---

### Post by YuraYong on 2010-06-05
Thank all for the tips... give me some idea of what I need :guitar:
But other credit also go to below help :)

[http://www.hackourlives.com/change-default-boot-order-ubuntu-10-04-lucid/](http://www.hackourlives.com/change-default-boot-order-ubuntu-10-04-lucid/)

(I am newbie here in this forum, hopefully didn't break any rule by posting the above link)

---

### Post by edw666 on 2012-02-10
Hello everybody,

I know this is probably an old question but how do you set Windows in a dual boot environment to boot first?  My understanding is that you have to set  
[I]GRUB_DEFAULT=4  
[/I]if Windows is the [I]4th entry in the grub menu!  But what will happen if the kernal is updated - then there are at least 2 new lines inserted for the new kernal and Windows will be in the 6th line!  Do I have to update the default value everytime this happens (alternatively delete the old kernal and subsequently the repective lines in Grup) or is there a smarter way around this issue! :confused: 

Thanks for your help and suggestions!


[/I]

---

### Post by bogan on 2012-02-10
Hi! **edw666**,
Rather than having to edit system files, as suggested in this old thread, or Startup Manage, which is a bit iffy with 11.10.

To edit and re-arrange the Grub menu, plus add a background image, alter  fonts and colours, and much else, you want Grub Customizer. It is an  easy to use Graphics tool.

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134) Go to Post #1 for a full explanation.

You are correct that you may have to alter the default setting after a major update, but with Grub Customizer you can make Windows the top entry in the Grub Menu, and then you will not have to alter it again; at least, not as long as you still want Win as default.

Chao!, **boga**n.

---

