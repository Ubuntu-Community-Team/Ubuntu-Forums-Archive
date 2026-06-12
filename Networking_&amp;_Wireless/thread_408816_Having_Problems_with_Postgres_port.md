---
title: "Having Problems with Postgres port"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by microchip13 on 2007-04-13
Sorry for the vauge title, I still hope some people will read this.

I'm having problems with the firewall(although it seems as though there are no rules, iptables -L produces no interesting output).


The services I want open to the world are Postgres(5432) and SSH(22). 

If I nmap localhost, I get these results:
Interesting ports on localhost (127.0.0.1):
(The 1671 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
22/tcp   open  ssh
631/tcp  open  ipp
5432/tcp open  postgres

Here, these are what I want open. This is correct.

The IP address of the computer is 192.168.0.109(The same one that's mentioned above), and if I nmap that I get these results:

Interesting ports on 192.168.0.109:
(The 1673 ports scanned but not shown below are in state: closed)
PORT   STATE SERVICE
22/tcp open  ssh



Anything I can do here? I just need all of the ports that show up nmapping localhost open to places other than localhost. SSH works though and that's confusing me.


Thanks Very Much In Advance!

---

### Post by amohanty on 2007-04-13
If your IP is static or dhcp on a very small home lan (it doesnt change much in that case), put the following line in your **/etc/hosts** file:

192.168.0.109    localhost

restart postgres and run another nmap scan.

---

### Post by microchip13 on 2007-04-14
> **amohanty said:**
> If your IP is static or dhcp on a very small home lan (it doesnt change much in that case), put the following line in your **/etc/hosts** file:

192.168.0.109    localhost

restart postgres and run another nmap scan.

I added that line into the hosts file and restarted postgres, unfortunately, it seems to have no effect.

---

### Post by amohanty on 2007-04-15
Probably shoudl have asked you to try this first
use the **listen_addresses** directive
[http://www.postgresql.org/docs/8.2/static/runtime-config-connection.html#RUNTIME-CONFIG-CONNECTION-SETTINGS](http://www.postgresql.org/docs/8.2/static/runtime-config-connection.html#RUNTIME-CONFIG-CONNECTION-SETTINGS)

HTH
AM

---

### Post by microchip13 on 2007-04-16
It is currently set that way, unfortunately, that doesn't seem to be the case.

---

### Post by amohanty on 2007-04-16
Sorry I should have been clearer, I mean set it to one specific IP not *.

HTH
AM

---

### Post by microchip13 on 2007-04-16
Ah, I can give that a shot tomorrow when I'm at the computer yet again.


Thanks for all your help so far.

---

### Post by amohanty on 2007-04-17
Technically if the listen_addresses is set to *, and the ip is set in the /etc/hosts a reboot should do the trick. Anyway try setting it to the ip.

AM

---

### Post by microchip13 on 2007-04-17
Alright, everything checks out as you've mentioned, but still no go.

Port 631 now shows up when I nmap the IP address, but still not postgres.





Arrg! This is getting annoying.


Thanks again for helping!

---

### Post by microchip13 on 2007-04-18
Alright, I found out the problem...My own stupidity.


listen_address was set to *, but I neglected to uncomment the line.


It works great, thanks! now just getting PostGIS to work.

---

