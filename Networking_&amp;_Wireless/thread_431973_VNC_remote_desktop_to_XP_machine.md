---
title: "VNC remote desktop to XP machine??"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by rubrboots on 2007-05-03
I am trying to connect to an xp machine that has tightVNC server running on it. I have been connecting to it remotely from other windows machines for some time. I can also connect to the ubuntu machine from windows machine but not vice versa. Does anyone know how this can be done with VNC. I dont want to change programs if I dont have to, since I have tightVNC installed on all my other networked computers and it works great.

---

### Post by rubrboots on 2007-05-03
to answer my own question, 

Use terminal Server client (installed by default), it will fail if you use the "network name" of the computer, so use the actual ip address.

---

### Post by dbott67 on 2007-05-03
> **rubrboots said:**
> ...it will fail if you use the "network name" of the computer, so use the actual ip address.

If you want to resolve by hostname you need to install winbind (and possibly the samba packages samba, smbfs & smbclient):
```
sudo apt-get install winbind samba smbfs smbclient
```And then edit your /etc/nsswitch.conf file:
```
sudo gedit /etc/nsswitch.conf
```find this line (it may not be exactly that)

```
hosts:          files dns mdns
```and add wins, so now it looks like

```
hosts:          files dns mdns wins
```Read through this [thread]("http://ubuntuforums.org/showthread.php?p=2438836#post2438836") (post #2) and this [one]("http://ubuntuforums.org/showthread.php?p=2539757#post2539757") for further explanations & details.  The basic problem is 'name resolution', which is cured by installing winbind.

-Dave

---

