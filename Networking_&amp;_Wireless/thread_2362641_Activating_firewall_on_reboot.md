---
title: "Activating firewall on reboot"
date: 2017-05-31
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2017-05-31
I put "sudo ufw enable" into the startup apps.  Each time I reboot/ start Ubuntu  16.04 I discover that ufw is disabled. It does not allow traffic in or out. I have to enable it manually. 

How do I ensure it is automatically active on reboot?

---

### Post by Rex Bouwense on 2017-05-31
sudo ufw enable will enable the firewall.  How are you checking after you reboot?  Look in  /etc/ufw/ufw.conf  If the setting is ENABLED=yes then you should be good to go.  You should not have to manually place it in the start up aps.  sudo ufw status verbose will tell you that it is active

---

### Post by Robbyx on 2017-05-31
I have checked the ufw.conf. The setting is ENABLED=yes, but when I boot up and run **sudo ufw status **the answer is **inactive**. 

Can you please suggest how I should ensure that it is active on startup in these circumstances.

---

### Post by #&amp;thj^% on 2017-05-31
> **Robbyx said:**
> I put "sudo ufw enable" into the startup apps.  Each time I reboot/ start Ubuntu  16.04 I discover that ufw is disabled. It does not allow traffic in or out. I have to enable it manually. 

How do I ensure it is automatically active on reboot?

Did you remove this: "sudo ufw enable" from the startup?
When using systemd try this:

```
sudo systemctl enable ufw
sudo systemctl enable ufw.service 
```

---

