---
title: "DNAT PREROUTING not working"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2008-04-15
I just set a firewall with iptables (I will atach my script if needed).
I have two eth cards (eth0 LAN, eth1 Internet)
When I use my ADSL-router with NAT, it works fine: the problem appears when I try to make DNAT PREROUTING with some services with iptables.
I am adding some rules:
The first is suposed to allow traffic for vncviewer:
```
sudo /sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5920 -j DNAT --to 192.168.103.160:5920
```
It doesn't work.
The second should allow incomming connections to an IBM AS-400:
```
sudo /sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 23 -j DNAT --to 192.168.103.20:23
sudo /sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 8470:8476 -j DNAT --to 192.168.103.20
sudo /sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 449 -j DNAT --to 192.168.103.20:449

```
There must me something missing in my knowlege...:(
Thanks in advanced!

---

### Post by SpaceTeddy on 2008-04-15
if you use adsl, a ppp0 device is created which overlays the eth1 link. You should change the -i flag in the rules from eth1 to ppp0.

otherwise, the commands look fine.

BUT, do you have allowed the traffic to pass through your FORWARD chain ? the DNAT only rewrites the pakets, you will still need to accept them in your filter table. If you could paste the fill script i could tell if they pass there or not :)

---

### Post by jmvidalvia on 2008-04-15
Of course I can paste it!
Meanwhile I added some changes, but it is not working yet.
I didn't apply your suggestion yet: I can't now because I need to restart some services and some people are now working ;)

(sorry comments are not in English)

```
#!/bin/sh

## FLUSH de reglas
/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -Z
/sbin/iptables -t nat -F

## Establecemos politica por defecto
/sbin/iptables -P INPUT ACCEPT
/sbin/iptables -P OUTPUT ACCEPT
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT

# Aceptamos las establecidas
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Nota: eth1 (ip 122) es el interfaz conectado al router y eth0 (ip 123) a la LAN

# El localhost se deja (por ejemplo conexiones locales a mysql)
/sbin/iptables -A INPUT -i lo -j ACCEPT

# Al firewall tenemos acceso desde la red local
/sbin/iptables -A INPUT -s 192.168.103.0/24 -i eth0 -j ACCEPT

# Redirecciones

# IBM as 400
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --sport 1024:65535 -d my.external.ip --dport 23 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --sport 1024:65535 -d my.external.ip --dport 8470:8476 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --sport 1024:65535 -d my.external.ip --dport 449 -j DNAT --to-destination 192.168.103.20

/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 --dport 23 -m state --state NEW -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 --dport 8470:8476 -m state --state NEW -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 --dport 449 -m state --state NEW -j ACCEPT

# Camara IP
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 1234 -j DNAT --to 192.168.103.154:1234

# Terminal server
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 3389 -j DNAT --to 192.168.103.100:3389

# vnc
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5920 -j DNAT --to 192.168.103.101:5920
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5921 -j DNAT --to 192.168.103.240:5921
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5922 -j DNAT --to 192.168.103.160:5922

# enviamos el puerto 80 al 3128 para el proxy squid
/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

# Aceptamos que vayan a puertos https
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp --dport 443 -j ACCEPT

# Aceptamos que consulten los DNS
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp --dport 53 -j ACCEPT
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp --dport 53 -j ACCEPT

# Aceptamos que salgan por ssh
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp --dport 2223 -j ACCEPT

# Aceptamos que consulten y envien correo
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp --dport 995 -j ACCEPT
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp --dport 465 -j ACCEPT

# Para el messenger
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp --dport 1863 -j ACCEPT
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp --dport 6901 -j ACCEPT
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp --dport 6891:6901 -j ACCEPT

# ftp
/sbin/iptables -A FORWARD -m state --state ESTABLISHED -j ACCEPT
/sbin/iptables -A FORWARD -p tcp -m tcp -m state --dport 21 --state NEW -j ACCEPT
/sbin/iptables -A FORWARD -p tcp -m tcp -m state --sport 20 --state RELATED -j ACCEPT
/sbin/iptables -A FORWARD -p tcp -m tcp -m state --dport 1024:65535 --sport 1024:65535 --state RELATED -j ACCEPT

# ping
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p icmp -j ACCEPT

# Para jabber
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp --dport 5222 -j ACCEPT

# Este es para vmware
/sbin/iptables -A INPUT -p tcp --dport 902:903 -j ACCEPT

# Y denegamos el resto. Si se necesita alguno, ya avisaran
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -j DROP

# Ahora hacemos enmascaramiento de la red local
# y activamos el BIT DE FORWARDING 
/sbin/iptables -t nat -A POSTROUTING -s 192.168.103.0/24 -o eth1 -j MASQUERADE

# Con esto permitimos hacer forward de paquetes en el firewall, o sea
# que otras máquinas puedan salir a traves del firewall.
echo 1 > /proc/sys/net/ipv4/ip_forward

#Aceptamos ssh
/sbin/iptables -A INPUT -p tcp --dport 2223 -j ACCEPT

# Cerramos el rango de puertos conocidos
/sbin/iptables -A INPUT -s 0.0.0.0/0 -i eth1 -p tcp --dport 1:1024 -j DROP
/sbin/iptables -A INPUT -s 0.0.0.0/0 -i eth1 -p udp --dport 1:1024 -j DROP

# Cerramos un puerto de gestión: webmin
/sbin/iptables -A INPUT -s 0.0.0.0/0 -i eth1 -p tcp --dport 10000 -j DROP

# Fin del script
```

Many thanks! :)

---

### Post by SpaceTeddy on 2008-04-15
ok... the scripts seems to be doing the essential stuff for forwarding the stuff. No flaws in it that would suppress the pakets or send them the wrong way... 

The essential bit is that your FORWARD table is on ACCEPT, while you never drop any paket commin IN - you just drop those going out. So the FORWARD should always accept the incomming pakets. My guess is still that you should use the ppp0 instead of the eth1 (that is, if you do have an adsl uplink)

[SIZE="4"][OFFTOPIC][/SIZE]
As a side note - your script is rather confusing... took me a while to understand what is going on. For example - why do you write rules to accept pakets, then drop the rest and leave the default policy on ACCEPT... this does not make much sense to me... but then, as long as it works nobody cares what it looks like :)

The basic rule with iptables (or any other paket filter) is that you use a default policy, and then only define exceptions to it. This either means you set your Default on ACCEPT, and only have DROP rules - or you set your default to DROP, and only have ACCEPT rules. I, personally, prefer the later.

Another thing i noticed is that you sometimes use stateful rules and sometimes not. This also makes no sense - since your Router would need to keep track of the connections, even tho you only sometimes use the information on them...  

Don't get me wrong, i admire anyone who is willing to put his stuff out there and get things to work. These are just suggestions on how to improve your script. If you don't mind i could try to reorder/rewrite some of your script of how i think it would do the same job consistently... But i will only do this if you want me to. If you only want your question answered, that also fine by me (and less work :) )

---

### Post by jmvidalvia on 2008-04-15
Of course I would like to!
Your help will be very very wellcome.
I already suposed my script was not good enought, but never hoped to get this kind of direct help.
I hope I will finally lean iptables, the same I could learn a little bit of networking, Samba, nfs, ssh, et etc to get my DIY-server working.
Thank you very much! :D

---

### Post by SpaceTeddy on 2008-04-15
ok, i don't know how much this will acctually resemble your network configuration, as i have no idea how much traffic accidentially passed through your router (with all the Defaults on ACCEPT, it could have been loads). Anyway, i tried to make it as close to your set as possible.

There are also a few questions in there that you might want to think about. This is still far from perfect, but i'd say it is a step into the right direction. If you have questions about a specific rule or how to do something, just ask.
Also, the full set should now be statefull... i hope that was desired... (i have made the major changes bold - or tried to)

> #!/bin/sh

## FLUSH de reglas
/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -Z
/sbin/iptables -t nat -F

## Establecemos politica por defecto
/sbin/iptables -P INPUT **DROP**
/sbin/iptables -P OUTPUT **DROP**
/sbin/iptables -P FORWARD **DROP**
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT

# Aceptamos las establecidas
# Acppet any connection that was already initiated. these rules do NOTHING by themselves.
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
**/sbin/iptables -A FORWARD -m state --state ESTABLISHED -j ACCEPT**

## Nota: eth1 (ip 122) es el interfaz conectado al router y eth0 (ip 123) a la LAN

# El localhost se deja (por ejemplo conexiones locales a mysql)
# localhost can talk to itself on anything. Also, talking on the loopback is stateless, as we do not need to track ourself
[B]/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -i lo -j ACCEPT[/B]

# Este es para vmware
# vmware connection can be done from the outside world ? this is desired ??? i would not allow this, instead open an ssh port and tunnel over it...
/sbin/iptables -A INPUT -p tcp --dport 902:903 -m state --state NEW -j ACCEPT

# Al firewall tenemos acceso desde la red local
# This Accepts all connections comming in from the local network to this machine. (this is the desired behaviour ?)
/sbin/iptables -A INPUT -s 192.168.103.0/24 -m state --state NEW -i eth0 -j ACCEPT

#Aceptamos ssh
/sbin/iptables -A INPUT -p tcp --dport 2223 -m state --state NEW -j ACCEPT

#this is a dummy rule. Since i do not know where your machine is allowed to send stuff to, this overwrites the default rule for DROP. You might want to figure out what your machine is acctually allowed to do and restrict it from there
**/sbin/iptables -A OUTPUT -m state --state NEW -j ACCEPT**

#####################
## transit traffic ##
#####################

#Allow rewritten paket for the AS400 to pass
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 23 -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 449 -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 8470:8476 -j ACCEPT

#Allow internal network hosts to use special services
#NOTE: there are essential ports missing here (for my taste), e.g.: ssh, smtp, imap, pop3. Also i would never allow the messengers :)
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp -m state NEW **-m multiport --dports 53,443,465,995,1863,2223,5222,6901** -j ACCEPT
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp -m state NEW --dport 6891:6901 -j ACCEPT

