---
title: "ieee80211 + ipw2200 install issues"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by Waqsss on 2008-05-15
Hi, first of all I am a total newbie with linux, only started using it today but am already familiar with a few things including some terminal commands.

What I am trying to do is install the following:

IPW2200BG Latest Driver - ipw2200-1.2.2.tgz
IPW2200BG Latest Firmware - firmware v3.0

IEEE80211 Subsystem - ieee80211-1.2.18.tgz


At first, my wireless network connection was working fine in Ubuntu but after trying to follow the instructions for installing the drivers I somehow managed to mess something up and now I think Ubuntu cannot see no wireless device. I have either removed the ipw2200 drivers or the ieee subsystem???

Can somebody please help me get everything up and running again, I'm not in a rush and do not care how long this takes aslong as its fixed.

Thanks alot.

Edit: ieee80211 subsystem has definitely been removed by accident.

---

### Post by Waqsss on 2008-05-15
This is the error I get when I enter the make command within the ieee80211 folder. If I do the sudo make command I get the same response minus the permission denied section and am also having no luck with the make SHELL command.




> waqar@waqslaptop:/Desktop/ieee80211-1.2.18$ make
Makefile:17:
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21:
Checking in /lib/modules/2.6.24-16-generic for ieee80211 components...
make -C /lib/modules/2.6.24-16-generic/build M=/home/waqar/Desktop/ieee80211-1.2.18 modules
make [1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:17:
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:18: WARNING:$SHELL not set to bash
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:21:
  CC [M]  /home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.o
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function 'ieee80211_init':
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: 'proc_net' undeclared (first use in this function)
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function 'ieee80211_exit':
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:297: error: 'proc_net' undeclared (first use in this function)
{standard input}: Assembler messages:
{standard input}:9: Warning: can't open .lst: Permission denied
GAS LISTING                      page 1


    1                    .file "ieee80211_module.c"
    9                    .Ltext0:

GAS LISTING                     page 2


DEFINED SYMBOLS
                             *ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
make[2]: *** [/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/waqar/Desktop/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2


---

### Post by chili555 on 2008-05-15
What happens when you do as it suggests, *sudo make SHELL=/bin/bash*?

---

### Post by Waqsss on 2008-05-16
get this... same thing really

> Checking in /lib/modules/2.6.24-16-generic for ieee80211 components...
make -C /lib/modules/2.6.24-16-generic/build M=/home/waqar/Desktop/ieee80211-1.2.18 modules
make [1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:17:
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:18: WARNING:$SHELL not set to bash
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/waqar/Desktop/ieee80211-1.2.18/Makefile:21:
CC [M] /home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.o
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function 'ieee80211_init':
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: 'proc_net' undeclared (first use in this function)
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function 'ieee80211_exit':
/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.c:297: error: 'proc_net' undeclared (first use in this function)
{standard input}: Assembler messages:
{standard input}:9: Warning: can't open .lst: Permission denied
GAS LISTING page 1


1 .file "ieee80211_module.c"
9 .Ltext0:

GAS LISTING page 2


DEFINED SYMBOLS
*ABS*:0000000000000000 ieee80211_module.c

NO UNDEFINED SYMBOLS
make[2]: *** [/home/waqar/Desktop/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/waqar/Desktop/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

---

### Post by emilio320 on 2008-12-22
I know that this thread is fairly old but i am in virtually the same exact problem with the same exact error. I am using ubuntu 8.10 and i removed the ieee80211 subsystem and now i get an error while trying to install the new files using the Make command as well as the SHELL=/bin/bash command i am on the /2.6.27-9-generic kernel and i have the headers already  i have been researching this issue for 2 days now and i was hoping someone has since found the answer

---

### Post by dmitriyp13 on 2008-12-23
You can reinstall the ieee80211 subsystem by going to synaptic and searching for the current kerner (i.e. search for '2.6.27-9') select reinstall for everything that you find that is already installed.  This should do it.

---

### Post by acidgawd on 2009-04-29
That is the best you gots?

---

### Post by acidgawd on 2009-04-29
> **dmitriyp13 said:**
> You can reinstall the ieee80211 subsystem by going to synaptic and searching for the current kerner (i.e. search for '2.6.27-9') select reinstall for everything that you find that is already installed.  This should do it.

oh...BTW...that only leaves you back where you started...as soon as you try to reinstall ieee80211 subsystem you get the same errors

---

### Post by terminator557 on 2010-01-02
uh im having some similair issues

```
terminator557@Dissimulo:~/ieee80211-1.2.18$ sudo make ieee80211-1.2.18_INC=/usr/src/ieee80211/
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.31-16-generic for ieee80211 components...
make -C /lib/modules/2.6.31-16-generic/build M=/home/terminator557/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
/home/terminator557/ieee80211-1.2.18/Makefile:17: 
/home/terminator557/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/terminator557/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/terminator557/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/terminator557/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/terminator557/ieee80211-1.2.18/ieee80211_module.o
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c: In function ‘alloc_ieee80211’:
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:148: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:149: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:153: error: ‘struct net_device’ has no member named ‘get_stats’
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_init’:
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:268: error: ‘proc_net’ undeclared (first use in this function)
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c: In function ‘ieee80211_exit’:
/home/terminator557/ieee80211-1.2.18/ieee80211_module.c:297: error: ‘proc_net’ undeclared (first use in this function)
make[2]: *** [/home/terminator557/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/terminator557/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [modules] Error 2
terminator557@Dissimulo:~/ieee80211-1.2.18$ 

```

---

### Post by Markus83 on 2010-03-01
got exactly the same problem like terminator557 with ieee80211 on the 2.6.31-19 kernel... i found a diff patch for kernel 2.6.24 which only removes the "proc-net" errors, but the "struct net_device" errors are still there...

the diff-patch can be found here: [http://ubuntuforums.org/showthread.php?t=242556&page=10](http://ubuntuforums.org/showthread.php?t=242556&page=10)

it´s attached in the post from "gits83" (if anybody want´s to see the patch)

---

### Post by aalkounis on 2010-03-23
have the same problems with **Markus83** has anyone found a solution??

---

### Post by chili555 on 2010-03-23
Why, pray tell, are you trying to compile ipw2200 and ieee80211 from source? The built-ins work beautifully. Are you patching for some kind of injection, cracking, hacking stuff? If that is the case, I wonder if you shouldn't really be asking the developers of this ieee80211-1.2.18 file.

---

### Post by aalkounis on 2010-03-24
“A theory is something nobody believes, except the person who made it. An experiment is something everybody believes, except the person who made it.”

** Albert Einstein **

just experimenting :D

---

### Post by chili555 on 2010-03-24
> **aalkounis said:**
> “A theory is something nobody believes, except the person who made it. An experiment is something everybody believes, except the person who made it.”

** Albert Einstein **

just experimenting :DI wonder if you shouldn't really be asking the developers of this ieee80211-1.2.18 file.

---

