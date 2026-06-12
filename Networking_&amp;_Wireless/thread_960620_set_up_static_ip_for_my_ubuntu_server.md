---
title: "set up static ip for my ubuntu server"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by porteclefs on 2008-10-27
Hi,

I'm not really sure what I need to do in order to set up a static IP for my Ubuntu server. I have the latest version of Ubuntu server edition with LAMP. Nothing else really going on with it at the moment.

Thanks

---

### Post by cariboo on 2008-10-27
This is not specific to Ubuntu it works with any Linux distribution. I assume that because you are running the server version that you aren't running a gui, so all the instructions are done in a console:

You need to edit /etc/network/interfacces:

```
sudo nano /etc/network/interfaces
```

This will open the file for editing. It should look something like this:

```
auto lo
iface lo inet loopback
```

Add the following lines:

```
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

Press Ctrl-o to save and Ctrl-x to exit.

The above addresses are for my own server, I am accessing the internet through a Linksys WRT54GS.

You should change the addresses to reflect your own network. If you are behind a router I suggest using an ip address outside the range that dhcp serves.

Once you have finished editing the file you need to restart networking:

```
sudo /etc/init.d/networking restart
```

If you are connected remotely using restart will not disconnect you.

Jim

---

### Post by porteclefs on 2008-10-27
thanks

---

