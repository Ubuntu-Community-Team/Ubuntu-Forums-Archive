---
title: "Can't connect to wired router..."
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by xeriouxi on 2008-10-23
Hi!

A friend of mine told me that I could use my old wireless router to connect to my brothers PC and share files and do LAN gaming etc. with it.

I plugged both our computers into it but there's a problem. I can access the admin page of the router just fine on my brothers PC (which uses XP) but I can't connect to it on mine. We both use wireless to connect to the main router downstairs so this one isn't connected to the Internet. It's a Belkin F5D7230-4. Does anyone know why he can connect and I can't?

Thanks! =)

---

### Post by prshah on 2008-10-23
> **xeriouxi said:**
>  Does anyone know why he can connect and I can't?


Are you using a _wired_ connection? (Plugged in?)

In that case, possibly because his machine has been assigned an IP address valid to the router. Here's some steps you can take:

a) Check if you're actually connected or not; Open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo mii-tool eth0
```

b) Check if you've got a valid ip address```
ifconfig eth0
``` You should see an ip address that will differ only in the last set of digits from that of your brother; eg, if the IP address on his machine is 192.168.2.2, your will be 192.168.2.x, where x can be any number from 3~255.

c) If you feel the IP address is not correct, check if you can automatically get an IP address```
sudo dhclient eth0
```

d) If that doesn't work, set an IP address manually, similar to your brother's, with the last digit changed. ```

sudo ifconfig eth0 address 192.168.2.27 netmask 255.255.255.0

```

If you still cannot connect to the admin page on the router after following all these steps, post back the information of ```
ifconfig
``` from your machine and ```
ipconfig /all
``` from your brother's (Windows) machine.

If you're using a wireless connection, please post back, the instructions change.

---

### Post by xeriouxi on 2008-10-23
Thanks very much for the detailed information, prshah!

I don't know what I did but I managed to get myself connected to the router admin page, but it took out my wireless connection to the Internet in doing so. I think I connected myself to the 'Auto eth0' connection in the Network Manager and it must have stopped my wireless from working somehow. It said my wireless was still connected (i.e. the radio button was checked) but I couldn't access the Internet... only the router admin page worked.

---

### Post by Iowan on 2008-10-23
Network Manager seems to like only one interface active at a time.  If you've re-selected wireless, you may need to (in a terminal) issue:```
/etc/init.d/networking restart
```.

---

