---
title: "RTL8821CE Issues with Wi-Fi connection"
date: 2019-04-09
forum: Networking &amp; Wireless
---

### Post by rebellious.ben on 2019-04-09
Everytime I start my HP Laptop it works perfectly, but, when I awake the machine from sleep I have to put the machine to sleep again & awake it for the Wi-Fi to work again.  Or i can just restart the machine and it will work again.  This is a minor issue but I would like to get this fixed if possible. I have posted this problem before but I was not able to resolve it.  My laptop is only a few months old so It's not a old machine, I am hoping to fix this issue.

---

### Post by kc1di on 2019-04-09
You can also just restart NetworkManager with this command in a terminal and see if that works for you.

```
systemctl restart NetworkManager 
```

---

### Post by rebellious.ben on 2019-04-20
I will try this next time I have this issue & get back to you. Thanks.

---

### Post by rebellious.ben on 2019-04-21
I tried using the command & It still did not work. I had to close the lid & re open it again for the network to work again.

---

