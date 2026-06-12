---
title: "Problems with one partition! I CANT SEE IT!"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by slcsfinest801 on 2011-03-05
Hi everyone!
I just switched completely to Ubuntu 10.10 and I love it!
However I have a problem that I can't figure out.

When I installed Ubuntu on my laptop my computer already had 3 partitions. 
Partition dev/SDA1: 10gb, I used it as Swap
Partition dev/SDA2: 150gb, I used it to install Ubuntu OS, in "/" and its a EXT3
Partition dev/SDA3: 150gb, I didn't use it, it's a EXT3 and it's placed in /home

My problem is that from the file manager I can't see, or better, access partition SDA3. I kept it cause I wanted to just use it as a "data folder" but I can't access it. When I had windows I was able to see C: and D: as two separate partitions, both accessible.

How can I fix it? I tried everything I could think, its 3 days that I look on guides online and I find nothing! :) 

Let me know!

Thanks so much!

---

### Post by sandy8925 on 2011-03-05
I think it's because sda3 is mounted under /home. In that case, you are able to access it siince you can access your home directory. Also, I recommend using ext4.

---

### Post by Old *ix Geek on 2011-03-06
> **slcsfinest801 said:**
> When I installed Ubuntu on my laptop my computer already had 3 partitions. 
Partition dev/SDA1: 10gb, I used it as Swap
Partition dev/SDA2: 150gb, I used it to install Ubuntu OS, in "/" and its a EXT3
Partition dev/SDA3: 150gb, I didn't use it, it's a EXT3 and it's placed in /homeYes, you *DID* use it. You're logged in, aren't you? Then you're using that partition, as that's where your user directories are, in /home/your_user_name.
> My problem is that from the file manager I can't see, or better, access partition SDA3.Yes, you are accessing it. See above. :)
> I kept it cause I wanted to just use it as a "data folder" but I can't access it.See above.
> When I had windows I was able to see C: and D: as two separate partitions, both accessible.You need to lose the goofy windoze way of looking at things! Linux is intelligent. It sees partitions as branches on its file system tree, so unless you're really TRYING to see them as separate partitions, you'll normally just see them as directories.
> How can I fix it?There's nothing to fix. Do the following so you can see what's happening, okay?

From a command line (in a terminal), type the following and then post the output so we can see it:
```
mount
```

Do you see a line like:
```
/dev/sda3 on /home type ext3 (rw)
```

From within whatever file manager you're using, navigate to / and tell me if you see "home" listed under it. Yes? Perfect!

By the way, your partitioning scheme is really off--in my humble opinion, of course. ;) Giving 150GB for the OS is completely unnecessary, and by doing so you're losing tons of space you could use for file storage. Also, the 10GB swap space is pretty small. If you're so inclined, you might want to just start over--backing up any important files first--and re-do your partitioning scheme. I'd go with 30GB or LESS for /, about 30GB for swap, and I'd personally split the remainder into two more partitions, one for /home and I always do one for /data.

---

### Post by Dutch70 on 2011-03-06
She's right, you need to rethink you're partition scheme, you're wasting a lot of Gigs.
Old *ix Geek, please explain the 30GB swap recommendation. :confused:

 I have 4GB of RAM & 4GB/swap which acts like a pagefile in windows. Mine never gets used at all, even when I try to bog down my system by running 3-4 OS's with virtualbox. It didn't even get used when I only had 2GB of RAM & a 2GB swap file. 

15-20 GB for "/" (root) 
swap equal to your physical RAM if you want to hibernate.
the rest for /home.

Don't take my word for it. Google it for yourself.

---

### Post by Old *ix Geek on 2011-03-06
> **Dutch70 said:**
> He's rightShe. :D

---

### Post by Dutch70 on 2011-03-06
> **Old *ix Geek said:**
> She. :D

LOL...fixed & I do apologize. :)

---

