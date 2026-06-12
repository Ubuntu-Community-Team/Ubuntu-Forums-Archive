---
title: "How to fool the WLAN of my school?"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by amityak on 2008-01-25
Hello All

Kinda newbie here, but managed somehow to get Ubuntu running on my laptop and im very happy with it. Right now im in Berlin learning German and they give a student service of of free WLAN (yeeeey!!) but the only problem it works only with Windows or MAC OS.
They supplied me with a WEP code, an IP and a Port number of their Proxy server. 

How does the router/server knows im under Linux and not under Windozz?? How can I trick it?
im using ubuntu 7.10 under FujitsuSiemens Amilo Pro V2035D

Thanx all , please save me from beeing dependent on windows (:

---

### Post by lswest on 2008-01-25
have you tried connecting to it?  if they want you using a proxy server then they might need software that only runs on windows/mac, but you can probably set it up in linux anyways if that's the case.  Try to connect normally to it though, and, they should have, an article on how to connect in windows, which might be worth having a look at if they want some VPN software, or specific proxies.  Otherwise it should work fine...they might just not mention Linux because they didn't realize people used it :P

---

### Post by amityak on 2008-01-25
hey thanks for the post

well, the way i did it with windows was simply put the proxy definitions into firefox and then i worked.
i did exactly the same in ubuntus firefox and it didnt work.
should a VPN client solve the problem ?
the dudes here in the office are complete jurks and know nothing about it ):

---

### Post by lswest on 2008-01-25
nah, i don't think VPN would solve it, but some schools use VPN clients, and i wasn't sure if yours did too.  You could try inputting the proxy information into the gnome proxy, under system-->preferences-->network proxy  and otherwise, can you connect to the WLAN? if you can, then the only problem is getting the proxy sorted.

---

### Post by amityak on 2008-01-25
ill try that, thanks !

---

### Post by salazar on 2008-01-25
if it is a WLAN school, probably ther's a  windows domain ?
user permissionas! your linux user is the same of the windows test machine?

if it is a WLAN school and a  proxy, Isa Server ?
isa server normaly needs an application on the client, and also user permissions!

try to find router IP and use it as your gateway.

---

### Post by ugm6hr on 2008-01-26
> **amityak said:**
> They supplied me with a WEP code, an IP and a Port number of their Proxy server. 


I presume you want it just for internet (i.e. Firefox), and not to use GAIM / Synaptic etc.  If so, you just need to do as you already have in Firefox network settings (Manual proxy).  You should be able to try the settings in Gnome proxy, but they may not work, since most network managers will only allow "http" proxy use (at least at my work).

However, the problem is that you haven't yet connected to the gateway (I presume).

If they supplied you with an IP, then you have a "fixed IP".  Importantly, Network Manager (the default wifi roaming app in Ubuntu) cannot cope with fixed IP addresses (or it couldn't in Feisty, and I think also in Gutsy).

So, you will have to cope without roaming if you want to continue to use the default setup.

Your options:
1. Manual configuration:
System-> Administration-> Network
In Connections tab: Click Wireless connection then click Properties
Untick Enable roaming mode
Enter the details with Configuration: Static IP selected
2. Use Wicd (roaming app that replaces Network Manager) - see the link below

---

### Post by tekguy on 2008-01-26
> **amityak said:**
> Hello All

Kinda newbie here, but managed somehow to get Ubuntu running on my laptop and im very happy with it. Right now im in Berlin learning German and they give a student service of of free WLAN (yeeeey!!) but the only problem it works only with Windows or MAC OS.
They supplied me with a WEP code, an IP and a Port number of their Proxy server. 

How does the router/server knows im under Linux and not under Windozz?? How can I trick it?
im using ubuntu 7.10 under FujitsuSiemens Amilo Pro V2035D

Thanx all , please save me from beeing dependent on windows (:


The proxy ip and port will get you out on the Internet but the first thing that needs to be done is with that WEP key. If your wireless is installed and running you should have a network manager icon near your clock. You should be able to see available wireless networks and select the one you want to connect to. It should then prompt you for your wep key. Enter your wep key. Then you should be connected. I'm not at my linux box right now to be able to tell you exactly where everything is. So hopefully I remembered that correctly.

---

