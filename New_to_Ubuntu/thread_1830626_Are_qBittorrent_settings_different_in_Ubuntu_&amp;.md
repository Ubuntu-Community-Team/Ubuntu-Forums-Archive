---
title: "Are qBittorrent settings different in Ubuntu &amp; Kubuntu?"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by babloo75 on 2011-08-22
I have installed Kubuntu 11.04 on a desktop computer which initially had Ubuntu 11.04.
All was fine earlier that the 'connection status' icon was green and speeds were good.
Now with Kubuntu and same settings (port opened), the icon remains yellow and speeds are low. The tool tip window states that "No direct connections. This may indicate network configuration problems"
Can you please help me.

---

### Post by ankspo71 on 2011-08-22
Hi,
Do you have your UFW firewall and router firewall opened on port 6881? If either of these is not opened, then you will see a yellow icon in qBittorrent like you describe.

To check which ports are opened in UFW, you can use this command in your terminal:

```
sudo ufw status
```

Your results should look like this:
> james@Kubuntu:~$ sudo ufw status
[sudo] password for james: 
Status: active

To                         Action      From
--                         ------      ----
6881/tcp                   ALLOW       Anywhere
6881/udp                   ALLOW       Anywhere
6881/tcp                   ALLOW       Anywhere (v6)
6881/udp                   ALLOW       Anywhere (v6)


Or you can install "gufw" to configure the firewall graphically.


Additional info on UFW is here.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
Additional info on port forwarding (for routers)
[http://portforward.com/](http://portforward.com/)


PS. The qBittorrent settings are probably the same in Kubuntu and Ubuntu.

---

### Post by ankspo71 on 2011-08-22
Sorry about the duplicate reply.

---

### Post by babloo75 on 2011-08-22
It says:

babloo@babloo-OptiPlex-330:~$ sudo ufw status
[sudo] password for babloo: 
Status: inactive
babloo@babloo-OptiPlex-330:~$

---

### Post by babloo75 on 2011-08-22
I installed gufw, as advised earlier.
And opened the ufw ports as well.
Here is the output: 
babloo@babloo-OptiPlex-330:~$ sudo ufw status
[sudo] password for babloo: 
Status: active

To                         Action      From
--                         ------      ----
6881/tcp                   ALLOW       Anywhere
6881/udp                   ALLOW       Anywhere
xxxxx                     ALLOW       Anywhere
xxxxx                     ALLOW       Anywhere

babloo@babloo-OptiPlex-330:~$ 

[FONT="Arial Narrow"]*(xxxxx are the two ports, I have opened in my router)*[/FONT]

The icon is still yellow. Please help

---

