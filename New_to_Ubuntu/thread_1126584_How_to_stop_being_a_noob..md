---
title: "How to stop being a noob."
date: 2009-04-15
forum: New to Ubuntu
---

### Post by phreaknite on 2009-04-15
Since I have installed Ubuntu there is always this lingering fear over my head - the fear of not being able to return.

I have several bugs on my ubuntu that I am still sorting out such as:
1) Suspend/Hibernate not working
2) Headphone jack not deactivating main speakers
3) Pidgin randomly stops producing sounds
4) My theme is not as seamless/beautiful as I would like

However, with these issues I am debating whether I should just let them go or even switch over to Vista full time....or hell, even trying to install OSX86 onto my box.

Every time something doesn't work my chest tightens when I go to fix it.  WHen I have tried to fix things in the past it was often a long 10 hour hallway that led to nowhere -- i would wind up reinstalling and learning from the experience and avoiding the problem in the future rather than actually fixing something that is broken.

Is there any way to alleviate this fear?  Maybe a full system save option or something like that?  What is the best way to get over this?

---

### Post by Therion on 2009-04-15
Hmmmm... What version of Ubuntu are you running; is it 8.10 by any chance?

---

### Post by kamitsukai on 2009-04-15
> **phreaknite said:**
> Since I have installed Ubuntu there is always this lingering fear over my head - the fear of not being able to return.

I have several bugs on my ubuntu that I am still sorting out such as:
1) Suspend/Hibernate not working
2) Headphone jack not deactivating main speakers
3) Pidgin randomly stops producing sounds
4) My theme is not as seamless/beautiful as I would like

However, with these issues I am debating whether I should just let them go or even switch over to Vista full time....or hell, even trying to install OSX86 onto my box.

Every time something doesn't work my chest tightens when I go to fix it.  WHen I have tried to fix things in the past it was often a long 10 hour hallway that led to nowhere -- i would wind up reinstalling and learning from the experience and avoiding the problem in the future rather than actually fixing something that is broken.

Is there any way to alleviate this fear?  Maybe a full system save option or something like that?  What is the best way to get over this?

May I just say that I feel that way more often than not, and I've been using Ubuntu a while...

---

### Post by hovzio on 2009-04-15
Sorry misposted, I apologize..

---

### Post by candtalan on 2009-04-15
Which version of ubuntu are you using I wonder?
8.04 and also to some extent 8.10 use pulse audio for sound server and I believe that the implementation of this has not been the best at all. So there may be some problems with sound - I certainly have some in my desktop - with these versions in some machines. 

The particular machine you have will also be relevent. Some machines are good with linux.

Suspend/hibernate problem is a very common problem in laptops with linux, not sure why but it is likely related to the often unique hardware used by manufacturers who do not talk to linux community (yet) enough or even at all.
Experiments and need to reinstall:
With linux you can expect it work like it did yesterday, unless you change it. I found with Windows it changed even when I did not want it to. However, I understand your point and sympathise. afaik themes are easy to change, to your own taste. Have you considered trying kubuntu sessions? It has a different approach and lots of bling. However, there is a learning curve, so relax and enjoy it......

I wonder if your expectations are to find a replacement for windows which is perfect for you? This will exist, although probably not out of the box, so you gathering some configuration experience  will be useful.

---

### Post by lisati on 2009-04-15
Stick with it: if Ubuntu is for you, then patience, perseverance, and practice will bring their rewards. For myself, I have successfully used Ubuntu on three different machines. I've read of other forum users successfully installing Ubuntu on more than that.

Don't worry too much if you don't "get it" immediately: even after using Ubuntu for a couple years now, and managing to clock up several thousand posts on these forums, I find I still don't know everything - a number of times I've read questions on the forums and found myself muttering something like "I *should* know the answer to that!". 

I don't know how well this compares with the experience of other forum users, but a combination of reading the information available in the forums **and** trying something new every now and again is a great way of connecting the theory with the practice, and can sometimes provide the kind of experience that only reading about something can't provide.

---

### Post by WatchingThePain on 2009-04-15
Same here..I want to know if there's a way to clone or exactly copy an image of a hard disc so that it can be put on a shelf then used as required.
Is this possible do you think?.
Come on you Gurus.

---

