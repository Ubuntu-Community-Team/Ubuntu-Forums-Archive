---
title: "Just Upgraded to Edgy now Wireless not Working..."
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by cerhart on 2007-02-08
I just upgrade from Daper to Edgy. Under Daper I had no problems with my wireless, it worked from the moment I installed it and put in my wireless card (a Netgear WG511T). Last night I upraded my system to Edgy and after the system restarted my wireless connection no longer worked. 

In Gnome if I go to System > Administration > Network Tools and select my card (ath0) from the network device dropdown menu it will display my IP addresses in the IP Information box below and it picks up all of the wireless card information in the section at the bottom. It will even tell me about the connection (how many packets have been sent/received etc.). If I click on the "Configure" button on this screen I get the message that "The configuration could not be loaded. You are not allowed to access the system configuration." It never gives me the opportunity to enter my administrator password though. 

If I go to System > Administration > Networkworking then I get the Network Settings window. The first connection listed is the Wireless connection but it says "This network interface is not configured." If I select it and click on properties then the settings window comes up. I can check the "Enable this connection" box and click the OK button but it still says that the interface is not configured and if I go back into "Properties" then the "Enable this connection" box is unchecked again. 

The network manager (the little icon that looks like two monitors in the system tray) recognizes the connection and will provide all the information it should (signal strength, packets sent & received. 

It just looks like the card is working and is recognized but Edgy won't let me enable it or use it. 

Any ideas?? Thanks!!!!

---

### Post by dannyboy79 on 2007-02-08
try these commands from the command line. sudo ifdown ath0
and then sudo ifup ath0.
also, please post your /etc/network/interfaces file. I have that same exact card but I still use Xubuntu Dapper because I heard of wireless issues with Edgy. Anyway, I only figured if you're having problems using the gui stuff, you could always try the cli. good luck

---

### Post by dannyboy79 on 2007-02-08
yep, this is a bug with the madwifi driver. dapper used madwifi-old and not edgy uses madwifi-ng. supposedly the fix is to update madwifi-ng r2081 per this link, look at the very bottom, whoever posted on 2/6/07 states that this issue is fixed with the release of madwifi-ng r2081.

[http://madwifi.org/ticket/1016](http://madwifi.org/ticket/1016)

good luck.

---

