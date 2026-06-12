---
title: "Problems accessing my encrypted network..."
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by cfwrsfan on 2008-03-08
Hello everyone I'm new here so sorry if this is a pathetic question to ask...

My question is how come I cannot connect to my home encrypted network?  I have the WEP code and I double and triple check it, but for some reason it won't connect.  The settings are all correct (connect to WEP 128-bit and open)  but it still won't connect.  My wireless network card is an Intel PROset wireless (4935?)  but i already checked that it is compatible.  Any help or redirection to another post would be greatly appreciated.

P.S -other unprotected networks work just fine but for some reason the encrypted networks keep asking me for a passphrase after timing out every minute or so.

---

### Post by ruy_lopez on 2008-03-08
Try editing /etc/network/interfaces.

Look for lines like this (yours might not be eth1):
```

iface eth1 inet dhcp
wireless-essid router_essid
wireless-key FFF9CDEFABABAABABABABAB

```

If you don't have "wireless-essid" and "wireless-key" in /etc/network/interfaces, add them. Add your key. If it still doesn't work, try adding "restricted" after wireless-key, like this:
```

wireless-key restricted ABCAEFEACBABABABA . . .

```

Then restart the interface (replacing eth1 with your interface):
```

sudo ifdown eth1
sudo ifup eth1

```

My own wireless network doesn't work without the "restricted" keyword.

---

### Post by cfwrsfan on 2008-03-08
When I try to type in /etc/network/interfaces my computer tells me that my permission is denied...any ideas?

---

### Post by ruy_lopez on 2008-03-09
/etc/network/interfaces is a file. Edit it with an editor, like this:

```

sudo gedit /etc/network/interfaces

```

---

