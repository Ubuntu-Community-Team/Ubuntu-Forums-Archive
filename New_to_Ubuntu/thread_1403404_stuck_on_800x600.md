---
title: "stuck on 800x600"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by richard.smith71 on 2010-02-10
I know this pops up from time to time but the solutions I've seen seem to be about particular graphics cards.  The problem is, under display preferences I only get two options, 800x600 or 640x480.

Any ideas?

I'm using an old Dell machine with (I think) Intel Grantsdale G Integrated Video, and Ubuntu 9.10.

---

### Post by L Campbell on 2010-02-10
> **richard.smith71 said:**
> I know this pops up from time to time but the solutions I've seen seem to be about particular graphics cards.  The problem is, under display preferences I only get two options, 800x600 or 640x480.

Any ideas?

I'm using an old Dell machine with (I think) Intel Grantsdale G Integrated Video, and Ubuntu 9.10.

Hi, I have had a similar problem on my machine.

What I did was to re-install from my 8.04.4 Live CD and the problem was gone.

I hope this will be helpful to you.

Kind regards.

---

### Post by lockalidiot on 2010-02-10
Hi.

I also had the same problem with my 64-bit karmic. What I did was to run update manager and install all the updates it recommended. After restarting the computer I was able to use Nvidias own tools to adjust my resolution.

---

### Post by patchwork on 2010-02-10
I'm curious to see what mode pool is being created during X initialization (and what modes are being rejected).

---

### Post by richard.smith71 on 2010-02-10
> **patchwork said:**
> I'm curious to see what mode pool is being created during X initialization (and what modes are being rejected).

How would I find that out?

---

### Post by patchwork on 2010-02-10
It would require adding the line

```
Option "ModeDebug" "True"
```to the "Device" section of your /etc/X11/xorg.conf file

Next, restart the X server (sudo service gdm restart), or reboot

After this, please post your Xorg.0.log output (found in /var/log/Xorg.0.log)


EDIT:  Also, do you have any information on your monitor's capabilities, such as resolution, refresh, sync frequencies, etc?  Anything you have will help us down the raod)

---

