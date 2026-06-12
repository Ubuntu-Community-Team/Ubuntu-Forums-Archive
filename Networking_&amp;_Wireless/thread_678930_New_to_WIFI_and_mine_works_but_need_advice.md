---
title: "New to WIFI and mine works but need advice"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by darkworld on 2008-01-26
Ok Ive spent a day on a new build PC. Im well chuffed I got Gusty up and running fine, ive worked through my probs one at a time and actually feel im a bit of a star! Sound working! Nividia 3D working and net connection.

I was very lucky because I was able to jump on an unsecure router in my street and get updates and drivers etc. Now im new to routers and switches etc, ive got a basic understanding. My pc connects to my new router fine.

What I now need to do is make sure my wifi from pc to router and the router is secure. This is where I get out of my depth.

My router is a WRT54GL 2.4ghz 802.11g broadband router and my PCI card is a Pulsecom technologies WP-RT2561T. Both devices recommended by Ubuntu users.

How do I secure my router to stop other peeps in street jumping on it?

Is encrypted transmission necessary?

---

### Post by malluen on 2008-01-26
I couldn't tell you exactly what to look for with that router but point yourself to 192.168.0.1 in your web browser to get to the web configuration page. Look for encryption or securing your connection and activate it with WEP. You may have to dig a bit to find it depending on the router but it sounds as if you have come this far that you'll have no problem with the rest.

---

### Post by 50words on 2008-01-26
I thought WEP had pretty big security problems as compared with WPA.

---

### Post by Hightide on 2008-01-26
> **darkworld said:**
> 

How do I secure my router to stop other peeps in street jumping on it?

Is encrypted transmission necessary?

I agree with 50words that WEP is less secure than WPA.

See Weiman01 tread about security

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

I would use WPA  

regards
:)

---

### Post by maconga on 2008-01-26
WEP = Weak
WPA = Stronger 


This is how you can secure your wireless network. i personally would secure it, so that nobody steals your internet to download illigal stuff, and you get charged for it. 

Open a new tab and enter this  [http://192.168.1.1](http://192.168.1.1) 
You should see a log in, leave the username blank, and the password should be "admin" without the ""

You should now see a "Wireless" tab, click that, now click "wireless security" 

For security mode select "WPA Personal"
For the Share Key (password) make it something easy for you to remember like "heymynameisbob" with out " " 

click save settings and your done! 

You now have a secure wireless network

---

