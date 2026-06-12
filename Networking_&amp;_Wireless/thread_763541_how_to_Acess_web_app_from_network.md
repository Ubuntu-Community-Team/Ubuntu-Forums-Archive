---
title: "how to Acess web app from network"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by jagdishrao on 2008-04-23
hi guys

i am on acer 4710 Laptop with ubuntu gutsy sibbon on it.
i am a rails developer and am running a mongrel webserver 
(a web server for ruby on rails platform) on port no 3000.

while the server is running i am able to acces the app with url
[http://localhost:3000/](http://localhost:3000/) and it works fine
but
when other people on network want to test the application
using the url [http://192.167.0.67:3000/](http://192.167.0.67:3000/)

firefox does not show the page and throws a error

Unable to connect


firefox can't establish a connection to the server at 192.168.0.67:3000.

strangely there some other ubuntu and windows development machines
on which when we access the apps with the url format
[http://ip_address:port_no/](http://ip_address:port_no/)
it works fine

pls help me 
what setting i need to set for this to work.
FYI : i have sshd(ssh server) and smbd(samba server) installed and running as service.

Regards
Jags

---

### Post by SpaceTeddy on 2008-04-23
this sounds more like a network card binding problem than network. 
But i can possibly think of two things going wrong

1.) your Development server only binds to the loopback device. Check this via ```
sudo netstat -lnp
``` and search for something listeing on port 3000. If there is such a thing, make sure it is connected to the IP 0.0.0.0 or the IP of your network card. If it only specifies 127.0.0.1, then your webserver only binds to the localhost and is NOT accessable from the outside. You will need to reconfigure the server

2.) you have a firewall or iptables set installed that does not allow connections to your computer. Firestarter is a usual app that gets in the way. Check with this command ```
sudo iptables -L
``` to see your settings. if there is lots, you probably have a firewall problem. As an example, i will post something here what it should look like:
>  sudo iptables -L 
Chain INPUT (policy **ACCEPT**)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy **ACCEPT**)
target     prot opt source               destination         

the bold bits are the important ones. They are the defaults that take place on your machine. If there is something in there, the easiest way (to check) is to flush the input and output chains and set the default to ACCEPT. do this via
```
sudo su
iptables -F INPUT
iptables -F OUTPUT
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
```
you can replace the first command (sudo su) with a sudo infront of every command following it. 
These commands are not permanent, a reboot will undo all done changes...

that is all i can think of right now - hope it helps :)

---

### Post by jagdishrao on 2008-04-24
hey spaceteddy

thank you man

sudo netstat -lnp showed 3000 binded to 127.0.0.1
i am using aptana ide for ror development and when u create a 
mongrel server instance it defaults to 127.0.0.1 as host parameter.

changed it to 0.0.0.0 and it worked

thanks again guys 
jags

---

