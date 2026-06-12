---
title: "[SOLVED] Wireless problems in 8.04"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by riminicat on 2008-11-01
I have an open network in my apartment with both my computers connected to it.  My windows partitions connect with no problems but when I try to connect in Ubuntu it asks for a password but I haven't set one.  I've got a linksys router if that means any thing to any one.  Does any one know how to fix this?

---

### Post by thon0925 on 2008-11-01
You may want to try the latest release, as it has a reworked network manager or you could add a password to your network and see if it works then. Have you tried just typing some letters when it asked for a password?

---

### Post by coolvinod00 on 2008-11-01
> **thon0925 said:**
> You may want to try the latest release, as it has a reworked network manager or you could add a password to your network and see if it works then. Have you tried just typing some letters when it asked for a password?

Hi,
I had the same problem. I could fix it by carefully following the steps 1,2,3 in [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction:](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Introduction:))

---

### Post by riminicat on 2008-11-01
Hey guys thanks for the reply's, I'm going to try them and see what I get.  I have tried typing in some random letters but it wont let me on. I just found out my neighbor has the same router too, I think Ubuntu is getting them confused.

---

### Post by thon0925 on 2008-11-01
Go into your routers settings and change the name and channel its on, so Ubuntu will be able to tell the difference between the 2 routers.

---

### Post by riminicat on 2008-11-02
No luck now I can't connect to any thing.  I'm downloading 8.10 right now to see if it works better.  I have wicd now but still no luck.

---

### Post by riminicat on 2008-11-02
Hey thanks for the help guys, especially thon0925.  I have 8.10 on disk and I'm installing it. My wireless card isn't supported but I know how to get around that.

---

### Post by riminicat on 2008-11-02
Wow, after all this trouble I find a simple explanation.  I am dual booting Vista/ubuntu and it turns out I didn't tell windows to release my IP address on shutdown, so the router wouldn't give me a new one when I was in Ubuntu.  Fixed it.

---

