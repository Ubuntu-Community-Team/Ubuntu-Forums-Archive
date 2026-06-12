---
title: "FTP via ETH0 everything else via PPP0"
date: 2015-02-21
forum: Networking &amp; Wireless
---

### Post by geekyhawkes on 2015-02-21
Hello;

I have an ubuntu server I use to wget certain files from the internet via a VPN.  I have set the VPN up using PPP0 and currently adjust the route like this:

sudo route add default ppp0

Everything is working fine with the vpn connection, but now I would like to route FTP traffic via eth0 and not the VPN.

I tried sudo route add default eth0 for the period I was using FTP but lost the internet connection until

 ifdown eth0 ifup eth0

was called.

Clearly I am doing something wrong.

Ideal solution would be to always route all FTP via eth0 if that is easy, if not then what should I add to my bash script to route the traffic back to eth0 while the FTP upload completes (at which point I can go back to route add default ppp0).

EDIT:  Using this iptables -t nat -I POSTROUTING -p tcp --dport 21 -j SNAT --to  MYIPADDRESSFORETH0 i have some success but... I am trying to use this bash script to connect to my FTP server:

 ftp -n ftp.myserver.co.uk <<End-Of-Session

user {username} {password}
binary
put "file1"
put "file2"
bye
End-Of-Session
EDIT: The results of sudo nmap -PN ftp.myserver.co.uk are

 Host is up
 Not shown: 998 filtered ports
 PORT    STATE SERVICE
 80/tcp   open    http
 443/tcp  open    https
whereas when I run nmap from my desktop I get way more ports open (including 21!) I think maybe this is related to my ubuntu server firewall settings? I have tried:

 sudo ufw allow 20 && sudo ufw allow 21

 sudo iptables -A INPUT -p tcp --dport 20 -j ACCEPT  (and the same for 21)
No change.
Thanks for the help;

Andy

---

