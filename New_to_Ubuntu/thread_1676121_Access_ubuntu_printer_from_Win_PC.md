---
title: "Access ubuntu printer from Win PC"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by BrianV on 2011-01-26
How do I configure a ubuntu 10.94 PC to share its printer with Windows PCs on the home network?

I have a NetGear WPN824v3 router with the ubuntu desktop PC and a WinXP PC wired to two Ethernet ports and a Vista laptop connected by wireless.

So far I have set up file sharing using samba on the ubuntu PC and confirmed I can see the share folder on the laptop.

I cannot see the ubuntu printer (a Cannon IP2000) from the laptop. 

Since this must be a fairly common need, I expected to find a 'How To' on the topic, but I must be using the wrong search words. A pointer to the correct documentation would be great!

---

### Post by Frogs Hair on 2011-01-26
This may give you a start. [https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by Wobblybob on 2011-01-26
assuming you have set the printer up and can print to it from ubuntu, go to [System], [Administration], [Printing], [Server], [settings] tick publish shared printers connected to this system. ok it and in the server tab click on connect and ok.

open a browser and go to [http://localhost:631](http://localhost:631) which should open the cups web page. Check out what you printer queue name is in the [Printers] tab, mine was Epson-Stylus-Photo-R200 then on the Windows pc my wife is Win7 add the printer as [http://server_name:631/printers/EPSON_Stylus](http://server_name:631/printers/EPSON_Stylus) Photo-R200

server_name is whatever [hostname] you called the ubuntu pc during install or it's ip address if it's fixed.

Good Luck

---

### Post by sammiev on 2011-01-26
> **Wobblybob said:**
> assuming you have set the printer up and can print to it from ubuntu, go to [System], [Administration], [Printing], [Server], [settings] tick publish shared printers connected to this system. ok it and in the server tab click on connect and ok.

open a browser and go to [http://localhost:631](http://localhost:631) which should open the cups web page. Check out what you printer queue name is in the [Printers] tab, mine was Epson-Stylus-Photo-R200 then on the Windows pc my wife is Win7 add the printer as [http://server_name:631/printers/EPSON_Stylus](http://server_name:631/printers/EPSON_Stylus) Photo-R200

server_name is whatever [hostname] you called the ubuntu pc during install or it's ip address if it's fixed.

Good Luck

Hi Wobblybob, I came across your post just mins a go and this is one of the things I wanted to try with the kids laptop I put together with Ubuntu so they could play. It only took seconds to get the printer working with your example. TY sir! :)

---

### Post by BrianV on 2011-01-27
> **Wobblybob said:**
> assuming you have set the printer up and can print to it from ubuntu, go to [System], [Administration], [Printing], [Server], [settings] tick publish shared printers connected to this system. ok it and in the server tab click on connect and ok.

open a browser and go to [http://localhost:631](http://localhost:631) which should open the cups web page. Check out what you printer queue name is in the [Printers] tab, mine was Epson-Stylus-Photo-R200 then on the Windows pc my wife is Win7 add the printer as [http://server_name:631/printers/EPSON_Stylus](http://server_name:631/printers/EPSON_Stylus) Photo-R200

server_name is whatever [hostname] you called the ubuntu pc during install or it's ip address if it's fixed.

Good Luck

Thank you, Wobblybob. 

I have followed your instructions, but the Vista laptop cannot see the printer: on trying to add a network printer (on the Vista machine)following your suggested format I get the error message:

"Windows cannot connect to the printer. Make sure you have typed the name correctly, and that the printer is connected to the network." 

I have tried using the http://<computer-name>/printers/Canon-iP2000 shared printer name variant, also using the computer's IP-address instead of <computer-name>, also using usb instead of printers, also adding/.printer (which Vista seems to want. In every case I get the same failure.

Any further suggestions?

---

### Post by Wobblybob on 2011-01-27
did you add the :631 port info as in http://<computer-name>:631/printers/Canon-iP2000 ?

can you connect to the cups web page on the server from your windows pc with http://<server-name>:631 in your browser. If not then you have a network problem, firewall problem?

---

### Post by BrianV on 2011-01-27
Thanks for the fast reply, Wobblybob.

I did miss out the :631, and putting it in properly has solved the problem.

Thanks for your kind and fast help.

---

### Post by sammiev on 2011-01-27
> **BrianV said:**
> Thanks for the fast reply, Wobblybob.

I did miss out the :361, but putting it in hasn't helped. On the Vista machine Windows Firewall is turned off and I suppressed the Norton360 firewall while trying to connect to [http://brian-desktop:361](http://brian-desktop:361). Netscape reports "Unable to connect", while I can still connect to other sites. Also tried with the IP-addrerss, with the same result. Is it a firewall on the ubuntu machine that I need to suppress/modify?

Hi BrianV, all I did was followed his instructions and when I went to the other computer with the info I got from [http://localhost:631](http://localhost:631) which was:

Description:	EPSON Stylus Photo R280
Location:	sam-Satellite-L500
Driver:	Epson Stylus Photo R280 - CUPS+Gutenprint v5.2.6 Simplified (color, 2-sided printing)
Connection:	usb://EPSON/Stylus%20Photo%20R280

When I entered in my location: sam-Satellite-L500 and did a search and it found the rest it else. Tried to connect and bingo. Saved and was done. I was however going from ubuntu to ubuntu. Never adjusted any firewall in ubuntu. GL :)

---

### Post by BrianV on 2011-01-27
Thanks, sammiev. See my edited post; the problem is solved. I need to be more careful about reading things accurately!

---

### Post by Wobblybob on 2011-01-28
glad your both sorted, BrianV, can you mark the tread as solved noe - see thread tools at the top of page.

Ta

---

