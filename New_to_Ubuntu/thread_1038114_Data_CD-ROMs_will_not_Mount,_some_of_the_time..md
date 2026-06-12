---
title: "Data CD-ROMs will not Mount, some of the time."
date: 2009-01-12
forum: New to Ubuntu
---

### Post by urbandryad on 2009-01-12
EDIT: I just checked and BOTH laptops run 8.10 Ubuntu, so its not a problem with 8.10

I have a whole collection of backups I've made over the years on various windows systems, with various windows programs. I'm not going over the little quibbles over which programs I used to burn them. This archive goes back at least 6 years.

So anyways some of my CDs will mount, some will not, some will run once, then won't run, but will run again with much reloading and trying to force the disk to eject.

If the CD doesn't mount the CD-ROM will not let me eject it until after several tries.

I asked in the IRC channel about this and was told this was a windows compatibility issue.

I JUST loaded these CDs into my old laptop, with Ubuntu 8.10 and the CD-ROM detects these CDs just fine.

There are two culprits then that I can see: My CD-ROM drive has a driver or hardware issue at the heart of it.



I would love some help. In the IRC channel people seemed quick to blame and bash Windows, but some of these may have been made in Ubuntu Dapper Drake, or Windows 2000, XP or Vista.

Thanks guys.

---

### Post by LowSky on 2009-01-12
CD-R sdo not last forever. usually ony a few years 2-3 max life if you but the cheap ones. If you need to do archiving Tape drives and Backup hard drives are better mediums.

