---
title: "Can't connect to my router"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by thecynicality on 2006-11-24
We just got a new connection at our house, we switched to verizon fios, and im trying to connect to my router from my laptop to get to the internet. I'm using kubuntu and i open the wireless assisstant and i see the router listed there, and when i go to connect i put in the wep key, ive checked over and over to make sure its right, i set it to automatic(DHCP) and to open connection. Then when i click on the router name to connect it tries to connect for a few seconds and then it says connection failed. My wireless has been working for me at school, and i can't figure out why i can't connect to the router.

Does anybody have any ideas?

---

### Post by Spin Doctor on 2006-11-24
I had the same problem with Ubuntu 6.06LTS. I could not connect to my accesspoint using wireless. I upgraded to 6.10, and then it magically starts working.

Start with the lowest possible configuration of your accesspoint to be able to troubleshoot the router. Meaning no encryption, no limiting MAC addresses, dont hide SSID, and so forth. I know it is not very uncomfortable to leave you accesspoint open like this, but to be able to troubleshoot it, you might have to for a little while atleast.

If it then starts working at minimal configuration, start adding those security meassures back again, one by one, and see when it does not work anymore, and you can target on that problem. Could even try adding them in different order.

If it doesnot even work with the lowest available configuration to reach your accesspoint, then I would assume you need to upgrade or use another driver for your wireless network card, or even upgrade to the latest version of Kubuntu in your case that is.

---

### Post by Feenix3k on 2007-03-23
I see my house and other networks, but cant conect. In the Syslog it skips the conection because it is not WPA. But our system is not WPA.

Another place it says its already assoceated, so I dont know what is going on. It is frustarating to see you connection on the computer but not being able to conect

---

