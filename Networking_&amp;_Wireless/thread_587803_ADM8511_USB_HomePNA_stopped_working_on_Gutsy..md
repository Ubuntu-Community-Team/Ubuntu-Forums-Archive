---
title: "ADM8511 USB HomePNA stopped working on Gutsy."
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by noyhta on 2007-10-23
Hi all, 

I have a problem with ADM8511 HomePNA adapter. It used to work in Feisty but when I installed Gutsy it stopped working. I used to have same kind of problem with it  but I managed to fix it by reloading pegasus driver with mii_mode=1 parameter. Now this fix does not help anymore. Can anybody know if there is any changes in pegasus driver in Gutsy ?

---

### Post by sugardrunk on 2007-10-25
Hello,

I have the same problem with my** XUBUNTU FEISTY** (before I tried with FEISTY to GUTSY upgrade and experienced the same problem)

I added "**sudo modprobe -rv pegasus**" and "**sudo modprobe mii_mode=1**" to my **/etc/modules/** like i used to do in Feisty,
But now (with Gutsy) the network seems to work randomly. Sometimes it just keeps "thinking" (looking for host?) for long and if i write those
"modprobe commands" to terminal, the whole thing may disconnect or by suprise, work!
Even though when i restart my eth1 and eth0 from NETWORK (I guess i have my USB HomePNA connected to my network card or such? Works fine with WinXP) it will work like 60% of time.
So now I'm really confused...

Any help for this problem? Is there a change in pegasus driver, bug, some wrong config or what?
It all used to be fine in Feisty.


Here is a screenshot about route and ifconfig, If it can explain anything... this is while the web is working fine (after restarting eth1 and eth0).
[IMG]http://www.hear.fi/mukawakiwa/info.png[/IMG]

---

### Post by noyhta on 2007-10-30
I managed to solve this problem. The pegasus driver in Gutsy were somehow changed and after compiling pegasus driver that came with Feisty and loading driver with mii_mode=1 network went up again.

---

### Post by hafuch on 2007-11-05
Hey Noyhta,

You said you got your ADM8511 USB Homepna adapter working, but how exactly? I've got the same adapter but haven't figured out how to get it to work. Could you (or someone else who knows) provide step by step instructions for how to do it? I and others I'm sure would certainly appreciate it!

Thanks!

---

### Post by noyhta on 2007-11-18
Hi, 

I don't exactly remember the details of how I managed to get pegasus driver working but I can tell the main steps: 

First I figured out the version of kernel that Feisty had and then downloaded that kernels source code. In the kernel source package there are two files pegasus.c and pegasus.h which have to be compiled as a kernel  module. Examples of  compiling kernel modules can be found all around the Internet. After the compilation I replaced the old pegasus.ko 
file in with the new one. The last step was to reload pegasus with mii_mode=1 parameter: 

sudo modprobe -r pegasus
sudo modprobe pegasus mii_mode=1

I'm sorry that I cannot provide more detailed instructions.

---

