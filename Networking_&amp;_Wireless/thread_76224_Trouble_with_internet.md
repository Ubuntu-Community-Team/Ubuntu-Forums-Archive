---
title: "Trouble with internet"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by whythehellcantilogon on 2005-10-14
Hi, today I brought my computer to my dad's store to download and install breezy which went just fine. (downloaded using his laptop with windows). I am now trying to connect to the internet on my computer but have never set up a high speed connection so I am a little fuzzy on what to do.

I tried setting it up in the network settings but can't seem to make it go. Then I tried using pppoeconf and it started scanning the interfaces but I got an error. 

Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not resond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.

Also I popped in my windows hd and I cant connect under that either so I dont think it is because of ubuntu, any ideas of what I can do to correct this problem?

Erik

---

### Post by mips on 2005-10-15
whythehelldoyougiveissolittleinfo ?

Define high speed, modem, ISDN, ADSL, CABLE, T1, Fiber etc ?
What hardware (CPE) are you using for your connection, Make & Model ?
Does it use USB or Ethernet ?
Who is your ISP ?

---

### Post by whythehellcantilogon on 2005-10-15
Cable
It is on an ecs p4vmm2 V3.2 motherboard
ethernet
comcast

sorry

---

### Post by mips on 2005-10-16
Hi,

By CPE I ment modem brand/model but I'm going to assume you use a product supplied by comcast.

There is no need to try and run PPPoE.

Simply just configure your PC's LAN card TCP/IP settings to receive an IP address via DHCP and Auto DNS.

Nothing more should be required.

[http://www.comcast.com/Support/Corp1/FAQ/FaqDetail_2539.html](http://www.comcast.com/Support/Corp1/FAQ/FaqDetail_2539.html)
[http://www.comcast.com/Support/FaqResults.asp?SearchHelp=Linux&x=6&y=8](http://www.comcast.com/Support/FaqResults.asp?SearchHelp=Linux&x=6&y=8)

---

### Post by mips on 2005-10-16
Please look at this, looks like you have to register with a proxy server before you can do anything.

[http://www.tiger-marmalade.com/~james/journal.php?cms=568](http://www.tiger-marmalade.com/~james/journal.php?cms=568)

---

### Post by mips on 2005-10-16
And incase you are wondering about email...     [http://www.comcast.net/help/faq/index.jsp?faq=EmailMozilla17473](http://www.comcast.net/help/faq/index.jsp?faq=EmailMozilla17473)

You can always call Comcast to confirm the DHCP part & Proxy story.

---

### Post by breakthestate on 2005-10-16
I use comcast and never had to do anything with a proxy.  I assume you have the cable modem hooked up?  

Start by telling me what happens after that. Does the line go from the cable modem to a router and then to your computer; or, does it just go from the modem to your computer? 

If you are using a router, you need to make sure it is setup to use DHCP.  I assume that it is.

Open up the /etc/network/interfaces file and copy its contents in here.  That will tell me more.

---

### Post by Deathcon_1 on 2005-10-16
if you're behind a router that can make a huge difference.  the only things that would work are DHCP, manually setting a Static IP and having the router assign yo a static IP based on your MAC address. 

Also, its possible that you have a faulty highspeed modem; call up comcast and ask them to do a remote check on the modem (if the do that?)

---

### Post by mips on 2005-10-17
Did you come right ?

---

### Post by whythehellcantilogon on 2005-10-17
hey, thanks for the sugguestions. I am not currently at that location, but the next time I go down there I will try them out and let you know how they go. 

There is no router there.
The modem is hooked up and works with my laptop so that should be fine.
I will check my /etc/network/interfaces when I get time away from school.


The modem is a motorola surfboard and I think the model is sb5100 but I am not sure on that.

Again, thanks

Erik

---

### Post by Randux on 2006-02-01
It sounds like everybody with cable modems is having problems???

---

