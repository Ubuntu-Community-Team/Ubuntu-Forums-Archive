---
title: "torrents - bypass Comcast RST Packets"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by HokeyFry on 2007-09-21
hi

i unfortunately have Comcast as my ISP:mad:

they dont like torrents:mad:

i read in [this thread]("http://ubuntuforums.org/showthread.php?t=531467&highlight=comcast%2C+torrents") that you can turn away the RST packets. i would like to know how to do this.

can anybody help me turn my :mad: into :guitar:

thanks for any help in advance

---

### Post by HokeyFry on 2007-09-21
i found [this]("http://www.linuxtopia.org/Linux_Firewall_iptables/x4550.html"), i feel that this is on the right track, but it looks like it would be rejecting any incoming connections on that port. how would i use this to reject RST packets only?

---

### Post by psusi on 2007-09-21
You can not ignore resets; it is how connections are normally closed.  Comcast is literally closing the connection for you, and there is nothing you can do about it.

---

### Post by HokeyFry on 2007-09-21
](*,)


crap, that makes me sad.

i still think though there is a way, im determined lol

---

### Post by Uncle_Eck on 2008-06-15
What that last guy said is pure bull***t. :lolflag:
RST is NOT how a connection is closed. It IS how Sandvine, that Comcast uses, closes your connection.:mad:
The proper TCP flag for ending a session is 'FIN' not 'RST'.
You can ignore RST packets but the server you are connected to will need to be ignoring them as well.



> **HokeyFry said:**
> ](*,)


crap, that makes me sad.

i still think though there is a way, im determined lol

---

