---
title: "IP address based restriction for remote desktop access"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by ssppune on 2009-12-03
Hi, I configured the remote desktop feature of Ubuntu 9.04.It is working file on entire network.
 
I want to restrict the access of my Ubuntu PC 's desktop to one windows vista PC only. I want this restriction on IP address based.
 
How can i do that? Which config file need to be edited to achieve it?

---

### Post by ukripper on 2009-12-03
you can either use firestarter GUI firewall or command line iptables to block that ip.

For iptables follwo this excellent guide - [http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

otherwise if you want to use firestarter, it is very simple enough. install it ```
sudo apt-get install firestarter
```

---

### Post by ssppune on 2009-12-05
That is not desired... as Nmap indicates that port 5900 is filtered. I donot want to give the slightest of the idea , what is on my ubuntu machine.

---

