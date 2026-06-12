---
title: "How do I permanently set boot options for different version"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by idloveacupoft on 2011-07-18
The title may seem a bi vague so here's the detail.
I recently upgraded to natty narwhal 11.04 from 10.10(maverick meerkat). This went okay but then a few days ago, I ran the automatic updates in the update manager and (btw, i'm bit of a noob) I think it tried to set up the version 2.6.38-10-generic. 
Anyways, I restarted the computer to finish the updates and while the computer was booting, it could not get past the purple screen.
I have read that this was a common problem. 
Then on reset the computer gives you the option to boot using an older version, which I have done, and have been doing since.

Basically, I would like to know how to permanently set it to this previous version without having to boot - reset - boot previous version.
I was thinking of deleting the newer version's files in the package manager but am worried in case I mess up an older version.  
Any thoughts are welcome. This is probably a piece of cake for a lot of people:D

---

### Post by Brushstroke on 2011-07-18
Do you mean boot into the old kernel? 

Get to the GRUB screen by holding the Shift key when your computer turns on. Check which versions there are. The lineup goes like this:

kernel #1 (this is 0)
kernel #1 recovery mode (this is 1)
kernel #2 (this is 2)
kernel #2 recovery mode (this is 3)
memtest (this is 4)

...something like that. 

You're automatically booting into the first option, the latest kernel. What you want to do is edit /etc/default/grub: 

```
sudo gedit /etc/default/grub
```You'll see this: 

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=769"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1366x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```You want to edit the line **GRUB_DEFAULT=0** and change it to **GRUB_DEFAULT=2 **to get GRUB to automatically boot into the old kernel. After that, save the file. 

Then run: 
```
sudo update-grub
```
And reboot. And you should be good.

---

### Post by idloveacupoft on 2011-07-19
That was exactly what I was looking for and it sorted out the inconvenience. Thanks friend.

---

