---
title: "Automatic Setup of Wireless Security Possible?"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by GregA on 2008-03-10
Have just installed a Netgear Wireless Router, on a HP desktop originally just hooked to the internet via a standard cable-modem.   Now, I have the cable modem linked to the router using an ethernet cable.  I have no issues at all connecting to the web, or connecting my wifes Lenovo Laptop to the Netgear wireless signal.

But I want to get WPA-PSK security setup as soon as possible.  Let me pose a few basic questions to see if I understand what I need to:

1).   I assume my Desktop is still secure (as it was before connecting the wireless router) because this is still essentially a "wired" connection (i.e., I'm not getting the internet "from" a wireless signal, but from the ethernet cable connecting the cable-modem to the router.
Is this assumption correct?  (I do have the Firestarter front-end to iptables set up).  In other words, if someone outside my home connects to my Netgear wireless, can they somehow see my PC, and it's drives and files?

2).   I also "assume" again, that the security risk is when I connect with the laptop, to the wireless router.   Someone could scan/read the transmission, and possibly decode any sensitive information.   Is this correct?   Further, could that someone, also then access the laptop's drives and files?   I do have Firestarter enabled also on the laptop.

3).   IF, I don't send any sensitive info over this connection (like buy or sell things), is the basic firewall setup sufficient to prevent hackers from accessing the laptop.   I guess the key question is, can any of these 2 computers (desktop and laptop) be comprimised if someone connects to the router?

4).   The PDF manual for the Netgear router, makes it seem relatively simple to enable WPA-PSK by accessing the router setup site, and completing a basic "setup" window, where the SSID is entered, the region is updated, and the radial button for WPA-PSK is selected, and last, the passphrase is entered.   It seems pretty straightforward, almost "too simple" . . . . . can this be all there is to it?  

5).   Again, my next "assumption" is that when hooking up via the laptop, after setup of the WPA-PSK on the desktop, will I be prompted at connect time, for the passphrase (if so, is WPA-Supplicant doing that)?   Or do I need to do something else, like login to the same Netgear setup site, and do the same thing for the laptop as previously done on the desktop?   Or do other manual configs such as listed in the lengthy tutorials?

By the way, I know the old-saying we've all heard about "assuming" - - - so, am I wishing for too much, am I in the real-world of wireless security?   I looked thru some of the wireless/security instructions here in the Ubuntu forums, and my initial thought was . . . . oh my gosh . . . what Joe or Jan AverageUser, would go thru all those steps as a default to getting wireless security running . . . . . or is all the detail provided because there are so many potential issues, and the instructions can be used then, to fix those failures???

Maybe the best way to find out is to try the Netgear website setup, but I wish I knew if I can do a "fall-back" if the laptop won't connect after security setup . . . ???

Any answers to the above or insights is much appreciated.

Greg

---

### Post by kevdog on 2008-03-11
Just a few points

1. The wired connection is safe
2. If you dont have file sharing between the two computers - then networking is safe -- filesharing would be something like samba or cfs
3. Use WPA - the setup you about the password, etc, is really that simple.
4. You dont have to type the password everytime if you set it up appropriately.

---

### Post by GregA on 2008-03-11
Thanks Kevdog!  I appreciate your help - - I was "dazed and confused" after reading thru some of the excellent wireless & security guides.  Not because the instructions were hard to follow, but because I can't clearly envision the situations that require those steps.  

I think by fate or luck I must have chosen hardware that works very well with Ubuntu.  Even my Compaq v2414 laptop with broadcom modem was setup easily using the proprietary setup tool.  I especially chose the Netgear router (originally I was going to get a Linksys), because it was the only commercial packgage that clearly stated on the box that Linux and OS-X were are supported.

Well, now to give it a go!


Greg
Omaha

---

### Post by BLTicklemonster on 2008-07-01
I have a wireless linksys on the way via ups and want to be sure I set it up correctly, so what is the deal with wpa, or will I just find out when I hook the router up?

I'll use the ports for the most part, but I have a laptop I'd like to be able to use from time to time, and it would be nice to have a wireless router sitting around. But I don't want to just bend over and hike my skirt if you know what I mean. ...not that I wear a skirt, you know. And if I did, I certainly wouldn't go bending over hiking it. 

Koff koff, anyway, moving right along, so being new to this wireless stuff, at what point will I need to concern myself with wpa, and how shall I go about it?

---

