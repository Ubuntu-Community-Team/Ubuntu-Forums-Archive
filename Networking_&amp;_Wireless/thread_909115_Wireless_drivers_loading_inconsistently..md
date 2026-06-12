---
title: "Wireless drivers loading inconsistently."
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by chrisN_uk on 2008-09-03
I wasn't quite sure where to post this, so sorry if it in the wrong place. My situation is this:

Whenever I turn on my computer with my wireless card plugged in, the correct drivers fail to load and I'm the card is unresponsive.

However, if I plug the card in *after* I've logged on, the card works...

It seems like there should be a simple solution to this, can someone give me a hint as to which log file to look in for clues?

---

### Post by Ayuthia on 2008-09-03
> **chrisN_uk said:**
> I wasn't quite sure where to post this, so sorry if it in the wrong place. My situation is this:

Whenever I turn on my computer with my wireless card plugged in, the correct drivers fail to load and I'm the card is unresponsive.

However, if I plug the card in *after* I've logged on, the card works...

It seems like there should be a simple solution to this, can someone give me a hint as to which log file to look in for clues?

You can start in dmesg to see if there are any messages.  That is done in the Terminal.  Another Terminal command is lshw -C network.  This command will give you information about your network cards.  You can see the name of the driver that it is trying to use.  It could also help you find the name of the driver in dmesg.  There might be an issue there.

---

### Post by chrisN_uk on 2008-09-03
Thanks!  lshw told me that the driver I didn't want was rndis_wlan. So I blacklisted that and now it loads up with the correct driver (ndiswrapper+bcmrndis) but the card won't respond and dmesg has quite a few lines like this:
 Buffer I/O error on device sr0, logical block 0
 Buffer I/O error on device sr0, logical block 1

 end_request: I/O error, dev sr0, sector 0
 end_request: I/O error, dev sr0, sector 4

and says eth0 and wlan0 are busy...
Isn't sr0 the cd drive though? I'm stumped as to what those messages mean...

---

