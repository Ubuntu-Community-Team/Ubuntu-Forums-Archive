---
title: "Dialup + LAN not working together"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by NJC on 2008-01-06
I have Gutsy and XP as separate PC's connected together via wired router. As well, I'm using a dialup modem to connect to internet but they both don't work simultaneously ... I have modem as Default route to internet in network-admin but that didn't help. 

As soon as I check to activate modem in network-admin, I lose my MSHOME share in XP. Any ideas to have both work at same time?

---

### Post by foolsh on 2008-01-06
see if this works
```
sudo aptitude install firestarter ipmasq dnsmasq
```
then 
with your dialup connection connected
manually configure your Ethernet adapter as static ip address with
address 192.168.0.1
netmask 255.255.255.0
gateway address 192.168.0.1
make sure you place a check in the box next to the connection after you close the properties window
then configure your windows network connection as a static address with
address 192.168.0.2
netmask 255.255.255.0
default gateway 192.168.0.1
and set it to use 192.168.0.1 as the dns server aswell
then

```
gksudo firestarter
```
the first run wizard will help you setup your internet as well as internet sharing
set the dialup adapter as the default internet connection and enable internet connection sharing on the next page
do not enable the dhcp for network box under internet connection sharing
after you click save and the firewall starts with no errors if it does not check to make sure your all your connections are enabled and up
set your network address range to allow connections from the windows box by
clicking on the policy tab then
right click in the "Allow connections from host" field then add 192.168.0.2
 to get things up and running make sure you click the apply button with the green check mark on it
if everything went well you should now be able see your windows computer and give it internet access to it too, while connected to the dialup connection


that was really longer than I planed but I hope this works out for you

---

### Post by NJC on 2008-01-07
foolsh;
 
Thanks for the help ... I went through all of the steps but it only worked intermittently to access XP files from Ubuntu, but not the other way.
 
A few questions. I see Firestarter is blocking 192.168.0.1 - does this need to be added to bypass list? As well, it's blocking my pop3 mail server and since it seems to come up as a different IP each time, I'm not sure how to unblock it.

---

### Post by NJC on 2008-01-11
Any other suggestions? I now have my XP and Ubuntu 7.10 boxes talking to each other after much grief, having followed the SAMBA HOWTO located on this forum. 
 
But as thread title suggests, I cannot use my dialup connection and LAN at same time - one will not work if they are both active in network-admin. Ubuntu is connected to internet via serial dialup modem; XP to Ubuntu via wired router.
 
One oddity in network-admin: delete DNS servers in Ethernet, and it's deleted in dialup modem connection - and vice-versa. And after I connect to my ISP, the DNS servers are added back in - but added to the Ethernet connection as well! 
 
How to proceed?

---

