---
title: "Bounty= Blackberry  or ATT WIreless"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by Wharf Rat on 2008-09-18
Getting desperate here.
I live along the Texas Coast - Freeport to be precise.  This is the first i-net access since last week and I am using my wife's EeePC with a ATT USB air card under Windows.

My Thinkpad is only loaded with Ubuntu. I have tried in the past to set up either the ATT card or use the BB as a tethered OR Bluetooth modem. I have yet to achieve this. 

I will pay a bounty to anyone who can walk me through setting up the Blackberry.  (She won't let me keep here Aircard). Terms negotiable.

Components are:
Blackberry Curve 8310 using ATT
Thinkpad T61 loaded with ubuntu Hardy

To date I have installed the Btools and the BB is recognized as a USB storage device and will auto mount using a USB cable.

Using a USB Cable:
Ubuntu sees the BB and will auto mount as a storage device.
Ubuntu  will pick up the Mac address from the BB.
I cannot get the PPP or GPRS script to work.


Using Bluethooth

Bluetooth will connect both devices and share data.
Ubuntu will pick up the BB MAC address.
Again, I cannot get the script to work.

I did download, and attempt to compile the bluetooth scripts from instructions I found on the internet. However, it will hiccup and tell me one of the files for Chat is not found.

If you can assist, please e-mail me 

[email]johnhoss@att.blackberry.net[/email]
Thank you in advance.

BTW
No significant damage to home, family or business.  Especially compared  to those who lost everything just miles up the coast. 
We do not expect power until after 9/22. Phone, Cable - ??
EEPCs are not meant to support my typing fingers.

---

### Post by attle on 2009-01-22
I have exactly the same setup , using bluetooth.

First thing is that the BB can be progrmmed to NOT use the internal gprs modem. This is done by the supplier or IT dep. You can check that under the config, service settings.. somewhere :-)

If you have it : 

sdptool search DUN

should find all bluetooth dial up modems.

sudo gedit /etc/bluetooth/rfcomm.conf

edit with you channel and bt adress

Attached is my /etc/ppp/peers/files..

they are used to start and connect to via pppd

change gprs to include you phonennumber etc..

then use 

sudo pppd call gprs

Hopefully it will work..

---

### Post by DFord425 on 2009-01-22
Have you tried XMBlackBerry?
[http://sourceforge.net/projects/xmblackberry/](http://sourceforge.net/projects/xmblackberry/)

---

### Post by ieee488 on 2009-01-22
I have Sierra Wireless AirCard 860 which with help from search on these forums and elsewhere I have now working in Ubuntu 8.10 (Intrepid Ibex).
I am with AT&T too.

---

### Post by Wharf Rat on 2009-02-01
Thanks all.
I am sorry I just discovered I had missed the posts here.

Yesterday I upgraded to 8.10 and I am having a few issues getting all the tweeks back in place --- without screwing up the new install.  <G>

As soon as I get a little experience with 8.10 I am going to attempt the BB tethered arrangement as well as the ATT aircard.

Yes..  I backed up my data.

---

### Post by kevdog on 2009-02-01
Id take a look at this page first off -- a lot of forum pages and users have had success with this:
[http://www.netdirect.ca/software/packages/barry/](http://www.netdirect.ca/software/packages/barry/)

---

### Post by lazysarah on 2009-02-02
This may be off-topic but does anyone know a food diary software for the [http://www.10facts.com/article/Technology/Mobile-Phones/BlackBerry/BlackBerry-Curve.html]("http://www.10facts.com/article/Technology/Mobile-Phones/BlackBerry/BlackBerry-Curve.html")?

---

