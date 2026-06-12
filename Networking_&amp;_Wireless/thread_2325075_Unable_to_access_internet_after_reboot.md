---
title: "Unable to access internet after reboot"
date: 2016-05-18
forum: Networking &amp; Wireless
---

### Post by Ashwin_D on 2016-05-18
I am a BSNL broadband user from India and I am unable to access the broadband connection after I reboot Ubuntu .

I tried the following commands and they did not work.

sudo infconfig eth0 up
sudo dhclient 

I also made modifications to /etc/dhcp/dhcpclient.conf by adding name servers 8.8.8.8 to that file but that did not work.

The /etc/resolv.conf file is empty after reboot. 

What seems to happen is when I insert the LAN cord into the USB port Ubuntu tries to get a connection again and again and then gives up 

I am able to access BSNL broadband wired connection from Windows just fine.

---

### Post by Ashwin_D on 2016-05-19
Any commands that I can type and post their results here that would help pinpoint where exactly the problem is ?

Is it due to Ubuntu or due to the modem?

---

### Post by Ashwin_D on 2016-05-20
Finally some clarity after  a long time. I am able to connect to internet via a static IP address. So why is DHCP failing ? 
If is it something with the modem can Ubuntu help me pin point that fact ?

---

