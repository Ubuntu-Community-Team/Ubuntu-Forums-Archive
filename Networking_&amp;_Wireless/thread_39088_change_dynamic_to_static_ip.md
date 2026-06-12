---
title: "change dynamic to static ip"
date: 2005-06-03
forum: Networking &amp; Wireless
---

### Post by nianhbg on 2005-06-03
Hello I installed an ubuntu server on my machine im having dynamic ip from my dhcp server but i would like to change it to static ip insted.

I have tried this in my /etc/net/resources

.
.
.

# iface eth0 inet dhcp
iface eth0 inet static
adress 192.168.0.5
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

auto eth0

but my networkcard would not start up. When i do this

iface eth0 inet dhcp
# iface eth0 inet static
# adress 192.168.0.5
# netmask 255.255.255.0
# broadcast 192.168.0.255
# gateway 192.168.0.1

# auto eth0

it runs ok but with dynamic ip
any ideas?

---

### Post by dataw0lf on 2005-06-03
/etc/net/resources ??? Do you mean /etc/network/interfaces ?
Anyways, switch 'adress' to 'address' in your interfaces file.

---

### Post by BabyUbuntu on 2005-06-03
or .. if ya using gnome . system --> administration --> networking

---

### Post by nianhbg on 2005-06-06
[QUOTE=dataw0lf]/etc/net/resources ??? Do you mean /etc/network/interfaces ?
Anyways, switch 'adress' to 'address' in your interfaces file.[/QUOTE]

Thanks for the answer it was a spelling error....  :smile:  It´s working now.

---

