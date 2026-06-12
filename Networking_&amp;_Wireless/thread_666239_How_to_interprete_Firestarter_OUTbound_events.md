---
title: "How to interprete Firestarter OUTbound events?"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by perixx on 2008-01-13
Hello!

I've set up Firestarter recently and I'm not pretty knowledgeable in terms of firewall events... when looking at my Firestarter's logged events, there are some OUTgoing ones reported that take place on (to me) uncommon ports:

I have installed (among other, non-GUI apps): Envy, gFTP, OpenOffice, Firefox, Thunderbird, SMPlayer, Mplayer, Mixxx and Bittornado Client, but are not currently running them (apart from FF, of course). Also, subversion and mercurial are on my system - regarding programs that I think that might want to connect to the internet. 

Further things I could think of: auto-update features of Xubuntu, Firefox or FF plugins (NoScript, Prefbar, FoxyProxy, RefControl, Controle de Scripts, Addblock Plus, ChatZilla (not active atm.), DownloadHelper, Status Bar, BatchDownload, Iget, DownThemAll) or perhaps Firestarter itself. Ah yes, and of course Unreal Tournament 2004 as well (but it's mainly using ports around 7777, AFAIK).

Does someone know about any of those programs using ports as high-numbered as 15xxx?
How can I sort out and track down which applications cause which connection?

Btw., does anyone know why so many incoming DCOM connections from Windows PC's are trying to set up?

perixx

---

### Post by perixx on 2008-01-13
Additional question, how do I distinguish between actually successful (INbound) connections and rejected ones? By the 'TOS 0x00' flag?

perixx

---

### Post by perixx on 2008-01-13
> Additional question, how do I distinguish between actually successful (INbound) connections and rejected ones? By the 'TOS 0x00' flag? I think I've understood that one; as far as I can tell, all listed events are blocked, thus 'unsuccessful'. 
Established connections must be specified in the rules section and are therefore known by the user and not listed at all -- anybody please correct me if I'm wrong.

> Does someone know about any of those programs using ports as high-numbered as 15xxx?
How can I sort out and track down which applications cause which connection? Well, for sure many of those connections I've noticed were triggered by UT2004 (starts a whole bunch of connections, I guess to all listed servers provided by the master server - I'm not sure). Those are OUTbound cons, though. I'm not perfectly sure but I think I also noticed INbound cons with strange port numbers; I'll start a few single apps and have a second look...

perixx

---

