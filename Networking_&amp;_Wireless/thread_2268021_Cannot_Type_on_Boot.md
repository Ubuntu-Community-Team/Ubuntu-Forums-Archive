---
title: "Cannot Type on Boot"
date: 2015-02-09
forum: Networking &amp; Wireless
---

### Post by Justin_Yarrington on 2015-02-09
> **Hadaka said:**
> and change your router encryption from TKIP  to wap2

Thank you for the quick reply. I can't change the router options. Does it work without changing the encryption?

Nevermind I have figured it out from this post
[http://ubuntuforums.org/showthread.php?t=1850379](http://ubuntuforums.org/showthread.php?t=1850379)
Thanks again for the help.

> **sandyd said:**
> Good, we can now make it permanant.

Run this
```

sudo sed -i 's/\<splash\>//g' /etc/default/grub && sudo update-grub
```


Didn't even see this reply! I'm sorry! thanks though!

---

