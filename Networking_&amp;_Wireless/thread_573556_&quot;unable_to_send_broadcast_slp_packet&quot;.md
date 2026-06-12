---
title: "&quot;unable to send broadcast slp packet&quot;"
date: 2007-10-11
forum: Networking &amp; Wireless
---

### Post by geofff on 2007-10-11
I'm still using Ubuntu 6.06. I've set up an hp deskjet d4260 printer on a networked windows machine, replacing a previous printer now broken. The machines are only networked for printing purposes - via a D-link router. 

The driver for 4200 series printers is not available via synaptic and has been downloaded from HPLIP and installed as far as it will go. However I cannot get it to see the networked printer. I get a message "unable to send broadcast slp packet (1,operation not permitted)". I've checked to see if for some reason firestarter, loaded not too long back,  is stopping it but, being very none techy I cannot see how it could be. I've made sure the printer on the windows machine is shared.

I did think I might get round the problem by loading the new printer from system/admin now that the new HPLIP files have been loaded but the 4200 still doesn't show up!

Can someone tell me what has to be enabled in firestarter for an slp packet to get through so that I can check to make sure I've done whats needed. Any other ideas also very welcome!

Thanks

Geofff

---

### Post by geofff on 2007-11-23
I decided the time had come to upgrade from Dapper to try to fix some of the bugs that had accumulated over the years.  Gutsy automatically loaded the relevant printer driver but I still didn't know what service to allow through the firewall. 

The answer was simple for anyone knowing anything about firewalls and firestarter:- opened the firestarter events window - then accessed the network setup window through System>Admin>Network, ticked (in my case) wired connection, looked up properties, unticked "enable roaming" and chose DCHP configuration and closed window. The system looked for network connections automatically. A message was instantly received in the Firestarter events window. Right clicking on this highlighted it and then left clicking brought up options for automatically allowing the service. The outgoing service (with restrictive firestarter options enabled) for me was Samba (SMB) which I had to set up  because the automatic system only set up host address. 
The incoming service Snmp was established automatically on clicking on the options window. 
Havilng then set up the various printer options I can now print.

---

