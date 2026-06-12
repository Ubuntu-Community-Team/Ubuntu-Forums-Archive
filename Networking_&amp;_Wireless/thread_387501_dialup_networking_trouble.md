---
title: "dialup networking trouble"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by netsplit on 2007-03-18
Okay I've got my modem installed and can dialout with pon as well kpp (gnomeppp seems to have weird password  errors even though it's the same password as kppp and it connects fine). The helps says I should be able to connect with the networking tool but all that does is let me check and uncheck the connection. Won't dial out.

When it connects checking the networking tool shows it auto configured the dns servers correctly, but all I get is can't find server errors. Nothing loads.

If it helps any the modem is an intel 636EP and it's linked to dev/modem.

Any tips/places or things I should check?


If so much appreciated.

---

### Post by netsplit on 2007-03-19
Okay yay managed to connect using pon.

Needed to add replacedefaultroute to the pppconfiguration file as mentioned in this thread.
[http://www.linuxquestions.org/questions/showthread.php?threadid=341151](http://www.linuxquestions.org/questions/showthread.php?threadid=341151)



As well as changing auth to noauth in my /etc/ppp/options file. This had the side effect of making networking actually be able to control the connection. Except it has the same trouble pon originally did. However looking around it turns out networking uses the file /ect/ppp/peer/ppp0 for dialing out. Copied the contents of the working pppconfig file to ppp0 and now I can connect through networking:)

So if anyone else if having that trouble maybe that will help.

In the /ect/ppp/options file it was very adamant that I not change it to noauth. Are they any risks running this way?

---

