---
title: "forcing drive letters in samba/windows share"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by BarryDocks on 2009-04-03
Hi there,

hopefully this is a very basic question.  I have a small samba file/print sharing network up and running.  What I would like to do is to force the samba shareto be mounted as specific drive letter in windows, is this possible without seting up DNS?

Thanks

---

### Post by talsemgeest on 2009-04-03
In windows, you should be able to map the network drive (My computer>Tools>Map network drive) and select the drive letter you want from there. I hope that is what you are asking...

---

### Post by halitech on 2009-04-03
> **talsemgeest said:**
> In windows, you should be able to map the network drive (My computer>Tools>Map network drive) and select the drive letter you want from there. I hope that is what you are asking...

that certainly works but I think they are asking if when browsing to the server it automagically assigns a certain drive letter when they connect to it. I could be misreading it but not sure.

---

### Post by talsemgeest on 2009-04-03
Ah, well if that was the case then I'm not so sure, but if you map it as a network drive it should keep the same drive letter when it does get mounted.

---

### Post by halitech on 2009-04-03
not sure how current this is but maybe this will help (if this is what they wants)

[http://lists.samba.org/archive/samba/2004-February/081427.html](http://lists.samba.org/archive/samba/2004-February/081427.html)

---

### Post by BarryDocks on 2009-04-04
> **halitech said:**
> that certainly works but I think they are asking if when browsing to the server it automagically assigns a certain drive letter when they connect to it. I could be misreading it but not sure.

Yes this is exactly what I want.

do I add the lines under [gobal] or [data] << my share name?

Please can you explain how the lines 'logon path' & 'logon home' work?

Thanks

---

### Post by halitech on 2009-04-04
glad I made a good guess on what you wanted :)

far as any other info, I'm over my head, I found the link on google but I don't know beyond whats on that page.

---

