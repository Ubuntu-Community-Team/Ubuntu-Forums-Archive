---
title: "A question about the repository"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Gaphumbala on 2009-03-11
After installing 8.10 there were 263 updates to be downloaded and installed.  The download speeds were bad to the point of 600 Bytes/sec, and downloading for about 15 sec. and no activity for 10 minutes!  At one point the estimated time to completion was over 46,000 days!  I don't think I have that much time left on this planet.. :-)  So, my question is this, are there mirrors that one can download from the repos from?  And if so, how do you make the manager use them?  Thanks!

---

### Post by iaculallad on 2009-03-11
Try changing your download Server:

System->Administration->Software Sources

Under the Ubuntu Software tab, try to select **Main Server** from "download from:" option then click on Close button. Now, open your terminal and rerun update:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Kareeser on 2009-03-11
In my experience, the Main Server and the default Canadian server are both quite slow.

There's an option in that dialogue to request Ubuntu ping multiple servers for the fastest one. Give that a shot :)

---

### Post by Gaphumbala on 2009-03-11
I found the Software Sources box and played around with it and it seems Germany was the quickest.  Thanks for the info!

---

### Post by SunnyRabbiera on 2009-03-11
Yeh personally I use multiple mirrors just in case, I use UK mirrors, European mirrors, and sometimes South American when the US servers seem to be on the fritz.

---

### Post by mlentink on 2009-03-11
> **SunnyRabbiera said:**
> Yeh personally I use multiple mirrors just in case, I use UK mirrors, European mirrors, and sometimes South American when the US servers seem to be on the fritz.


Ah! So *that's* what's slowing down our mirrors!

;-)

---

