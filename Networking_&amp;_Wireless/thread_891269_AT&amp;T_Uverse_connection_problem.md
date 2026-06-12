---
title: "AT&amp;T Uverse connection problem"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by joruss1 on 2008-08-15
I am having problems getting connected to the internet from Ubuntu 7.10.  My Windows connection is working fine.  I called Uverse and they said they don't support Linux and couldn't help me.  Is there any one out there that is using Uverse to connect to the internet?

---

### Post by Sir darkm on 2009-03-17
try this link i'm a newbie here but it worked for me( I over analyzed it and  made it difficult)  either way  I have Uverse and it's working so give me know more details and I may be able to help. 


[http://ubuntuforums.org/showthread.php?t=1094806&highlight=uverse](http://ubuntuforums.org/showthread.php?t=1094806&highlight=uverse)

---

### Post by LoganW on 2009-03-18
I've had no luck with wireless on the uverse box at home with my Acer 5050 - I think it's the Intel 2200 chipset. It works while being hardwired. I'm running wicd and ndiswrapper. After reading up and trying a bunch of different things with no success, I took the machine to work and tried to connect to my buffalo (I think) router, it connected with no problems using WEP. I am running WPA on uverse.

However, I removed security at home and still could not connect. Very strange indeed.

I really do like this version (8.1) of ubuntu but this one may be a show stopper.

---

### Post by LittleBirdie on 2009-09-29
I finally got a hold of someone at U-Verse who knows what they are doing.  (I know, I know.......anyway)  This is what happened.  To connect to the internet go to your Network Settings.  Select Wireless Network Connection then select properties.  Under Wireless Settings you will put in for the Network Name (ESSID) 2WIRE and the last three digits of your serial number on the modem.  Under Password Type select WEP Key (Hexadecimal) then under your network password enter the Wireless Network Key on your Modem if you have the 3800 on the 3700 the password is located under the serial number bar on your Modem.  Select Automatic Configuration (DHCP) then hit okay.  Then go to your internet and open your browser.  You should be connected.

---

### Post by jdtoth on 2010-05-07
I was able to get my Ubuntu laptop wireless working with Uverse by using wicd instead of network-manager-gnome.
Use a wired connection then follow the instructions here -
[http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu](http://wicd.sourceforge.net/moinmoin/Wicd%20on%20Ubuntu)

---

