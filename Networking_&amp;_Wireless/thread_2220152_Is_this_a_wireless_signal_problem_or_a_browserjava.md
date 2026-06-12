---
title: "Is this a wireless signal problem or a browser/javascript problem?"
date: 2014-04-26
forum: Networking &amp; Wireless
---

### Post by a5tudent on 2014-04-26
With windows XP, the computer connects to the local ATT/Wayport hotspot and loads the authentication webpage without a problem.  The only problem is that it would be *better* to connect *with Linux *than with windows, and Linux will not fully establish the connection until a solution is found.

The system is dual boot with Ubuntu 12.04.1 LTS using kernel 3.2.  The other OS is XP sp3.  The hardware for both is exactly the same, of course, as is the position of the wireless antenna.  The windows setup uses the Realtek wireless "LAN utility" to select an access point and establish a wireless connection. The Realtek utility seems to recognize that there can be several different access points all named "attwifi" and it seems to dynamically seek the best signal out of the bunch.  XP works every time to make the connection, and this is embarrassing because I'm the one who is always telling family members to switch from windows to Ubuntu.


Attempts to connect in Ubuntu have not worked yet.  Here is the typical sequence of events:
1. Ubuntu recognizes the wireless adapter (AWUS036H with Realtek RTL8187L chip) and attempts to find an access point.  
2. Recognition of the local ATT/Wayport hotspot is successful.  'iwlist wlan0 scan' reports the quality as 47/70, which is low, but it worked in windows at similar levels.  
3. An IP address is assigned by DHCP.  Default gateway and DNS servers are successfully assigned.
4. Ping to Google DNS servers is successful.
5. The attempt to login to Wayport is _not_ successful because the ATT/Wayport.net login page _will not even load_!

Here are the extra steps tried so far:
1. Installing the recommended RTL8187L driver for kernel 3.2 and boosting to maximum permitted power level.
2. Updating to the latest Oracle JRE with correct Mozilla plugins.
3. Attempts to load the Wayport login page using both the latest Firefox and the latest Opera.

So far nothing has worked, and no authentication can be completed with the ATT hotspot.  However, when 
this same Ubuntu setup was tried with a pay-as-you-go Karma hotspot that requires authentication using a different webpage (and presumably a different script), it worked perfectly at least at close range.  However, Karma's typical rate of $14/GB is just too high for me for everyday use as a grad student.

I've searched everywhere and found no answer.  The only possible lead is when Opera reports that x_core.js did not load or master.js did not load.  However, I don't know how to fix that problem, and this file loading problem could still be due to a low signal.  Don't you hate it when something works in Windows but not in Ubuntu? Would you say this is a wireless connection problem or a browser and javascript problem?  Any ideas?

---

### Post by varunendra on 2014-04-28
Welcome to Ubuntu Forums a5tudent! :)

If you doubt it is browser related, have you tried chromium as well? And/Or updating "icedtea-7-plugin" package which provides the Java plugin to the browsers?

If that didn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

**PS:**
There is no shame in accepting drawbacks/disadvantages of something you like. Wireless support for Linux is still not as good as it is for Windows and that's a bitter truth. Yet there are things that are better in Linux than in Windows, tell your family members about those (along with a honest description of possible disadvantages too). Different people have different priorities, so just spread the word and let them make their own choices.

---

