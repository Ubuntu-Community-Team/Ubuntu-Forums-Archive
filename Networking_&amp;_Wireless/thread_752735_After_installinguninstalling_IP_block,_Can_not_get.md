---
title: "After installing/uninstalling IP block, Can not get on internet"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by pandorazboxx on 2008-04-11
Hello,

I recently installed IPblock. Before I installed it, I could access the internet just fine. But once I installed IPblock I could no longer get on the internet. I tried with an instant messenger, firefox, and Evolution Mail. I thought maybe my DNS servers were somehow blocked. But i couldn't figure out how to unblock it. So i decided to just uninstall IPblock. so i did the following code:

```
sudo aptitude purge IPblock 
```

and it uninstalled. But i still couldn't access the internet. I checked the usr/var/cache directory and there is still a folder for ./IPblock, but I can't delete the files inside of it. Has anyone had this problem or know any possible solution?

Thanks for any help!

---

### Post by pandorazboxx on 2008-04-12
still stuck in the 80s :(

---

### Post by 19bab79 on 2008-04-12
you could go into your network settings and try to change the dns numbers and see if that helps. try 4.2.2.2 and 4.2.2.3

---

### Post by pandorazboxx on 2008-04-12
I have it connected to my router, and I let it automatically assign a DNS though.

---

### Post by superprash2003 on 2008-04-12
are you able to ping? go to the terminal and type ping google.com and post results here

---

### Post by 19bab79 on 2008-04-12
if you can't ping google try pinging your router. you should try staticly assigning those dns numbers as well.

---

### Post by pandorazboxx on 2008-04-14
I would advise anyone that has this problem in the future to consider restarting their system :oops:

thanks though for the help!

---

