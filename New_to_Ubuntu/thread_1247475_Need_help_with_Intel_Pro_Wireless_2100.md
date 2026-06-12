---
title: "Need help with Intel Pro Wireless 2100"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-08-23
Can you help me follow these instructions.

I am having the problem in 2.1  (see below)


I tried the command,and got...


luke@vaio:~$ grep CONFIG_NET_RADIO /lib/modules/2.4.26/build/include/linux/autoconf.h
grep: /lib/modules/2.4.26/build/include/linux/autoconf.h: No such file or directory
luke@vaio:~$ 


the 2nd command

luke@vaio:~$ define CONFIG_NET_RADIO 1
bash: define: command not found



..............
[http://ipw2100.sourceforge.net/faq.php#qa_2_0](http://ipw2100.sourceforge.net/faq.php#qa_2_0)

Wireless Tools

2.1. IPW2100 - Why won't the wireless tools (iwconfig, iwlist, etc.) work
    If the Wireless tools have not been installed, and the kernel has not been configured to use them, then they will not work.
    Ensure that your kernel has been compiled with the CONFIG_NET_RADIO=y parameter. (Can check using:

    % grep CONFIG_NET_RADIO /lib/modules/2.4.26/build/include/linux/autoconf.h

    and checking that you see:

    #define CONFIG_NET_RADIO 1

    Also, ensure that the latest wireless tools have been installed from [http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html). 
..............

---

### Post by 3rdalbum on 2009-08-23
Whoa, soldier, there's no need to do that.

"2.1. IPW2100 - Why won't the wireless tools (iwconfig, iwlist, etc.) work
If the Wireless tools have not been installed, and the kernel has not been configured to use them, then they will not work."

The wireless tools are installed and the kernel is configured to use them. This is Ubuntu, it supports wireless networks out-of-the-box.

Those instructions were written YEARS ago, before Ubuntu ever came out, and back when a wireless card was a rare and exotic piece of hardware. Back when the kernel version was 2.4.26 (all versions of Ubuntu, from 2004 onwards, have shipped with kernel 2.6). That's why the command fails: You don't have any directories corresponding to kernel 2.4.26.

That set of instructions tells you how to enable wireless support on that old kernel. You have wireless support. If you persist with this, you *WILL* mess up your system.

---

### Post by nhasian on 2009-08-23
if your trying to get your wifi to work with ubuntu, you can start by telling us which version of ubuntu your using.  8.10, 9.04?  32bit or 64bit?  next we need to know which network adaptor you have.  in a terminal type:

```
lshw -C network
```

---

### Post by wlraider70 on 2009-08-23
ok so let me back up.
what i want to do is make my card go into monitor mode.

but when i try this 

luke@vaio:~$ iwconfig eth1 mode managedError for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not permitted.
luke@vaio:~$ iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :

    SET failed on device eth1 ; Operation not permitted.
luke@vaio:~$ 
luke@vaio:~$ 


so i thought the above was the key.

how would i go to monitor mode.

---

### Post by aysiu on 2009-08-24
Should automatically work:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

What's the problem exactly?

---

### Post by wlraider70 on 2009-08-24
the card does work. im using it now.
i just want to go into monitor mode, and i can't.

---

### Post by WitchCraft on 2009-08-24
> **wlraider70 said:**
> the card does work. im using it now.
i just want to go into monitor mode, and i can't.

You need to patch the driver for promiscous mode.

Note: IPW 2* driver source files are in the Linux kernel, in the net directory.

```

all:~# finger @kernel.org
[kernel.org]
The latest stable version of the Linux kernel is:           2.6.30.5
The latest prepatch for the stable Linux kernel tree is:    2.6.31-rc7
The latest snapshot for the stable Linux kernel tree is:    2.6.31-rc7-git1
The latest 2.4 version of the Linux kernel is:              2.4.37.5
The latest 2.2 version of the Linux kernel is:              2.2.26
The latest prepatch for the 2.2 Linux kernel tree is:       2.2.27-rc2
The latest -mm patch to the stable Linux kernels is:        2.6.28-rc2-mm1
all:~# uname -a
Linux all 2.6.31-rc7-custom #1 SMP Sun Aug 23 14:55:53 CEST 2009 i686 GNU/Linux

```

[http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.31-rc7.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.31-rc7.tar.bz2)

---

### Post by wlraider70 on 2009-08-25
i have never updated my kernel, i did some looking and it seems that i need to up grade to each new version of the kernel.
I can just jump from my version to whatever the version I want is.

Can i have some guidance.



luke@vaio:~$ uname -a
Linux vaio 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
luke@vaio:~$ 


I want to go to...

The latest prepatch for the stable Linux kernel tree is:    2.6.31-rc7

according to the previous post.

---

### Post by WitchCraft on 2009-08-25
> **wlraider70 said:**
> i have never updated my kernel, i did some looking and it seems that i need to up grade to each new version of the kernel.
I can just jump from my version to whatever the version I want is.
 
Can i have some guidance.
 
 
 
luke@vaio:~$ uname -a
Linux vaio 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux
luke@vaio:~$ 
 
 
I want to go to...
 
The latest prepatch for the stable Linux kernel tree is: 2.6.31-rc7
 
according to the previous post.
 
 
I've already given you the link to the full prepatch version source of the kernel (.tar.bz2).
 
Follow this link to find out how to compile and install a new kernel:
[http://ubuntuforums.org/showthread.php?p=7295561](http://ubuntuforums.org/showthread.php?p=7295561)

---

### Post by wlraider70 on 2009-08-26
i installed the new kernel and i can change modes on my wifi card.

THANKS

---

### Post by WitchCraft on 2009-08-26
> **wlraider70 said:**
> i installed the new kernel and i can change modes on my wifi card.

THANKS

Good, now in which Wireless LAN do you intend to intrude ? :lolflag:

---

