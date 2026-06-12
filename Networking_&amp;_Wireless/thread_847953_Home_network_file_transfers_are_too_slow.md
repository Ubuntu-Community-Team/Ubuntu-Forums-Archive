---
title: "Home network file transfers are too slow"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by spintriae on 2008-07-03
I've just installed openssh-server on my desktop so I can backup files from my laptop. Both machines are connected wirelessly to a router; I don't have physical access to the router. My laptop is logged in to the desktop through its static IP (192.168.1.xxx) and I'm currently uploading files, but it's painfully slow. Are the files are being transferred through the ISP? Is there a way to connect the two machines through just the router without going through the ISP if I don't have physical access to the router?

---

### Post by kevmitch on 2008-07-03
If you've ssh'ed directly to a 192.168.1.xxx ip, then it's unlikely that the ISP is involved. You can reassure yourself of this by running

traceroute 192.168.1.xxx

you'll likely get there in the first hop. 

Is it possible that you're signal isn't as strong as it could be?

---

### Post by spintriae on 2008-07-03
30 hops! I don't know what that means but it seems like a lot. Anyway to improve this?

```
traceroute 192.168.1.104
traceroute to 192.168.1.104 (192.168.1.104), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
```

---

