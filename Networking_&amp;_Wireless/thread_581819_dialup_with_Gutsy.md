---
title: "dialup with Gutsy?"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by NJC on 2007-10-19
Does Gutsy include decent dialup modem support - IE better than Dapper?

---

### Post by NJC on 2007-12-14
Since I have now installed Gutsy on a Dell PIII/933Mhz box with an external serial US Robotics modem, I can answer yes, dialup works better in Gutsy vs Dapper. 
 
After editing the Network manager settings to include ph #, login name etc, I could dial directly from Network Manager. That was very easy although it seemed flaky so I installed Gnome-PPP instead. Gnome-PPP works well but it does have a bug. The "Connecting" window stays open after a connection is made, instead of docking. See here for more info: [https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487)

---

### Post by madjr on 2007-12-22
> **NJC said:**
> Since I have now installed Gutsy on a Dell PIII/933Mhz box with an external serial US Robotics modem, I can answer yes, dialup works better in Gutsy vs Dapper. 
 
After editing the Network manager settings to include ph #, login name etc, I could dial directly from Network Manager. That was very easy although it seemed flaky so I installed Gnome-PPP instead. Gnome-PPP works well but it does have a bug. The "Connecting" window stays open after a connection is made, instead of docking. See here for more info: [https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487)


gnome-ppp patched:
[http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb](http://launchpadlibrarian.net/10692409/gnome-pppfixedforgutsy_0.3.24-1_i386.deb)

---

### Post by oxman on 2008-01-10
Hello, 
I have installed gutsy for a neighbor. They have a usrobotics external modem. I tried setting it up using network settings to no avail. Can you point me in the right direction? Any help is appreciated.

---

### Post by NJC on 2008-01-11
Hi oxman;

Under System/Administration/Network is the modem listed?

---

### Post by oxman on 2008-01-11
Thank you for your reply.

Yes the modem did appear in the network dialog box. The small icon indicating network connectivity has a small exclamation mark next to it and there seems no way to activate the modem connection. I configured the modem manually in the network dialog.

---

### Post by NJC on 2008-01-11
Oxman, I see you are using Dapper. Check out the #2 post of this thread:

[http://ubuntuforums.org/showthread.php?t=375233](http://ubuntuforums.org/showthread.php?t=375233)

As well, go to Synaptic package manager and search for "Gnome-PPP" and install. I think that's all I did. 

Post back the results.

---

### Post by oxman on 2008-01-12
I have installed gutsy on a neighbors box and I also have it on my other sata drive. Same problem. No internet connection. I use gnomeppp for dapper myself but that doesn't help me connect using the gutsy release.

---

### Post by NJC on 2008-01-14
For Gutsy, I went to System/Administration/Network and entered the telephone #, and other relevant connection information. Ensure connection is enabled (check mark beside device in Network). 
 
What does ifconfig say?

---

### Post by oxman on 2008-01-15
Well, when all else fails...start over right? I did a fresh gutsy install on my second sata drive and bingo! here I am. Followed the same procedure and had no problems. Easy as could be. In fact, easiest I've ever seen it. I probably did something stupid or maybe just a glitch somewhere.
Anyway my gratitude for your replies.

---

### Post by NJC on 2008-01-15
Good to hear your machine is working! I also found installing the dialup modem incredibly easy for Gutsy (although not so for Dapper). There is a fix for Gnome-PPP not docking properly (IE it hangs on the "Connecting..." window although it is connected); I can provide a link if need be.

---

### Post by oxman on 2008-01-16
> **NJC said:**
>  There is a fix for Gnome-PPP not docking properly (IE it hangs on the "Connecting..." window although it is connected); I can provide a link if need be.

Yes please give me the fix URL. I'd be grateful. BTW I am on amd 64 bit.

---

### Post by NJC on 2008-01-21
It's post #3 of this thread - but it didn't fix the problem.

---

### Post by NJC on 2008-05-03
Gnome-PPP 0.3.23-1 finally docks properly in Ubuntu 8.04.

---

