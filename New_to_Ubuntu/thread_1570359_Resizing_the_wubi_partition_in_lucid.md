---
title: "Resizing the wubi partition in lucid"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by durand on 2010-09-08
Hi,

Is it possible to increase the size of an ubuntu partition installed via wubi? A friend of mine installed ubuntu this way but she needs more space. The method in the ubuntu wiki apparently doesn't work for 10.04. Is there an alternative?

Thanks!

---

### Post by Mark Phelps on 2010-09-08
See the instructions below, section 8.9:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by durand on 2010-09-08
Yeah, that method doesn't work in 10.04.

---

### Post by Mark Phelps on 2010-09-08
> **durand said:**
> Yeah, that method doesn't work in 10.04.

Sorry ... not a fan of Wubi; don't use it.  Only trying to help.

Perhaps, if you (and other Wubi users) found a way to contact the Wubi providers, they would update their sadly-out-of-date documentation.

---

### Post by durand on 2010-09-08
Thats ok, I appreciate it. I don't use wubi either but I might have to install it to see what works.

Thanks.

---

### Post by bcbc on 2010-09-08
> **durand said:**
> Thats ok, I appreciate it. I don't use wubi either but I might have to install it to see what works.

Thanks.

You can resize the root.disk. It's not strictly speaking a resize - you have to create a new bigger one and copy the data across (i.e. to make a 5GB disk 7GB, you need 7GB free space, not 2GB). It might be better to split the /home into a new virtual disk.

The problem with lvpm is that it requires grub-legacy due to the way the transfer to partition part works (or doesn't work anymore, to be precise). The resize part is fairly simple. I've just run a test on it and it works (I made my new.disk 5GB):

```
sudo -i
cd /host/ubuntu/disks
dd if=/dev/zero of=new.disk bs=1M count=5000
mkfs.ext4 -F new.disk  # use ext4 with new installs on 9.10 or later
mkdir /media/extra
mount -o loop,sync /host/ubuntu/disks/new.disk /media/extra
rsync -av --exclude '/sys/*' --exclude '/proc/*' --exclude '/host/*' --exclude '/mnt/*' --exclude '/media/*/*' --exclude '/tmp/*' --exclude '/home/*/.gvfs' --exclude '/root/.gvfs' / /media/extra
umount /media/extra
rmdir /media/extra
exit
#reboot to windows, rename root.disk to root.disk.old and new.disk to root.disk
```

Caution should be used getting someone to run commands as root or using dd and mkfs - but you could easily put it in a shell script.

---

### Post by bodhi.zazen on 2010-09-08
For the effort it takes to resize a wubi installation I suggest you go ahead and perform a standard installation, it is much easier to maintain and IMO wubi is for trial only.

---

### Post by bcbc on 2010-09-08
> **bodhi.zazen said:**
> For the effort it takes to resize a wubi installation I suggest you go ahead and perform a standard installation, it is much easier to maintain and IMO wubi is for trial only.

The user can decide what they want to do. I don't think it's a large effort - maybe because it's not in a program or script, but it's a lot less 'real' effort (and risk) than resizing partitions.

---

### Post by bodhi.zazen on 2010-09-08
> **bcbc said:**
> The user can decide what they want to do. I don't think it's a large effort - maybe because it's not in a program or script, but it's a lot less 'real' effort (and risk) than resizing partitions.

You are of course welcome to do as you wish. I think we will have to agree to disagree on this topic.

---

### Post by bcbc on 2010-09-08
> **bodhi.zazen said:**
> You are of course welcome to do as you wish. I think we will have to agree to disagree on this topic.

I can do that ;)

The way I see it, people chose wubi for a reason. They deserve help if they need it, the same as any other forum user. When they're ready, they can move on to a real install. I don't think that we need to force their hand whenever they have a problem - but sure it's a good idea to suggest it, especially if its simpler than the fix.

---

### Post by durand on 2010-09-09
Hmm, well, bcbc, thanks a lot for that! I'll tell my friend about the code but she's completely new to linux so I think it might be easier to just get her to reinstall it. I personally don't like using wubi because you're tied to windows that way. But anyway. Thanks bodhi.zazen as well :)

---

### Post by bodhi.zazen on 2010-09-09
> **bcbc said:**
> I can do that ;)

The way I see it, people chose wubi for a reason. They deserve help if they need it, the same as any other forum user. When they're ready, they can move on to a real install. I don't think that we need to force their hand whenever they have a problem - but sure it's a good idea to suggest it, especially if its simpler than the fix.

You raise a good point, I would just say we do support wubi here.

We just differ on when to advise one to do a "standard" install. I know the loop mounted file or virtual HD can be resized, but, IMO, most people who install wubi find that task to be more difficult then a standard installation.

