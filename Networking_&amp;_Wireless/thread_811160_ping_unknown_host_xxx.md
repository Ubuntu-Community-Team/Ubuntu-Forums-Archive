---
title: "ping: unknown host xxx"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by molotov00 on 2008-05-28
A ping to Google.com and others works just fine. A ping to any of the other computers on my network fails with: "unknown host <hostname>"

I know the fix is probably dead easy, I just don't know where to look. I'm running xubuntu and am comfortable with the terminal. I've configured much more difficult things... just don't know where to look to fix this.

Resolving hostnames works for all other computers on the network, which are a mix of linux and windows machines.

Thanks,
M

---

### Post by Iowan on 2008-05-28
Check in your **/etc/resolv.conf**.  Mine has a **search myDomain** line.

---

### Post by molotov00 on 2008-05-31
I've continued to try to figure out this problem. I am not part of a domain. I also thought the issue may be a range extender I have for the wireless but I ruled that out today by removing it from the network.

Also, I can report that other computers on the network cannot ping this machine by its hostname. I also thought that it may have been a subnet issue but everything is on the same subnet.

If I add the other computers on the network to this computer's hosts file then the ping works fine. But this is not a viable solution because the IPs are dynamic.

I have a WRT54G acting as a DHCP server. 

Again, if anyone can help with this it would be much appreciated. I am sure it's not terribly difficult. I'm just not sure where to take this next. My Ubuntu server (7.10) never had this problem and the network has not changed, if that helps...

Thanks,
M

---

### Post by Iowan on 2008-05-31
> **molotov00 said:**
> ...Also, I can report that other computers on the network cannot ping this machine by its hostname... The default **/etc/dhcp3/dhclient.conf** file does not send hostname to server.  You can find, uncomment, and change this line to send the proper hostname - hopefully this will let other machines ping this one by name:
```
#send host-name "<hostname>";
```

---

### Post by molotov00 on 2008-05-31
I've made this change. So far it doesn't make a difference, but I'll leave the change intact as it may still have been part of the problem. Thanks.

---

### Post by Iowan on 2008-05-31
I presume you restarted networking after making the change?

---

### Post by molotov00 on 2008-05-31
Yessir ;)

I'm not quite sure what's going on but fortunately this is a 5 computer network so even though DHCP is enabled the addresses the computers get tend to be consistent. I'm not too worried about this one in the near term, although it is something I'll want to figure out eventually.

---

