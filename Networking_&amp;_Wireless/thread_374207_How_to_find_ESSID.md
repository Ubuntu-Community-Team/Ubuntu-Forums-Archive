---
title: "How to find ESSID?"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by Buster95 on 2007-03-02
Edgy didn't capture my home wireless router settings when I installed it (I presume that it should). So, how or where do I find the network name (ESSID) and password? I looked up the wireless connections on XP (dual boot on the same laptop). It makes no reference to either network name and password.

Where to next?

Cheers

---

### Post by Hallvor on 2007-03-02
Log on to your router? You`ll find essid and password there.

---

### Post by Buster95 on 2007-03-02
Thanks for the response.
How do I log onto my wireless router? It's a D-Link DL 524.

Cheers

---

### Post by finer recliner on 2007-03-02
open a web browser type this in your address bar:

[http://192.168.1.1](http://192.168.1.1)

^this is usually the address to edit your router's settings and configuration. you will need the login name and password. your router manual will have the default values if you have not changed it.

---

### Post by Buster95 on 2007-03-02
Thanks for that.
I followed your suggestion using the default name and password from the manual but the damned thing didn't like it!
I know I haven't changed them (wouldn't know how). Looks like I'll have to try something else. Any suggestions?
Cheers

---

### Post by Hallvor on 2007-03-02
I searched the web a little. It seems that D-link for the most part uses: 

login: admin
password: admin

Worth a try if you haven`t changed anything and can`t find the manual.


[http://governmentsecurity.org/archive/t8088.html](http://governmentsecurity.org/archive/t8088.html)

---

### Post by Hallvor on 2007-03-02
You could always push the reset-button on the back for 30 seconds. But that means you will lose all your settings (essid/password, open ports, etc.). But you will be able to log on and make things the way you want.

---

### Post by finer recliner on 2007-03-02
i agree with hallvor -- reset your router, then login. the first to change when you log in is your login name and password. write it down someone safe, and don't give it to anyone.

---

### Post by Buster95 on 2007-03-02
Thanks for that. Now to see if the next step works. I'm trying to get Edgy to recognise my wireless router. So far nothing has gone my way, but this is a new lead for me.

Cheers

---

### Post by Buster95 on 2007-03-02
I interrogated my wireless router using the "admin/admin" suggestion. It worked.
There is a "username" displayed, but not a password. I entered the username in system/administration/network settings/wireless connection/properties. I left the password blank. It seemed to accept it without objection, but still no connection.

I'll keep experimenting with it, but any ideas?
Thanks

---

### Post by Prometheus.172214 on 2007-03-02
First :
        From a system that is connected to the Router, open up a browser and use tha address 192.168.1.1 (As suggested earlier). Then it should prompt you to enter a user name and password. If you have not made any changes it should be admin and admin again. If you made any changes, then first reset the router (already suggested). For this, on the back of the router, you will see a small pin hole and here press and keep the reset button pressed down for 30 seconds. Then the leave the router for about a minute or two, so that it can start up and assign DHCP addresses. Now try logging into the router again with the 192.168.1.1 address and admin / admin as username and password should work.

Now in the Router webpage, click on the wireles tab.
If you have not reset the router and have logged in, then you will find the existing ESSID and Hex Key there (Depends on what encryption you are using).

The ESSID is entered as shown and the Hex Key is the password.

If you have reset the router, then configure your wireless and the encryption and enter the details accordingly.

---

### Post by Buster95 on 2007-03-02
Opened a browser; went to the address given (Netcomm); used admin/admin as suggested for username and password; it worked. I got in.
However, can't find a wireless tab or anything that specifically referred to ESSID or Hexkey.
Where do I look?
Thanks

---

### Post by Prometheus.172214 on 2007-03-02
Can I get the router manufacturer name and model type please? I can check. I have quite a huge load of routers lying around in my office.

---

### Post by Buster95 on 2007-03-02
D-Link Model DL-524 wireless Router 802.11/2.4GHz.
It's connected to a Netcomm NB5 ADSL2+ Modem.

I'm still a little puzzled about post #4: website 192.168.1.1 interrogates the modem, not the wireless router.

Cheers

---

