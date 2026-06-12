---
title: "Disable networking for a set period of time?"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by gazer22 on 2008-05-08
In pursuit of productivity...

Does anyone know a way to disable all network/internet access for a given amount of time?  Preferably reversible (during that period of time) only through something drastic like a reboot.

Example usage:
running get_to_work.sh would turn off my network/internet access for two hours.  After two hours, the network would start working again.  Prior to two hours, the only way to get networking back would be to do a re-boot.

Yes, the purpose is to prevent myself from surfing the 'net when I should be getting some work done on the local machine... ;-)

---

### Post by tamoneya on 2008-05-08
you could just do ```
sudo ifconfig eth0 down
```Then when you have finished your work```
sudo ifconfig eth0 up
```You could put this in a script with a cron job or something but I would just do it manually if it was me.

---

### Post by gazer22 on 2008-05-08
Thanks - 

That'll definitely work.  Now I'm thinking of some sort of daemon that can monitor eht0 and pull it down...  

Scheduling via "at" may be a good idea too.

---

