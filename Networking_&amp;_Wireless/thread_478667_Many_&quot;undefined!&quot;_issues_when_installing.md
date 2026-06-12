---
title: "Many &quot;undefined!&quot; issues when installing ipw3945."
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by Rudy246 on 2007-06-19
Hello all.

I seem to be having a minor issue with installing the drivers for my Intel(R) PRO/Wireless 3945ABG Network Connection card. 

I just installed Ubuntu yesterday, but waited until today to start working on getting connected to the internet. I'm currently hooked up to my router via ethernet cable so that I may download packages and whatnot to aid in my installing. 

I've just finished installing IEEE80211-1.2.17 and have begun installing ipw3945-1.2.0.

Upon entering the following steps from the INSTALL.TXT instructions, I received many "Warning!!!...is undefined!" errors in the terminal.

Instructions:
```
Once the ieee80211 subsystem is installed, we build the ipw3945.ko module:

	% tar xzvf ipw3945-1.2.0.tgz
	% cd ipw3945-1.2.0
	% make
```

Errors given after entering commands into the terminal:
```
rudy@rudy-laptop:~$ cd ipw3945-1.2.0
rudy@rudy-laptop:~/ipw3945-1.2.0$ make
 Using ieee80211 subsystem version API v2 from:

        Base: /lib/modules/2.6.15-28-386/build/
        Path: /lib/modules/2.6.15-28-386/build/include/

 EXTRA_CFLAGS = -DIPW3945_COMPAT=2 -g -Wa,-adhlms=check_inc.lst

mkdir -p /home/rudy/ipw3945-1.2.0/tmp/.tmp_versions
make -C /lib/modules/2.6.15-28-386/build M=/home/rudy/ipw3945-1.2.0 MODVERDIR=/h ome/rudy/ipw3945-1.2.0/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-28-386'
  CC [M]  /home/rudy/ipw3945-1.2.0/ipw3945.o
  Building modules, stage 2.
  MODPOST
*** Warning: "free_ieee80211" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined!
*** Warning: "alloc_ieee80211" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined!
*** Warning: "ieee80211_wx_get_encodeext" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined!
*** Warning: "ieee80211_wx_set_encodeext" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined!
*** Warning: "ieee80211_wx_get_encode" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] und efined!
*** Warning: "ieee80211_wx_set_encode" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] und efined!
*** Warning: "ieee80211_wx_get_scan" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undef ined!
*** Warning: "ieee80211_freq_to_channel" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] u ndefined!
*** Warning: "ieee80211_rx_mgt" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined!
*** Warning: "ieee80211_rx" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined!
*** Warning: "ieee80211_channel_to_index" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined!
*** Warning: "escape_essid" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined!
*** Warning: "ieee80211_txb_free" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefine d!
*** Warning: "ieee80211_is_valid_channel" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined!
*** Warning: "ieee80211_set_geo" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined !
*** Warning: "ieee80211_tx_frame" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefine d!
*** Warning: "ieee80211_get_channel_flags" [/home/rudy/ipw3945-1.2.0/ipw3945.ko]  undefined!
*** Warning: "ieee80211_get_channel" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undef ined!
*** Warning: "ieee80211_get_geo" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined !
  CC      /home/rudy/ipw3945-1.2.0/ipw3945.mod.o
  LD [M]  /home/rudy/ipw3945-1.2.0/ipw3945.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28-386'
rudy@rudy-laptop:~/ipw3945-1.2.0$ *** Warning: "free_ieee80211" [/home/rudy/ipw3945-1.2.0/ipw3945.ko] undefined!
bash: CHANGES: command not found

```

It seems as though everything is running smoothly until it begins building modules in stage 2. Also, the final line of the command, saying, "bash: CHANGES: command not found," leads me to believe that I need to download a package with the command for change. Could that be the error?

