---
title: "Headless Encrypted File Server Setup"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by noblunts on 2008-07-17
I'm setting up a headless file server on my home network. Its running NX for administration and Samba for windows shares. 

Specs
P3 Coppermine 1.0ghz
256MB PC133
450+ GB HDD Space (i know, not much)
10/100Lan
HP Travan Tape (wont work, grrr!)


My goals are. 
1. No Keyboard/Mouse/Monitor **-SUCCESS!-**
   Works with NX. Does have problems accessing certain things 
   like network control panel in Gnome. Won't let me unlock but  
   otherwise ok.

2. SAMBA **-SUCCESS!-**
   Works except for WINS, have to connect to the 
   server by IP. I think I firewalled it out. I also have to use 
   a different l/p for shares, my server 2003 system account is 
   root :)

3. Remote Wakeup/Shutdown when idle  **-SOMEWHAT-**
   WakeOnLan works (finally!). Have not looked into shutdown at 
   idle and things like that yet.

4. Encryption **[COLOR="Red"]-FAIL!-[/COLOR]**
   I want to set the server to only allow the SMB connection 
   over encryption, even on the local intranet. I don't want to
   run any extra software on my Server 2003 machine to connect
   so I'm stuck with microsoft supported things. Originally 
   wanted SSH but its not supported.

[COLOR="Red"]**So what should I use?**
IPsec? L2tp? Poptop? Openswan? ipsectools? How do I set them up? 

[/COLOR]

---

