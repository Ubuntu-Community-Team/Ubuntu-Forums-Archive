---
title: "Testing your patience, sorry!"
date: 2005-08-29
forum: Networking &amp; Wireless
---

### Post by errata on 2005-08-29
Hi all - I installed ubuntu today. It was, in the main a very straightforward process and 90% of the quirks that were troubling me, I got sorted out, either through brute force and ignorance, or by a constant referral to this brilliant forum...

Alas, I've hit the wall. I'm trying to install the files which will allow me to use my RT2500 wireless dongle.... I followed the guide here: [https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/)

but then, being a complete and utter incompetent newbie, I got lost...

I followed the installation guide, word for word (i pasted the text into the terminal hehe) and it worked perfectly until:

4. Now Type:

cd ./rt2500-cvs-*/Module

I get; bash: cd: ./rt2500-cvs-*/Module: No such file or directory

so logically i'm referencing a file that doesnt exist... i've tried to search for another file with "rt2500" in the title, but failed....

if i've followed the guide letter for letter, where else could the file be?

i'm really sorry for this total newbie question - you guys seem to have near limitless patience, and i wouldnt be posting this unless it was 3am and i was on the verge of going insane trying to get this to work

really hope you can help... have full installation txt if that would be of help...

thanks for reading

---

### Post by chiefofthejojos on 2005-08-29
> cd ./rt2500-cvs-*/Module 

off-hand i think it looks like that you probably shouldn't type the '*' here.  Instead, after you have typed "cd ./rt2500-cvs-", press the <tab> button and ubuntu should auto-complete the rest of the directory name, then add "Module" to the end of it.

---

