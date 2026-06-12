---
title: "ssh clarification"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by Dark006 on 2009-07-09
Ok, so I just have a quick question about ssh. From what I've heard, if you have ssh setup properly, you can access it from anywhere in the world through Cygwin or putty (windows) or the CLI in linux. How would one go about doing this? If you have openssh-server installed, would you just ssh your **username@your-external-ip**? (external ip found at "whatismyip.com")

Or would you have to know your IP thats assigned to your computer in your network and then do; **ssh internal-ip@external-ip** ??

Any clarification or explanation is appreciated, thanks.

---

### Post by spiderbatdad on 2009-07-09
you can test ssh inside your network like```
ssh -X username@internalip
```You have to forward port 22 to the internal ip address of the machine you are accessing via your router's configuration page. If you are accessing from outside your network, then use the external ip address. Have you read the community ssh documentation? [https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

---

### Post by Dark006 on 2009-07-10
@[COLOR="Red"]spiderbatdad[/COLOR]
Ok I have my router now forwarding the port (not 22, I changed sshd_config file) and I ran **ssh -X username@interal-ip** and it appears to work. Does this mean it will work from outside my network now (after using the external IP)?

---

### Post by The Cog on 2009-07-10
> **Dark006 said:**
> @[COLOR="Red"]spiderbatdad[/COLOR]
Ok I have my router now forwarding the port (not 22, I changed sshd_config file) and I ran **ssh -X username@interal-ip** and it appears to work. Does this mean it will work from outside my network now (after using the external IP)?

Should do. If you can connect internally, the only hiccup might be a problem with the router forwarding. Be **very** careful with your password - there are lots of password-guessing bots out there. You may want to look at AllowUsers in sshd.conf to limit who can log in and from where. Actually, I have a firewall configured that only allows SSH from my home LAN or from work.

---

### Post by spiderbatdad on 2009-07-11
> **Dark006 said:**
> @[COLOR="Red"]spiderbatdad[/COLOR]
Ok I have my router now forwarding the port (not 22, I changed sshd_config file) and I ran **ssh -X username@interal-ip** and it appears to work. Does this mean it will work from outside my network now (after using the external IP)?

Yes. should also work via external ip address as long as you arent behind a nat, or some other isp related issue. With router frowarding, it is a good idea to give your machine a static address...since the router is forwading to the same address everytime. Do this in the file /etc/network/interfaces with something along these lines, generally assigning a number outside the dhcp range.
```
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
network 192.168.1.1
broadcast 192.168.1.255
gateway 192.168.1.1

```

---

### Post by porchrat on 2009-07-11
Also depends on whether or not you can find your machine from anywhere in the world. If your external IP address assigned to you by your ISP is dynamic you are going to need to setup a DDNS. No good port forwarding if there is no way to reach the router from the outside world. I assume you have that dealt with already though.

---

### Post by MrWES on 2009-07-11
> **Dark006 said:**
> Ok, so I just have a quick question about ssh. From what I've heard, if you have ssh setup properly, you can access it from anywhere in the world through Cygwin or putty (windows) or the CLI in linux. How would one go about doing this? If you have openssh-server installed, would you just ssh your **username@your-external-ip**? (external ip found at "whatismyip.com")

Or would you have to know your IP thats assigned to your computer in your network and then do; **ssh internal-ip@external-ip** ??

Any clarification or explanation is appreciated, thanks.

Here's a couple of links you might want to read:
[http://ubuntuforums.org/showthread.php?t=254149]("http://ubuntuforums.org/showthread.php?t=254149")
[http://www.debian-administration.org/articles/152]("http://www.debian-administration.org/articles/152")
[http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/]("http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/")
[http://www.dyndns.com/]("http://www.dyndns.com/")


~Bill

---

