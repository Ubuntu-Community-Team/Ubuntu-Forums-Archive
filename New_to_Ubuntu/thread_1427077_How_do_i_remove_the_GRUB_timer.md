---
title: "How do i remove the GRUB timer?"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by leinad177 on 2010-03-11
can somebody please tell me how to remove the timer?

if you can't, then can you tell me how to increase it?

---

### Post by mikewhatever on 2010-03-11
By removing the timer, you'll get straight into booting, which is the opposite of increasing the count. Anyway, both are easily done, just need to know what version of Ubuntu you are running. If you don't know, take a look at the 'System' tab under Systtem->Admin->System-Monitor.

---

### Post by leinad177 on 2010-03-11
> **mikewhatever said:**
> By removing the timer, you'll get straight into booting, which is the opposite of increasing the count. Anyway, both are easily done, just need to know what version of Ubuntu you are running. If you don't know, take a look at the 'System' tab under Systtem->Admin->System-Monitor.

im running 9.10

---

### Post by Sub101 on 2010-03-11
The easiest way is to install startup manager.

```
sudo apt-get install startupmanager
```

Its a GUI which lets you change most of the grub2 settings.

---

### Post by mikewhatever on 2010-03-11
If I understand correctly, you'd like to either increase the countdown number, or to make Grub stop at the menu and wait for selections. For both, you'll need to edit a few lines in /etc/default/grub. I highlighted the changed parts.

gksudo gedit /etc/default/grub

1. 
GRUB_HIDDEN_TIMEOUT_QUIET=[COLOR="Red"]false[/COLOR]
GRUB_TIMEOUT=[COLOR="Red"]30[/COLOR] 
[COLOR="Red"]#[/COLOR]GRUB_HIDDEN_TIMEOUT=0

2.

GRUB_TIMEOUT=[COLOR="Red"]-1[/COLOR]
[COLOR="Red"]#[/COLOR]GRUB_HIDDEN_TIMEOUT=0

---

### Post by leinad177 on 2010-03-11
> **Sub101 said:**
> The easiest way is to install startup manager.

```
sudo apt-get install startupmanager
```Its a GUI which lets you change most of the grub2 settings.

> 
daniel@daniel-desktop:~$ sudo apt-get install startupmanager
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package startupmanager

doesn't seem to work

---

### Post by leinad177 on 2010-03-11
> **mikewhatever said:**
> If I understand correctly, you'd like to either increase the countdown number, or to make Grub stop at the menu and wait for selections. For both, you'll need to edit a few lines in /etc/default/grub. I highlighted the changed parts.

gksudo gedit /etc/default/grub

1. 
GRUB_HIDDEN_TIMEOUT_QUIET=[COLOR=Red]false[/COLOR]
GRUB_TIMEOUT=[COLOR=Red]30[/COLOR] 
[COLOR=Red]#[/COLOR]GRUB_HIDDEN_TIMEOUT=0

2.

GRUB_TIMEOUT=[COLOR=Red]-1[/COLOR]
[COLOR=Red]#[/COLOR]GRUB_HIDDEN_TIMEOUT=0


i tried that but it keeps on changing the file back to normal when i reset my computer

---

### Post by Sub101 on 2010-03-11
> **leinad177 said:**
> doesn't seem to work

Ok then do:

```
sudo apt-get update
sudo apt-get install startupmanager
```

---

### Post by mikewhatever on 2010-03-11
> **leinad177 said:**
> i tried that but it keeps on changing the file back to normal when i reset my computer

Did you run <gksudo gedit ...> as suggested above?
Did you hit the 'Save' button before closing?

---

### Post by garvinrick4 on 2010-03-11
Go alt/F2  then type in gksudo nautilus and you be in root for file system. Navigate to etc/default/grub like the gentleman before me stated change to -1 like he stated and hit save. Will not return to previous if you are in root. If not in root will not let you hit save, saved will be grayed out.

gksudo gedit /etc/default/grub is same as this way except at command line to bring up file in root. Do which ever you wish. But it will
stop your timer completely. Mikewhatever has been giving you the correct instruction follow him. -1 is the answer.

---

### Post by philinux on 2010-03-11
> **mikewhatever said:**
> Did you run <gksudo gedit ...> as suggested above?
Did you hit the 'Save' button before closing?

You forgot to tell him to run this.

```
sudo update-grub
```

---

### Post by leinad177 on 2010-03-11
now it just automatically boots into ubuntu...

this is my grub file at the moment, can somebody please show me what it should be?

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=-1
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
```

---

### Post by leinad177 on 2010-03-11
> **philinux said:**
> 

```
sudo update-grub
```


This is what comes up
```

daniel@daniel-desktop:~$ sudo update-grub
[sudo] password for daniel: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
```

---

### Post by leinad177 on 2010-03-11
ok i restarted, and it works now, thanks guys!

---

### Post by mikewhatever on 2010-03-11
> **philinux said:**
> You forgot to tell him to run this.

```
sudo update-grub
```

Indeed, and I have to confess, I keep forgetting to run it myself.

Let's now put it all in one piece.

1. Open the file for editing:
gksudo gedit /etc/default/grub


2. Change the lines as indicated:

GRUB_TIMEOUT=[COLOR="Red"]-1[/COLOR]
[COLOR="Red"]#[/COLOR]GRUB_HIDDEN_TIMEOUT=0

3. Save and exit.

4. Run **sudo update-grub**

---

