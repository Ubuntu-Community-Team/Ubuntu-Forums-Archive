---
title: "moving sync to ntp.ubuntulinux.org?"
date: 2005-07-25
forum: Networking &amp; Wireless
---

### Post by tuxtail on 2005-07-25
Hi

Is it possible to move the ntpdate command when booting up kubuntu?

For a lot of reasons, I have my network configured late in the boot proces, and ntpdate fails due to the network not being set up... :-? 
But I can't seem to find any script in rc2.d or elsewhere, so that I can move it...

How do I do that? I do NOT wish to disable... :-# 

/tuxtail

---

### Post by majikstreet on 2005-07-25
[QUOTE=tuxtail]Hi

Is it possible to move the ntpdate command when booting up kubuntu?

For a lot of reasons, I have my network configured late in the boot proces, and ntpdate fails due to the network not being set up... :-? 
But I can't seem to find any script in rc2.d or elsewhere, so that I can move it...

How do I do that? I do NOT wish to disable... :-# 

/tuxtail[/QUOTE]
 The only thing I can think of is have your network configured earlier in /etc/network/interfaces (that's where mine is configured)
How is yours configured at boot? Maybe we can change it to configure earlier.

---

### Post by tuxtail on 2005-07-26
This is unfortunately that is not an option  :???: 

I use the Laptop on different networks, both WiFi and ethernets, and I have a program to select  which network I want to join. This is nice to have as close to the login (kdm) screen as possible.

I have intentionally moved the start of kdm a bit, and the start of the network too. An that should be it... Now I really need to move the ntpdate to later...

Is this really not possible? If not, I think it should be :smile: 

/tuxtail

---

### Post by majikstreet on 2005-07-26
[QUOTE=tuxtail]This is unfortunately that is not an option  :???: 

I use the Laptop on different networks, both WiFi and ethernets, and I have a program to select  which network I want to join. This is nice to have as close to the login (kdm) screen as possible.

I have intentionally moved the start of kdm a bit, and the start of the network too. An that should be it... Now I really need to move the ntpdate to later...

Is this really not possible? If not, I think it should be :smile: 

/tuxtail[/QUOTE]
 Hmm.....

I would imagine it would be pretty hard to move that syncing.

But, I'm not sure how to do it, hopefully someone knows how.

---

### Post by tuxtail on 2005-07-27
Weeee, I figured it out...

I found out that the symbolic link that called ntpdate (S51ntpdate) resided in /etc/rcS.d/ !!!  :-P

So running this command:

sudo update-rc.d -f ntpdate remove

removed the starting of ntpdate. Then I needed to add it somewhere else.
I did that to runlevel 2 with this command:

sudo uddate-rc.d ntpdate start NN 2 .

NN is the runlevel in wich I wanted to start ntpdate, AFTER I got my network up and running. In my case:

sudo uddate-rc.d ntpdate start 22 2 .

That did the trick for me...   :grin: 

/tuxtail  8)

---

### Post by majikstreet on 2005-07-27
[QUOTE=tuxtail]Weeee, I figured it out...

I found out that the symbolic link that called ntpdate (S51ntpdate) resided in /etc/rcS.d/ !!!  :-P

So running this command:

sudo update-rc.d -f ntpdate remove

removed the starting of ntpdate. Then I needed to add it somewhere else.
I did that to runlevel 2 with this command:

sudo uddate-rc.d ntpdate start NN 2 .

NN is the runlevel in wich I wanted to start ntpdate, AFTER I got my network up and running. In my case:

sudo uddate-rc.d ntpdate start 22 2 .

That did the trick for me...   :grin: 

/tuxtail  8)[/QUOTE]
 That's great!

Cool.

---