#i am never sure if this works... if DNS can be handeled stateful or not... i think it can, but this might need to be replaced with the two rules below
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp -m state NEW --dport 53 -j ACCEPT
# /sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp --dport 53 -j ACCEPT
# /sbin/iptables -A FORWARD -d 192.168.103.0/24 -o eth0 -p udp --sport 53 -j ACCEPT

# ftp Allow active and Passive FTP
/sbin/iptables -A FORWARD -p tcp -m tcp -m state **--dport 20,21** --state NEW -j ACCEPT
/sbin/iptables -A FORWARD -p tcp -m tcp -m state --dport 1024:65535 --sport 1024:65535 --state RELATED -j ACCEPT

# Load the Kernel modules for Active and Passive FTP Connection tracking
[B]modprobe ip_nat_ftp ports=21
modprobe ip_conntrack_ftp[/B]

# Allow icmp (ping) from internal to any network
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p icmp -j ACCEPT

# Ahora hacemos enmascaramiento de la red local
# y activamos el BIT DE FORWARDING 
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

###################
## Redirecciones ##
###################

# enviamos el puerto 80 al 3128 para el proxy squid
/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

# IBM as 400 (why restrict the source ports here ? is there a reason for it ?)
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --sport 1024:65535 -d my.external.ip --dport 23 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --sport 1024:65535 -d my.external.ip --dport 8470:8476 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --sport 1024:65535 -d my.external.ip --dport 449 -j DNAT --to-destination 192.168.103.20

# Camara IP
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 1234 -j DNAT --to 192.168.103.154:1234

# Terminal server
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 3389 -j DNAT --to 192.168.103.100:3389

# vnc
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5920 -j DNAT --to 192.168.103.101:5920
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5921 -j DNAT --to 192.168.103.240:5921
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5922 -j DNAT --to 192.168.103.160:5922

# Con esto permitimos hacer forward de paquetes en el firewall, o sea
# que otras máquinas puedan salir a traves del firewall.
echo 1 > /proc/sys/net/ipv4/ip_forward

# Fin del script

---

### Post by jmvidalvia on 2008-04-15
Dear SpaceTeddy:

You can not imagine how helfull you are! Thanks again.
I will try to ask or comment on your modified script:

> **SpaceTeddy said:**
> #!/bin/sh

## FLUSH de reglas
/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -Z
/sbin/iptables -t nat -F

## Establecemos politica por defecto
/sbin/iptables -P INPUT DROP
/sbin/iptables -P OUTPUT DROP
/sbin/iptables -P FORWARD DROP
[COLOR="Red"]-----------------------------ok, I change ACCEPT by DROP[/COLOR]
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT

# Aceptamos las establecidas
# Acppet any connection that was already initiated. these rules do NOTHING by themselves.
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A FORWARD -m state --state ESTABLISHED -j ACCEPT
[COLOR="Red"]---------------------------If they do nothing, should I leave them or remove?[/COLOR]

## Nota: eth1 (ip 122) es el interfaz conectado al router y eth0 (ip 123) a la LAN

# El localhost se deja (por ejemplo conexiones locales a mysql)
# localhost can talk to itself on anything. Also, talking on the loopback is stateless, as we do not need to track ourself
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -i lo -j ACCEPT
[COLOR="Red"]--------------------------So, should I remove these two rules?[/COLOR]


# Este es para vmware
# vmware connection can be done from the outside world ? this is desired ??? i would not allow this, instead open an ssh port and tunnel over it...
/sbin/iptables -A INPUT -p tcp --dport 902:903 -m state --state NEW -j ACCEPT
[COLOR="Red"]------------------------No, just from "inside": my mistake: I will remove it.[/COLOR]

# Al firewall tenemos acceso desde la red local
# This Accepts all connections comming in from the local network to this machine. (this is the desired behaviour ?)
/sbin/iptables -A INPUT -s 192.168.103.0/24 -m state --state NEW -i eth0 -j ACCEPT
[COLOR="Red"]---------------------------No, my second (at least) mistake: I thought this rule was necessary. I just need to allow ssh (port 2223 for me) from everywere and http just from inside. No mail server is running.
[/COLOR]
#Aceptamos ssh
/sbin/iptables -A INPUT -p tcp --dport 2223 -m state --state NEW -j ACCEPT

#this is a dummy rule. Since i do not know where your machine is allowed to send stuff to, this overwrites the default rule for DROP. You might want to figure out what your machine is acctually allowed to do and restrict it from there
/sbin/iptables -A OUTPUT -m state --state NEW -j ACCEPT
[COLOR="Red"]---------------------My machine sould only be allowed to send out of the LAN rsync connections and sending mails using the gmail relay.
[/COLOR]
#####################
## transit traffic ##
#####################

#Allow rewritten paket for the AS400 to pass
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 23 -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 449 -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 8470:8476 -j ACCEPT

#Allow internal network hosts to use special services
#NOTE: there are essential ports missing here (for my taste), e.g.: ssh, smtp, imap, pop3. Also i would never allow the messengers
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp -m state NEW -m multiport --dports 53,443,465,995,1863,2223,5222,6901 -j ACCEPT
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp -m state NEW --dport 6891:6901 -j ACCEPT
[COLOR="Red"]-----------------------ssh is included in port 2223, I have no mail server, just need to forward traffic comming from Outlook (ports 465 and 995). I need to allow messengers: we use it as a comunication system within our Company. Yes, I know it is awful, but we started with it in the begining of IM and got used to it. Need to think about a new system...[/COLOR]:)

#i am never sure if this works... if DNS can be handeled stateful or not... i think it can, but this might need to be replaced with the two rules below
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp -m state NEW --dport 53 -j ACCEPT
# /sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp --dport 53 -j ACCEPT
# /sbin/iptables -A FORWARD -d 192.168.103.0/24 -o eth0 -p udp --sport 53 -j ACCEPT
[COLOR="Red"]---------------I will remove my rule(s) and add yours then.[/COLOR]

# ftp Allow active and Passive FTP
/sbin/iptables -A FORWARD -p tcp -m tcp -m state --dport 20,21 --state NEW -j ACCEPT
/sbin/iptables -A FORWARD -p tcp -m tcp -m state --dport 1024:65535 --sport 1024:65535 --state RELATED -j ACCEPT

# Load the Kernel modules for Active and Passive FTP Connection tracking
modprobe ip_nat_ftp ports=21
modprobe ip_conntrack_ftp
[COLOR="Red"]----------------------------You don't forget anything! I already added these modules to /etc/modules
[/COLOR]

# Allow icmp (ping) from internal to any network
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p icmp -j ACCEPT

# Ahora hacemos enmascaramiento de la red local
# y activamos el BIT DE FORWARDING
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

###################
## Redirecciones ##
###################

# enviamos el puerto 80 al 3128 para el proxy squid
/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

# IBM as 400 (why restrict the source ports here ? is there a reason for it ?)
[COLOR="Red"]--------------------------No, there was no reason, just got it from a manual after trying "dozens" of wrong ways. I understand I must remove "--sport 1024:65535" [/COLOR]
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --sport 1024:65535 -d my.external.ip --dport 23 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --sport 1024:65535 -d my.external.ip --dport 8470:8476 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --sport 1024:65535 -d my.external.ip --dport 449 -j DNAT --to-destination 192.168.103.20

# Camara IP
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 1234 -j DNAT --to 192.168.103.154:1234

# Terminal server
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 3389 -j DNAT --to 192.168.103.100:3389

# vnc
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5920 -j DNAT --to 192.168.103.101:5920
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5921 -j DNAT --to 192.168.103.240:5921
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5922 -j DNAT --to 192.168.103.160:5922

# Con esto permitimos hacer forward de paquetes en el firewall, o sea
# que otras máquinas puedan salir a traves del firewall.
echo 1 > /proc/sys/net/ipv4/ip_forward

# Fin del script
[COLOR="Red"]-------------------------What about your suggestions about changing eth1 by pppo?[/COLOR]


Thank you very much again for your support!
Best regards, 

jm

---

### Post by SpaceTeddy on 2008-04-15
1.) ESTABLISHED RULES
these rules do not do anything by THEMSELVES ! that is the important bit - THEMSELVES. these rules are very important !
Any connection that gets ACCEPTED (anything rule that has the state NEW) will only accept the initiating paket from the connection. The kernel will put it into it's connection tracking table and hold it there. The Established rules allow any Connection that is in this very connection tracking table to pass. Without these rules, you will not be able to pass anything through the router. leave them in. 
However, with these no connection can be initiated... that's why i said they don't do anything by themselves... 

2.) Loopback
leave them in. These rules cannot be used in any way for anyone to get to the host (unless they already broke in). These two rules are only so that servers on the router can talk to other server via the loopback device

3.) VM-ware
Don't remove the line, refine it instead. For example, add the -i and -s flags to restrict it so that only internal host can connect to it. Otherwise, you won't be able to connect to the vmware server at all...

the whole INPUT/OUTPUT issue is rather difficult to understand at the start... there are a few services that one might not think of to be needed, but they are. For example, you will need dns resolving even if you never use it (activly). Also, you want your server to be able to use port 80  to get updates for the system. Furthermore, you want your server to allow connection on port 80 (outgoing) for the proxy, and 3128 (incomming) for the proxy.
Before you go into changeing these rules, make sure you KNOW which ports are definetly needed and allow them. Otherwise, you might cut off essential services. 
a good look at the output of *netstat -lnp -inet* can help, as this tells you which server are currently running and which ports you need to allow in what direction... (if in doubt, paste the output here or pm it to me)

