---
title: "Little help with my wireless"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by Takebacker on 2008-05-20
Now, i've read the guides as well as [this one]("http://www.linlap.com/wiki/Configuring+the+ndiswrapper+driver+for+wireless+controllers+without+native+Linux+drivers") and [even this one which is more specific for my computer.]("http://www.linlap.com/wiki/HP+Pavilion+dv1000")

I'm using an hp pavillion dv1000 and i've already recognized the card but the problem is with actually connecting to the network. It requires a WEP key and every time i type it in it spits it back out asking for it again.

Thanks for any help. :D (running ubuntu 7.10 i think if that helps)

---

### Post by mapes12 on 2008-05-20
Hi 

Try this thread:

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

---

### Post by Takebacker on 2008-05-20
> **mapes12 said:**
> Hi 

Try this thread:

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

Well now that looks EXTREMELY promising...thanks for that mate. I'll try that later if ndiswrapper doesn't work like it should.

---

### Post by Ayuthia on 2008-05-20
> **Takebacker said:**
> Now, i've read the guides as well as [this one]("http://www.linlap.com/wiki/Configuring+the+ndiswrapper+driver+for+wireless+controllers+without+native+Linux+drivers") and [even this one which is more specific for my computer.]("http://www.linlap.com/wiki/HP+Pavilion+dv1000")

I'm using an hp pavillion dv1000 and i've already recognized the card but the problem is with actually connecting to the network. It requires a WEP key and every time i type it in it spits it back out asking for it again.

Thanks for any help. :D (running ubuntu 7.10 i think if that helps)

Have you tried it from the Terminal:
```
sudo iwconfig wlan0 essid <name> key <passkey>
sudo dhclient wlan0
```

Replace <name> with the name of your router and <passkey> with your key.

---

