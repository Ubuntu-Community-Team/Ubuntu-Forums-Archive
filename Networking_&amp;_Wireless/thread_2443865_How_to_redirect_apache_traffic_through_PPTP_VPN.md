---
title: "How to redirect apache traffic through PPTP VPN"
date: 2020-05-21
forum: Networking &amp; Wireless
---

### Post by bax001 on 2020-05-21
Hello everyone,
I am new here, so please forgive me if I am doing something wrong.

I have a free Amazon EC2 server with Ubuntu 19. I would like to redirect only traffic from and to Apache through my home VPN (PPTP). Can you give me please a atep by step solution or links how to it?

Many thanks

Bart

---

### Post by slickymaster on 2020-05-21
Thread moved to **Networking & Wireless** for a better fit

---

### Post by SeijiSensei on 2020-05-21
No one should be using PPTP these days. It has well-known security issues.

I suggest installing OpenVPN on both ends of your connection.  If you use a [static connection]("https://openvpn.net/community-resources/static-key-mini-howto/"), it's pretty easy to configure.

---

### Post by bax001 on 2020-05-22
Thanks for your answer, but I know it is not very safe, but I don't use it public and it is much easier for me to just type login and password without certificates. I use it only from time to time to get an access to one of my computers over the internet. Server is not really public, because there is only a script in PHP to scrap information from one website and I need a VPN connection only for that (rest of the traffic should go without a VPN)

---

### Post by SeijiSensei on 2020-05-23
We need more details. How is this PPTP connection set up? 

If you always connect from home, and your home connection has a reliably stable IP address, I'd use firewalling on the EC2 instance to accomplish what you want.
```

sudo /sbin/iptables -A INPUT -p tcp --dport 80  -s your.home.ip.addr -j ACCEPT
sudo /sbin/iptables -A INPUT -p tcp --dport 443 -s your.home.ip.addr -j ACCEPT
sudo /sbin/iptables -A INPUT -p tcp --dport 80  -j REJECT
sudo /sbin/iptables -A INPUT -p tcp --dport 443 -j REJECT

```
The last two lines block any other connections to HTTP and HTTPS.  However, if your server is out in the wild, you should consider blocking all incoming traffic other than what you specifically permit like this:
```

sudo /sbin/iptables -P INPUT -j DROP
sudo /sbin/iptables -A INPUT -p tcp --dport 80  -s your.home.ip.addr -j ACCEPT
sudo /sbin/iptables -A INPUT -p tcp --dport 443 -s your.home.ip.addr -j ACCEPT

```
The first line sets the default "policy" for the machine. In this case it drops all incoming packets that don't match an ACCEPT rule on the floor.

---

### Post by bax001 on 2020-05-30
1) VPN PPTP server is on my Asus router at home (I use DDNS as  have a dynamic IP)
2) On Amazon server I have a Discord bot (written in Python) and an Apache with PHP script to harvest data from one website and pass that data to a bot (PHP script needs a VPN connection as a website doesn't allow connections through VPS, proxy etc.) . This is all what is used on that server.

---

