---
title: "Grub2"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by jnmjr on 2009-12-30
I have a question about Grub2 taking a very long time to load. 
When I start my computer (cold start, restart) and after the usual bios stuff, I get a black screen with GRUB LOADING, this takes well over 30 secs. before the Grub menu comes up, if there's a way to reduce this it would substantially speed-up the total time it takes Ubuntu to load. To me at least it's very annoying. THX. :(

---

### Post by Sef on 2009-12-30
What are your system specs? (especially your graphics card.)

---

### Post by philinux on 2009-12-30
> **jnmjr said:**
> I have a question about Grub2 taking a very long time to load. 
When I start my computer (cold start, restart) and after the usual bios stuff, I get a black screen with GRUB LOADING, this takes well over 30 secs. before the Grub menu comes up, if there's a way to reduce this it would substantially speed-up the total time it takes Ubuntu to load. To me at least it's very annoying. THX. :(

It has affected a few unlucky peeps.

[http://www.google.co.uk/search?q=grub2+takes+ages+to+load&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.uk/search?q=grub2+takes+ages+to+load&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by QIII on 2009-12-30
On various test machines, I have noticed a significant delay in the presentation of the GRUB2 menu when GRUB2 has been installed on an IDE drive. 

I have even noticed the same issue using an IDE drive with a SATA converter plugged into a SATA header.

SATA drives have been no problem.

Which sort of drive are you using?  Is this an older machine?

I don't think multi-booting is an issue as others have suggested, since I have one machine with four physical drives with Karmic, Vista, OpenSolaris and Lucid on separate drives.  No delay at all (although to get OpenSolaris to run I had to put an entry in 40_Custom to get it, since the os-prober doesn't find it).

I'm with Sef, by the way.  System specs are important.

---

### Post by Paqman on 2009-12-30
> **QIII said:**
> 
SATA drives have been no problem.


I've been bitten by this bug. The system has one SATA HD and one SATA SSD.

---

### Post by QIII on 2009-12-30
There seem to be enough problems to go around right now.

The latest GRUB installer doesn't make changes to the device.map, so you get a "You must start the kernel first..." error unless you make changes directly in your device.map.

But it's all fun, right?

---

### Post by jnmjr on 2009-12-30
OK, my system is older but runs great SEF,

MSI MS 6380
AMD XP2400+ 2.0 MHz 
NVidia GeForce 8400 GS
Audigy SE OEM
2 IDE drives WD 500 gig    1: XP Pro, 2: Ubuntu 9.10

So if I understand correctly there's no cure due to IDE drives?

QIII Can you expand on the device.map reply. Is it a way to quicken Grub2?? I'm verrrrrrrrrry new to Linux...:confused:

---

### Post by QIII on 2009-12-30
Unless you are running a multi-boot system, the device.map file is probably not something to worry about now.

If I have a chance this evening when I get home, I'll see if I can find some work around for the IDE drive speed issue.

It's been so long since I've used and IDE system regularly (I only do it to test stuff out so when I recommend Ubuntu to people with older machines), I can't really say for sure what I experienced in the "old days" myself.

Remember that an IDE drive can only deliver 100/133 MB/s throughput to the bus (even less on older drives), or about a third of a SATA (rev 2.0) drive.  But even still, a SATA drive gives you the menu nearly instantaneously -- maybe a second or two of latency.

Edit:  I re-read your post, and it appears you are running a dual boot system.  Are you able to boot both?  The device.map file basically says "Hey!  There are <number of> devices that you can boot from, and here are their names."  I think that as of Karmic, things worked well, so you may not have encountered this particular issue.

---

### Post by jnmjr on 2009-12-30
Yes, I dual boot, Xp and Ubuntu, both work fine, seems then device.map is not an issue, neither should drive speed, I've done some digging---see Philinux post--- and this is an unresolved  Grub2 bug. Workarounds are available, but are also capable of messing things up for an inexperienced guy like me. I'm hoping someone has a simpler solution. THX.

---

### Post by oldfred on 2009-12-30
There is a known bug in grub2 for multi drive configurations. If grub is on one drive and Ubuntu on another it goes off on a search for about 20 seconds.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

When I reinstalled grub2 to sdc and changed it to my boot drive I booted a lot faster.

---

### Post by QIII on 2009-12-30
Interesting.

I guess I'd never run into that.

When I install the dev version of Ubuntu, I always install it on something other than sda and make sure during installation to set the grub-install to happen on sda...

Will wonders never cease.

But on a particular machine that I use with IDE drives, I still get the delay even without a multi-boot.

Ah, well...

---

### Post by jnmjr on 2009-12-30
> **oldfred said:**
> There is a known bug in grub2 for multi drive configurations. If grub is on one drive and Ubuntu on another it goes off on a search for about 20 seconds.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

When I reinstalled grub2 to sdc and changed it to my boot drive I booted a lot faster.

I tried your suggestion but it seems Grub is not installing on SDB.

in my Bios  SDA=IDE-0 which is where I'm booting from now.
                                 SDB=IDE-1 which is where I tried to install Grub as per your post.
                                                                   This is the drive Ubuntu is on.

When I swichted to IDE-1 in Bios I got blank boot screen. I had to go back to IDE-0.
Maybe I did something wrong, can't say for sure. I did it a couple of times , same result.

---

### Post by oldfred on 2009-12-30
One user recently had to change all his Sata drives to be master by plugging them into certain ports. The BIOS did not support switching master & slave. I do not think you can boot a slave under old IDE setups.

---

### Post by jnmjr on 2009-12-31
So if I understand you correctly, switch SDA to Slave =SDB, make SDB Master=SDA. As far as I know there's no bootloader in new SDA, what would I have to do to install Grub2 on this drive?  THX.

---

### Post by oldfred on 2009-12-31
If you are in your working Ubuntu, this will  let you choose which drive to install grub2 to.

sudo dpkg-reconfigure grub-pc

---

### Post by jnmjr on 2010-01-01
> **oldfred said:**
> If you are in your working Ubuntu, this will  let you choose which drive to install grub2 to.

sudo dpkg-reconfigure grub-pc

THX OldFred for pointing me in the right direction, the command you posted didn't work for me but I used... sudo grub-install /dev/sdb... instead, this wrote Grub2 to SDB mbr, my BIOS allows to switch booting drives without switching cables, now Grub works the way it's supposed to. Looks like if you want to dual boot without delay, Grub2 must be installed in HD  with Ubuntu on it, if installed on HD with Windows as I had then delay occurs. I would think this bug will be fixed in a future release. THX again. :)

---

