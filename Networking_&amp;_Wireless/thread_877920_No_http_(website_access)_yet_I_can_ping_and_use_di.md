---
title: "No http (website access) yet I can ping and use dig"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by Enicomb on 2008-08-02
Ok So I just installed Kubuntu 8.04 (Hardy Heron) and it refuses to connect to the web.

I can on the other hand ping say bbc.co.uk or google.com and get a 100% success, I can also use the dig command and I get the correct response. I can even ping my gateway and connect to a network share (and transfer files about) so I know it's not a problem with the actual settings or driver for my NIC.

However I cannnot view any web pages using either Konqueror or Firefox 3.0.1. 

I've been searching on my XP laptop for hours now and tried a couple of 'fixes' like disabling ipv6 both globally and in Firefox, yet still nothing. It stinks to me of a firewall problem but I don't believe I have one installed and as far as I can tell iptables is not running.

I never had these problems with Fedora or XP or even Vista. To say it's frustrating is an understatement. 

Can anyone help?

---

### Post by Enicomb on 2008-08-02
Oh and the Updater recognises there's an update to install, but won't/can't download it

---

### Post by bogdanbiv on 2008-08-02
Try removing knetworkmanager with your package manager or type this in a console ```
sudo apt-get remove knetworkmanager
```. Then try using Konqueror. Google something and make sure the page doesn't load from cache.

If Konqueror works and Firefox doesn't come back here. Or you can go to the File menu in Firefox and check and uncheck 'Work Offline' option a few times (2-3 times does the trick for me). 

Please come back to tell the results.
My problem is/was remarkably similar to yours - it seems there's something wrong with knetworkmanager and PPP connections.
How do you connect to internet?

---

### Post by Enicomb on 2008-08-02
Thank you for your reply.

I connect to the internet over my LAN using a router. I'm connected to it using my XP laptop, so I know there's no issue with the connection :(

I've removed Knetworkmanager (although it wouldn't remove using the terminal; it just kept saying no packeage to remove) but I have removed it using the add/remove program menu instead. I can still ping, etc but I still can't connect to any websites, just rebooting for good measure.......

---

### Post by Enicomb on 2008-08-02
....still nothing although knetworkmanager is definately gone now.

I tried changing from work offline to online a couple of times in Firefox too, still nothing :(

---

### Post by Enicomb on 2008-08-02
Can anyone help?

---

### Post by Enicomb on 2008-08-02
Ok so now I can only connect to mozilla.org but still no other websites.
 
This is utterly stupid.

---

### Post by Enicomb on 2008-08-02
Linux 'just works'?

Not if you use ubuntu

---

