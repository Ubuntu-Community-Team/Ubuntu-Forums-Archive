---
title: "Navigation via cellular phone only with disconnected LAN"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by gioloi on 2008-08-11
Hi and excuse my English..
when I use the cellular phone as a modem, I must disconnect from LAN to navigate (the phone is connected and the DNS are automatically assigned, I see it from the output of vwdial, but I can't navigate). I think the problem is that the default gateway remains that of LAN instead of It to be changed by the connection.
To navigate, I must do a ifdown eth0 before connect and ifup eth0 after disconnect. 
I need the eth0 for local networking too (file e printer sharing), but I can't use eth0 while using internet.

Can anyone help me?

Thank you in advance.

---

