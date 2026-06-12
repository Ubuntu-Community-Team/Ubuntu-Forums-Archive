---
title: "Can't make PCMCIA 3G data card work"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by hchaseshields on 2009-09-15
I installed Jaunty two weeks ago and have everything working except my data card. 

The card is Japanese, a Kyocera w05k PCMCIA card (QUALCOMM 3G CDMA) for use on the the au network here in Japan. When I insert the card the log reads:

Sep 16 10:52:54 cmoney-laptop kernel: [ 5229.307124] pcmcia_socket pcmcia_socket0: pccard: card ejected from slot 0
Sep 16 10:53:39 cmoney-laptop kernel: [ 5274.796062] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
Sep 16 10:53:39 cmoney-laptop kernel: [ 5274.796401] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
Sep 16 10:53:40 cmoney-laptop kernel: [ 5274.954956] 0.0: ttyS3 at I/O 0x2e8 (irq = 4) is a XScale
Sep 16 10:53:40 cmoney-laptop kernel: [ 5274.955284] 0.0: ttyS1 at I/O 0x2f0 (irq = 4) is a XScale

And when I go to GNOME PPP to dial, it can't detect a modem. It Windows, it runs via the Standard PCMCIA Modem Driver. The card currently works on a windows system.

Searched threads, but couldn't come up with anything useful, probably due to my inexperience (this is week two with Ubuntu). Thank you for your help!

Cheers,

Chase

---

