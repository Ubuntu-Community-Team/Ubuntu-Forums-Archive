---
title: "Deleted Network Manager, How Do I get It Back???"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by 1mla4e1 on 2008-09-15
Hi, I was trying to get the wireless on my HP NC6000 working and heard that installing WICD could help. I installed it and it deleted network manager. Not only did my wireless not work but I could no longer get my regular wired net to work. So I got rid of that but seams like in order to get network manager back, you need the internet... Nice little paradox there. Any ideas? At this point I just need network manager, WIFI is not too critical, thanks!

O yeah, running HARDY

---

### Post by imdano on 2008-09-15
You can probably connect through ethernet using ```
sudo ifconfig eth0 up
sudo dhclient eth0
```

---

