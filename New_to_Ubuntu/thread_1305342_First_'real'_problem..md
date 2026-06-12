---
title: "First 'real' problem."
date: 2009-10-29
forum: New to Ubuntu
---

### Post by Captain Kremmen on 2009-10-29
OK.. told you I'd be back :)

So I installed on a new partition, eveything seemed to go ok, but when installation was complete and I booted into Ubuntu for the first time.. it didn't go anywhere :/.. selected it from the grub boot loader, and all I get is a black screen and no HD activity.....so what am I doing wrong?

BTW it's the first time I've come across a request for 'mount point' so I chose '/' from the pull down is this ok?

... also didn't really understand about chosing the drive for a swap area (and didn't want to mess anything up by chosing wrongly) so I installed without one.. is this ok? (or is this causing the black screen?)

Looks like I'll be here for a while :/.. lol

---

### Post by coolbrook on 2009-10-29
You chose the right mount point but it's possible that the partition isn't bootable.  There's probably an easier workaround but you can always run through installation again.  The swap file should be around twice the amount of RAM you have installed and its partition is /swap.

---

### Post by Captain Kremmen on 2009-10-29
Hmm.. I chose primary partition when given a choice between creating a primary or logical... any ideas why the partition wouldn't be bootable?

As for the swap area, how would I create one? creating the boot drive and selecting a place for the swap area seem to be two separate tasks and I don't seem to see a way to have them both on the same drive. (or do I just want to do something silly?)

Believe it or not... I'm not as technically inept as I'm coming across, I do know my way around tech.. but even this simple operation on Ubuntu is causing problems :/

---

### Post by Pogeymanz on 2009-10-29
Don't worry about swap for now; it's unrelated to your problem.

As for your boot problem. I assume you also have some other OS on your hard drive. Try putting the Ubuntu LiveCD back in and booting from that.

Then use a program called GParted. You might have to install it since I don't think it is included by default.

You can use GParted to make the / partition bootable by right-clicking it and choosing "manage flags"

tell us if that works.

---

### Post by autocrosser on 2009-10-29
I don't think that the install guide for 9.10 is ready yet, but take a look at the one for 9.04--It will give you a much better idea ---  [https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)

---

### Post by coolbrook on 2009-10-29
^ That's a good idea.

---

### Post by autocrosser on 2009-10-29
Here is the sub-section you want to read: [https://help.ubuntu.com/9.04/installation-guide/i386/partition-sizing.html](https://help.ubuntu.com/9.04/installation-guide/i386/partition-sizing.html)

---

### Post by JBAlaska on 2009-10-29
You can only have 4 primary partitions on a drive (This includes the swap partition) if your duel booting it's possible that you will (Have) exceeded this number..

For some reason the partitioning in the install of 9.10 does not warn of this, it will go ahead and install as if nothing is wrong...but on reboot you have nothing.

Boot to the LiveCD, start gparted and see if your exceeding the 4 primary partition limit.

---

### Post by Captain Kremmen on 2009-10-30
Ok read the article, or at least the parts that even remotely applied, no luck....

Tried Gparted also no luck, though I did note that if I make my ubuntu drive 'boot', my xp drive unboots :/  I can only have one 'boot' at a time.

And as my machine only has 4 partitions total.. even if they were all primary, which is unlikely, it shouldn't be affected.

Hmmm... all this and I nearly lose my xp install into the bargain, not going very well for me is it.. :(

---

### Post by Captain Kremmen on 2009-10-30
Sorry to bump this, but the pages go by so quickly on this forum :/

---

### Post by Captain Kremmen on 2009-10-30
Hmmm :<..

All you gurus and still no solution for this.

---

### Post by cenzorrll on 2009-10-30
I'm not sure exactly why you aren't able to boot Ubuntu, what i would suggest is to make sure your partition isn't inside an extended partition. i don't believe it's possible to boot if it is.

don't worry about changing which partition has the boot flag, if it doesn't work you can always stick the cd back in and mark your xp partition as boot again. it doesn't actually mess with the partition itself, it just tells the computer what's what.

as for swap.  it's only necessary if you plan on hibernating your computer or you have very little ram (ubuntu typically uses less than 512mb, so unless your computer is 10 years old i wouldn't worry too much at the moment)

---

### Post by Captain Kremmen on 2009-10-30
Hmm... my partition isn't part of an extended partition either :/... this is becoming rather annoying :(

The boot switch doesn't actually affect my ability to boot into xp either.

and I have 2gb of ram, so I should be fine then..

...If only I could get this thing booted :<

---

### Post by 4Orbs on 2009-10-30
Did you install Ubuntu on ext3 or ext4?

---

### Post by Captain Kremmen on 2009-10-30
Ext4.. I just left it at default.

---

### Post by uberg on 2009-10-30
Don't worry about the boot flag.  That is there for Windows.  Grub and Linux don't need it to be bootable.

Don't worry about if it is a primary or extended partition.  Grub and Linux don't care one way or the other. *

Just before I replied here I installed Karmic on a partition I had previously set aside for this very purpose.  This is on an extended partition that is not flagged as bootable.  It booted up just fine.

It might help if you were to post the output of the following command:
```
sudo fdisk -l
```Did you try to boot from the LiveCD and see if you can mount the new Linux partitions from there?

As coolbrook suggested you might have to go through the install process again but post the output suggested above and let's see if we can find anything in output.

* Although, as someone already stated, you can't have more than 4 primary partitions.  This is for historical reasons I believe.  You can have as many extended partitions as you need.  The output from the code might help to clear this up.

---

### Post by Captain Kremmen on 2009-10-30
Hi.. :)

