---
title: "[SOLVED] Bluetooth DUN works on Vista need help config Cell1"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by volkswagner on 2007-10-09
With help following this thread and the how to mentioned

[http://ubuntuforums.org/showthread.php?t=464613&highlight=bluetooth+dun]("http://ubuntuforums.org/showthread.php?t=464613&highlight=bluetooth+dun")

My phone Nokia 6126 Cellular One (Dobson) is paired and asks to allow dialup when i 

```
pon cingular
```

I used this to keep everything same as thread. 

What can I check in vista to get my config files correct for Ubuntu?

changes these   /etc/ppp/peers/cingular     /etc/chatscripts/cingular ? Mine are copied from byunique's thread

I was unsuccessful in configuring pppconfig because I did not know what to select for Dhcp, static, etc.....

thanks in advance

---

### Post by volkswagner on 2007-10-10
I am connected to internet through Nokia 6126 now on Vista OS.  I see the modem is connecting through comm port 2, this may help.

Anything else I check while connected.  Perhaps answers to DHCP settings.  The phone itself does not have any settings to view.

I am connecting through Vista not through the Nokia Suite itself.  I believe to be true anyway.

---

### Post by volkswagner on 2007-10-10
Here is what I can dig up in windows vista

In network connections vista claims connected to the phone but internet is x's out but I am clearly connected as writing this.

Vista

Network Connection Details


> Connection-specific DNS Suffix: 
Description: Nokia 6126 Bluetooth Modem (OTA)
Physical Address: 
DHCP Enabled: No
IPv4 IP Address: 166.209.123.112
IPv4 Subnet Mask: 255.255.255.255
IPv4 Default Gateway: 
IPv4 DNS Servers: 12.25.118.5, 12.25.118.10
IPv4 WINS Server: 
NetBIOS over Tcpip Enabled: No




Found this under modem Config

PPP setting
yes enable LCP extensions
yes enable software compression
no  Negotiate Mult-link for for single-link connections

Found this under advanced modem settings

Allow these protocalls
	yes Unencrypted password (PAP)
	yes Challenge Handshake application protocall (CHAP)
	yes Microsoft CHAP version 2 (Ms-chap ver.2)
 	
		EAP not being used

Can I use this info to enter in Ubuntu?
Where? and How?

Thanks,  The BT issues I have is the only time I use MS on my lapptop.

---

### Post by volkswagner on 2007-10-10
Anyone?

Am I asking the wrong question?

Any advice where to Post?

---

### Post by volkswagner on 2007-10-10
Can't anyone offer help to my problem?

Why does a post like this get so much response and mine seem to lay stagnant?

[http://ubuntuforums.org/showthread.php?t=212458&highlight=linuxmint]("http://ubuntuforums.org/showthread.php?t=212458&highlight=linuxmint")

Should I ask why does the squeaky wheel get the grease?
OK now five pages for a rant.  Can someone please tell me what I am doing wrong?

Thanks

Eric

---

### Post by volkswagner on 2007-10-10
well I wish it did not take so long.  I found this thread

[http://ubuntuforums.org/showthread.php?t=536217&highlight=bluetooth+pairing]("http://ubuntuforums.org/showthread.php?t=536217&highlight=bluetooth+pairing")

I followed the above thread and still had problems.  I could not find info on the modem location.  I also did unbind rfcomm0 and and did bind rfcomm0 mymacaddressofphone.  I also did pppconfig and entered some of the info I dug up from windows.

Well it is working, I edited so many things not sure how messed up I made things.  I cant get it to connect via the network icon on desktop I must pon provider.

Is this why nobody wants to help.  I need to research for two days just to get a connection that was plug and play on windows.  I just hope it will get easier in the future.  I am new to linux in the last six mmonths.

---

### Post by Lambert on 2007-10-10
Sorry to see you didn't get help and felt ignored here.

1. We are all just users, giving back a little help where we can.
2. It's a problem or area where many have never tried or used so they can't offer anything. i know i've never tried this and could never offer any help.

Linux will get easier in the future. With companies like Dell, HP, and IBM showing more interest in providing products with gnu/linux installed by default, more improvements will happen.

There are still things that need to be worked out to make this a little easier, support from vendors and major computer companies is a good start.

---

