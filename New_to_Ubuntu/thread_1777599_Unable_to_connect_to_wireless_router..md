---
title: "Unable to connect to wireless router."
date: 2011-06-07
forum: New to Ubuntu
---

### Post by gordon33 on 2011-06-07
Hello All


This is the last part towards correcting 3 recent problems see:[http://ubuntuforums.org/showthread.php?t=1774626](http://ubuntuforums.org/showthread.php?t=1774626)
[B]
What connection boxes needs to be checked on my HP G60t-200 lap top with Ubuntu 10.04 to get it to see my Netgear wireless router?  
[/B]

When I try to go wireless I get wireless disconnected.  When I try to connect; the wireless icon waves or scrolls and ends asking me for the wep.  Its there in the box with my ssid and I click apply and again the icon waves but their still is no connection.

The other problems appeared to have been cleared up by updating my Netgear wireless router's firmware.  

Thank you

gordon33

---

### Post by fabricator4 on 2011-06-07
That seems to be indicating that your WEP passcode is incorrect.

You should be able to log onto the router and get the correct code. 


Chris

---

### Post by gordon33 on 2011-06-07
Hello Chris (fabricator4) 	

That seems to be indicating that your WEP passcode is incorrect.
You should be able to log onto the router and get the correct code.

[B]
The WEP Key I have been using is correct.  Is that what you mean by passcode?

[/B]

Gordon33

---

### Post by gordon33 on 2011-06-07
The attachment shows what comes up.  when i click show WEP it is the same as the Netgear router page WEP.

---

### Post by pastalavista on 2011-06-07
Check to see if Network Manager wireless connection IPv6 settings are "Ignore" or uncheck "require IPv6 connectivity" unless you know your ISP has it already and the router supports it

---

### Post by gordon33 on 2011-06-08
Hello pastalavista

How or where would I check to see if Network Manager's wireless connection IPv6 settings are "Ignore" or unchecked? 

I know my system worked 6 days ago buy things went bad and it took me a while to get to the network wired.

I will be looking in the ubuntu help part of my computer for IPv6 searching Network Manager seemed endless.

Gordon33

---

### Post by pastalavista on 2011-06-08
Sure, sorry... right-click the network manager icon in the panel and select 'edit connections' then select the wireless tab, highlight your connection and click 'edit' and then the IPv6 settings tab. This is just an unlikely but possible source of your problem. If this doesn't work, you could also download the Windows binary driver and install it with 'ndiswrapper' which is in the Ubuntu Software repositories. Instructions are on the web (Google works) and not simple, but with Linux, almost anything is possible, it just takes a bit of work sometimes.

---

### Post by gordon33 on 2011-06-08
Hello pastalavista

Thank you for the instruction.  I am still learning the what things are called.  

Getting to the IPv6 settings tab I found a "Ignore" in a box that was labled "Method" to its left.

The pull down menu of the Method box offered 5 choices, other then Ignore.  

Such as: Automatic, Automatic Addresses only, Manual, Link-Local Only, and Shared to Other Computers.

Which of the above should be selected?

Thank you

gordon33

---

### Post by grahammechanical on 2011-06-08
Hi

It is advised that you set the method to Ignore IPv6 for the time being. In future all IP addresses will use IPv6 but until then it has been found the setting to method to ignore IPv6 avoids some problems.

But the real issue is why is the connection bing refused? You are confident that the pass phrase is correct. The other thing that would prevent a connection being established is if Network Manager was set for a different encryption method to the router. Are you sure that the router is set for WEP and not WPA-PSK?

Other than that here is a link to the trouble shooting guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards

---

### Post by gordon33 on 2011-06-09
see

[http://ubuntuforums.org/showthread.php?t=1778631](http://ubuntuforums.org/showthread.php?t=1778631)

---