### Post by lisati on 2009-04-15
> **WatchingThePain said:**
> Same here..I want to know if there's a way to clone or exactly copy an image of a hard disc so that it can be put on a shelf then used as required.
Is this possible do you think?.
Come on you Gurus.

Although it isn't exacly a "disk imaging" program, remastersys can be used to make a LiveCD version of your current installation.

---

### Post by Irihapeti on 2009-04-15
There's some useful info here:

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

I've used the BackupYourSystem/TAR option and it's got me out of a hole on several occasions.

Ideally, one should backup just before playing with a new program or settings. 

Do I always do that? Er, no... And I've had to revert to a fortnight ago... One day I'll remember.

---

### Post by Therion on 2009-04-15
> **phreaknite said:**
> Since I have installed Ubuntu there is always this lingering fear over my head - the fear of not being able to return...  What is the best way to get over this?
> **kamitsukai said:**
> May I just say that I feel that way more often than not, and I've been using Ubuntu a while...
Alright, serious answer.  Just my opinion but here goes...

First and foremost a good Ubuntu experience starts with a ROCK-SOLID install.  What does that mean?  It means a clean install first and foremost.  It means doing a clean install from media that you've *actually* and *thoroughly* checked: Md5 Sum and SHA1 sums are good (both the download and the burn), it means you've burned the name brand CD at 8x or 16x and checked it for errors from the splash screen.  It means you've got as bullet-proof an install CD as is humanly possible.  I don't think I can overstate the importance of this.  You're not just burning a casual mix-CD of your fav hip-hop crap here, you're burning the install CD for your entire operating system.  Think about that for a minute and let the importance of what it means sink in.

Secondly it means being willing to abort the install if ANYthing does not go 125% correctly.  If your cat farts in the vicinity of your hard drive, you take that as a *direct communication* from GAWD that you need to abort the install and start over.  Absolutely everything from the word "Go" must happen effortlessly or it's a redo until it happens seamlessly.

Then, upon your first boot into your new, freshly installed Operating System you do nothing but update and reboot and update again until there are no more updates.  You configure NOTHING until this is done.  You install NOTHING but updates via the Update Manager - not even your video driver; that will be the last update you do.  You then install the basic/essential packages: Flash, Java, codec support, et al.

This is the point from which you begin testing.  And at the same time we come to the REAL Heart of the Matter.  You are going to find that you are either having a Positive Ubuntu Experience or you going to find yourself having a Less Than Ideal Ubuntu Experience.  

If you find you are having a lot of issues that are not readily fixed, if you find you are going down too many of those "long, dark hallways" that go nowhere after doing as I've advised, then it may be time to conclude that Ubuntu quite simply may not be the distro for you...  And that's okay.  Maybe Fedora IS your distro, or OpenSuse or Saybayon or Debian.  One of them is going to fit and that's really what you want.  You want the distro that works for you.  Maybe it's Ubuntu, maybe it's not.

---

### Post by phreaknite on 2009-04-15
> **Therion said:**
> Hmmmm... What version of Ubuntu are you running; is it 8.10 by any chance?

Yes, 8.10 -- why do you ask?  Did you have a suggestion?

> **candtalan said:**
> Which version of ubuntu are you using I wonder?
8.04 and also to some extent 8.10 use pulse audio for sound server and I believe that the implementation of this has not been the best at all. So there may be some problems with sound - I certainly have some in my desktop - with these versions in some machines. 

As stated above its 8.10 on a brand new HP dv6t with ATi Graphics (which has proven to be a nightmare until I learned how to use it...got Compiz working which is the main reason i switched to linux)

Other little things include the remote which is SUPPOSED to be 100% compatible right OOB but has not been working...don't really care about that though since I will likely never use it.

I remember reading a bit about how pulseaudio can be a problem -- maybe I should re-investigate deactivating it on the current boot so that it doesn't change any config settings permanently to see if that will fix my headphone problem?

> **candtalan said:**
> 
Suspend/hibernate problem is a very common problem in laptops with linux, not sure why but it is likely related to the often unique hardware used by manufacturers who do not talk to linux community (yet) enough or even at all.

I found that its half linked to the video card and half linked to...something else.  I feel like I may be able to figure it out...as I said above I am just really iffy on trying something because if I need to reinstall due to a major system FUBAR then I would have to recustomize a LOT of **** again to get back to where I am right now..almost enough to make me just say "Screw it"