### Post by Old *ix Geek on 2011-03-06
> **Dutch70 said:**
> LOL...fixed & I do apologize. :)It's all good. :D (It's a common mistake, too. Back in the Stone Age...er, the mid-1980s, when I started programming and administering UNIX systems, I was in a VERY small minority of females in the field. I liked that, though!)

---

### Post by Old *ix Geek on 2011-03-06
> **Dutch70 said:**
> Old *ix Geek, please explain the 30GB swap recommendation. :confused:I don't use any of the common methods of figuring out how much space to allocate to swap. I base it on total disk space--and 2.5 decades of experience. :eek: The OP apparently has 310GB of total space available; allocating 30GB for / (which is actually a lot more than necessary), 30GB for swap, and about 125GB each for /home and /data (or whatever they want to call the additional partition) should give them a nicely functioning system.

---

### Post by srs5694 on 2011-03-06
You can find out how your partitions are currently mounted (or *if* they're currently mounted) with "df", as in:

```

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/nessus-g_root
                       6291260   1404344   4886916  23% /
udev                     10240       408      9832   4% /dev
/dev/sda2               199797     59815    129667  32% /boot
/dev/mapper/nessus-g_usr
                      20970876   7683188  13287688  37% /usr
/dev/mapper/nessus-home
                     104854396  72126132  32728264  69% /home
shm                    1899008         0   1899008   0% /dev/shm
```

This example is from a system that uses Logical Volume Manager (LVM), so the only partition that's mounted directly is /boot (/dev/sda2). There are also some non-partition filesystems mounted -- udev and shm. You can ignore them. If your /dev/sda3 is being mounted at /home, you should see an entry for that. If you don't see such an entry, then you may need to adjust /etc/fstab -- but before you do that, you'll need to move files around. Post back if you have questions about that.

---

### Post by Old *ix Geek on 2011-03-06
> **srs5694 said:**
> If your /dev/sda3 is being mounted at /home, you should see an entry for that. If you don't see such an entry...They're using their computer--so they're clearly logging in, which means they're using their /home partition. :)

The OP doesn't understand how *nix displays its partitions as normal looking directories under root.

---

### Post by srs5694 on 2011-03-06
> **Old *ix Geek said:**
> They're using their computer--so they're clearly logging in, which means they're using their /home partition. :)

