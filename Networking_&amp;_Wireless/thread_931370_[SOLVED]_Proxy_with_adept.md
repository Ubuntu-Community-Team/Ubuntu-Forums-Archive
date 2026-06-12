---
title: "[SOLVED] Proxy with adept"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by achilleslaststand on 2008-09-27
Hello, I'm am connected to the internet through a proxy and I've already configured my apt-get to use it (by editing the .bashrc file) but I don't know how to configure adept to work with...
Could anybody help me ?

---

### Post by poison-br on 2008-09-29
> **achilleslaststand said:**
> Hello, I'm am connected to the internet through a proxy and I've already configured my apt-get to use it (by editing the .bashrc file) but I don't know how to configure adept to work with...
Could anybody help me ?

Some issue here, and the real problem is that the TI retard blocked all browser trafic that uses wht word "proxy" so i cant really open any site with help about it.
My proxy requires a username and a pwd also.
Was able to make Synaptic to work tho

---

### Post by poison-br on 2008-09-29
> **achilleslaststand said:**
> Hello, I'm am connected to the internet through a proxy and I've already configured my apt-get to use it (by editing the .bashrc file) but I don't know how to configure adept to work with...
Could anybody help me ?

Just got it to work.

1 - open console
2 - sudo kate /etc/apt/apt.conf
3 - Add this: 

Acquire::http::Proxy "http://username:password@IP:port"; 

Where "username" : is your username if proxy requires it
Where "password" : is your password if proxy requires it

Example: 

Acquire::http::Proxy "http://kenny:123456@172.16.0.1:8080"; 

4 - save the file.
5 - All done, test adept.

Hope it helps. :D

---

### Post by achilleslaststand on 2008-10-07
It works perfectly for me.
Thanks a lot

---

### Post by vivek962 on 2008-10-17
hello.........i am using ubuntu 7.10.....and i used ur method but it says that/tmp/kde /username is owned by uid 1000 instead of 0...and nothing happens..

---

