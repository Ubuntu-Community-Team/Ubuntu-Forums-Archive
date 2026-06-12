---
title: "[SOLVED] Changed WPA key and now cannot connect."
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by Scrib on 2007-09-20
HELP!!!! I changed my WPA key on my router and now UBuntu will not connect.

My Vista and PS3 (which is why i changed the key cos PS3 does not ike spaces in the key - which I had) work fine.

It might be something to do with my Keyring - but I'm not sure how to chnage it.

Can anyone suggest anything.

---

### Post by noob12 on 2007-09-21
You can use the keyring manager (**System | Administration | Keyring Manager**) to delete the key for that network and you should be asked to enter it again the next time.

---

### Post by Scrib on 2007-09-21
Tried that and entered new key, but it still didn't work.

If I want to check the wireless card mac address do i just do a ifconfig ?

---

### Post by noob12 on 2007-09-21
Yes, **ifconfig -a** should show it as HWaddr; without the **-a** it will skip interfaces that are down.

---

### Post by Scrib on 2007-09-22
Still no luck - I deleted the "Default" keyring and rebooted. When I logged on it did ask for the WPA password (which it did before) but then it failed to connect again.

The only one left is the "Session" keyring, but I don't have access to delete that.

Any more ideas? I have MAC filtering on my router (which is why i asked about the ifconfog command) but the "WLAN" mac address is in the allowed addresses (and it worked fine before I changed the WPA pasword).

Any more ideas - I'm currently a bit lost without intenet access on this box.

---

### Post by kevdog on 2007-09-22
You dont have any strange characters in the WPA do you -- other than numbers or characters??  Is the ESSID being broadcast on the router??  Turn of MAC filtering for now, and try changing the key to something easy like HOME or something and see if it can connect.

---

### Post by Scrib on 2007-09-23
I have turned off mac address filtering and still the same problem. I knew this wouldn't work (but it was worth a try) as the machine duel boots with XP and good old XP works ok using the same wireless card and WPA key, etc.

The SSID is not broadcast, but again, this worked until I changed the WPA key.

When i try to connect to asks for the WPA key and I enter it correctly, but it fails to connect. Its as though its some how using the old key still (?).

I'm having to use XP at the moment until i get this resolved. :lolflag:

Any more ideas?

---

### Post by Scrib on 2007-09-23
I have fixed it. I tried connecting, yet again, but the ONLY thing I did different this time was that I did not tick the "show password" box (the one that shows you the password/key so you know its correct).

By doing this it connected first time - wired or what?

---

