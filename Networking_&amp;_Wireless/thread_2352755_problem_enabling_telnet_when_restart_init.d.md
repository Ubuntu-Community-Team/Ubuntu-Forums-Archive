---
title: "problem enabling telnet when restart init.d"
date: 2017-02-15
forum: Networking &amp; Wireless
---

### Post by samuelbles on 2017-02-15
hi,

I have a problem installing telnet in my ubuntu 16.04. According to this tutorial [http://quehow.com/how-to-install-and-use-telnet-in-ubuntu/3629.html](http://quehow.com/how-to-install-and-use-telnet-in-ubuntu/3629.html) , i have to restart the init.d .
But when i  entering this command ```
sudo /etc/init.d.open-bsd-inetd restart
``` the reply is ```
sudo: /etc/init.d.open-bsd-inetd: command not found
``` .
when i skip that step, i just trying enter ```
telnet localhost
``` but the response is ```
Trying 127.0.0.1...telnet: Unable to connect to remote host: Connection refused

```
The purpose i want to turn on telnet because i want to learn socket programming in python. that's why i telnet to this localhost. Is it possible?
 same as when i using ssh command. 
Please help, thanks before

---

