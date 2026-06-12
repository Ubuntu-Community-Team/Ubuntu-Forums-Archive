---
title: "Ubuntu equivalent of &quot;ipconfig /renew&quot;?"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by anon0 on 2009-01-27
On Windows you can disable/renable the NIC in control panel/networking, and release/renew the IP address with ipconfig. How do you do these in Ubuntu?

---

### Post by xbalboa on 2009-01-27
I don't know about the command-line equivalent, but you should be able to disable and re-enable your network via the NetworkManager GUI

---

### Post by blueridgedog on 2009-01-27
You can release the dhcp lease with:
```

$ sudo dhclient -r
```

Then renew it with:

```
$ sudo dhclient 

```
or just do it all with

```
$ sudo /etc/init.d/networking restart
```

---

