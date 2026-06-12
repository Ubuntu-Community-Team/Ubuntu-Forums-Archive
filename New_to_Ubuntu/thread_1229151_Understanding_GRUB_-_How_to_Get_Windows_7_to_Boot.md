---
title: "Understanding GRUB - How to Get Windows 7 to Boot?"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by jfrancis on 2009-08-01
Hey folks,

I have Ubuntu as my primary OS. Prior to this, I had Vista, but I got rid of it (leaving just a small partition for it that is a restore point put there by Packard Bell).

Anyway, I just installed Windows 7 to see what the fuss was about, and of course it being Windows removed my prior GRUB. 

So I put it back - but I don't really know what I am doing :P

So now I have GRUB back, and I can boot just fine into Ubuntu (yeah!) but the boot option that I added for Windows 7 won't boot it.

Here's fdisk -l of my system:

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1045     8393931   27  Unknown
/dev/sda2            1046       19457   147894390    5  Extended
/dev/sda5            1046        2350    10482381   83  Linux
/dev/sda6            2351       13823    92156841   83  Linux
/dev/sda7           19197       19457     2096451   82  Linux swap / Solaris
/dev/sda8           13824       19196    43158591    7  HPFS/NTFS
 
```

And here's the entry I added to my GRUB:

```
title 		Windows 7
root 		(hd0,7)
makeactive
chainloader 	+1
```

What did I do wrong? :)

Thanks in advance for any help.

>J

---

### Post by LewRockwell on 2009-08-01
windoze wants to be on the first primary partition on a hard drive

you've placed it in the last partition...and an extended(logical) partition

food for thought perhaps:

[https://answers.launchpad.net/ubuntu/+source/grub/+question/19707](https://answers.launchpad.net/ubuntu/+source/grub/+question/19707)

.

---

### Post by jfrancis on 2009-08-01
> **LewRockwell said:**
> windoze wants to be on the first primary partition on a hard drive

you've placed it in the last partition...and an extended(logical) partition

food for thought perhaps:

[https://answers.launchpad.net/ubuntu/+source/grub/+question/19707](https://answers.launchpad.net/ubuntu/+source/grub/+question/19707)

.

Hey thanks for the reply.

I checked out that link - so does it mean I got to add hide and unhide commands to all boot options, or just to the windows one? Is that really all I can do, other than install windows in the primary partition? 

Thanks,

>J

---

### Post by presence1960 on 2009-08-01
windows does not have to be on the "first" primary partition of a drive. It just needs to be on a primary partition. It does not matter which partition on the drive it is on as long as it is primary. You have yours on sda8 which is a logical partition inside an extended partition- no good!

---

### Post by jfrancis on 2009-08-02
> **presence1960 said:**
> windows does not have to be on the "first" primary partition of a drive. It just needs to be on a primary partition. It does not matter which partition on the drive it is on as long as it is primary. You have yours on sda8 which is a logical partition inside an extended partition- no good!

Ah... okay thanks for this. I have no idea what to do about it, but I know why it won't work now at least.

o/

---

### Post by mikechant on 2009-08-02
The outline of what you need to do to get windows7 on a primary partition is something like:

1/ Boot from Live CD
2/ Start gparted
3/ Turn swap off (right click swap partition and select swapoff)
4/ Delete sda8
5/ Successively move sda7, sda6, sda5 up to towards the end of the disc.
6/ Move the start of sda2 up as far as it will go.
7/ Now you have space between sda1 and sda2 - you can create a new NTFS partition in this space and install windows here.

This is just an outline and I'm not very sure about what install options windows 7 allows so this may not work. It might be easier to backup to an external drive, wipe the entire internal drive and start again, installing windows first.

---

### Post by oldfred on 2009-08-02
Herman's page:
[]("hhttp://members.iinet.net.au/%7Eherman546/p22.htmlttp://")[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
shows how to dual boot win7 but says win7 installs a 1mb boot partition at the beginning of the drive.
His GRUB entry is this:
title        Windows 7 Ultimate, chainloader (on /dev/sda1)
root        (hd0,0)
savedefault
chainloader +1

(hd0,0) because of the boot partition at the beginning. I also saw someone say not to use [COLOR=DarkRed]makeactive[/COLOR] for win7 or else it will not work.

---

### Post by Mark Phelps on 2009-08-03
If you install Windows 7 to an unformatted drive, it installs two partitions, the first being a boot partition.  If you format a partition as NTFS and install Windows 7 there, it will use that partition and not create a second (boot) partition.

---

