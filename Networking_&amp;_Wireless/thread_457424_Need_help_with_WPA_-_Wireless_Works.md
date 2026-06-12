---
title: "Need help with WPA - Wireless Works"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by kingleer on 2007-05-28
Okay, my wireless card works with ubuntu. I've been using my laptop to access the wireless network at home and on my campus using Ubuntu for some time.  Recently, I changed the firmware in my wireless router at home. 

See the link below for the firmware I'm using - 

[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)

This time, I decided to use WPA encryption (instead of WEP like I had it in the past). 

But, I'm at a loss for how to connect if my network is using WPA encryption. 

My skill level = noob. 

I consulted the sticky from the main wireless help forum concerning WPA 

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

With no luck. 


When, I open up the terminal and enter "sudo iwconfig" I get the results you see in the screenshot I've attached to my post. 

So, what should I do/check next? 

Thanks in advance.

---

### Post by ellisdee on 2007-05-29
Did you have a passkey prior to upgrading the firmware (whether it be WPA or WEP)?

Do you use Gnome Keyring Manager?

You may need to just remove your old key from the Gnome Keyring Manager and then setup your wireless connectivity again.

---

