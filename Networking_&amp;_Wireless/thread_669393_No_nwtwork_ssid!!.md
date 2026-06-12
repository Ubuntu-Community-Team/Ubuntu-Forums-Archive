---
title: "No nwtwork ssid!!"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by Dwiman89 on 2008-01-16
Hi I usually connet to my parents wirelles router. But When I came home today. I couldn't connect. when I scan, I dont get a ssid. Its just blank. Anyone know whats wrong?

---

### Post by Dwiman89 on 2008-01-16
Anyone?

---

### Post by freddyp on 2008-01-16
1. Have you tried cycling the power or resetting the router?
2. Has anyone turned off the SSID broadcast on the router?
3. Have you tried manually entering the SSID (assumes you know it) just in case it was turned off?
4.  have your verified that the wireless is turned on on your laptop? (Mine has a slide switch that I often bump to the off position).

Just a few starting suggestions.

---

### Post by Hightide on 2008-01-16
It sounds like the SSID broadcast may be disabled on the router. You may wish to check that first.

can you give us more information on your setup? 

:lolflag:

---

### Post by Dwiman89 on 2008-01-16
I did check it. but in the router settings it was set to broadcast. I kept reseting the router and that didn't fix it ether...

---

### Post by freddyp on 2008-01-16
Have your verified that the wireless is turned on in your laptop? (Mine has a slide switch that I often bump to the off position).

Do you have Wi-fi radar or wicd installed?  If so, are you getting asny indications that the router is transmitting?

Maybe try changing the  Wireless Network Mode or Wireless Channel.  Just a few other thoughts.:

---

### Post by Dwiman89 on 2008-01-17
ITs on a desktop. Everytime I do  reboot i have to load Ndis wrapper by typing "sudo modprobe ndiswrapper" every time. the modules are loaded when I try to mess with it.  I can scan and everthing by typing "sudo iwlist wlan0 scan"

---

### Post by freddyp on 2008-01-17
Sorry, thought you were talking about a notebook.  (You can tell my bias :-)  So can you connect once you sudo modprobe ndiswrapper?  If so, then you're looking at the need to automatically loading at start-up, right?  Have you checked out the documentation at:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

Section 3.7 Automatically loading at start-up might help.  Sorry if I'm confused about the symptoms....just trying to help.  I know the frustration.

---

### Post by Dwiman89 on 2008-01-17
no everything is loaded and I  pick up the connection.... It just wont connect.....

---

### Post by freddyp on 2008-01-17
Ok, so can you connect to the router, login and see the router settings via wireless, right?  If so, the router RF link is working....not sure why no SSID??  If this is true, it looks like this might turn into an issue about getting out on the web. And again, my apologies if I misunderstand the problem.  Just trying to take this step-by-step to get to a root cause.

---

### Post by lespaul_rentals on 2008-01-17
So, you can connect to the WLAN, correct?  And once you connect, you have problems accessing the Internet?

Are you sure your DNS hosts are set up correctly?  If using static IP, you will need to set them yourself.  If using DHCP, your router needs to be set to give you DNS names.

---

### Post by Dwiman89 on 2008-01-17
Its misterously working now...I think my parents are screwing with it. They aren't very computer illiterate. I kept trying to connect and it eventually connected. btw. I could see the signal strength in the scan but I never could get t to show the signal strength in the bars up top. But I would still like to get to the bottom of this jut in case it happens again....

---

### Post by Hightide on 2008-01-17
can you have a look at Kevdogs tutorial. I may help!
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

:)

---

