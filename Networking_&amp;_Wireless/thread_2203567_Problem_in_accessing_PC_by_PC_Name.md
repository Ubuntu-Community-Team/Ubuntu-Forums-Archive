---
title: "Problem in accessing PC by PC Name"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by chirag4 on 2014-02-04
Hi,

I am new to Ubuntu.

I have a LAN setup of 4 PC.

Out of 4 PC 3 are Windows PC and 1 is Ubuntu 12.04 PC.

I installed samba server to access files on LAN.

I want to access LAN PC by PC Name.

I can access LAN PC by IP Address but I can not Access it with PC Name.

Help is needed.

Thanks.

---

### Post by theDaveTheRave on 2014-02-04
For transforming IP address to a computer name you need to have the names saved in a file.

On you ubuntu this is the /etc/hosts file.

I'm not sure if samba can be set up to present a host name lookup to other pcs on the network.

Otherwise you will need to set up a name server on one of your pcs (I guess the ubuntu 12.04 one).

check out the docs on the debian site[domain-name-servers]("http://debian-handbook.info/browse/wheezy/sect.domain-name-servers.html")

---

### Post by chirag4 on 2014-02-04
If i add computer name to /etc/hosts file it works fine for me.

But it is not feasible to add every pc name and ip to /etc/hosts file.

Is there any other way that automatically detect computer name and its ip address ???

---

### Post by Morbius1 on 2014-02-04
Edit /etc/samba/smb.conf as root and add the following line under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```
Then restart samba in this order:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```

When you restart the samba daemons the network goes into a hissy fit - it's a Microsoft thing - so wait a few minutes before you can see if this change works for you.

Of course this all depends on all your machines being in the same subnet - all connected to the same router - since samba can't browse by name otherwise.

---

### Post by chirag4 on 2014-02-04
Hi Morbis,

I did same you told me but it does not work. :( :(

---

### Post by Morbius1 on 2014-02-04
There's only a few things that can prevent "bcast" from doing it's thing:

[1] Every one is not in the same subnet.
[2] Firewall is in the way - disable them all and try again.
[3] host name is too long - they have to be 15 characters or less in length.
[4] Samba services ( smbd and nmbd ) are not running.

---

### Post by chirag4 on 2014-02-04
How can i check that all pc are in the same subnet or not?

---

### Post by Morbius1 on 2014-02-04
Here's a way to check for items [1] and [2]:

Install nmap:
```
sudo apt-get install nmap
```
Run the following command to list all the machines by ip address on your subnet:
```
sudo nmap -sP -oG- 192.168.0.100/24
```
[COLOR=#0000cd]* Change 192.168.0.100 to the ip address of the machine you are running.*[/COLOR]

Then chose one of them ( 192.168.0.105 in this example ) and run this command to see what ports are open:
```
sudo nmap -sS -sU -T4 192.168.0.105
```

---

