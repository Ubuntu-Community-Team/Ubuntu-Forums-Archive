---
title: "Wireless Instability &amp; Inability to save settings"
date: 2006-09-29
forum: Networking &amp; Wireless
---

### Post by Digicrat on 2006-09-29
The wireless network works perfectly well on my laptop using ndiswrapper, except for a tendency for the system to lock up and its refusal to save connection settings.


Every other time that I use the wireless in linux, the system will lock up (and can only be restored with a hard reset - holding the power button).  It almost always crashes after connecting to a wireless network using the graphical utilities, and can happen anywhere from a few seconds to 10 minutes after a connection is established.  So far, I have not been able to find anything in the system logs.


Another issue, is that the graphical utilities to list available networks and/or automatically connect are not working.  To be precise, I can't use them to see a listing of or connect to a wireless network until **after** I am already connected!


The most annoying issue (next to the system crashing), is that I cannot get the system to save the network settings:
- the wireless configuration utility, as stated above, does not reliably work
- I have tried saving profiles in the network configuration manager.  The problem is that a)it takes a long time to change profiles and has a higher tendency of crashing after this process and b) while this works well for a non-secured network (campus wi-fi) it refuses to save the WEP Key for the home profile.  
- the command line utilities tend to work, but are annoying, particularly when it comes to the WEP-enabled home network.  Connecting to the campus network is also annoying with these utilities as it does not show progress, and dhcp is very slow on the campus wireless.


Any ideas?  Thanks

---

### Post by naily on 2007-01-20
Same issue here on my WEP network at home.
Making matters worse for me is the fact that the network manager keeps crashing.  I check the bug reporter website, and it tells me the bug is fixed, but gives me no clue as to how to fix it....!

I have saved settings in my /etc/network/interfaces file, but when I reboot, it can see the wireless, but not connect to the router.  Now, even when I try manually typing iwconfig settings, it's not connecting.

Please help..!

---

