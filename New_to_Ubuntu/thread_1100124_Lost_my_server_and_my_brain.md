---
title: "Lost my server and my brain"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by tmbg002 on 2009-03-18
I have a back-up server at work that is just a computer with Ubuntu server 8.4 with a samba share and series of cronjobs that use rsync to copy data from our main server (running i think fedora 3) then the folder is shared with a bunch of windows computers with samba like I said. 

Everything was working fine, but the other day the share stopped showing up and the computer isn't showing up in the router table anymore either. 
I have looked at /etc/network/interfaces and it looks fine (it was using a static route and I switched it back and forth between static and dhcp and that didn't change anything) 

I have also looked at my samba share and it looks identical to another "server computer thing" that I setup that is still working.

I've restarted every computer twice, and have looked where I have had problems before and i'm coming up with blanks.

I am not sure where else I need to be looking or what information I need to tell you guys so I will leave it at that.\

Any advice would be very helpful.

---

### Post by amauk on 2009-03-18
Have you ruled out anything physical (damaged CAT cable, etc.)

---

### Post by tmbg002 on 2009-03-19
Thanks for the response, but I switched out the cable and switched between the network card in the PCI slot and the one on the Mobo. If I need to post any outputs or files I would be willing to, but I do not know where to even start anymore. If anyone could help it would make my month.

---

### Post by Calmor on 2009-03-19
On the backup server, do you have network connectivity?  i.e. - can you ping other computers on the network, what is the output of ifconfig, etc.

Can you ping the backup server from the main server by either the name or IP address?

Have any updates been performed recently on this machine or the router?  

How is it set up as static (router-determined or locally set in /etc/network/interfaces)?  I ask because my router is set up to assign a static IP based on a specific MAC address for my Mythbuntu server.

---

### Post by tmbg002 on 2009-03-19
> On the backup server, do you have network connectivity? i.e. - can you ping other computers on the network, ... Can you ping the backup server from the main server by either the name or IP address? 

I could not ping to or from the backup server.

> 
what is the output of ifconfig, etc.

ifconfig gives me

```
lo link encap: local loopback
   inet addr: 127.0.0.1 mask:255.0.0.0
   inet6 addr: ::1/128 scope hoste
   UP LOOP BACK RUNNING MTU:16436 metric:1
   Rx packets:252 errors:0 dropped:0 overruns:0 frame:0
   Tx Packets:252 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueueten:1000
   Rx bytes: 121921 (119.0 KB) Txbytes:121921 (119.0 KB)
```

> Have any updates been performed recently on this machine or the router?

The only thing I have done recently was edit the /var/named/chroot/var/named/mydomain.com.hosts file
in order to fix an issue with trying to get to a website named the same as our default name server, but I have switched it back to how it was and still have problems. 

> How is it set up as static (router-determined or locally set in /etc/network/interfaces)? I ask because my router is set up to assign a static IP based on a specific MAC address for my Mythbuntu server.

I have switched it back and forth between static and dhcp here is the non commented lines of my /etc/network/interfaces file

```
auto lo
iface lo inet loopback

iface eth0 inet static
     address 192.168.1.25
     netmask 255.255.255.0
     gateway 192.168.1.1
```


I have also tried

iface eth0 inet dhcp  (and commenting out the rest) 
I ahve also tried commenting out auto lo and iface lo inet loopback. 

Let me know what else I can provide you.

---

### Post by rhcm123 on 2009-03-19
according to ifconfig, you only have a loopback interface on your pc... this may have been caused by swithing out the network cards. Run this command to see the PCI network cards
```
lspci
```

---

### Post by tmbg002 on 2009-03-19
lspci gives me a bunch of things, but one of them is

00:12.0 Ethernet Controller:VIA technologies, INC. VT6102 [rhine-II] (rev74)

also
ifconfig -a

gave me a eth0 and eth1 but both had 0 Rx/Tx bytes and Packets

so I'm still in the dark.

---

### Post by rhcm123 on 2009-03-19
> **tmbg002 said:**
> lspci gives me a bunch of things, but one of them is

00:12.0 Ethernet Controller:VIA technologies, INC. VT6102 [rhine-II] (rev74)

also
ifconfig -a

gave me a eth0 and eth1 but both had 0 Rx/Tx bytes and Packets

so I'm still in the dark.

then try to bring the card up. I'll assume it's eth0.
```
sudo ifup eth0
```

---

### Post by tmbg002 on 2009-03-19
That worked! Wow.. thank you!!!

---

### Post by rhcm123 on 2009-03-19
> **tmbg002 said:**
> That worked! Wow.. thank you!!!

no problem
it should start automatically at boot time, post again if there is a problem.

---

