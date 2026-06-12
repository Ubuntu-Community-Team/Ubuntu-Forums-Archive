---
title: "2 Home networks, from 1 access point?"
date: 2014-08-19
forum: Networking &amp; Wireless
---

### Post by karlowbrian on 2014-08-19
Hello Ubuntu Forums!

So at my house I have one modem and one access point. But for what ever reason I am giving off 2 networks from my access point? For example, The name of m,y home network is "Blazeracing" but when I scan for nearby networks, "Asus5_G" appears. Now I know that this is mine because I have an Asus access point called the 5G. Also if I turn off my modem and access point not only does "Blazeracing" go away, but so does "Asus5_G" Now how would I disable the "Asus5_G" network?


Thanks
-Brian

---

### Post by weatherman2 on 2014-08-20
Sounds like you have a dual band access point, with separate SSID names; you named the 2.4GHZ SSID "Blazerracing" but never picked a name for the 5GHZ SSID, so it defaulted to the factory setting of "Asus5_G."  You can choose to give them the same name and let your equipment decide which has the best signal and connect to it.  I prefer to keep them separate.

I would simply rename "Asus5_G" to "Blazerracing5G" or something and give it the same password/security type.  Then you can use either 2.4GHZ or 5GHZ.  In a congested area where numerous neighbors have 2.4GHZ access points that could interfere with yours, 5GHZ can give you better reception.  But not all WiFi equipment can do 5GHZ.

---

### Post by karlowbrian on 2014-08-21
Ohhh! Yeah your exactly right! Thank you so much for the help! I wasn't even thinking about it being a dual band access point. Now this is also kind of a rokkie questionj but how would I change the name and set a password for the Asus5_G network?

---

### Post by weatherman2 on 2014-08-21
You should be able to login to your router using a web browser.  Typically you would point our web browser to [http://192.168.1.1](http://192.168.1.1) or a similar address - this will vary by the make/model of router.  if there's a user's manual for your router, dig it up and it will probably be in there if 192.168.1.1 isn't right.

Next, you'll need an administrator login/password for your router.  Typically this would be "admin" for the username and either a blank password or "admin" or "password" - or again, look in your user's manual.

Now, you should have a web browser with menus and options you can change.  Look around for wireless options and find the 5GHZ network name (SSID) and change it there, then apply, etc.

---

### Post by karlowbrian on 2014-08-23
Okay awesome! Thank you so much!

---

