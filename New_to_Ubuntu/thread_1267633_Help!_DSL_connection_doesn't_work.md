---
title: "Help! DSL connection doesn't work"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by elsrkite on 2009-09-16
[SIZE=2]My apartment has a DSL connection which I can't get to work.  I have no idea what's going on.

I called the ISP and they gave me instructions to run diagnostics on the modem.  Here are the results:
[/SIZE][SIZE=2]Test your ENET Connection: [/SIZE] [SIZE=2]PASS[/SIZE]                                                        
[SIZE=2]Test ADSL Synchronization:                         [/SIZE]                         [SIZE=2]PASS[/SIZE]
[SIZE=2]Test ATM OAM F5 segment ping:[/SIZE]                          [SIZE=2]PASS
[/SIZE][SIZE=2]Test ATM OAM F5 end-to-end ping:[/SIZE]                          [SIZE=2]PASS [/SIZE]                                                                               
[SIZE=2]Test PPP server session:[/SIZE]                         [SIZE=2]FAIL[/SIZE]
[SIZE=2]Test authentication with ISP:                         [/SIZE]                         [SIZE=2]PASS
[/SIZE][SIZE=2]Test the assigned IP address: [/SIZE]   [SIZE=2]FAIL[/SIZE]
[SIZE=2]Ping default gateway: [/SIZE]   [SIZE=2]FAIL[/SIZE]
[SIZE=2]Ping primary Domain Name Server: [/SIZE]   [SIZE=2]PASS[/SIZE]   [SIZE=2]

After that didn't get me anywhere, the ISP sent someone to check out the modem, and said it was working fine.

When I type "sudo pppoeconf" into the terminal it eventually gives me this:
"PPPoe access concentrator cannot be found" ... it suggests checking the cables, and if there are "other processes" controlling the modem.

Any ideas? Should I try a different ethernet cable? That's what the terminal message says, but it seems strange that I could be connected to the modem but not the internet, if the modem is okay.  I don't know where to start here.

Thank you!
[/SIZE]

---

### Post by FreewheelinFrank on 2009-09-16
What's the make and model of the modem?

---

### Post by briantoumbs on 2009-09-16
Did you goto the modems ip? like [http://192.168.1.0](http://192.168.1.0) or what ever its set as, normally on the bottom sticker i think, then put the modem access code in. see if it is connected?

---

### Post by elsrkite on 2009-09-16
The modem is a ZTE ZXDSL 831 II.

Yeah, the modem's IP is where I ran the diagnostics. Is putting in the modem access code something else? Where would I find it?

---

### Post by FreewheelinFrank on 2009-09-16
Google brings up plenty of hits, like this one.

[http://smartinfo.com.my/it/PC_Hardware/TM_Net_Streamyx_ZTE_ZXDXL_831_Modem.htm](http://smartinfo.com.my/it/PC_Hardware/TM_Net_Streamyx_ZTE_ZXDXL_831_Modem.htm)

The settings below will need changing according to your ISP. If you Google the name of your ISP and the router, you should get the settings you need- that's how I got my modem/router running with my current ISP.

> PPP Interface = ppp-0
ATM VC = aal5-2 or equivalent ( VPI=0, VCI=35 setting)
Interface Sec Type = Public
Status = Start
Protocol = PPPoE
Use DHCP/DNS = Enable
Security Protocol = PAP
Login Name = yourname@streamyx
Password = your password

---

### Post by elsrkite on 2009-09-16
Okay, thanks! I'm trying to work it out, but it's hard because I'm in Argentina and all the hits for my ISP (Speedy) are in Spanish, which isn't my native language. But I think this'll get me going...

---

### Post by FreewheelinFrank on 2009-09-16
These are the settings according to a web search:

> ISP: Speedy
  	Protocol: PPPoE - RFC2516
  	VPI: 8
  	VCI: 35
  	Encapsulation: LLC


[http://bijesh.mukundan.googlepages.com/ISPSETTINGS.doc](http://bijesh.mukundan.googlepages.com/ISPSETTINGS.doc)

---

### Post by elsrkite on 2009-09-16
Got it working :)
Thanks again for the help!

I thought the whole problem came from Argentinian configurations being different somehow -- I couldn't connect to any open wireless networks either.  But I guess that was just bad luck...

---

