---
title: "Password issues"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by badgerzilla on 2008-08-18
Okay- i am definitely new to linux, so bear with me.

I have a fresh install, am using the preloaded driver (with ubuntu) for an Atheros-chipset card. The card recognizes my network, and when I attempt to connect to it, it requests a password (WEP). However, the password that functions under Windows does not do the trick here, and as well, it's a 10-number string and the options are all 64-bit or 128-bit, not 80-bit.

Sorry if this is a RTFM question, but I am mystified.

---

### Post by Nye28 on 2008-08-18
We're having the same problem with Kbuntu.  It gives us the option of passphrase and a 40-bit and 140-bit key... the way our linksys AP is set up is that it has a 128-bit key.. and the passphrase we set up fails.

---

### Post by HalPomeranz on 2008-08-18
64-bit and 128-bit refer to the strength of the steam cipher used to protect the connection, not the password that you type in.  It sounds like you want to choose the "WEP 64/128-bit Hex" choice for "Wireless Security" and then enter the password into the appropriate box.

---

### Post by badgerzilla on 2008-08-18
Thanks, I'll try it. It's been depressing to see that shiny new computer I built lay unused 'cuz I don't have interwebs.

EDIT: Typing from the boxen- that was exactly what Ineeded to do. Thanks again!

---

