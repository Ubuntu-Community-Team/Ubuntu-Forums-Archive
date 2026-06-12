---
title: "Quick linux port question?"
date: 2005-08-15
forum: Networking &amp; Wireless
---

### Post by c-m on 2005-08-15
I have amule installed in ubuntu and emule in XP. Both are set to use the exactly the same ports (as those are the ones forwarded through my router).

The problem is that my windows emule has a high ID and the ports are open yet if i boot into ubuntu and load up amule it says the port is blocked and hence i get a lowid.

Firstly what is the command to check what ports are open?

secondly if i find the ports i need are closed, what is the command to open them?

Cheers.

---

### Post by h4rdc0d3 on 2005-08-16
**While I am not learned in mules...**

```
netstat -tuna
```

t=tcp
u=udp
n=numerical ip addr (vice names)
a=all

See 'man netstat' or 'info netstat' for the whole deal.

Btw, simply running a program opens a port... for instance, starting up a default install of the Apache web server opens up port 80 (HTTP). You need not worry about opening ports, however you may need worry about your router port forwarding traffic to your computer. For those details please inquire with your router's documentation.

---

### Post by c-m on 2005-08-16
[QUOTE=h4rdc0d3]**While I am not learned in mules...**

```
netstat -tuna
```

t=tcp
u=udp
n=numerical ip addr (vice names)
a=all

See 'man netstat' or 'info netstat' for the whole deal.

Btw, simply running a program opens a port... for instance, starting up a default install of the Apache web server opens up port 80 (HTTP). You need not worry about opening ports, however you may need worry about your router port forwarding traffic to your computer. For those details please inquire with your router's documentation.[/QUOTE]
 the router is configured correctly, this is proved by the fact that windows on the same machine has the required ports open, yet linux on the same machine with the same ip address doesnt.

This was proved by running the command you typed above. I setup amule to use port 666 tcp, yet in the long list of ports shown by that command port 666 is no where t be seen. and most connections are being attempted around ports 53000+

---

### Post by h4rdc0d3 on 2005-08-16
I would think that those high port (53000+) connections are outbound. Sorry, I can't be more help. There's gotta be someone else who knows about amule.

---

### Post by kostkon on 2005-08-16
c-m maybe I know a solution to your problem.

I had the same problem when I was dual booting Windows ME and Mandrake 9.0.

I think that when you log in to Linux, router gives a different IP to Linux and when you are in Windows a different one again. For example, when you are in Windows your PC has the IP 192.168.1.3 and then in Linux you have 192.168.1.5!

Thus, the only solution is to open the same ports in your router for the two IPs or just see what IP you have when you have Windows and then setup Linux to use this IP only  instead of getting it through DHCP.

Go into console in Windows and type *ipconfig* to see what IP you have and then do the same in Linux with *ifconfig*; if they don't match then I have right.

---

### Post by yyagol on 2005-08-17
I have the same problem and both IP's are the same
still netstat dont show the ports 2 b open.
i even try to add the program (linuxdcpp) to the /etc/services
but it dos'nt seem to help
when i run **linuxdcpp** in terminal i get restricted for the ports
only when i run as root its o.k. but i **do not** want to run as root!!
my router is cool couse XP work fine. when i use the original installed ports it works.
the question is where to change this ports in linux that it'll use the ones you want?

---

### Post by cwaldbieser on 2005-08-17
[QUOTE=yyagol]I have the same problem and both IP's are the same
still netstat dont show the ports 2 b open.
i even try to add the program (linuxdcpp) to the /etc/services
but it dos'nt seem to help
when i run **linuxdcpp** in terminal i get restricted for the ports
only when i run as root its o.k. but i **do not** want to run as root!!
my router is cool couse XP work fine. when i use the original installed ports it works.
the question is where to change this ports in linux that it'll use the ones you want?[/QUOTE]

On GNU/Linux, low numbered ports (less than 1024) require admin privledges to access.  High number ports do not.  If you want to run a server app and not run as root, you should configure it to run on a higher number port.

---

