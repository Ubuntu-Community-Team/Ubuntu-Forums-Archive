---
title: "Ubuntu 18.04-No WPA options for wireless WIFi!?"
date: 2018-12-19
forum: Networking &amp; Wireless
---

### Post by emarkay on 2018-12-19
Can not connect to wifi.  Hardwired internet works OK. Why would WPA (TKIP+AES) not work?  
I see no WPA options at all in 18.04 on 2 different machines, and there are 2 bugs noted, but no workarounds that make sense.  
(See sig below, note one laptop is from 2006! - no secure boot ...).  
Also, wireless **does** connect to local park's Wifi (using no security), so it is not hardware!                 

HELP,  please!

MRK

---

### Post by ajgreeny on 2018-12-19
You really need to be connecting with WPA2, not WPA-(TKIP+AES).

From what you say it seems you do not see a WPA2 option; what router have you got?
Are there any settings in the router that you can change to get WPA2?

---

### Post by Frogs Hair on 2018-12-19
Moved to *Networking & Wireless*.

---

### Post by emarkay on 2018-12-20
All my other devices are unaffected, as well as the two pc units that worked OK in 16.04.  
Instead of messing with the router, where do I get the settings options in 18.04 for WPA?  The only options are for two WEP settings!  
Nothing else has changed, all works except am unable to WPA connect the 2 laptops I (unfortunately???) reinstalled 18.04 over 16.04.5!
There are bug reports I have subscribed to, but no workarounds other than to downgrade programs to 16.04 and add lines to files through Terminal.  Say what? 

Who has a good WPA (any flavor) working on 18.04, and if so how can we compare settings???

HELP! Both my laptops can only connect by cable or unsecured WiFi!

Thanks, 
MRK

---

### Post by ajgreeny on 2018-12-20
In spite of your comment in the first post it might be hardware related; your wireless hardware may be unable to see  any WPA2 connections, so see **Wireless-info** in my signature, download it and run the script, then report back the output here or using [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) if the output is too large to add direct. 

One of our wifi experts will hopefully be able to suggest a solution.

---

### Post by emarkay on 2018-12-21
Thanks, will get them out this weekend and see.  Does your 18.04 show more than 2 selections for WiFi??  Do you have a WPA option(s)??

---

### Post by ajgreeny on 2018-12-21
Yes, my hardware show several options as shown in my screenshot which I got from the "Edit connection" item from the network icon in the panel.

There is another option I get missing from the image which is cut off at the top by xfce4-screenshooter but it was another WEP 40/128bit encryption which is no longer secure enough for me to consider using.

---

### Post by emarkay on 2018-12-31
Major embarrassment - There was a printer I had left connected, and it was affecting the wireless.  Dum-me used same network name.  All OK!  THANKS!!!

---

