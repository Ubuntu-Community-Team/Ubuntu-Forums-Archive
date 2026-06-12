---
title: "DHCP Broadcast Flag disable?"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by Antioch on 2008-11-18
Hi guys.

I'm using my laptop at my new school. Under Vista I couldn't get the wireless to associate with certain Wireless APs until I disabled Vista's DHCP broadcast flag (as described here [http://support.microsoft.com/kb/928233/EN-US/](http://support.microsoft.com/kb/928233/EN-US/)). After that I was able to associate with the APs fine.

Then I installed Intrepid. Now I cannot associate with the same troublesome APs. I believe the problem is the same as I can connect to my wireless at home. Can anyone tell me how I can disable the BROADCAST flag in my DHCP client? I've googled and come up short.

Thank you, I really appreciate the help.

---

### Post by iponeverything on 2008-11-18
The reason that vista's dhcp client required a hack to get it to work with some dhcp servers is because their client implantation was broken. 

dhclient does not have the option to  change the broadcast flag, because it does the correct thing when it does a dhcp broadcast. 

Just a wild guess.. but it sounds good ;)

---

### Post by Antioch on 2008-11-18
Hmm. Then I wonder why I am unable to connect to that same AP?

I can connect to several other ones without a problem - but that specific one is a trouble maker.

---

