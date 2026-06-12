---
title: "Odd WD TV Live login problem with Ubuntu Server (Greyhole)"
date: 2014-08-10
forum: Networking &amp; Wireless
---

### Post by futz2 on 2014-08-10
Friend's network: He has a DSL-modem/router/switch for internet. There's a 5-port switch that has connected one wire to a computer, one wire to the modem/router for internet, one wire to an Ubuntu Server (Greyhole) NAS box and one wire to a WD TV Live.

Should be simple. My setup at home is very similar and my WD TV works perfect with his NAS box plugged into my network.

But when I plug the NAS into his network and try to login with the WD TV box, the WD complains that the username/password is invalid. It's NOT invalid. I can take the ethernet wire out of the WD TV box, plug it into a laptop, start a terminal and login to the NAS box with no problem, using the exact same username/password.

I brought my (identical) WD TV box and swapped it for his. It won't login to the NAS while in his network, even though it had his user/pass already saved. Tried re-typing it in - no change.

I can take his NAS box to my house, plug it into my network and my WD TV box logs in normally. No complaints about username/pass at all. It just works.

I temporarily swapped out his switch and the WD TV ethernet cable with known-good parts (from my house), just in case, but nothing changed.

Here's a rough sketch of the pertinent parts of his network:

[IMG]http://imgur.com/tzbphOz.jpg[/IMG]

---

### Post by futz2 on 2014-08-11
> **futz2 said:**
> But when I plug the NAS into his network and try to login with the WD TV box, the WD complains that the username/password is invalid. It's NOT invalid. I can take the ethernet wire out of the WD TV box, plug it into a laptop, start a terminal and login to the NAS box with no problem, using the exact same username/password.
It occurred to me today that these are two different logins. Duh! :biggrin: The WD box is doing a Samba login to shares. But I'm doing an SSH login from the laptop. So disregard that part of the above paragraph.

I'm thinking it must be some kind of weird Samba share permission thing, but why does it work on my network but not on his? Same equipment both places. Tomorrow I'm going to drag my file server over to buddy's house and see if his WD will login...

---

### Post by futz2 on 2014-08-12
This thing is making me crazy.

Went back to friend's house, taking his new file server **and** my own. I plug mine in and start up the WD TV box. I login and am playing movies right away. Good.

So I unplug my server and plug his in. Once again, the WD box won't login to it, claiming the user/pass is invalid. There's nothing wrong with the user/pass. I pull the ethernet cable out of the back of the WD box, plug it into my CrunchBang netbook, login to Samba and play movies, no problem. Put the same wire back into the WD box and it refuses to login.

So I pack up and take his WD box home with me. I replace my WD box with his in my network and test. Of course it works perfectly, and I can login to any of the three Samba servers here, including friend's, with no problems whatsoever. They're the same WD box - I can't tell his from mine.

I'm completely confused. This should work, but it doesn't, and I have no idea why. 

I have one strange little clue for you all to go on. On my network, when I SSH to any server it asks for the password pretty quickly - essentially instantly. But on buddy's network it makes me wait for a while - maybe 30 seconds or more? - before asking for the password. I don't know if that has anything to do with it, but it seems to me that should give somebody a clue as to what's happening.

EDIT: Just tested the server by logging in from a Windows 7 box. It logs in and accesses files on the server shares perfectly. This is on my network though. I don't have any portable Windoze machines to test with at buddy's house (he's a Mac guy).

---

### Post by futz2 on 2014-08-15
Fixed it.

Friend's new server install was 14.04. My older server was 12.04.

I wiped his box and reinstalled with 12.04. Including everything, it took me two hours. When I was done I took it to his house, plugged it in and the WD TV box logged in normally and works great.

Bonus: The file transfer speed on the 14.04 install was pathetic - around 6 to 8 MB/s. I had been blaming it on the old mainboard. Once I installed 12.04 it jumped to a very normal 22 to 27 MB/s. And the weird 40 second SSH and Samba delays went away.

I've come to the conclusion that Ubuntu 14.04, both server and desktop (which I run on my main computer) are a buggy mess, and it seems like nothing is being done about it.

---

