---
title: "UFW and Port Forwarding"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by stack on 2008-06-19
I've got my Ubuntu box acting as a router / firewall for my network and everything is working fine.  I need to forward some ports into my network, but I'm unsure how to do this.  I have the proper iptables command to enable it, and if I run it from the command line, it works.  I imagine the rule has to go into /etc/ufw/before.rules, but I don't know where.

iptables code that works:
```
sudo iptables -A PREROUTING -t nat -p tcp -i eth0 --dport 50002 -j DNAT --to 192.168.100.20
```

ufw status:
```
To                         Action  From
--                         ------  ----
Anywhere                   ALLOW   192.168.100.0/24
22:tcp                     ALLOW   Anywhere
22:udp                     ALLOW   Anywhere
192.168.100.20 50002:tcp   ALLOW   Anywhere
192.168.100.20 50002:udp   ALLOW   Anywhere

```

/etc/ufw/before.rules:
```
 
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.100.0/24 -o eth0 -j MASQUERADE

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT

# Don't delete these required lines, otherwise there will be errors
*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]
# End required lines


# allow all on loopback
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -i lo -j ACCEPT

# connection tracking rules
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

# drop INVALID packets
# uncomment to log INVALID packets
#-A ufw-before-input -m conntrack --ctstate INVALID -j LOG --log-prefix "[UFW BLOCK INVALID]: "
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP

# connection tracking for outbound
-A ufw-before-output -p tcp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
-A ufw-before-output -p udp -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

# allow dhcp client to work
-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT

#
# ufw-not-local
#
-A ufw-before-input -j ufw-not-local

# if LOCAL, RETURN
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN

# if MULTICAST, RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN

# if BROADCAST, RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN

-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK NOT-TO-ME]: "

# all other non-local packets are dropped
-A ufw-not-local -j DROP

# allow MULTICAST, be sure the MULTICAST line above is uncommented
-A ufw-before-input -s 224.0.0.0/4 -j ACCEPT
-A ufw-before-input -d 224.0.0.0/4 -j ACCEPT


# don't delete the 'COMMIT' line or these rules won't be processed
COMMIT

```

---

### Post by clarknova on 2008-09-30
```
-A PREROUTING -p tcp -m tcp -i eth0 --dport 50002 -j DNAT --to-destination 192.168.100.20
```

I believe that goes right before your MASQUERADE line. Or at least I can say that I had that line right before my MASQUERADE line on an old debian router and it was working fine.

db

---

### Post by clarknova on 2008-10-02
I still can't get port forwarding and ufw to work together. I tried stack's before.rules file (substituting my own values) and still no dice. When I enable ufw, forwarding stops. When I disable ufw I get forwarding back.

Anybody have this working? stack, does the config you posted here work for you? Did you have to alter any other ufw config files to make it roll?

db

---

### Post by clarknova on 2008-10-06
> **clarknova said:**
> I still can't get port forwarding and ufw to work together.
[URL="https://help.ubuntu.com/8.04/serverguide/C/firewall.html"]
https://help.ubuntu.com/8.04/serverguide/C/firewall.html[/URL]

Check the section on masquerading. The tutorial assumes that your LAN is 192.168.0.0/24. Aside from doing everything there, you must also add at least one rule to allow your lan to access the outside world.

```
sudo ufw allow from 192.168.0.0/24 to any
```

Then restart the firewall.

db

---

### Post by asm2000 on 2008-11-07
please every body here...i wana make ubuntu proxy server in my country where no blocked websites..coz i ve in other country where i work some blocked sites...so i want to make my ubuntu server forward internet so i can use it as proxy in the other country to use in order to open these blocked sites.....thanks for all of you..

---

### Post by jure1873 on 2008-11-07
asm2000: this is ot 
install squid, allow connections from localhost and connect to your box with ssh and forward -L 3128:localhost:3128, then set your proxy to localhost in firefox

---

### Post by asm2000 on 2008-11-07
thanks its nice of you to reply me this post ..but still vague for me could u please simplify it for me ...i know much headacke but im still new to ubuntu servers..thanks again

---

### Post by clarknova on 2008-11-12
> **asm2000 said:**
> i wana make ubuntu proxy server in my country where no blocked websites.

Rephrasing your question: How do I use an ubuntu server in country B act as a proxy for web client in country A, where certain web sites are blocked in country A, but not blocked in country B?

If that is your question then try searching for instructions on using ssh or putty (from windows) to connect to an ubuntu machine and use it as a socks proxy. Here's a start:

