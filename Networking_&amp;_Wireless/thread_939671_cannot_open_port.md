---
title: "cannot open port"
date: 2008-10-06
forum: Networking &amp; Wireless
---

### Post by liskiewicz on 2008-10-06
This is my first post, so hello everyone :).

I was trying to open the ports for Torrent under Ubuntu (it works under winXP so it's not a problem of my network). In trnsmission client am still getting info that the port is closed, while test avaliable on [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) says that this port is "stealth". 

I have looked through similar posts, and installed firestarter to open all ports for both Torrent, and a Mule. My system is new, and no firewall was run yet.

What could be the reason of that?

---

### Post by kevdog on 2008-10-06
Did you clear the iptables?

sudo iptables -X
sudo iptables -F

That should flush the iptables that firestarter setup.  To verify:
sudo iptables -L

---

### Post by liskiewicz on 2008-10-06
Thank You for reply. I have tried with that. Then after writing "sudo iptables -L" I've got something like that:

```
Chain INPUT (policy DROP)
target     prot opt source               destination

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy DROP)
target     prot opt source               destination
```

Port was still closed (according to transmission Bittorrent and website check)
Then I wrote "sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT". And "sudo iptables -L" resulted in:

```
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:6881

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy DROP)
target     prot opt source               destination

```

And the port was still closed...

---

### Post by kevdog on 2008-10-06
If you look at your default policies -- they are all DROP.

Here is what I would do --  type it out by hand and tell me what iptables -L shows:


sudo iptables -F
sudo iptables -F -t nat
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT

---

### Post by liskiewicz on 2008-10-06
That is the ouput:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

But all ports are still recognized as closed. And again even after adding the rule to open some port: "sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT" -L displays this rule, but program still recognizes that port as closed. I have no idea what's going on... ](*,)

---

### Post by liskiewicz on 2008-10-08
I am still trying to figure out what is blocking my ports. Does anybody have any idea? As I said I am new with Ubuntu, and it is probably something easy...

---

### Post by cariboo on 2008-10-08
How are you connecting to the internet? Is it through a router? If so you have to port forward from your computer to your router.  Windows uses Upnp through the router so there isn't much need to open a specific port. Linux doesn't use Upnp because of security issues so port forwarding is a must. There are a lot of different routers out there and they are all different, consult the documentation that came with your router to set up port forwarding.

Jim

---

### Post by liskiewicz on 2008-10-09
I am connecting through USB modem (webstar atlanta DPC2100) which has Ethernet port as well (which I am using at the moment). Modem is connected to local cable TV. Do I need port forwarding for that? I have installed Guidedog which is GUI for port forwarding, but I don't know how to fing proper IP, and portnumbers to specify the rule.
I've looked trough the manual and there is no single word about port forwarding. However I was not installing any drivers for that. I've just connected the modem and it worked.
Another thing is that I could browse the web through that connection, but when I do port check for port 80 it shows that the port is closed (any port I have checked was closed). How could it work then?

---

