---
title: "How do I find the device Id?"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by CrazyTn on 2007-03-01
I am trying to find the device ID to my Pro/wireless 3945ABG
so I can link it to the driver I installed using ndiswrapper.

The guide I was using shows how to find the id using lsusb, but that didnt work for me
because my Pro/wireless is internal.

Any tips would be much appreciated

---

### Post by erkki70 on 2007-03-01
Hi,
What's the output of:
```
lspci
```?

---

### Post by CrazyTn on 2007-03-01
> **erkki70 said:**
> Hi,
What's the output of:
```
lspci
```?
Thanks thats what I needed.

This is the guide I am using [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29)
I used lspci 
which showed 

```
 
lspci
.......
......
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
 
```
then lspci -n
```

lspci -n
...
...
0b:00.0 0280: 8086:4222 (rev 02)

```
using the 8086:4222 to link correct?

But I think I have another problem.
When I run 
```

sudo ndiswrapper -i w39n51.inf
Installing w39n51......

```

The guide said I should get this output or something similar:
installing w39n51...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

So I don't know what I am doing wrong

---

### Post by JonnyTrombone on 2007-03-01
When you run
```

sudo ndiswrapper -i w39n51.inf

```
What does it say? Does it just hang with "installing w39n51" ?

---

### Post by CrazyTn on 2007-03-01
just installing w39n51 .....
name@name$

Just installing ... then it is done
and goes back to me@host

---

### Post by JonnyTrombone on 2007-03-01
Try ```
ndiswrapper -l
```

And since I'm guessing that the driver you want to use isn't just in /, you may want to give ndiswrapper the full filepath when you use ndiswrapper -i.

---

### Post by CrazyTn on 2007-03-01
This is what I typed

[code]
crazytn@CrazyTn:~/Desktop/driver/Drivers$ sudo ndiswrapper -i /home/crazytn/Desktop/driver/Drivers/w39n51.inf 
installing w39n51 ...
crazytn@CrazyTn:~/Desktop/driver/Dri[vers$ 
/code]

I used the full directory and still came out to be the same

---

### Post by JonnyTrombone on 2007-03-01
Try this: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by CrazyTn on 2007-03-01
I am trying a new way

[http://ipw3945.sourceforge.net/INSTALL](http://ipw3945.sourceforge.net/INSTALL)

But again at a dead end

```

% tar xzvf ipw3945-1.1.3.tgz
	% cd ipw3945-1.1.3
	% make

```

getting ths error
```

/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
crazytn@CrazyTn:~/Desktop/Wireless/ipw3945-1.2.0$ sudo make
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1

```

Being a noob, no idea what to do now.

---