Correction: A /home *directory* (and a user's home directory within that) exists. Whether that's a separate partition or just a directory on the root (/) partition is another matter. The original post seems to indicate that /home is a separate partition, but verifying this will do no harm; and on the off chance that the partition intended to be /home is *not* so configured, learning that fact sooner is better than learning it later.

---

### Post by Old *ix Geek on 2011-03-06
> **Old *ix Geek said:**
> They're using their computer--so they're clearly logging in, which means they're using their /home partition. :)

The OP doesn't understand how *nix displays its partitions as normal looking directories under root.

> **srs5694 said:**
> Correction: A /home *directory* (and a user's home directory within that) exists. Whether that's a separate partition or just a directory on the root (/) partition is another matter. The original post seems to indicate that /home is a separate partition, but verifying this will do no harm; and on the off chance that the partition intended to be /home is *not* so configured, learning that fact sooner is better than learning it later.You're correct that verifying the situation will do no harm. However, from the OP's OP, it's pretty clear how the installation went:
> When I installed Ubuntu on my laptop my computer already had 3 partitions.
Partition dev/SDA1: 10gb, I used it as Swap
Partition dev/SDA2: 150gb, I used it to install Ubuntu OS, in "/" and its a EXT3
**Partition dev/SDA3**: 150gb, I didn't use it, it's a EXT3 and it's **placed in /home**
It's also clear, to me, that as a *nix newbie s/he is WHOLLY unlikely to have taken it upon themselves to manually create a /home directory and then populate it with users. I don't think so!

---

### Post by srs5694 on 2011-03-06
> **Old *ix Geek said:**
> You're correct that verifying the situation will do no harm. However, from the OP's OP, it's pretty clear how the installation went:
> When I installed Ubuntu on my laptop my computer already had 3 partitions.
Partition dev/SDA1: 10gb, I used it as Swap
Partition dev/SDA2: 150gb, I used it to install Ubuntu OS, in "/" and its a EXT3
**Partition dev/SDA3**: 150gb, I didn't use it, it's a EXT3 and it's **placed in /home**
It's also clear, to me, that as a *nix newbie s/he is WHOLLY unlikely to have taken it upon themselves to manually create a /home directory and then populate it with users. I don't think so!

That's why I said that the original post "seems to indicate" this configuration. The trouble is that, in my experience, newbies often think they're doing one thing when in fact they're doing something else. In this case, clicking the wrong button, accidentally selecting the wrong option, or various other mistakes during installation could create a configuration that's at odds with what the OP stated, leaving the OP's beliefs and the real world out of sync. Since the original post is based on the OP's beliefs, that leaves some uncertainty about the state of the real world.

I'd like to emphasize that I have no specific reason to think that the system is not configured as presented initially in this particular case. Confirming it by typing a simple command is, however, worth doing.

---

### Post by slcsfinest801 on 2011-03-07
Hi guys thanks for your help, I ended up reinstalling everything and repartitioning the disk correctly following your directions, now everything seems making more sense! :)

Thanks!!

P.S. I read on different forums and articles that if I use Ubuntu I won't need any antivirus software as long as I don't use ubuntu as a root user all the time, is this true?

---

### Post by Dutch70 on 2011-03-07
> **slcsfinest801 said:**
> Hi guys thanks for your help, I ended up reinstalling everything and repartitioning the disk correctly following your directions, now everything seems making more sense! :)

Thanks!!

P.S. I read on different forums and articles that if I use Ubuntu I won't need any antivirus software as long as I don't use ubuntu as a root user all the time, is this true?

