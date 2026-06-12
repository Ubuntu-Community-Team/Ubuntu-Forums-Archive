---
title: "Wireless does not auto connect on startup"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by rraheja on 2008-02-06
Sony Vaio VGN-N130G laptop with Intel wireless B/G adapter.

I setup a wireless connection (no changes to any network file) using WEP 64bit Hex and hidden SSID and it works fine. However, it does not auto-connect on startup again. If I manually click the network manager icon, it suddenly wakes up and then makes a connection. Is there any way to setup auto-connect of the wireless on startup directly from the Network Manager? or do I need additional software like WCID/WiFi Radar for this basic functionality?

Due to the non availability of the network, even my SAMBA shares are not available, and given that my entire music/video collection is on my network drive, it is not automounted and I have to manually do a "sudo mount -a".  In windows, this would auto connect when the network became available and is a huge usability issue.  Any suggestions would be appreciated.

Thanks
-raj

---

### Post by gnicko on 2008-02-15
Unfortunately I have the same problem using WCID...set to automatically connect. I doesn't. Works like a champ when I click on the toolbar icon or otherwise initiate the connection, but does nothing on its own....wish I had a solution for you....:(

---

### Post by NuxIT on 2008-02-15
I was having the same problem for months. I decided to look into it today and found this solution. 
Add this to your /etc/rc.local file

/etc/init.d/networking restart

I only tried one restart after using this option and it worked for me. Give it a try. I'm going to reboot again to make sure.:guitar:

---

