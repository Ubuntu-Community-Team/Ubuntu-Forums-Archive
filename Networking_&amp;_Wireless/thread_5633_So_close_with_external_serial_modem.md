---
title: "So close with external serial modem"
date: 2004-11-20
forum: Networking &amp; Wireless
---

### Post by dishbert on 2004-11-20
I bought a Diamond SupraExpress 56 K Pro serial modem specifically to get into Linux.  

I managed to get it going with wvdial in Suse 9.1 (and with XP).  I replaced Suse with Ubuntu and can get it to dial OK using ppp and modem lights (no luck with the gnome network gui), but I can't get the browser to connect to the web.  Apt-get update also stalls, and the mail program also fails.  Modem lights shows a connection, but never shows any bytes sent or received.

I can hear the modem dialing, and the "handshake".  The same led's on the box that are lit when it is working on XP are also lit under Ubuntu.  The user name and password seem to be OK, because when I change pppconfig to an incorrect password,  ppp disconects after the handshake, but does not when I have the correct password.

There is no modem directory in the /dev directory, so I made one. Do I need to create a link to my modem which is on ttyS0?  Do I need to edit something in init.d?

---

### Post by dishbert on 2004-11-20
I've checked the usage log at my ISP's web site, and it records my ppp attempts, so it seems that I am indeed connecting with their server.

However, now that I read the help section of the Modem Lights app, I see that the lights that indicate a completed connection only show for a split second after the dial-up,  so that would indicate that I'm not connected.

Stranger and stranger.

---

### Post by dishbert on 2004-11-23
I got it working, but I have no idea what I did correctly.  

I reinstalled Ubuntu, left the Gnome GUI alone, and used pppconfig instead.  It still didn't seem to work, but I pinged my ISP, got a response, and everything's been hunky-dory since.

As they say, all's well that ends well.

---

### Post by alcibiades on 2004-11-26
I am having a similar problem.  Open terminal, startup wvdial, and it connects and gets dns information and writes it to etc/resolv.conf.  I can ping the nameserver.  However, I can't access anything through the browser.

I also cannot for the life of me figure out how to open a dialup connection not using the terminal window, and having opened it, cannot figure out how to take it down again without turning off the modem.   I tried creating an application link with the path to wvdial, but it does nothing.

I also note that trying to activate through the networking panel is problematic.  It does dial out and make the connection, but the connection is similarly unusable, and the check mark does not appear to stick in ppp0.

My main machine is Mandrake this is another person's machine - how simple it is to manage dialup connections there using kppp and the little control panels.  I can't expect my user to open terminal windows.....  Well, I can expect, but she won't!

Anyone have any ideas?


alcibiades

---

### Post by az on 2004-11-26
al,

You can always try
sudo pppconfig
and then sudo pon to connect
and sudo poff to disconnect

In pppconfig, add your user to the dip group so that you can drop the sudo

Then, add the ModemLights applet to your panel.  It uses pon and poff out of the box.




Stop calling your wife user.  Mine hates that.

---

### Post by alcibiades on 2004-11-27
Thanks for the advice on ppp.  If anyone else is reading this looking for an answer, running pppconfig is not enough - you then have to edit the default provider file, unless you pass the ISP name.  Having done this, the modem and connection part works fine.

However, dns still doesn't work.  I can't figure this out at all.  /etc/resolv.conf is read enabled.  It has the right entries in.  

It must be something totally obvious, but what am I missing?

Al

---

### Post by alcibiades on 2004-11-27
From extensive reading, it seems that the cause of this problem is unknown, but the solution is to install resolvconf, pump and dnsmasq.  I'm more than willing.  The problem is that I can't connect to the net from the machine in question - Synaptic doesn't work over the connection.  So I have downloaded them from another machine.  Now I can't figure out how to install the stuff from a CD or the hard drive.  Is there a way?

Al

---

### Post by alcibiades on 2004-11-28
After more research, I got resolvconf in and working, though not the other stuff.  It made things worse, there was now no way to get the right DNS entries into etc/resolv.conf.  So I uninstalled it, and then redid the physical connections.  The modem is now connected through a router, and not directly through the PC.  Now DNS works fine.  Yet, I have not changed the DNS settings.  This is more and more baffling.  As a workaround OK, and it lets one use Synaptic, but setting up and taking down connections are still problematic - you have to do it through a browser interface.

Starting to think the answer is another try at Mandrake....

Al

---

### Post by dishbert on 2004-12-01
I had much the same problem:  I have to "disable" my network connection in order to access the web through my dial-up modem.  Otherwise, the modem squeeks and hums, says it's connected (it is), but the browser won't connect.  

This is a pain because you have to remember to "disable" the network card after every boot, or delete it.  There must be a setting to enable the dial-up connection and still use the network card, but I have no idea what it might be.

I also ended up using pppconf to set up my modem, and then I added the Modem Lights app to the top panel, which works just fine.

How did you connect your modem through your router?  I thought the phone and Cat 5 connectors were incompatible.

---

### Post by brentroos on 2006-04-12
*

---

