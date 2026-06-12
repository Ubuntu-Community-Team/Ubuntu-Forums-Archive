---
title: "Samba could save me at work, but..."
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by rogerdean on 2008-04-24
Hello folks

I've just been given a new work laptop (XP of course), but want to sideline it in favour of my own Ubuntu lappy. Only hitch right now is that I can't work out how to access our shared drives.

So far I can see -

Network Servers -> Windows Network -> NRCAF -> SHELTERPC

which is the one I want. However when I double click I get a blank pane, no items, no password prompt. I know my username and password, so how do I get Ubuntu to prompt me for these details and then connect?

I found one howto which made me suspect that my Ubuntu login had to be the same as my network ID, but surely this isn't the case? Struggling to understand, to be honest ](*,)

Can anyone point me in the right direction pls?

Allbest
Roger

---

### Post by Monicker on 2008-04-24
> **rogerdean said:**
> Hello folks

I've just been given a new work laptop (XP of course), but want to sideline it in favour of my own Ubuntu lappy. Only hitch right now is that I can't work out how to access our shared drives.

So far I can see -

Network Servers -> Windows Network -> NRCAF -> SHELTERPC

which is the one I want. However when I double click I get a blank pane, no items, no password prompt. I know my username and password, so how do I get Ubuntu to prompt me for these details and then connect?

I found one howto which made me suspect that my Ubuntu login had to be the same as my network ID, but surely this isn't the case? Struggling to understand, to be honest ](*,)

Can anyone point me in the right direction pls?

Allbest
Roger

Try the following command from a terminal, and see it if lists any shares:

smbclient -N -L SHELTERPC

---

### Post by Iowan on 2008-04-24
I frequently have better luck with the **Connect to Server** option.

---

### Post by rogerdean on 2008-04-25
thanks to you both. as guaranteed, the network has now gone down... i'll get to try those soon i hope...
cheers
roger

---

