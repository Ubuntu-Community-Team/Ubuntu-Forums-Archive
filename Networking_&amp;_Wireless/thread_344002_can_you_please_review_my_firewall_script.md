---
title: "can you please review my firewall script?"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by pmark on 2007-01-22
Since I installed Ubuntu, I edited a script someone else was using and ended up with this simple script as a basic firewall:

```

# prevent SYN floods from consuming memory resources
echo "1" > /proc/sys/net/ipv4/tcp_syncookies

# set the default policy for each chain
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# flush (remove) all rules
iptables -F INPUT 
iptables -F FORWARD 
iptables -F OUTPUT 

# allow traffic for sessions which are already established
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# open the loopback for applications that communicate using the loopback address
iptables -A INPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -i lo -j ACCEPT

# open ports for HTTP and HTTPS
iptables -A INPUT -p tcp -s 0/0 --destination-port 80 --syn -j ACCEPT
iptables -A INPUT -p tcp -s 0/0 --destination-port 443 --syn -j ACCEPT
```

The problem is that, _[Shields Up](https://www.grc.com/x/ne.dll?bh0bkyd2)_ shows that there is a number of open ports:

```
GRC Port Authority Report created on UTC: 2007-01-22 at 15:39:43

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
                            119, 135, 139, 143, 389, 443, 445, 
                            1002, 1024-1030, 1720, 5000

    3 Ports Open
   21 Ports Closed
    2 Ports Stealth
---------------------
   26 Ports Tested

Ports found to be OPEN were: 21, 23, 80

Ports found to be STEALTH were: 135, 445

Other than what is listed above, all ports are CLOSED.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.
```

This is strange, WinXP with ZoneAlarm passes the test without any "flaws".

Why is this happening? Does my iptables script need improovements?

---

### Post by kosmic on 2007-01-24
Your firewall rules are very simple and do not block all ports, if you are new using iptables, use a gui like ***Firestarter*** or [I][B]Guardog.

[/B][/I]If you look carefull at your firewall rules you are opening ports 80 a 443 for incoming traffic

for example try putting this rule in your iptables :

[B]iptables -A INPUT -i eth0 -m state --state ! ESTABLISHED,RELATED -j DROP

*eth0 - *if you are using and ethernet adaptador
ppp0 - if you connect directly to the net like an USB modem
[/B]   ;) and then try shields up again and post here the results.


Some usefull iptables rules are :

AVOID PING OF DEATH :
iptables A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT
iptables A INPUT -j DROP


IP SPOOFING PROTECTION
iptables -A INPUT -s 192.168.1.0/24 -i ! eth0 -j DROP
iptables -A INPUT ! -s 192.168.1.0/24 -i eth0 -j DROP

* 192.168.1.0 - should be your internal ip, if you dont know do 'ifconfig' in a terminal and have a look there.

---

### Post by handy on 2007-01-24
A wonderful how-to by Frodon is here:

_***[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)***_

Once you have read through it once, it will take you < 5 minutes to set up a machine in future, just cutting & pasting from the how-to. :D

[Edit:] I thought I'd throw the following link in for good measure:

