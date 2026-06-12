---
title: "DHCP: What happened"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by scott_b on 2007-02-25
I recently installed edgy.  Wireless worked fine.  I updated everything a couple days ago.  Still, everthing was working.  Today I booted up, and I can't get an IP address.  It simply times out.

There are only two things I can think of that I did different between the last time I saw it working (yesterday afternoon) and now.   (1) Yesterday evening I used eth0 for the first time.  And (2) I did so after I had did a suspend - not power-off, power-on.  

I have killed every dhclient process running.  I have edited /etc/networking/interfaces so that everything is commented out except for lo and ath0.  I have found and killed all memory of previous leases I could find.  I have done if-up/down half a million times.  

I'm about to explode.  

Any ideas?

---

### Post by gradedcheese on 2007-02-25
you are sure it successfully associates first?  Try doing it manually and then run "iwconfig ath0" afterward to see if it associated.

---

### Post by r4ik on 2007-02-25
Try,

[http://forums.debian.net/viewtopic.php?p=44352#44352](http://forums.debian.net/viewtopic.php?p=44352#44352)

And look for stream303 

Good luck !

---

### Post by scott_b on 2007-02-25
> **gradedcheese said:**
> you are sure it successfully associates first?  Try doing it manually and then run "iwconfig ath0" afterward to see if it associated.

Yeah, tried that.  I'm doing all of this at school.  The windoze guys can connect. So, I know that's not a problem.  I do a iwlist scanning and plug the mac add into iwconfig.  I have tried that on two seperate ap's with no success

 > Try,

[http://forums.debian.net/viewtopic.php?p=44352#44352](http://forums.debian.net/viewtopic.php?p=44352#44352)

And look for stream303

Good luck !

I'm going to give that a shot in a bit.  So....uh....I'm a bit embaraced, but I don't know what info to put in for: prepend domain-name-servers.  

Could one of you help me there. (keep in mind I'm doing this all at school, which is the only place I have access to the internet).
thanks

---

### Post by scott_b on 2007-02-26
Update -

It works.  I can't explain it, but it works.

I didn't get a chance to try anything suggested by that post you recommended r4ik.  I decided to lock up my laptop and leave it running at school.  I got here this morning and it has an IP address.  

I'm pleased to have access to the internet again, but I'm frustrated because I don't know what happened.  What if I loose the ability to acquire an address again, am I supposed to let my computer run for 12 hours until it works it out?  That doesn't seem reasonable.  

I should say this:  I was having a similar problem with a different card a month or so ago.  Some said that it was because of the card.  But now I'm running a supported D-link card.  So, why the problems?  I'm beginning to suspect a larger issue.  But what do I know? 

Any ideas?

---

