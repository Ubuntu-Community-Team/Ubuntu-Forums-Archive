---
title: "Web surfing is slower than Windows"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by davidryder on 2008-10-02
I've had this problem before and found the solution but I can't remember what it was. 

Even in VirtualBox running XP things are a lot faster. For instance, if I click on a link it will say "Connecting to ....." slightly longer than it does in Windows. My dedicated download speeds are the same but it seems resolving hosts or making multiple connections is just overall slower than it is in Windows. 

I installed bind9 and changed my DNS server to localhost but that hasn't made a noticeable impact.

---

### Post by superprash2003 on 2008-10-02
try using opendns servers .. 208.67.222.222 and 208.67.220.220

---

### Post by jones139 on 2008-10-02
I had a very similar problem once and it turned out that I had two entries in /etc/resolv.conf, and one of them was pointing to a computer that didn't exist any more - removing that entry from resolv.conf sorted it.

---

