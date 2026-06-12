---
title: "Loading b43 driver and module"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by ThreeLies on 2010-02-17
I recently was setting up a custom Kubuntu 8.10 distro (Backtrack 4 final). From stock my b43 Broadcom card worked out of the box but then I attempted to update the driver in an attempt to add injection ability. Following instructions from here hxxp://www.aircrack-ng.org/doku.php?id=b43 also installing compat-wireless latest version.

After a few reboots I am not able to get my wireless card to show up in ipconfig -a command. Issuing a 'modprobe b43' returns this

> FATAL: Error inserting b43 (/lib/modules/2.6.30.9/updates/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by lkraemer on 2010-02-18
WOW,  You have a post with lots of possibilities that could be wrong.
First off, the Hardware isn't a b43 card.  The b43 is your driver for
your hardware.  Second, the command is iwconfig (ifconfig) for Linux.
Don't mix-n-match as it makes it hard for others to understand what
you're trying to tell us.

The best thing to do is to have you do the following in a
Terminal Window:
```

history > lastcmds.txt
lspci
lspci -nn
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig

```
Then post the output of these commands, along with the history file.

Most likely you had errors in the make and either didn't notice or didn't
care.  By posting the commands we will have an idea of the steps you took,
but not the result.  That is going to have to come from you, along with
what hardware was used to make the proper choices from the Aircrack site.
[http://www.aircrack-ng.org/doku.php?id=b43](http://www.aircrack-ng.org/doku.php?id=b43)

So, sit down, relax, and make a listing of what you think you did,
what choices were made as to the hardware, and the route and commands
used as best you can remember.  Your history should help give us more
details.

lk

---

### Post by ThreeLies on 2010-02-18
So to rule out any other problems I am trying this from a fresh install. I am attempting to install compat-wireless using this page for information [http://www.aircrack-ng.org/doku.php?id=compat-wireless](http://www.aircrack-ng.org/doku.php?id=compat-wireless)

My kernel version is '2.6.30.9' so on that page I follow the instructions that say 'Kernels newer than and 2.6.27' and follow them exactly from a fresh install (i also have a pastebin of the make/make install).

make - hxxp://pastebin.com/m6443dd0f
make install - hxxp://pastebin.com/m53b5501f


After the 'make install' I run 'make unload' and reboot the machine no luck on the wireless card still.

Thanks for help too, its very much appreciated.

---

