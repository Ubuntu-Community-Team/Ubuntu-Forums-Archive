---
title: "Ubuntu Server 10.10 Setup"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by andrewdavies007 on 2011-03-20
Hi,
I have been using ubuntu desktop for a couple of years and now I want to setup a server.

The server would be setup on a home network:
 Server           >
 Windows PC's >Router > Internet
 Linux PC's      >

I also have a ubuntu 10.10 laptop which will sometimes access from the internet and sometimes from withing the home network

I want to be able to:
host websites (HTML, php, mysql)
run my own programs (java) such as a chat server that i have written myself
use ssh

Can ubuntu do all this (I'm assuming it can)?
And does anyone know of any good tutorials of how to set this all up

Thanks in Advance
Andrew

---

### Post by taseedorf on 2011-03-21
YES! Love it.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

that will tell you how to set up a LAMP server.... which is what you want to do.

this will tell you how to set up an ssh server

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

and this will tell you how to do VNC or remote desktop if you wish

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

that should get you started

you also will need to edit your iptables (firewall) to allow incoming connections for your webserver, php....remote desktop

and EASIER way to do this is to download Firestarter and do it from a GUI

sudo apt-get install firestarter

if running Ubuntu server and no GUI....you'll have to read on how to edit IPtables...which is Ubuntu's firewall

ALSO...make sure to forward all ports on your router so that people on the internet can access your http server and such

---