> **candtalan said:**
> 
Experiments and need to reinstall:
With linux you can expect it work like it did yesterday, unless you change it. I found with Windows it changed even when I did not want it to. However, I understand your point and sympathise. afaik themes are easy to change, to your own taste. Have you considered trying kubuntu sessions? It has a different approach and lots of bling. However, there is a learning curve, so relax and enjoy it......

Right now Gnome is very nice for my needs in terms of "bling".  Compiz works great just wanted to experiment with some other themes aside from the OSX theme I currently have installed.  The OSX Theme is OK but i never really did like Mac's Top Toolbar so I would like to play around with it but just dont want to make my system fail because something wasn't "pretty enough" you know?

> **candtalan said:**
> 
I wonder if your expectations are to find a replacement for windows which is perfect for you? This will exist, although probably not out of the box, so you gathering some configuration experience  will be useful.

My expectations so far, with the things that are working on Ubuntu, have been exceeded, for the most part.  It is definitely better than Vista and has some legs-up on Mac though mac is MUCH more usable in some aspects (like the File Browser/Finder, for example).  Overall I am happy with Ubuntu but the things that are not working (like Suspend/Hibernate) may be dealbreakers for me since i travel so much.

> **lisati said:**
> Although it isn't exacly a "disk imaging" program, remastersys can be used to make a LiveCD version of your current installation.

Interesting...can you use that Live CD to restore the installation on the hard disk in case something gets FUBAR'd?

---

### Post by WatchingThePain on 2009-04-15
I like the sound of remastersys.

---

### Post by anjilslaire on 2009-04-15
> **WatchingThePain said:**
> Same here..I want to know if there's a way to clone or exactly copy an image of a hard disc so that it can be put on a shelf then used as required.
Is this possible do you think?.
Come on you Gurus.

Clonezilla. Exactly what you're looking for.

---

### Post by WatchingThePain on 2009-04-15
CloneZilla yes, I like.

---

### Post by llamabr on 2009-04-15
> **WatchingThePain said:**
> Same here..I want to know if there's a way to clone or exactly copy an image of a hard disc so that it can be put on a shelf then used as required.
Is this possible do you think?.
Come on you Gurus.

mkisofs will make an image of your current configuration.

---

### Post by phreaknite on 2009-04-15
Which of these options is the best to recover a system from a botched upgrade attempt?

1) remastersys
2) Clonezilla
3) mkisofs

---

### Post by WatchingThePain on 2009-04-15
TY just checked up mkisofs. Good stuff.

---

### Post by AndyCooll on 2009-04-15
Clonezilla does as it says on the tin. It "clones", i.e. makes an exact replica copy of a disk/partition at a certain point in time. So if you botch up an ugrade, provided you cloned it before you started you can then just reinstate the cloned disk/partition.

:cool:

---

### Post by lykwydchykyn on 2009-04-15
g4l is another alternative that I use regularly.

From a liveCD, partimage or just making a tar.gz archive of the partitions can also do this.

But the tools mentioned are probably friendlier, I'm just mentioning things I usually use.

---

### Post by raymondh on 2009-04-15
> **Therion said:**
> First and foremost a good Ubuntu experience starts with a ROCK-SOLID install.  What does that mean?  It means a clean install first and foremost.

Hear, hear.  My thoughts exactly.  I seem to have this preference for a "fresh, clean install" any time something does not go right, feel right or if the moon's out of its' phase.

In fact, I have 9.04 beta and ext4 on it's own partition.  When the official release comes out, I AM STILL considering making another 9.04 official fresh install rather than upgrade thru the networks.

Oh well, it may just be me.  Nevertheless, hear, hear.=D>

---

### Post by qwertyuiop96 on 2009-04-15
The suspend/hibernate thing is a failing of linux in general, I think.  It MAY be corrected and fixed in upcoming Jaunty--let's hope so!  I have not been able to find a solution, and thus set the power prefs to never put the machine to sleep.  I then choose no screensaver.  So- my rather useless answer?  Avoid sleep.  And pester the Jaunty developers.

---

### Post by AndyCooll on 2009-04-15
My view to stop being a newb is to dual-boot until you reach the stage where you realise that you are using one OS all the time and the other one is essentially gathering dust. And where you realise that whatever problems may arise you feel confident that you can rise to the challenge to overcome it. If there are concerns, it really doesn't have to be an all or nothing. Confidence is developed over time, and often gradually.

