---
title: "Grub Endless Reboot"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by Beggar Su on 2009-07-01
Hi all,

I have this annoying problem with my Dell Vostro 400 desktop computer during start up. When I power on the computer the following occurs:

* Dell logo
* Grub loading stage (count down message) with the option to press Esc to edit options etc.
* 
**Boot from** (partition number etc)
[B]Starting up ...
[5.x] Not responding[/B] (where x is different for every reboot)

* Computer reboots

It does this repeatedly unless I go to recovery mode at the grub menu and resume normal boot from there or start pressing the num lock key at the "Starting up..." stage and hopefully get a "Loading..." message, which will then resume the boot to the desktop.

I have ubuntu 9.04 - fresh install.

Is this a USB problem? Also there are no problems using the keyboard during bios, grub boot options editing or after login.

Please help :(

---

### Post by coffeeaddict22 on 2009-07-01
The kernel writes all it's messages to a log; you need to have a look through there to see where the problem might be.  There's a number of ways to look at it, try whichever suits:  
1) System/admin/log file viewer; there's a fair few files in there, and that's a good way of flicking through them if you're not into much typing.
2) In a terminal: ```
dmesg
``` will give you most of the boot time messages
3) in a Terminal again: all the log files are in /var/log.  cd /var/log to start, then ls will list them; you can see what's in file xxxx by typing ```
cat ./ xxxx
```  Post the terminal output back if you want more help.

---

