---
title: "connection to network after install"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by Mia_tech on 2006-11-12
hello guys
just finish installing ubuntu and after configuring the 
/etc/network/interfaces file, still got no connection to network
ie: can't ping gateway (router) or any other computer for that matter
this is what my file looks like
******************************************************************
auto lo
iface lo inet lookback

auto eth0
iface eth0 inet static
address 10.200.50.5
netmask 255.255.255.0
gateway 10.200.50.1

****************************************************************
here is my /etc/hosts file
****************************************************************
127.0.0.1 localhost ubuntu-box
10.200.50.5 ubuntu-box

any help will be appreciated

---

### Post by Mia_tech on 2006-11-12
oh by the way I added 
network 10.200.50.0
broadcast 10.200.50.255

to the /etc/network/interfaces file

---

### Post by MrFSL on 2006-11-12
Ater you wrote you config files did you reset networking so everything would take effect?

For instance:
```
sudo /etc/init.d/networking stop
sudo /etc/init.d.networking start
```

If there is a problem you should at least get some output from these two commands.

---

### Post by Mia_tech on 2006-11-12
> **MrFSL said:**
> Ater you wrote you config files did you reset networking so everything would take effect?

For instance:
```
sudo /etc/init.d/networking stop
sudo /etc/init.d.networking start
```

If there is a problem you should at least get some output from these two commands.

when I do a [ sudo /etc/init.d/networking start ] it gives me the following
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received
No working leases in persisten database - sleeping

and it goes on and on trying to get DHCP address or at least contacting the DHCP server which I know is working have a windows xp box and another ubuntu box on same network and Im able to do /etc/init.d/networking stop and start and I get ip address with no problem.
oh they are all dynamic ips
Im starting to suspect nic driver corrupted or not working properly
anybody knows how to check for correct nic driver installation and function
ifconfig eth0 shows all detail of what appears to be a good nic card
I know the nic card is good because when I boot from live cd it works

---

### Post by stream303 on 2006-11-13
Ah, your router is set up for DHCP, but you want to run a static address?  It can be done, but I wonder if you'd have better luck getting off the ground by using DHCP in your Ubuntu Networking settings...

The line from your interfaces file kind of gave it away

iface eth0 inet static

Maybe try System > Administration > Networking > Properties for your card and see if dhcp is checked.

Apologies if you are really wanting to run static...

---

### Post by Iowan on 2006-11-13
> **stream303 said:**
> Maybe try System > Administration > Networking > Properties for your card and see if dhcp is checked.

If DHCP IS checked, that may explain why **dhclient** is trying to run. You might UNCHECK it to see if your static settings take effect (after network restart).

---

### Post by Mia_tech on 2006-11-14
> **Iowan said:**
> If DHCP IS checked, that may explain why **dhclient** is trying to run. You might UNCHECK it to see if your static settings take effect (after network restart).

no guys...the idea was to have a static ip yes with DHCP on router.....
I made sure when I modify the interface file to chage everthing to static even in the network GUI.....didn't work....as an alternative for troubleshooting I switch back everthing to dynamic that's why u see the box trying to contact the DHCP....but then again didn't get a connection
but the strange things is when I boot up the same computer with ubuntu live cd it works well........uhhh, go figure....I was thinking to completly trun off DHCP on router and see what happens...right now I'm working off an ubuntu laptop with HD install...dynamic ip...I have switched to static and work, back to dynamic and works too....lol
thanks for everthing guys

---

