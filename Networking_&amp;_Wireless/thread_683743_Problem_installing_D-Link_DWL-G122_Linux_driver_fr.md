---
title: "Problem installing D-Link DWL-G122 Linux driver from Ralinktech."
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by eduardo.mendes on 2008-01-31
Hi everyone,

I am new to Linux, and bláblá, you know the story, lots of probs :confused:

I have a Wireless G USB  D-Link DWL-G122 version 3.10 C1, which I am trying to install in Ubuntu 7.10 (Gutsy Gibbons). I got the Linux driver from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html), and downloaded the *RT2500USB(RT2571/RT2572) (source Code)*.

After unpacking that bundle, have been trying to follow the instructions in the README file. My current problem is, when trying to execute the Makefile, I get the following error:
$ make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/eduardo/Downloads/USB G Wireless adapter/RT25USB-SRC-V2.0.8.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `G'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

Below, I am also posting the result (pls see attachment) when I run *make -d*. Does any of you have any idea why this is happening? Where does this G target come from? Thanks in advance for any help you can give. I have already lost so much time with this issue, that I am even ashamed to tell :-(

---

### Post by Hightide on 2008-01-31
HI eduardo

network manager may be causing you problems. Have a look at an alternative called WICID

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

regards

:)

---

### Post by eduardo.mendes on 2008-02-01
Hello Hightide,

thanks for the tip. But I would still need to get my wireless driver up and running, even when using  wicd? I am not being able to do that, as the make used to compile it is failling :-(

Any help would be much appreciated!

Thanx.

---

### Post by hnasaabom on 2008-06-12
I see this is fairly late, but in case you havn´t solved the problem, the issue is with the folder name in your path. Flder names with spaces  cannot be read from the comandline as they become interpreted as arguments in the command. .Remove any spaces from the folder names or replace with dashes/underscore or similar and try again.

Hans

---

