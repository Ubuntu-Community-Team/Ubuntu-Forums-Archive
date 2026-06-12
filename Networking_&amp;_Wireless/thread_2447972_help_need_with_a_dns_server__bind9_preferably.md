---
title: "help need with a dns server  bind9 preferably"
date: 2020-07-29
forum: Networking &amp; Wireless
---

### Post by villarroel on 2020-07-29
After several fails I am not even sure if a DNS server does what I used to believe that does.
I have an small network. One of the machines connected is a server (a desktop 20.04 ubuntu really). I have a private website running on that server. The problem is the users needs to enter the server ip at their browsers to see the website. I tried to install a DNS server called BIND9 on that server thinking to make things easy for visitors so they can enter a normal url instead of the server ip.
After several tries and fails doubts increased.
I follow the next tutorial in order to install BIND9

[https://www.linuxbabe.com/ubuntu/set-up-local-dns-resolver-ubuntu-20-04-bind9](https://www.linuxbabe.com/ubuntu/set-up-local-dns-resolver-ubuntu-20-04-bind9)

beside that did not work there is a section almost at the end 
[h=2]Setting Default DNS Resolver on Client Computers[/h]What ???? do I need to configure the client computers in order to make that works ??? I can not touch the visitors computers so if I need to do something like that I am sure that will not work.

Like I said I need to change an IP address for a name to access a website. That is all. Any help is welcomed and even if you know an easier software to do that I will take that.

thanks a lot in advance and any help is welcomed
Silvano Villarroel.

---

### Post by TheFu on 2020-07-30
Normally, for small networks, the DNS server IP is provided with the DHCP request for an IP, subnet, gateway.  Many home routers have a DNS capability built-in, so you may be able to just enable that, follow the router setup instructions for DNS of the LAN systems you want to use by name, and be happy.  The "server" must have a static IP for this to work. [https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

Of course, not all routers have this capability, so YMMV.  

**OR **

If your router doesn't support local DNS, then there are some other options:

Bind9 is an industrial solution for businesses.  There are other methods more suitable for home/small networks.  If you have a pi-hole setup, you can add a DNS server to that - you'll get ad-blocking for the entire subnet AND a lite-DNS.  You can run pi-hole in an LXD container.  Keeping "infrastructure" separate from desktops/servers is a best practice.  DNS is "infrastructure."  Actually, having multiple DNS servers on a LAN is a smart idea - running on different physical systems, of course.  After all, when DNS doesn't work, the entire internet seems down. Users don't like that.
[https://discourse.destinationlinux.network/t/pi-hole-in-canonical-lxd-container/1337](https://discourse.destinationlinux.network/t/pi-hole-in-canonical-lxd-container/1337)
[https://github.com/pi-hole/pi-hole/#one-step-automated-install](https://github.com/pi-hole/pi-hole/#one-step-automated-install)
[https://discourse.pi-hole.net/t/howto-using-pi-hole-as-lan-dns-server/533](https://discourse.pi-hole.net/t/howto-using-pi-hole-as-lan-dns-server/533)

I have a pi-hole + LAN DNS running in an LXD container here. I followed those instructions.
```
$ lxc list
+--------+---------+---------------------+------+------------+-----------+
|  NAME  |  STATE  |        IPV4         | IPV6 |    TYPE    | SNAPSHOTS |
+--------+---------+---------------------+------+------------+-----------+
| pihole | RUNNING | 172.22.22.80 (eth0) |      | PERSISTENT | 0         |
+--------+---------+---------------------+------+------------+-----------+
```
For guest machines to use it, I just had to modify the DHCP settings in the router (my DHCP server) to provide the pihole IP (172.22.22.80) as the primary DNS server to all DHCP clients. Works great, but of course, the machine running that LXD container has to be on all the time.  
I made my pihole storage much too large.
```
$ dft
Filesystem            Type  Size  Used Avail Use% Mounted on
lxd/containers/pihole zfs    13G  **607M**   12G   5% /
```
800MB would have been fine.

---

### Post by Doug S on 2020-07-30
I run bind9 on my LAN. I also run a dhcp server on the same computer. Visiting computers acquire a dynamic IP address, which includes which DNS to use. Then they can access my web site by name. If those same computers are connected somewhere outside my LAN, they use whatever DNS and still access the same web site, but via it's external IP address. The typical user doesn't have to think about it at all. so, I think that all you are missing is the default DNS assignment for computer on your LAN, which you should be able to do via whatever DHCP server you are using.

---

### Post by SeijiSensei on 2020-07-30
How small is "small?" If you're talking just a few clients, it's probably easier to modify the /etc/hosts file to associate a name with the IP. You'll need to edit it as root with sudo, e.g., "sudo nano /etc/hosts".

```

10.10.10.10     ourwebserver [alias1 alias2 ...]

```

The aliases are optional and probably unnecessary in your case.

You can take the same route on Windows clients.  The relevant file is C:\Windows\System32\Drivers\etc\hosts. It has the same syntax as the one on Linux.

---

### Post by Skaperen on 2020-07-30
how do the client machines get their IP address?  is DHCP running?  if the clients have their IP address permanently configured then they almost certainly need to have their /etc/resolv file permanently configured.  that file tells the system what IP addresses (up to 3) to sens DNS queries to.  gotta start lookups somewhere.

---

### Post by TheFu on 2020-07-30
I love /etc/hosts ( [https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279](https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279) ) to block ads and configure LAN devices, but for non-computer clients (phones/tablets) on the network, that often isn't possible.  Still, a good post for later lurkers.

Modifying /etc/hosts on Windows takes a little effort, since they don't have sudoedit. Some parts of MS-Windows don't pay any attention to the /etc/hosts file.  The same existed on Android for a few releases. The only way to get Android to pay attention to LAN lookups was to run a DNS on the LAN. My Android is long rooted and long swapped out for non-google releases, so I don't know what any recent Google versions do.

Some OSX users reported problems, which made little sense to me, but that crowd was less technical so I suspect they deleted the localhost addresses when they merged the the files together.

---

### Post by villarroel on 2020-07-30
Thanks for all your answers 

it is made for a class room. So the guesses get in to the room. They will get a dynamic ip address from the router so I believe there is a DHCP running on the router.
We usually have between 30 to 40 connections. Rarely more than 40.
Guesses get connected with whatever they bring to the training. That means from laptops to smartphones and I can not touch their stuff. That is their personal stuff. 

I will keep trying with the bind9 server but if that exceeds my skills (I am programmer and I have never done this before) I will explore the pi hole  option.

Anyone knows a better tutorial to configure bind9 ??

Once again thanks to all of you guys for your help

---

### Post by villarroel on 2020-07-30
do you know a better tutorial to configure bind9 ???

---

### Post by villarroel on 2020-07-30
can you point me out a better tutorial to configure bind9 ??

---

### Post by Doug S on 2020-07-30
> **villarroel said:**
> can you point me out a better tutorial to configure bind9 ??[The ubuntu serverguide]("https://ubuntu.com/server/docs/service-domain-name-service-dns")

---

### Post by TheFu on 2020-07-30
> **villarroel said:**
> can you point me out a better tutorial to configure bind9 ??

BIND is kinda ugly. 

For just a few systems, there are smaller, easier to configure, solutions.  dnsmasq is one. That's what the pihole uses. Just to be clear, pihole is just the project name. It can run on any Linux system that has 1 network interface - not just raspberry pi computers.  dnsmasq will use a file very much like the /etc/hosts file to perform DNS lookups for the LAN. The only mandate that I've noticed is that the short hostname must come first and the FQDN must be 2nd. One record would be:
```
172.22.22.23 hdhr4 hdhr4.thefu.lan
```

As stated above, to have all the DHCP clients get the settings automatically, you'll need to modify the DHCP server settings.  Then all DHCP clients will point to your DNS server.  Then those clients will get the DNS server you want just like they get the IP, subnet, default gateway ... 

I've run BIND for a few years. If you need full DNS forward and reverse lookups, then you want BIND. If you just need forward lookups, like a webserver/webapp needs, then dnsmasq is much easier and less risk from a security standpoint.

IMHO.

---

