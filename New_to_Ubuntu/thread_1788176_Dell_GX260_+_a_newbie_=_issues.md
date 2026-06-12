---
title: "Dell GX260 + a newbie = issues"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by TheBlueMonkey on 2011-06-22
Hello one and all, 

My google-fu appears to be weak on this one so forgive me if this has been covered.
Here are the steps and conclusions I've come to so far.

I tried to install the latest version of ubuntu on an old Dell GX260, it boots as far as what looks like a desktop\install screen but then starts spitting out errors and won't let me install.

I tried a number of other modern releases of linux and all did roughly the same kind of things, Fedora boots to the desktop but then I can't click the install icon, Suse shows me a green screen with the suse logo, gentoo.... well... I'm new and I got part way through the install and had no idea what was going on.

Being from a windows background I figure "hey, maybe this is like installing windows 7 on an old machine" so I start looking for an older version of ubuntu to use. The handful I've tried have all had the same issues untill I tried 4.10.

I presume it's some kind of driver issue so,

Is there a way of upgrading from 4.10 to the latest release?
Does anyone else have Ubuntu on a GX260, if so, what version?
Is there a way of "slip steeaming" the drivers for the GX260 into an ubuntu install CD?

I know I should just get a newer machine to install it on but I want to try it out on this before I go the whole hog and switch.

---

### Post by crispy_420 on 2011-06-22
Older post but may be relevant to your issue:
[http://ubuntuforums.org/showthread.php?t=481558](http://ubuntuforums.org/showthread.php?t=481558)

---

### Post by candtalan on 2011-06-22
Just a thought- the lighter versions of ubuntu are more friendly for older hardware, and are worth considering to try also - such as xubuntu and lately lubuntu.

---

### Post by iclestu on 2011-06-22
absolutely!

Go for a 'light' installation rather than an old version. Old versions are no longer supported, dont have the latest software, bug fixes etc...

xubuntu or lubuntu are more likely to meet your requirements and are still actively developed....

---

### Post by grahammechanical on 2011-06-22
How much memory does this machine have? The installation process needs a certain amount of memory. How much? I cannot remember. Sorry. You could try an Alternate Install CD. This uses a text based installer that does not require as much memory to the standard install CD.

Regards.

---

### Post by TheBlueMonkey on 2011-06-22
Sounds like a smarter way of doing things :)

so I've been skim reading some bits about the light versions and I don't really get the difference between lubuntu and xubuntu.

I mean, I get that one uses Xfce and the other uses LXDE but I don't exactly get what that means... what's the difference?
Which is better?

also, 

Where do I get these "alternate" downloads from? I've been rumadging and I'm having a very bad google day ¬¬

---

### Post by iclestu on 2011-06-22
> **TheBlueMonkey said:**
> 
Where do I get these "alternate" downloads from? I've been rumadging and I'm having a very bad google day ¬¬

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

for the Ubuntu alternative installer.

Lubuntu and Xubuntu will almost certainly be fine as is.

You never really answered the spec questions which may give people a better idea as to whether to advise you to persevere with Ubuntu or go for a lighter system like lubuntu or xubuntu.

In terms of which of the lighter ones are 'better' it really is personal preference. Try em and see!

---

### Post by lykwydchykyn on 2011-06-22
Neither one is "better"; they're just different desktops.  In my opinion/experience, LXDE is a bit lighter and faster, but XFCE is much more mature, stable, and feature-complete.


The GX260 is cursed with an onboard intel i845 graphics chip, which works poorly with Linux, unfortunately.  It works acceptably if you update the BIOS on the system to the latest version, but I would stay away from desktops like KDE4, Unity, or GNOME3 with that graphics chip.

---

### Post by iclestu on 2011-06-22
> **TheBlueMonkey said:**
> Sounds like a smarter way of doing things :)

so I've been skim reading some bits about the light versions and I don't really get the difference between lubuntu and xubuntu.

I mean, I get that one uses Xfce and the other uses LXDE but I don't exactly get what that means... what's the difference?
Which is better?

