---
title: "so how do i set the alternate dns server?"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by I WILL DO IT on 2009-12-15
so how do i set the alternate dns server?
and preferred dns server?

---

### Post by doas777 on 2009-12-15
in network manager, just add a comma delimited list, starting with the primary.
same with resolv.conf. should work in the order declared.

---

### Post by I WILL DO IT on 2009-12-15
am lost can you show me a picture or something?

---

### Post by doas777 on 2009-12-15
(note: the bolding just shows action items. not yelling)
ok, **Right click on the network-manager icon on your panel **(usually on the top right panel, near your clock), and **select "Edit Connections"**. 

now, **select the interface you are trying to configure**. for wired it usually starts with "Auto EthX" where X is an integer, and for wireless, it is usually "wlanX"
with your interface selected, **click Edit**.

**go to the tab that says "IP V4 Settings"**
**add your server IP addresses to the box labelled "DNS servers"**, in this format ```
<primary DNS server IP>, <secondary DNS server  IP>
```then reboot.

---

### Post by jamieleshaw on 2009-12-15
Or you can do it through the gui please refer to [http://jamieleshaw.files.wordpress.com/2009/11/dns_network_configuration.png?w=262](http://jamieleshaw.files.wordpress.com/2009/11/dns_network_configuration.png?w=262)
that picture

---

### Post by Iowan on 2009-12-15
In case the method prescribed by **doas777** doesn't work, I remember a thread from awhile back that suggested the list needed to have spaces around the comma:```
<primary DNS server IP> , <secondary DNS server  IP>
```

---

### Post by wojox on 2009-12-15
Here:

[IMG]http://ubuntuforums.org/picture.php?albumid=1546&pictureid=5345[/IMG]

---

### Post by wojox on 2009-12-15
See below.

---

### Post by sandyd on 2009-12-15
can also be done in /etc/dhcp3/dhclient.conf

---

### Post by wojox on 2009-12-15
> **carlee said:**
> can also be done in /etc/dhcp3/dhclient.conf

Thanks carlee that's what I meant.

```
gksudo gedit /etc/dhcp3/dhclient.conf
```

Add

```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```

To the bottom of the script

---

### Post by sandyd on 2009-12-15
p.s. you have to restart.
and run this first before starting the instructions above (as a safety measure)
```

sudo cp /etc/resolv.conf /etc/resolv.conf.auto

```

---

### Post by doas777 on 2009-12-15
> **Iowan said:**
> In case the method prescribed by **doas777** doesn't work, I remember a thread from awhile back that suggested the list needed to have spaces around the comma:```
<primary DNS server IP> , <secondary DNS server  IP>
```
good point. thanks for catching that.

---

### Post by Akuma_s on 2010-01-29
This also works when behind a router?

Thanks anyway for the info... ;)

---

