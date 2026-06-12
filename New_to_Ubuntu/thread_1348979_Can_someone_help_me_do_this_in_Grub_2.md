---
title: "Can someone help me do this in Grub 2?"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Kraust on 2009-12-07
Grub Version: 1.97 beta4

I currently dual boot Ubuntu and XP but I let my mother sometimes use Ubuntu to check her mail and whatnot. I do NOT want her to be able to access the XP part of the System in the chance that she may get a virus on my computer.

The problem is that when Grub loads it gives Options to boot from Ubuntu (2 different Kernels and recovery options) Memtest, and XP for a set time. In previous Grub Versions I've used I didn't have to see the boot OS choice screen unless I purposely hit the ESC key within a time limit (probably like 3 seconds)

That all sounds a bit wanky with the wording so I'll just get to what I want:

I want to make it so I need to press a key to see a list of Operating Systems to boot into rather than giving me a list and a time limit. Also, I want to defaultly boot unto Ubuntu without the need to press any Keys.

I'm sorry, I don't know what file to edit for this. I'm not that good with Grub and I've only modified it a few times in my linux experience.

---

### Post by bsharp on 2009-12-07
> **Kraust said:**
> Grub Version: 1.97 beta4

I currently dual boot Ubuntu and XP but I let my mother sometimes use Ubuntu to check her mail and whatnot. I do NOT want her to be able to access the XP part of the System in the chance that she may get a virus on my computer.

The problem is that when Grub loads it gives Options to boot from Ubuntu (2 different Kernels and recovery options) Memtest, and XP for a set time. In previous Grub Versions I've used I didn't have to see the boot OS choice screen unless I purposely hit the ESC key within a time limit (probably like 3 seconds)

That all sounds a bit wanky with the wording so I'll just get to what I want:

I want to make it so I need to press a key to see a list of Operating Systems to boot into rather than giving me a list and a time limit. Also, I want to defaultly boot unto Ubuntu without the need to press any Keys.

I'm sorry, I don't know what file to edit for this. I'm not that good with Grub and I've only modified it a few times in my linux experience.
Add "hiddenmenu" (no quotes) somewhere in /boot/grub/menu.lst

---

### Post by Kraust on 2009-12-07
That easy? Thanks.

---

### Post by community nerd on 2009-12-07
on my computer it, ubuntu is the default. As far as editing the grub file it is /boot/grub/menu.lst. all the OS are listed on there and I assume you could change their position with that. but you would have to edit it through 
[PHP]sudo gedit /boot/grub/menu.lst[/PHP]

---

### Post by Locke_99GS on 2009-12-07
There is no /boot/grub/menu.lst used by Grub2, which the OP is using.

Open /etc/default/grub and *un*-comment the line that says "**#GRUB_HIDDEN_TIMEOUT=0**". That should hide the menu. After which, issue the update-grub command to rebuild the grub config.
```

sudo gedit /etc/default/grub
sudo update-grub

```

edit: Ohh yeah, once you hide the menu, you'll need to hold SHIFT while booting to display it.

---

### Post by Kraust on 2009-12-07
> **Locke_99GS said:**
> There is no /boot/grub/menu.lst used by Grub2, which the OP is using.

Open /etc/default/grub and *un*-comment the line that says "**#GRUB_HIDDEN_TIMEOUT=0**". That should hide the menu. After which, issue the update-grub command to rebuild the grub config.
```

sudo gedit /etc/default/grub
sudo update-grub

```

edit: Ohh yeah, once you hide the menu, you'll need to hold SHIFT while booting to display it.
Thanks, I just booted back in and I was wondering why editing an Empty file that should have been there did nothing <_<.

Now I need to go back into Ubuntu and fix this.

---

### Post by Kraust on 2009-12-07
Alright, apparently that didn't do anything. Did I have to give a value to the **GRUB_HIDDEN_TIMEOUT=0** variable other than 0 for it to work?

Here's the /etc/default/grub file I have right now:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
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

So If I wanted it to not show the Boot menu and lets say give me 5 seconds to activate it, how would I edit my file to do it?

---

### Post by Locke_99GS on 2009-12-07
Alter GRUB_HIDDEN_TIMEOUT value to reflect wait time in seconds..
It may not function as expected with other OS's present. According to this: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) and this: [https://wiki.ubuntu.com/DesktopExperienceTeam/KarmicBootExperienceDesignSpec#Bootloader](https://wiki.ubuntu.com/DesktopExperienceTeam/KarmicBootExperienceDesignSpec#Bootloader) , the devs may have screwed us over *again*.

---

### Post by Kraust on 2009-12-07
Aww, thanks for your help. That kinda sucks that GRUB_HIDDEN_TIMEOUT is broken.

---