also, 

Where do I get these "alternate" downloads from? I've been rumadging and I'm having a very bad google day ¬¬

I just had a thought...

you realise that the 'alterative installer' is a different way of getting the main Ubuntu distro onto your system?

the other flavours (lubuntu and xubuntu) can be found here:

[http://people.ubuntu.com/~gilir/lubuntu-11.04.iso]("http://people.ubuntu.com/%7Egilir/lubuntu-11.04.iso")

and here:

[http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)

---

### Post by TheBlueMonkey on 2011-06-22
> **iclestu said:**
> 
You never really answered the spec questions 


Sorry about that, It's a GX260 P4 2.4GHZ 256MB 20GB but I'm rumadging for some spare\cheap memory for it

---

### Post by lykwydchykyn on 2011-06-22
> **TheBlueMonkey said:**
> Sorry about that, It's a GX260 P4 2.4GHZ 256MB 20GB but I'm rumadging for some spare\cheap memory for it

You'll definitely want more memory for that.  But the lighter distros should still run ok on it.

Just make sure you have BIOS A09.  It will sort out some of the graphics issues.

---

### Post by iclestu on 2011-06-22
> **TheBlueMonkey said:**
> Sorry about that, It's a GX260 P4 2.4GHZ 256MB 20GB but I'm rumadging for some spare\cheap memory for it


gotta be a light distro then:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

as you dont meet min memory requirements for main ubuntu.

Even with some more memory I think id opt for a light distro. By and large you can still run pretty much any software you need to but it will run much more 'crisply'. No sense bogging down your kit with the OS and leaving no resources for applications to use. Just my opinion but either way, as it is, you dont have enough memory for the main Ubunto distro. Pick between lubuntu and xubuntu which should both just about be fine

---

### Post by crispy_420 on 2011-06-22
Max memory is 2GB is you can find some laying around, good. You may able to grab some on craigslist used for a decent price too.

Here are the specs:
[http://www.crucial.com/store/listparts.aspx?model=OptiPlex%20GX260%20Series&Cat=RAM](http://www.crucial.com/store/listparts.aspx?model=OptiPlex%20GX260%20Series&Cat=RAM)

---

### Post by TheBlueMonkey on 2011-06-23
Thank you for all your help, 

Changing the video memory has fixed my install issues (even with bios 03, I'll get the latest version on there at some point)

I've thrown ubuntu 7.10 on there at the moment to play around with while I wait for some extra memory to turn up, then I'm thinking about getting Lubuntu on there and seeing what I think of that.

---

### Post by crispy_420 on 2011-06-23
Was was it the default 1MB set for video memory?

Can you call this solved yet?

---

### Post by PhilGil on 2011-06-23
Just a heads-up to the OP...

I administer several GX260's at my office. To date, I have been unable to get any version of Ubuntu or Debian using kernel 2.6.32 or newer to function with the onboard graphics. Increasing the video memory does not solve this issue.

You can stay with an older version of Ubuntu (up to 9.10). My work-around was to purchase cheap, used AGP graphics cards from ebay (they were less than $10 each).

With only 256 mb of RAM you'll want to run one of the lightweight DE's. With 512 mb you can run Gnome2 satisfactorily, but it won't be a speed demon.

---

### Post by TheBlueMonkey on 2011-06-27
> **crispy_420 said:**
> Was was it the default 1MB set for video memory?

Can you call this solved yet?


Yes this can be closed as resolved.

In the end I got a copy of the alternate lubuntu 10.10 install from here
[https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall)

I changed the graphics settings in the bios from 1mb video memory to 8mb video memory.

I also upped the ram to 1gb

I ran through the text install which all went smoothly and started the machine after install into the desktop.

I then ran the various system updates from the update manager.

there were a couple of errors saying things like
"services to restart for GNU libc library upgrade
rsync cups cron atd"

Overall, it all seems fine.... I just have to learn what these messages actually mean and fix em now ;)

---