There are many support questions that are no more or less difficult on wubi then a standard install, and in those cases wubi is supported.

---

### Post by durand on 2010-09-09
It should be pretty easy to support wubi resizes by just making a windows program to do all that.

---

### Post by bcbc on 2010-09-09
> **bodhi.zazen said:**
> You raise a good point, I would just say we do support wubi here.

We just differ on when to advise one to do a "standard" install. I know the loop mounted file or virtual HD can be resized, but, IMO, most people who install wubi find that task to be more difficult then a standard installation.

There are many support questions that are no more or less difficult on wubi then a standard install, and in those cases wubi is supported.
Yeah, after some sober second thought, I believe you're right  

Part of the problem is that tools like LVPM haven't been updated for 2 years. Resizing shouldn't be that complicated, but without a properly tested and foolproof solution, it's not worth the risk to new users. As I found out last night, it's a very time consuming, painful process to test something like this.

> **durand said:**
> It should be pretty easy to support wubi resizes by just making a windows program to do all that.

I believe the creator of Wubi proposed a windows tool that would allow the user to migrate their install to partition. It certainly makes sense to be able to do this and resizing from Windows - but I don't think any progress has been made in this regard.

---

### Post by joonjoon on 2011-03-01
Sorry to dig up old dirt, but this is the most thorough thread I've read regarding this topic. Like many others easily found on the forums, I installed 10.04 (it seemed like the thing to do) with Wubi on a basic 5 GB and after a few days it's bursting at the seems. 

So I'm just wondering if there are any updates, it being 6 months later (and me not having a clue where to start looking). 

I guess wubi is a good trial, but it also kind of sucks they make it so easy you get hooked, but if you want the real deal you need to start over and do what you didn't want to do anyway... 

*ps: if I were to install 10.04 again, would it suffice to backup my home-dir? or as there anything else/more/better I can do?*

---

### Post by bcbc on 2011-03-01
> **joonjoon said:**
> Sorry to dig up old dirt, but this is the most thorough thread I've read regarding this topic. Like many others easily found on the forums, I installed 10.04 (it seemed like the thing to do) with Wubi on a basic 5 GB and after a few days it's bursting at the seems. 

So I'm just wondering if there are any updates, it being 6 months later (and me not having a clue where to start looking). 

I guess wubi is a good trial, but it also kind of sucks they make it so easy you get hooked, but if you want the real deal you need to start over and do what you didn't want to do anyway... 

*ps: if I were to install 10.04 again, would it suffice to backup my home-dir? or as there anything else/more/better I can do?*
I wrote a script for it so you have an option if you wish... 
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

You can also migrate the wubi install to a real partition here: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by joonjoon on 2011-03-03
thanks a bunch :) will try it one of these days

---

### Post by beew on 2011-03-03
> **bcbc said:**
> The user can decide what they want to do. I don't think it's a large effort - maybe because it's not in a program or script, but it's a lot less 'real' effort (and risk) than resizing partitions.

There will be no risk if OP gets an old external hard disk and install Ubuntu on it (a full install, not a live usb) . He can get a real Ubuntu installation and try that out by booting into it without altering anything in his internal drive (while WUBI does change his Windows install, like you would by installing any Windows program) As an added bonus it is portable so it can be used with almost any machine. 

I am with Bodhi, I am no fan of WUBI, it is a diminished shawdow of the real thing that works under the limitation of Windows,

---

### Post by Trooper_Max on 2011-03-03
I'm actually very fond of Wubi/loop-mounted installs.

And it is VERY EASY to resize the disks...

Just boot up using a LiveCD (preferably Maverick, though Lucid may work as well).

