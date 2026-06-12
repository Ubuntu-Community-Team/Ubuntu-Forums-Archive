---
title: "Ubuntu text mode"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by frankbr on 2009-11-26
How can I Initialize or switch Ubuntu to text mode ? I need ´ccause I´m About to install a video driver an Xserver must not be running .

Does startx initialize X ?

---

### Post by MelDJ on 2009-11-26
boot into recovery mode?

---

### Post by coffeecat on 2009-11-26
What video driver are you trying to install? And are you really still running 6.06?

If you are running a later version of Ubuntu, the Hardware drivers utility or, failing that, envy, should be able to install most proprietary video drivers.

---

### Post by frankbr on 2009-11-26
> **coffeecat said:**
> What video driver are you trying to install? And are you really still running 6.06?

If you are running a later version of Ubuntu, the Hardware drivers utility or, failing that, envy, should be able to install most proprietary video drivers.

I&#7743; tryng to install a Nvidia Gforce MX 4000 driver I´ve just Downloaded from
the net and the installer wont run in graphic mode It demands Xserver to be turned OFF in order to proceed the installation process.

---

### Post by The Cog on 2009-11-26
I don't know why you don't just install the driver in the repository, but here's how I install the downloaded driver (on my ION chipset PC):

Go to a text console: **Ctrl-Alt-F1**
Kill the X server: **sudo /etc/init.d/gdm stop**
Install the driver: **sudo ./watever-the-installer-is-called**
Restart the X server: **sudo /etc/init.d/gdm start**

---

### Post by falconindy on 2009-11-26
Alternatively, append 'text' to your kernel boot line on bootup. Stopping gdm doesn't always kill X server entirely.

---

