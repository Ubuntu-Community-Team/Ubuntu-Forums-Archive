---
title: "CPU always at 100% PLEASE HELP!"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by ariascarlos1990 on 2010-03-30
So I've had this problem since I first installed the software on this computer. And I'm hoping to get some help to solving it. Any advice would be appreciated!

Heres what im running:
[http://i125.photobucket.com/albums/p51/scooter_dude442/Screenshot-1-3.png](http://i125.photobucket.com/albums/p51/scooter_dude442/Screenshot-1-3.png)


And heres a picture of my recourses:
[http://i125.photobucket.com/albums/p51/scooter_dude442/Screenshot-6.png](http://i125.photobucket.com/albums/p51/scooter_dude442/Screenshot-6.png)
Thanks.

---

### Post by Elfy on 2010-03-30
I would imagine that if you have a normal ubuntu install it is related to running it with less than the recommended RAM.

Check out what is using 100% of the RAM - open a terminal from Apps > Accessories 

```
top
```
use q to quit

---

### Post by the yawner on 2010-03-30
Check out the processes. See what process is taking that much CPU.

---

### Post by NightwishFan on 2010-03-30
I think it would run choppy on such a machine but it would run. I have a suspicion we are going to see Xorg as the culprit. If that is the case, please check your installation cd for errors.

Your machine is really low end for Ubuntu, perhaps try Lubuntu or Puppy.
[http://lubuntu.net/](http://lubuntu.net/)
[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

---

### Post by ariascarlos1990 on 2010-03-30
I restarted it and now its not running at 100%. Still it does this all the time. It will start lagging real bad. 

but, heres my top and cpu % as of now.

[http://i125.photobucket.com/albums/p51/scooter_dude442/Screenshot-2-2.png](http://i125.photobucket.com/albums/p51/scooter_dude442/Screenshot-2-2.png)

---

### Post by NightwishFan on 2010-03-30
Actually that looks normal for such a low end machine. Most of your ram is being used by firefox, do you ever watch flash videos?

---

### Post by ariascarlos1990 on 2010-03-30
> **NightwishFan said:**
> Actually that looks normal for such a low end machine. Most of your ram is being used by firefox, do you ever watch flash videos?

Like youtube? yah sometimes...

Watching videos makes my computer slower?

---

### Post by NightwishFan on 2010-03-30
The flash plugin is very CPU intensive. Any task you do on such a low end machine will be interrupted by the need to swap to disk. I reiterate that performance will be tolerable but never good. I would suggest you try a lightweight Ubuntu variant such as Xubuntu. I have heard of a lighter one coming out called Lubuntu, but it seems it is in beta.
[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by mindcrusher on 2010-03-31
I experienced a similar problem today. I have a Core2Duo (2GHz) laptop with 2 GB of RAM. 
The laptop started lagging and when I checked in the system monitor one of the cores was at 100%(cycling between core1 and core2). After checking with TOP I saw the Xorg process was using 99% so I killed it. X restarted and now I have tow idle cores doing the same jobs as before. 

I am not running any proprietary drivers and no 3D effects so I presume it might be an issue with Xorg.

---

### Post by ariascarlos1990 on 2010-03-31
> **NightwishFan said:**
> The flash plugin is very CPU intensive. Any task you do on such a low end machine will be interrupted by the need to swap to disk. I reiterate that performance will be tolerable but never good. I would suggest you try a lightweight Ubuntu variant such as Xubuntu. I have heard of a lighter one coming out called Lubuntu, but it seems it is in beta.
[http://www.xubuntu.org/](http://www.xubuntu.org/)

ok so heres the question....

If I install Xubuntun Lubuntu, or Puppy will I lose all my saved data, programs and such?

And does it work the same at Linux? If not whats the difference between the two?

---

### Post by J V on 2010-03-31
Xubuntu and lubuntu can be installed through synaptic like any app, if you made a seperate home partition you will keep your data transferring to puppy, or if you just compress the whole /home and extract it on the new install.

Xubuntu has become very heavy for a "Lightwieght" distro, and lubuntu is experimental. Still experimental is often good with linux, it may not be polished, but lubuntu will do the job well.

---

### Post by Sk41m4n on 2010-03-31
You are really low on RAM. Getting some extra 512 or 1024 MB on eBay or such would be a good idea.

---

### Post by ariascarlos1990 on 2010-03-31
> **J V said:**
> Xubuntu and lubuntu can be installed through synaptic like any app, if you made a seperate home partition you will keep your data transferring to puppy, or if you just compress the whole /home and extract it on the new install.

Xubuntu has become very heavy for a "Lightwieght" distro, and lubuntu is experimental. Still experimental is often good with linux, it may not be polished, but lubuntu will do the job well.

Thanks thats what I needed!

> **Sk41m4n said:**
> You are really low on RAM. Getting some extra 512 or 1024 MB on eBay or such would be a good idea.

Do you know what one would work for my machine? and will it configure itself after installation?

Sorry I'm still a noob.

---

### Post by Sk41m4n on 2010-03-31
> **ariascarlos1990 said:**
> Do you know what one would work for my machine? and will it configure itself after installation?

Sorry I'm still a noob.

Upgrading RAM is easy, you have a guide here: [http://www.ehow.com/how_895_install-ram.html](http://www.ehow.com/how_895_install-ram.html)

To find out what type of RAM you should get you could open your computer and look at the tag of the existing RAM (don't do this while the computer is running though ;)). If it says something like DDR PC2700/333 MHz that's what you should be looking for. This information may also be given by your BIOS or by running "sudo lshw" from a terminal in Ubuntu.

---

### Post by ariascarlos1990 on 2010-03-31
> **Sk41m4n said:**
> Upgrading RAM is easy, you have a guide here: [http://www.ehow.com/how_895_install-ram.html](http://www.ehow.com/how_895_install-ram.html)

To find out what type of RAM you should get you could open your computer and look at the tag of the existing RAM (don't do this while the computer is running though ;)). If it says something like DDR PC2700/333 MHz that's what you should be looking for. This information may also be given by your BIOS or by running "sudo lshw" from a terminal in Ubuntu.

Sweet thanks!

So it looks like I have two slots that can use RAM and the max I could use is 1GB for each slot so 2GB total. 

Would this make a substantial difference?

Right now it looks I only have 256MB of RAM in there.

---

### Post by lotharmat on 2010-03-31
> **ariascarlos1990 said:**
> ...the max I could use is 1GB for each slot so 2GB total. 

Would this make a substantial difference?

Ooooooooooooooohhhhhhhhhhh Yes! - A difference you would not believe!

---

### Post by ariascarlos1990 on 2010-03-31
> **lotharmat said:**
> Ooooooooooooooohhhhhhhhhhh Yes! - A difference you would not believe!

Sweeeeeeeeeet!!

I'll be picking up a set soon!

---

### Post by bhmildy on 2010-03-31
Don't spend too much.  $100 is too much for your computer.  You're better off spending a couple hundred bucks for something newer  with a better chip, larger hard drive and more memory.  20G hard drive is too small to be really useful. I think I've got 20 gigs of my 40 filled up, without doing much. my comp runs really good at 512, but I'd be happier w/ 1G RAM, but don't really need it.

I'd see if I could pick up used RAM for $50. if not, get newer computer.
Or, install old linux, perhaps ubuntu v. 6 or 8 LTR, that needs less to run, but that's probably not going to be easy install, because lots of devices will probably need manual install.

install flashblock firefox extension to keep firefox from automatically playing flash on websites.  you can always remove or hit play to view flash on a site.

---

### Post by ariascarlos1990 on 2010-03-31
> **bhmildy said:**
> Don't spend too much.  $100 is too much for your computer.  You're better off spending a couple hundred bucks for something newer  with a better chip, larger hard drive and more memory.  20G hard drive is too small to be really useful. I think I've got 20 gigs of my 40 filled up, without doing much. my comp runs really good at 512, but I'd be happier w/ 1G RAM, but don't really need it.

I'd see if I could pick up used RAM for $50. if not, get newer computer.
Or, install old linux, perhaps ubuntu v. 6 or 8 LTR, that needs less to run, but that's probably not going to be easy install, because lots of devices will probably need manual install.

install flashblock firefox extension to keep firefox from automatically playing flash on websites.  you can always remove or hit play to view flash on a site.


Yah theirs alot of 2GB RAM packs on ebay I could get a set that would for my PC for $45 shipped. Anybody have any experience with ebay specials?

Oh and I have a 120GB HDD

---

### Post by NightwishFan on 2010-03-31
Ariascarlos, please ensure your machine can actually use the RAM. Just having the slots does not mean your machine is compatible with it.

---

### Post by ariascarlos1990 on 2010-04-01
> **NightwishFan said:**
> Ariascarlos, please ensure your machine can actually use the RAM. Just having the slots does not mean your machine is compatible with it.

I did. Check it:

[http://www.crucial.com/store/listparts.aspx?model=Presario%20SR1503WM#](http://www.crucial.com/store/listparts.aspx?model=Presario%20SR1503WM#)

"Each memory slot can hold DDR PC2700,DDR PC3200 with a maximum of 1GB per slot."

---

### Post by NightwishFan on 2010-04-01
Sorry if you mentioned that previously, the Scottish in me was making sure you did not part with your money fruitlessly. Enjoy!

---

### Post by ariascarlos1990 on 2010-04-01
> **NightwishFan said:**
> Sorry if you mentioned that previously, the Scottish in me was making sure you did not part with your money fruitlessly. Enjoy!

I don't think I posted it before.

but, good lookin out!

---

### Post by egalvan on 2010-04-01
> **ariascarlos1990 said:**
> Yah theirs alot of 2GB RAM packs on ebay I could get a set that would for my PC for $45 shipped.
 **Anybody have any experience with ebay specials?**


For eBay RAM specials, deal with sellers who guarantee their merchandise.
Also ones who are willing to specify the RAM manufacturer, not just the chip manufacturer.

Crucial, Hynix, Samsung, Kingston, Dell, HP, IBM, 

are examples of RAM manufacturers.

All else being equal, try to get the faster PC3200 RAM.
(PC2700 is slower)

If it's stated PC2700/PC3200 it means it runs at either speed.

Good luck,

and as *lotharmat* stated, you WILL see a difference!

Next step, a possible CPU upgrade ;)

---

### Post by ariascarlos1990 on 2010-04-01
> **egalvan said:**
> For eBay RAM specials, deal with sellers who guarantee their merchandise.
Also ones who are willing to specify the RAM manufacturer, not just the chip manufacturer.

Crucial, Hynix, Samsung, Kingston, Dell, HP, IBM, 

are examples of RAM manufacturers.

All else being equal, try to get the faster PC3200 RAM.
(PC2700 is slower)

If it's stated PC2700/PC3200 it means it runs at either speed.

Good luck,

and as *lotharmat* stated, you WILL see a difference!

Next step, a possible CPU upgrade ;)

Hey thanks!

I kinda figured that a PC3200 is faster than a PC2700. (see im getting it!)

Theres some people that are local that are selling some RAM I think I might look into that.

---

