---
title: "Need help for VPN configuration"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by sidatra7 on 2007-07-23
Hallo everybody!!!
I am a new user of ubuntu and basically I am very satisfied using it.
But unfortunately there is one last problem that doesnt let me get rid of my windows partition. 

@@@@@@@@@@@@@@@@@@		MY WLAN Configuration	@@@@@@@@@@@@@@@@@
I can work using the wireless network in the student house where i live,
BUT I CANNOT WORK USING THE WIRELESS NETWORK OF MY UNIVERSITY
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Therefore I will give u a complete description of my problem and hopefully 
u can help me.

1. I use Ubuntu 7.04 - the Feisty Fawn (ONLY GNOME XWINDOWS used)
2. My laptop is a HP nx7400
3. The laptop wireless card is the: Intel(R) PRO/Wireless 3945ABG 
and I have installed its drivers(they exist for linux) without any problem
4. I have a dual-boot configuration (Ubuntu-MICROsoft Xp)
5. I need to access 2 different wireless networks:
	
	a.Wireless Connection of the Student house
	ESSID: e.g. essid1
	WITHOUT a VPN account

	b.Wireless Connection of the University
	ESSID: e.g. essid2
	WITH a VPN required (where I have to enter a usename and a pass)

6. The following are installed in my Ubuntu:

	pptpconfig
	VPN Connection Manager (vpnc)
	VPN Connection Manager (openvpn)
	VPN Connection Manager (PPP generic)
	Wireless Assistant
	Wifi-radar
	Network manager
	Network Selector


7. The 5a. works WHILE THE 5b. NEVER WORKED TILL NOW
8. For windows the following VPN adjustments are used:
	VPN type: automatic
	Security: typical (safe password is required,Data encryption is required)
9. Consider my linux command line knowledge regarding networking with linux poor (therefore i please u for 
sth like a step by step guide if possible) 


@@@@@@@@@@@@@@@@@@@@			QUESTIONS
Q1. HOW CAN I CONFIGURE MY WIRELESS SO THAT BOTH WIR.NETWORKS CAN WORK WITH MY MACHINE??
Q2. IS IT POSSIBLE THAT ALL THESE VPN TOOLS I' VE INSTALLED MESS WITH EACH OTHER ??

THNX A LOT IN ADVANCE EVERYBODY :)
Harry

---

### Post by kacheng on 2007-07-23
This likely has something with the DNS settings of your connection.
Check if you have set static DNS servers - you need it to be dynamic so that you can use both your home subnet and the university subnet.
Also check to see if there is a setting on the VPN client regarding gateway servers.  You may not be routing your traffic correctly through the university gateway if you have a static gateway value setup.
Good luck.

---

### Post by sidatra7 on 2007-07-24
thanks for the hint but the problem remains unsolved.
On the other hand there was some progress:

when i run the pptpconfig
i get the following error:

[COLOR="Blue"]**CANNOT DETERMINE ETHERNET ADRESS FOR PROXY ARP**[/COLOR]
Any idea??

THNAKS AGAIN

---

### Post by kacheng on 2007-07-24
There are many ways to setup a VPN and it looks as though your university utilizes proxy servers too.
Do you have specific instructions from your university IT department as to how to configure your VPN?

---

### Post by wraithe on 2007-07-24
well at least you can use pptpconfig...lol...

u may have to add a proxy to your browser, and ensure you have set encryption to mppe or what ever u r using...u can get all the info out of win-xp vpn as it basicly has the same settings just in diff places...when u go into your vpn properties setting in win-xp, just goto details and copy it all down, it should give you the basic vpn settings there, then  go and do your proxy settings...


next is good luck and all should be ok...
:popcorn:

---

### Post by wraithe on 2007-07-24
plus, forgot to add, you need to add a proxy server address for vpn authentication...."arp"

---

