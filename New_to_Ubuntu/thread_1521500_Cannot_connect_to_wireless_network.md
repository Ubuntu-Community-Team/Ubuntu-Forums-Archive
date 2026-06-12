---
title: "Cannot connect to wireless network"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by C:/orpse on 2010-06-30
Hi, as stated in the thread title I am unable to connect to my wireless network. I am currently running Ubuntu 10.04, and this is in fact my first experience with linux. I've been messing around with this issue for about three weeks now and have had no success. As I mentioned my wireless adapter (D-Link DWA-140) will detect my network, which means that at the very least I would assume my device is working with linux. So far I've made sure that wireless networking is enabled, and I have my IP adressing set to automatic, I have not manually set any adresses. I've been told that the driver may not be working but again, my networks are detected I just cannot connect. Can anyone give me any advice on getting connected? Thank you.

---

### Post by anewguy on 2010-06-30
If you can see wireless networks, that's an indication that your driver is probably working.  If you can't connect to your router, be sure to check and then enter correctly as needed:

- does your router use encryption?  If so, you need to specify the type and the password/passphrase when setting up your connection in Ubuntu.

- does your router use MAC filtering?  If so, be sure your adapters' MAC address is in the MAC table in the router.

- does your router broadcast the network name (ESSID)?  If not (such as when you are trying to keep your router hidden), then you manually have to set up the connection via network manager.

- if you can see your network, what happens when you click on it?


Dave

---

### Post by C:/orpse on 2010-07-01
> **anewguy said:**
> If you can see wireless networks, that's an indication that your driver is probably working.  If you can't connect to your router, be sure to check and then enter correctly as needed:

- does your router use encryption?  If so, you need to specify the type and the password/passphrase when setting up your connection in Ubuntu.

- does your router use MAC filtering?  If so, be sure your adapters' MAC address is in the MAC table in the router.

- does your router broadcast the network name (ESSID)?  If not (such as when you are trying to keep your router hidden), then you manually have to set up the connection via network manager.

- if you can see your network, what happens when you click on it?


Dave

Thanks for the reply. My router is not encrypted, I chose not to do so as I do not have many neighbors out here. MAC filtering appears to be disabled on my router, as my router settings show mac restricted mode is disabled. My ESSID is indeed being broadcast, which linux does correctly identify the network. And when I click on my network in Ubuntu, it acts like it trys to connect for roughly 6-10 seconds then it just says disconnected. As far as I can tell all my settings are good, so I'm genuinely confused. I might also mention that I do not have Ubuntu installed on a dedicated partition, I chose to install it within windows as my hdd space is running low currently. Could that be an issue?

---

