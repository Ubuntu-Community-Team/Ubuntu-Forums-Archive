---
title: "Change mac address on boot?"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by strm on 2007-05-22
Hello,
I am trying to find a simple way to change the mac address on my network card (eth0), without having do it every single time i boot into ubuntu (using ifconfig eth0 down; ifconfig eth0 hw ether newmacaddr; ifconfig eth0 up).

The simplest quote unquote solution i have found was adding the line "hwaddress newmacaddress" to my /etc/network/interface file however that only seemed to work for 1 boot, now i am back to doing it manually with the above method.

Some tips will be appreciated, thanks.

---

### Post by Znupi on 2007-05-22
```

sudo gedit /etc/rc.local

```
Add this to the file (before the 'exit 0' statement):
```

ifconfig eth0 down hw ether <new_mac_addr>
ifconfig eth0 up

```
Save and close. That should do it.

---

### Post by strm on 2007-05-24
Doesn't seem to work, right after I log in, I check *ifconfig* whether the hardware address is changed, and it is. However, when I right click on the network icon on one of my panels and click connection information, it still displays the old address.
To get it to work I have to bring down eth0 and then back up again manually (*ifdown eth0; ifup eth0*) after which the connection seems to start working (the university only assigns IPs to machines with known mac addresses on wired connection).

---

### Post by Znupi on 2007-05-24
That's strange, it should've worked. I had the same problem but I used to do it manually, I didn't know about the rc.local file. The only thing I can think of is pausing a little between the two commands:
```

ifconfig eth0 down hw ether <new_mac_addr>
sleep 3
ifconfig eth0 up

```

---

### Post by strm on 2007-05-25
everything works now, thank you, however the "Connection Information" still shows the old HW address, ifconfig shows the correct one.

---

### Post by Znupi on 2007-05-25
At least it works :). You can play around with the delay time if you really want "Connection Information" to show the new address...

---

