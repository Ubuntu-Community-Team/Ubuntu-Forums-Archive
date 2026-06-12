---
title: "Network topology advice"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by GeertC on 2007-04-23
Hi,

I would like to give the Ubuntu server a go to act as a Home File Server/Web Server/Print Server and I would appreciate some advice on which network topology to go for;

My current setup is:
[ATTACH]30592[/ATTACH]

I was thinking of using an old PC I have with 2 network cards to do something like this:
[ATTACH]30593[/ATTACH]

But I guess an other option might be this:
[ATTACH]30594[/ATTACH]

I would like to use the Ubuntu server as a headless (no screen) server hidden away somewhere in the wardrobe or something.

What would be the best setup and is there a tutorial or guide I can follow to get the network settings right. I am ok with setting the router but I have never installed a server.

---

### Post by dbott67 on 2007-04-23
I would choose option 3 (server on same subnet as laptops & printer; using the linksys AP as the router/gateway/nat device).

Just give the server a static IP on the same subnet as your laptops.

If you post the internal IP scheme you're presently using (192.168.0.xxx), plus the IP address of each device, I can give you specific steps:

192.168.0.1 - Linksys WRT54 Router
192.168.0.2 - Ubuntu server (static IP)
192.168.0.10 - print server (static IP)
192.168.0.100 - Laptop - Ubuntu1 (DHCP)
192.168.0.101 - Laptop - Ubuntu2 (DHCP)
192.168.0.102 - Laptop - Mac (DHCP)

-Dave

---

### Post by SishGupta on 2007-04-23
Yeah definitely do it like you have your 3rd picture set up. I don't even know why you would do the 2nd picture. Quite an odd setup. Having the server come after the router means that it will be protected by the router.

This is the way most home networks are set up.

Like the first replier from St. Catherines said, give the printer and box static ips. 
I give all my machines static ips but at a minimum give all servers a static ip.
Setting up the extra machine shouldn't be much different than setting up the laptops, except setting the static ip which should be an option on the router interface. Select the MAC addy for the server and then set the ip to something like 192.168.0.x (where x can be a number of your choice from 2-254 assuming your routers ip is (192.168.0.1). Also if you want the server to be accessible from the internet you will have to open ports to the servers static ip.

Also, If you can't directly network your printer (like I can not), just connect it to the server and use cups to handle network printing.

---

### Post by GeertC on 2007-04-23
Thanks. How would I open the port to the Ubuntu server's static ip?

---

### Post by dbott67 on 2007-04-23
Assuming that your subnet is 192.168.0.xxx, you would need to edit your interfaces file.  It probably looks similar to this:
```
dbott@feisty:~$ cat /etc/network/interfaces 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet [COLOR=Blue]dhcp[/COLOR]

```

Open a terminal and type:
```
sudo gedit /etc/network/interfaces
```

Change the dhcp to static, and then add the lines in red:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet [COLOR=Blue]static[/COLOR]
[COLOR=Red]address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1[/COLOR]
```

-Dave

---

