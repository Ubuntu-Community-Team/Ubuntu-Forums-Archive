---
title: "Installing WN511B wireless card"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by trethomil on 2009-12-17
Hi, I am starting this thread as an alternative to my other thread about 0% wireless connection.

I have downloaded and unpacked the driver for a WN511B wireless card from Netgear.

I got as far as this instruction in the README: (lsmod  | grep "b43\|ssb\|wl") and started being told I didn't have permission to do what I was trying to do.

This is what the Terminal showed after I tried to follow the subsequent instructions:

   b43                   122136  0 
  ssb                    35300  1 b43
  led_class               4096  2 b43,rt2x00lib
  mac80211              181236  3 b43,rt2x00pci,rt2x00lib
  cfg80211               93052  3 b43,rt2x00lib,mac80211
  jane@jane-laptop:~/hybrid_wl$ rmmod b43
  ERROR: Removing 'b43': Operation not permitted
  jane@jane-laptop:~/hybrid_wl$ rmmod ssb
  ERROR: Module ssb is in use by b43
  jane@jane-laptop:~/hybrid_wl$ echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
  bash: /etc/modprobe.d/blacklist.conf: Permission denied
  jane@jane-laptop:~/hybrid_wl$ echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
  bash: /etc/modprobe.d/blacklist.conf: Permission denied
  jane@jane-laptop:~/hybrid_wl$ modprobe lib80211
  FATAL: Error inserting lib80211 (/lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko): Operation not permitted
  jane@jane-laptop:~/hybrid_wl$ rmmod wl
  ERROR: Module wl does not exist in /proc/modules
  jane@jane-laptop:~/hybrid_wl$ insmod wl.ko
  insmod: error inserting 'wl.ko': -1 Operation not permitted
  
Any ideas how to fix this?

All help will be most appreciated!

---

### Post by anewguy on 2009-12-17
For each of the commands that returned a permissions error, preface the command with "sudo ", example:

sudo rmmod b43
sudo rmmod ssb
sudo echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
sudo echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
sudo modprobe lib80211
sudo rmmod wl *this will probably still say module doesn't exist)
sudo insmod wl.ko

Dave :)

---

### Post by trethomil on 2009-12-18
That worked! Marvellous. Thanks very much for your help.

Well, most of it worked, even putting sudo in front of the blacklist commands told me I hadn't the correct permission. Does this matter?

---

### Post by anewguy on 2009-12-19
If your wireless is working now then it's okay, otherwise, you have just run into something I have had happen since going to 9.10 that I don't know the work around for (well. I do, but it involves enabling the root login, and we try to avoid that with beginners whenever possible).  I have done a few "sudo" commands that give permission errors in 9.10 as well, when they aren't supposed to. 

Post back first and let me know if your wireless is working.  If not, I'll private message you with some instructions.

Dave :)

---