4.) Ports in forwarding
It's ok if you don't need those ports ... i just wanted to make sure you knew that you are potentially essential for critical internet services. Also, the 2223 for ssh is nice, but "normal" ssh server run on 22, and your firewall does not allow that... maybe it is just me, since i basicially live in ssh sessions on remote servers... 

5.) source ports in Port forwarding
The source ports should not matter (much), as any non-root process on any machine cannot bind itself to any port below 1024 anyway. I was just surprised to see them, as they are not nessessary... and yes, just remove --sport 1024:65535

6.) the ppp device
Check if you have a ppp0 device when your router is connected. if so, replace all occurances of eth1 in the script by ppp0 and try again. I always have to use the ppp0 device on adsl uplinks... it's definetly worth a try...

---

### Post by jmvidalvia on 2008-04-15
Thank you very much: I will check everything tomorrow.
I prefer not to change the complete script from home with ssh: I can lose the connection.
Regarding ppp0, I've never seen this interface in my machines, all using adsl: ¿is there any other way to check it appart from sudo ifconfig?
Thanks again!

---

### Post by SpaceTeddy on 2008-04-15
if ifconfig does not show it, it does not exist. strikes me odd, but it can be... just try the new rules and see what happens. Maybe it really was a iptables problem...

as for another way to show it...
> sudo apt-get install iproute
ip link show

also shows all network cards, regardless of being configured, plugged in or running... it shows them all - allways

---

### Post by jmvidalvia on 2008-04-15
> **SpaceTeddy said:**
> if ifconfig does not show it, it does not exist. strikes me odd, but it can be... just try the new rules and see what happens. Maybe it really was a iptables problem...

as for another way to show it...


also shows all network cards, regardless of being configured, plugged in or running... it shows them all - allways

This is what I am getting:
```
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth1: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:17:3f:0a:ea:c4 brd ff:ff:ff:ff:ff:ff
3: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:50:8d:59:76:ba brd ff:ff:ff:ff:ff:ff
4: sit0: <NOARP> mtu 1480 qdisc noop 
    link/sit 0.0.0.0 brd 0.0.0.0

```
So definetly ppp0 seems not to be there.
One more question (today ;))
In loopback rules you added a copy/paste line:
```
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A INPUT -i lo -j ACCEPT
```
Should the second one be: '/sbin/iptables -A OUTPUT -o lo -j ACCEPT' ?
Many  thanks!

---

### Post by SpaceTeddy on 2008-04-15
yes, it should be OUTPUT on the second line, you're right. I must have mistyped that :)

also, on the router, can you give me the output of the following commands (just to be sure)
```
ls /etc/ppp/peers
cat /etc/network/interfaces
```

thanks

---

### Post by jmvidalvia on 2008-04-15
> **SpaceTeddy said:**
> yes, it should be OUTPUT on the second line, you're right. I must have mistyped that :)

also, on the router, can you give me the output of the following commands (just to be sure)
```
ls /etc/ppp/peers
cat /etc/network/interfaces
```

thanks

Sure!
```
jmd@server:~$ ls /etc/ppp/*
/etc/ppp/ip-down.d:
clamav-freshclam-ifupdown

/etc/ppp/ip-up.d:
clamav-freshclam-ifupdown  exim4

jmd@server:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

auto lo eth0 eth1

iface lo inet loopback

iface eth0 inet static
address 192.168.103.123
netmask 255.255.255.0
gateway 192.168.103.201
nameserver 80.58.0.33 194.179.1.100

iface eth1 inet static
address 192.168.103.122
netmask 255.255.255.0
gateway 192.168.103.201

jmd@server:~$ 

```
As you see, no /etc/ppp/peers...

Thanks!

---

### Post by SpaceTeddy on 2008-04-16
ok, good, it cannot be the ppp0 device then... must be the rules... sorry :(

---

### Post by jmvidalvia on 2008-04-16
Hi SpaceTeddy, 

Glad to see you again! :)
Some "silly" problems appeared this morning while trying the new script:
```
Bad argument `NEW'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `NEW'
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.6: invalid port/service `20,21' specified
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `d'
Try `iptables -h' or 'iptables --help' for more information.

```

I checked everything but couldn't find the mistake.
This is how it looks the "last version":
```
#!/bin/sh

## FLUSH de reglas
/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -Z
/sbin/iptables -t nat -F

## Establecemos politica por defecto
/sbin/iptables -P INPUT DROP
/sbin/iptables -P OUTPUT DROP
/sbin/iptables -P FORWARD DROP
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT

# Aceptamos las establecidas
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A FORWARD -m state --state ESTABLISHED -j ACCEPT

## Nota: eth1 (ip 122) es el interfaz conectado al router y eth0 (ip 123) a la LAN

# El localhost se deja (por ejemplo conexiones locales a mysql)
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A OUTPUT -o lo -j ACCEPT

# Este es para vmware
# restringirlo a red local
#/sbin/iptables -A INPUT -p tcp --dport 902:903 -m state --state NEW -j ACCEPT

# Al firewall tenemos acceso desde la red local
# This Accepts all connections comming in from the local network to this machine. (this is the desired behaviour ?)
# tengo que sustituir esto por los servicios que permito, como samba, dns o ftp.
/sbin/iptables -A INPUT -s 192.168.103.0/24 -m state --state NEW -i eth0 -j ACCEPT

#Aceptamos ssh
/sbin/iptables -A INPUT -p tcp --dport 2223 -m state --state NEW -j ACCEPT

#this is a dummy rule. Since i do not know where your machine is allowed to send stuff to, this overwrites the default rule for DROP. You might want to figure out what your machine is acctually allowed to do and restrict it from there
# tengo que sustituir esta linea por los output que voy a permitir, como 80, 53.
/sbin/iptables -A OUTPUT -m state --state NEW -j ACCEPT

#####################
## transit traffic ##
#####################

#Allow rewritten paket for the AS400 to pass
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 23 -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 449 -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 8470:8476 -j ACCEPT

#Allow internal network hosts to use special services
#NOTE: there are essential ports missing here (for my taste), e.g.: ssh, smtp, imap, pop3. Also i would never allow the messengers
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp -m state NEW -m multiport --dports 53,443,465,995,1863,2223,5222,6901 -j ACCEPT
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp -m state NEW --dport 6891:6901 -j ACCEPT

#i am never sure if this works... if DNS can be handeled stateful or not... i think it can, but this might need to be replaced with the two rules below
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp -m state --state NEW --dport 53 -j ACCEPT
# /sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp --dport 53 -j ACCEPT
# /sbin/iptables -A FORWARD -d 192.168.103.0/24 -o eth0 -p udp --sport 53 -j ACCEPT

# ftp Allow active and Passive FTP
/sbin/iptables -A FORWARD -p tcp -m tcp -m state --dport 20,21 -m state --state NEW -j ACCEPT
/sbin/iptables -A FORWARD -p tcp -m tcp -m state --dport 1024:65535 --sport 1024:65535 --state RELATED -j ACCEPT

# Load the Kernel modules for Active and Passive FTP Connection tracking
# ya cargados en /etc/modprobe
#modprobe ip_nat_ftp ports=21
#modprobe ip_conntrack_ftp

# Allow icmp (ping) from internal to any network
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p icmp -j ACCEPT

# Ahora hacemos enmascaramiento de la red local
# y activamos el BIT DE FORWARDING
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

###################
## Redirecciones ##
###################

# enviamos el puerto 80 al 3128 para el proxy squid
/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

# IBM as 400 
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp -d my.external.ip --dport 23 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp -d my.external.ip --dport 8470:8476 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp d my.external.ip --dport 449 -j DNAT --to-destination 192.168.103.20

# Camara IP
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 1234 -j DNAT --to 192.168.103.154:1234

# Terminal server
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 3389 -j DNAT --to 192.168.103.100:3389

# vnc
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5920 -j DNAT --to 192.168.103.101:5920
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5921 -j DNAT --to 192.168.103.240:5921
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5922 -j DNAT --to 192.168.103.160:5922

# Con esto permitimos hacer forward de paquetes en el firewall, o sea
# que otras maquinas puedan salir a traves del firewall.
echo 1 > /proc/sys/net/ipv4/ip_forward

# Fin del script

```

Thank you so much  :p

---

### Post by SpaceTeddy on 2008-04-16
> **jmvidalvia said:**
> Hi SpaceTeddy, 

Glad to see you again! :)
Some "silly" problems appeared this morning while trying the new script:

> #!/bin/sh

## FLUSH de reglas
/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -Z
/sbin/iptables -t nat -F

## Establecemos politica por defecto
/sbin/iptables -P INPUT DROP
/sbin/iptables -P OUTPUT DROP
/sbin/iptables -P FORWARD DROP
/sbin/iptables -t nat -P PREROUTING ACCEPT
/sbin/iptables -t nat -P POSTROUTING ACCEPT

# Aceptamos las establecidas
/sbin/iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A FORWARD -m state --state ESTABLISHED -j ACCEPT

## Nota: eth1 (ip 122) es el interfaz conectado al router y eth0 (ip 123) a la LAN

# El localhost se deja (por ejemplo conexiones locales a mysql)
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A OUTPUT -o lo -j ACCEPT

# Este es para vmware
# restringirlo a red local
#/sbin/iptables -A INPUT -p tcp --dport 902:903 -m state --state NEW -j ACCEPT

# Al firewall tenemos acceso desde la red local
# This Accepts all connections comming in from the local network to this machine. (this is the desired behaviour ?)
# tengo que sustituir esto por los servicios que permito, como samba, dns o ftp.
/sbin/iptables -A INPUT -s 192.168.103.0/24 -m state --state NEW -i eth0 -j ACCEPT

#Aceptamos ssh
/sbin/iptables -A INPUT -p tcp --dport 2223 -m state --state NEW -j ACCEPT

