---
title: "Access shared folders from wireless storage enclosure on Gutsy?"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by Ningen on 2008-08-23
Yeah... I'm a newb.

My house recently got a D-Link DSM-G600 Storage Enclosure, and it has about 2 TB of memory on it, so I obviously want to be able to access it. On XP, you only have to go to My Network Places to get to it, but I can't find an equivalent of that on Ubuntu. Can you please tell me how I might be able to access it?

---

### Post by bab1 on 2008-08-24
I assume the D-link has Windows based shares.  To use ubuntu's client you will need to install the smbfs/cifs client.

From the command line try: ```
sudo apt-get install smbfs
```

This should install the client and any dependencies.  Then you should be able to browse to find it.  Try Places>>Network.

Hope this helps.

---

### Post by Ningen on 2008-08-24
Thank you, that worked! I didn't know about the Network folder in Places either ^_^;;

---

### Post by bab1 on 2008-08-24
Mark it solved and say thanks (please).  :D

---

