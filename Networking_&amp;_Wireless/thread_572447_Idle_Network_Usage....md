---
title: "Idle Network Usage..."
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by GSF1200S on 2007-10-10
I just did a reinstall of buntu using kdebase just as an experiment. Everything has been awesome, with the exception of a network issue that I havent experienced before.

For some reason, whenever im not doing anything, conky is reporting constant downloads from the internet at a very consistent amount of time. I installed wireshark to see if this was in fact the case, and wireshark confirms this.

Ive attached a screenshot with wireshark results up. You all may be quick to jump on Amarok and Kontact as possible reasons, but ive closed both and the problem remains.

Any ideas on how to find the offending party here?

---

### Post by GSF1200S on 2007-10-10
bump..

---

### Post by GSF1200S on 2007-10-11
final bump...

---

### Post by NotRoot:-) on 2007-10-11
type netstat -p from a terminal window.  The "p" flag lists the program.

You can type man netstat       or   info netstat   for more detailed information on this useful command.
Its also available in Winderrors  :-)

netstat -ptn  may be the command that you are looking for.

---

### Post by GSF1200S on 2007-10-11
> **NotRoot:-) said:**
> type netstat -p from a terminal window.  The "p" flag lists the program.

You can type man netstat       or   info netstat   for more detailed information on this usefull command.
Its also available in Winderrors  :-)

Ill have to try this when I get home. I dont guess this command is like top where it consistently monitors the net connection (*as top manages cpu/mem/etc)? 

Thanks alot :)

---

### Post by NotRoot:-) on 2007-10-11
The c flag is for continuous.  So try netstat -ptnc
The n flag is for numeric.  If you'd rather see the name, instead of the ip address, just omit the n flag.

---

### Post by Boomy on 2007-10-12
Those are SSDP (Simple Service Discovery Protocol) frames from your router. Mine does the same thing. I think it is basically advertising that it is the gateway, dns, and dhcp.

[http://en.wikipedia.org/wiki/Simple_Service_Discovery_Protocol](http://en.wikipedia.org/wiki/Simple_Service_Discovery_Protocol)

---

