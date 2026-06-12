---
title: "dual boot but use same home &amp; user"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by ave2 on 2010-03-23
Currently I am dual booting between ubuntu and Ultimate Edition- 
with Ubuntu I have a 10gb partition for the system files and a 156gb home partition.

now when ubuntu 10.04 comes out, I want to dual boot between ubuntu and Kubuntu- I want each distros root files to be in their own partition, but for them to share the same home directory- how difficult is this to do.

---

### Post by Daniel1994 on 2010-03-23
I'll guess you will have to create a separate home partition, and select it as home-mountpoint during the installation process of both.

BTW, you probably do know this, but you can run KDE and GNOME on the same installation(f. ex. one ubuntu with both KDE and GNOME), choosing between them on start up.

---

### Post by Paqman on 2010-03-23
> **ave2 said:**
> how difficult is this to do.

Very, very easy. I've been doing it for years.

During installation, choose manual partitioning, select the correct partition for the mount point /home, and make sure it isn't going to be formatted. Then just pick the right partitions for root and swap (these ones will be formatted).

You'll need to use seperate user accounts on the two systems. Each will end up with their own home folder (eg: /home/user1 and /home/user2)

There's no need to dual-boot just to have Ubuntu and Kubuntu on the same machine though. Just install both ubuntu-desktop and kubuntu-desktop and pick whether you want to log in to Gnome or KDE at the login screen. The only drawback of this is that since it installs all the default apps and utilities from both DEs your menus can get a little cluttered.

---

### Post by ave2 on 2010-03-23
> **Paqman said:**
> 

There's no need to dual-boot just to have Ubuntu and Kubuntu on the same machine though. Just install both ubuntu-desktop and kubuntu-desktop and pick whether you want to log in to Gnome or KDE at the login screen. The only drawback of this is that since it installs all the default apps and utilities from both DEs your menus can get a little cluttered.

Normally I like to install Ubuntu, and then a second distro to mess around with. kubuntu is the one I want to try next, because I havent tried KDE yet, but in two months I may want to format that drive and install debian, or something else- thats why I want two separate partitions.  


> **Paqman said:**
>  

You'll need to use seperate user accounts on the two systems. Each will end up with their own home folder (eg: /home/user1 and /home/user2) 

so is there no way to use the same user on both distro's 

can I use the same swap partition?

---

### Post by tom.swartz07 on 2010-03-23
> **ave2 said:**
> Normally I like to install Ubuntu, and then a second distro to mess around with. kubuntu is the one I want to try next, because I havent tried KDE yet, but in two months I may want to format that drive and install debian, or something else- thats why I want two separate partitions.  




so is there no way to use the same user on both distro's 

can I use the same swap partition?

As long as you set the partition as /home when youre installing it, it will use the same data. You just have to assure you use the EXACT same username.

and yes, you could use the same swap. Should only need 1 partition of that.

---

### Post by Ghost|BTFH on 2010-03-23
A quick down 'n dirty trick for a single user system is what I have done in the past, works quite well:

**Partitions:**
[I]/
/swap[/I]
*/home/username* -> My home directory for my username
*/home/username/music* -> Separate drive with my music
*/home/username/videos* -> Separate drive with my videos

Then I just make sure of two things - one, I NEVER-EVER-EVER select format for any of them beyond /swap and two, I make sure that *username* is the same name I use for my account.

I have fresh installed 3 generations of distros testing this out with minimal issues (usually the only issue is "hey, you don't have those themes installed anymore, so we're defaulting!" etc).

Cheers,
Ghost|BTFH

---

### Post by Paqman on 2010-03-23
> **tom.swartz07 said:**
> As long as you set the partition as /home when youre installing it, it will use the same data. You just have to assure you use the EXACT same username.


Sort of, technically it would have to be same UID. Not all distros start numbering UIDs from 1000.

I would strongly advise against using the same user account on multiple installs. While much of it would probably work fine, you're running a real risk of your config files getting completely snarled up. Different distros use different versions of the same software, and are not necessarily compatible.

> 
and yes, you could use the same swap. Should only need 1 partition of that.

The only time you'd ever want individual swaps is if you wanted the systems to be able to hibernate independently of each other.

---

### Post by Calash on 2010-03-23
For permissions you will want the same UID as well as the same name.  I have never done it this way, but I have played around with mounting a network /home folder.  Same UID. GID, and name will get you in good shape.

---

### Post by tom.swartz07 on 2010-03-23
> **Paqman said:**
> Actually no, technically it would have to be same UID. Not all distros start numbering UIDs from 1000.

I would strongly advise against using the same user account on multiple installs. While much of it would probably work fine, you're running a real risk of your config files getting completely snarled up. Different distros use different versions of the same software, and are not necessarily compatible.



The only time you'd ever want individual swaps is if you wanted the systems to be able to hibernate independently of each other.

He mentioned that he was going to use Kubuntu and Ubuntu, both which have similar config files. Granted, if it was FreeBSD or some other off the wall, then no- definitely do not use the same partition.

Thats all I meant.

---

### Post by ave2 on 2010-03-23
thanks for all the advice- this helps a lot

---

