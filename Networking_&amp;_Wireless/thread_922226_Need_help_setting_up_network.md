---
title: "Need help setting up network"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by Prestario on 2008-09-17
Hello,

I have just installed xubuntu 8.04.1 
and i am unsure on how to make a network connection.

i have tried to make one already in network settings but it shows as if there is no modem connected.

Any help would be much appreciated as i would like to get to know more about these os.

cheers

---

### Post by NoReflex on 2008-09-17
Hello!

You'll have to be a little more specific: how do you connect to the internet (ADSL, 3G, PPPoE), what's the modem's model etc.

Best wishes,
NoReflex

---

### Post by Prestario on 2008-09-17
ok well i connect by serial modem and according to the top of that modem it is a model of rockwell.

I also have a 10/100 network card:

([http://www.trademe.co.nz/Computers/Components/Other-PCI-cards/photos/a-171549740/p-71741767.htm](http://www.trademe.co.nz/Computers/Components/Other-PCI-cards/photos/a-171549740/p-71741767.htm))

Hope this helps as i do not no where to look for more infomation on internal hardware on that type of os.

---

### Post by NoReflex on 2008-09-23
If you connect via modem first you should check if it's detected. Try with **lspci** and **lsusb** to see if you can find it.
After you connect your modem wait about 30 seconds and run **tail /var/log/messages** and try to figure out if the modem was associated with /dev/modem. After this start Gnome PPP (install it with **sudo apt-get install gnome-ppp** if you don't have it) fill in the required data and hope for the best. 
Good luck!

Bets wishes,
NoReflex

PS : Sorry for the late reply

---

