---
title: "WPC54G version 2 problems"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by xnszxdotnet on 2008-02-22
I have been following this guide...
[http://blog.eksfiles.net/2007/12/30/using-the-linksys-wpc54g-v2-and-wpa-with-ubuntu-gutsy/]("http://blog.eksfiles.net/2007/12/30/using-the-linksys-wpc54g-v2-and-wpa-with-ubuntu-gutsy/")

I've got to the part about "ndiswrapper -l" on step 8 and I get this:

```
booger@lappy:~/linksys$ ndiswrapper -l
lstinds : invalid driver!
```

i'm lost on what to do now. I have used this guide on a different install on the same harware before with no problems. please help. the card shows up in the " lspci "

---

### Post by longboneslinger on 2008-03-30
> Before we go any further, we need to fix up a couple of things. First, rename tnet1130.sys to TNET1130.sys, and rename tnet1130x.sys to TNET1130X.sys. Then edit the LSTINDS.INF file and change all instances of “tnet1130&#8243; (regardless of case) to “TNET1130&#8243; (all uppercase), and likewise all instances of “tnet1130x” to “TNET1130X”.

My first suggestion is the one that worked for me. Go back through LSTNDS.INF and triple check that you renamed ***_all_*** instances of tnet1130 and tnet1130x.sys to upper case. Also make sure the actual files themselves are both upper case.

I had the same problem on the same card. It turned out that I missed one instance of tnet in LSTINDS.INF and it was killing everything. After that, I was up and running. Now if I can just get wpasupplicant to cooperate so I can get an encrypted connection besides WEP. 

Good luck and don't give up. That cards a pain.
bOnE

---

