---
title: "Connecting windows 10 computer to Ubuntu 18.04.2 LTS"
date: 2019-07-20
forum: Networking &amp; Wireless
---

### Post by an-ordered-hole on 2019-07-20
I have a windows device that I want to connect to a Ubuntu 18.04.2 LTS desktop using ssh. I cannot ping the ubuntu computer from the windows device and cannot access the ssh. I have limited knowledge networking with linux and do not know how to troubleshoot this.

I tried reading a few posts about ssh problems and I am completely lost and need help. 

ubuntu running: openssh-server
windows running: PuTTY for ssh; pinging with cmd prompt

---

### Post by SeijiSensei on 2019-07-20
Are both machines connected to the same router?  If so, I would try using the Ubuntu machine's IP address. If you don't know its address, you can find it with the command:
```
ip addr | grep 'inet '
```
You'll probably get back multiple entries. The one ending in enoX or wloX is the one you want. The first would be the result if you're using an Ethernet cable; the second would apply if you're using wifi.

---

### Post by an-ordered-hole on 2019-07-20
The computers are wirelessly connect to the same router. 

I already obtained the IP address of the Ubuntu machine and that is what I tried to ping from window's cmd prompt. This is the output from the process.
[I]
Packets: Sent = 4, Received = 0, Lost = 4 (100% loss)
[/I]
From my understanding, I must be able to ping before I can attempt the ssh. There is something interfering with the two computers communicating but I have no clue where the interference is coming from.

---

### Post by SeijiSensei on 2019-07-20
Is either machine running a firewall, in particular the Ubuntu host? If so, turn it off.

Are there other devices on your network (smartphones, printers, etc.) connected to the same router? Can you ping them from Windows?

Can you ping other hosts like 8.8.8.8?

---

### Post by an-ordered-hole on 2019-07-20
I tried pinging 8.8.8.8 and was successful:

[I]Ping statistics for 8.8.8.8:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 21ms, Maximum = 22ms, Average = 21ms[/I]

I will look for a firewall on the ubuntu machine but I have not installed one myself so it must be something that comes with the install. 

Do you think the router itself is causing a problem?

---

### Post by SeijiSensei on 2019-07-20
Usually there is no firewall set up by default.

Can you ping the router's address from the Ubuntu machine?

---

### Post by an-ordered-hole on 2019-07-20
1. It is possible to ping 8.8.8.8 in the  ubuntu terminal. 

2. Also I found windows 10 has a 'Windows Defender' firewall. I am not familiar with it's setting or how to change them if they need adjusting.

*edit*

3. I have tried pinging the router from both machines and was unsuccessful. It's possible I am not using the correct IP#. I found it using a website and using what it called the 'Router's Public IP'.

---

### Post by The Cog on 2019-07-20
If you are both on the same wireless network then the route's public IP is the wrong one to use. You can find Ubuntu's IP with the command ```
hostname -I
```, and with windows, probably with **ifconfig**.

---

### Post by TheFu on 2019-07-20
If you run 
**route -n**
on the linux machine, the router internal IP will come back as the gateway.

It is possible for some routers to be configured to prevent devices on the same internal LAN not to allow access to each other.  This is commonly configured at cafes and small businesses so customers don't hack each other.

The route command above will show if that is configured too.  I think Windows supports the same route command.

---

### Post by an-ordered-hole on 2019-07-20
> **The Cog said:**
> If you are both on the same wireless network  then the route's public IP is the wrong one to use. You can find  Ubuntu's IP with the command ```
hostname -I
```, and with windows,  probably with **ifconfig**.


I'm am not connecting the computers with the router IP. I believe that was just to verify if the computers can communicate with the router?

I tried pinging the IP you get from your command on my windows machine before and was unsuccessful.

---

### Post by SeijiSensei on 2019-07-20
On Windows the command is "ipconfig".

If the computers have addresses like 192.168.1.27, the router address is likely 192.168.1.1.  

As TheFu says, if you use the command "route -n" on Ubuntu, the top line, the one that begins 0.0.0.0, will have a "gateway" address assigned as well. That's the internal address of the router.

---

### Post by an-ordered-hole on 2019-07-20
> **TheFu said:**
> If you run 
**route -n**
on the linux machine, the router internal IP will come back as the gateway.

It is possible for some routers to be configured to prevent devices on the same internal LAN not to allow access to each other.  This is commonly configured at cafes and small businesses so customers don't hack each other.

The route command above will show if that is configured too.  I think Windows supports the same route command.

1. I can ping the gateway IP from the ubuntu terminal but cannot ping that IP(the one derived on the ubuntu machine) on my windows machine. 

2. I can ping the default gateway IP from the ipconfig command in windows. The default gateway is different from the ubuntu gateway and I am not sure if that is expected.

3. I cannot tell by the output if internal LAN access is restricted.

---

### Post by TheFu on 2019-07-20
At some point, you will want the "server" to have a static LAN IP.  Otherwise, it can change and any stuff you've hooked up or scripted to use the DHCP IP address will all break.  On my LAN, every device that isn't portable, like a laptop or tablet, gets a static IP and the devices that are portable get DHCP reserved IPs, so they are effectively static at  home, but when connected to other networks, they get whatever IP is provided.

The router is probably the DHCP server for the home network and it has a range of IPs that it gives out.  Static IPs **must not** be inside that range.  .100-.254 is a common range for DHCP addresses, but every router is configured differently.
How to setup _DHCP Reservations_ is also configured differently inside every router, so you'd need to look up that for your exact vendor and model and installed router software.  Reservations use the MAC for each network device, so you'll need to find those on your systems, if you choose to go that way for force static IPs.

If you don't understand basic IPv4 networking, the chance of making a mistake is high.  It isn't hard at all, but you do need to understand the basics.

---

### Post by an-ordered-hole on 2019-07-20
I do not understand the the connection between DHCP Reservations and what I was doing before re: pingning IP addresses. It's too big of a logical leap for my networking skills. 

Are you sure the problem is because of DHCP Reservations? What is the reason for this assumption?

---

### Post by SeijiSensei on 2019-07-20
If you can ping the router from Ubuntu, and also ping the router from Windows, but you cannot ping across the router, then the router is somehow blocking the connection.  Have you tried resetting the router?

---

### Post by TheFu on 2019-07-20
> **an-ordered-hole said:**
> I do not understand the the connection between DHCP Reservations and what I was doing before re: pingning IP addresses. It's too big of a logical leap for my networking skills. 

Are you sure the problem is because of DHCP Reservations? What is the reason for this assumption?

If you want to use ssh or any client/server connection between these systems, then the "server" will really need to be setup with a static IP.  If you don't handle that now, you'll have to handle it later.  ssh can be really picky if IP addresses change. It could decide that someone is trying to hack it and block the connection if the IP changes.

Basically, I'm trying to head off all sorts of issues that WILL happen later, today.

But .... you do you.

---

### Post by an-ordered-hole on 2019-07-20
I resolved the problem for now. It was the router. I chose another router and it worked first try.

---

