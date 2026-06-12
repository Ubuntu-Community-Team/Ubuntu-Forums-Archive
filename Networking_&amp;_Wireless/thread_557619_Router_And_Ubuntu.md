---
title: "Router And Ubuntu"
date: 2007-09-22
forum: Networking &amp; Wireless
---

### Post by KillerbawX on 2007-09-22
I have a box and when we run dmz on the router Apache, Webmin and so on. Soon as we take the router off DMZ we loose connection. Only thing that seems to work behind the router is SSH for telneting in. We have no firewalls running as far as we know. We do use non standard ports for some SSL ports. From what I can think of is there is some sort of firewall running that is conflicting with the router but like I said we run no firewall. Any one have a suggestion or 2.

---

### Post by reckless2k2 on 2007-09-22
i'm having a little trouble understanding what you are saying but if it's a hostname issue with apache, make sure your /etc/hosts resolves that url and or make sure the virtual hosts in apache is setup to work correctly for such a behind NAT issue.

ssh will work because it is IP related.

---

### Post by KillerbawX on 2007-09-23
In the router we put the machine with ubuntu on DMZ internal ip is 192.168.1.29. Soon as we turn the router on for that box and take it off DMZ and forward all the ports we need we loose the access to them 
ex.

Webmin - port 10000 ( DMZ - Works ) ( No DMZ and port fowarded in router - No Work )
Unreal IRCD - port 7000 ( DMZ works ) ( No DMZ and port forwarded in router - No Work )

As long as we use DMZ all stuff works fine. Soon as we take the box off DMZ and use port forward we loose these things. Only things that work on router is SSH and VNC

---

### Post by reckless2k2 on 2007-09-23
again, it sounds like a hostname issue on that box. have you looked at those files i suggested?

how are you trying to access them? 

if you can access those pages via IP and not by hostname, again it's a hostname issue in the places i suggested.

---

### Post by KillerbawX on 2007-09-23
Hostname is fine and no I can not access  them by IP either. This is why im lost on what is wrong. Soon as router is taken of DMZ for this box we loose pretty much all of the access. SSH work but anything to do with ssl doesn't could there be soemthing in ssl not working

---

