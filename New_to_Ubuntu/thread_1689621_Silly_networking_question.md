---
title: "Silly networking question"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Hilarie on 2011-02-17
I switched to ubuntu 10.10 a couple of weeks ago, and have been having a great time exploring,

Next week I will be getting my desktops in the mail (Finally)

And here is what I wanted to do.

I live in an apartment building with shared wifi for our internet and it's patchy throughout the apartment

What I was hoping to do, was to install ubuntu 10.10 Desktop Edition on Desktop one, cannibalize the wifi adapter on desktop 2, put in in desktop 1, and have desktop 1 act as a server type thing broadcast wifi that my laptop(s) could then connect to for a more stable wifi connection throughout my apartment, and hopefully eventually get a proxycache and a firewall set up on the desktop etc

Is it possible to have 2 WIFI NIC's in ubuntu desktop edition

Is it possible to bridge the connection between those's wifi cards, I.E. Share the internet connection

Is it possible to go beyond just bridging it to put a firewall and and other services in line

What is a DHCP server and how do I get one?

Sorry for all the questions

---

### Post by taseedorf on 2011-02-17
Is it possible to have 2 WIFI NIC's in ubuntu desktop edition

Yes, it is.

Is it possible to bridge the connection between those's wifi cards, I.E. Share the internet connection

Yes, it is.

Is it possible to go beyond just bridging it to put a firewall and and other services in line

yes, it is.

What is a DHCP server and how do I get one?

DHCP server dishes out IP addresses....however,  your set up wont work...the wireless signal will probably still be weak.

---

### Post by Hilarie on 2011-02-17
Behind my front door where I leave my laptop overnight for large downloads will be the new home for it :)

What kind of level of techsavvyness will I need for this, will there be alot of commandline stuff?, I saw firestarter has a built in DHCP server, so would it be as simple as messing around in there to get basic configuration started?

---

### Post by YesWeCan on 2011-02-17
I think you can configure Ubuntu to share the internet connection, which is accessed via wifi A, with wifi B.  See [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

All devices on your network have to have a unique IP address. Simplifying, dhcp assigns an IP address to a newly connected client. A client doesnt have to get its IP this way; instead it can decide it for itself and this is called a static IP address. Dhcp also tells it what IP addresses to use to find DNS servers. The latter are usually provided by your ISP. Dynamic Name Servers translate textual internet addresses into IP addresses.

Everything on the internet and your local network operates using IP addresses. Technically, it operates using hardware addresses like MAC addresses but you don't usually need to know this. So when you use a browser and put in something like "www.google.com" the browser has to find out what the corresponding IP address is before it can send a request to Google's server. It does this by asking a DNS server what the IP address is. BTW you can acces google by putting its IP address in your browser rather that its text url.

---

### Post by taseedorf on 2011-02-17
It might be difficult to do if you don't have a lot of tech savvy.  I'd just pay for internet access, but this is what you would need to do.

On one computer install two WIFI nics. (One wifi and one wired would be better) Bridge the two connections together, (one connection would NEED to be in ad-hoc mode using two wireless devices.  Have one wifi nic pick up the foreign wifi, have the other wifi nic bridged with it in ad-hoc mod and set up a connection to your other box with it.

DHCP will be installed by default in ubuntu and will accept DHCP information from the original wifi signal and give it an address.  One your internal pc's, just use a static ip.

This is VERY...cumbersome, to say the least but should be possible.

I cannot write an entire guide...take too much time tonight..but it wouldn't take ALOT of time.

(wifisignal)<---------->[(wifinic1) ---bridge--- (wifinic2adhoc)]----------->(other pc)


EDIT: you would not need to have a firewall at the brirdge or a proxy cache....you COULD use Squid if you wanted to cache webpages...but, it's probably not needed.  a firewall on your desktop should be enough... however, if you want to be anal you can have one guarding the bridged connection.

---

