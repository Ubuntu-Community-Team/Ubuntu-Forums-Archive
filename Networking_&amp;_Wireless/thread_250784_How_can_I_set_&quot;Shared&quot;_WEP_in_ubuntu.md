---
title: "How can I set &quot;Shared&quot; WEP in ubuntu?"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by Zorander on 2006-09-04
Hi there,

I'm a new ubuntu user, and I cant get my wireless to work.  My PCI seems to be working fine automatically, the problem is getting the router to authorize me and give me an IP.  I can connect no problem in windows, so I know my WEP key is correct.  However, in Windows it was required that I set it to be a "Shared" connection, not Open, before anything would work.  I do not see options for this in my Ubuntu network setup, so I think this may be the problem?   I believe the physical connection to the router is fine. 


Thank you so much for the help!

Zor

---

### Post by x64Jimbo on 2006-09-04
Go into your router and change the setting to "open" in your wireless security settings. This should work fine.

---

### Post by Zorander on 2006-09-04
Thanks for the response but I actually do not have access to the router, it is being provided to me by my landlord and the setting will have to remain "shared".  Surely there must be a way to set this in Linux?

---

### Post by tylerjames on 2006-09-04
yes, i would love it if someone could tell me how to do this as well.... i've been using the internet at my girlfriend's place and it works fine in windows when set to Shared.... there must be some way

---

### Post by x64Jimbo on 2006-09-04
It's an option in iwconfig. You add it with this option:
> iwconfig [interface] essid [ssid] key [key] restricted  but I don't know how to do it through the Network Manager
Just reset the router that your landlord set up and make up your own key. Tell him/her that you can't expect your session to be secure if there are others out there (ex-tenents) who know your key.

---

### Post by tylerjames on 2006-09-06
hmm.... still seem to be having difficulty

when you're inputting the hex key do you need to include the hyphens? ie. fd-28-c4..... or is it just fd28c4... ?

---

### Post by x64Jimbo on 2006-09-07
no hyphens. make sure that you send the interface for a dhcp renew after you apply those settings. 
sudo dhclient <interface>

---

