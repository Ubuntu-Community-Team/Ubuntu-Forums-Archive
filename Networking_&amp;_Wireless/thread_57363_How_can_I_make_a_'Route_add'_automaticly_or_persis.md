---
title: "How can I make a 'Route add' automaticly or persistent?"
date: 2005-08-16
forum: Networking &amp; Wireless
---

### Post by mikuskuikku on 2005-08-16
I use a 2 modems to connect to each outhers network (ppp).
But when i made connection between the modems (authorizing and so on) I need to make a 'Route add' so that my computer finds the way through the modem when contacting a computer in the other network. (I think I need to do a 'Route add' on the both computers holding the modems.)

Is there a way to make a 'Route add -net 192.168.0.0/24 gw 192.168.10.1' persistant or to automaticly execute this command when connection is made (I'm using 'mgetty' to connect and answer incomming calls).

Pleace help!
<<mikuskuikku>>

---

### Post by PeP on 2005-08-16
I think that you  are looking to add a script in thisfolder:
/etc/ppp/ip-up.d/

quote from /etc/ppp/ip=up

> # This script is run by the pppd after the link is established.
# It uses run-parts to run scripts in /etc/ppp/ip-up.d, so to add routes,
# set IP address, run the mailq etc. you should create script(s) there.
#
# Be aware that other packages may include /etc/ppp/ip-up.d scripts (named
# after that package), so choose local script names with that in mind.
# 

so creating /etc/ppp/ip-up.d/route-up.sh 
containg
#!/bin/sh
route add -net 192.168.0.0/24 gw 192.168.10
should work.

(and dont forget to make it executable:
```
sudo chmod u+x etc/ppp/ip-up.d/route-up.sh
```
)


I think you are supposed to remove the route when the line is down(add a script to do that in /etc/ppp/ip-down.d) , but I guess that you don't need this for your application.

---

### Post by mikuskuikku on 2005-08-16
He still doesn't make the route.
Im run the 'pon MyConn' fron a standard user (in 'users' and 'dip' group) called 'jvsh'.
The 'route-up.sh' looks like this:
-rwxr-xr-x 1 root root ....

Do I need to configure a nother file to start the 'route-up.sh'?
Is the script run as root so I don't need to type 'sudo'?
Hopfully I don't need to type 'sudo' when the user 'jvsh' doesn't got sudo priviliges.

<<mikuskuikku>>

---

