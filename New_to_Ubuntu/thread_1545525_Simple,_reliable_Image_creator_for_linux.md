---
title: "Simple, reliable Image creator for linux"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by knightblade on 2010-08-04
Hi Ubuntians ):P

I've been looking for a simple, reliable easy to use, preferably having a GUI image creator/disc burner for ubuntu 10.04. 

So far I've heard of [LIST=1]
[*]Ghost for Linux
[*]remastersys
[*]part Image
[/LIST]

The problem is either they're command line based, unreliable or need to be burnt on a disk, boot from the disk and then create an image, which no offence, I find stupid. :D

Software should make life easier. Is there anything that you guys know of that will make this task easier? I play around with the OS a lot and eventually mess it up. I need to create one good image with all software et al set up which I can simply restore from.

Thanks!

---

### Post by pithdillinja on 2010-08-04
Brasero is the generic GUI CD/DVD burning application in ubuntu. It is installed by default in 10.04, as it has been for a while.

---

### Post by knightblade on 2010-08-04
Thanks for the reply. :)

Perhaps I should have been more clear. I need to burn an image of the hard drive/hdd partition, not an ISO. AFAIK, Brasero doesn't do this.

---

### Post by mapes12 on 2010-08-04
> I need to burn an image of the hard drive/hdd partition, not an ISO.In my experience you're not going to create an image of your HDD partition without an ISO.

Remastersys has a great GUI. Using the "dist" option works for me.

Another option is FSarchiver.

---

### Post by mike555 on 2010-08-04
" Multicd " is in package manager , I haven't tried it and don't know if it does whole partitions ..........

---

### Post by Paddy Landau on 2010-08-04
AFAIK, there is no simple GUI front-end for any of these, unless you want a paid-for version.

If I were a programmer, I'd program a front-end to [CloneZilla]("http://www.clonezilla.org/").

I use CloneZilla. It's not exactly GUI, but it does prompt you for what you need, so you don't need any command line interface (CLI) -- though CLI is available as an option.

The good thing about CloneZilla is that it's proved reliable. The bad thing is that the front-end takes a bit of getting used to. Once you're used to it, it's easy to use.

---

### Post by mike555 on 2010-08-04
You might want to try " RedoBackup " .... [http://redobackup.org/](http://redobackup.org/)

---

### Post by Paddy Landau on 2010-08-04
> **mike555 said:**
> You might want to try " RedoBackup " .... [http://redobackup.org/](http://redobackup.org/)
It looks impressive; it uses the same system as CloneZilla but with a better front-end.

Unfortunately, it locks up on my system. :(

---

### Post by knightblade on 2010-08-04
Thanks for the replies people! :-)
I'll try these out as soon as I'm back home.

---

### Post by akoskm on 2010-08-04
For creating images I'm using (d)isk (d)ump
```

man dd

```
. There is no graphical interface interface but requires only 2 input parameters - and you can type those before any GUI starts. :D
Some examples: [http://mydailyhash.wordpress.com/2009/03/12/creating-and-mounting-iso-images-in-linux-terminal]("http://mydailyhash.wordpress.com/2009/03/12/creating-and-mounting-iso-images-in-linux-terminal/").

---

### Post by ranch hand on 2010-08-04
I am not sure what it is you are trying to do exactly.  If what you want to do is copy a partition to another drive or partition on the same drive then you have the tool you need on any Live CD.

Gparted will copy very well.  As I have three or four drives I can do it from one that is not involved in the process, which you do want.  A thumb drive with an install on it would do the job.

It is as simple as right clicking on the partition you want to copy, select "copy" go to where you want to put it and right click on it and select "paste".  Sit back and enjoy the show.

The only problem that you will have is needing to go into /etc/fstab and edit the partition(s) that it is now on from the partitions it was on so that it can be booted.  This is simple in nautilus as root or, for that matter, gedit by it self.

I think you will find that you need t odo that if you use clonezilla too, which I do not use but has a very good reputation.  I just like to cut out the middle man and use gparted.

---

### Post by Paddy Landau on 2010-08-05
> **ranch hand said:**
> Gparted will copy very well.
Cool! I learn something every day!

GParted's copy function is fine if you're copying partition-to-partition, but I  don't think it's suitable for backing up partitions (correct me if I'm  wrong). I have several computers with multiple partitions, which I back up onto a single  large external hard drive.

To be clear, the programs that use [PartClone ]("http://partclone.org/")(e.g. [CloneZilla]("http://www.clonezilla.org/"), [Redobackup]("http://redobackup.org/")) all do something important:

[LIST]
[*]They back up or restore only the used portions of the disk, making them fast and reducing the size of the backup.
[*]They compress the backup, further reducing the size of the backup.
[/LIST]
I know that CloneZilla also backs up the MBR if you back up the entire disk; I don't know about the others.

---

