---
title: "Pidgin Gtalk Issue"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by gaffurabi on 2009-04-13
i moved to a new home and i currently use ADSL (thus a modem, before it was internet thru LAN) and i am pretty sure the reason i cannot connect to gtalk is this:

[http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#WhycantIlogontomyGoogleTalkGoogleAppsaccountanymore]("http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#WhycantIlogontomyGoogleTalkGoogleAppsaccountanymore")

when i do ```
dig +short SRV _xmpp-client._tcp.gmail.com
``` it does not return any results. can anyone help me how to *"Use Router as DNS Server"*, -as stated on pidgin help-?

---

### Post by gaffurabi on 2009-04-13
anyways i got the solution from the pidgin irc channel. 

**temporary solution:**

set 'talk.google.com' to *connect server* field.

**permanent solution:**

go thru your modem documentation in order to disable "Use Router as DNS Server". Usually done by [http://192.168.2.1/](http://192.168.2.1/) and setting it up.

---

