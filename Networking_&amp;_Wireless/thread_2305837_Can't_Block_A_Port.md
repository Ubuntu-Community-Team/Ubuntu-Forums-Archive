---
title: "Can't Block A Port"
date: 2015-12-09
forum: Networking &amp; Wireless
---

### Post by shane_faulkinbury2 on 2015-12-09
I just started using UFW and I need to learn how to block a 4 digit port.  Here is a screenshot of the port I'm trying to block and a screenshot of other 3 digit ports I have blocked.

---

### Post by QDR06VV9 on 2015-12-09
```
sudo ufw deny ####(Port)
```

To write deny rules, you can use the commands you have except you need to replace "allow" with "deny".


For example to deny HTTP connections, you could use this command:

```
[FONT=Verdana]sudo ufw deny http[/FONT]
```

Or if you want to deny all connections from 15.15.15.51 you could use this command:

```
sudo ufw deny from 15.15.15.51
```

More info here [https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-14-04)
Also you can block or even close ports by way of your Router, And you may have to google your router name on some..

Hope that is what you wanted
Regards

---

### Post by shane_faulkinbury2 on 2015-12-09
I just put in this command and the IP is gone now!```
iptables -A INPUT -s 9001 -j DROP
```

---

### Post by QDR06VV9 on 2015-12-09
If memory serves correctly 9001 Belongs to Tor?? Could be wrong..
If you ever need to see all established connections
```
sudo lsof -i| grep ESTABLISHED
```
And you check Probe on that port here [https://www.grc.com/x/portprobe=9001](https://www.grc.com/x/portprobe=9001)
It should at the very least show [B]'Stealth'can
[/B]And as Always you can get more info with
```
man ufw
```
Regards

---

