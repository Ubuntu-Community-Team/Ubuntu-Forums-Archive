---
title: "Stop ICS (Internet connection sharing) on my network!"
date: 2015-06-28
forum: Networking &amp; Wireless
---

### Post by angus6 on 2015-06-28
Hello everybody

I have quite a large problem where people that use my small class c network use Internet Connection Sharing to allow their friends to use free internet. I am wondering if Linux can block Internet Connection Sharing with group policies kind of like windows server (example [https://technet.microsoft.com/en-us/library/cc770930(v=ws.10).aspx)](https://technet.microsoft.com/en-us/library/cc770930(v=ws.10).aspx)) 
I already have a localized server running apache so I can run a server for anything (Layer 3 options would be best as I have multiple L3 networks, but seriously any option would help)
Any exotic/awesome way greatly appreciated!

---

### Post by angus6 on 2015-06-28
Sorry everyone, the bracket at the end of the link ruins the link, find what I am referring to here [https://technet.microsoft.com/en-us/library/cc770930(v=ws.10).aspx](https://technet.microsoft.com/en-us/library/cc770930(v=ws.10).aspx)

---

### Post by Skaperen on 2015-06-30
tell us more about "my small class c network".  how do the users of it connect to it?  how do the friends of these users connect? what OS do the users and their friends use?

---

### Post by SeijiSensei on 2015-06-30
There is no way to institute group policies in Windows via Linux.

There is also no way to stop traffic coming from a machine that uses ICS to masquerade other computers.  All the traffic will appear to be coming from the masquerading machine; you cannot determine the origin of masqueraded packets.

Yours is a "human relations" problem not soluble by technological means.  If people are abusing your network, you either need to make them stop, or boot them from the network entirely.

---

### Post by angus6 on 2015-06-30
I hate those kind of problems! But that link I posted does work for windows server in an enterprise environment...
My small class C is an enterprise WIFI system with multi-access points behind load balance's and firewalls.

Is there any kind of distinct packet fingerprint I can find with a device using ICS such as ICMP packets? If so I could do periodic tcp dumps

---

