---
title: "cannot ssh to my desktop"
date: 2014-05-25
forum: Networking &amp; Wireless
---

### Post by htorres on 2014-05-25
I just recently installed xubuntu and installed the openssh-server package. I made sure the daemon was running using ```
service ssh start
``` and it said it was already running.

I tried connecting with my Macbook, and it hung. My instinct was to try and ping the desktop, but it just came back with request timeouts. I tried from my Windows machine, and it said the host was down.

I checked my firewall with ```
sudo iptables -L
``` and it said all the policies were set to accept. Also, I'm typing this from the desktop in question, so the internet works.

What could be causing this?

---

### Post by Hadaka on 2014-05-25
Hi, here are some tutorials with good information
[http://chrisjean.com/2009/02/19/ssh-tutorial-for-ubuntu-linux/](http://chrisjean.com/2009/02/19/ssh-tutorial-for-ubuntu-linux/)

[http://teamprincipia.wordpress.com/2008/05/29/beginning-ssh-on-ubuntu/](http://teamprincipia.wordpress.com/2008/05/29/beginning-ssh-on-ubuntu/)

Test Your Desktop
If your desktop is configured correctly then do.
at the Desktop
```
ssh localhost
```
it should connect ask for your password
if it does not...find out why. check your configurations.
*do yourself a favor and dig for the answers.

**If you are trying to ssh to the desktop via your routers ip...that wont work
from a on your lan machine...you need to test that from off your lan net.

---

### Post by htorres on 2014-05-25
> *do yourself a favor and dig for the answers.

I did. Obviously you skipped over the part where I said I couldn't even ping the box. ssh-ing locally was one of the first things I tried and it worked.

I can't even ping the box.

---

### Post by steeldriver on 2014-05-25
If the desktop is wired and the other devices you've been trying to access it from are wireless, the first thing I would check is that wireless isolation is not enabled on the router. Also might be worth power cycling or rebooting the router. If you still can't ping then start looking at the netmasks and default route info on the repsective machines.

---

### Post by Hadaka on 2014-05-25
ok. no i did not see that you did "ssh localhost"
can you access the internet with that machine?
can the desktop ping it's self?
what is the EXACT command you are using to test ssh?
what ports are set to "Listen" in the desktop?
To view listen ports
```
cat /etc/ssh/sshd_config
```
have you gone over every single line that it takes to build
ssh on a machine...the links i sent. printouts and real data
informtion is needed to assist you in finding an answer.

---

### Post by htorres on 2014-05-26
> If the desktop is wired and the other devices you've been trying to  access it from are wireless, the first thing I would check is that  wireless isolation is not enabled on the router. Also might be worth  power cycling or rebooting the router. If you still can't ping then  start looking at the netmasks and default route info on the repsective  machines.

The desktop is wireless as well. Everything's wireless.

Out of curiosity I just tried to ping my Macbook from the desktop and it didn't work either. But, I can ping my iPhone from both the desktop and the Macbook.

---

### Post by jonobr on 2014-05-27
This doesn't seem to be an ssh problem.
If you cant ping from device a to device b then ssh wont work.
If ping is not working from mac to desk and not working from desk to mac but is working from desk to iphone, then it sounds as if either your mac is on a different network, or something else more fundamental is going on.

Try posting ifconfig from your linux box and the ipconfig from your mac.
IP on the iphone would also help

---

