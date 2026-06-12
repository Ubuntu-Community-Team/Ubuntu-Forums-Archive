---
title: "Itunes, C drive and me"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Major_Tom on 2009-11-25
Hi all.

I've been running 9.10 from the Live CD for a few days now, I wanted something different to Vista and this does it for me, so I should have no qualms about dual booting at the very least. I have a few key questions that I would much appreciate an answer to before I can commit to a switch.


[LIST=1]
[*]If I partition my hard disk, can I access media files on the Windows side from the Ubuntu side, or would I have to move them across?
[*]I've been trying to understand this "virtualization" malarkey, but failing. Does this mean I can run my currently installed Vista and it's programs through Ubuntu, or do I have to reinstall the whole lot for this to work?
[*]This is the big one: I am an iPhone user, and as such, must, must, must have iTunes. At the moment, this means I need to keep Vista on my machine. This isn't such a problem, but it links to Q1 & 2. Could I run iTunes virtually within Ubuntu? If not, would I be forced to rip any new music to both sides of the HDD partition to keep up to date, or is there a more elegant way around this?
[*]Is there another option I don't know about? (BTW, the iPhone is my favourite piece of consumer technology, ever. Getting rid of it is not an option.)
[/LIST]
Sorry if any of this is patently obvious, and thank you if you have any advice/links to where I can get the answers I need for myself.

---

### Post by pi.boy.travis on 2009-11-25
> **Major_Tom said:**
> Hi all.

I've been running 9.10 from the Live CD for a few days now, I wanted something different to Vista and this does it for me, so I should have no qualms about dual booting at the very least. I have a few key questions that I would much appreciate an answer to before I can commit to a switch.


[LIST=1]
[*]If I partition my hard disk, can I access media files on the Windows side from the Ubuntu side, or would I have to move them across?
[*]I've been trying to understand this "virtualization" malarkey, but failing. Does this mean I can run my currently installed Vista and it's programs through Ubuntu, or do I have to reinstall the whole lot for this to work?
[*]This is the big one: I am an iPhone user, and as such, must, must, must have iTunes. At the moment, this means I need to keep Vista on my machine. This isn't such a problem, but it links to Q1 & 2. Could I run iTunes virtually within Ubuntu? If not, would I be forced to rip any new music to both sides of the HDD partition to keep up to date, or is there a more elegant way around this?
[*]Is there another option I don't know about? (BTW, the iPhone is my favourite piece of consumer technology, ever. Getting rid of it is not an option.)
[/LIST]
Sorry if any of this is patently obvious, and thank you if you have any advice/links to where I can get the answers I need for myself.

OK, Ubuntu WILL be able to access all of your Windows files.

Virtualization is a computer in a computer.  You can run Vista within Ubuntu, but you will have to reinstall it in the virtual machine.

There are a few iPod management tools available for Ubunti, however, I recommend you keep Vista and iTunes for the time being, and use Ubuntu for everything else.

Hope this helps. . .

---

### Post by Major_Tom on 2009-11-25
Right. That's kind of what I had first thought, but I wasn't sure. I only sync once every 2 weeks, so it isn't an arduous task.

Thanks pal.

---

### Post by Lvcoyote on 2009-11-25
If you partition your HDD and load Ubuntu, then Ubuntu should see the Windows partition and allow you to mount and browse it.

As far as having to use the iPhone and its software, maybe someone else knows of a linux equivilent program, if there is not one then you obviously would need to keep a windows install.

There are a few different Virtualization software packages out there to choose from.  Here is a good tutorial on how to use virtualbox, which is one option.  The guide was written for 9.04 but I assume the process woould be the same for 9.10.
[http://www.howtoforge.com/installing-virtualbox-3.0-on-an-ubuntu-9.04-desktop](http://www.howtoforge.com/installing-virtualbox-3.0-on-an-ubuntu-9.04-desktop)

---

### Post by Major_Tom on 2009-11-25
OK then, I think I have a plan of action. Create a partition in Vista. Install Ubuntu. Get the pack that allows the media player to recognise restricted files. Mount C drive and let the good times roll!

Not sure on the etiquette on this board, should I lock this now I'm sorted out?

---

### Post by Lvcoyote on 2009-11-25
Naw, just keep the thread going.... you might be back.....LOL.  IIRC you  should be able to partition the HDD while installing Ubuntu.....

---

### Post by pi.boy.travis on 2009-11-25
> **Major_Tom said:**
> OK then, I think I have a plan of action. Create a partition in Vista. Install Ubuntu. Get the pack that allows the media player to recognise restricted files. Mount C drive and let the good times roll!

Not sure on the etiquette on this board, should I lock this now I'm sorted out?


Don't create the partition using Windows, just shrink the partition and leave the free space, it is better to let the Ubuntu installer create the partitions itself.

Once you have Ubuntu installed, install the ubuntu-restricted-extras package to get the codecs to play the media files

You don't have to lock the thread, but it would be good to mark it as [SOLVED].

EDIT: lvcoyote beat me. . .

---

### Post by Major_Tom on 2009-11-25
Wonderful. Instantly Linux has better tech support than Vista. I ****ing hate Vista.

---