_***[http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables](http://ubuntuforums.org/showthread.php?t=159661&highlight=iptables)***_

---

### Post by pmark on 2007-02-05
After adding the lines that you gave me, I tried again GRC and hackerwatch.org portscanners and got the same results.

I begun to suspect that it's something else that's going wrong. And then it hit me... I am using a DSL modem/router (Zyxel Prestige 660HW-61) to connect to the Internet. I disconnected the DSL modem and connected via a serial modem. I tried the portscanners again and the results were much, much better. The ports that the portscanners reported as open were in fact the ports that are open on the router.

Next, I read the guides and wrote a nice script that only allows specific things for OUTPUT. This improoved things even more. All ports from 1 to 1023 are beeing reported as "stealth". Is that better than "closed"?

Well, anyway, I guess I am (or just feel) a little more secure now :-P

I am including the script to get additional feedback and just in case someone else would like to use it.

Two questions:
1. Does the "--syn" tag I have added (and don't really know what it does) provides anything useful?
2. Does really FTP needs so many ports on OUTPUT

```
# =================================================
# iptables script (originally for ubuntu 6.10)
# date: 2007-02-02 15:05
# =================================================


# prevent SYN floods from consuming memory resources
echo "1" > /proc/sys/net/ipv4/tcp_syncookies

# no ICMP (although I am blocking everything and I am not specifically allowing ICMP on INPUT, so this could be omited)
echo "1" > /proc/sys/net/ipv4/icmp_echo_ignore_all
# echo "1" > /proc/sys/net/ipv4/icmp_echo_ingome_broadcasters

# no spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
  then
    for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
  do
    echo 1 > $filtre
  done
fi 

# set the default policy for each chain
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

# flush (remove) all rules from default chains
iptables -F INPUT 
iptables -F FORWARD 
iptables -F OUTPUT 

# remove all custom chains
iptables -X

# allow traffic for sessions which are already established
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# open the loopback address
iptables -A INPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -i lo -j ACCEPT

# HTTP
iptables -A INPUT -p tcp -m tcp --source-port 80 --syn -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --destination-port 80 -j ACCEPT

# DNS (domain lookup, HTTPS will not work without it, and probably other things too)
iptables -A OUTPUT -p udp -m udp --destination-port 53 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --destination-port 53 -j ACCEPT

# HTTPS
iptables -A INPUT -i eth0 -p udp -m udp --source-port 443 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --source-port 443 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --destination-port 443 -j ACCEPT
iptables -A OUTPUT -o eth0 -p udp -m udp --destination-port 443 -j ACCEPT

# IRC IDENT (but not DCC)
iptables -A OUTPUT -p tcp -m tcp --destination-port 6667 -j ACCEPT

# POP3S
iptables -A OUTPUT -p udp -m udp --destination-port 995 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --destination-port 995 -j ACCEPT

# IMAP2
iptables -A OUTPUT -p udp -m udp --destination-port 143 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --destination-port 143 -j ACCEPT

# IMAP3
iptables -A OUTPUT -p udp -m udp --destination-port 220 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --destination-port 220 -j ACCEPT

# Newsgroups/Usenet
iptables -A OUTPUT -p tcp -m tcp --destination-port 119 -j ACCEPT

# SMTP
iptables -A OUTPUT -p tcp -m tcp --destination-port 25 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --destination-port 465 -j ACCEPT

# FTP
iptables -A OUTPUT -p tcp -m tcp --destination-port 21 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --destination-port 20 -j ACCEPT
iptables -A OUTPUT -p tcp -m tcp --source-port 1024:65535 --destination-port 102:65535 -j ACCEPT # suspicious line, but lets leave it like this for now

# MSN messenger (Microsoft/Hotmail)
iptables -A OUTPUT -p tcp -m tcp --destination-port 1863 -j ACCEPT

# TELNET (useful for configuring the router)
iptables -A OUTPUT -p tcp -m tcp --destination-port 23 -j ACCEPT

# allow outgoing ICMP requests (PING)
iptables -A OUTPUT -s 192.168.1.0/0 -p ICMP -j ACCEPT

# --- appendix ---

# IRC IDENT & DCC
# iptables -A INPUT -p tcp -m tcp --source-port 6667 -j ACCEPT
# iptables -A INPUT -p tcp -m tcp --source-port 113 -j ACCEPT
# iptables -A OUTPUT -p tcp -m tcp --destination-port 6667 -j ACCEPT
# iptables -A OUTPUT -p tcp -m tcp --source-port 1024:65535 --destination-port 1024:65535 -m state --state NEW -j ACCEPT
```

---

### Post by dannyboy79 on 2007-02-05
> **kosmic said:**
>  

iptables -A INPUT -i eth0 -m state --state ! ESTABLISHED,RELATED -j DROP

 

i just looked at my iptables-rules file and noticed something odd. I have this line for my already made connections: 
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
is this ok compared to what you have above?? I thought that you shouldn't put what interface it should be for (eth0 or eth1) etc because if you don't it should applty to all interfaces which is what you'd want most of the time isn't it??? I have added your ping of death and ip spoofing things as I didn't have them and I'll use any security I can get. my ip is 192.168.0.3 so my ip spoofing line is iptables -A INPUT -s 192.168.0.0/24 -i ! eth0 -j DROP which would be right wouldn't it be?? 

1 last thing, I used this link to do my iptables config ([http://www.ubuntuforums.org/showthread.php?t=57111)](http://www.ubuntuforums.org/showthread.php?t=57111)), what it does is actually creates a script that runs and asks you want you want to do, what rules you'd like to apply and then after you answer y or n to the rules you want applied, it applies them but I have noticed that I added an extra rule by copying and pasting from an existing line and changing it to meet the needs to open up the ntp ports but when I restart my machine, those rules that I added weren't readded to the iptables -L. why is this?? I am doing iptables-save after I run the script before I restart the machine. can you maybe explain this?? i would really appreciate the help from anyone.

---

### Post by dannyboy79 on 2007-02-05
> **kosmic said:**
>  
AVOID PING OF DEATH :
iptables A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT
iptables A INPUT -j DROP
. 

i have just found out that these are incorrect. they don't work as is. to correct them you need to add a "-" before the A so they would be

iptables **-**A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT
iptables **-**A INPUT -j DROP

---

### Post by dannyboy79 on 2007-02-05
and actually after I rerun my script, I get this:
Applying rules...Bad argument `DROP'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `DROP'
Try `iptables -h' or 'iptables --help' for more information.
 ok !
so I don't know what's going on????? because I had this rule prior to adding your ip spoofing and ping of death thing and my script worked fine?

#Drop everything else
iptables -A INPUT -j DROP

and all I added was these

#AVOID PING OF DEATH
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -j ACCEPT
iptables -A INPUT -j DROP

#IP SPOOFING PROTECTION
iptables -A INPUT -s 192.168.0.0/24 -i ! -j DROP
iptables -A INPUT ! -s 192.168.0.0/24 -i -j DROP

why would iptables not liek the DROP? is it because I have iptables -A INPUT -j DROP twice? once under the Drop everything and once under your ping death thing?? I don't even allow pings so I probably don't beed that ping of death protection would I? plus I have a hardware firewall between the internet and me and that doesn't allow pings either! any comments from anyone would be great.

By the way, I am **not trying to hi-jack your thread**. I am trying to ask the same type of questions for your benefit as well. I don't agree with opening a new thread with the same subject.

---

