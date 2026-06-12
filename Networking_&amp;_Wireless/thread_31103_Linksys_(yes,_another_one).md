---
title: "Linksys (yes, another one)"
date: 2005-05-01
forum: Networking &amp; Wireless
---

### Post by WhirlwindMonk on 2005-05-01
I'm also having trouble getting my linksys WUSB11 802.11b usb wireless adapter to work. I'm am trying to get the drivers to install properly, but everytime I get an error. I am trying to use the atmel drivers. I get as far as the make command and this is the output I receive:
```
root@WhirlwindMonk:/home/adam/Desktop/at76c503a # make
mkdir -p .tmp_versions
cp /lib/modules/2.6.10-5-386/build/.tmp_versions/*.mod /home/adam/Desktop/at76c5 03a/.tmp_versions
cp: cannot stat `/lib/modules/2.6.10-5-386/build/.tmp_versions/*.mod': No such f ile or directory
make: [modules] Error 1 (ignored)
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/adam/Desktop/at76c503a MOD VERDIR=/home/adam/Desktop/at76c503a/.tmp_versions \
EXTRA_CFLAGS=" -DCOMPILE_FIRMWARE_INTO_DRIVER" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
CC [M]  /home/adam/Desktop/at76c503a/at76c503-i3861.o
...
...
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
```

The only problem that I can see is the No suck file or directory error when it tries to copy stuff out of the .tmp_verisons directory (which does not exist, I can't access it with the root console either, so i'm assuming it isn't hidden or anything). Can anyone help? Thanks.

---

### Post by XDevHald on 2005-05-01
[QUOTE=WhirlwindMonk]I'm also having trouble getting my linksys WUSB11 802.11b usb wireless adapter to work. I'm am trying to get the drivers to install properly, but everytime I get an error. I am trying to use the atmel drivers. I get as far as the make command and this is the output I receive:
```
root@WhirlwindMonk:/home/adam/Desktop/at76c503a # make
mkdir -p .tmp_versions
cp /lib/modules/2.6.10-5-386/build/.tmp_versions/*.mod /home/adam/Desktop/at76c5 03a/.tmp_versions
cp: cannot stat `/lib/modules/2.6.10-5-386/build/.tmp_versions/*.mod': No such f ile or directory
make: [modules] Error 1 (ignored)
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/adam/Desktop/at76c503a MOD VERDIR=/home/adam/Desktop/at76c503a/.tmp_versions \
EXTRA_CFLAGS=" -DCOMPILE_FIRMWARE_INTO_DRIVER" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
CC [M]  /home/adam/Desktop/at76c503a/at76c503-i3861.o
...
...
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
```

The only problem that I can see is the No suck file or directory error when it tries to copy stuff out of the .tmp_verisons directory (which does not exist, I can't access it with the root console either, so i'm assuming it isn't hidden or anything). Can anyone help? Thanks.[/QUOTE]
 Correct me please if I am wrong, but Linksys is not supported by Linux. I have the SAME one you have and it won't work :(

If you do get it to work, Private Message me so I can get this fixed myself :)

Hope it does get resolved though.

---

### Post by WhirlwindMonk on 2005-05-01
I have seen that some people have gotten it to work, but I'm missing something when I try what they did because I get an error. And I'm sure I'm doing everything they did because I've gone through it at least 6 times.

---

### Post by ate50eggs on 2005-05-05
[QUOTE=WhirlwindMonk]I'm also having trouble getting my linksys WUSB11 802.11b usb wireless adapter to work. I'm am trying to get the drivers to install properly, but everytime I get an error. I am trying to use the atmel drivers. I get as far as the make command and this is the output I receive:
```
root@WhirlwindMonk:/home/adam/Desktop/at76c503a # make
mkdir -p .tmp_versions
cp /lib/modules/2.6.10-5-386/build/.tmp_versions/*.mod /home/adam/Desktop/at76c5 03a/.tmp_versions
cp: cannot stat `/lib/modules/2.6.10-5-386/build/.tmp_versions/*.mod': No such f ile or directory
make: [modules] Error 1 (ignored)
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/adam/Desktop/at76c503a MOD VERDIR=/home/adam/Desktop/at76c503a/.tmp_versions \
EXTRA_CFLAGS=" -DCOMPILE_FIRMWARE_INTO_DRIVER" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
CC [M]  /home/adam/Desktop/at76c503a/at76c503-i3861.o
...
...
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
```

The only problem that I can see is the No suck file or directory error when it tries to copy stuff out of the .tmp_verisons directory (which does not exist, I can't access it with the root console either, so i'm assuming it isn't hidden or anything). Can anyone help? Thanks.[/QUOTE]
 I'm having trouble with this too. I have a WUSB11v4. I tried the instuctions here:

[http://ubuntuforums.org/showthread....ighlight=wusb11](http://ubuntuforums.org/showthread....ighlight=wusb11)

i got the same output from make as you did:
[I]
make: [modules] Error 1 (ignored)[/I]

then it seemed to complete. make install had a similar ignored error and seemed to complete, then no wireless. Has anyone resolved this yet? Is it possible that it *did* work but I just don't know the next step?

---

### Post by philipacamaniac on 2005-05-06
I had my WUSB11v2.6 working in Slackware (definitely NOT out-of-the-box; it took a lot of trial and error). That was on Linux kernel 2.4, so with Ubuntu Hoary (kernel 2.6) and a Debian-based system, we really shouldn't be having these problems.

I also have been trying it with no success. I know it is possible - the stupid card IS compatible with Linux. I'll try it again tonight and post my results.

---

### Post by LloydA on 2005-05-06
I have a Linksys wusb11. I am using Mandrake 10.1 and the WUS11 works fine. I install Ubuntu on a second computer and have yet to get the WUSB11 to work. I guess the people who got the WUSB11 to work are leaving some trivial step out and I am too ignorant to see what it is.

Anyhow it works fine under Mandrake 10.1 ...

---

### Post by philipacamaniac on 2005-05-08
Alright, I got mine working by downloading and compiling the latest CVS of the atmel drivers. However, I'm having a difficult time getting the essid and key settings to be remembered after a boot.

*posted wirelessly - yay*

---

### Post by ate50eggs on 2005-05-09
[QUOTE=philipacamaniac]Alright, I got mine working by downloading and compiling the latest CVS of the atmel drivers. However, I'm having a difficult time getting the essid and key settings to be remembered after a boot.

*posted wirelessly - yay*[/QUOTE]

what is the version number for your wusb11? a lot of people have posted about getting wusb11v2.6 to work.  I'm starting to think wusb11v4 may not be compatable.

---

### Post by philipacamaniac on 2005-05-09
Yeah sorry, I have a v2.6

We need to consolidate the current thread with this one:
[http://ubuntuforums.org/showthread.php?t=29554](http://ubuntuforums.org/showthread.php?t=29554)

---

### Post by mirza.k on 2005-11-06
UBUNTU HOARY
i need to connect my LAN via 
USB LinkSys WUSB11 v2.6
any1 success ? cause i got msg error like the other... :((
please help step by step so i can follow the instruction well :((
i have tried using ndiswrapper...
it detect but when i iwconfig scan
my linux show msg that my hardware doesnt support autodetect :((
helppppppppppppppppppppppppppppppppppppppppppppppppppppppppppppppppppp

step by step :((

---

### Post by muted on 2005-11-07
its the make file which refers to some files (i guess) which are not there...

try  this first:

```
apt-get install build-essential linux-headers-`uname -r

```
 then make again...

---

### Post by muted on 2005-11-07
[QUOTE=ate50eggs]what is the version number for your wusb11? a lot of people have posted about getting wusb11v2.6 to work.  I'm starting to think wusb11v4 may not be compatable.[/QUOTE]
yeah I made a thread about that to, i have the WUSB11v.2.4 too. I have made it work though, with the old Ubuntu, but with 5.1 it just doesn't seem to work

---

