---
title: "Command"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by RemmyNumber7 on 2010-02-03
How do you get into Root from the Terminal.?   What command do you use ? Also i am getting a strange error when trying to   apt-get autoclean  it reply back in terminal 

with   E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory


also the same error with      apt-get clean


Tell me is there a set number of maintenance that you have to do after downloading and installing a new program

---

### Post by l-x-l on 2010-02-03
Do this and use your own password when prompted. I'm assuming you're the one who installed Ubuntu on your pc/laptop.

"sudo apt-get autoclean"

---

### Post by drzoo2 on 2010-02-03
> **RemmyNumber7 said:**
> How do you get into Root from the Terminal.?   What command do you use ? Also i am getting a strange error when trying to   apt-get autoclean  it reply back in terminal 

with   E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory


also the same error with      apt-get clean


Tell me is there a set number of maintenance that you have to do after downloading and installing a new program

You need to be root to use apt.
sudo apt-get <command>
To get to a root prompt use sudo su
Anytime you use sudo it will ask for YOUR password. This will be your user password.

z

---

### Post by RemmyNumber7 on 2010-02-03
thanks that did work thank you vary much

---

### Post by RemmyNumber7 on 2010-02-03
thank you for the root advice

---

### Post by RemmyNumber7 on 2010-02-03
I am about to get a new motherboard. This one that i am using is an old 866 mhz. It is not much but gets me online.My question is the new board is a 64 bit and this one is 32 bit.. 
Is there any changes that i must know between the both board as far as partition. What system requirements are needed for a swap file.For example lets say the new system has more then 1 gig of ram or more then a 100 gig hard drive.

---

### Post by drzoo2 on 2010-02-03
> **RemmyNumber7 said:**
> I am about to get a new motherboard. This one that i am using is an old 866 mhz. It is not much but gets me online.My question is the new board is a 64 bit and this one is 32 bit.. 
Is there any changes that i must know between the both board as far as partition. What system requirements are needed for a swap file.For example lets say the new system has more then 1 gig of ram or more then a 100 gig hard drive.

The swap partition is debatable. I believe it is required if you use Hibernate function as it copies your system ram to the swap. If this is the case you will need to have as much swap space as you do ram.

I have three partitions on a 250G drive. 
Swap --> 1G same as my system ram
root --> 50G
Home --> 175G

Having your home on a separate partition or drive makes upgrade easier.

I have a 64 bit computer but am running a 32bit OS. Unless you have more that 4G of RAM 64 isn't required. I'm sure more will chime in on 32 vs. 64.

---

### Post by RemmyNumber7 on 2010-02-03
How long have you been running Ubuntu? I just came from windows myself. But after running Ubuntu Linux i am never going back to windows ever.

---

### Post by RemmyNumber7 on 2010-02-03
what are those bean like objects next to everyone's name ?

---

### Post by drzoo2 on 2010-02-03
> **RemmyNumber7 said:**
> How long have you been running Ubuntu? I just came from windows myself. But after running Ubuntu Linux i am never going back to windows ever.

Since about Feisty which was version 7.10. I just upgraded from Hardy to Jaunty this month. I was going to wait until the next LTS (Lucid) but after seeing Karmic I'm not real happy with the direction it's heading. We'll see when Lucid comes out if I upgrade or Jump to a different distro. Every other Ubunut release always has seemed more like a technical testing release while they figure out all the NEW functionality.

Not sure what the beans are. Probably noob status.

---

### Post by Diametric on 2010-02-03
I also made the jump to Ubuntu and will never again use windows.  What don't you like bout Karmic?

---

### Post by lisati on 2010-02-03
> **RemmyNumber7 said:**
> what are those bean like objects next to everyone's name ?

The beans are meant to be a bit of fun, and are related to the number of posts in support sections of the forums. See here: [http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)

---

### Post by LMZKJ on 2010-02-03
Not sure what the beans are. Probably noob status.

The beans are an indicator of how many posts you have made.  The more active you are on the forum, the more beans you will have...

---

### Post by drzoo2 on 2010-02-03
> **Diametric said:**
> I also made the jump to Ubuntu and will never again use windows.  What don't you like bout Karmic?

The decision to use grub 2.
The ability to edit the boot menu.
The loss of GDM customization.
Default apps like Pidgin F-spot ect....

---

### Post by Diametric on 2010-02-03
Hmm...you got me on the use of grub 2, it threw me off also, however what about the default apps.  Don't like them, what?

---

### Post by drzoo2 on 2010-02-03
> **Diametric said:**
> Hmm...you got me on the use of grub 2, it threw me off also, however what about the default apps.  Don't like them, what?

The new messaging client still uses the Pidgin libraries. While I don't know why the decision on this was made, I don;t like finding my default apps change every distro. Just a peave that sudo apt-get install can fix.


Oh the last big issue I have. The new default search in FF is Yahoo/Bing (Microsoft). This is upcoming.

---

### Post by Diametric on 2010-02-03
> **drzoo2 said:**
> The new messaging client still uses the Pidgin libraries. While I don't know why the decision on this was made, I don;t like finding my default apps change every distro. Just a peave that sudo apt-get install can fix.


Oh the last big issue I have. The new default search in FF is Yahoo/Bing (Microsoft). This is upcoming.

Unless I'm missing something the default search is google.  However, despite that, if you find a distro that works better for you then you should use it.  I've  just come to really enjoy the Ubuntu community, despite some of the peeves that I've encountered.  Cheers, mate.

Oops, I missed "this is upcoming" - if it is, I would agree, but still go back to my thought on the Ubuntu community...

---

### Post by RemmyNumber7 on 2010-02-03
wow you have way more experience then i do. I first started with the version i am running now witch is 8.04. I like it really although there are allot of things i haven't learned about it.But i do want to thank you for your help that you gave me.

---

### Post by Diametric on 2010-02-03
> **RemmyNumber7 said:**
> wow you have way more experience then i do. I first started with the version i am running now witch is 8.04. I like it really although there are allot of things i haven't learned about it.But i do want to thank you for your help that you gave me.

Hey Remmy, glad you like Ubuntu!  Do yourself a favor and make sure you learn the command line (also called the terminal or shell etc...) it will make your experience that much more rewarding.  Good luck!

---

### Post by drzoo2 on 2010-02-03
> **Diametric said:**
> Unless I'm missing something the default search is google.  However, despite that, if you find a distro that works better for you then you should use it.  I've  just come to really enjoy the Ubuntu community, despite some of the peeves that I've encountered.  Cheers, mate.

Oops, I missed "this is upcoming" - if it is, I would agree, but still go back to my thought on the Ubuntu community...

[http://linux.slashdot.org/story/10/01/27/0118244/Ubuntu-Moves-To-Yahoo-For-Default-Firefox-Search?from=rss]("http://linux.slashdot.org/story/10/01/27/0118244/Ubuntu-Moves-To-Yahoo-For-Default-Firefox-Search?from=rss")

Read on

---

