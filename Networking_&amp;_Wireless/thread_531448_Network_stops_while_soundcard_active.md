---
title: "Network stops while soundcard active"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by Darreln on 2007-08-21
I have a Soundblaster Live 5.1 sound card.  When I play a cd or a music file, my network response time becomes non-existent.  Basically I get no response, can't surf the net or get email.  As soon as I stop the music the response time goes right back to normal.  I can surf the net, get email, etc.  If I remove the sound card, then enable and use the onboard audio,  everything works normally.   I used a couple of different music players, moved the sound card around to different pci slots, disabled the parallel port and the usb ports to get the sound card on it's own irq (not shared) and nothing made any difference.  If that sound card is installed and I play any music my internet response time slows to a crawl.
I am running Ubuntu 7.04 on an AMD 1.33 processor.  The network card is a wireless Linksys WMP11. 
I am wondering if anybody out there has any other ideas I might try or possibly somebody has encountered this problem or a similar problem in the past.

Darreln

--

---

### Post by ddrichardson on 2007-08-21
Is the soundcard interfering with the wireless? Any problems if you use a wired network?

---

### Post by Darreln on 2007-08-21
The problem is only with the wireless connection.  I hard wired from the router to a nic on the computer and everything worked normally.  I could play music and surf the net at the same time.

---

### Post by ddrichardson on 2007-08-21
Try sheilding the wireless from the soundcard.

---

### Post by Darreln on 2007-08-21
I have had the  two cards on opposite ends of the pci receptacle string (5).  How would you go about shielding one pci card from another?

---

### Post by ddrichardson on 2007-08-21
Well, earthing the soundcard's frame to the chassis may help, but try using an insulator to block the gap between them. Alternatively and somewhat easier, change the wireless card and routers channel to see if the interference is only in one frequency range - which it probably is.

---

### Post by Darreln on 2007-08-24
I changed the channel on the router from 11 to 1 and then 6.  Neither made any difference. It currently on channel 6.  As for the grounding and/or sheilding, I haven't tried that yet.  This is my everyday computer, so I have pulled the sound card out for now and have gone back to using the onboard sound.  I will get back to this problem in the future with a grounding/sheilding plan.  Thanks for the the help.

Darreln

---

