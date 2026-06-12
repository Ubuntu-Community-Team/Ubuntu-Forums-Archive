---
title: "Ubuntu on an external hard drive"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by Ronnicus on 2010-02-08
I just bought an external hard drive and I want to install Ubuntu on it, because there's really no room in my primary HDD. Is that possible? Would that decrease performance or something? What's the best way to partition Ubuntu given my situation?

Thanks

---

### Post by mbzn on 2010-02-08
USB? (Really slow)
e-SATA is fine.
You should install the bootloader(grub) on the internal drive, or you can set your bios to boot from external first.

Partitioning  / = 10G
           swap = 2G
          /home = The rest
If you want Grub on the internal

hda +/- 100Meg shouls be fine and mount to /boot

---

### Post by sgosnell on 2010-02-08
I don't quite agree with this.  You need more room for /, if it's available.  Installing packages eats up storage space.  Put GRUB on the external HDD, not on the internal drive.  If you put it on the internal drive, you won't be able to boot without having the external drive connected, and you can't boot on any other computer.  Put it on the USB drive, and you can then use it to boot on any computer. Make a separate partition for /home.  USB will be a little slower than SATA, but not painfully slow.

---

### Post by karmic-koala on 2010-02-08
I do not think running Ubuntu (or for that matter any operating system) from an external hard drive is a good idea. I run several operating system in a virtual environment from my external drive and get very poor performance when the OS makes extensive read/writes.

I have a 1TB drive and get a maximum of 15 MB/s write speed.

---

### Post by tea for one on 2010-02-08
> **Ronnicus said:**
> I just bought an external hard drive and I want to install Ubuntu on it, because there's really no room in my primary HDD. Is that possible? Would that decrease performance or something? What's the best way to partition Ubuntu given my situation?

Thanks

You can install Ubuntu on an external drive. I would allow 20GB for /, and approx 50GB for /home.

Allow Grub to install on the external HDD assuming you can change your BIOS to boot from USB.

If you cannot boot from USB, you may wish to consider creating a live Ubuntu and a Boot CD from these instructions:-

[http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/#more-2681](http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/#more-2681)

Best wishes

---

### Post by mikechant on 2010-02-08
karmic-koala said:

> I have a 1TB drive and get a maximum of 15 MB/s write speed.

I know some people don't get anything near the maximum speed; however it is possible to get up to nearly 50Mb/s write speed (I've measured both my external drives getting around this figure, rsync to an empty filesystem).

---

### Post by Ronnicus on 2010-02-08
I freed up some space on my internal drive, since the previous posts have said that the performance is greatly reduced by running Ubuntu from an external hard drive. However, I only have maybe 30 gb on the internal,and nearly 400 gb on my external. What would be the best way to partition the drive now?

Thanks

---

### Post by mikechant on 2010-02-09
30Gb is plenty enough for a normal Ubuntu install as long as you store all your 'large' data collections (loads of music track, videos, iso files etc.) on a seperate data partition on the external drive or in the NTFS partitions.
If you have 2Gb of RAM, I'd suggest 10Gb for / (root), 18Gb for /home and 2Gb for swap**

** typical swap sizes:
If RAM less than 2Gb, swap=2*RAM size
If RAM greater than or equal to 2Gb swap=RAM size

If you don't want to use the hibernate feature and have more than 2Gb RAM you don't really need any swap at all

You can get away with less than 10Gb for / but you might run out of space if you installed lots of applications. I would strongly recommend not going below 6Gb.

---

### Post by raymondh on 2010-02-09
Just my .02 worth of thoughts:

I would still put Ubuntu in the external, and making sure (in step 7 of the install process) that I put GRUB2 in the external as well.  You do that by clicking the advanced button in step 7.  My only concern would be to mount/unmount the external properly prior to any shutdown

If OP now wishes to install in internal, 30gb is more than enough (as already mentioned) for as long as OP recognizes that amount when OP starts 'saving' media (or large) files.  However, I would keep Ubuntu all within root (/) and not separate /home ... considering the original space (30gb).