That is very much true, see here....
[[COLOR="Blue"]&#8220;Why GNU/Linux Viruses are fairly uncommon&#8221; from Charlie Harvey[/COLOR]]("http://www.gnu.org/fun/jokes/evilmalware.html")

Of course that is a joke, but there are no Linux virus' currently in the wild. The only reason you may want to run an AV, is if you xfer files to a windows based machine. Even then, you only need to run a scan before you move a file. (nothing built for windows, runs on linux) see .exe, ...it just won't work.

In other words, you can have an infected file on Ubuntu, but Ubuntu would be immune. If you xfer that file to a windows based machine, windows would pick up the virus, but imho, that's why you keep an AV on your windows machine. I've been running Ubuntu for nearly 3yrs. and I wouldn't dream of putting any kind of AV on it to save windows, let windows save itself. :)

Having a strong password is the best thing you can do to protect your system.

Doing your banking from a live cd/usb is the best way to protect such critical info.

---

### Post by srs5694 on 2011-03-07
> **slcsfinest801 said:**
> P.S. I read on different forums and articles that if I use Ubuntu I won't need any antivirus software as long as I don't use ubuntu as a root user all the time, is this true?

Linux security issues aren't the same as those for Windows. In Windows, viruses are fairly common, just because of the nature of the Windows security model and the way Windows users tend to use their computers. In Linux, viruses are rare (I'm not aware of any "in the wild," although I've heard of proof-of-concept viruses being written but never released). Linux's security model makes it harder -- but not impossible -- for viruses to propagate, and Linux is most dominant as a server platform, so it's not used as much in the ways that virus writers rely on, and when it is used that way, the numbers are small enough to make Linux a less appealing platform. (Many of the people posting here use Ubuntu as a desktop platform; but that's not very relevant, since it's the overall "ecosystem" that renders Linux viruses not worth writing for the people who write them for Windows.)

Traditionally, Unix and Linux security issues relate to vulnerabilities being found in servers and used by outsiders or local users exploiting local security problems. Such attacks don't usually propagate in a virus-like fashion, but in many respects they're similar -- both result in a system that's no longer fully under the control of the person who owns the hardware. To minimize your risk of being compromised, you need to keep your system from running unnecessary servers and ensure your software is kept up to date. Putting it behind a NAT router also makes sense. I know of one tool, [chkrootkit,](http://www.chkrootkit.org/) that scans a Linux system for signs of intrusion that are often left behind by attackers. I've also heard of a Linux anti-virus tool, but my limited understanding is that it's intended for use on file servers and scans for Windows viruses.

Running as root vs. as an ordinary user has some effect on security, in that if you do run everything as root, any malicious software you're tricked into running will be able to do more harm than if you were running as an ordinary user. IMHO, though, an equally or more important reason to not run as root any more than is necessary is that it's far too easy to accidentally trash your system if you make a mistake as root. For instance, you could easily delete critical program files or libraries as root, but not as an ordinary user. Many Linux commands provide very little in the way of idiot-proofing; they rely on the security system and the competence of administrators to keep things safe. If you remove the security system from the picture by running everything as root, then sooner or later you'll slip up and do a lot of damage. (Note that the "sudo" command runs things as root, so you should be cautious when using sudo.)

Finally, Windows viruses can propagate on Linux systems if you run Windows in a virtual machine or if you run the virus in WINE. Of course, running Windows in a virtual machine means you're running Windows, so that goes back to being a Windows issue. WINE is another matter, though. I'm not sure how many viruses can run in WINE, and of course a Windows virus running in WINE is unlikely to be able to do any damage to the bulk of the Linux installation; but it can do damage to your WINE installation, and depending on what the virus does, it could do damage outside of your system. For instance, in theory such a virus could serve to turn your system into an attack device on a botnet, to perform distributed denial of service (DDoS) attacks against innocent parties. In theory, such a virus could be just as effective when run via WINE as when run in Windows. I don't know how well most viruses run in WINE, though -- it's possible that most of them just don't run properly. Also, your risks of infection are lower because you might not run the programs that the virus authors rely on to get themselves onto computers in the first place. For instance, if a virus spreads by exploiting a vulnerability in a Windows e-mail client, you can't be infected unless you run that Windows e-mail client via WINE.

---

### Post by Old *ix Geek on 2011-03-08
> **slcsfinest801 said:**
> Hi guys thanks for your help, I ended up reinstalling everything and repartitioning the disk correctly following your directions, now everything seems making more sense! :)Great to hear things are looking good now. :D
> P.S. I read on different forums and articles that if I use Ubuntu I won't need any antivirus software as long as I don't use ubuntu as a root user all the time, is this true?In addition to the excellent replies by Dutch and srs5694, I want to point out that due to its UNIX history, Linux is inherently safer than windows. UNIX was built from the ground up with the idea of being multitasking, multi-user, networked, stable and secure. Its file system and its ownership/permission scheme are what keep it safe. Even if a normal user's account got hacked, even if dangerous files were allowed in, they cannot bring down the SYSTEM, they can only affect that user. This is why it's so very important that root/superuser access be reserved for only the most necessary functions. Don't ever log in as root and stay that way!

(Okay, I'll admit something...I've done that MANY times over the years. But my first experience with UNIX was as a programmer and sysadmin, and most of what I needed to do when getting that system up and running involved being root. So I got used to being logged in as root and thought nothing of it--and never screwed up. Most people probably can't claim that, as it's just too easy to accidentally--and irrevocably--delete or damage system files. Even though I can, and occasionally do, log in as root now, I just prefer to stick with my normal user account. Less stress!)

Anyway, spend as little time as necessary running root privileged functions and you should be fine.

---

### Post by slcsfinest801 on 2011-03-08
Awesome!
Thank you for the great explanation! Very very very good! I'm impressed :) thank you guys!

---

