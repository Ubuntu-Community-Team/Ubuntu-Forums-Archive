---
title: "Networkmanager"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by dmsn on 2007-02-17
Evening all.
I have a little problem with this networkmanager in Ubuntu Edgy.
Idon't see the AcessPoints in my network manager :(
How can i fix that?

Another thing i want that my laptop can connect automatic when im in school
or home, how can i conf that in /etc/networking/interfaces ?

Thanks for help

---

### Post by dbott67 on 2007-02-17
Can you post the output of the following commands:
```
cat /etc/network/interfaces
```
and
```
iwlist scanning
```

Thanks,
Dave

---

### Post by dmsn on 2007-02-17
**cat /etc/network/interfaces**

auto lo
iface lo inet loopack

# Home
auto eth1
iface eth1 inet dhcp
wireless-essid DMSN_AP

# Universty
auto eth1
iface eth1 inet dhcp
wireless-essid LUNI

---

### Post by dbott67 on 2007-02-17
What is the output of **iwlist scanning**?

-Dave

---

### Post by dmsn on 2007-02-17
Why you need a list with ~23 acess points ? :P
Please answer on my question better ;)
I can connect to it manually but i want auto connect if im in scool or home.

---

### Post by dbott67 on 2007-02-17
> **dmsn said:**
> Why you need a list with ~23 acess points ? :P
Please answer on my question better ;)
I can connect to it manually but i want auto connect if im in scool or home.

You were the one that posted:

[QUOTE=dmsn]I have a little problem with this networkmanager in Ubuntu Edgy.
[COLOR="Red"]I don't see the AcessPoints in my network manager[/COLOR]
How can i fix that?[/QUOTE]

I was making sure that iwlist scanning was able to "see" them.  If it doesn't return any results, you'll never be able to connect. ;)  

If you want to be able to connect to "preferred" networks whenever you get in range, try this:
```
sudo apt-get install network-manager-gnome
```

More info here:
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

---

