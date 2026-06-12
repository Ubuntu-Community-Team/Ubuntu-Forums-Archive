---
title: "Bluetooth MAP request"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by benz0 on 2014-06-03
I'd like to figure out why my kubnutu 14.04 box keeps sending MAP requests to my Samsung Galaxy S5.  I have the phone paired via Bluetooth and every few seconds I get a message on my phone saying "linuxbox-0 is requesting permission to connect to your messages".  There is a check box next to "Don't ask again" and then I can select yes or no.  If I select "Don't ask again" I don't get prompted again until I'm out of range of the linuxbox and then come back, otherwise the message pops up every 2-5 seconds.  As far as I can tell there is no way to prevent this message from coming back and it's getting annoying.

Just to provide a bit more background, I'm also using BlueProximity 1.2.5.  I was tailing system logs for any messages when the message pops up on my phone but I didn't see anything.

Does anyone know what is prompting this message to pop up?  How do I disable it?

---

### Post by accounts-z on 2014-06-18
> **benz0 said:**
> I'd like to figure out why my kubnutu 14.04 box keeps sending MAP requests to my Samsung Galaxy S5.  I have the phone paired via Bluetooth and every few seconds I get a message on my phone saying "linuxbox-0 is requesting permission to connect to your messages".  There is a check box next to "Don't ask again" and then I can select yes or no.  If I select "Don't ask again" I don't get prompted again until I'm out of range of the linuxbox and then come back, otherwise the message pops up every 2-5 seconds.  As far as I can tell there is no way to prevent this message from coming back and it's getting annoying.

Just to provide a bit more background, I'm also using BlueProximity 1.2.5.  I was tailing system logs for any messages when the message pops up on my phone but I didn't see anything.

Does anyone know what is prompting this message to pop up?  How do I disable it?

You've probably figured this out by now but the messages are being caused by BlueProximity. The RFCOMM channel you are using in the Bluetooth Device tab in BlueProximity Preferences is probably the channel the phone uses for remote messaging.  If you try other channels you can probably find one that doesn't cause the phone to prompt you. I'm using channel 12 and it seems to be silent.

---

