---
title: "[SOLVED] I want to filter ip adress like a router"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by jeantasse on 2008-07-01
Hi everybody, i would like to filter ip adress on my ubuntu server like a router would.  Exemple: i have block about 10 chinesse isp because about 90% of the people that tries to hack me comes from there.  But now my router tells me hes full.  Can i compensate with a program install on my server??  Thank you i advance

P.S. Happy Canada Day to all Canadian out there ):P

---

### Post by superprash2003 on 2008-07-02
yes.. you could do this through iptables..

---

### Post by kevdog on 2008-07-02
If the IP addresses are not contiguous, then each one would have to be filtered something like:

iptables -A INPUT -s <source IP> -j DROP

Something like this:

iptables -A INPUT -s 192.168.1.105 -j DROP


For each address, you would need a separate line!

---

### Post by jeantasse on 2008-07-02
thank you very much for the help, but now what if lets say its from 200.0.0.0 to 200.0.0.255, how do i write it?


And thank you again!!

JF

---

### Post by kevdog on 2008-07-02
Since they are contiguous it would be something like:

iptables -A INPUT -s 200.0.0.0/24 -j DROP

This would match all addresses from 200.0.0.0 to 200.0.0.255

---

### Post by Rhubarb on 2008-07-02
If people are trying to hack in to an open ssh port on your server, you could try moving your ssh port to a much higher port number and / or installing sshguard from the Ubuntu repositories.

sshguard can be configured up to block access to your ssh port from the originating IP address if there has been a failed attempt at logging in via ssh.  I use this on my hobby server at home, it updates a list of blocked IPs in /etc/hosts.deny automatically.

If you do choose to use sshguard, make sure you don't manage to block yourself out ;)
(It is possible to specify a white list of IP addresses that will never be blocked by sshguard).

---

### Post by jeantasse on 2008-07-03
Thanks guys, i realy apreciate.

Take care

JF :)

---

### Post by kevdog on 2008-07-03
You could also set time limits in your iptables rules that would limit connection attempts from certain/all iptables.  For example more that 5 login attempts in one hour -- you would ban that ip address from future login attempts for example one hour.  Again the actual number of login attempts, the frequency of attempts, and the ban time can be customized if you need to do this.

---

