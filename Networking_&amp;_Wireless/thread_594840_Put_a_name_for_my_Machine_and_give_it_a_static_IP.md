---
title: "Put a name for my Machine and give it a static IP"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by Peter Alien on 2007-10-28
Where in Ubuntu 7.10 can i put the name of my PC or Server Machine?

And where can i configure a static IP in it?
Is there an application where i can do it, like Network Manager for example, or do i have to edit some files in Ubuntu?


Many thanks.

---

### Post by Peter Alien on 2007-10-29
Anybody ?  :)

---

### Post by wolfsta on 2007-10-29
Hey Peter

If you want to configure a static IP for the machine your on.. go ahead and edit the following file

/etc/network/interfaces

youll need to have a section similar to this

> auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168,1.1

also in /etc/resolv.conf add your dns nameservers that you wish to use be it your router or isp dns servers

> nameserver 192.168.1.1
nameserver 123.8.13.1

Cheers :)

---

### Post by Peter Alien on 2007-10-30
many thanks... :)

just tell me one thing more, in wich section of ubuntu can i put a name for my machine, like "Home PC"?

---

### Post by kevdog on 2007-10-30
I believe that is in the smb.conf file.

---

### Post by wolfsta on 2007-10-31
/etc/smb.conf is only for when your browse to your computer from a windows box.

If you want to change the actual hostname of the computer then

'hostname newhostname' will change it temporarily

for permanent change.. edit /etc/hostname and put the new name in then run 'sudo /etc/init.d/hostname.sh start' to make the change without rebooting

---

### Post by breezyfox on 2007-10-31
> **Peter Alien said:**
> many thanks... :)

just tell me one thing more, in wich section of ubuntu can i put a name for my machine, like "Home PC"?

Hi you can do this way
  1. edit  /etc/hostname
 sudo gedit /etc/hostname

2. edit /etc/hosts

sudo gedit /etc/hosts

3. go to system > administration > network

click on host tab , you will find the name for your localhost.

try first two first.

hope this helps

bz

---