ok.. this is what I get from doing as you suggested.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
37 heads, 15 sectors/track, 1759951 cylinders
Units = cylinders of 555 * 512 = 284160 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      110703    30720075    7  HPFS/NTFS
/dev/sda2          110704      479712   102399997+   7  HPFS/NTFS
/dev/sda3          848722     1759947   252865215    7  HPFS/NTFS
/dev/sda4          479713      848719   102399442+  83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda4 /mnt/ubuntu
ubuntu@ubuntu:~$ df -h

Filesystem            Size  Used Avail Use% Mounted on
aufs                 1007M   27M  980M   3% /
udev                 1007M  296K 1007M   1% /dev
/dev/sr0              690M  690M     0 100% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                 1007M  104K 1007M   1% /dev/shm
tmpfs                1007M   12K 1007M   1% /tmp
none                 1007M   80K 1007M   1% /var/run



As you'll see it's the xp drive that is marked as boot... but I've tried it the other way and it makes no difference.

I hope this shines some light on things.

---

### Post by phillw on 2009-10-30
just a kwik btw ..... how much of your own data do you have stored on the ubuntu part of your install ?

Phill.

---

### Post by Captain Kremmen on 2009-10-30
None.. it's a clean install on a clean partition.

---

### Post by phillw on 2009-10-30
> **Captain Kremmen said:**
> None.. it's a clean install on a clean partition.

Would you mind if I got u back to a 'clean' 9.04 install ?

even though I'm on 9.10, I'm thinking it may actually be easier & quicker to get you to a standard 9.04 install, then follow my blog (in my sig).

The choice, as ever is yours.

Just a thought.

Phill.

---

### Post by Captain Kremmen on 2009-10-30
You read my mind.... just burning a copy now, will come back when it's installed.

---

### Post by phillw on 2009-10-30
> **Captain Kremmen said:**
> You read my mind.... just burning a copy now, will come back when it's installed.

Follow my blog .....

Heck, it worked for me & that's why it is there.

BACKUP your windows stuff (Documents, photos, media etc)

Use GParted to 'play' with the partitions.

Ubuntu install needs 10GB for itself (okay, so u can make it smaller ... trust me unless you're short of room)
1GB SWAP - up & untill you have 1GB RAM, there after, SWAP GB = RAM GB

If you have a lot of 'media' then ...
1) If it's on your windows area .... leave it there - ubuntu can kwik mount it at boot.
2) If you're going to be doing loads on Ubuntu & sacking windows, set up a partition called /mystuff .. some say call it /home, but I'm a bit dubious about that - I may have a couple of linux versions on my computer & sharing ~home seems a little too iffy to me.  ~home is for each version ... /mystuff is for music, docs, etc.

