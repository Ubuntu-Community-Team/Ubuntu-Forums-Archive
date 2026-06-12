---
title: "sl-modem not working on gutsy"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by Nevermore on 2007-12-22
I am really pissed that the modem package doesn't work on gutsy...
It simply doesn't compile, there are a few miles long bug about that, but seems the package maintainer doesn't care. 
SO PLEASE REMOVE HIM SINCE HE IS NOT DOING ANYTHING.
This still has been going on from tribe 3, i can't believe nobody saw this issue going on...
I tried even to install the debian unstable packages, then it compiles, but sl-modem-daemon says i don't have the module installed (i installed both sl-modem-daemon and sl-modem-source from debian unstable)..
Finally, i compiled them from source, and it DOES work, however i can't connect..
the modem keeps hanging with this message:
NO_DIALTONE
I removed from /etc/chatscript/provider all the error lines but ABORT BUSY
now the error became
NO_CARRIER
HOW CAN I USE MY WINODEM LIKE I WAS DOING ON FEISTY?

yea gutsy is nice, it has the good useless compiz activated by default, but if this is the case, that i have to give up modem in order to have compiz, well, i think you are really making a mistake.

---

### Post by mickeyWD on 2008-01-04
Hi,
I'm not compiled driver package but I'm using restricted driver automatically loaded.

I've read about ModemDialUp on the Wiki and installed gnome-ppp
because I don't know how to connect from System -> Admin -> Network
and need to execute wvdial ( at least my girlfriend can use a UI ).

I've the same error reported by nevermore:

1) NO DIALTONE 
2) NO_CARRIER
after I've changed the inizialization string.

Is really a version wide problem?

---

