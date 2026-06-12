---
title: "[SOLVED] Icant bridge my wireless and eth0 so i can get xbox live"
date: 2008-07-22
forum: Networking &amp; Wireless
---

### Post by kielanmatt on 2008-07-22
I tried brctl and i done it the furthest i got was the IP test on the 360 network test and then it failed the DNS test

Then i went onto FIRESTARTER and it said the internet device is not ready, so i went on the ubuntu forums and looked up that i need to make it have static ip and i have done so it has done the same on the 360 DNS test FAILED. I dunno what to do now

I BRIDGED MY 360 BEFORE WITH WINDOWS AND IT WORKED

my config

WLAN0 (internet)
IP: 192.168.1.10? (the last number is assigned differently each time i connect because my linksys has DHCP)
NETMASK 255.255.255.0 (or summink along the lines of)
GATEWAY 192.168.1.1 (the routers IP)

ETH0 (xbox360 to linux)
IP: 198.162.105.1 (the console's is set to 198.162.105.2)
NETMASK: 255.255.255.0 (the network tool filled this in automatically)
GATEWAY: 198.162.105.1 (consoles same)

MAYBE I SHOULD TRY brctl with static (i did DHCP before) but it has no logic to work.

OR

should i change ETH0's GATEWAY to WLAN0 gateway

---

### Post by Washer on 2008-07-22
Can't really parse your post so I'll just explain. There's a number of things you need to do.

Read this carefully: [http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

On the linux computer:
- setup firestarter sharing
- Fix the device not ready error
- Allow the xbox's (static) IP past the firewall

On the xbox:
- Give it a static ip along eth0
- gateway# = the eth0 IP of your linux computer. Check with "ifconfig" in a terminal.
- setup the DNS servers, see link


Disclaimer: I did this with 2 computers so it might be different on an xbox. I doubt it, though.

---

### Post by kielanmatt on 2008-07-22
u are so fuckign awesome

---

### Post by Washer on 2008-07-22
call me Big Bird like sesame street

---

### Post by kielanmatt on 2008-07-23
it didnt work i did everything and even forwarded the ports (55 for DNS of course, 88 and 3704) and it didnt work dunno what to do now it still fails the DNS test

---

### Post by Washer on 2008-07-23
DNS test meaning you can't resolve anything? I need details about your setup, post the result of ifconfig. Can you ping between computers? Last item on the list - do they have the same nameservers?

---

### Post by kielanmatt on 2008-07-23
i did ICS and it worked its solved

---

