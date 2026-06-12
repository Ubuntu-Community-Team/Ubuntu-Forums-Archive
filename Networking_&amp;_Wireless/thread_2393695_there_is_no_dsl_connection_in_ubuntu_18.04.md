---
title: "there is no dsl connection in ubuntu 18.04"
date: 2018-06-06
forum: Networking &amp; Wireless
---

### Post by massprog on 2018-06-06
Hi
I want to connect dsl cable internet but there is no dsl connection settings and when I use nm-connection-editor command it adds dsl connection but doesn't show where i can connect to it  ](*,)
what should i do?

---

### Post by TheFu on 2018-06-06
Where I live, DSL is very different from Coax cable connections.

DSL uses a phone  line into a DSL modem. That modem can be a card or a separate box , usually provided by the telephone company.  They might call it a router.   The DSL uses a PPP connection for account authentication.

Coax cable normally uses a DOCSIS modem.  I've **Never** seen one of these as an internal card for a computer.  You can buy your own modem or modem+router or the CATV company provides it (for a monthly rental). DOCSIS modems generally use tftp to get settings from the cable ISP based on the MAC for the account.

If you use an external modem/router, then your PC connects via ethernet (CAT5 cable) to the other box.  As far as Linux is concerned, it is a normal network connection and has ZERO to do with coax or DSL.

**So, if you can clarify your setup, someone might be able to help.  The main information needed would be the company providing service and the general area for that service.  **

Where I live, in Squidbilly-land, Comcast is the provider and because of my network setup, I'm forced to use their cable-modem-router to have a connection to the internet.  If I had a simple connection, I would be able to purchase an approved DOCSIS modem or modem-router and save $8/month rental. But I have a group of static IPs, so that isn't allowed.

---

### Post by massprog on 2018-06-06
I have same as Yours But said it wrong
there is no coax cable I use Ethernet input of laptop and I think it's called Ethernet cable or whatever it is
there is modem and we use output of modem with LAN cables but every one has it's username and password for connecting to internet My networking knowledge is not good sorry for wrong information

---

### Post by TheFu on 2018-06-07
Sorry, I still don't understand.  

My setup doesn't have any logins to the network that any computer knows about.  The MAC address for their modem hardware is used by the cable company to determine which account.

At hotels, there might be something called a "captive portal" which does require a login to access the internet, but all the hotel  websites are allowed without any login.  Running a browser and trying to go anywhere will redirect to the "captive portal".  This is just a normal webpage with login/password/room number.  It could ask for anything like agreeing to terms of service.  After passing the tests of the captive portal, the MAC address for the connected device is added to an allowed-for-internet list inside the router and internet access is provided  for the next 24 hrs. That is a common hotel technique all over the world.

If you can more clearly spell out what is supposed to happen, maybe someone else can help.
* name of the provider
* location of service
* type of modem

---