#this is a dummy rule. Since i do not know where your machine is allowed to send stuff to, this overwrites the default rule for DROP. You might want to figure out what your machine is acctually allowed to do and restrict it from there
# tengo que sustituir esta linea por los output que voy a permitir, como 80, 53.
/sbin/iptables -A OUTPUT -m state --state NEW -j ACCEPT

#####################
## transit traffic ##
#####################

#Allow rewritten paket for the AS400 to pass
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 23 -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 449 -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -d 192.168.103.20 -m state --state NEW --dport 8470:8476 -j ACCEPT

#Allow internal network hosts to use special services
#NOTE: there are essential ports missing here (for my taste), e.g.: ssh, smtp, imap, pop3. Also i would never allow the messengers
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp -m state **[COLOR="Red"]--state[/COLOR]** NEW -m multiport --dports 53,443,465,995,1863,2223,5222,6901 -j ACCEPT
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp -m state **[COLOR="Red"]--state[/COLOR]** NEW --dport 6891:6901 -j ACCEPT

#i am never sure if this works... if DNS can be handeled stateful or not... i think it can, but this might need to be replaced with the two rules below
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp -m state --state NEW --dport 53 -j ACCEPT
# /sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp --dport 53 -j ACCEPT
# /sbin/iptables -A FORWARD -d 192.168.103.0/24 -o eth0 -p udp --sport 53 -j ACCEPT

# ftp Allow active and Passive FTP
/sbin/iptables -A FORWARD -p tcp -m tcp -m state **[COLOR="Red"]-m multiport[/COLOR]** --dport**[COLOR="Red"]s[/COLOR]** 20,21 -m state --state NEW -j ACCEPT
/sbin/iptables -A FORWARD -p tcp -m tcp -m state --dport 1024:65535 --sport 1024:65535 --state RELATED -j ACCEPT

# Load the Kernel modules for Active and Passive FTP Connection tracking
# ya cargados en /etc/modprobe
#modprobe ip_nat_ftp ports=21
#modprobe ip_conntrack_ftp

# Allow icmp (ping) from internal to any network
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p icmp -j ACCEPT

# Ahora hacemos enmascaramiento de la red local
# y activamos el BIT DE FORWARDING
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

###################
## Redirecciones ##
###################

# enviamos el puerto 80 al 3128 para el proxy squid
/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

# IBM as 400 
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp -d my.external.ip --dport 23 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp -d my.external.ip --dport 8470:8476 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp **[COLOR="Red"]-[/COLOR]**d my.external.ip --dport 449 -j DNAT --to-destination 192.168.103.20

# Camara IP
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 1234 -j DNAT --to 192.168.103.154:1234

# Terminal server
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 3389 -j DNAT --to 192.168.103.100:3389

# vnc
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5920 -j DNAT --to 192.168.103.101:5920
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5921 -j DNAT --to 192.168.103.240:5921
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 5922 -j DNAT --to 192.168.103.160:5922

# Con esto permitimos hacer forward de paquetes en el firewall, o sea
# que otras maquinas puedan salir a traves del firewall.
echo 1 > /proc/sys/net/ipv4/ip_forward

# Fin del script


Thank you so much  :p
well, i do need sleep... sometimes :) marked the bits that are wrong in bold... it was mainly typos and forgetting of switches... i must have been really tired last night... 

check if it works now :)

---

### Post by jmvidalvia on 2008-04-16
:(
```
iptables v1.3.6: invalid port/service `20,21' specified
Try `iptables -h' or 'iptables --help' for more information.

```

Thanks a lot. :p

---

### Post by jmvidalvia on 2008-04-16
Sorry, sorry!
My fault, I did'nt see your ammend!
:oops:

---

### Post by SpaceTeddy on 2008-04-16
```
# ftp Allow active and Passive FTP
/sbin/iptables -A FORWARD -p tcp -m tcp -m multiport --dports 20,21 -m state --state NEW -j ACCEPT
/sbin/iptables -A FORWARD -p tcp -m tcp --dport 1024:65535 --sport 1024:65535 -m state --state RELATED -j ACCEPT

```

there was a flaw in there tho... the -m state was specified twice... and i could not run the command on my machine either... not it runs on mine tho :) (tested both commands as i was starting to doubt my spelling skills)

---

### Post by jmvidalvia on 2008-04-16
_Testing report ;)_

Regarding... ```
#I am never sure if this works... if DNS can be handeled stateful or not... i think it can, but this might need to be replaced with the two rules below
/sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp -m state --state NEW --dport 53 -j ACCEPT
# /sbin/iptables -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp --dport 53 -j ACCEPT
# /sbin/iptables -A FORWARD -d 192.168.103.0/24 -o eth0 -p udp --sport 53 -j ACCEPT
```
... DNS don't work.
I comment the first rule and uncomment the second and the third and DNS work again.

(to be continued):)

---

### Post by jmvidalvia on 2008-04-16
_Testing report -2_

Important things are working, (thanks again!) but..I couldn't connect from outside to my As-400 yet.
When I do NAT with my router (please, see atached image) everything works.
Just in case, a silly question: I NAT all ports from my router to the external card (ip 122, eth1). I assume I am doing it right, don't I? Remember my second ethernet card (for internal traffic) has ip 123 and connects to eth0.
As soon as I remove lines 7 to 9 from the router, connections to AS from outside don't work.
I also tried to connect with terminal server and also couldn't.
Same for vnc.

It seems that there's something related with PREROUTING not working...but I am afraid I can not wonder what alone :(
Thanks a lot.

PS: Next step will be finding out which rules apply from inside (eth0) to server, and from server to outside (eth1), instead of leaving them both ACCEPT, as you suggested previously, but I will leave you breath first a litlle bit ;-)

---

### Post by SpaceTeddy on 2008-04-16
air is overrated - who needs breathing anyway :)

back to the topic at hand... the rules definety match the ip and port description. They do the same as the ones in your router. But, without more information this is getting hard to figure why these rules do not work. There are several ways to figure this - but all involve looking at paket dumps :(

The easiest way to see if the rules are even accepted, would be to apply the rules, then test the connection (even if you know they don't work) and then look if any pakets acctually matched them - you can do that with
```
iptables -L -vnx --table nat
```

the output shoult look like this:

> Chain PREROUTING (policy ACCEPT 4 packets, 1272 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       [COLOR="Red"]0        0[/COLOR] DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpts:8470:8476 to:192.168.103.20 
       [COLOR="Red"]0        0[/COLOR] DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:23 to:192.168.103.20 
       [COLOR="Red"]0        0 [/COLOR]DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:449 to:192.168.103.20 


the red bits are the important ones. If they remain at 0 after the connection attempt, the rules did not catch the pakets - which means they are too restrictive or have wrong paramters set... 

also, could you draw me a picture of your network layout... just so i know how the physical layout works (can send it via pm to me if you do not want it to show in the forum)

thanks

---

### Post by jmvidalvia on 2008-04-16
Hi again...
Just in case you didn't see the my editing of the previous post, I repeat the question:
*Just in case, a silly question: I NAT all ports from my router to the external card (ip 122, eth1). I assume I am doing it right, don't I? Remember my second ethernet card (for internal traffic) has ip 123 and connects to eth0.*
I will work on what you suggest.
Many thanks!

---

### Post by jmvidalvia on 2008-04-16
Sorry again:

Is there any easy way to make tests of DNAT wihtout the need to use the real services.
I mean, every time I need to try the connection I must change the router configuration, logout from my net, connect 3G mobile to my laptop, test, change the router again, etc..:-P
¿couldn't I simply add a new rule to iptables with a new port, connect from work to my home server through ssh, and send from there the tcp packets to my.external.ip: port?
If yes, How can I send packets? I understand ping is not tcp...
Thanks again!

---

### Post by SpaceTeddy on 2008-04-16
of course you can... the thing, you need to understand what you are doing in order to do this... and building the whole test setup itself can go pretty wrong :)

the easiest way is to log yourself in at home with a console (ssh preferibly) and then just telnet into the ports that you want to test... i.e. if you want to test port 23, you would do

```
telnet example.host.com 23
```

this will establish a tcp connection to port 23 on the host example.host.com. The session will most likely crash, but if it does connect, you have at least survided the tcp connection establishment, which already uses all rules you need for a real connection. The point is here that while you are in a terminal session at home, you acctually utilize that shell to connect back to yourself from an external ip... that makes sense... i believe.

of course you can do that with any other port aswell - just change the 23 into whatever port you want to test... 

was that understandable... :)

---

### Post by jmvidalvia on 2008-04-16
Hi again!
Is there any limit for your patience? ;)
I tried with telnet from home to work using port 3389: no signal, no packets.
I tried from another location with a terminal server client,same port 3389: no signal and no packets :(
```
iptables -L -vnx --table nat
Chain PREROUTING (policy ACCEPT 245 packets, 21732 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
     163     9372 REDIRECT   tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 redir ports 3128 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            217.126.73.79       tcp dpt:23 to:192.168.103.20 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            217.126.73.79       tcp dpts:8470:8476 to:192.168.103.20 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            217.126.73.79       tcp dpt:449 to:192.168.103.20 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:1234 to:192.168.103.154:1234 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:3389 to:192.168.103.100:3389 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:5920 to:192.168.103.101:5920 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:5921 to:192.168.103.240:5921 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:5922 to:192.168.103.160:5922 

Chain POSTROUTING (policy ACCEPT 5 packets, 754 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
     272    16374 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 440474 packets, 31750449 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

```
Does it mean there are no packets going into the server, so the problem might be in the router? Perhaps packets are not redirected as they "don't come in"?
:confused:
Thanks^2

jm

By the way: how often are iptables statistics clean? I realize they are reset every X minutes...

---

### Post by SpaceTeddy on 2008-04-16
> **jmvidalvia said:**
> Hi again!
Is there any limit for your patience? ;)

do you want me to stop replying ;) ? would save me time. But on the other hand, i help people because i want to help - and as far as i can tell you still have the same problem... so i will go on.

