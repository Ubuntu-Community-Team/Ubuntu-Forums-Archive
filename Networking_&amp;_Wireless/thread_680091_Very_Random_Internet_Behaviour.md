---
title: "Very Random Internet Behaviour"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by kempy1000 on 2008-01-27
Hello,

I recently got Ubuntu working just as I wanted it with apache mysql php mythtv etc etc

However when I now boot I have no internet connection at all I cant ping or load pages.
I use a static IP of 192.168.62.52 with gateway 192.168.62.1

It was all fine for a while no problems then suddenly after reboot it goes wrong.

If I start Ubuntu then change the network settings to DHCP I can use the internet like normal if I then switch back to static I sometimes get a normal connection other times I'm back at the start with no internet at all.

I cant have a DHCP configuration as i want to run servers and have a stand alone box. 

Thank you for any possible fixes!

---

### Post by hahahan on 2008-01-28
Kempy1000,

Did you add a nameserver entry in your /etc/resolv.conf file ? See man resolv.conf.

Regards

---

### Post by kempy1000 on 2008-01-28
Thanks For the Help
My DNS Server (192.168.62.1) is in the /etc/resolv.conf file along with 0.0.0.0
And still the same problem.

---

### Post by kempy1000 on 2008-01-28
SORTED--
Thanks

I had two network cards in my computer plus the onboard Ethernet.
I was trying to use the bulit in LAN.
The two network cards had been detected as one because they were exactly the same (for some reason) i removed the two cards and continued to use the onboard LAN all is now good!

---

