---
title: "Where is grub?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by wordmaster on 2010-05-24
I tried following some instructions to modify grub and it included opening grub under etc/default, but grub is not there. I am in 10.04. Where would it be?

---

### Post by -humanaut- on 2010-05-24
I think what your looking for is /boot/grub

or
/etc/default/grub
/etc/grub.d <--- Probably this one.

---

### Post by Superkoop on 2010-05-24
Ubuntu 10.04 uses GRUB 2, So you are either looking for ```
/etc/grub.d 
```or ```
/etc/default/grub
```

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Considering I don't know what you are trying to do, I can't help much more than this.

---

### Post by wordmaster on 2010-05-24
Here are the instructions. I want to be sure I get the right grub:

gksudo gedit /etc/default/grub

Look for this line and add:

GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

Save and close your file then run:

sudo update-grub2

Reboot and see if you notice a difference.

---

### Post by Superkoop on 2010-05-24
> **wordmaster said:**
> Here are the instructions. I want to be sure I get the right grub:

gksudo gedit /etc/default/grub

Look for this line and add:

GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

Save and close your file then run:

sudo update-grub2

Reboot and see if you notice a difference.


Yes you are in the correct location. =] Just run gksudo gedit /etc/default/grub in the command line, and continue with the instructions.

---

### Post by -humanaut- on 2010-05-24
/etc/default/grub would be correct

ipv6.disable=1

is all you'd need to add the run update-grub from a terminal

---

### Post by wordmaster on 2010-05-24
However, there is no grub in etc/default. There are other grubs, but which one do I use? I am trying to turn off ipv6 in the hope that it will speed up my internet. Currently it takes several minutes for  a web site to open.

---

### Post by SPARTAN-118 on 2010-05-24
Can you please tell us the output of ```
$ ls
``` so we know what you're talking about? In my /etc/default there is only one "grub" file.

---

### Post by wordmaster on 2010-05-24
Here is the result:

$ ls
$: command not found

In my /etc/default there is "no" grub at all. There are grubs in other locations

---

### Post by kansasnoob on 2010-05-24
> **wordmaster said:**
> However, there is no grub in etc/default. There are other grubs, but which one do I use? I am trying to turn off ipv6 in the hope that it will speed up my internet. Currently it takes several minutes for  a web site to open.

What in the world are you talking about?

Please provide a link to where you found this brilliant idea.

---

### Post by MBG1987 on 2010-05-24
type in terminal:

[PHP]sudo chmod 770 /boot/grub/grub.cfg
sudo gedit /boot/grub/grub.cfg[/PHP]

now you can mass up with grub, be careful!

---

### Post by wordmaster on 2010-05-24
In this thread:

[http://ubuntuforums.org/showthread.php?p=9344871#post9344871](http://ubuntuforums.org/showthread.php?p=9344871#post9344871) 

I found this help address:

[http://wojox.homelinux.org/?p=46](http://wojox.homelinux.org/?p=46)

So the grub in boot is the one I need to change to kill the ipv6?

---

### Post by wordmaster on 2010-05-24
Also, here is the results of ls in etc/default

p@p-desktop:/etc/default$ ls
acpid         clamsmtp       kernel-helper-rc  powernowd          syslogd
acpi-support  console-setup  kerneloops        pulseaudio         tmpfs
alsa          cron           klogd             randomsound        ufw
apmd          cups           ld10k1            rcS                useradd
apport        dbus           locale            rsync              wicd
avahi-daemon  devpts         ntpdate           rsyslog            winbind
bootlogd      halt           nvidia-kernel     saned              yate
brltty        irqbalance     pmi               speech-dispatcher

---

### Post by wordmaster on 2010-05-24
hmmm, in /boot/grub/ there is no grub.cfg

---

### Post by Miljet on 2010-05-24
In /boot/grub do you find a file called menu.lst?  If so, you are running the old legacy grub and you would make your changes to the menu.lst file.

---

### Post by SPARTAN-118 on 2010-05-25
I don't recall *ever* hearing you can edit GRUB to speed up your Internet. I believe that is something you will have to take up with your Internet Service Provider (i.e. Bell, Rogers, etc.).

Does your Internet work okay (i.e., not slow) in Windows?

---

### Post by wordmaster on 2010-05-26
Yes, it is not an internet problem. It works fine in windoze and it worked fine in ubuntu untill the second to last upgrade.

---

### Post by wordmaster on 2010-05-26
Found menu.lst, but there is no line similar to what I need to change. Apparently this is not the correct file either.

---

### Post by Miljet on 2010-05-26
Yep, that is the correct file. I don't know which line to edit, but now that they know that you have legacy GRUB, I'm sure that someone will come along to help further.

---

