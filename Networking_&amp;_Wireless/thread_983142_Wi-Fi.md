---
title: "Wi-Fi"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by Oli1122 on 2008-11-15
I have finally got my wireless card to work and i don't know how to connect to my router i got to network manager but it isn't detected :confused::confused::confused:

can anyone help plz???????

olly

---

### Post by gvigorus on 2008-11-15
Are you certain your wifi card works? Are you using ndiswrapper?

---

### Post by Oli1122 on 2008-11-15
yes i have it reconises it but wont find any networks 

how do i scan for networks???

my router is a Netgear ADSL modem router DG834GSP???


thankx oli1122

---

### Post by rlzyoner on 2008-11-15
run the command 

iwlist scan

This should run a wireless network scan and return the results.

Are you  sure that your router is broadcasting its essid ?

You'd be best off hardwiring to the router and acccessing its config page (i think netgear is 192.186.0.1 or something similar) and then check the wireless settings

---

### Post by Oli1122 on 2008-11-15
it worked in windows but i cant findout if its essid how can i change it to that????

---

### Post by rlzyoner on 2008-11-17
Generally all settings regarding your wireless router configuration are stored in the router itself.
Open yur browser and head to the default gateway address of your router (something like 192.168.1.1) and check the wireless settings there.

The essid settings (broadcast and hidden) should be there.

---

