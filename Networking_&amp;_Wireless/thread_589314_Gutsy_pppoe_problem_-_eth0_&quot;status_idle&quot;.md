---
title: "Gutsy pppoe problem - eth0 &quot;status: idle&quot;"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by Lesleyp on 2007-10-24
Greetings Ubers

Since changing from Ubuntu 7.04 to 7.10 (clean install not update) I am unable to connect to the internet by ADSL/ethernet (wired). Synaptic and Firefox etc can’t connect.

Connection properties for eth0 shows “status:idle”

F.Y.I
System is Pentium 4 1600 Mhz 384 MB RAM
Netcomm ADSL2 Modem  Model NB5
O.S. Dual Boot to Gusty or Windows XP
No firewall installed in Gutsy

I have used manual configuration to set DHCP (automatic), 
All network settings and addresses are allocated indicating that the connection is present.
The modem lights indicate “ppp”; “ADSL” and “Ethernet:” are all OK.
In windows XP (dual boot from same computer, Netcomm NB5 modem & connectors) the net connection works fine.
Dialup from  Ubuntu also works fine.

I have gone thoroughly  through the help sections Network Toubleshooting document and removed support for pV6 as suggested.

The only problem that I can find is as follows:-

Action: sudo pppoeconf
Result:
I found 1 ethernet device
eth0
Are all your ethernet interfaces listed?........
'Yes' entered ......
 'Looking for Access Concentrator on eth0'
&#61656; NOT CONNECTED Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.

Also tried
sudo pon dsl-provider
I got a long string of script, but still theconnection is “idle

---

### Post by luopio on 2007-10-26
You can try running pppoeconf with an explicit device name:
pppoeconf eth0

This helped me in getting past the "Access Concentrator"-bit, but did not solve the issue (HomePNA/pppoe-network not working). I'll try again today. I'm hopeful that the issue can be solved by giving arguments to the kernel module:

sudo modprove pcnet32 pcnet32_homepna=1
sudo depmod -a

this will hopefully force the device to use the homepna port (?) and will lead into finding the access concentrator.

---

### Post by Lesleyp on 2007-10-28
Thanks muchly for your reply, however time and my patience ran out, I deleted the Gutsy (Gusty might be a bettey name?) partion and reinstalled Feisty which sets up the connection first off. However, I'd be interested to find out if you get it going. Assuming that you are considerably more knowledgeable than myself, is this a bug in Gutsy?

thanks,
Lesley

---

### Post by luopio on 2007-10-28
I got it working. I had to edit some module loading code under /etc to get the module working with the "homepna=1" parameter (it's "homepna" not "pcnet32_homepna"). Can't remember which files, but I think the instructions were here on ubuntuforums.

---

