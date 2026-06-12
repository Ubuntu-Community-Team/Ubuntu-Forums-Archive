---
title: "The configuration defaults for Gnome Power Management  are installed incorrectly??"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by mikodo on 2010-03-15
Hello everyone,

I was trying to use

 [code] sudo cp -p -r /home /media/Backup [code] 

to copy my /home partition to a usb external HD and of course this was going to be my only backup, having deleted the contents of my previous backups from the USB HD. After running this command I noticed that I could not use Gparted or Firestarter, as I was given a warning about ?? needing root privileges or something. Sorry, I didn't read it clearly and rebooted to receive this warning:

Install problem. The configuration defaults for Gnome Power Manager have not been installed correctly. Please contact your Administrator.

I continually receive this every time I try to log in.

I am writing this in Hardy on another partition, not in my regular Karmic partition, that is now not available to me, as outlined above.

Is there an easy solution to this? It looks like I have hosed the system again!! I really didn't want to mess this one up and start again from scratch. Presumably the contents of /home are on the USB HD, just not accessible as it is formatted as Ext4 FS and Hardy uses Ext3 and cannot read it.

Thank you.

---

### Post by mikodo on 2010-03-15
A couple of other things.

1) When I was running the cp command it told me that it had troubles (My words) with /home/mikodo/.gvfs (and again my words it couldn't deal with it). I don't what that is.

2) It flashed me a screen towards the end of the copying that it was running out of disk space. Where I didn't understand as it seemed I had enough. 

3) Finding another thread similar, a responder suggested the OP had a dfgconf database that has been corrupted and requested a print out of df. Here is a print out of df from the Hardy machine. I don't know if any of this is helpful as it is from Hardy.

mikodo@mikodo-desktop:~$ 
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              9690316   3189232   6012712  35% /
varrun                 1680220       100   1680120   1% /var/run
varlock                1680220         0   1680220   0% /var/lock
udev                   1680220        84   1680136   1% /dev
devshm                 1680220        12   1680208   1% /dev/shm
lrm                    1680220     40000   1640220   3% /lib/modules/2.6.24-27-generic/volatile
/dev/sda5             15889788   3620312  11468636  24% /home
gvfs-fuse-daemon       9690316   3189232   6012712  35% /home/mikodo/.gvfs
mikodo@mikodo-desktop:~$ 

Below is a screenshot of my gparted from Hardy that shows /dev/sda7 ext 3 which is really ext4 when in Karmic and is my / partition and /dev/sda8 ext3 which is really ext4 in Karmic and is my /home partition. From that I see /dev/sda7 (/) partition is now full, where it was not before??

---

### Post by mikodo on 2010-03-15
Oh well, I am at a complete loss and do not know what I reading about and will stop here. So if anyone wants to show me the way, GREAT, if cannot, thanks for reading this far. The only solution I see is to start over again, and see if I can get my data from the USB HD when I reinstall Karmic. Oh well... if/when I'm up to it again!

 GVFS:

From Wikipedia, the free encyclopedia
Jump to: navigation, search
	Free software portal
GVFS

GVFS[1] is a replacement for GnomeVFS,[2] the GNOME Virtual File System. GVFS optionally allows supported virtual file systems to be mounted through FUSE.[3]

GVFS consists of two parts: a shared library which is loaded by applications supporting GIO and GVFS itself, a collection of daemons which communicate with each other and the GIO module over D-Bus. This moves the virtual file systems out of client processes, unlike GnomeVFS, but somewhat similar to KIO.

Supported backends include HAL integration, SFTP, FTP, WebDAV, SMB, ObexFTP, and archive mounting support (through libarchive).[4]

As of July 2009[update], 107 of 113 registered GNOME components have been ported to GIO,[5] as necessary to support GVFS URIs. For components that don't currently support GVFS URIs, the GVFS-Fuse module is used, which gives absolute paths to applications, mounted under a folder in the user's home directory.
[edit]

Thank you.

---

### Post by mikodo on 2010-03-15
Well, it has been just about a year since I started using GNU/Linux and Ubuntu. It's been fun; but da.. it takes a lot of time to learn it..

I don't have the inclination to pursue it anymore, since this latest setback.

Thank you everyone, for all the support, patience, time and effort you have afforded me this last year.

Best regards,

Mike

---

### Post by mikodo on 2010-03-16
Well, I got over my pout and reinstalled Karmic and brought my /home subdirectory from my earlier install. Everything is OK, just wish I had learned how to easily keep track of the apps and configs, so as to not have to try to remember everything. What hurts the most is my VBox setup. But that's for another day.

Thank you.

---

### Post by brucemuir on 2010-04-27
Hi.
I'm using 10.04 and I get the same problem. I think its because I was playing around with LVPM ([http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)), trying to resize my Ubuntu inside windows partition.  (I'm new to this ... sorry if this doesn't make sense). Anyway I did basically everything it said here [http://ubuntuforums.org/archive/index.php/t-980711.html](http://ubuntuforums.org/archive/index.php/t-980711.html) but nothing seemed to work.

So then I read this:
[http://ubuntuforums.org/showthread.php?t=1424976](http://ubuntuforums.org/showthread.php?t=1424976)

and it said 

"ROOT CAUSE - Ubuntu HDD (Partition on HDD) was full and therefore login  would not succeed. "

So I deleted some stuff and that fixed it..

Anyway.. after playing around with LVPM again I got the same problem, however I can't think of anything else to delete..

---

### Post by mngsailing on 2010-05-04
I am a new arrival with this problem.  Beats me why it says it is solved.

I got some messages about running out of disk space on home.  Then I gor the could not access the PID for nmbd  message.

I get a new kind of login panel, with my long name in it - says login as (short name) .

Ubuntu goes to start, but asks me to fix the default power saving configuration in Gnome.  Of course, I can't get in there, because I can't login. 

I can reach a root login, but I don't know root's password. How might root get into Gnome?  I guess I'll have to try an old install disk and reinstall. I sure am glad my home is not under / ! 

In this game you really have to be an expert to try a new release in its first six months.  

mngsailing

---

### Post by mikodo on 2010-05-05
I marked it as solved as I have have come to see that my external HD was mounting in my /root partition, hence when I ran cp for /home it filled the / partition. I have re-installed and am not getting any of the previous errors for now. I am going to correct the mount point tomorrow with the help of a professional who is going to correct other errors that I created.

Good luck with your problem, I am too new to try to help you with yours.

Mike

---

### Post by thanhquanky on 2010-06-13
I have the same problem. When I run df -h, it shows that / still has 19 G available. What is the problem with gnome-power-manager?

---

### Post by jamesisin on 2010-08-14
> **mngsailing said:**
> I can reach a root login, but I don't know root's password. How might root get into Gnome?

You can use sudo su - to get change users to root (use your password).  If you are trying to run a specific Gnome application you should use gksudo [application name].

---

