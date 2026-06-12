---
title: "Nicotine+, Firestarter, and Ports"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by Southeast First on 2007-08-01
I know there are already ten thousand topics on this subject, but having read all of them I'm still completely dumbfounded.

On my Feisty box I'm trying to run Nicotine+. Well, it was working at one point, because I apparently downloaded 8 files, as there are 8 songs missing from my downloads queue and the files are in my download folder. The thing is, though, that those in queue give me the "User logged off" status, so I can't tell if the new files I'm trying to download won't because the user has dissallowed shares or if my ports are somehow messed up.

I've tried the command line 
[PHP]sudo iptables -A INPUT -p tcp --dport 2240 -j ACCEPT[/PHP]
with multiple variations in the ports (2234-2240) but that didn't solve the problem. Nor did installing Firestarter and trying to open the port that way.

When Nicotine+ is running, Firestarter shows that it's an active connection, but nevertheless I get the "Cannot connect" status in Nicotine+. I've also tried playing with the inbound traffic policies but that was without avail. As of now I've got

Allow Service 
Name: Soulseek
Port: 2234
IP, host, or network: 192.168.1.102

But that hasn't changed anything. As I said, I've played around with the settings, changing the services IP to and from multiple different IPs and even to the "Everyone" setting. Still, I can't connect to these users on Nicotine+. I assume I'm just not knowledgeable enough with opening ports and such, as I never had this problem on Windows and I never had to forward ports despite being using an ADSL modem with a Linksys wireless router. Any help or advice would be greatly appreciated.

---

### Post by Claus7 on 2007-08-02
Hello,

if as you said you did everything as far as firestarter is concerned probably you should do port forwarding.
There are two links that I can give you:

[http://portforward.com/routers.htm](http://portforward.com/routers.htm)
where you can choose the type of the modem/rooter you have and configure it accordingly and

[http://ubuntuforums.org/showthread.php?t=472123](http://ubuntuforums.org/showthread.php?t=472123)
which is focused on another program and probably modem/rooter, yet the general idea is the same.

I hope this helps,
Regards!

---

### Post by Southeast First on 2007-08-21
Forwarding the port did nothing.

---

### Post by Claus7 on 2007-09-03
Hallo,

really I haven't used the program you are interested in so I 'm not an expert. What I tell you is from my humble experience with another p2p program (I think that's what the program in question is). 
There are two things that I can tell you :

i) Are you sure that the port forwarding via your modem with the opening of ports with firestarter was done simultaneously using the same numbers (to your modem, to your program -probably in some options sub menu-, to firestarter) ? 

ii)I have heard something about proxy servers. Do you think that this might be your problem? Unfortunately I do not know exactly what these are, yet I have come across with these in the forums before.

I hope you the best,
Regards!

---

