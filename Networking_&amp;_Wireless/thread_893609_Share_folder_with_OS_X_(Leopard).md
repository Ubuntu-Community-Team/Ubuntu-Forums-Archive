---
title: "Share folder with OS X (Leopard)"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by shaker108 on 2008-08-18
Hi,

I have just switched from using Fedora to Ubuntu and I'm having trouble sharing a folder with my Mac. I have tried right clicking the folder I want to share and set the sharing options but its not appearing in the Finder on my Mac. I also tried to use the Samba Server Configuration app but no luck

Any suggestions?

---

### Post by sea_monkey987 on 2008-08-18
I have no idea how sharing works with a mac but I'll try to help you.  Am I correct in assuming macs can connect to windows shared folders?  please post the output from typing this in the terminal:```
cat /etc/samba/smb.conf
```

---

### Post by shaker108 on 2008-08-18
Edit: Now I know why it didnt automatically show up in the finder. I had forgotten to add a samba.service file in "/etc/avahi/services" :p

---