> **jmvidalvia said:**
> 
I tried with telnet from home to work using port 3389: no signal, no packets.
I tried from another location with a terminal server client,same port 3389: no signal and no packets :(
```
iptables -L -vnx --table nat
Chain PREROUTING (policy ACCEPT 245 packets, 21732 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
     163     9372 REDIRECT   tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 redir ports 3128 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            217.126.73.79       tcp dpt:23 to:192.168.103.20 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            217.126.73.79       tcp dpts:8470:8476 to:192.168.103.20 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            217.126.73.79       tcp dpt:449 to:192.168.103.20 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:1234 to:192.168.103.154:1234 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:3389 to:192.168.103.100:3389 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:5920 to:192.168.103.101:5920 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:5921 to:192.168.103.240:5921 
       0        0 DNAT       tcp  --  eth1   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:5922 to:192.168.103.160:5922 

Chain POSTROUTING (policy ACCEPT 5 packets, 754 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
     272    16374 MASQUERADE  0    --  *      eth1    0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 440474 packets, 31750449 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

```
Does it mean there are no packets going into the server, so the problem might be in the router? Perhaps packets are not redirected as they "don't come in"?

that i do not understand... i thought the router is between you and the internet. can you PLEASE draw me a picture of what your layout looks like. I have the suspicion i have a different setup in my head than you in your office... 
Otherwise, if there is no paket showing in the rule, it means that the rule did not rewrite any pakets... i am a bit reluctant to start explainig on how to use tcpdump... but you might have to work with that to acctually debug the pakets :( We'll leave that as a last resort, tho.
> **jmvidalvia said:**
> By the way: how often are iptables statistics clean? I realize they are reset every X minutes...
iptables does not reset it's paket count ever. It only get reset if a rule is deleted, a chain is flushed or a specific command for deleteing the paket count it given. Otherwise - nothing is done to the paket counts... as far as i know..

i'm waiting for the picture :)

---

### Post by jmvidalvia on 2008-04-16
Dear SpaceTeddy

I have been doing some "homework" for you.
First, my drawing. Flease, find it atached. I am a little bit ashamed: the network has a nasty design. But, you know, a switch brakes, can't find a big one, buy two small, or just a hub, etc. Fortunately, I am not the IT manager...:P
As you will see, the linux server is not in the right position: logical order would be (as far as I know) Internet >> Router>> Firewall(server)>>Switch>>PC's.
IT man has the reordering of everything in the "to do list" :( He told me again and again it doesn't matter if the Linux firewall is "in the middle of the LAN" or wherever, as it is nowadays...it should work anyhow (¿?).

My second duty: I did a little bit of research.
I Installed Wireshark and start listening the LAN while trying to connect thought port 3389 from the outer IP XXX.XXX.XXX.XXX. Only my firewall was trying to redirect those packets, as the rule had already been removed from the ADSL router.
Well.
First test: scanning only eth0:3389. Here is what I get:
```
No.     Time        Source                Destination           Protocol Info
   1582 0.345927    xxx.xxx.xxx.xxx          192.168.103.122       TCP      37787 > 3389 [SYN] Seq=0 Len=0 MSS=1400

Frame 1582 (62 bytes on wire, 62 bytes captured)
Ethernet II, Src: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd), Dst: AbitComp_59:76:ba (00:50:8d:59:76:ba)
Internet Protocol, Src: xxx.xxx.xxx.xxx, Dst: 192.168.103.122 (192.168.103.122)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
    Total Length: 48
    Identification: 0x01bd (445)
    Flags: 0x04 (Don't Fragment)
    Fragment offset: 0
    Time to live: 123
    Protocol: TCP (0x06)
    Header checksum: 0x6d6b [correct]
    Source: xxx.xxx.xxx.xxx
    Destination: 192.168.103.122 (192.168.103.122)
Transmission Control Protocol, Src Port: 37787 (37787), Dst Port: 3389 (3389), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
  16235 3.300065    xxx.xxx.xxx.xxx          192.168.103.122       TCP      37787 > 3389 [SYN] Seq=0 Len=0 MSS=1400

Frame 16235 (62 bytes on wire, 62 bytes captured)
Ethernet II, Src: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd), Dst: AbitComp_59:76:ba (00:50:8d:59:76:ba)
Internet Protocol, Src: xxx.xxx.xxx.xxx, Dst: 192.168.103.122 (192.168.103.122)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
    Total Length: 48
    Identification: 0x026d (621)
    Flags: 0x04 (Don't Fragment)
    Fragment offset: 0
    Time to live: 123
    Protocol: TCP (0x06)
    Header checksum: 0x6cbb [correct]
    Source: xxx.xxx.xxx.xxx
    Destination: 192.168.103.122 (192.168.103.122)
Transmission Control Protocol, Src Port: 37787 (37787), Dst Port: 3389 (3389), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
  44712 9.233241    xxx.xxx.xxx.xxx          192.168.103.122       TCP      37787 > 3389 [SYN] Seq=0 Len=0 MSS=1400

Frame 44712 (62 bytes on wire, 62 bytes captured)
Ethernet II, Src: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd), Dst: AbitComp_59:76:ba (00:50:8d:59:76:ba)
Internet Protocol, Src: xxx.xxx.xxx.xxx, Dst: 192.168.103.122 (192.168.103.122)
    Version: 4
    Header length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00)
    Total Length: 48
    Identification: 0x04b3 (1203)
    Flags: 0x04 (Don't Fragment)
    Fragment offset: 0
    Time to live: 123
    Protocol: TCP (0x06)
    Header checksum: 0x6a75 [correct]
    Source: xxx.xxx.xxx.xxx
    Destination: 192.168.103.122 (192.168.103.122)
Transmission Control Protocol, Src Port: 37787 (37787), Dst Port: 3389 (3389), Seq: 0, Len: 0
```
As far as I can understand, packets from outside going to IP 122. I am not sure it is right, as IP 122 was suposed to be assigned to eth1, not eth0, the one I am scanning first. :confused:

Second test: scanning eth1:3389. ¿what I get?
```
------
```

Right! Nothing, no packets. Wasn't they suposed to be comming form outside to IP 122 in eth1?

Ok, I think: isn't the sniffer running behind the firewall? that's why packets don't arrive to it. Then I add a temporary new rule accepting incoming packets within this port, and test again.
Here are the results:
```
No.     Time        Source                Destination           Protocol Info
      8 1.388043    192.168.103.122       xxx.xxx.xxx.xxx          TCP      3389 > 37932 [RST, ACK] Seq=0 Ack=0 Win=0 Len=0

Frame 8 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Belkin_0a:ea:c4 (00:17:3f:0a:ea:c4), Dst: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd)
Internet Protocol, Src: 192.168.103.122 (192.168.103.122), Dst: xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)
Transmission Control Protocol, Src Port: 3389 (3389), Dst Port: 37932 (37932), Seq: 0, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
     14 1.948498    192.168.103.122       xxx.xxx.xxx.xxx          TCP      3389 > 37932 [RST, ACK] Seq=0 Ack=0 Win=0 Len=0

Frame 14 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Belkin_0a:ea:c4 (00:17:3f:0a:ea:c4), Dst: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd)
Internet Protocol, Src: 192.168.103.122 (192.168.103.122), Dst: xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)
Transmission Control Protocol, Src Port: 3389 (3389), Dst Port: 37932 (37932), Seq: 0, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
     25 2.450292    192.168.103.122       xxx.xxx.xxx.xxx          TCP      3389 > 37932 [RST, ACK] Seq=0 Ack=0 Win=0 Len=0

Frame 25 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Belkin_0a:ea:c4 (00:17:3f:0a:ea:c4), Dst: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd)
Internet Protocol, Src: 192.168.103.122 (192.168.103.122), Dst: xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)
Transmission Control Protocol, Src Port: 3389 (3389), Dst Port: 37932 (37932), Seq: 0, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
    190 7.236531    192.168.103.122       xxx.xxx.xxx.xxx          TCP      3389 > 37937 [RST, ACK] Seq=0 Ack=0 Win=0 Len=0

Frame 190 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Belkin_0a:ea:c4 (00:17:3f:0a:ea:c4), Dst: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd)
Internet Protocol, Src: 192.168.103.122 (192.168.103.122), Dst: xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)
Transmission Control Protocol, Src Port: 3389 (3389), Dst Port: 37937 (37937), Seq: 0, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
    241 7.883243    192.168.103.122       xxx.xxx.xxx.xxx          TCP      3389 > 37937 [RST, ACK] Seq=0 Ack=0 Win=0 Len=0

Frame 241 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Belkin_0a:ea:c4 (00:17:3f:0a:ea:c4), Dst: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd)
Internet Protocol, Src: 192.168.103.122 (192.168.103.122), Dst: xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)
Transmission Control Protocol, Src Port: 3389 (3389), Dst Port: 37937 (37937), Seq: 0, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
    258 8.389910    192.168.103.122       xxx.xxx.xxx.xxx          TCP      3389 > 37937 [RST, ACK] Seq=0 Ack=0 Win=0 Len=0

Frame 258 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Belkin_0a:ea:c4 (00:17:3f:0a:ea:c4), Dst: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd)
Internet Protocol, Src: 192.168.103.122 (192.168.103.122), Dst: xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)
Transmission Control Protocol, Src Port: 3389 (3389), Dst Port: 37937 (37937), Seq: 0, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
    375 12.976674   192.168.103.122       xxx.xxx.xxx.xxx          TCP      3389 > 37938 [RST, ACK] Seq=0 Ack=0 Win=0 Len=0

Frame 375 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Belkin_0a:ea:c4 (00:17:3f:0a:ea:c4), Dst: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd)
Internet Protocol, Src: 192.168.103.122 (192.168.103.122), Dst: xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)
Transmission Control Protocol, Src Port: 3389 (3389), Dst Port: 37938 (37938), Seq: 0, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
    386 13.616151   192.168.103.122       xxx.xxx.xxx.xxx          TCP      3389 > 37938 [RST, ACK] Seq=0 Ack=0 Win=0 Len=0

Frame 386 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Belkin_0a:ea:c4 (00:17:3f:0a:ea:c4), Dst: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd)
Internet Protocol, Src: 192.168.103.122 (192.168.103.122), Dst: xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)
Transmission Control Protocol, Src Port: 3389 (3389), Dst Port: 37938 (37938), Seq: 0, Ack: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
    392 14.130691   192.168.103.122       xxx.xxx.xxx.xxx          TCP      3389 > 37938 [RST, ACK] Seq=0 Ack=0 Win=0 Len=0

Frame 392 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Belkin_0a:ea:c4 (00:17:3f:0a:ea:c4), Dst: ZyxelCom_29:c5:fd (00:13:49:29:c5:fd)
Internet Protocol, Src: 192.168.103.122 (192.168.103.122), Dst: xxx.xxx.xxx.xxx (xxx.xxx.xxx.xxx)
Transmission Control Protocol, Src Port: 3389 (3389), Dst Port: 37938 (37938), Seq: 0, Ack: 0, Len: 0
```
And here I get totally confused: packets from my eth1 card, IP 122 going outside (¿?)

I suspect all of this won't be usefull for anything: this is the only idea I had trying to help you.
Can't imagine how I can return so much help to you...
Thanks^3

---

### Post by SpaceTeddy on 2008-04-17
The Picture first... 

mhm... ok. Maybe i overlooked this earlier, but this setup cannot work (at least as far as i understand networks). Your linux server has two nics on the same subnet. Now, physicially, that is not a problem, you can have multiple Network cards attached to the same switch, but what you can not have is two network cards within the same IP subnet. Any paket your server wants to send out - what interface does it choose ? both are connected to the same subnet. Your linux box has exactly the same configuration (apart from the ip) on your nics. so it either sends on random (which is not going to happen) or it is bound to get confused as it cannot decide which interface to use. 

To overcome this problem, there are two ways to go. If you cannot change the physical layout of your network (i.e. rewire it) you will need to segment to make this work. This will be option A. Option B will go into plugging cables (acctually, i think you just have to replug one and remove another. This will also need reconfiguration of your IP's, but it is... lets say cleaner and eaiser to understand.

Either way, you will have to reconfigure your network so that the ip segment between the  ADSL router and Linux box has a different IP-range than the one between the Linux router and the Servers. If that is no option, you will need to configure your linux box to be a transparent firewall. But that would involve a setup like shown in Option B.

As far as i know networks, you current setup cannot work...

Why does it not work ? well, by the looks of it, your ADSL router does the DNAT. your linux box only forwards traffic (however that works with two nics on the same subnet). As soon as you take out the port forwarding from your ADSL router, the pakets don't even reach your internal network. Unless you remove it... Or is there to this setup that i do not know about ?

Also, how does your proxy work. I saw the rule for a transparent proxy in your Rules - does that mean your machines use the 192.168.103.122 as a gateway, which then will use the adsl router as a gateway ? i am confused... still... 

as for the scanning - i think as long as your have the multple nics on one subnet, it is pointless to scan. The paket flow itself is already pretty wicked... i'll attach a picture of how i would change the lan (with minimal effect on everything so that this could work... 
( by the way , why do you still use the adsl router if you have a linux box ? wouldn't be easier to replace the adsl router with the linux box ? )

so long...

PS: Option C is what i thought your network looks like... As you can see, i don't care about clients, i just want to know how to pakets flow... 

PPS: The red Arrow in Option A is the paket flow as i would direct them. Or how i think they should flow through your network - it's kinda ugly that they pass the adsl router twice...

---

### Post by jmvidalvia on 2008-04-17
:oops::oops::oops:
So clear now!
This is an example of trying to build rockets without understanding why rocks fall and birds fly...
Yes, your nice drawings are totally understandable.
What is funny is that I was waiting to rewire the net (your option B) till the redirecting of packets work, what would have never happened till I change the configuration of my LAN (your option A).
What I am going to do now is:

I will change the adsl router IP from 192.168.103.1 to 192.168.102.1.
I will change the default gateway IP in /etc/network/interfaces 
I will change the eth1 ethernet card of my Linux from 192.168.103.122 to 192.168.102.2 in /etc/network/interfaces.
I will change in my iptables script all 192.168.103.122 by 192.168.102.2

I assume this should be enough for now, shouldn't it?
Afterwards, (after testing it for a couple of days) I will proceed with your option B and C.

Although I read quite a lot about networks (I promise :)), it is real life that puts everyone in his own place, but it is the only way of learning.
By the way, I ever didn't think about removing my adsl router, but I is an idea I really like. As dhcp is already provided by the WIN server (soon by my Linux box ;-)) I supose it won't be difficult (removing adsl I mean). Any Idea about where I can read something about it before just asking you? I assume it is not just plug&play...

I finished the different ways of saying thank you, so I start again:
Thank you very much!

---

### Post by SpaceTeddy on 2008-04-17
> **jmvidalvia said:**
> I will change the adsl router IP from 192.168.103.1 to 192.168.102.1.
I will change the default gateway IP in /etc/network/interfaces 
I will change the eth1 ethernet card of my Linux from 192.168.103.122 to 192.168.102.2 in /etc/network/interfaces.
I will change in my iptables script all 192.168.103.122 by 192.168.102.2

first off, i must warn you that you can possibly break your itnernet connection with that - but i really admire your spirit :)
ok, that said, there are a few more things to think about - or so think. 
1.) make sure that all clients on your network (the servers and the users) ALL know the new default gateway (which, in your case, would be 192.168.103.123) and have a proper dns entry (since your adsl router changed it's ip, you might have to change the clients or dhcp-server too)
2.) make sure that a dns server can still be reached.
3.) any forwarding you have setup in your adsl router must be changed to always forward to 192.168.102.2. that will make sure that everyting reaches the linux server. Then you can use the DNAT on that server to forward it further (this is not the best solution, but it should work)

if anything fails - first check if the linux box has full internet connectivity. (if in doubt, change the DROP from the default policies in your iptables script to ACCEPT to make sure that nothing is blocked for the tests). 
Once you are certain that the linux box has full connectivity, debug the clients. But you probably know that already... 
> **jmvidalvia said:**
> I assume this should be enough for now, shouldn't it?
Afterwards, (after testing it for a couple of days) I will proceed with your option B and C.

Although I read quite a lot about networks (I promise :)), it is real life that puts everyone in his own place, but it is the only way of learning.
By the way, I ever didn't think about removing my adsl router, but I is an idea I really like. As dhcp is already provided by the WIN server (soon by my Linux box ;-)) I supose it won't be difficult (removing adsl I mean). Any Idea about where I can read something about it before just asking you? I assume it is not just plug&play...
acctually, if you have an adsl modem, it is quite simple to setup (you can probably degreade your router to just act as modem) on the linux side... 
install the adsl connection programm with this command
```
sudo apt-get install pppoeconf
```

