---
title: "unable to connect Cell phone with pon"
date: 2005-06-13
forum: Networking &amp; Wireless
---

### Post by rlwrenn on 2005-06-13
My older USB1.1  laptop just died yesterday so I am trying to get my new Toshiba laptop with usb 2.0 to dial out to my Sanyo SCP4900 cell phone. 
   My old laptop was using knoppix-std distro, and I was using the pon scripts (/etc/chatscripts/sprint, /etc/ppp/peers/sprint ) that were already in that distro (/dev/modem was changed to /dev/ttyACM0).
   Unfortunatly Knoppix-STD doesn't recognize my USB 2.0 ports on the new laptop. Ubuntu does recognize the ports and the cell phone correctly (ttyACM0). But when I run "pon sprint" my cell phone doesn't dial out, and pon doesn't display any errors.
    Any sugesstions? :|

---

### Post by alastair on 2005-06-13
You should check your system logs i.e.

/var/log/syslog

See also : man pppd

You can add "debug" to pppd scripts, and "-v" to any chatscripts. A bit painful I know - but it does keep life interesting. You learn more when things don't work.

---

### Post by az on 2005-06-13
sudo type
tail -f /var/log/messages
in a terminal while doing sudo pon in another.

Post the output here.

---

### Post by rlwrenn on 2005-06-14
Thanks for reminding me to check the logs . We are visiting family here in PA. The problem was the Sprint servers here  were either down  or too busy during the mid morning yesterday. It started working when I tried again after 5:30pm 
   The messagelog showed that the servers were not responding and thus the script just timed out. So I tried the web function on the phone itself and got the message that the servers are busy or down.

---

