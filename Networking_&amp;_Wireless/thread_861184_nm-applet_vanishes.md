---
title: "nm-applet vanishes"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by catinthehood on 2008-07-16
I put Ubuntu on an IBM Thinkpad. It connects directly to the internet with the cable but when I click on the icon in the upper right and select my wireless router and put in my wep password it thinks and thinks and thinks and then asks me for the password again. I put it in and then the nm-applet (Icon in the upper right corner) disappears. At this point I try to get on the terminal but it gets buggy and I can't type anything. I try and log off but the little red button on the upper right doesn't work and I eventually have to hold the power button to shut it off. This happens everytime I try and connect to the wireless. Any suggestions?
I can have more specifics this evening when I am on it again.

Thanks

---

### Post by prshah on 2008-07-16
> **catinthehood said:**
> 
select my wireless router and put in my wep password it thinks and thinks and thinks and then asks me for the password again. I put it in and then the nm-applet (Icon in the upper right corner) disappears. 


Try this for debugging: Open a terminal (Applications-Accessories-Terminal), then ```
sudo killall nm-applet
nm-applet
``` At this point, nm-applet will reappear in the notification area. Try to connect to your wireless network as you've done before, but this time, you will be presented with a ton of debug messages in the terminal. Post those messages here for a clue to your problem.

---

