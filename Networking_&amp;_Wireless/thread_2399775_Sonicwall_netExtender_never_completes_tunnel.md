---
title: "Sonicwall netExtender never completes tunnel"
date: 2018-08-29
forum: Networking &amp; Wireless
---

### Post by jhb3 on 2018-08-29
I am running 16.04.4 LTS with NetExtender 8.6.801 installed. From command line I get the the below output.  (GUI just freezes, never writes log)
Win7 in Virtual Box connects fine. 

Thanks 
JHB
[FONT=monospace][COLOR=#000000]

sudo netExtender[/COLOR]
[/FONT]

connecting to 123.456.789.001:1234
Connected.
Logging in...
Login successful.
Version header not found
SSL Connection is ready
Using SSL Encryption Cipher 'ECDHE-RSA-AES256-SHA384'
Using new PPP frame encoding mechanism
Using PPP async mode (chosen by server) 
Connecting tunnel...

<after <ctrl c>

[FONT=monospace][COLOR=#000000]^CTerminating pppd...[/COLOR]
SSL VPN logging out...
SSL VPN connection is terminated.
Exiting NetExtender client


[/FONT]

---

