---
title: "WPA support in Ubuntu?"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by NevroMance on 2007-01-14
I wonder about the WPA support in Ubuntu.

I can logg inn to a open nettwork, but when I try to use my WPA encrypted network I can't logg inn. I thought the "Plain (ASCII)" was for WPA, but it won't logg on to it. Just tell me if you need any more information, and I will find it for you ;)

Thanks for all the help

---

### Post by kilps on 2007-01-14
I have found network-manager capable of managing my various secure wireless connections - install it from Applications > Add/Remove ... and then press Alt-F2 and run nm-applet

hope this helps :)

---

### Post by frisket on 2007-01-31
> **kilps said:**
> I have found network-manager capable of managing my various secure wireless connections - install it from Applications > Add/Remove ... and then press Alt-F2 and run nm-applet

That's a step forward, many thanks. I had only found kwlan. 

Problem is, nm-applet is asking me for a "passphrase" whereas what my helpdesk has given me is a username and password pair. I was expecting the applet to ask me for a username and password, not a passphrase.

What is this passphrase -- something I make up? If I type in a word, it tries to connect, but the console says nm-applet 8201 warning error saving passphrase in keyring Ret=6 (I'm running this as root)

---

### Post by frisket on 2007-01-31
> **frisket said:**
> I was expecting the applet to ask me for a username and password, not a passphrase.

Problem solved: I had been told (wrongly) that the network was not using WPA. It is, so selecting one of the WPA settings in nm-applet lets me enter the assigned username and password.

Worth noting however (at least in my case) that you *must* enter your username in the Anonymous field *as well as* in the Username field. I don't know if this is required elsewhere.

---

