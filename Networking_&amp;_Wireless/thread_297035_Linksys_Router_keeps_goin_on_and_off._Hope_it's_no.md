---
title: "Linksys Router keeps goin on and off. Hope it's not because of Ubuntu plz help"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by Epperly on 2006-11-10
I'm on the internet and every once in a while my internet'll just stop working. I have to unplug the router and plug it back in, and sometimes I have to go to system monitor deactivate and activate.

So, I can't tell if this is happening because of the Linksys or because of the Linksys and Ubuntu. It started happening right after I got Ubuntu and wireless working on my laptop.
The way I can tell if my internet goes off is that in the system monitor the received packets will stop going up(besides the fact that the internet won't work, ha)

I have a BEFW11S4 version 4 Linksys router and Ubuntu 6.06 on both computers.
Please help me! This is a *real* pain.

---

### Post by PisstMSTRCHIEF on 2006-11-10
Do you have another operating system to test your theory?

---

### Post by Epperly on 2006-11-10
Nope I recently did away with Windows on my PC, switching between GUI's caused more problems(HD problems).

---

### Post by PisstMSTRCHIEF on 2006-11-10
It seems unrelated, the router might just be on its last lags. 

Is the router dusty or getting hot?

---

### Post by Epperly on 2006-11-10
It is dusty because I don't clean it hah, but it isn't hot.
I didn't know routers get "last legs" :(
But it's not hot, though...
I've called Linksys and they changed some setup settings and it made it a little faster and stays connected longer... but it does still go off sometimes. It is kinda old though I think, at least a year.
Also the firmware is up to date.

---

### Post by PisstMSTRCHIEF on 2006-11-10
One of my routers (I thought) was dieing, so I got a new one (WRTSL54GS). 

With the old one I put DD-WRT on it just for fun and it started working! 
I then did the same for the new one. :mrgreen:

---

### Post by PisstMSTRCHIEF on 2006-11-10
Just something to try:

[http://dd-wrt.com/dd-wrtv2/index.php](http://dd-wrt.com/dd-wrtv2/index.php)

look at the wiki and ask on the forums if you run into trouble.

---

### Post by Epperly on 2006-11-10
um, what is that? ha
nvm saw the Wiki.
Is it safe? what is the difference between that and the oem firmware?
and I install that to my PC?

---

### Post by PisstMSTRCHIEF on 2006-11-10
You install it on the router.

Yes it is safe.

It should make your router run more efficiently.

If you like Linux you'll love this!

---

### Post by PisstMSTRCHIEF on 2006-11-10
Oh! make sure you know your router version! v5 & v6 are hard all others are easy.

---

### Post by Epperly on 2006-11-10
How do I install it? it's v4 router

---

### Post by dannyboy79 on 2006-11-10
he pointed you to the forums of the firmware, that's where you'll get the most help.

---

### Post by FrodoB on 2006-11-10
You can only get new firmware from Linksys as you have BEFW11S4 version 4 which I also have.  Go to the Linksys web site and make sure that you have the latest version of firmware.

[http://www.linksys.com/servlet/Satellite?c=L_Content_C1&childpagename=US%2FLayout&cid=1115416835852&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Content_C1&childpagename=US%2FLayout&cid=1115416835852&pagename=Linksys%2FCommon%2FVisitorWrapper)

When you log into your router in the upper right hand corner you will see the latest firmware version, something like this:

Firmware Version: 1.52.02 


The latest BEFW11S4 ver 4 firmware is: 1.52.02

Release notes: Note item 18. Fixed wireless client compatibility issues.

1.52.02		Apr 7,2005	1. Added Internet port Speed and Dulex option
				2. Added DDNS & TZO Dynamic DNS.
				3. Modify dynamic routing UI.
				4. Speed up FTP throughput in PPTP and L2TP mode.	
				6. Fixed Multicast over PPPoE issue.
				7. Added Lazy WDS support (does not support WPA security mode).
				8. Fixed DHCP client always showing lease time at 2 days issue.
				9. Fixed MTU/MRU issue.
				10. Fixed Long passphrase that will crash the Router.
				11. Fixed Internet Connectivity issues for PPPoE, DHCP, and PPTP
			    	    Connection type.
				12. Fixed Firmware upgrade problem through the web browswer.
				13. Updated library to fix bugs below:
				    - When a Deauthentication frame received 
	        		      from an associated STA but with a BSSID 
				      in the frame different from AP's, AP
		                      would still accept it.
            			    - When LAN-PC sends a DHCP-DISCOVER, AP
		                      doesn't forward the DHCP-OFFER sent 
                                      by DHCP-Server.
				14. Fixed L2TP bug
				15. Fixed auto connection (PPTP or PPPoE) when filtered by IP or MAC.
			            it should not allow user to ping out and automatically connect to
				    the Internet.  
				16. Modified passphrase length to 31 characters.
				17. Solved Heart Beat issue.
			 	18. Fixed wireless client compatibility issues.

---

### Post by Epperly on 2006-11-11
Yes BEFW11S4 is not compatible with the DD firmware thing. Frodo I've already had the latest 1.52.02 firmware for a long time.

---

### Post by FrodoB on 2006-11-11
Sorry to hear that, it actually made a big difference in mine.

Good Hunting.

---

### Post by Epperly on 2006-11-12
Should I upgrade to a Wireless-G WRT54G router?
Or maybe WRT54GS router with speedbooster?

Also what is the WRT54GL? I couldn't find the difference between that and the 54G..

---

### Post by agntsmyth on 2007-11-27
The WRT54GL is made for the DD-wrt firmware as i understand it doenst ship with it but the switch is made to be very easy. the plain 54G is version 5 and until i read this post I thought it wasnt possible to put the DD-WRT firmware on a v5 WRT54G. I also think i read that the WRT54GL has more flash so you can fiddle with the router functionality a little more. The WRT54GS with speed boost requires you to also purchase special adapters otherwise you wont experience faster speeds. If you want to get the WRT54GS you might as well go all out and make a real speed difference by getting your self an N router

---

