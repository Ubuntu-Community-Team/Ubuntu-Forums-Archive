---
title: "display issues"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by shimmshaw on 2011-01-21
Hi, newbie here. I'm trying to install ubuntu on my laptop, but whenever it starts up, the screen is fuzzy and noisy, like a t.v. getting bad reception. It doesn't appear to show any error messages, from what I can tell through the distortion, but I can't read most of the text on the menus so I have no idea how to fix it.  I have this problem when i try installing from a CD and running inside windows through wubi. My laptop is an HP NV53 ( [http://www.gateway.com/systems/product/529668522.php](http://www.gateway.com/systems/product/529668522.php) ).  What can I do to fix it?

---

### Post by gordintoronto on 2011-01-21
It's almost certainly something to do with the video adapter, which is an ATI 4200. You could try Google: 4200 linux

Or have a look at the Ubuntu Community document on BootOptions. (Nomodeset, perhaps.)

By the way, your computer is a Gateway, not an HP.

---

### Post by shimmshaw on 2011-01-21
Sorry...I knew that. Thank you for your reply. I did the nomodeset and vga=771 , which the help guide said would fix laptops with display issues. I'm running it from the CD now. If I install it, would I have this problem every time the computer starts, or will it stay fixed now?

---

### Post by gordintoronto on 2011-01-22
You could install, then specify the same things so it runs OK. Then you could make a permanent change in Grub so you don't have to do anything when you boot.

---

### Post by shimmshaw on 2011-01-22
Well I don't know what to think now. I made the change permanently in grub, but when I restarted, the problem came back. After trying a few different things over and over, and restarting the computer over and over, ubuntu boots up with a clear screen, but without nomodeset or any other changes to grub. But then I closed the laptop's lid and the screen turned fuzzy again. After some more restarting, it starts normally again. To me it seems like the system needs to be restarted a certain number of times before it cooperates with the video card... although I'm sure somebody out there has a more logical explanation :)

---

### Post by gordintoronto on 2011-01-23
"I made the change permanently in grub..."

Which version of grub you have, depends on which version of Ubuntu you have. Making the change permanent is different between the versions. Are you sure you got instructions for the right version?

---

### Post by shimmshaw on 2011-01-23
I am pretty sure I did (used this tutorial: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) ), but i ended up reverting the changes anyway when i found out it didn't fix the problem. I thought that maybe i had done something wrong and messed up grub, but even when i try booting from the CD it doesn't seem to make a difference whether i have nomodeset checked or not.
This morning I decided I wouldn't even try messing around in grub, I just kept restarting it when it gave me a fuzzy screen. By the fourth or fifth try, the screen was clear. I guess it's less of a problem now, more of a bizarre inconvenience.

---

### Post by sikander3786 on 2011-01-25
> **shimmshaw said:**
> I am pretty sure I did (used this tutorial: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) ), but i ended up reverting the changes anyway when i found out it didn't fix the problem. I thought that maybe i had done something wrong and messed up grub, but even when i try booting from the CD it doesn't seem to make a difference whether i have nomodeset checked or not.
This morning I decided I wouldn't even try messing around in grub, I just kept restarting it when it gave me a fuzzy screen. By the fourth or fifth try, the screen was clear. I guess it's less of a problem now, more of a bizarre inconvenience.
Did you run the command *sudo update-grub* after you made changes to your /etc/default/grub?

We need to see the output of this command.

```
cat /etc/default/grub
```

---

### Post by shimmshaw on 2011-01-25
Yes, I ran sudo update-grub when I made the changes and when I git rid of them. When I ran that, it told me this:
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash "
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


---

### Post by sikander3786 on 2011-01-25
There is no 'nomodeset' in your /etc/default/grub. Do you want to pop it in now?

It has an ATI 4200 graphics card. Did you check for any available graphics drivers under System > Administration > Hardware Drivers? If drivers are available, install them and the problem should go away.

Please take a look at this page.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1358746&page=2](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1358746&page=2)

Regarding nomodeset, all you have to do is edit your /etc/default/grub

```
gksudo gedit /etc/default/grub
```

And type nomodeset at the end of this line.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash "
```

And make it look like this.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

There is a space between splash and quotes but I don't think if it is affecting any thing here. But, remove it.

Now,

```
sudo update-grub
```

---

### Post by shimmshaw on 2011-01-25
:D Installing the driver seems to have fixed it; I restarted a few times to check. Thank you both for your time.

---

