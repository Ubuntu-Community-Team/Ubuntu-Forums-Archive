---
title: "Downgrading from Namaroka for a beginner."
date: 2010-03-10
forum: New to Ubuntu
---

### Post by Zappanale on 2010-03-10
Hi, I've had a few problems with Namaroka while using 9.10, and would prefer to go back to the previous firefox. 

Could anyone please give a newbie friendly guide to doing this? Thanks.

---

### Post by wolfkstaag on 2010-03-10
Go to System->Administration->Synaptic Package Manager and "Completely Remove" Namaroka/Firefox 3.6 or whatever it's calling itself this week.

Go to System->Administration->Software Sources and click the "Other Software" tab. Uncheck anything that says "Mozilla" in it.

Open a terminal and put in:

```
sudo apt-get install firefox-3.5
```

Should work after that. :)

---

### Post by lovinglinux on 2010-03-10
As already posted, disable *ubuntu-mozilla-daily* ppa from Software Sources, remove *firefox* package and install it again. Doing a re-install of *firefox* package should also work.

---

