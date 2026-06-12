---
title: "Unable to complete boot with Ubuntu 9.04"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by allblackfan on 2009-10-22
[COLOR=black][FONT=Verdana]I have Ubuntu 9.04 loaded on an Acer Travelmate 8000. I have been trying to get familiar with the OS, but now I am unable to complete the boot sequence. 
I get past the username and password boxes, and then get an error meassage that reads:

"I could not start your session and so I have started the failsafe xterm session. Windows now have focus only if you have your cursor above them. To get out of this mode type 'exit' in the window in the upper left corner".

When I accept the message I get the terminal box with the following:

"basename: relocation error: basename: symbol_guard, version GLIBC_2.3.2 not defined in file libc.so.6 with link time reference.
[:253:=:unexpected operator
sed: relocation error: sed: symbol_guard, version GLIBC_2.3.2 not defined in file libc.so.6 with link time reference".

I have tried to boot in recovery mode and tried 'repair broken packages', 'file system check' etc. Nothing works. I also tried all the routines on the Ultimate Boot CD without success. I started to run the installation CD but it wants to start from the beginning with partitions etc.

Can anyone help? Is there anyone in Jakarta that might help?[/FONT][/COLOR]

---

### Post by ranch hand on 2009-10-22
When you get to xterm, with the cursor in the box, type;
```

sudo apt-get update

```
and then when that is finished;
```

sudo apt-get upgrade

```
when that is finished, try rebooting and post the results.

---

### Post by linuxdualbooter on 2009-10-28
I have the same problem. What is xterm?

---

### Post by zeroseven0183 on 2009-10-28
> **linuxdualbooter said:**
> I have the same problem. What is xterm?

xterm is another Command Line Interface (CLi) in Ubuntu. It works like the gnome-terminal.

See this thread: [http://ubuntuforums.org/showthread.php?t=521212](http://ubuntuforums.org/showthread.php?t=521212)

@allblackfan It will also help if you could recall the last activity you did before that happens.

---

