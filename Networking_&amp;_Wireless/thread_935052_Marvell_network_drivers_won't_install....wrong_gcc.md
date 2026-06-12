---
title: "Marvell network drivers won't install....wrong gcc"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by besseriym on 2008-10-01
Someone please help,

I have been searching for a fix to my problem for a week now with no success. I have already posted a vague thread, but have found some more information since.

My problem is that I seem to get disconnected from the internet at random intervals. I first noticed this when my Pidgin client would disconnect and then reconnect like 2 times per hour. After some research I found out that the skge drivers are buggy and do not play nice with AMD64 systems (which is what I'm currently running.)

After locating and downloading the correct driver from the marvell website and following the instructions given by belatra in this tutorial ([http://ubuntuforums.org/showthread.php?t=895814&highlight=skge](http://ubuntuforums.org/showthread.php?t=895814&highlight=skge)) I have come to a roadblock in the form of an error message telling me that the gcc version used to compile the script is different than the version I am currently using (which is correct...the script indicates gcc-4.2.3 and I am using gcc-4.2.4) and fails.

```
Create tmp dir (/tmp/Sk98IQOpJYeYUhjTJReUOQleF)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.24-21-generic)                             [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (1)                                             [   OK   ]
Check architecture./functions: line 326: arch: command not found
 (found)                                                             [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check kernel gcc version (4.2.3)./functions: line 641: [: 4.2.3: unary operator expected
 (Kernel:4.2.3 != gcc:4.2.4)                                         [ failed ]
There is a version mismatch between the compiler that was used
to build the current running kernel and the compiler which you
intend to compile the kernel module with. In most of the cases,
this is no problem, but there are cases in which this compiler-
mismatch leads to unexpected system crashes
 
If you know what you are doing and want to override this   
check, you can do so by setting IGNORE_CC_MISMATCH system  
variable:                                                  
    Example: export IGNORE_CC_MISMATCH=1                 
Installation of package failed.
Delete temp directories (done)                                       [   OK   ]

```

and yes, I have tried setting "export IGNORE_CC_MISMATCH=1" with no luck.

I have tried the only other workaround I could find (appending my kernel with "mem=3G" via the bootloader) and I still experience the disconnects. I'm not even 100% sure that this is my problem, but I have been searching for weeks through all the "connection problem" threads, trying all the fixes posted, but I have had NO success at all. 

I am on a home network with a Linksys wired router, and I am the only one in the house using Linux. There have been absolutely no problems with any of the other machines (4 of them) that are running on the network.

I am running Ubuntu 8.04 Hardy Heron on an AMD64 system. The NIC is onboard (Asus SK8V motherboard.)

I have completely run out of ideas, and I'm at the point of total frustration. I've only been using Linux now for about a year and I would rather not reinstall Winblows at ANY cost, so if I can't fix this problem I might be out of luck, or have to switch to another Distro or something.

ANY suggestions or ideas are welcome and appreciated.

Thanks in advance,
besser

---

### Post by besseriym on 2008-10-05
Nobody ? Really...?

Bummer. :(

---

### Post by besseriym on 2008-10-16
HELP! lol...problem still exists and it's reeeeeeeeally annoying.

---

