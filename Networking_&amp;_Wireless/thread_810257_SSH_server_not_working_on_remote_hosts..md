---
title: "SSH server not working on remote hosts."
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by Dennis Beekman on 2008-05-28
so i decided that i needed to use my workstation @home on a remote location over the internet and setup a openssh tunnel and vnc/ftp server on that workstation... all was well so far.

Any local network host can use the ssh server and both services just fine and everything works.
But when i tell my modem to forward port 22 from the servers ip number to the external isp ip number i cannot get a connection.

When i load the isp ip in putty it fails with the message "error - connection denied..."
even with all firewall turned off the device doesn't become accessable from the wan side of the router from anywhere (checked my at my friends house aswell.)

Did anyone have a similar problem, and how was it resolved... ?
I found a lot of refferences on google but non actually held a solution to the problem.:(

---

### Post by bluefrog on 2008-05-28
not sure what kind of port forwarding you are doing there.

On your router, you need to forward/redirect the port 22 to your machine internal IP (e.g. 192.168.1.1) and port 22

---

### Post by Dennis Beekman on 2008-05-28
i made a virtual server on my modem...

It is setup as follows

Internal port start: 22
Internal port last: 22

Protocol TCP/UDP

External port start: 22
External port last: 22

Internally on any of my 192.168.0.* hosts it works fine, but externally it doesn't .... "error: connection denied i get"

i'm thinking that my wan ip blocked from the firewall or that the ssh server need to be told to allow remote hosts...but how does one do this ? and why is this not setup by default...its what ssh is for right so why block them...

---

### Post by Wicca on 2008-05-28
> **Dennis Beekman said:**
>  But when i tell my modem to forward port 22 from the servers ip number to the external isp ip number i cannot get a connection.

It's the other way around. You have to 'tell' your modem/router to forward port 22 requests, coming from your external IP number, to the IP-address of your server.

> **Dennis Beekman said:**
> i made a virtual server on my modem...

It is setup as follows

Internal port start: 22
Internal port last: 22

Protocol TCP/UDP

External port start: 22
External port last: 22


Where is the IP-address of your ssh server in this setup?

> 
and why is this not setup by default...its what ssh is for right so why block them...
You should be very happy that things don't work by default... your LAN should be overcrowded with hackers, crackers and porn otherwise :lolflag:. Besides that, how can by default your modem/router be aware of your specific setup, like the IP-address of your ssh server?

Check the settings for the virtual server. It should point to the IP-address of your ssh-server.

---

### Post by Dennis Beekman on 2008-05-28
oke, oke your got me there... :lolflag:

I made a virtual server to the specific adress of my server to allow sending and recieving of packages on port 22 via my modem... it targets my server offcource.

I also do not get a "cannot connect error" i get a "connection denied" error wich makes me believe that it is blocking me instead of not recieving me.:confused:

is there a setting in sshd wich tells it to allow remote machines until told otherwise ? or visa versa ?

---

### Post by Wicca on 2008-05-28
> **Dennis Beekman said:**
> 
I made a virtual server to the specific adress of my server to allow sending and recieving of packages on port 22 via my modem... it targets my server offcource.

Well ehh..:???: I am not sure what you mean with 'sending', as your ssh-server isn't sending anything at all on port 22, at least nothing that needs to be  configured in a router or firewall. You only have to configure your modem/router so that it will accept traffic from the outside world on port 22 and send it further to your internal ssh-server, so he can receive it.

> 
is there a setting in sshd wich tells it to allow remote machines until told otherwise ? or visa versa ?

Your ssh-server is not aware of remote vs. 'nearby' machines, it just welcomes packets from anywhere, as long as you do not tell him to do not so.

Some ISP's will block traffic on all ports below 1024, perhaps that's the case. You can easily find out by changing the port to a higher number. You can change the port in sshd_config and then restart sshd. After that, configure the virtual server settings in your router to accept and forward that specific port.

---

