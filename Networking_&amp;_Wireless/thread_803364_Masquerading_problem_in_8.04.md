---
title: "Masquerading problem in 8.04"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by DriftingDutchman on 2008-05-22
Hi, I am trying to forward traffic from 192.168.0.0/24 through ath0 (192.168.1.52). I have been able to do something similar in Edgy, Feisty, and Gutsy. 

In Hardy I have no such luck.

Besides the fact that I am using a wifi card as the outgoing interface instead of an ethernet card, nothing has changed AFAIK.

cat /proc/sys/net/ipv4/ip_forward returns 1

I have used shorewall with webmin just as in the past. When masquerading still turned out not to work, I tried direct IP tables manipulation, firestarter, and ufw as well. Now I am back with shorewall and tried changing ath0 into wifi0 because options seem to be running out.

Any help would be appreciated.

---

### Post by SpaceTeddy on 2008-05-22
mhm, can you please post the output of
```
ifconfig
```
to confirm the names and ip-addresses of your network devices.

also, can you please post your current iptables configuration from these commands:
```
sudo iptables -L
sudo iptables -L --table nat
```

thanks :)

---

### Post by DriftingDutchman on 2008-05-22
Thank you for your quick response.
Please find the requested outputs attached.

Thanks!

---

### Post by pyramid6 on 2008-05-22
I think iptables or the kernel is broken.  I've spent the last 5 hours trying to get port forward to work on 2 different system with no luck.  Unfortunately, they are both up to date.  Anyone know what happened?  

My iptables is 1.3.8, and my kernel is 2.6.24-16-generic.

Thanks

---

### Post by pyramid6 on 2008-05-23
I got it to work.  It appears I needed to restart the server.  Not sure why that helped, but it did.

---

### Post by DriftingDutchman on 2008-05-23
I'm using 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 and have tried 2.6.24-16 as well. Rebooted a few times too. I am using iptables 1.3.8.0debian1-1ubuntu2, so everything is up to date.

---

