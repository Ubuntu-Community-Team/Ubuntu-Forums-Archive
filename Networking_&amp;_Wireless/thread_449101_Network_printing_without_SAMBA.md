---
title: "Network printing without SAMBA?"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by BroadArrow on 2007-05-19
Is there a practical way to share a printer connected to an Ubuntu server with Windows machines without using SAMBA?

My wife's work laptop is set up with her work's workgroup settings so she can't see the our home workgroup which the Ubuntu server uses.

However, I see that it is possible to add a printer with an [http://.](http://.).. address -- does this mean it's possible to somehow share a printer over http or some other protocol without having to use SAMBA?

---

### Post by dolphin_oracle on 2007-05-19
as long as you are using cups on your ubuntu machine, you can share the printer that way.  Make sure cups is allowing you to share your printer and note the name it has.  Then in Windows, add a new printer, specify a network printer and use an address like

[http://xxx.xxx.xxx.xxx/printers/printername](http://xxx.xxx.xxx.xxx/printers/printername)

Specify the proper driver in the wizard and you should be good, no samba required.

I print from a xubuntu box and two windows boxes to a ubuntu connected printer this way.

good luck.

---

### Post by dmizer on 2007-05-20
use the cups interface ... [http://server:631](http://server:631) to configure your printer, and allow sharing.

you'll have to add your ubuntu user to the cups group like so:
```
sudo adduser cupsys shadow
sudo adduser <yourusername> lpadmin
sudo sudo /etc/init.d/cupsys restart
```

then you can add the printer in windows with the url [http://server:631/printers/printername](http://server:631/printers/printername)

---

### Post by BroadArrow on 2007-05-25
Thanks for that. I had no idea Windows could use a CUPS shared printer. I'll give it a go.

---

### Post by tagra123 on 2007-05-27
Did this work for you?   I haven't been able to get printing via IPP or http since breezy.

---

### Post by BroadArrow on 2007-05-27
> **tagra123 said:**
> Did this work for you?   I haven't been able to get printing via IPP or http since breezy.

Yep. It worked. The server is using FF and is up to date.

---

### Post by tagra123 on 2007-05-29
What kind of printer?

 My printer is an HP and this does not work. I went ahead and tried again but same result -- blank pages from remote machine. Does the same on a clean install. Many seem to have trouble with the HP and the current cups. I'm still waiting to get a clear answer as to why. It's odd beacuse local printing works fine, samba printing works from  remote machine but remote printing using cups http doesn't .

---

### Post by BroadArrow on 2007-05-29
The printer is a fairly old HP LaserJet 5M Plus.

Sorry, I don't know enough about how CUPS works to know what might help in your case. I didn't even know it was possible to share a printer with a Windows machine using CUPS until reading the responses to this thread!

---

### Post by tagra123 on 2007-05-30
I had a laser jet in the shed, maybe I should give it a try.  When someone gets the printer  to work with ipp-- the way it should - I just try to find out what is  working. 

I ended up resorting to a very odd method of sharing that seem to work every time and is not dependant on cups.

---

