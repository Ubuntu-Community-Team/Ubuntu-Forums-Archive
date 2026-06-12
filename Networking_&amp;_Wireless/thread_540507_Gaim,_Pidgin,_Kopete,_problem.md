---
title: "Gaim, Pidgin, Kopete, problem"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by jaymz on 2007-09-01
Ok, this is a really weird problem...

I have perfect internet connection as far as firefox is concerned, the apt-gets all work fine as well.

Nevertheless I am absolutely incapable of using any form of messenger. Neither Pidgin, gaim or Kopete are able to connect. The weirdest part is that they all sign in and I get my friend list but I can't talk to anyone.

People see me signing in as well, but they can't reach me either...

---

### Post by Zorael on 2007-09-01
Is your firewall set up to block outgoing traffic? You may need to lessen the clamp (and allow everything outgoing), or define and allow the ports for the protocols you use in Gaim/Pidgin/Kopete.

apt-get downloads its stuff through the normal HTTP protocol (and port), I believe, so if Firefox works so should apt-get. And your router is likely allowing stuff on the HTTP port. :)


edit: I mean, at least in the case of ICQ, traffic is not normally done through the server port, but rather in a random port (or a random port in a specified interval). Because of this, I usually open a range of ports and map them to my ip; like, 3200-3400 - and make sure my IMs listen on these ports for messages, file transfers, etc.

I hope I'm making sense.

---

### Post by jaymz on 2007-09-01
Indeed you are and that worked fine :)

Thank you!

---

### Post by jaymz on 2007-09-04
Ok, so here I am again... 

All IM programs are not working, I don't understand why. In my desktop, under windows, everything works fine. This is just one of those annoying Linux situations in which a simple thing can get too complicated for someone who, like me, doesn't consider themselves to be a complete noob...

Any help would be adorable, any questions you have just fire away

---

### Post by parias on 2007-09-06
I have exactly the same problem! I have tried Gaim, Pidgin, Kopete, and none of them connect to the MSN network. My proxy is correctly configured (I can use Skype and I can perfectly surf the  Web). I tried to open the range of ports in Gaim (didn't work); I reinstalled everything... nothing seems to work. I keep getting this message with Kopete: "Operation is not supported". Any ideas guys?:confused::confused::confused:

---

### Post by knutschr on 2007-11-04
I asked Pingin to listen to all ports from 80 to 2048.
Then it worked!

---

