---
title: "Internet Connection Sharing with Vista host"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by wabbit46 on 2009-02-08
I am trying to share an internet connection with a windows vista host.

I have set up a static IP address and normal networking works fine.

I have added the windows IP address as the default gateway.

When I edit /etc/dhcp3/dhclient.conf and change the line "prepend domain-name-servers" and restart networking it tells me resolv.conf does not exist. The internet connection does not work.

Is there some module I must load before I can get this sharing to work?

---

### Post by yeats on 2009-02-08
The /etc/resolv.conf file is where Ubuntu looks for domain nameserver information.  Mine has a single (uncommented) line:

```
nameserver 192.168.1.1

```

perhaps you could open (with sudo) /etc/resolv.conf with your favorite text editor, substituting the Windows IP?

Try that and see what it does.

---

### Post by wabbit46 on 2009-02-08
Thanks that solved it.

---

