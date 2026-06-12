---
title: "radius server error"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by ryanfx on 2007-08-26
Hey all,

I just finished setting up a PEAP radius server and I'm having some trouble connecting to it with wpa_supplicant

I get the error:

```


Trying to associate with *AP's MAC* 
WPA: Failed to get master session key from EAPOL state machines
WPA:Key handshake aborted
WPA: Failed to get master session key from EAPOL state machines
WPA:Key handshake aborted
WPA: Failed to get master session key from EAPOL state machines
WPA:Key handshake aborted
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys


```


any common problems associate with this kind of error?

I followed this guide step by step

[http://ubuntuforums.org/showthread.php?t=478804](http://ubuntuforums.org/showthread.php?t=478804)

---

### Post by ryanfx on 2007-08-27
bump ?

---

### Post by wirelessmonkey on 2007-08-28
This happens when your radius server aborts the wpa handshake.  I ""looks"" like your crypto settings aren't quite right.  Are you using inner and outer identities and certs?
Without seeing your configuraton, it's kinda hard to tell.

---

