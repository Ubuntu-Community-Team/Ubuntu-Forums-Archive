---
title: "Cannot connect  to the internet."
date: 2010-05-16
forum: New to Ubuntu
---

### Post by SKYDOS on 2010-05-16
Just installed Linux Mint, before I had Ubuntu and the same problem with Internet
On windows it works just fine, but when I try to plug in my LAN cable in notebook(ubuntu) nothing is happening... no internet.
pls help!

**sudo ifconfig**

[IMG]http://img714.imageshack.us/img714/3223/screenshotterminal.png[/IMG]

---

### Post by TironN on 2010-05-16
Ok first of all is your router running DHCP?

If so try

```

dhclient eth0

```

and post the results!

---

### Post by SKYDOS on 2010-05-16
> **TironN said:**
> Ok first of all is your router running DHCP?

If so try

```

dhclient eth0

```and post the results!

[IMG]http://img4.imageshack.us/img4/3223/screenshotterminal.png[/IMG]

---

### Post by TironN on 2010-05-16
Hmm, its obviously not connecting to your dhcp but all seems well besides that. 

I'm really sorry but I'll have to hope some one more knowledgeable helps you!

---

