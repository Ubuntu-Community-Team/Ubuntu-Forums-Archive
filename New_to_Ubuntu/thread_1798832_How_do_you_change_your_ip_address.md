---
title: "How do you change your ip address?"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-07-06
Is it even possible?

---

### Post by Perkins on 2011-07-06
Of course it is.  The terminal command is ifconfig.  To make it automatic on startup, look in /etc/network/interfaces.  Or you can right-click on the network manager icon and choose "edit connections."

---

### Post by doppel.ganger on 2011-07-06
I'm sorry, I don't quite understand you.

---

### Post by Paqman on 2011-07-06
Do you mean your external IP address or your internal one? 

Your external address (ie: your address on the internet) is assigned to you by your ISP. If you're a home user they most likely change this occasionally.

Your internal IP (ie: your address on your home network) is assigned by your router. You can set the router to give a machine a specific IP. By default most will just assign on when the machine is switched on.

---

### Post by doppel.ganger on 2011-07-06
The one that is xx.xxx.xx.xxx not xxx.xxx.xxx.xxx. I THINK the external.

---

### Post by Perkins on 2011-07-06
Open a terminal, and type "man ifconfig"  That will give you instructions for using the terminal program for configuring your ip address, network mask, and other, associated parameters.

"man interfaces" will give you instructions for making your changes permanent on bootup.

If you're scared of the terminal, one of the icons in your system notification area is the network manager.  It's the one that you click on to connect to a wireless network, and generally looks like either a network cable, or a signal-strength meter.  If you right click on it and choose "edit connections" you can set the parameters for your wired network connection.

---

### Post by courage1919 on 2011-07-06
It's easy. IF you have a dynamic IP. A dynamic IP changes every time you restart your modem or router. A static IP is an IP address that stays the same and doesn't change every time you restart your modem or router. I have a dynamic IP. Can you restart your modem or router right now, come back on the forum and tell me if your IP changed or not? If not, it's static for sure. But there is a way to change a static IP.

---

### Post by Perkins on 2011-07-06
> **doppel.ganger said:**
> The one that is xx.xxx.xx.xxx not xxx.xxx.xxx.xxx. I THINK the external.


Either one could conform to that mask depending on how things are set up.  Perhaps a better description of the problem you are trying to correct would help.

---

### Post by moonman1001 on 2011-07-06
Depending on your reason for changing your IP address, you may want to mask it with a proxy or VPN instead. If this is not suitable, you may also want to try calling your ISP and asking them to give you a new address.

---

### Post by doppel.ganger on 2011-07-06
Thank you perkins, but even with your gui instructions, I'm lost. Say I wanted my new ip to be 12.123.12.123. Can you give me step-by-step instructions?

---

### Post by moonman1001 on 2011-07-06
You cannot simply change your external IP address to any one you wish.  Your ISP has reserved addresses, and one is chosen and assigned to you  when you connect.

---

### Post by doppel.ganger on 2011-07-06
I was banned from an irc for flooding, which I guess I was doing without realizing it. I use irssi at irc.twit.tv on channel #twitlive. I figured I would be able to get back in if I changed my ip address. Here is what irssi gave me:

19:52 -!- Irssi: Looking up irc.twit.tv
19:52 -!- Irssi: Connecting to irc.twit.tv [174.37.23.130] port 6667
19:52 -!- Irssi: Connection to irc.twit.tv established
19:52 !irc.twit.tv *** Looking up your hostname...
19:52 !irc.twit.tv *** Found your hostname (WS-ESR2-xx-xxx-xx-xxx.xxxxx.net) -- 
          cached
19:52 !irc.twit.tv *** You're banned!
19:52 -!- ERROR Closing link (lewis@WS-ESR2-xx-xxx-xx-xx.xxxxx.net) [K-Lined: 
          session flooding irc server]
19:52 -!- Irssi: Connection lost to irc.twit.tv

The x's are my ip and xxxxx.net is the .net part.

---

### Post by overdrank on 2011-07-06
Sorry for your issues but the forums can not support circumventing restrictions place on your account. Thread closed.

---