[http://ubuntuforums.org/showthread.php?t=952043](http://ubuntuforums.org/showthread.php?t=952043)

You're very off topic in this thread though, so post your further questions somewhere more appropriate, like in the above-linked thread.

db

---

### Post by asm2000 on 2008-11-14
thanks dear finally i did it and like to sumarize steps for others :
after ubuntu server installation::
---------------------------------------deleting all roles---------------------------------------
sudo iptables -F
sudo iptables -X
sudo iptables -t nat -F
sudo iptables -t nat -X
sudo iptables -t mangle -F
sudo iptables -t mangle -X
---------------------------------------allowing NAT---------------------------------------
# modprobe iptable_nat
# echo "1" > /proc/sys/net/ipv4/ip_forward
# iptables â€“t nat â€“A POSTROUTING â€“o eth0 â€“j MASQUERADE
---------------------------------------installing squid---------------------------------------
sudo apt-get install squid
---------------------------------------configuring squid---------------------------------------
sudo -s
cd /etc/squid
mv squid.conf squid.conf.original
touch squid.conf
nano squid.conf
::then add :: considering server name is [server]::

http_port 3128
visible_hostname server
acl all src 0.0.0.0/0.0.0.0
http_access allow all               [to be deleted later after finishing all configuration]
---------------------------------------restarting squid---------------------------------------
sudo /etc/init.d/squid restart
---------------------------------------preparing cache---------------------------------------
sudo nano /etc/squid/squid.conf
::and add::

cache_mem 512 MB
maximum_object_size_in_memory 64 KB
maximum_object_size 1024 MB
minimum_object_size 0 KB
cache_swap_low 90
cache_swap_high 95
cache_dir ufs /var/spool/squid 81920 16 256
cache_access_log /var/log/squid/access.log
refresh_pattern ^ftp: 15 20% 2280
refresh_pattern ^gopher: 15 0% 2280
refresh_pattern . 15 20% 2280
---------------------------------------proxy authentication---------------------------------------
sudo apt-get install apache2-utils
---------------------------------------
sudo -s
touch /etc/squid/squid_passwd
htpasswd /etc/squid/squid_passwd username

*then it will ask for pass

::then after adding users add following lines to squid.conf::

auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid/squid_passwd
acl allowed_users proxy_auth REQUIRED
http_access allow allowed_users

---

### Post by rotty3000 on 2009-02-04
I figured out how to get DNAT to work with ufw.

Add the following to the very beginning of the [FONT="Courier New"]before.rules[/FONT] file.

```
#
# rules.before
#
# Rules that should be run before the ufw command line added rules. Custom
# rules should be added to one of these chains:
#   ufw-before-input
#   ufw-before-output
#   ufw-before-forward
#

*nat
:PREROUTING - [0:0]

# My DNAT rules
-A PREROUTING -i <iface> -p tcp --dport <port> -j DNAT --to-destination <addr>
-A PREROUTING -i <iface> -p udp --dport <port> -j DNAT --to-destination <addr>

# don't delete the 'COMMIT' line or these nat table rules won't be processed
COMMIT

...
```

then

```
$ sudo ufw disable
$ sudo ufw enable
```

Hope that answers many people's questions.

---

### Post by ene_dene on 2009-10-03
This is strange, first rule works but the other ones are ignored (other ones in prerouting, the last rule masquerade works fine). Here's my before.rules:
```
#nat Table rules
*nat
:PREROUTING ACCEPT [0:0]
-A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.0.200:80
-A PREROUTING -i eth1 -p tcp --dport 10090 -j DNAT --to 192.168.0.2:22

:POSTROUTING ACCEPT [0:0]
#forward from eth0 through eth1
-A POSTROUTING -s 192.168.0.0/24 -o eth1 -j MASQUERADE
COMMIT
```
The forwarding of port 80 to host 192.168.0.200 works fine, but forwarding from 10090 to 192.168.0.2 port 22 doesn't work. And if I interchange the rules then the forwarding to 22 works fine and to 80 on a 192.168.0.200 doesn't.
I assume that I need to add something to before second rule, but what?

EDIT:
It's more complicated than this... Now some rules work... other don't, I don't know where to start.
Is there some other firewall that I could use like Firestarter (I can't use it on server, because no gui) where port forwarding is easier?

---

### Post by rotty3000 on 2009-10-03
Looks like you forgot the COMMIT instruction after the table rules. 

Try:

```
#nat Table rules
*nat
:PREROUTING ACCEPT [0:0]
-A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.0.200:80
-A PREROUTING -i eth1 -p tcp --dport 10090 -j DNAT --to 192.168.0.2:22
COMMIT

:POSTROUTING ACCEPT [0:0]
#forward from eth0 through eth1
-A POSTROUTING -s 192.168.0.0/24 -o eth1 -j MASQUERADE
COMMIT
```

... I think!

---

### Post by ene_dene on 2009-10-04
Thank you for your answer, but the problem was a little more confusing than that. Some rules that I put to before.rules were working after I deleted them, and some didn't after I put them (I also tried iptables -F)... After restart everything works like it should, here is how I put it:
```
:POSTROUTING ACCEPT [0:0]
#forward from eth0 through eth1
-A POSTROUTING -s 192.168.0.0/24 -o eth1 -j MASQUERADE
-A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.0.200:80
-A PREROUTING -i eth1 -p udp --dport 10090 -j DNAT --to 192.168.0.202:22
-A PREROUTING -i eth1 -p tcp --dport 10090 -j DNAT --to 192.168.0.202:22
COMMIT

```
I will be very glad if programmers of ufw would put masquerading and forwarding/routing options in their firewall so it's easy to use like Firestarter. Than having a home server and good firewall would be really easy. 
Does anyone know are there such plans?

---

