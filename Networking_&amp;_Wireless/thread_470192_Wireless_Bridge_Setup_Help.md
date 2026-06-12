---
title: "Wireless Bridge Setup Help"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Polygon on 2007-06-10
Ok, i need help with setting up my wireless bridge, a netgear me101

First thing, is that no computer even recognizes that the bridge is attached. the only computer that will actually see the bridge attached is my brothers Mac OS X laptop. But i need windows to be able to see it so i can upgrade the firmware..... The ethernet port works fine as when i have a ethernet cable from my router to my computer, it connects fine, but then when i plug in the ethernet bridge it says "no network cable plugged in". hmm. 


The second thing is that i need help actually setting it up. Ive been trying to enter my network information in the "network" settings in xubuntu, but it doesnt seem to work. There is a configuration utility for windows, but windows doesnt see the bridge. There is ALSO a web configuration utility, but you have to do something strange to make it work, like change your IP address to 192.168.0.201 and then go to 192.168.0.200 in your web browser, and i have only gotten this to work on my brothers Mac OS X laptop, with windows and linux it just says "connection refused".

so any help on getting this to work? this is the information that i know so far:

wireless Router IP : 192.168.0.1
Bridge IP: 192.168.0.200
Bridge name: netgear_me101
my network has WEP encryption

So, any tips on how to get this wireless bridge to work with xubuntu? (xubuntu uses the same network preferences thing that ubuntu does)


EDIT: 

i figure out how to do it. turns out i was not using a "crossover cable" and instead i was using a "ethernet cable".

so if its not working for you, make sure you are using a ethernet cable! it worked instantly once i used a ethernet cable. Then i could go into the web config interface ([http://192.168.0.200](http://192.168.0.200)), edit the config, and then set it up. then once it was setup, in xubuntu i just set "eth0" to DHCP and everything worked ;)

---

