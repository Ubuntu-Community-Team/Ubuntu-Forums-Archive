---
title: "kbluetoothd &amp; kpilot in Feisty"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by spidie on 2007-04-25
Hi All

I've having a lot of fun with Feisty Kubuntu on my new Macbook - most things work, although I've been putting off bluetooth sync with my Treo 650 until last.

I can see a few tutorials on setting up the Treo with ubuntu which do it the manual way setting up dialup networking etc. However, I noticed Feisty comes with new bluetooth stuff and thought maybe this might work too.

I managed to very easily pair my treo with macbook and when I start a hotsync - kbluetoothd comes up asking if I want to give the treo permission to write to the serial port - if I say yes I then get kbtserialchat window with the treo merrily attempting to connect.

Is there a way that I can link this into kpilot somehow? Does this serial port appear in /dev at all - I can't see it.

If this is a no go (which would be a shame - it's all very nice and easy) should I deinstall all the standard kbluetoothd stuff as it looks like the other methods are completely different and not dependent on this.

Many Thanks in advance
Steve

---

### Post by spidie on 2007-04-25
Just in answer to my post - I think the best way to do it is using the DUN approach. Have followed the instructions in:

[https://help.ubuntu.com/community/PalmBluetoothHowto](https://help.ubuntu.com/community/PalmBluetoothHowto)

and it all works a treat. It's a little easier in Feisty but instructions much the same. I'll update the wiki if when I get some time.

Steve

ps. I removed kbluetoothd to be safe

---

