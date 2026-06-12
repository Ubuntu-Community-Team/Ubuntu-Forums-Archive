---
title: "Weird Samba Behaviour"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2008-01-30
Using 7.10 on a home network of five PCs + occasional notebook. 

The network is pretty much sorted and working. 

However,  one WindowXP machine when, after its been rebooted or a new user logs on, fails to connect to  linux (samba) PC which AFAIK is working correctly. Error messages vary;  "<server> not found, "Network path not found" or a log in dialog pops up.

I can always connect using the Linux PC's IP address. 

[B]I have worked out that if I restart SAMBA, and sometimes I have to do this several times, the WindowsXP PC throwing the errors will eventually connect. 
[/B]
Any one have any clues as to what might be happening here?

---

### Post by mpokrywka on 2008-01-30
Sometimes some firewall software on windows interacts badly with netbios name resolution - try:

1. set windows not to be "local master browser" (somewhere in properties of microsoft network) - I attach "reg" file that makes that change, reboot to check if it helps,

2. force ubuntu PC to be "local master browser" - add ```

    os level = 255
    domain master = yes
    local master = yes
    preferred master = yes

``` to /etc/samba/smb.conf and restart samba```
sudo /etc/init.d/samba restart
```
check if windows PC now connects,

3. turn off firewall on windows and check if problems disappear - if only this helps, try some firewall configuration, maybe unblock all packets from ubuntu IP.

---

### Post by GuiGuy on 2008-01-31
> **mpokrywka said:**
> Sometimes some firewall software on windows interacts badly with netbios name resolution - try:.

Thanks. I'll give it a whirl and will let you know.

Cheers

---

