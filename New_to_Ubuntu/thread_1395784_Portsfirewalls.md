---
title: "Ports/firewalls"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by il pepe on 2010-02-01
i have problems with my ports/emails/firewall

I tried a couple of different firewalls, did some changes, deinstalled them and tried another one. 
now i'm using gufw as a simple tool to change my settings in ufw and so in iptables.

But no i can't send no emails anymore via smtp.
I can receive them, but i can't send them anymore (thunderbird 3), although i clearly have opened the port.

since the playing around with the firewalls, vuze doesn't work either any more.

I did the iptables flush..

any one any ideas to help me out?

---

### Post by skymera on 2010-02-01
To see what is happening a bit better install Firestarter.

It's a frontend to IP tables and it's GUI, so you can fiddle a bit easier :)

---

### Post by mcduck on 2010-02-01
> **il pepe said:**
> i have problems with my ports/emails/firewall

I tried a couple of different firewalls, did some changes, deinstalled them and tried another one. 
now i'm using gufw as a simple tool to change my settings in ufw and so in iptables.

But no i can't send no emails anymore via smtp.
I can receive them, but i can't send them anymore (thunderbird 3), although i clearly have opened the port.

since the playing around with the firewalls, vuze doesn't work either any more.

I did the iptables flush..

any one any ideas to help me out?

Did you open the outgoing port used by Thunderbird, or the SMTP server port (25)?

Usually there really isn't any reason to restrict any outgoing traffic with your firewall. It's not as if this was Windows where you can't trust your applications to not call home or spread viruses... ;)

For prety much all home use as simple configuration as allowing all outgoing traffic and stopping all incoming is enough. After that you can open incoming ports as required.

...although even having a firewall at all isn't that importnat on defaut Ubuntu setup. There are no runnng services that would listen for incomng connections, so there isn't any need for closing any ports. Most users will be just fine without a firewall, you only need to install one if you are running some server software that doesn't have built-in options for restricting connections, or if you need t restrict what contents and services users are able to connect to.

---

### Post by mkvnmtr on 2010-02-01
Every time I have tried to install a front end I have fouled up the firewall that is running by default. iptables does a fine job of controlling the ports without my intervention. It allows me to send email, torrent or anything I want to do. Then when I check my system with some so called hacker tools that I have I find closed or filtered ports. I believe we are better off not fooling with the default settings unless we know and understand exactly what we are doing.

---

### Post by il pepe on 2010-02-02
i reinstalled firestarter and i'm able to send emails again. 
I didn't have to change anything.... Weird.
anyway, thanks for the tips.

Vuze is still not working properly but that will be caused by something else i suppose...

---

### Post by superprash2003 on 2010-02-02
do mark this thread as solved if your problem is solved

---

