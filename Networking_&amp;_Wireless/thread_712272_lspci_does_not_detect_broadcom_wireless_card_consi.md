---
title: "lspci does not detect broadcom wireless card consistently"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by kapil_karekar on 2008-03-01
I am using a hp tx1000 machine with Gutsy. The funny thing is it detects my Broadcom wireless card sometimes. Whenever the card is detected wireless works fine.

Can someone please help me to get the card detected consistently?

Whenever the card is detected, lspci lists it as:

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

---

### Post by Hightide on 2008-03-01
Hi

are you using ndiswrapper? this [thread]("http://ubuntuforums.org/showthread.php?t=706034") may help 


regards

:)

---

### Post by kapil_karekar on 2008-03-02
Thanks for the reply :)

I have already tried using ndiswrapper. It worked for me. 

However, it does not work consistently. Only rarely does my wireless card gets detected.

The problem to solve here is why doesn't lspci detect my wireless card. Once lspci detects the card then the rest is quite straightforward ... hopefully :-(

Cheers!

---

### Post by kevdog on 2008-03-02
Check dmesg after boot to see if there is an error during boot to determine why your card is detected.  If nothing shows up, you may have a bad card or faulty connection.

---

