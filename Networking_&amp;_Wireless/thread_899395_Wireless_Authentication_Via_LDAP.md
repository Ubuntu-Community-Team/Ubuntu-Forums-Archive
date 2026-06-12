---
title: "Wireless Authentication Via LDAP"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by glal on 2008-08-24
Hello all,
  Please, is there a way to use my LDAP accounts to authenticates my wireless users ?

---

### Post by SpaceTeddy on 2008-08-24
802.11x is the protocol i think. It authenticates against radius, which can use an ldap backend - if i can not mistaken.
This is pure academical knowledge, i have never done or even attempted to do this myself. I would be interested in a howto explaining how to get this to work. Also, i think you need access points that can handle 802.11x

hope it helps...

---

### Post by glal on 2008-08-25
Thanks really, I will go through and inform you back.

---

### Post by ajrichens on 2008-10-20
Hey-

Did you ever get a chance to figure this out? I'm interested in it as well.

Thanks!

---

### Post by SpaceTeddy on 2008-10-21
i am still working on this myself, and so far i don't even understand how it should work in theory (Wifi client -> Access Point -> FreeRadius -> LDAP). I cannot get the Radius to even authenticate via a password file - let alone against an LDAP. 

So - no, i did not get anything to work (yet), but i am working on it... or something like it. 

Any help would be greatly appreciated :)

PS: what i (think i) know is that you need EAP/PEAP to be enabled in FreeRadius - since this needs TLS, you will need to compile the FreeRadius yourself as the ubuntu/debian packets have this feature disabled. But with a self compiled freeradius, i have NO idea how to acctually get this thing talking to a Client...

---