and then configure it using this command
```
sudo pppoeconf
```

which will run you through a console based set of question and configures everything. btw. if you do this you will end up with a ppp0 device which overlays eth0. Which brings us back to my first thought what your problem might be...  :)

hope you get it working.

PS: i usually stay with a thread on subscription for seven days and then delete the subscription. If you take longer, simply send me a pm.

---

### Post by jmvidalvia on 2008-04-17
Dear Space Teddy, 

Thanks again for your last comments.
I changed the IP's configuration, create a second subnet for the router and one ethernet card, remove NAT from router, adjust everything.
My Linux box had Internet, I connected from home with ssh, XP's boxes could navigate, dns worked, etc. Everything was fine...except prerouting.
The strange thing is that just ONE (one of the vncviewer) of the redirecting rules was working.
My idea now is that there's something in my LAN that allows to get connections between some machines, but not some others. No idea!
As I don't want to bother you any more, I will rewire the LAN, put all together in two switches (not four), etc. and test it again.
Then, if you don't mind, I will come to you later, with some conclusions.
I just can say you thank your very much once again, and sorry for having this not-easy-to-solve post...
Another solution is that you come to Barcelona...;-)
You shall hear form me soon!
Thanks again! :D

---

### Post by SpaceTeddy on 2008-04-17
[/QUOTE]> **jmvidalvia said:**
> remove NAT from router
This was probably not a very good idea. How do i explain this... mhm... this is about paket flow and directing addresses... The pakets from your internal network will leave your network as planned, since every client knows that their default gateway is now the linux box at 192.168.103.123. Also, the linux box knows that the default gateway is 192,168.102.1, so the pakets will flow back there too. What happens after the adsl route shall not concern us right now. 
Anyways, there is an answer comming back, which will eventually reach your adsl router. So the router is not stuck with a paket direct at a 192.168.103.x address, but does not know where to find that address. So the answer will never reach the sender... 
If you leave the nat in, this should not be a problem... and i think this is also the cause for your problems and the strange behavoir of the pakets... i guess... maybe :)
> **jmvidalvia said:**
> sorry for having this not-easy-to-solve post... 
i know that when i answer a post it coul be easy to solve, or it could be a challenge. I like challenges, an i really don't mind answering posts. If i meet people who want to learn, i am happy to help them - always ! so don't worry about it.
> **jmvidalvia said:**
> Another solution is that you come to Barcelona...;-)
mhm.. quite tempting :) it's bee raining here for about a week straight, and i can't remember how often i have gotten home totally soaked and frozen... :(

---

### Post by jmvidalvia on 2008-04-17
> This was probably not a very good idea. How do i explain this... mhm... this is about paket flow and directing addresses... The pakets from your internal network will leave your network as planned, since every client knows that their default gateway is now the linux box at 192.168.103.123. Also, the linux box knows that the default gateway is 192,168.102.1, so the pakets will flow back there too. What happens after the adsl route shall not concern us right now. 
Anyways, there is an answer comming back, which will eventually reach your adsl router. So the router is not stuck with a paket direct at a 192.168.103.x address, 

Interesting point!
As I am not sure about what you mean about NAT (all packets from all ports or just some ports), I atach a png whith what I did.
I also atach a ods, in order to save your time in case you prefer to write something directly on my file...

We will solve it!!
Milion thanks!

[COLOR="Red"]Please, refer to next post for attached files. These ones are wrong but I can not remove them.[/COLOR]

---

### Post by jmvidalvia on 2008-04-17
Here the right ones.
Sorry.

---

### Post by jmvidalvia on 2008-04-17
Remember me? :D

I have been thinking :-k

With so many code lines (for a newbie like me) it is difficult to understand what is happening. Lets take just port 23 (one of the As400 ports) and see which rules are applied (appart from general rules). This is what I find:
```
/sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 23 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -m state --state NEW --dport 23 -j ACCEPT
```
First rule is sending tcp packets comming from eth1 with destination port 23 to machine 192.168.103.20. Ok.
Second rule allows to forward all new connections with tcp packets coming from eth1 and going to eth0, with source port > 1024 and destinatin port 23.
Ok, this is also understandable for me. 
But...what about the way back to outside?
Shouldn't we add a rule like:
```
/sbin/iptables -A FORWARD -i eth0 -o eth1 -p tcp --sport 23 -j ACCEPT
``` or similar?

Last tests of connections from outside died due to timeout. Connections were not rejected, just seem to die waiting for the answer...
Thank you so much.

---

### Post by SpaceTeddy on 2008-04-18
> **jmvidalvia said:**
> Second rule allows to forward all new connections with tcp packets coming from eth1 and going to eth0, with source port > 1024 and destinatin port 23.
Ok, this is also understandable for me. 
But...what about the way back to outside?

to explain this i will need to take show detour in how tcp connections work... and this is not twhat i think is the problem :)

