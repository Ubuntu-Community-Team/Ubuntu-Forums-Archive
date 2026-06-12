---
title: "Router Reset Lost Server"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by andrewt522 on 2010-04-22
I have a Linksys WRT54G2 router connected to a headless Ubuntu Server 9.10 and my laptop running Ubuntu 10.4.

Everything was working fine with the exception of my inability to access the router's web-based utility.  This posed a problem as I wanted to configure a DNS so I could access my server's FTP from work.  So, I reset the router with the hope that I could reconfigure the router as necessary.  

Good news is, I can finally access the utility.  
Bad news is, my network is useless.  

I have not been able to access the server, which is plugged into the router, in any way.  No NFS, no FTP, no SAMBA, no PuTTY.  It took me the better part of the evening just to get back online. As of this morning, my router was not recognized by my laptop, which leads me to believe that another reset is in order. Currently, my laptop is plugged directly into my DSL modem.

I want to believe that the answer is somewhere online, but I'm afraid I'm over my head.  I understand networking in theory, but I'm overwhelmed by IP addresses, ports, masks, etc.  Also, it is quite possible that I'm not searching the right terms, as I want to believe the answer is relatively simple.

Any help you might provide would be most appreciated.

---

### Post by novelty on 2010-04-22
When you reset your router did you proceed to reconfigure it?  

There is an internet setup and a network setup on the first page of the router configuration utility.  Both of those would need to be configured so your router can 'talk' to your modem and 'talk' to your network.

Depending on your internet modem you may also need to power it down if your are changing between laptop and router connections while attempting to troubleshoot this.  Some modems remember the 'last device' and won't work with a different one until you reboot it.

---

### Post by andrewt522 on 2010-04-22
I thought I did...at least the internet part.  In order to get internet access, I had to change the router's IP from 192.168.1.1 to 192.168.2.1.  I think there might be a better solution which I found [here]("http://blogs.zdnet.com/Ou/?p=840"), which would change my modem's setting from PPPoE to bridged, passing the signal and control to my router.

As for the Server, I'd have to look at the setup page again.  It's possible I was misunderstanding what was in front of me.

---

### Post by kingpoiuy on 2010-04-22
So, you can log into your router's web configuration right? What address are you using to get to it? If it's an IP address; is that IP address on the same subnet as your server? What is the IP of your router versus the IP of your server? Do your computers get their IP address automatically?

If you aren't sure how to check these things let us know.

---

### Post by novelty on 2010-04-22
I don't have any experience with the at&t dsl, so as far as what you need to do with the dsl modem I wouldn't know. 

The number you changed on the linksys would relate to your local network.If you manually assign network card ip's they need to match your router (the first three sets in the ip need to match). If you have your network cards setup to acquire an address automatically you just need to make sure you have DHCP server enabled and the relevant info filled in on the linksys router page.

As a side note (which you may have already figured out) changing the router ip changes how you log in to your web utility. You would log into your web utility using the the new ip you gave it.

After making changes to the router you may want to power down inside out (pc-router-modem), then power up outside in (modem-router-pc).  A pain, but a best practice kind of thing.

---

### Post by andrewt522 on 2010-04-22
Yes, I can log in to the web configuration.  Currently, after reset, it is 192.168.1.1, which is the factory default.  I should note, and as novelty pointed out, I needed to enter 192.168.2.1 in my browser after I changed it to agree with my modem.

My server's IP is 192.168.0.100 and is a static IP.  If I understand my research, my router is not on the same subnet as my server.  Is this correct?

---

### Post by novelty on 2010-04-22
Yes, you need to change the server IP to something like 192.168.2.100.

If I am reading your posts correctly, the ip 192.168.1.1 is no longer a relevant number.

An alternate solution, if your internet connection isn't dependent on your router being 192.168.2.1, you could change the router network IP to 192.168.0.1 to agree with your server.

Edit: To add some info you may or may not have. If you are changing the server network card settings you also need to change the gateway to reflect the "new" ip of your router, 192.168.2.1

---

### Post by andrewt522 on 2010-04-22
Bingo!!!  192.168.0.1 worked like a charm!!!  All is back to normal...I have internet, access to my server, and a new DNS!

Well done Novelty!  Mark this solved!!!

---

