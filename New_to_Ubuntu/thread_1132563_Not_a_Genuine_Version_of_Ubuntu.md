---
title: "Not a Genuine Version of Ubuntu?"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-04-22
Cairo Dock crashed for some reason I haven't figured out (or really care to) and I got a message asking saying that it detected a crash or something and asked if I wanted to send an error report. I clicked yes and then it says that it failed because I'm not using a genuine version of Ubuntu? I downloaded and installed from the ISO from the main website. Why did I get the message?

I'm using 8.10 and my home folder is on a separate partition.

---

### Post by youknowwhat4q on 2009-04-22
> **sup3r3g0 said:**
> cairo dock crashed for some reason i haven't figured out (or really care to) and i got a message asking saying that it detected a crash or something and asked if i wanted to send an error report. I clicked yes and then it says that it failed because i'm not using a genuine version of ubuntu? I downloaded and installed from the iso from the main website. Why did i get the message?

I'm using 8.10 and my home folder is on a separate partition.

oh my god!!!  Ubuntu is turning in to vista!!!!!!

Everyone run!

---

### Post by Sup3r3g0 on 2009-04-22
That's what I thought!

---

### Post by pbpersson on 2009-04-22
Um.....I am hoping the wording was a little different.

That's scary  :confused:

---

### Post by nwadams on 2009-04-22
> **Sup3r3g0 said:**
> Cairo Dock crashed for some reason I haven't figured out (or really care to) and I got a message asking saying that it detected a crash or something and asked if I wanted to send an error report. I clicked yes and then it says that it failed because I'm not using a genuine version of Ubuntu? I downloaded and installed from the ISO from the main website. Why did I get the message?

I'm using 8.10 and my home folder is on a separate partition.

my guess is that it probably didn't like the kernel version you were using for some reason. Or the version of Cairo Dock was no the latest or something.

---

### Post by kpkeerthi on 2009-04-22
> **Sup3r3g0 said:**
> Cairo Dock crashed for some reason I haven't figured out (or really care to) and I got a message asking saying that it detected a crash or something and asked if I wanted to send an error report. I clicked yes and then it says that it failed because I'm not using a genuine version of Ubuntu? I downloaded and installed from the ISO from the main website. Why did I get the message?

I'm using 8.10 and my home folder is on a separate partition.

Really? Thats funny. Do you have a screenshot?

---

### Post by Ericyzfr1 on 2009-04-22
Did you download the "Genuine Advantage" app that will......Hold a second, it reminds me of something used to pop up on my screen.....No that can't be the same thing, it was in another life where I used to pay for all the stuff that made my laptop......well sloooooowwwwwwww!!!!

---

### Post by Sup3r3g0 on 2009-04-22
> **pbpersson said:**
> Um.....I am hoping the wording was a little different.

That's scary  :confused:

The wording *was* a little different. But that was the gist of it.

---

### Post by Sup3r3g0 on 2009-04-22
I think it might of been because I didn't get a chance to do all of the updates. I'm still using the 8.10 from the first week it was released. It was probably a small bug. 

Does anyone know of a way that I can crash another program? I want to see if I can get that message again.

---

### Post by youknowwhat4q on 2009-04-22
> **Sup3r3g0 said:**
> I think it might of been because I didn't get a chance to do all of the updates. I'm still using the 8.10 from the first week it was released. It was probably a small bug. 

Does anyone know of a way that I can crash another program? I want to see if I can get that message again.

An update might be a good place to start.

---

### Post by Sup3r3g0 on 2009-04-22
I updated and cairo dock works now. Before, it wouldn't even show in the applications menu, I would have to launch it with the terminal.

---

### Post by pbpersson on 2009-04-22
Maybe it is an Easter Egg buried inside Ubuntu
[B]
Ubuntu Genuine Advantage has determined your copy of Ubuntu has been pirated.  You must become Genuine now or Tux will find you when you are sleeping.  Be afraid.....be very afraid.....[/B]

---

### Post by halovivek on 2009-04-22
I got this same error from one of system. but the I crashed the OS by installing all the softwares.

---

### Post by kramer65 on 2009-04-22
Look I had the same!!

Aaaargh!!](*,)

---

### Post by clive littlewood on 2009-04-22
Thats a very scary screen !!!!!!!!!!!!!!!   :(


Clive

---

### Post by capnthommo on 2009-04-22
> oh my god!!! Ubuntu is turning in to vista!!!!!!

VUBUNTU anybody?
cheers
nigel
having a lazy day in the sun

---

### Post by Peter09 on 2009-04-22
If I remember rightly the actual message is along the lines that the version of the software that you are using is not up-to-date and suggests that you update your machine.

---

### Post by youknowwhat4q on 2009-04-22
```
sudo apt-get autoremove ; sudo apt-get autoclean ; sudo apt-get install update ; sudo apt-get clean
```

Run this and call me in the morning.
:P

---

### Post by stmiller on 2009-04-22
[IMG]http://xs138.xs.to/xs138/09173/debian-cert651.png[/IMG]

:)

---

### Post by crabclaw on 2009-04-22
> **youknowwhat4q said:**
> ```
sudo apt-get autoremove ; sudo apt-get autoclean ; sudo apt-get install update ; sudo apt-get clean
```

Just for those dummies who like the joke but didn't get that, what does it mean?

---

### Post by LowSky on 2009-04-22
run this command(s) and you machine will be up to date and free of all old packages... basically its magic 

```
sudo apt-get autoremove & sudo apt-get autoclean & sudo apt-get update & sudo apt-get upgrade & sudo apt-get sudo apt-get clean
```

---

### Post by Shpongle on 2009-04-22
yea id say its most likely an update issue

---

### Post by Paqman on 2009-04-22
> **Sup3r3g0 said:**
> Cairo Dock crashed for some reason I haven't figured out (or really care to) and I got a message asking saying that it detected a crash or something and asked if I wanted to send an error report. I clicked yes and then it says that it failed because I'm not using a genuine version of Ubuntu? I downloaded and installed from the ISO from the main website. Why did I get the message?

I'm using 8.10 and my home folder is on a separate partition.

The error message would have been something like:
> 
Cannot submit a crash report, as packages X,Y and Z are not genuine Ubuntu packages


You'll get this message from Apport if you get a crash in an app that isn't from the main repos.

---

### Post by Castor68 on 2009-04-22
Oh my God!

Do I have to validate every ISO I downloaded and burned ?????

jajajajajaaa

---

### Post by egalvan on 2009-04-22
> **LowSky said:**
> run this command(s) and you machine will be up to date and free of all old packages... basically its magic 

```
sudo apt-get autoremove & sudo apt-get autoclean &
 sudo apt-get update & sudo apt-get upgrade &
 sudo apt-get clean
```

I've got something similar (no "upgrade" tho) in a little script...
I run it once a week, or so...

I installed it in ~/bin, and it is a no-brainer to do...

It was my first script... taught me about "#!/bin/bash"
and how placing in in ~/bin/ would let me run it from any terminal...

ErnestG

---

### Post by youknowwhat4q on 2009-04-23
> **egalvan said:**
> I've got something similar (no "upgrade" tho) in a little script...
I run it once a week, or so...

I installed it in ~/bin, and it is a no-brainer to do...

It was my first script... taught me about "#!/bin/bash"
and how placing in in ~/bin/ would let me run it from any terminal...

ErnestG

That is a good idea.

If you would be so kind it would be nice to have a little instructional on how to do it.  Sure would save me a few key strokes.

---