Perhaps first of all it's more about growing comfortable in using Linux first. So set the dual-boot to default to Ubuntu for instance. And then gradually reduce the dual-boot opening option menu's delay time. It defaults to 10 secs, over time reduce this. It's likely that soon you'll find yourself doing everything in Ubuntu. And you'll work out how to overcome any problems you may have. Persevere.

For me this meant six months of dual-booting. After a month or so I was rarely using Windows but there was one game that I enjoyed playing that I couldn't get working in Ubuntu.

Eventually, using Wine I did get it working. 

I currently can't get the latest version of the game working under Wine, but now I've now moved on and my priorities have changed. So even though this new laptop came with Vista on it, and even though I've left it on (after all it's paid for), if it doesn't run under Linux it doesn't get played, since Linux is my OS of choice and the one I feel most comfortable using.

:cool:

---

### Post by Twitch6000 on 2009-04-15
> **qwertyuiop96 said:**
> The suspend/hibernate thing is a failing of linux in general, I think.  It MAY be corrected and fixed in upcoming Jaunty--let's hope so!  I have not been able to find a solution, and thus set the power prefs to never put the machine to sleep.  I then choose no screensaver.  So- my rather useless answer?  Avoid sleep.  And pester the Jaunty developers.

That is false. However looking at your join date I will let that slide...

The Ubuntu devs are not to bright on bug fixing... they always blame bugs on the wrong people...

Yet its their fault..

Look at fedora ... its bleeding edge yet Suspend works... Pulse Audio works... You know why... The devs made it work ...

Anyways... @op I would suggest you dual boot. 

I find dualbooting or even tribooting is the only thing that makes my laptop happy...

---

### Post by Jacdeb6009 on 2009-04-15
> **raymondhenson said:**
> Hear, hear.  My thoughts exactly.  I seem to have this preference for a "fresh, clean install" any time something does not go right, feel right or if the moon's out of its' phase.

In fact, I have 9.04 beta and ext4 on it's own partition.  When the official release comes out, I AM STILL considering making another 9.04 official fresh install rather than upgrade thru the networks.

Oh well, it may just be me.  Nevertheless, hear, hear.=D>
I agree with Therion and raymondhenson 125%.  If the initial install is not perfect you are in for some blood, sweat and tears...

In my case I have installed on two different notebooks (Acer Aspire and Dell Vostro) 7.04, 8.04, 8.10 all with differing degrees of "issues" but *never* a totally unusable install.  Persevere, this knocks the socks of Windows any day.

---

### Post by phreaknite on 2009-04-16
Right now i have a pretty stable install...I may just start hacking away at things...

Just uncovered a few more issues with my sound so it may be worthwhile to start looking into that side of things...

> Persevere, this knocks the socks of Windows any day. 

Yeh, but what about OSX? :P

---

### Post by qwertyuiop96 on 2009-04-17
> **Twitch6000 said:**
> That is false. However looking at your join date I will let that slide...

The Ubuntu devs are not to bright on bug fixing... they always blame bugs on the wrong people...

Yet its their fault..

Look at fedora ... its bleeding edge yet Suspend works... Pulse Audio works... You know why... The devs made it work ...

A couple people said it was common in some other thread-- that's where I got it from.

---

### Post by raymondh on 2009-04-18
> **phreaknite said:**
> Yeh, but what about OSX? :P

I am a mac user, having migrated from Vista.  I also enjoy my Ubuntu.  I've made my linux/ubuntu install as "close-to-pretty" and productive to my mac.  In that regard, I think linux can be an equal to apple.  The only difference is that I had to tweak/refine my ubuntu to get there whilst my mac came out-of-the box working and strong. I have not yet made the switch from Mac to Linux because my macs have never failed me, crashed, hanged or lost my files in 3 years....unlike Vista. 

Mac's still get my vote as no. 1 because of the reliability, UI and sanity it has given me.  Linux comes a close second as I consider it a very powerful OS because of the flexibility it provides.

Just my .02 worth.

---

### Post by me.translucent on 2009-04-19
well if you decide to dual boot ..i suggest you to use wine with windoze and make a copy of your .disk files in the ubuntu folder from windows these disk files represents the hard disk that your ubuntu installation is using and so whenever u feel the need to get the system restored from the backup just log into windoze replace the disk files in the ubuntu directory with the initial copy and u are done.

---

