---
title: "confused and in need of advice (ubuntu inside windows or virtual box)"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by mrgreaper on 2011-04-25
ok heres the situation, me and a mate run a minecraft server, i have access to the machine via teamviewer. 

os: windows xp 32bit old install
ram: 3 gig

we tried to install ubuntu onto it today using the 64bit 10 10 iso (and the official guide on the ubuntu site to put it on a usb stick) however the usb stick would not load (no configuration found or some such error) i went to your irc channel for help and two people tried to help us but ultimatly we couldnt fix it. 

the fixes included editing the syslinux cfg file and commenting out the default v something file etc or changing it to default live neither worked

the reason for the need to change java now uses 98% of the cpu but only when running minecraft server on his pc (same files on my laptop or on my pc 40%cpu max!) 

so i installed virtual box and mineos(a operating system made (badly) for minecraft) and i got the server running in that perfectly (same files) 

so here leads me to my two options (maybe 4)

option 1 install ubuntu 64bit into a virtual box give it 2 gigs of the 3 available (would love to give it all 3 but windows says no) with this i could then latter as per the advice of someone else make that version of ubuntu all set up into an install disc and overwrite the host os when im able to travel to the machine

option 2 install ubuntu 32bit as a windows application (im guessing i cant install it as a 64bit application on a 32bit os?)

option 3 find some way to get a working usb pendrive configured (could be the tutorial on the official site is not good anymore)

option 4 burry head in sand stick with mine os (not a real option)


ok so the questions

if i go for option 1
1 64bit virtual pc in a 32 bit os...is that wise? 


if i go for option 2
1 will this be using java of the local machine? therefore 98% cpu usuage
2 can i still access it via team viewer of the local pc ?
3 once set up can i make the pc boot into this ubuntu install and bypass windows completly 

if i go for option 3 
1 how?? 

thanks in advance for your help ...if you can think of any way i can install ubuntu remotly with out hassle on my mates part let me know trying to sort this out is becoming costly (2 hours to his mobile earlier, hour and a half yesterday)

---

### Post by mrgreaper on 2011-04-25
been reading the wubi guide seems thats the answer to my prayers! 
my plan
install wubi 
get my mate to boot into wubi
get my mate to install teamviewer on wubi install
access it remotly configure minecraft 
inform our players we are back up and running get them to enjoy themselfs again (i would also like to take this moment to express our server is non profit we charge no one nor do we accept donations for minecraft server)

---

### Post by Jgke on 2011-04-25
Please don't use Wubi for installing Ubuntu. Tried that once and it cut my system's power in half. You should try [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/"), and choose ubuntu_live. Boot off the usb stick and install Ubuntu.

---

### Post by mrgreaper on 2011-04-25
> **Jgke said:**
> Please don't use Wubi for installing Ubuntu. Tried that once and it cut my system's power in half. You should try [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/"), and choose ubuntu_live. Boot off the usb stick and install Ubuntu.

gave that a try already. any method of making a usb stick seems to fail im guessing thats my mates system

we did the wubi install and its all working fine, the server keeps warning us it cant keep up but with two players in causing mass mayham (to stress test) there was no lag it worked better then it has on xp in a long time...in short life is back to good i just need to find how to install mysql as painless as possible and apache (we used wamp on windows that made it simple once you added passwords to secure it !)

---

### Post by Mark Phelps on 2011-04-26
> **mrgreaper said:**
>  ..we did the wubi install and its all working fine ...

For now ...

Wubi is NOT intended for long-term usage; instead, it's intended for use to try out Ubuntu.

Understand that if you make a routine update in Wubi, you will run the risk of it crashing.  We see posts about this all the time.

Also, since it's inside the Windows filesystem, if that gets corrupted, you'll lose access to Ubuntu.

---

