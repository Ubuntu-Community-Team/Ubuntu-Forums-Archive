---
title: "configuring network interfaces"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2009-04-20
Hi

my computer keeps getting hung up on "configuring network interfaces"

i cannot edit
> 
/etc/dhcp3/dhclient.conf

to shorten the time out

as it says permission denied even though I'm in as root

---

### Post by ptn107 on 2009-04-20
```
sudo chmod 644 /etc/dhcp3/dhclient.conf
sudo gedit /etc/dhcp3/dhclient.conf
```

?

---

### Post by halitech on 2009-04-20
you don't need to edit the permissions on the file, just use sudo to edit it

```
sudo nano /etc/dhcp3/dhclient.conf
```
or
```
gksu mousepad /etc/dhcp3/dhclient.conf
```

---

