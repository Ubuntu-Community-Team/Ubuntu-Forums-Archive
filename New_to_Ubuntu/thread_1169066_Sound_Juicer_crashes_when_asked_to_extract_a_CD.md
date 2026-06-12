---
title: "Sound Juicer crashes when asked to extract a CD"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-05-24
why can't sound juicer extract cd's successfully?

if i hit "extract cd" it crashes, i get "segmentation fault" in terminal. 

fresh install of ubuntu 9.04. + fresh install of sound juicer. still fails. extracting cd's is day one stuff. they've had applications for this for 10 years now. this shouldn't require 30 minutes of diagnosing and troubleshooting. 

what do i need to do to fix this, what does segmentation fault mean, and why isnt this working out of the box?

this app is like 5 megs and is as simple as it can possibly get, yet it fails. cmon....

---

### Post by asuastrophysics on 2009-05-24
<please delete this post.>

---

### Post by clhsharky on 2009-05-24
Did you install ' ubuntu-restricted-extras '

---

### Post by asuastrophysics on 2009-05-27
> **clhsharky said:**
> Did you install ' ubuntu-restricted-extras '

```
girdy@girdy-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for girdy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
girdy@girdy-laptop:~$ 

```

sorry for my short tone.

---

### Post by kpkeerthi on 2009-05-27
> **asuastrophysics said:**
> of course, nobody has any ideas. i tried audex, which is the only other cd extracting program for ubuntu. 
There are many. Try abcde, rubyripper, grip (google!).

What format are you trying to rip to? For mp3, you need **lame** installed.

I presume your CD is bad since you could not get it work in both the rippers. Did you try with any other CD?

---

### Post by asuastrophysics on 2009-05-27
no both rippers didn't work because lame was not installed, but it's weird that such a required codec wasn't installed with the package.

what's weirder is that cd extractor doesn't popup a window to make you aware of this issue. instead, it crashes

---

### Post by kpkeerthi on 2009-05-27
Ubuntu ships with only free (as in freedom) software.

[http://www.ubuntu.com/community/ubuntustory/philosophy](http://www.ubuntu.com/community/ubuntustory/philosophy)

---

### Post by kpkeerthi on 2009-05-27
> **asuastrophysics said:**
> what's weirder is that cd extractor doesn't popup a window to make you aware of this issue. instead, it crashes
File a bug report

---

### Post by andrew.46 on 2009-05-27
Hi asuatrophysics,

> **asuastrophysics said:**
> it has taken me now 3 hours to extract a simple cd. fail. 

I can see that you are more than a little frustrated with this whole experience. The best solution might be, as kpkeerthi suggested, to try a different approach. I wrote a guide quite some time ago that could certainly be described as a 'different approach' when compared to Soundjuicer:

HOWTO: Convert music CDs to MP3 using the Command Line
[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)

Take this for a spin, it will certainly rip your audio cds and convert to mp3 and hopefully you will have a little fun while you explore this great set of programs :-).

All the best,

Andrew

---

### Post by Johan-Steyn on 2009-05-27
Hi Asuastrophysics,

For what it's worth I also struggled to get Sound Juicer to work properly. Mp3 extract produced only garbage.

The best advice I could possibly give you is to dump Sound Juicer altogether and install RipOff. Easy, intuitive interface, easy configuration - excellent results.

I would say it easily out performs the rip functionality of Windows Media Player 10/11. 

Be sure to also install the ripoff-mp3-plugin from synaptic.

Regards,

JS

---

### Post by takayuki on 2009-06-16
same here...

in Jaunty: grip and sound juicer did not work

RipOff works!

sudo apt-get install ripoff ripoff-mp3-plugin

---

### Post by MacP2008 on 2009-07-10
I just downloaded this as I had the same problem with Sound Juicer.

Why is RipOff so slow at ripping? (:confused:

---

### Post by pedricus on 2010-01-24
I had the same problem with sound juicer... ripoff worked first time, no issues... i'd like to try out sound juicer since it's the one that is listed in the ubuntu manual... but it seems to crash whenever the 'extract' button is pushed... 

any ideas would be appreciated...


....


nevermind.. i'll just use rythmbox, which is already installed... and works just fine... maybe i should try reading the manual that matches my release version... i bet that would help alot.... *hmph*

---

### Post by sunew on 2010-05-31
I'm also bitten by this - segfault when extracting. It's 2010 (!) and ubuntu out of the box install still has problems doing something so ordinary as ripping a cd. Everytime I have to do some non-programming task, I can be sure there'll be a problem. The lesson is: Don't count on that you can print, rip cd's, watch tv or movies, share files out of box.

---

### Post by areteichi on 2010-06-08
I found out from [this thread]("http://ubuntuforums.org/showthread.php?t=1146052") that the reason why Sound Juicer was crashing for me was because the titles and the artist were left blank. I was able to get it to work simply by manually inserting the information.

> sound-juicer crashes when extracting a song with empty/null name

This bug has been around at least since 2007. Hope somebody who knows how to fix it reads this thread and fixes it. I would if I could...

Meanwhile, make shure to name your songs. It'll save you the frustrations of looking for another ripping program.

---

### Post by robin48gx on 2010-06-08
Why can't we have GRIP inm ubuntu ?


We use SUSE Linux 11.2 at work and this has grip and its really easy to use.

AND reliable...

---

### Post by joseielpi on 2010-07-16
I have the same problem. Adding names to the tracks did not avoid the crash. I am currently using Ripoff.

---

