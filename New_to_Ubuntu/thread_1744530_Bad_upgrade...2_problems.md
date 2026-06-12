---
title: "Bad upgrade...2 problems"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Norm24 on 2011-04-30
Was upgrading from Maverick to Natty and all went well till the end when a window popped up saying Grub-PC being configured and it just seized up,computer completely froze and I had to do a hard restart.Once restarted grub showed both my windows and ubuntu installs.Grub can't load Ubuntu but it does windows.This is my first problem.

My second is I'm a complete moron and I forgot to back up home.How do I recover data from my Ubuntu partition?

I do have a livecd.

---

### Post by jiggajoe506 on 2011-04-30
I would also like to know how to do a complete recovery to start fresh like it was my first time using.

---

### Post by oldfred on 2011-04-30
@Norm24

Use liveCD and backup /home is my first suggestion. You never can have enough backups and a problem always happens just before you do you next backup that you had been putting off for too long (I know from experience:)).

Have you tried recovery mode? Can you then boot to command line as recovery from that is easier than having to chroot from liveCD and then running recovery.

drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
kansasnoob- full chroot one line version with &&----
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)


#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
Commands once in chroot:
if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

@jiggajoe506
If you have nothing to save and/or have backed up everything, just do a install. Choose manual/advanced and reuse existing / partition. Do not reformat /home if you have one. Otherwise review the many instructions on installing.
One site with lots of detail/not as complex as it may look:
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by axi.torvalds on 2011-04-30
> **Norm24 said:**
> Was upgrading from Maverick to Natty and all went well till the end when a window popped up saying Grub-PC being configured and it just seized up,computer completely froze and I had to do a hard restart.Once restarted grub showed both my windows and ubuntu installs.Grub can't load Ubuntu but it does windows.This is my first problem.

My second is I'm a complete moron and I forgot to back up home.How do I recover data from my Ubuntu partition?

I do have a livecd.
If your home folder is not encrypted you can boot using the live CD try Ubuntu and then you can access all partitions including the Ubuntu partition you will find your home folder in /home

---

### Post by Norm24 on 2011-05-01
Not sure what happened after I backed up /home using the livecd I tried booting into recovery mode and was able to.I didn't do anything.

So I restarted and there was a new entry in my grub menu named "previous versions" so I clicked that there were two entries so I clicked on the kernal entry and Ubuntu loaded no problem.For the heck of it I used update manager and was given the option for a partial upgrade and I did so.The upgrade to Natty was completed and here I am!

Like I said I don't know what I did but I'll mark this as solved!

---

