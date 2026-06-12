---
title: "ZD-1201 / Zyxel USB dongle working."
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by DarkN00b on 2006-09-13
I'm really sorry for this, but I posted a solution for my wireless problem in the Absolute Beginners forum when it should have been here. Anyway, this applies to the ZyXel B-220 wireless dongle and any adapter using the ZyDas 1201 chipset.

The original post can be found [here]("http://www.ubuntuforums.org/showthread.php?t=256025&highlight=b-220").

---

### Post by DarkN00b on 2006-09-19
Just a bump to update the above linked post. I updated my machine this morning and found my wireless was broken. Here's how I fixed it. Follow the instructions at the link above until you reach:

```
sudo cp *fw /lib/firmware/`uname -r`
```

Instead, type in:

```
sudo cp *fw /lib/firmware/2.6.15-27-386
```

You'll probably have to do this for every kernel update, substituting the latest firmware directory each time.

---

