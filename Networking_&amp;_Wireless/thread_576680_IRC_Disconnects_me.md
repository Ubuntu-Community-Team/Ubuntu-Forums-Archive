---
title: "IRC Disconnects me"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by joegiampaoli on 2007-10-15
Every darn time I try to use an IRC client my network just totally dies (no internet, no network), had this bug in Edgy I am now in Feisty and I still have the same problem it didn't happen before (like 5 months ago), but this is new, I am not sure if it has something to do with my provider blocking some ports or what, what can I do? or What can I tweak so any IRC client I use doesn't do this to me, even with firefox IRC plugins it will do totally disconnect me making me reset the router modem and network in ubuntu.:confused:

---

### Post by openaddict on 2007-10-15
Wow, that's a strange error indeed.  And you say it happens no matter which IRC client you use?  Perhaps it's a shared library issue.  Try booting from a Live CD and trying out the same IRC client.  If that works without problems then it's a software issue.

---

### Post by joegiampaoli on 2007-10-16
Well I made the test booting with the Live CD, and no success, I installed Xchat in the Live CD session, and got the disconnection again, but the weirdest thing of all this is that I like still see what other people are chatting about in the IRC client, but I don't think they can see me, and I pen firefox and no internet. Get a load of that......:confused:

---

### Post by joegiampaoli on 2007-10-18
Mega BUMP!!!*:confused:
I wish I could connect to IRC for help on this, obviously I can't.....

---

### Post by tkharris on 2007-10-18
I would try connecting on an alternitive port ( like 6669 which most irc servers support ), also try using SSL ( if the server you're using supports it ).  If both of those fail, try making an ssh tunnel to a shell you have on another network ( You use irc, so I assume you're got shell accounts on friends servers ) and then using your IRC client through that ( not using a client in ssh, mind you ) this will at least tell you if it's problem with your ISP blocking the traffic both on string matches and ports.

---

### Post by | MM | on 2008-05-30
> **joegiampaoli said:**
> Every darn time I try to use an IRC client my network just totally dies (no internet, no network), had this bug in Edgy I am now in Feisty and I still have the same problem it didn't happen before (like 5 months ago), but this is new, I am not sure if it has something to do with my provider blocking some ports or what, what can I do? or What can I tweak so any IRC client I use doesn't do this to me, even with firefox IRC plugins it will do totally disconnect me making me reset the router modem and network in ubuntu.:confused:

I have this same problem. Dlink 504t modem.  As soon as i connect to the IRC server my modem just goes blank.  All the status lights go out including LAN and power... everything!  Truely bizarre.  I will test windows XP tonight.

---

### Post by joegiampaoli on 2008-05-30
Now I'm on Hardy, and guess what?

Same thing........:mad:

---

