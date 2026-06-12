---
title: "wvdial and gppp work, kppp doesn't"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by blastus on 2005-10-23
On both Ubuntu Hoary and Ubuntu Breezy, wvdial and gppp works. On Mepis kppp works. On Kubuntu Breezy, kppp completes dialing, connects (after ATDT I get CONNECT 44000 V42bis), but then instantly fails. 

I've tried looking at my settings in kppp on Mepis and comparing that to kppp on Kubuntu, and I just don't get it. Does anyone know how to make kppp work?

The pppd daemon died unexpectedly!

Exit status: 1

Oct 23 21:37:17 localhost pppd[8637]: The remote system is required to authenticate itself
Oct 23 21:37:17 localhost pppd[8637]: but I couldn't find any suitable secret (password) for it to use to do so.
Oct 23 21:37:17 localhost pppd[8637]: (None of the available passwords would let it use an IP address.)

---

### Post by blastus on 2005-10-24
I have apparently solved the problem. I changed "auth" to "noauth" in /etc/ppp/options. However, I don't think this is a permanent solution (based on the comment in /etc/ppp/options related to that setting.)

```
# Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
noauth
```

---

### Post by cdhinch on 2005-11-17
Here is the prefered method of adding noauth.

```
sudo kedit /etc/ppp/peers/kppp-options
``` 

File before
```
#noauth
``` 

File after
```
noauth
```

Charles

---

### Post by blastus on 2005-11-21
Thanks for that tip cdhinch! I'll have to try it out.

Edit: I edited /etc/ppp/options and changed "noauth" back to "auth" then edited /etc/ppp/peers/kppp-options and uncommented "#noauth" to "noauth" and it works. Thanks again cdhinch. :)

---