TBH, I still have my vista partition I actually use it as storage area for muzic, my ISO images  (Okay, I confess, I  still support windoze from 98 --> Vista for people on vpolink, Derrick is going to be looking after the Win7 people ..... But don't tell him ;-)   )

Phill.

---

### Post by Captain Kremmen on 2009-10-30
See this is what I'm not sure of.... the partition and sizing shouldn't be the problem, it getting installed on a clean 100 gb partition.... it should just go smoothly... not unless it doesn't like 'too big' :/

---

### Post by phillw on 2009-10-30
> **Captain Kremmen said:**
> See this is what I'm not sure of.... the partition and sizing shouldn't be the problem, it getting installed on a clean 100 gb partition.... it should just go smoothly... not unless it doesn't like 'too big' :/

Give me a couple of min ...

---

### Post by Captain Kremmen on 2009-10-30
Yep.. no problems with 9.04. Fired up fine and I used ext4 so it wouldn't interfere with a 9.10 upgrade.

I'll probably just have to wait for 9.10 to mature a bit before I expect a clean install from it, so in the meantime I'll just upgrade (once I get the hang of 9.04).

EDIT... ok, now to try and get my usb dsl modem to work :/

---

### Post by phillw on 2009-10-30
Jeez, either 16 hours of support, or the bottle of wine is kicking in....


Soz, I don't have your computer spec.

All I need is RAM and quantity & size of hard-drives.

Phill.

---

### Post by Captain Kremmen on 2009-10-30
ok.. 2GB ram and 1*500gb hdd in 4 partitions.... do you need partition sizes? roughly split to.. 30/100/100/200-ish.

Everything seems accessable through 9.04.

---

### Post by phillw on 2009-10-30
> **Captain Kremmen said:**
> Yep.. no problems with 9.04. Fired up fine and I used ext4 so it wouldn't interfere with a 9.10 upgrade.

I'll probably just have to wait for 9.10 to mature a bit before I expect a clean install from it, so in the meantime I'll just upgrade (once I get the hang of 9.04).

EDIT... ok, now to try and get my usb dsl modem to work :/


As i noted in my blog, my upgrade was painless. Surreal, yes, but painless.

The secret, as it is for a good meal, is preparation.

Having an idea of your computer RAM / drives, will allow me to give you an IMHO of slicing the disk(s) up.

Phill.

---

### Post by Captain Kremmen on 2009-10-30
THB.. unless it's the partition size that's stopping the install then I'm fine with keeping Ubuntu on the 100gb partiton...

---

### Post by phillw on 2009-10-30
> **Captain Kremmen said:**
> ok.. 2GB ram and 1*500gb hdd in 4 partitions.... do you need partition sizes? roughly split to.. 30/100/100/200-ish.

Everything seems accessable through 9.04.

Okies ....

windows has a problem seeing linux areas (yes, it can be sorted - but it's easier to leave windows look after it's own areas)

So, with a dual boot system ... I'd do this ....

50 GB  Windows system
50 GB Ubuntu
2 GB Swap
remainder as NTFS partition for data that can be then shared between windows and ubuntu

That'll give you plenty of room for any stuff you want to store in either system, and a shared area that both can access.

There is method in my generous allocation to the o/s for each .. it is that each can hold a backup of the other, you have to look after the data partition yourself ;)



Phill.

---

### Post by phillw on 2009-10-30
under windows, that partion would be drive D: as a rule, sometimes it comes as E:, depends on how windows sees drive letters - don't worry, once it's got the drive letter it doesn't chahge it !!!

---

### Post by phillw on 2009-10-30
> **Captain Kremmen said:**
> THB.. unless it's the partition size that's stopping the install then I'm fine with keeping Ubuntu on the 100gb partiton...


I'd like to give a clean, expandable set of partitions - I know it's a pain, but it will make any alterations in the future a lot easier.

If, at this point, you just want 'to get it working', then that's fine.

what is on what partition ?

---

### Post by Miljet on 2009-10-30
phillw, I think you are beating a dead horse. The OP has told you several times that he now has 9.04 working fine. The only problem he has now is that he has no swap partition, but that should be no problem unless he wants to hibernate since he has plenty of RAM.

---

### Post by phillw on 2009-10-30
> **Miljet said:**
> phillw, I think you are beating a dead horse. The OP has told you several times that he now has 9.04 working fine. The only problem he has now is that he has no swap partition, but that should be no problem unless he wants to hibernate since he has plenty of RAM.


Well, that proves the last entry in my blog ..... too tired... thanks :D

Phill.

---

### Post by Captain Kremmen on 2009-10-30
Well thanks everyone who who helped out..I'm up and running, gonna stick to Jackalope for a while til Koala gets ironed out.

In fact I'm writing this, my first post from Ubuntu/Firefox ..... and it only took me two hours to figure out how to install my usb dsl modem :O LMAO.

:D.. Cheers peeps... particularly Phil.. you worked hard for me mate :)

---

