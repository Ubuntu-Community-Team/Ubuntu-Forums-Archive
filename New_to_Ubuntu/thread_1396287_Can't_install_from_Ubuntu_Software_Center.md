---
title: "Can't install from Ubuntu Software Center"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by rudhra on 2010-02-01
hii friends.....i m using ubuntu 9.04....i m unable to install softwares and even updates...i m encountering a problem states that u should have 324mb free space in '\'....but i have 29.12gb free space......and even not able to download softwares and install them....please help me

---

### Post by overdrank on 2010-02-01
Moved to Absolute Beginner Talk

---

### Post by NightwishFan on 2010-02-01
Try these instructions, if you have dial-up or slow internet, I would advise you not to continue, as you may want the cache available.

Go to "Applications -> Accessories -> Terminal"

When the terminal opens type:
```
sudo apt-get clean
```

Press enter, and you will asked for your password. It will not show up when you type, but it is there. This will clear any downloaded packages in the cache.

If that clears up your issue, then you had a lot of packages in the cache. If not, then we can debug otherwise. Should be a simple solution, as you might have the /var/cache/apt folder on a different partition.

---

