---
title: "ubuntu werewolf 15.10 keeps dropping internet connection"
date: 2015-12-21
forum: Networking &amp; Wireless
---

### Post by ryschwoch on 2015-12-21
I am very new to using ubuntu. So far I like how it works, as I have always been a Windows guy. I installed it on a Dell laptop I have, and although I am currently typing this post using that laptop over wifi, it randomly stops working on the internet. To fix I disconnect from my network and reconnect, and then the internet connection starts working again. It is seemingly random in timing. Any help would be a plus, wondering if I have some sort of a driver issue.

---

### Post by Bucky Ball on 2015-12-21
Welcome. Perhaps we have a preliminary look at what you have so far. Please open a terminal and copy/paste this in (contol+shift+c and p respectively):

```
sudo lshw -C network
```

You will be asked for your password. When you type, it will be invisible. That's normal. Post output between [code] tags (see last link in my signature).

Also, have a read of [this networking sticky]("http://ubuntuforums.org/showthread.php?t=370108"). :)

---

