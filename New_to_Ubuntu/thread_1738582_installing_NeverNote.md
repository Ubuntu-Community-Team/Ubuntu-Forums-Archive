---
title: "installing NeverNote"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-04-25
Ok, so I'm a noob.

Can someone walk me through installing NeverNote on Ubuntu 10.10? I can't seem to install it....And I have no idea how

---

### Post by wolfen69 on 2011-04-25
Download it from [here]("http://sourceforge.net/projects/nevernote/"), and just click to install.

---

### Post by skyzthelimit230 on 2011-04-25
Yep, I have tried that already. I download the .deb package and it dosent install. I open it in ubuntu software center and it says wrong architecture ix38 or something like that. 

:)

---

### Post by collisionystm on 2011-04-25
You need to open terminal, Browse to your Downloads folder

and do a sudo dpkg -i --force-architecture <filename>

---

### Post by collisionystm on 2011-04-25
And did you know there is a 64 bit version on there? I just downloaded it this morning lol. I am running 64 bit ubuntu as well

---

### Post by skyzthelimit230 on 2011-04-25
ah Cool I did not! Thanks I opened up the terminal and did what you have said. Worked like a charm :)

Thanks mate

---

### Post by AlanR8 on 2011-04-25
Something to watch out for.

When I close NeverNote, processor utilisation ramps up and the cooling fans spool up!

Looking in System Monitor it appears that Java is "Sleeping" but CPU utilisation is at 100%. I kill the process and all is well again.

---

### Post by skyzthelimit230 on 2011-04-25
yeah I've noticed that earlier! It slows my system down a bit too. I figure I'll open it only when I need to. ugh, why is finding a good note taking program so tough on Linux? I love linux, but little issues like this are going to prevent its desktop appeal to the lay user

---

### Post by AlanR8 on 2011-04-25
You could always just go straight to the Web based version.....

---

### Post by baumgarr on 2011-04-27
> **AlanR8 said:**
> Something to watch out for.

When I close NeverNote, processor utilisation ramps up and the cooling fans spool up!

Looking in System Monitor it appears that Java is "Sleeping" but CPU utilisation is at 100%. I kill the process and all is well again.

This is a known bug fixed in the next release (probably out in a few days).  To stop it, go into Edit/Preferences and disable the "Synchronize on Close" option.

Thanks.

---

### Post by Hendry on 2011-05-26
> **baumgarr said:**
> This is a known bug fixed in the next release (probably out in a few days).  To stop it, go into Edit/Preferences and disable the "Synchronize on Close" option.

Thanks.
Any idea when a new version will come out? My version is now instable on ubuntu 11.04. It disappears, doesn't sync right etc. Running 64 bits by the way

---

### Post by baumgarr on 2011-05-26
A new release came out on April 29.  Are you running 0.99?

If it disappears you might try running it in a terminal and seeing if it crashes & puts out any messages.

---

### Post by betterhands on 2011-06-09
> **AlanR8 said:**
> You could always just go straight to the Web based version.....

that's what i've been using so far but i'll give the next version a shot and see how it goes.  i've come to use Evernote quite a bit and don't mind the web interface in the meantime.

---