[http://en.wikipedia.org/wiki/CD-R](http://en.wikipedia.org/wiki/CD-R)

Also how would your CD-ROM drive have a driver issue?

I'm not blaming windows, because It could  be a number of things. Anytime a Drive has ahad time reading a drive it could be potentially many issues.

---

### Post by urbandryad on 2009-01-12
The IRC Guys have been trying to work me through the problems. The old CDs I don't care about anymore and don't mind, but now we've discovered a problem with newer CDs and DVDs being burned. 

I put dmesg in a terminal and this is the output, Imagine it repeated over and over and over again and thats what happens when I'm trying to load one of the CD or DVD data CDs. Keep in mind these CDs WORK in my other laptop, which has Ubuntu 8.10

[http://paste.ubuntu.com/104049/](http://paste.ubuntu.com/104049/)

We tried burning a DVD with Brasero and the burn stopped with an error at the end of the burning that  told me that it could not mount the disk: 

(scroll to the end) [http://paste.ubuntu.com/104063/](http://paste.ubuntu.com/104063/)

A recent DVD burn from a Vista OS works, but an older CD does not. One CD did eventually load, after a lot of tries, and I managed to copy the content from that to my desktop, and I'm glad I did because it will not load again.

This is really frustrating since I've never had trouble with these CDs before.

---

### Post by kestrel1 on 2009-01-12
To me it sounds very much like a hardware problem. If the disc's load fine on one machine, but not on the other I would be changing the CD drive.
There is no way that this is any sort of computability problem from Windows to Linux.
I have many years of CD's & these are fine on my machines.
I have had times when CD's or DVD's wouldn't mount & it is normally down to the hardware or the disc itself. If you can get a CD/DVD drive cleaner you could try that, as dust on the CD's laser head could cause problems.
If newer disc's mount each time it could be down to the older disc's not being of a good quality & have degraded slightly & the drive that wont normally read them having a dirty head would also affect things.
Anyway, my suggestion would be try to clean the drives laser with a good cleaner or change the drive.

---

### Post by urbandryad on 2009-01-18
It can't be a hardware problem, the drive WORKS under Vista!

I've made a bug for it in the bug reporter thing, nobody has looked at it yet but at least the bug is up there. :( I don't think I can remove the CD drive on this laptop either. Music and factory burned CDs work so I dunno. I just dunno.

---

### Post by kestrel1 on 2009-01-19
Sorry, didn't realize that you had this on a dual boot machine.

---

### Post by urbandryad on 2009-01-19
Not a dual boot anymore, I put Ubuntu on it and the errors occur. While vista was on it no errors occurred. I could burn, get my files from my backups, without any problem.

Maybe there's a proprietary driver that Ubuntu's repository doesn't know about that i NEED. Where would I go to look for that?

---

### Post by kestrel1 on 2009-01-19
You shouldn't need proprietary drivers for a CD/DVD drive, it should just work.
It is always possible that the firmware for the drive is out of date & Ubuntu doesn't recognize it correctly, but I doubt that.
How long ago did you have Vista on the machine?
With the symptoms that you are describing, the first thing I would do is swap out the drive to make sure it isn't faulty. Drives can go faulty for no reason & at the drop of a hat.

---

### Post by yeats on 2009-01-19
I had this problem under Kubuntu 8.10 and it is NOT a hardware problem, since the CD/DVD drive works perfectly under my fresh reinstall of Kubuntu Hardy.  I found Intrepid to be quite buggy in ways like this . . .

---

### Post by urbandryad on 2009-01-19
> **kestrel1 said:**
> You shouldn't need proprietary drivers for a CD/DVD drive, it should just work.
It is always possible that the firmware for the drive is out of date & Ubuntu doesn't recognize it correctly, but I doubt that.
How long ago did you have Vista on the machine?
With the symptoms that you are describing, the first thing I would do is swap out the drive to make sure it isn't faulty. Drives can go faulty for no reason & at the drop of a hat.

Its a laptop so I can't swap out the drive.

I had vista on this machine in early December, its been no more than a month.

---

### Post by kestrel1 on 2009-01-19
I must admit, I have never come across this when installing Intrepid. It does look like a bug then.
I wonder if the age of the firmware or the make of the drive is playing an important roll in this bug. Of course I could always be wrong, as it looks like I was wrong about the hardware fault :)
What make & model is the Laptop?

EDIT:
Just had a thought. Would you be willing to try Ubuntu 8.04 LTS. This may fix it.

---

### Post by egalvan on 2009-01-19
> **urbandryad said:**
> Its a laptop so I can't swap out the drive.


What make and model of laptop?

I admit, some are more difficult to swap, but this is *almost *always possible.

What most folks ( and some repair techs ) don't realize is that most all laptop optical drives are a standard size, with a standard connector.
Each manufacturer then puts their own mounting rail and/or connector system around this core.

It can get fiddly, but almost are are possible.

ErnestG

---

### Post by nepmit on 2009-01-19
I just came across this thread. I'm confused is it only data cds that won't mount or any cd or dvd? I had a problem with Hardy and Ibex. Sometimes the drives mounted but would not mount later.

---

### Post by kestrel1 on 2009-01-19
> **egalvan said:**
> What make and model of laptop?

I admit, some are more difficult to swap, but this is *almost *always possible.

What most folks ( and some repair techs ) don't realize is that most all laptop optical drives are a standard size, with a standard connector.
Each manufacturer then puts their own mounting rail and/or connector system around this core.

It can get fiddly, but almost are are possible.

ErnestG
This is very true, Often all you need to do is remove the caddy that the drive is in & use another drive in it's place. Sometimes the front face plate requires changing but this is normally easy. I have done this a few times now.

---

### Post by urbandryad on 2009-01-20
Ah, so many replies to give! I'll do them all in one post to save a bit of time and space.


> **kestrel1 said:**
> I must admit, I have never come across this when installing Intrepid. It does look like a bug then.
I wonder if the age of the firmware or the make of the drive is playing an important roll in this bug. Of course I could always be wrong, as it looks like I was wrong about the hardware fault :)
What make & model is the Laptop?

EDIT:
Just had a thought. Would you be willing to try Ubuntu 8.04 LTS. This may fix it.


The hardware is only 3 months old, I don't want to go to all the hassle of sending it back since the hardware still all works with the Operating System it came with, so I can't claim its not working properly with -windows-.

Its an Acer Extensa 4630z, I got it from Best Buy with a special price reduction, they were clearing out computers. It came without any Vista CDs so I had to get Vista myself, and I chose to download it, (I know this is wrong, but I had vista on my laptop for about a month before putting ubuntu on) therefore this burned OS CD would not work after Ubuntu was installed. Ubuntu was a burned CD, and it boots from the startus. All OS CDs seem capable of mounting and booting from startup. I can put the vista CD in this drive and it will NOT mount. But music CDs and the Ubuntu CD will mount. DVDs mount, they will not playback with any considerable proper resolution, but most of my DVDs have some sort of protection so VLC would have problems with that.

I have these burned CDs, and the latest burned CD I made in vista will sometimes mount, and sometimes not mount. Other older CDs just will not mount. It can't be the CD because the CDs work in my other laptop USING Ubuntu 8.10. Its just this laptop. I think its not a hardware problem, since burning and mounting CDs worked with Vista.

Thats the situation with which CDs can and can't mount. I can rip music CDs easy, but not BURNED music CDs. I unfortunately discovered this, and I have 8GBs of music backed up and now I can't use any of it. Back to buying CDs I guess until I can be sure I can make a backup that works. :(

Sigh, or buy an external HD

> **nepmit said:**
> I just came across this thread. I'm confused is it only data cds that won't mount or any cd or dvd? I had a problem with Hardy and Ibex. Sometimes the drives mounted but would not mount later.

Its only Data CDs that I've seen. DVDs have trouble loading, but I'm blaming the copy protection for that, not the drive.

> **egalvan said:**
> What make and model of laptop?

I admit, some are more difficult to swap, but this is *almost *always possible.

What most folks ( and some repair techs ) don't realize is that most all laptop optical drives are a standard size, with a standard connector.
Each manufacturer then puts their own mounting rail and/or connector system around this core.

It can get fiddly, but almost are are possible.

ErnestG

Do you have a link for places that can show me how to do this, and where to buy a replacement drive? :( Could I harvest the drive from my thinkpad or will I need one specifically for acer laptops?

Thank you everybody for all the help. I may just run the ubuntu live CD and see if data CDs work then, if they do it may be a fault with the installation. If not then who knows. :(


EDIT: FORGOT TO MENTION! 8.04 LST would NOT work on this laptop! Or rather, video would not work, so I could not install 8.04. But 8.10 Wubi worked in Vista for a month so I burned the 8.10 CD and that worked well. This is newer hardware so I'm guessing its not supported yet in 8.04 but more supported in 8.10. Maybe the next Ubuntu will fix the CD problem!

---

### Post by kestrel1 on 2009-01-20
You could always get an external USB CD drive instead of messing with the internal one.
The old Dell Inspiron D600 had removable Floppy & CD drives & they had mini USB ports for use with a cable. This was a very useful feature. Shame they don't do this in new machines. Obviously not floppy drives now though.

---

### Post by nepmit on 2009-01-20
I went back and reread your first post.Very similar to the problem I had. I didn't see if you're running 64bit system? I won't go into all the things I tried but I tried them all. When you type into a terminal sudo lshw -C disk, what is the output? Do this when the disk won't mount. If you get other than a complete description of your disks go here.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) (Copy and paste.) Add:noapic=off per the instructions. Besure it's at the end of the proper line.I add to both places to make it permenent. No problems sense. If this doesn't help just reverse.

---

### Post by urbandryad on 2009-01-20
> **nepmit said:**
> I went back and reread your first post.Very similar to the problem I had. I didn't see if you're running 64bit system? I won't go into all the things I tried but I tried them all. When you type into a terminal sudo lshw -C disk, what is the output? Do this when the disk won't mount. If you get other than a complete description of your disks go here.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) (Copy and paste.) Add:noapic=off per the instructions. Besure it's at the end of the proper line.I add to both places to make it permenent. No problems sense. If this doesn't help just reverse.

This is what I got.

>   *-disk                  
       description: ATA Disk
       product: Hitachi HTS54251
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: BB2O
       serial: 080517BB6200WBK48LYG
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=5423f069
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-L633A
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: AC00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       size: 16MiB (16MB)
       capabilities: partitioned partitioned:dos
       configuration: signature=2080f435


I didn't do the steps you said because it shows my CD-ROM drive and everything. Should I try the steps you pointed to?

---

### Post by nepmit on 2009-01-20
If you ran that command after a disk failure,I mean you put in a disk and no icon appeared on the desktop it just spun and stopped, than it probably will not help. If that is not the case, try the fix. You can always reverse the process.You need to figure out if it's a burn problem or a hardware problem. If you have a factory disk,not a system disk, does it mount and play every time? When you're working with a burned disk you really don't know if it's the burn or the hardware. If a factory disk plays every time it probably is a burn issue.
Re: an earlier post I believe dvds should play regardless of the copy protection, if all the codecs are installed. Just can't copy them.

---

### Post by egalvan on 2009-01-20
> **urbandryad said:**
> Its an Acer Extensa 4630z, 


Do you have a link for places that can show me how to do this, and where to buy a replacement drive? :(
 Could I harvest the drive from my thinkpad or will I need one specifically for acer laptops?

I'm not famillar with Acer, but the Thinkpads have a good forum:

forum.thinkpads.com

you can find info on the thinkpad-specific optical drives...

basically, the two diffenreces you will find are;

1) the face-plate... size, shape, color and location of led, button and hole
these can sometimes be swapped out, or you can leave it if you don't mind the aesthetics...
 I have a T23 with a Sony DVD-DL burner taken from a Dell, it has a silver face plate with a curve. Looks funky, but it works.


2) the thickness... there are two basic thicknesses. T40 and T60 for instance use a thinner core. The older T2x models used a thicker core.

Most laptops use the thicker core.

everything else is just held on with screws or tabs...

Some Sony laptops had a rather complicated cage with eject mechanism...

Another laptop I worked on (don't remember the make) only had a thin guide on one side, two screws and it was swapped.

Since Thinkpads tend to use swappable (easy-to-eject) optic drive, you should be able to hold it up to your Acer to see if the thickness is right,
 and if you need/want to change the face-plate.

Removing the drive from your Acer may be easy or hard...
totally depends on how it is mounted.

If your Acer uses the thicker model, then you will have a world of options, these are easy to find on eBay for instance.
 I try to buy these from the store-type vendors, and get a new one... versus some cast-off that may or may not work.
 Though the thinkpad forum may yield some better bargains on a DVD-reader drive ( I have gotten two).
Or even a single-layer DVD-burner, since most folks want dual-layer these days.
 You need to subscribe to buy/sell, but you can peruse without.
Or post a WTB (Want-To-Buy) describing what you are looking for.

And finally, your non-working music cd burns,,, may have been burned at too high a speed.
there is a Windows-based program called Exact Audio Copy (EAC) that *may* be able to read them. It's worth a try.

[http://www.exactaudiocopy.de/](http://www.exactaudiocopy.de/)

---

### Post by urbandryad on 2009-01-21
Just realized: if I'm running a live CD, I CAN'T test the CD-ROM drive. XD

---

### Post by urbandryad on 2009-01-22
> **nepmit said:**
> I went back and reread your first post.Very similar to the problem I had. I didn't see if you're running 64bit system? I won't go into all the things I tried but I tried them all. When you type into a terminal sudo lshw -C disk, what is the output? Do this when the disk won't mount. If you get other than a complete description of your disks go here.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) (Copy and paste.) Add:noapic=off per the instructions. Besure it's at the end of the proper line.I add to both places to make it permenent. No problems sense. If this doesn't help just reverse.

I did the steps in the URL and it didn't work. The CDs still won't load. Now the CD I burned in vista that had been loading is not loading anymore. I wonder maybe this IS a hardware problem. From birth. It works in Vista not in Linux and maybe I can't change that. I should just get an external.

But that drives me insane. I paid for this hardware it should work!

---

### Post by kestrel1 on 2009-01-22
Do you know anyone who may have an external CD drive that you could try?
Maybe, your local computer shop might be willing to let you try one before you buy it if you take your lappy with you.

---

### Post by urbandryad on 2009-01-23
All right. Reinstalling Ubuntu did not fix the problem, and the CD-ROMs do work outside of the Ubuntu desktop environment, in boot and in Windows. So it must be a configuration or missing driver or drive information. Where do I go in terminal to get/edit my CD drive information? Maybe it needs something simple, like a manufacturers name. :/

---

### Post by egalvan on 2009-01-23
> **urbandryad said:**
> I wonder maybe this IS a hardware problem. From birth. **It works in Vista not in Linux and maybe I can't change that. **I should just get an external.

But that drives me insane. I paid for this hardware it should work!

Yes, sadly enough, there is hardware that is designed and built with only Microsoft in mind.

anybody else here remember Mandrake's problems with badly-programmed CD drives that were being zombied?


But have you checked on how difficult it would be to have the optical drive changed out?

---

### Post by kestrel1 on 2009-01-23
urbandryad:
Have you looked at this: [http://tech.bluesmoon.info/2008/12/installing-linux-on-acer-extensa-4630z.html](http://tech.bluesmoon.info/2008/12/installing-linux-on-acer-extensa-4630z.html)
Nothing mentioned about the CD drive, but plenty of other problems with this particular laptop.
It could be that egalvan is correct with what he has said.

---

### Post by urbandryad on 2009-01-23
> **egalvan said:**
> 

But have you checked on how difficult it would be to have the optical drive changed out?

I turned my laptop over, and there don't appear to be any screws or a plate in order to remove the CD-ROM. I'll have to check the acer site and see what I can find in terms of documentation.

---

### Post by kestrel1 on 2009-01-24
There may only be one screw holding the drive in. I have several laptops that I have to service etc. & with some there is a single screw under one of the covers that allows removal of the drive. Sometimes these are security type screws (often star drive)

---

### Post by urbandryad on 2009-01-29
UPDATE:

My boyfriend, a bit of Linux user himself and better with terminal commands, found a work around that'll let me mount my CDs, but wont' let me burn.

First I have to make a folder. Then use the terminal code he gave me:

 sudo mount /dev/scd0 /mnt/<new folder name

This mounts the CD-ROM to that folder, so that I can copy and explore the contents. He says there's an error with the automount. Does this help with finding a solution to my problem?

At least I have a workaround to access my files, even if I can't burn a CD.

---