-  You can always save large, media files in the external and mount it so that it be recognized immediately.
-  you can always 'save' your existing apps/packages in a safe place so that should you need to re-install ubuntu (which does not take long), you can also reinstall those packages back.  The format (in terminal) would be ...

```
dpkg --get-selections > package_list
cat package_list | sudo dpkg --set-selections && sudo apt-get dselect-upgrade
```


-  30gb .... specially with all the free apps out there, OP may soon run out of root (/) space.

Just my thoughts.

Raymond

---

### Post by Jefferythewind on 2010-02-09
I would say use that external HDD for storage, free up some internal HDD space and install ubuntu on the internal.  I think running Ubuntu from the USB drive would create a big bottle-neck, and probably be the same as using a live USB.

---

### Post by Jefferythewind on 2010-02-09
Once you remove files from your internal HD to free up some space, you can use GParted to re-size the partition. leave about 15GB of "free space" for Ubuntu.  Since you have such a big external HD, I think you should back up all your files there before messing with GParted, just to be safe.

---

### Post by DZ* on 2010-02-09
I use Ubuntu on an external drive. I simply did a full install on it.
It's a casual use install (for web browsing, email, LaTeX). 
I don't really notice that it is being sluggish.
Start of programs like firefox (after a power on) is quicker than that
from a full-encrypted internal disc install, although the write test
(below) shows a slower speed.

Write speeds
Command
```
/usr/bin/time -p -o /dev/stdout sh -c "dd if=/dev/zero of=ddfile.junk count=40000 bs=8k && sync" | grep real | awk '{print 328/$2}'
```


Internal Momentus 7200.2 SATA 160-GB Laptop Hard Drive (ST9160823ASG)
Full disk encryption (LUKS): 43 Mb/s

Internal Barracuda 7200.8 250-GB (ST3250823A)
Unencrypted: 66 Mb/s
Encrypted home (ecryptfs): 38 Mb/s

External (USB) WD 329 Gb "Passport" with Ubuntu 9.10
Unencrypted: 20 Mb/s
Encrypted home (ecryptfs): 21 Mb/s

---

### Post by raymondh on 2010-02-09
> **DZ* said:**
> 
It's a casual use install (for web browsing, email, LaTeX). 
I don't really notice that it is being sluggish.


+ 1.  I myself have not noticed sluggishness for as long as usage is for browsing, email, chat.  Quite minimal.

Raymond

---

### Post by Ronnicus on 2010-02-09
Sorry, this is a really beginnerish question, but if I partition Ubuntu during installation, how would I manually set up the partitions in order to specify the sizes? How would I choose which drive to install on (internal vs. external)?

I've read many partition guides on the forums, but none of them have been really pertinent to my situation. Can anyone give me some help on this?

---

### Post by sgosnell on 2010-02-10
Just run the install program from the LiveCD, and it will take care of the partitioning.  You can specify your own preferences or let the installer decide.  It also lets you choose which drives to use for what.  Once you see it, it's very intuitive, not difficult at all.  If you have doubts, run the installer, and then exit it before you click the final Forward button.

---

### Post by jeffery6803 on 2011-02-02
i also use ubuntu on a external ide harddrive compared to xp it`s great as you can only install hacked versions of a ms os on a external harddrive  and it becomes very slow and really unusable for anything other than web browsing as it will easily eat up 1gb of ram when viewing flash video(i`m still talking about xp) ubuntu on the other hand is still very usable peaking at about 256mb of ram i play alien-arena and savage2 and see no noticeable lag now understand you are giving up performance as internal is faster and the amount of ram you need should at least be 1gb to 2gb to offset the performance decline tried running with 512mb of ram and while this was usable lag increased  i consider 256 mb of ram in this configuration unusable esata is better than usb i`m using usb on a external ide harddrive 
doom3 playable no lag
wic playable no lag (wine)
ROTk11 no lag (wine)
movavi video converter no lag (wine)
openarena playable no lag 

laptop specs are very modest
Tecra S2 pentium M 770 2.13 ghz 1.5 gb ram  Go6600 gpu  128mb

---

