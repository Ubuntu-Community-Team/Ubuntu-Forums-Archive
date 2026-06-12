---
title: "Wireless network WAP, can't connect"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by TropheusJon on 2008-09-17
Hello,

I have problem connecting to the wireless network.  I can connect on the same machine on Windows Vista.

I setup ndiswrapper and when I click on the network icon on the top right, I can see the various wireless network detected.  I try to connect to the one I want.

Settings : WAP-Personal, Type : TKIP

It gets stuck at waiting for Network Key, I'm sure the password is correct since I can connect via vista.

I setup ndiswrapper using the tutorial found on this forum.

Please help.  I'm not running as super user?(I still need sudo to install things)

Sorry, total newbie with linux. Machine is Dell Studio 17 laptop

Please help!
Thanks
Jon

---

### Post by vorgusa on 2008-09-17
It should ask you for your password if you need sudo permissions.  try temporarily disabling the security on the access point and connecting just to test your computer.  If that works then when you add the WPA key back in copy and paste it into Ubuntu to make 100% sure it is exactly the same

---

### Post by TropheusJon on 2008-09-17
Hello,

It didnt' ask for my sudo password.  When I try to connect, it just prompts me for a password.  I entered it, and it said waiting for Network key, which it never receives.

Any help will be great!
Thanks!
Jon

---

### Post by vorgusa on 2008-09-17
did you try connecting with the wireless security disabled on the Access Point?

---

### Post by TropheusJon on 2008-09-17
Hi,

I'm trying to connect to a wireless network in the office.  I don't have access to the access point.

I read a few threads that doesn't have answer to this problem.  I'm still hoping to solve it.

I know the access point is working because I just connected to it using windows Vista.

Thanks!
Jon

---

### Post by TropheusJon on 2008-09-17
Hi,

Just to update, when I turn on the wifi switch, certain wireless networks get detected.

However, when I run :

 ndiswrapper -l

It says:

bcmwl5 : driver installed

It doesn't say device or anything.  When I installed bcmwl6, it does show the device but as far as I know, ndiswrapper doesn't work with bcmwl6.

Please help!
Thanks!
Jon

---

### Post by vorgusa on 2008-09-17
unfortunately I do not know enough about ndiswrapper.

---

