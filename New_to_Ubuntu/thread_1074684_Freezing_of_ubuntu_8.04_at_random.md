---
title: "Freezing of ubuntu 8.04 at random"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by shishir_knit on 2009-02-19
I hav installed ubuntu 8.04 
but i m facing a problem that my sytem freezes at any time
nither mouse nor keyboard works
the last option is only to restart my system

my system config is

intel dual core processor
two 512 mb ram
ati graphics chipset(which is restricted and i hav not installed its driver)

i hav given ubuntu 25 gb space

i hav done also many times memtest but it also not worked for me
i hav also not installed the visul effects


please help me out of this problem
reply will be appreciated

---

### Post by shishir_knit on 2009-02-19
waiting for ur reply

---

### Post by shishir_knit on 2009-02-19
anybody please reply

---

### Post by sydbat on 2009-02-19
If the memtest fails, you most likely have a problem with your RAM. 

If you have a desktop computer, shut off the computer (properly by selecting the shut down option), unplug the power cord after the power is off, open the box and make sure nothing is loose...meaning, make sure every connector is tight and the RAM modules are seated properly. (If you have a laptop, take it into a professional and have them make sure nothing is loose.)

Let us know if this solves your problem.

---

### Post by shishir_knit on 2009-02-19
i hav tested it before
i hav a desktop
and i hav gone through checking of its ram and connectors
it might be due to ram because this 512mb ram i hav inserted in my system about a week ago but after that i hav formatted my system and installed vista and ubuntu both
vista is not giving any problem.

so now what can i do for it

---

### Post by shishir_knit on 2009-02-19
any other suggestion please!

---

### Post by abyssius on 2009-02-19
> **shishir_knit said:**
> any other suggestion please!

Remove the RAM stick you inserted a week ago and run Ubuntu with 512Mb RAM. If it still locks up, remove that RAM stick, insert the other and try again. Ubuntu will run properly with 512Mb, although Vista probably won't - not even with 1 Gig of RAM.

---

### Post by shishir_knit on 2009-02-20
i hav tried this also but in both ram system freezes

---

### Post by shishir_knit on 2009-02-20
please any other suggestion

---

### Post by ikisham on 2009-02-20
Did you check the integrity of the ubuntu iso file (md5 sum), if you downloaded it? Also did you check the integrity of the disk burnt?

---

### Post by SamNSane on 2009-02-20
Just to make sure that we're all understanding each other -- you said:

> i hav done also many times memtest but it also not worked for me

What do you mean when you say "it also not worked for me"?

Do you mean:

1. Memtest is saying that there is nothing wrong with the system memory, and thus it is not "working" in helping you to find the problem.

OR

2. Memtest is saying that there **is** something wrong with your memory.

If #2 is what you are saying, then you did the right thing by testing the memory sticks one-by-one. If the system won't run properly with either stick alone, then **both** sticks are either bad, or they are not suited for use on your system.

---

### Post by shishir_knit on 2009-02-21
no mine is first option 
ie 
Memtest is saying that there is nothing wrong with the system memory, and thus it is not "working" in helping you to find the problem.

---

### Post by shishir_knit on 2009-02-21
i hav installed ubuntu throgh cd of 8.04
and whats this (md5 sum)
and how can i check the integrity of disk burnt

---

### Post by shishir_knit on 2009-02-21
please reply

---

### Post by SamNSane on 2009-02-21
> **shishir_knit said:**
> no mine is first option 
ie 
Memtest is saying that there is nothing wrong with the system memory, and thus it is not "working" in helping you to find the problem.

I was afraid of that. This is beginning to sound as though the drivers available in Ubuntu 8.04 don't support the combination of hardware / firmware in your system. My guess is that your hardware itself is healthy. Contrary to opinions I've seen stated in many places, Vista is pretty hard on hardware. If it runs on the system, the system is probably okay.

Ubuntu 8.04 and 8.10 are, I believe, the first versions of Ubuntu to use xrandr, 8.10 making more aggressive use of it than 8.04. There are many posts on these forums about particular video subsystems and particular LCD screens not functioning with these versions of Ubuntu.

I don't doubt that you might find a way to make the operating system work on your computer, but I think it will probably be difficult. It's certainly beyond my range of expertise to attempt something like this through this means of communication.

> **shishir_knit said:**
> i hav installed ubuntu throgh cd of 8.04
and whats this (md5 sum)
and how can i check the integrity of disk burnt 

Normally you can find the md5sum of the .iso image file on the page from which you download the file. To be sure that the .iso file you downloaded has the proper md5sum you just open a terminal window, change directory into the location of the .iso file and type --

md5sum filename.iso

-- (substituting the actual name of the .iso file, of course) then hit the <Enter> key. The system will spend a minute or so calculating the value and then present it on the command line interface as --

"xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx" filename.iso

You do that before you burn the .iso to disc. That's just to save you the trouble of burning a disc  that won't work. If you've booted that disc and told it to check itself, and the check came out okay, then the disc is okay.

My guess is that there's nothing wrong with your disc, and there's nothing wrong with your computer. It's just that you're going to find it hard (or impossible) to get Ubuntu to run on that system. It happens, unfortunately. It's easier to get most linux distros to run on older hardware than on newer hardware because the developers just haven't had the time to come up with proper drivers for all of the latest hardware.

Or it could also just be a problem with this particular version of the Ubuntu distro. You could find that 8.10, or even 9.04 (not officially released yet -- coming out in April) would work better. Or another distro like suse or fedora or whatever might also work.

I'm sorry I can't give you any solid answers.

:(

Have you contacted the technical support people for the computer? They might know of a particular linux distro and version that will work with it.

An Additional Question
----------------------

I didn't notice whether or not you said. Is this a 64 bit version, or a 32 bit version? Whichever it is, you could always download, burn, and install the other one. It's always possible that the hardware support in the other version would work better for your particular system.

Whatever else you do, though, do call the tech support folks. If your model is a popular one, it's possible some of the guys working in tech support own it and have tried linux on it. If you can find such a person (which will probably require much patience and persistence on your part) you could get lucky and get the information you need to make this work.

---

