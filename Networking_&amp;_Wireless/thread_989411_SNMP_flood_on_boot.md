---
title: "SNMP flood on boot"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by quetzalcoatl-9 on 2008-11-21
My network security admin told me my computer is still causing security warnings on boot:


[INDENT]Policy executed: SNMP Security Violation - ALL
By alert: SNMP Security Violation[/INDENT]

I removed NetworkManager and avahi, I set up a static IP address, I uninstalled any reference to snmp through Synaptic, what else can I possibly do?

This is only one computer out of hundreds.  If our office was all Ubuntu, would the switches crash in the morning when the computers came on from all the snmp flooding?

---

### Post by jonobr on 2008-11-21
did a quick google and saw this, IM not sure if it relates.
[http://labs.idefense.com/intelligence/vulnerabilities/display.php?id=141](http://labs.idefense.com/intelligence/vulnerabilities/display.php?id=141)

Possible a DOS attack due to radius and how it was compiled?

Anyway, could you get more specfics from your admin.
Are you issuing something , receiving? If sending ,
you could probably set something up to prevent that, we would need to know what that is,

---

