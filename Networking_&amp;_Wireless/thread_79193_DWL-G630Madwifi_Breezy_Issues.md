---
title: "DWL-G630/Madwifi Breezy Issues"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by firecat53 on 2005-10-19
I had my dwl-g630 working perfectly under Hoary using the Madwifi driver compiled from source. When I installed Breezy (fresh install), the whole system would lock up hard whenever the card was activated. So, I figured I'd go recompile the Madwifi drivers again. Installed build-essential and sharutils per the Madwifi directions. Also, the linux headers for 686.
Did:  
```
export KERNELPATH=/usr/src/linux-headers-2.6.12-9-686
export KERNELRELEASE=2.6.12-9-686
make
```
And got the following error(s):
```
firecat53@scotty:/usr/src/madwifi$ make
Checking if all requirements are met... ok.
mkdir -p ./symbols
for i in ./ath_hal ath_rate/sample ./net80211 ./ath; do \
        make -C $i || exit 1; \
done
make[1]: Entering directory `/usr/src/madwifi/ath_hal'
make -C /usr/src/linux-headers-2.6.12-9-686 SUBDIRS=/usr/src/madwifi/ath_hal MODVERDIR=/usr/src/madwifi/ath_hal/../symbols modules
/usr/src/linux-headers-2.6.12-9-686/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-686/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-686'
  CC [M]  /usr/src/madwifi/ath_hal/ah_osdep.o
In file included from include/asm/timex.h:10,
                 from include/linux/timex.h:61,
                 from include/linux/sched.h:11,
                 from include/linux/module.h:10,
                 from /usr/src/madwifi/ath_hal/ah_osdep.c:46:
include/asm/processor.h: In function 'load_esp0':
include/asm/processor.h:486: warning: implicit declaration of function 'unlikely'
In file included from include/linux/sched.h:12,
                 from include/linux/module.h:10,
                 from /usr/src/madwifi/ath_hal/ah_osdep.c:46:
include/linux/jiffies.h: At top level:
include/linux/jiffies.h:84: warning: type defaults to 'int' in declaration of 'u64'
include/linux/jiffies.h:84: error: syntax error before 'jiffies_64'
include/linux/jiffies.h:88: error: syntax error before 'get_jiffies_64'
include/linux/jiffies.h:88: warning: type defaults to 'int' in declaration of 'get_jiffies_64'
include/linux/jiffies.h:88: warning: data definition has no type or storage class
include/linux/jiffies.h: In function 'timespec_to_jiffies':
include/linux/jiffies.h:320: error: called object 'u64' is not a function
include/linux/jiffies.h:320: error: called object 'u64' is not a function
include/linux/jiffies.h:320: error: 'NSEC_PER_SEC' undeclared (first use in this function)
............

```

So, is there an issue with using the gcc 4.0 compiler that's standard now, or am I missing something??

Thanks, 

Scott

---

### Post by rhinomite on 2005-10-19
Hi Scott,

I'm having the same troubles with madwifi drivers in Breezy, and posted my problems on the forums the other day (See atheros 5212 post)

When I tried compiling from source as you did, I also ran into issues and suspect its the new 4.0 compiler.

The built in modules don't allow me to associate with my AP, however there are no noticable error messages... its got me stumped.

Hope we can fix this soon - other people seem to be having wierd issues as well.

---

### Post by firecat53 on 2005-10-20
In a nutshell, after finally getting the madwifi driver compiled from source, it still hangs the system as soon as I do "sudo ifconfig ath0 up " or "sudo ifup ath0".

After reading another thread regarding compiler issues, apparently the 2.6.12 kernel is compiled using gcc-3.4 (or 3.3?), so any kernel-related modules have to be compiled using the same version compiler. So I did
```
sudo apt-get install gcc-3.4
sudo vi /etc/bash.bashrc
```adding the following to the end of bash.basrc:
```
export CC=/usr/bin/gcc-3.4
```

So, it compiled and installed successfully, although I had to create new directories under /lib/modules/2.6.12-9-686/kernel/net/ called ath, ath_hal, ath_rate/amrr, and net80211/ per the madwifi INSTALL document to move the various .ko files into before I could modprobe ath_pci.

Now, iwconfig shows the wireless card ath0 and all appears normal, but when I type "sudo ifconfig ath0 up", it freezes the entire system until I remove the wireless card. Then I get the following line at the end of dmesg:
"ath0: ath_chan_set: unable to reset channel 3 (2422 MHz)"

If I try to set "sudo iwconfig ath0 channel auto" I get :
"error for wireless request "Set Frequency"(8B04): SET failed on device ath0; invalid argument."

There were a bunch of warnings when I compiled the drivers, but no errors. If anyone has an idea, I can provide those warnings as well.

Any thoughts?? I'd hate to have to go backwards to Hoary!! It was working perfectly!!

Thanks, Scott

---

### Post by firecat53 on 2005-10-21
I also found a similar issue in the madwifi wiki and did
"modprobe ath_pci xchanmode=0 "

Still no luck!

Anyone got ANY ideas???

Thanks, Scott

---

### Post by dmegg on 2005-12-02
The Breezy precompiled (restricted) ath0 driver -- which is apparently a bit old -- is working fine for me, but it seems to be sensitive to the order of commands.  Instead of ifup (which I cannot get to work), I have a script that does calls commands in this order:

iwconfig ath0 key s:XXXXX
iwconfig ath0 channel 4
iwconfig ath0 essid XXXXX
iwconfig ath0 rate auto
iwpriv ath0 authmode 2
dhclient ath0

It works every time.  I found that setting the rate to 'auto' was critical, at least for the driver version in Breezy.

---