To answer that question, let me first quote myself from 
[this]("http://ubuntuforums.org/showpost.php?p=4722953&postcount=8") post
> 1.) ESTABLISHED RULES
these rules do not do anything by THEMSELVES ! that is the important bit - THEMSELVES. these rules are very important !
Any connection that gets ACCEPTED (anything rule that has the state NEW) will only accept the initiating paket from the connection. The kernel will put it into it's connection tracking table and hold it there. The Established rules allow any Connection that is in this very connection tracking table to pass. Without these rules, you will not be able to pass anything through the router. leave them in.
However, with these no connection can be initiated... that's why i said they don't do anything by themselves...

Now, as you might have figured by now, this is all about the ESTABLISHED rules - or rather, this is all about statefull paket filtering. 
And now i'll stop being a smarty and explain what happens.

Lets say a new connection comes in. This connection goes exactly the way we want it to, so it is caught by the rule you specified, namely those:
> sbin/iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 23 -j DNAT --to-destination 192.168.103.20
/sbin/iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -m state --state NEW --dport 23 -j ACCEPT
As you said correctly, the first one will rewrite the paket, and the second will let it pass. But there is more happening here. This will not only let the paket simply pass, but also make an entry in your kernel remebering that a NEW connection was initiated. You will never acctually see that happen, but your router will now remember for the net 60 (?) seconds that a connection attempt was done. As tcp handshake (connection establishment) exchanged four pakets we don't need any data to see how the rule works. The server that now receives the paket (lets call it SYN) will see it (as it passed the firewall) and reply to it to initiate the connection. This will resolve in a paket going the other way (let's call that one SYN,ACK). The names are not chosen randomly, but by the flags set in the TCP paket. Since the answer as the SYN and the ACK set, it will NOT be caught by the NEW rule. But now this rule comes into play
> /sbin/iptables -A FORWARD -m state --state ESTABLISHED -j ACCEPT
as it stated that any connection that is established can pass. This means two things have to match.
1.) The paket has to have the ACK flag set 
2.) there must be an entry in the kernel connection table to match it to an existing connection.

condition 1 is easily satisfied (the ACK is set), and condition 2 also matches since the entry was created when the SYN paket passed. Hence, your paket can go through the firewall again, even if you never specified that it can pass. 

what i've really wanted to say is that you don't need a rule to pass the pakets back, but just a generic one that accepts established connections.

Now, your graphics... i am not quite sure that i understand them, but i can explain how i think the pakets should be rewritten and flow through your network so that it works...
But before, we have to take a shor detour again, this time into how routing works. I have no idea on how detailed your knowledge about that is, so i'll just explain it :)
i'll explain it with an outgoing connection tho - i'll take the imaginary host 192.168.103.254 (called S) which wants to connect to the internet, lets say the host 209.85.129.99 (called D). What happens ?

A will create a paket with the source address of 192.168.103.254 and the destination 209.85.129.99. then it will be haneded to the routing to figure out where that IP address is. Routing always works on the "best match" rule. i.e. your computer has information where to send pakets with which destination address. But since A is at the very end of the connection, it does not know much about the internet, and since the IP is clearly not in it's local lan, it does the only thing it can - it send it to the default gateway. This is the only way A knows how to contact the internet. The Default Gateway is your Linux box (called it L). L sees the paket and again trys to find the match for it in it's routing table. Again, there is no route, so the default route it chosen. By chooseing the default route this paket becomes a transit paket and will not pass through your iptables filter. What happens there we will ignore for now. 
To little paket now has left L towards the next default gateway - this will be your ADSL router (call it R). Again R will look at the paket, will figure out it has no route for it, and again will send it towards it's efault gateway. But before it does that, MASQUERADE will take place. The paket has not been rewritten yet, and still has the source of 192.168.103.254. But that address does not exist in the interent ! nobody in the internet knows that one. So the router replaces the 192.168.103.254 with it's own address and remember the connection to be able to match incomming pakets against it. This is neccessary since the answer that will come back will be directed at the router and NOT the host behind it. In order for this to work properly, the router will need to be able to figure out that this was a masqueraded paket to be able to forward it back to the orginal host.
Ok, your paket now has the destination of 209.85.129.99 and the source of your router, let's call it x.x.x.x (NOT 192.168.103.254 anymore !!!).

now the thing goes through the internet, reaches google (which is this ip 209.85.129.99) and google replies. The reply will now have source and destination swapped (as the reply is going to other way). this means that the source is now 209.85.129.99 and the destination is x.x.x.x (your router).
We'll just assume the internet works correct and the answer will eventually reach your router. Now, the router is clever and detects that this is a reply to a masquareaded paket, looks up in it's internal table what ip from where the initial connection came, changed the DESTINATION to 192.168.103.254, which is the proper destination (as this was the source where the paket initially came from). Once rewritten it will look up in it's routing table the best match for that address.
And this is where it runs into a problem. The router has NO IDEA where that destination might be. It is only attached to your ISP and the 192.168.102.254 network. There is no 192.168.103.x network nowhere to be found in it's routing table ! so it does exactly what the routing algorithm states - it sends it towards the best match. But the best match in this case is the default gateway. So the paket is sent back OUT into the internet instead of into your internal lan. it will now bounce a few times between your router and your ISP until it times out and it dropped. But it never reaches the originator of the paket... 

do you see the problem (and do you understand what i am trying to explain here )?

To overcome this problem, there are two solutions:
1.) tell R where the network is (i.e. set a route for it)
2.) eliminate the NEED for R to know about the network 

of course, option 1 is the cleaner solution. But for now, we will take the quick and dirty way here. We'll go with option 2. But how to eliminate the need for R to know about the 192.168.103.x network. Well, the same way it works on the internet. The internet does not know anything about your internal network either, yet can send reply back in. Why ? cos you MASQUERADE the paket at your router. So you will have to do exactly the same with the 192.168.103.x network. MASQUERADE it at the linux box, so the router thinks that the request acctually came from 192.168.102.2. since the router knows how to find that host, it can then send the incomming reply to 192.168.102.2. This is your linux box, which will also recognise the paket as a reply, rewrite the DESTINATION again to 192.168.103.254, check it's routing table, figure out that this is a host on a connected subnet, and forward the paket there. HAH - the reply got where it was supposed to go. VICTORY !!! :)

Ok, this was how INTERNAL hosts will connect to the internet. Now the other way around, what happens if you connect from the internet to an internal host. Well, it has pretty much been said. You will have to do a forwarding on your adsl router of the appropriate ports to the linux box (NOT the final destination, as the router cannot find the final destination). Once you forwarded them to the linux box, you will have to do another forward there to the appropriate host. So, you'll have to forward the paket twice.

i am very convinced that should work !

i am not sure how good/bad i explained that whole problem. if there are any question, again, just ask :)

PS: flight to barcelona is about 200 bucks - just teasing :)

---

### Post by jmvidalvia on 2008-04-18
Hi!
This time I needed the peace at home to read carefully your post.
Thank you very much again!
My question is...isn't this rule...
```
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

```
...already doing the masquerade you say?

Aren't packets flaged with source=192.168.102.2 instead of their original source=192.168.103.X when they are already postrouted to eth1? Isn't then the work of masquerading already done?
I asume adsl router (R) is still masquerading, as I didn't tell it not to do so, so we would have two masqueradings (R and L) as you suggest, wouldn't we?
Then which rule should we still add?
Still trying to learn, as you see :)
Thanks again!

---

### Post by SpaceTeddy on 2008-04-18
> **jmvidalvia said:**
> 
```
/sbin/iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
```
...already doing the masquerade you say?

Aren't packets flaged with source=192.168.102.2 instead of their original source=192.168.103.X when they are already postrouted to eth1? Isn't then the work of masquerading already done?
I asume adsl router (R) is still masquerading, as I didn't tell it not to do so, so we would have two masqueradings (R and L) as you suggest, wouldn't we?
mhm, and here i was thinking you took the rules out. If you left that one in, yes, the pakets that go out on eth1 will me masqueraded by it's ip. In that case, you have the two masquerades, and your internal clients work normally. I thought you took everything out and just left the bare essentials in... guess i was wrong there. 

