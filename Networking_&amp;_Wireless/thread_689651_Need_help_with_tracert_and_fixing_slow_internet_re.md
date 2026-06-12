---
title: "Need help with tracert and fixing slow internet response"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by nowhere@cox.net on 2008-02-06
Hey everyone.

I'm using a Sprint broadband connection to get into my network while on the road. Im have very very slow response times for mainly ssh activities (sshfs and such).  Browsing is not too bad. I did a simple tracert to google and here is the result.

```
Hop	Hostname	IP	Time 1	Time 2
1	68-26-13-205.area1.spcsdns.net	68.26.13.205	0.108ms	
1	68.28.49.69	68.28.49.69	243.919ms	
2	no	reply	*	
3	68.28.51.54	68.28.51.54	asymm	
4	68.28.55.5	68.28.55.5	asymm	
5	no	reply	*	
6	68.28.51.18	68.28.51.18	208.058ms	
7	sl-gw10-bur-14-0-0.sprintlink.net	144.223.255.5	asymm	
8	sl-bb21-bur-10-0-0.sprintlink.net	144.232.0.70	135.983ms	
9	sl-bb20-stk-8-2.sprintlink.net	144.232.18.162	148.173ms	
10	sl-crs2-stk-0-12-0-0.sprintlink.net	144.232.4.239	155.866ms	
11	sl-crs2-sj-0-12-0-1.sprintlink.net	144.232.9.227	143.942ms	
12	sl-st22-sj-9-0-0.sprintlink.net	144.232.18.182	167.941ms	
13	no	reply	*	
14	no	reply	*	
15	no	reply	*	
16	no	reply	*	
17	no	reply	*	
18	no	reply	*	
19	no	reply	*	
20	no	reply	*	
21	no	reply	*	
22	no	reply	*	
23	no	reply	*	
24	no	reply	*	
25	no	reply	*	
26	no	reply	*	
27	no	reply	*	
28	no	reply	*	
29	no	reply	*	
30	no	reply	*	
31	no	reply	*	

```

any ideas what's with the no replies and the "asymm" for a time?  I read some posts about disabling ipv6 but they are all old. Is this still relevant?

Thanks,
Eric

---

