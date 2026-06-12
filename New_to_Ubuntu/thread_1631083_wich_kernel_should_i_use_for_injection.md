---
title: "wich kernel should i use for injection"
date: 2010-11-26
forum: New to Ubuntu
---

### Post by mrpervie on 2010-11-26
ive been doing a lot of research today how to patch rtl8187 drivers for air crack suit

i have not been near Ubuntu in almost a year...could someone tell me the latest kernel release that supports Alfa usb 500 mw rtl8187 for monitor mode and packet injection

i am currently running 10.10 

or least  tell me weather or not im waisting my time looking for an updated tutorial for patching my drivers for 10.10 or point me in the right direction please.

---

### Post by Paqman on 2010-11-26
10.10 has a pretty recent kernel. Your path of least resistance is probably to swap your wifi card for one that you know will work, rather than messing about patching kernels and so on.

Do you mind us asking what you're using Aircrack for?

---

### Post by mrpervie on 2010-11-26
just to know how to use it..play around with my network security etc....i mostly just like to monitor...to know whos messing with my things i guess...

i figured 10.10 was the latest.

but what i mean is what is the latest that supports this card out of the box with injection and monitor mode.

or at least the most recent with an updated tutorial.....i just like to learn it all i guess

---

### Post by mrpervie on 2010-11-26
also buying a new card is out of the question.this is a decent card..and im a student who has no money and when i say no money...i mean debt =P

---

### Post by Paqman on 2010-11-26
> **mrpervie said:**
> also buying a new card is out of the question.this is a decent card..and im a student who has no money and when i say no money...i mean debt =P

Fair enough but you might be surprised how cheap they are. You could pick one up on eBay for the price of a couple of beers.

---

### Post by 3rdalbum on 2010-11-26
To my knowledge (which is a couple of years old), the only driver for this card that works with Aircrack is their own driver, which only supports WEP and is probably useless for your purposes.

I'd also probably be a bit careful. If a network near you had an intrusion and this was detected and investigated by the Police, you'd probably be Suspect #1 due to the size of the antenna on your card and the existence of Aircrack on your computer. It wouldn't surprise me if those Alfa cards were mainly bought by script kiddies and wannabe hackers, although mine has only ever been used to transmit big video files to my home server :-)

---

### Post by mrpervie on 2010-11-26
this card works better than any card i have ever purchased.and this card is cheap.it only cost around 20 bucks on eBay..i have several cards..none come close to this card.also this card has many features.one being able to broadcast as as a hotpot while receiving internet access...and i might add it is AMAZING when it comes to broadcasting as an access point ...20 bucks for for what it can do was not a bad investment.honestly..you should consider purchasing one ...
as for script kiddos buying this card ...why not? its a damn good card...
and the size of the antenna? its a simple 5 dbi antenna its not large at all....
as i said in a previous post i like to monitor (kismet) and the last i checked there is nothing illegal about testing the security of my own network...
i could give several reasons why i love this card...but what it all comes down to is....

i want to be able to do everything from one operating system...im tired of switching between distros and OSes to be able to do what i need to do.

but i think Ive found what i needed...not sure yet  if anyone as any suggestions im willing to check it out still any help would be appreciated...thanks again guys


3rdalbum,..is it possible to use their driver on ubuntu?

---

### Post by 3rdalbum on 2010-11-27
> **mrpervie said:**
> this card works better than any card i have ever purchased.and this card is cheap.it only cost around 20 bucks on eBay..i have several cards..none come close to this card.also this card has many features.one being able to broadcast as as a hotpot while receiving internet access...and i might add it is AMAZING when it comes to broadcasting as an access point ...20 bucks for for what it can do was not a bad investment.honestly..you should consider purchasing one ...

I have the N model.

> as for script kiddos buying this card ...why not? its a damn good card...
and the size of the antenna? its a simple 5 dbi antenna its not large at all....
as i said in a previous post i like to monitor (kismet) and the last i checked there is nothing illegal about testing the security of my own network...

I just pretty much wanted to check that you weren't breaking into someone else's network, no offence intended. The antenna is lot larger than you find on most USB wifi devices.

> 3rdalbum,..is it possible to use their driver on ubuntu?

It used to be, probably still is. But it only works for unencrypted networks and for WEP (this may have changed in the two years since I used this driver!). You don't want to change your network to WEP just to use the driver; I did and got a lot of "third-party" network use. At that time, the normal RTL8187 driver was a heap of poo and the Aircrack driver was decent.

---

### Post by mrpervie on 2010-11-29
I also have the N model i just have not had much luck with its sensitivity ...seems to be a bit weak. when it comes to receiving ..how is the sensitivity on your card? 
 i haven't played around with it much i let my brother use it,i was disappointed with it...maybe the newer drivers work better

but i did some more research on my card  from what i found and the part im stuck on the drivers do not want to compile with the new kernel in 10.10..so i guess ill just wait

unless someone can confirm  that awus360nh (N version) has a sensitivity  fix and is working just as well as its predecessors now

---

### Post by admiralspark on 2010-12-26
I have the solution.
Get BackTrack linux for penetration testing on your network. I know you said you didn't want to switch to another operating system, but Backtrack will include all of the relevant wireless patches for getting cards into monitor mode, to work with aircrack-ng, etc. I suggest you check that out.

Paqman: the thing about help and information sharing in general is this: regardless of the potential for good or ill use of a product, offering support on the public forums should be uncensored, regardless of the views of the poster. If you don't agree with the potential use of such a tool, do not post support--but it is also none of our business what he wishes to do with it unless it directly has an effect on support.

mrpervie, when using Backtrack and the aircrack-ng suite (use the Grimwepa program included instead for a nice, graphical layout of the command-line aircrack), it will automatically use the macchanger tool to 'spoof' your wireless's mac address, which will provide a more realistic attack (so that the router doesn't see it as coming from your computer, but from an unknown one). Reversing the process to find the real mac is basically impossible, which is why others trying to break into your network will use it to hide who they are. If you have two computers to use, you should practice using one with monitoring software and the other launching a wireless cracking attack against it. Very interesting to watch how it all works out.

---

