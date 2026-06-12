---
title: "Speedtouch scripting?"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by melat0nin on 2007-05-08
Hi all

I've installed Ubuntu on my mum's machine (yay.. another one converted!) and got her Speedtouch 330 usb modem working (it was surprisingly easy, and having it online permanently is very LAN/router-like which is nice) but the problem is if the modem disconnects for whatever reason, she'll not know what to do to get it to reconnect.

There are terminal options:

Dial the connection:
```
sudo pppd call speedtch
```

Disconnect:

```
killall pppd
```

Is it easy enough to create shortcuts to these commands, with feedback from the machine on what's happening?  I don't know anything about linux scripting, but it would be nice if there was a desktop icon which would execute each command, and perhaps provide a message saying "You are now connected" or "ADSL disconnected" when the relevant event happens, just to make sure she's not totally in the dark as to what's going on.

I found a thing called Gnome PPP in Automatix2 but it seems to be useful only really for dial up connections, although in theory I reckon it could be made to work with USB ADSL modems.  Trouble is, it doesn't detect the Speedtouch at all and seems to be totally oblivious to either its presence or the connection, so that option seems not to be much help.

Any ideas?

Help much appreciated!!

-m

---

### Post by melat0nin on 2007-05-08
Any ideas?

---

### Post by melat0nin on 2007-05-08
In the end I simply made two text files with those commands, made them executable, and created shortcuts to them.  Pretty simple!

---

### Post by melat0nin on 2007-05-08
Trouble is I can't get it to execute the script without asking whether the user wants it executed or displayed.  Is there some way round this?

---