I found a similar error on this website: 
[http://www.bughost.org/pipermail/ipw-bugs/2006-June/000006.html](http://www.bughost.org/pipermail/ipw-bugs/2006-June/000006.html)
It's not the exact same problem, but it is similar.

Any help is greatly appreciated. The sooner I can get wifi to work on this laptop, the sooner I can unplug this ethernet cable and start using Ubuntu regularly. 

Side note: I have an i386 system. I'm not sure if that's a piece of valuable information, but I thought I'd post it just in case.

Thank you for your time, I look forward to any responses.
-Rudy

---

### Post by Rudy246 on 2007-06-20
I think I may have resolved the problem, but I may still need help.

I reinstalled a few things and now it seems to install without error.

```
rudy@rudy-laptop:~$ cd ipw3945-1.2.0
rudy@rudy-laptop:~/ipw3945-1.2.0$ make
 Using ieee80211 subsystem version API v1 from:

        Base: /lib/modules/2.6.15-28-386/build/
        Path: /lib/modules/2.6.15-28-386/build/include/

 EXTRA_CFLAGS = -DIPW3945_COMPAT=1 -g -Wa,-adhlms=check_inc.lst

mkdir -p /home/rudy/ipw3945-1.2.0/tmp/.tmp_versions
make -C /lib/modules/2.6.15-28-386/build M=/home/rudy/ipw3945-1.2.0 MODVERDIR=/home/rudy/ipw3945-1.2.0/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-28-386'
  CC [M]  /home/rudy/ipw3945-1.2.0/ipw3945.o
  Building modules, stage 2.
  MODPOST
  CC      /home/rudy/ipw3945-1.2.0/ipw3945.mod.o
  LD [M]  /home/rudy/ipw3945-1.2.0/ipw3945.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28-386'
rudy@rudy-laptop:~/ipw3945-1.2.0$

```

The next step in the instructions is:

```
Now we install the firmware files (first finding where to install them):

	% wget http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.14.2.tgz .
	% DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" \
		/etc/hotplug/firmware.agent)
	% tar xzvf ipw3945-ucode-1.14.2.tgz 
	% less ipw3945-ucode-1.14.2/LICENSE.ipw3945-ucode
	# cp ipw3945-ucode-1.14.2/ipw3945.ucode $DIR

NOTE:  'DIR' above typically works out to /lib/firmware.
```

Yet when I try to perform the second command (beginning with "DIR=," the terminal gives me this:

```
rudy@rudy-laptop:~/ipw3945-1.2.0$ DIR=$(sed -ne "s:^FIRMWARE_DIR=\([^, ]*\).*:\1:p" \
> /etc/hotplug/firmware.agent)
sed: can't read /etc/hotplug/firmware.agent: No such file or directory
rudy@rudy-laptop:~/ipw3945-1.2.0$

```

Can anyone offer advice as to how to create the required folder?
I read in another thread that someone copied their ipw3945.ucode file to lib/firmware to fix this problem, but my file is already there. 

-Rudy

---

### Post by Rudy246 on 2007-06-20
I think I've gotten past the problem again, but I'm still running into problems.

The next step in the installation process states:

```
Now we obtain the regulatory daemon:

	% wget http://bughost.org/ipw3945/daemon/ipw3945d-1.7.22.tgz .
	% tar xzvf ipw3945d-1.7.22.tgz
	% less ipw3945d-1.7.22/LICENSE.ipw3945d

Depending on your architecture perform one of the following	

For 32-bit systems:

	# cp ipw3945d-1.7.22/x86/ipw3945d /sbin

or for 64-bit systems:

	# cp ipw3945d-1.7.22/x86_64/ipw3945d /sbin

And now we can try to load the module, first clearing the kernel log:

	# ./load debug=0

Finally we can check to see if things worked:
0
	# iwconfig eth1
```

The problem happens when it says, 
"And now we can try to load the module, first clearing the kernel log:

	# ./load debug=0"

I wasn't sure what directory I was supposed to be in when I typed that in, so I just went back into the ipw3945-1.2.0 directory and did it. Unfortunately, I received error messages.
```
root@rudy-laptop:/home/rudy/ipw3945-1.2.0# ./load debug=0
No modules unloaded.
FATAL: Module ieee80211 not found.
insmod: error inserting './ipw3945.ko': -1 Unknown symbol in module
Load failed.
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-06-20 17:28:49: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection
..done.

```

The line "FATAL: Module ieee80211 not found" is alarming, since I thought I had installed it correctly. 

Also, I tried typing iwconfig eth1, but I found out that my eth1 connection has disappeared. Can anyone offer advice as to how to fix these problems?

-Rudy

---

