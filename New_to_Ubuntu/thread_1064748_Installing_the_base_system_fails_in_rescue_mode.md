---
title: "Installing the base system fails in rescue mode"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2009-02-09
Hi,

  I'm trying to use Rescue mode on my Ubuntu 8.10 (alt txt) CD to restore Gnome panels which I deleted because of a mistaken understanding on my part.   :oops:

Rescue runs OK until I get to the Install the Base System step which reports:
Unable to install busybox-initramfs
Check /var/log/syslog
Fail to run chroot /target dpkg --force-depends --install var/cache/apt/archives/libc6_2.8~20080505-Oubuntu7_i386.deb

Because of this failure,  I can't complete the Rescue sequence, and now my Ubuntu 8.10 fails to boot, reporting:

modprobe: FATAL:  could not load /lib/modules/2.6.27-11-generic/modules.dep  no such file or derectory

An integrity check on my CD ROM was OK.  

I can get a root prompt when I'm in rescue mode, and I tried typing /var/log/syslog there  but it didn't display any log.

The rescue system assumes a rather greater knowledge of the filing and system structure than I posess myself as a relative newbie so I suppose it's possible that I've guessed wrong somewhere in my answers to the rescue system's setup questions.   Still,  considering my CD ROM tests OK,  I would have thought the system ought to have been able to reinstall any missing or corrupt files it encountered whilst installing the base system.  

Any suggestions or ideas how I could proceed with my rescue now?

---

### Post by Felix-the-Cat on 2009-03-14
You don't need to use a rescue CD to restore gnome panels. In fact I didn't know you could delete them all. If I were you I would save myself some time spent in the gnome configuration files for your user and just backup the user's /home folder and delete then recreate the user. It sounds like you may have a CD drive problem - it may be that it just isn't able to read quick enough. 

-Before your ubuntu boots can you choose another startup mode in GRUB by pressing ESC when prompted. If not I'd try another CD and/or drive and boot into the rescue cd and Enter Rescue mode after following all of the prompts and getting to the Select Disk (or something like that) screen. when you get to the rescue mode you'll need to know what partition your ubuntu install is on. You can do this by running "fdisk -l" and then looking for the partition that is probably the largest with a filesystem type ext3. To mount this you will do mount /dev/hd* /mnt (or it could be /dev/sd* where * is the appropriate letter). Then do chroot /mnt. Then run aptitude, to see if you have some broken dependencies. 

Let us know how this goes and we can go from there.

---

