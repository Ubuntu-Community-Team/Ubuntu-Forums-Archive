---
title: "How do I Manually Open Ports on Ubuntu?"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by Penguin Guy on 2009-04-02
> All ports are closed by default.
> If an application has to use a port, it will open it itself.

So I have a Mozilla Thunderbird addon that requires certain ports to be open; how do I manually open them myself?
[http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html](http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html)

---

### Post by JohnLM_the_Ghost on 2009-04-02
> **Penguin Guy said:**
> So I have a Mozilla Thunderbird addon that requires certain ports to be open; how do I manually open them myself?

Most direct interface is **iptables**, however it is very user-unfriendly.
For GUI I'd recommend **firestarter**. You will just have to make a rule to allow traffic on certain incoming port.

btw Does that addon really need that port open? It is not really usual practice to have a open listening port, for non-server (or no service serving) software. And outgoing ports are not blocked by default.
Client initiated passive connection is usual for these...

---

### Post by Penguin Guy on 2009-04-02
It is an addon that downloads hotmail email, it says there is errors with ports 25 and 110. So I assume that yes - it does require them. Also I'd be more than happy if there was a terminal command to open/close ports.

---

### Post by Vadi on 2009-04-02
Try [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html) too. It's better maintained than Firestarter.

---

### Post by superprash2003 on 2009-04-02
[http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html](http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html)

---

### Post by jigsaws on 2009-04-02
Are you sure the probles is with YOUR ports. 110 and 25 are standard mailserver ports.

You can by default open connection to any port on any server. There is not such thing as manual open port - aplication opens ports. But it can be blocked by firewall.

You can check if you have any firewal rules by "iptables -L".

---

### Post by bodhi.zazen on 2009-04-02
By default, iptables is permissive, so unless you have configured your firewall (with iptables, ufw, gufw, firestarter, etc) the problem is not with your box.

Do you have a router ? If so you will need to forward the ports from your router to your box. Be aware this is a possible security risk as you are now running a server.

It would also help if you told us what extension you are running so we can look at it.

If you did configure your firewall, what tool did you use ?

---

### Post by Penguin Guy on 2009-04-02
No, I'm not sure who's ports I am talking about. 
Thanks for the link ([http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html](http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html)).
I would rather not mess with ports and creating servers or anything, so if there is no easy solution I will just forget about it and use the hotmail website.

---

### Post by HermanAB on 2009-04-02
The whole 'opening ports' thing is a Windowsism, since Windows (any version) runs oodles of documented and undocumented services by default.  Therefore, to secure a Windows machine, you have to install a third party firewall to try and close the barn door.

The default Ubuntu install has NO servers running, therefore it doesn't listen on any port.

Thunderbird is a client program.  It doesn't provide any services, therefore with Thunderbird installed you still won't have any open ports to worry about.

When you install a file or mail server, it will activate and open the ports it needs by itself and then you still don't have to worry about it.

---

