---
title: "Recover from hung install with Update Manager - emulate Optical Disk Drive?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-07-07
[SIZE=2][COLOR=DarkRed]The Problem[/COLOR][/SIZE]

On my wife's Xubuntu mini-laptop, the Update Manager hung while installing updates. (I've never come across that error before!)

The only thing that I could do was restart the machine.

Now, when we attempt to boot, it drops into a text prompt, and I can't access apt-get, GParted, or anything useful.

I called technical support (the mini-laptop is still under warranty), and he said that we'd have to use the Product Recovery DVD. To do this, we need a **bootable external optical disk drive** (the mini-laptop doesn't have one built in). Unfortunately, we don't have one, nor do any of my friends.

[SIZE=2][COLOR=DarkRed]The Solution (I hope)[/COLOR][/SIZE]

I was wondering if either of the following would be possible, and if so, which would be easiest.


[LIST=1]
[*]Put the Product Recovery DVD into another laptop, connect it to the mini-laptop via a USB cord, and have the laptop somehow emulate a bootable external optical disk drive for the mini-laptop.
[*]Somehow copy the Product Recovery DVD to a USB flash drive and get the mini-laptop to boot from the flash drive.
[/LIST]

Here's hoping that someone can give me a great answer!

---

### Post by taurus on 2009-07-07
When you said you can't access apt-get, what exactly does it mean?  Does it give you an error when you try to run it or does it say something like "command not found"?

---

### Post by Paddy Landau on 2009-07-07
> **taurus said:**
> When you said you can't access apt-get, what exactly does it mean?
Sorry, I should have told you. The "(initramfs)" below is the prompt.

```
(initramfs) apt-get
/bin/sh: apt-get: not found
```I have access to the very basic commands such as *ls* and *cd* (these are built in, right?).

---

### Post by taurus on 2009-07-07
Can you boot your machine into recovery mode from GRUB menu?  Is that an option?

---

### Post by Paddy Landau on 2009-07-07
> **taurus said:**
> Can you boot your machine into recovery mode from GRUB menu?
Yes, I can. After a long wait, I get...
```
        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/sda2 does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
```Then I get exactly the same prompt and problems as I described in the first post.

Trying those commands from the error messages, I get the following.
```
(initramfs) cat /proc/cmdline
ro root=/dev/sda2 ht=on nohz=off single
(initramfs) cat /proc/modules
<no result>
(initramfs) ls /dev
<lots of files>
```

---