so if you forward anything that needs to forwarded to the linux box now (regardless of it's final destination), you still don't get any connection to your hosts ? can you show me the config of your routers port forwarding again after having it modified ? just want to make sure :)

and i assume you have not changed anything about the rules we discussed earlier. check if they still have the right interface and ip addresses set, then check again if they now get it upon incomming pakets... 

but if it is setup like that now, i (currently) have no idea on what is wrong...

---

### Post by mips on 2008-04-18
Would using [Firewall Builder]("http://www.fwbuilder.org/") not simplify this process, I know not everyone uses GUIs though.

---

### Post by jmvidalvia on 2008-04-18
> **mips said:**
> Would using [Firewall Builder]("http://www.fwbuilder.org/") not simplify this process, I know not everyone uses GUIs though.
:D
Kick in my ***!
:D
Well, you are probably right.
I am quite old fashoned and always liked to use terminal to configure everything. I found that while using GUI for that purpose my config files dind't belong to me really, and didn't know what they were doing.
I also appreciate to learn while fighting against my terminal.
But you are probably right: pople low-to-mid skilled like me should consider using this kind of tools.
Thanks a lot for your suggestion: I shall take it, but just once I am definitively defeat.
Or people like SpaceTeaddy leave me alone forever... :)
Thanks!

---

### Post by jmvidalvia on 2008-04-18
Well, 
Now it is my time to work on this: I shall improve the wiring, check everything, etc.
Meanwhile, I leave here the present situation, with a simplified script and a couple of drawings.
Shall I remind everything seems to work except NAT (connection to AS400 from outside).
After so many changes it was good also for me to clarify everything.
Once again, thank you very much.
:)

---

### Post by SpaceTeddy on 2008-04-18
looks good. The script seems to be correct, the drawing is good, the interfaces in the rules match. The forwarding on the adsl router also looks good. 

There is one thing that might be going wrong, otherwise, this should now work (as far as i can see from the configs :) ) - make sure that your internal hosts have internet connection. If they have that, you should be all set.

i cannot find any flaws in your setup now :) congratulations !!!

hopefully it works now

[EDIT]

don't forget, if this (for some unknown reason) does not work, set your FORWARD table to ACCEPT and try again to make sure there is not an accidental rule blocking you. Thought i might mention it by the off chance that it helps :)

---

### Post by jmvidalvia on 2008-04-19
Dear SpaceTeddy.
I think I found it.
Just walking arround under a sunny but windy day here, an idea came to me.
I started to remember what I did the day I tested the configuration I attached in the previous post.
I changed the IP of my router, from subnet 103 to subnet 102, and NAT all traffic to the Linux server, I changed the IP of the "outer" ethercard in my Linux server, from 103 to 102, I put the new gateway (the inner card of my Linux server) in the dhcp service of the Win Server, and tested.
Then, everything worked, except prerouting. Well, not exactly: one prerouting was working indeed (vnc viewer from outside to one of the machines in the LAN).
I have been wondering why THAT connection worked, and others don't.
The question (and the possible answer) is:
¿who changed the gateway adress (from subnet 103 to subnet 102) in the AS400? NOBODY
¿who changed the gateway adress in the Win Server? NOBODY (just dhcp was updated, but lan config was not updated)
Then all packets coming from outside went through the adsl router, then to the Linux Server, reached their destination, but when they had to return to outside, they tried to reach the old gateway, which had an IP than no more exists.
That's why I got timeouts. These packets must still be in the LAN wondering where the gateway is?
And this explains also that vncviewer worked with a box that had the right gateway (the 103 IP of the Linux Server).
Isn't it reasonable?
I would be pretty happy if this is the answer.
First because I won't bother you any more with my config troubles.
And second because I would have learned a little bit more.
Thanks again for your support!

---

### Post by jmvidalvia on 2008-05-09
Everything works now! Thanks you very much! In my last post I explained the reason why I was having troubles.
Thanks a lot!

---

### Post by SpaceTeddy on 2008-05-10
i must have overseen your answer two weeks ago... or was waiting for you to test the idea and then come back if something does not work.

either way, congratulations on getting it to work. And also on you learning something from this lengthy discussion. That makes all the effort worht it :)

---

### Post by jmvidalvia on 2008-05-11
Hi again!
For those that might be interested in the end of this neverending story, I am posting here my final script (I added restrictions for outgoing traffic and made it a little bit clear, adding some variables). Here it is:
```
#!/bin/sh

# Redes
IPT="/sbin/iptables"
LAN="eth0"
INTERNET="eth1"

# IPs
IBM="192.168.103.20"
SERVERWIN="192.168.103.101"
SEIUBI="192.168.103.240"
BELLIDO="192.168.103.160"
CAMARAIP="192.168.103.154"


## FLUSH de reglas
$IPT -F
$IPT -X
$IPT -Z
$IPT -t nat -F

## Establecemos politica por defecto
$IPT -P INPUT DROP
$IPT -P OUTPUT DROP
$IPT -P FORWARD DROP
$IPT -t nat -P PREROUTING ACCEPT
$IPT -t nat -P POSTROUTING ACCEPT

# Aceptamos las establecidas
$IPT -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -m state --state ESTABLISHED -j ACCEPT

# Dejamos todo a localhost
$IPT -A INPUT -i lo -j ACCEPT
$IPT -A OUTPUT -o lo -j ACCEPT

# Dejamos todo desde la LAN al server
$IPT -A INPUT -s 192.168.103.0/24 -m state --state NEW -i eth0 -j ACCEPT

# Aceptamos ssh
$IPT -A INPUT -p tcp --dport 2223 -m state --state NEW -j ACCEPT

# Permitimos las salidas restringidas

# Esta acepta todo, por si acaso
#$IPT -A OUTPUT -m state --state NEW -j ACCEPT

# Salida de Squid
$IPT -A OUTPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT

# dns
$IPT -A OUTPUT -p tcp --dport 53 -m state --state NEW -j ACCEPT
$IPT -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT

# rsync-ssh
$IPT -A OUTPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT

#ntp
$IPT -A OUTPUT -p udp --dport 123 -m state --state NEW -j ACCEPT

#ping
$IPT -A OUTPUT -p icmp -m state --state NEW -j ACCEPT


### Reglas de forward ###

# AS400
$IPT -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -m state --state NEW --dport 23 -j ACCEPT
$IPT -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -m state --state NEW --dport 449 -j ACCEPT
$IPT -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -m state --state NEW --dport 8470:8476 -j ACCEPT

# Resto de paquetes entrantes para los que hacemos NAT
$IPT -A FORWARD -i eth1 -o eth0 -p tcp --sport 1024:65535 -m state --state NEW -m multiport --dports 5920,5921,5922,3389 -j ACCEPT

# Resto de servicios permitidos
$IPT -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp -m state --state NEW -m multiport --dports 53,443,465,995,1863,2223,5222,3389,5900 -j ACCEPT
$IPT -A FORWARD -s 192.168.103.0/24 -i eth0 -p tcp -m state --state NEW --dport 6891:6901 -j ACCEPT

# DNS
$IPT -A FORWARD -s 192.168.103.0/24 -i eth0 -p udp --dport 53 -j ACCEPT
$IPT -A FORWARD -d 192.168.103.0/24 -o eth0 -p udp --sport 53 -j ACCEPT

# FTP
$IPT -A FORWARD -p tcp -m tcp -m multiport --dports 20,21 -m state --state NEW -j ACCEPT
$IPT -A FORWARD -p tcp -m tcp -m state --dport 1024:65535 --sport 1024:65535 --state RELATED -j ACCEPT

# PING
$IPT -A FORWARD -s 192.168.103.0/24 -p icmp -j ACCEPT

# Modulos ya cargados por /etc/modprobe
#modprobe ip_nat_ftp ports=21
#modprobe ip_conntrack_ftp

# Ahora hacemos enmascaramiento de la red local y activamos el BIT DE FORWARDING
$IPT -t nat -A POSTROUTING -o eth1 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward


### Redirecciones ###

# Enviamos el puerto 80 al 3128 para el proxy squid
$IPT -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128

# AS 400 
$IPT -t nat -A PREROUTING -i eth1 -p tcp --dport 23 -j DNAT --to-destination $IBM
$IPT -t nat -A PREROUTING -i eth1 -p tcp --dport 8470:8476 -j DNAT --to-destination $IBM
$IPT -t nat -A PREROUTING -i eth1 -p tcp --dport 449 -j DNAT --to-destination $IBM

# Camara IP
#$IPT -t nat -A PREROUTING -i eth1 -p tcp --dport 1234 -j DNAT --to $CAMARAIP:1234

# Terminal server
$IPT -t nat -A PREROUTING -i eth1 -p tcp --dport 3389 -j DNAT --to $SERVERWIN:3389

# vnc
$IPT -t nat -A PREROUTING -i eth1 -p tcp --dport 5920 -j DNAT --to $SERVERWIN:5920
$IPT -t nat -A PREROUTING -i eth1 -p tcp --dport 5921 -j DNAT --to $SEIUBI:5921
$IPT -t nat -A PREROUTING -i eth1 -p tcp --dport 5922 -j DNAT --to $BELLIDO:5922
$IPT -t nat -A PREROUTING -i eth1 -p tcp --dport 55064 -j DNAT --to $SEIUBI:55064

# Fin del script

# Activar solo para comprobar logs
#iptables -A OUTPUT -j LOG --log-level 6

```

I also made a drawing with the structure of my net, that you will find attached.

Thanks eveybody again, specially SpaceTeddy... ;)

PS: Sorry I didn't translate into English the comments into the script.

---

