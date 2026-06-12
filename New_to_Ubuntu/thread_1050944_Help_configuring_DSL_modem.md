---
title: "Help configuring DSL modem"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by sturdy on 2009-01-26
Hi all,

I'm having a hair-pulling printing problem with my DSL modem and ubuntu 8.10. I think the problem is caused by my DSL modem or firewall but I'm a noobe.

I dual boot with Win XP and everything works good under XP. I can print to my Linksys PPSX1 print server. I can enter 192.168.1.47 into IE and get the PPSX1 configuration menu. I can enter 192.168.1.1 into IE and get the DSL modem configuration menu.

But, when I boot ubuntu 8.10 I cannot see either config menu using Firefox. When I try to print, the print queue tells me the printer is busy. Sometimes I get a status message that says the IP appears valid but the printer may not be connected. I cannot ping either IP using Network Tools but I can see the modem lights blink for each ping attempt. Strangely, Firefox immediately connects to external URL so the config appears okay.

Any ideas? TIA...
Sturdy

---

### Post by Izek on 2009-01-26
[http://ubuntuforums.org/showthread.php?t=435983](http://ubuntuforums.org/showthread.php?t=435983)

---

### Post by sturdy on 2009-01-26
> **Izek said:**
> [http://ubuntuforums.org/showthread.php?t=435983](http://ubuntuforums.org/showthread.php?t=435983)

Hi Izek,

Thanks for that link...I'll try it tonight. I searched the forums for everything I could think of except PPSX1.

Sturdy

---

### Post by sturdy on 2009-01-27
Alas, no joy. I installed the print server/printer as described in the link and get the same results as before...print queue responds that the printer is busy and status area indicates the printer may not be installed. Prints hang in the queue without printing.

The problem seems to be the DSL modem or firewall blocking the print server. I should be able to access the DSL modem by entering the IP (192.168.1.1) but that fails in ubuntu, works in XP. Any ideas?

---

### Post by Izek on 2009-01-27
What is your DSL Modem?

---

### Post by sturdy on 2009-01-27
> **Izek said:**
> What is your DSL Modem?

The DSL modem is a Westell Versalink 327W. It works fine with XP so I don't see a problem with the modem. Since I cannot access the modem by IP from Firefox, it is more like a ubuntu config issue.  Maybe ubuntu iptables? Unfortunately, I don't yet know my way around ubuntu BUT I've been reading ;)

---

