---
title: "rt2500 problems!  PLEASE HELP!"
date: 2005-10-05
forum: Networking &amp; Wireless
---

### Post by gozel on 2005-10-05
Hi,
I've been using Ubuntu for about 2 months now.  I absolutely love it.  Recently I decided to get a wireless PCMCIA card - the Belkin Wireless G Notebook Card (part # F5D7010).  I followed the steps on the ubuntu wiki to the letter, but the "ra0" link doesn't appear when I go to System->Administration->Networking.  
What did I do wrong?
How do I fix it?
I really need this for school, so I would really really appreciate any help! (Please be gentle, I'm a newbie :oops:)  
By the way, I'm using a Dell Inspiron 6000.
Thank you so much!

---

### Post by mlomker on 2005-10-05
Post the output of **iwconfig** after loading the driver and we'll start from there.  I'm not sure if that card is 100% compatible with Atheros or not...sometimes you have to use ndiswrapper.

---

### Post by gozel on 2006-04-13
Wow, this is an old post.  I got the card working (I'm using it right now) using ndsiwrapper.  Very easy.  Not a hitch.  Sometimes, though, system gets unstable if there are many APs with the same name around (like at school).  Something about wireless event being too big or something.  Happens rarely.  All in all, very happy with it.
Gozel

---

