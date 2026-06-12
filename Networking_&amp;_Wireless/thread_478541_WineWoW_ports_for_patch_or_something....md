---
title: "Wine/WoW ports for patch? or something..."
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by dardack on 2007-06-19
Um so i have my router forward the ports for the WoW patch to my machine.  But for some reason it just sits there, it doesn't download at all.  I have to boot into windows and do it.  Was wondering, do i have to open those ports in linux or anything?  Or if anyone has any ideas or anything?

(yes i know that there are fileplanets, etc to download, they just usually take longer than booting into windows).

---

### Post by y6FgBn)~v on 2007-06-19
A section from the howto;

"The easiest way to open these ports is to use the firewall program Firestarter. From the command line, install Firestarter with this command: sudo apt-get install firestarter. When it is running, select the "Policy" tab, right-click in the Allow Service area, and select Add Rule. Under port, type 6112 and make sure that the "Anyone" radio button is selected. Make a note in the comments field that this port relates to Blizzard. Repeat these steps for ports 3724 and for the range 6881-6999 (which will be recognized as BitTorrent ports)."

Had you already performed this step?

---

### Post by dardack on 2007-06-19
I'm sorry i meant to add was there another way to do this without installing a soft firewall?  Just do it manually or something.  If not i'll do firestarter.  Is firestarter annoying and ask all the time for programs if it can use or what not?  (like those windoze soft firewalls that suck big time)

---