Find the disk file (back it up first if you're wary).

And use the resize2fs tool from the command line on it:
[http://manpages.ubuntu.com/manpages/maverick/en/man8/resize2fs.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/resize2fs.8.html)

You may have to use the -f flag to force it to proceed on a file as opposed to a block device, but I'm not even sure this is necessary (and don't want to test it again right now).

It will often tell you to run e2fsck first to check the filesystem before doing this, so just do what it says and then you should be able to try the resize2fs command again.

It will automatically enlarge the file too, no need to use dd to append to the file or anything like that. You can also use it to shrink the disk, in which case it will automatically truncate the file too. The -M option is very handy for this to find the minimum size to shrink it down to. This is handy if you want to transfer it somewhere (and re-enlarge it later) or archive it somewhere.

I've done this numerous times, as I've been fiddling around quite a bit with loop-mounted installs on various devices lately.

Alternatively, you might even be able to do it from Windows, following this guide written for resizing casper-rw images (which are just ext3 filesystems in a file, which are overlaid over a Live CD image in order to allow changes to persist):
[http://www.pendrivelinux.com/how-to-resize-casper-rw-images/](http://www.pendrivelinux.com/how-to-resize-casper-rw-images/)

It uses a tool called TopoResize.

Hope all this helps and let me know if you have any questions! I'm quite fond of Wubi (or at least loop-mounted installs, I usually end up getting rid of all traces of the installation from Windows anyway). I love the ability to juggle partitions as files instead of repartitioning.

EDIT: Didn't notice this thread had shifted more toward the topic of migration from a Wubi/loop-mounted install to a partition-based install. For that, I've been wondering how straight dd-ing the file into a partition would differ from a normal install (I know for one you'd need to go in and edit the fstab file to no longer mount from the file). Interestingly enough, I've done the opposite of this for testing out Natty on one of my devices. I installed the alpha 2 release on to a thumb drive using the normal install method to set it up on the thumb drive just as if it were a hard drive. I then dd'ed the thumb drive's partition into a file and went in and modified the fstab file to indicate the filesystem now being loopmounted, and it works (I setup GRUB by hand), though it is not quite the same as a wubi-install (mainly in the absence of the "host" folder).

I'm also quite disappointed with the general pessimistic attitude toward Wubi installs and implications that they are not "real" installs (and maybe they aren't, depends on your definition of real, but why such pessimism?). I know it complicates things and makes things harder in terms of support, but from an idealistic sense, why should Ubuntu care so much what layers of filesystems are running under it? There are conveniences to having an install entirely housed in a file, and some users will enjoy those conveniences (I know I do, and I've run pure-Linux systems as well as Windows and hybrid multibooting systems).

~Troop

---

### Post by bodhi.zazen on 2011-03-03
> **Trooper_Max said:**
> I'm actually very fond of Wubi/loop-mounted installs.

And it is VERY EASY to resize the disks...

<clip>

~Troop

wubi is a tool and it has it's merits.

As I said to bcbc some time ago, sure it is easy for you or I to resize these disks, but wubi is targeting people who want to "try" Ubuntu without partitioning their hard drives or installing GRUB.

IMO, once the trial is over, one needs to then decide what to do in the long run.

The options are:

1. Do a standard install. It is "easy" to migrate your customizations (you can generate a list of installed packages and back up /home).

2. Learn to manage a loop mount.

Of those two options, for users new to Linux, I highly suggest #1. IMO this is the easier, less error prone, and best supported option.

If a user really wants to manage a loop mount, or if they just want to learn, go with #2.

Both options are viable, but honestly which do you think is easier for the "average" wubi user ?

So it is not a debate about what is possible, but rather what to do with wubi users in the long run.

---

### Post by Trooper_Max on 2011-03-03
> **bodhi.zazen said:**
> wubi is a tool and it has it's merits.

As I said to bcbc some time ago, sure it is easy for you or I to resize these disks, but wubi is targeting people who want to "try" Ubuntu without partitioning their hard drives or installing GRUB.

IMO, once the trial is over, one needs to then decide what to do in the long run.

The options are:

1. Do a standard install. It is "easy" to migrate your customizations (you can generate a list of installed packages and back up /home).

2. Learn to manage a loop mount.

Agreed. (and I'd even be willing to concede at this point that the "standard" install may be the better option for most users after the trial period and is certainly the better supported option at this time)

But resizing is easy now (and should have been back then, I was mainly just surprised at the difficulty of the solutions suggested - indicating there need to be better guides for this stuff, so I was just trying to get a little information out there about how to easily do this stuff, I've been considering writing a few guides based on some of my experiences)

It really is just a matter of booting a live CD/USB and then a single command to check the filesystem and then a single command to resize it. You'd probably use a live CD/USB to resize your partitions in a standard install anyway, so I don't see much difference in the level of difficulty on this point at this time, other than the lack of a graphical tool like GParted. (though an even more advanced user might just be using LVM to manage logical partitions). Overall maintenance and support may still weigh toward using a standard install though.

So I actually agree and appreciate your level-headedness on this, bodhi.zazen. :-)

~Troop

---

### Post by bodhi.zazen on 2011-03-03
> **Trooper_Max said:**
> But resizing is easy now (and should have been back then, I was mainly just surprised at the difficulty of the solutions suggested - indicating there need to be better guides for this stuff, so I was just trying to get a little information out there about how to easily do this stuff, I've been considering writing a few guides based on some of my experiences)

Post a guide or contribute to the Ubuntu wiki, I would reference such a guide.

---

### Post by bcbc on 2011-03-03
Thanks for the info Trooper_Max.

I was aware there was a dynamic resize option but thought it was less reliable. I think as long as they backup first, this seems the easiest solution.

---

