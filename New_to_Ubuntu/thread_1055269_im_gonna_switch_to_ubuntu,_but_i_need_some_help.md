---
title: "im gonna switch to ubuntu, but i need some help"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by hyperhopper on 2009-01-30
hey guys! I just got a new computer(:KS) and its preloaded with *gulp* vista :(

i would just run a ubuntu install disc, but i want to be able to run vista inside vurtualbox in the future (only to watch instant netflix movies).

so, how do i switch to ubuntu and still be able to use the currently installed vista inside a vurtualbox?

---

### Post by Rompalle on 2009-01-30
> **hyperhopper said:**
> hey guys! I just got a new computer(:KS) and its preloaded with *gulp* vista :(

i would just run a ubuntu install disc, but i want to be able to run vista inside vurtualbox in the future (only to watch instant netflix movies).

so, how do i switch to ubuntu and still be able to use the currently installed vista inside a vurtualbox?


Your not going to get any kind of good video performance with Virtualbox. If you really want to stream Netflix to a Vista you should setup a dual boot, then just boot in Vista when you want to watch a Netflix.

You should have the install cd that came with the computer ? or it may be on another partition ? 

If you really want to conserve your install and run it in Virtualbox i suppose you could use Vmware converter to create a vmware image but your going to need another disk to save the image to.

---

### Post by agim on 2009-01-30
For a new user, def go with a dual boot.

You can shrink you're partition under vista, and then install ubuntu on the empty space. I can find the link for you (slow day :) ).

Out of curiosity, how much memory does your hard drive have?

EDIT: Here is the link to shrink Vista. After you do that, run the ubuntu liveCD and when it asks you to install, choose the option that says "Use largest continuous free space" or something to that affect.
And be sure to back up anything important. I have done dozens of dual boots for friends and myself, and never had a problem, but you never know.

[http://www.tech-recipes.com/rx/1593/vista_shrink_partition/](http://www.tech-recipes.com/rx/1593/vista_shrink_partition/)

---

### Post by hyperhopper on 2009-01-30
@%&$ 

it didnt come with an install disk.

how can i fing out if its on a different partition?

@agim, it has 250 Gigs of hard drive space! :KS good enough?

---

### Post by boof1988 on 2009-01-30
> **hyperhopper said:**
> it didnt come with an install disk.

I've never used Vista... but is there maybe an option (on the desktop or in a menu) for making a recovery CD.  If not, then there is probably a recovery partition on the drive somewhere.  If that's the case, make sure you know which partition it is so it does get lost.  Of course I have never used Vista so maybe things are way different now than when I had XP.

HTH a little.

---

### Post by agim on 2009-01-30
This is from the link I provided.

How to Shrink a Partition in Vista:
1. Press Win+R to open the run box
2. Type in diskmgmt.msc and click OK
3. Press the Continue button if you need to grant permission
4. Right-click on the partition you wish to shrink
5. Select Shrink Volume&#8230;

You have to decide how much space you want vista to take up. If you are going to use it for everything but netflix, then you can make it larger. If you think you will use Vista for more than just netflix, make it smaller.
You can shrink the vista side to as small as 50GB and still be able to keep dozens of movies. That would leave 200GB, of course, for Ubuntu. I have had Ubuntu running on as little as 5gb hard drive space, and you can even go smaller than that.

The decision is yours.


If you want to do the virtualbox thing, though, its a different process entirely.

---

### Post by hyperhopper on 2009-01-30
@ agim, and after i shrink volume i just run the ubuntu install disc?

@ boof, there is a program that burns recovery discs. should i burn some?

@ agim, thanks for your help

---

### Post by agim on 2009-01-30
No problem. Yes, after shrinking the vista partition, run the ubuntu liveCD. (If you haven't already run the livecd you should, just to check for quirky hardware, to make sure your wireless works, etc.)

When you install... and this is important... Click the option that says
"Install to the largest continuous free space" or something like that.

Very, very important.

Its step 4 or 5, I think.

---

### Post by hyperhopper on 2009-01-30
THANK YOU!, just one thing: sometimes the windows disc manager is funky, what if it screws me over somehow?

EDIT: what in the world happened the the thank you buttons! i need to press yours

---

### Post by agim on 2009-01-30
Thats why its important to backup any important info. As far as the disc manager being funky, I've never really had a problem. But I have only done around 30 dual boots with it. So thats not really a lot to go on.

---

### Post by hyperhopper on 2009-01-30
i just got the computer yesterday, the ONLY thing i did was install firefox, no info or anything on there

just curious, what field of business are you in that gave you that experience?

---

### Post by boof1988 on 2009-01-31
> **hyperhopper said:**
> @ boof, there is a program that burns recovery discs. should i burn some?

If you do not have an install CD, then it is probably a good idea.

If your windows install ever gets messed up (and you actually want to be able to use/re-install Windows), then it would be a good idea, IMHO, to have recovery disk(s) available.

---

### Post by stalkingwolf on 2009-01-31
> @ boof, there is a program that burns recovery discs. should i burn some?

Yes.  I usually make 2 cop[ies of things.  One for use and one I keep back
as a master just in case.

---

### Post by hyperhopper on 2009-01-31
sorry, but the program is one time use.

anyway to *coughgetpastthatandmake2copiescough*

---

### Post by albinootje on 2009-01-31
> **hyperhopper said:**
>  i would just run a ubuntu install disc

I recommend that you first use the "try without installing" live session from the Ubuntu installation cdrom.
And preferably try 8.04.2 (LTS) or/and 8.10.
See : [http://releases.ubuntu.com/8.04.2/](http://releases.ubuntu.com/8.04.2/)

What are the hardware specifications from your new computer ?

---

### Post by Jynxx on 2009-01-31
I had the same thing with my laptop. Make sure to run the backup program and create the backup disk before dual booting your system. I made this mistake and formated the entire drive on accident, rendering myself without vista. A quick call to HP and two days later, I had a disk in the mail. Once your backup is done, repartition your drive in Vista to the size that you want to allocate for Vista and for Ubuntu. Then you can run the live CD and install Ubuntu to the partition you desire. You can do this by selecting largest free space or my manually selecting the partition you want to use for Ubuntu. Install to largest free space is the easiest way to go. Good luck and let us know how it goes for you!   :D

---

### Post by carml on 2009-01-31
@ hyperhopper
To make a bakup disk for Win#[][s (Bad)Vista,go on Computer,right click your C: drive and select the entry under Properties.
N.B. there also an hidden partition of about 10 GB(that's so on my notebook),which is used by Vista for Recovery;if you mount all your partitions under Linux,that is the one called recovery.
Glad to help an unlucky Win@#*`~ Vista user,me too I have that OS boundled with the PC:).

---

### Post by hyperhopper on 2009-01-31
@ carmel

what?

the specs are

AMD duo core proccessor running at 2.3 ghz
geforce 6150 graphics card
and the hard drive is SAID to be 250 but is really 221

---

### Post by BeardedAvenger on 2009-02-07
Actually if you use xplite (vista build) and strip down your vista install to the bare-minimum to play nextflix movies, you will get pretty good video performance running vista(lite) under virtualbox.

xplite is a life saver sometimes...

---

