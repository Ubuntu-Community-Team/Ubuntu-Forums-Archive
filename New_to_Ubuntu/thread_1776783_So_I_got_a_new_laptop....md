---
title: "So I got a new laptop..."
date: 2011-06-06
forum: New to Ubuntu
---

### Post by jrozo17 on 2011-06-06
... yesterday as my graduation present! I pretty much freaked out since before I used an 8 year old computer that could do very little.(dead cdroms, etc) It even has a webcam ;)
 
So anyway now that my rant is over I have a few questions...
 
Is there, if any, difference between battery life on a laptop running Windows 7(preinstalled) or Ubuntu 11.04?
 
Is it true that Ubuntu uses the fan much more than Windows?
 
Should I download the 32 bit or 64 bit version? Will it make much difference?(I have a 64 bit system)
 
 
Thats about it for now. I'm not exactly a newbie to Linux, but I want to make sure I get everything right on my laptop the first time.
Thanks to any help. :)

---

### Post by uRock on 2011-06-06
What are the system specs on your new lappy? Mileage may very.

---

### Post by jrozo17 on 2011-06-06
> **uRock said:**
> What are the system specs on your new lappy? Mileage may very.
 
Its a Dell Inspiron N5010
 
Intel Core i3 CPU    M 380 @ 2.53GHz 2.53 GHz
 
4.00 GB of RAM
 
 
Is that enough info?

---

### Post by Jesus_Valdez on 2011-06-06
I usually get less battery life on Ubuntu that on Windows.

Also, I know no reason to not use 64 bit.

---

### Post by Immolatus on 2011-06-06
you will get roughly 1/2 the battery time with Linux as the system will not automatically turn system components on and of. They will all be on. Like turning off the disc drive when not in use will save something like 30 extra minutes of battery life across total span. There are no utilities of this nature for general use as of yet but soon I'm thinking.

I do know a guy who accomplished this through CRON and a whole lot of scripting. something like 10 hours of battery life.

P.S. My thinkpad gets 5 1/2 hours on win7 and 3ish for ubuntu.

---

### Post by collisionystm on 2011-06-06
Dell Vostro 1014. Same battery life on 7 and natty.

Intel core 2 duo, 4 gb of ram, 250gb hd

---

### Post by nzjethro on 2011-06-06
I haven't noticed any dramatic differences in battery life, but then again I'm on HP, which has a pretty sub-standard battery life fullstop. As for 32 vs 64, may as well go 64 bit if you've got the system. 4 gigs of RAM should be enough to see a positive difference, and almost all applications came out 64 bit these days.

---

### Post by wildmanne39 on 2011-06-07
> **jrozo17 said:**
> ... yesterday as my graduation present! I pretty much freaked out since before I used an 8 year old computer that could do very little.(dead cdroms, etc) It even has a webcam ;)
 
So anyway now that my rant is over I have a few questions...
 
Is there, if any, difference between battery life on a laptop running Windows 7(preinstalled) or Ubuntu 11.04?
 
Is it true that Ubuntu uses the fan much more than Windows?
 
Should I download the 32 bit or 64 bit version? Will it make much difference?(I have a 64 bit system)
 
 
Thats about it for now. I'm not exactly a newbie to Linux, but I want to make sure I get everything right on my laptop the first time.
Thanks to any help. :)
Hi, I ran a hp laptop and the battery life was the same, but the is a bug in natty that is affecting the battery life in some laptops but it is being worked on aggressively to be fixed. I do not know if it will affect yours or not.

---

### Post by Mark Phelps on 2011-06-07
> **jrozo17 said:**
> ... yesterday as my graduation present! I pretty much freaked out since before I used an 8 year old computer that could do very little.(dead cdroms, etc) It even has a webcam ;)
 
So anyway now that my rant is over I have a few questions...
 
Is there, if any, difference between battery life on a laptop running Windows 7(preinstalled) or Ubuntu 11.04?
At the current time, 11.04 is showing greater power demands than Win7, causing reduced battery life.  While the claim is that folks are working on this, at present, this is not solved to the advantange of Ubuntu.
 
> Is it true that Ubuntu uses the fan much more than Windows?
It's not a matter of fan usage, it's a matter of power saving profiles -- which as already implied, Win7 does better at present than Ubuntu 11.04.  If you DO install 11.04, don't make the mistake of trying to force your fans to run slower or quieter -- that will only hasten the burning out of components due to overheating.
 
> Should I download the 32 bit or 64 bit version? Will it make much difference?(I have a 64 bit system
In the past, there were problems getting Flash to install and run on 64-bit machines -- but that may have been solved.

Unless you're planning on using significantly more than 4GB of memory, you won't reap any real advantage of running 64-bit instead of 32-bit -- and no, 64-bit does not inherently run faster than 32-bit.

---

### Post by baligirl on 2011-06-07
I installed a 64-bit version of ubuntu on my laptop, and the first program I tried to install (skype) did not have a 64-bit version that would work on this OS (at least at that time, last year?)  So I had to back out to a 32-bit ubuntu.  So perhaps check on the programs that you plan to use and see if they are all up to speed with being 64-bit compatible before you get too far.

---

### Post by CVGH on 2011-06-07
I think I read something about the latest kernel having some power problems?

---

### Post by Paqman on 2011-06-07
> **Mark Phelps said:**
> 
In the past, there were problems getting Flash to install and run on 64-bit machines -- but that may have been solved.

It has.

> and no, 64-bit does not inherently run faster than 32-bit.

[Yes it does](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1). Common desktop tasks like video re-encoding will be significantly faster, for example.

---

### Post by FormatSeize on 2011-06-07
I don't have a laptop anymore (my dog knocked a cup of beer onto it), but I would have never imagined that software had an effect on battery life. It makes sense now that it was explained that Linux doesn't turn things on and off automatically.
 
I would like to know more about the efforts that someone took to make that happen in Linux, though. That sounds interesting.

---

### Post by Tony.B on 2011-06-07
> **jrozo17 said:**
> ... yesterday as my graduation present!
Congratulations on graduating.

---

### Post by Mark Phelps on 2011-06-07
> **Paqman said:**
> Common desktop tasks like video re-encoding will be significantly faster, for example.

As they say .. YMMV.

I installed 64-bit as a test on a separate partition, ran the two OSs (32-bit and 64-bit) for several weeks -- noticed NO performance gain in the 64-bit version.

Was so disappointed that I posted on the motherboard forum -- and was told by EVERYONE there, that a 64-bit OS is NOT inherently faster than a 32-bit OS -- which was supported by my testing and is what I meant to say.

And Yes, SOME 64-bit apps, under SOME circumstances, are going to run faster -- but that's if they were written to take advantage of 64-bit processing, and (in many cases) more memory.

---

### Post by DogMatix on 2011-06-07
I no longer run windows on my laptop but didn't see a particularly noticeable difference in battery life when I did. I do run the screen as dim as i can tolerate when not on AC and have sleep and hibernate cut in fairly quickly if my attention is diverted or I nod off for a while.

I would absolutely recommend 64 bit Ubuntu. I have had no problems with enabling Flash in recent versions.

---

