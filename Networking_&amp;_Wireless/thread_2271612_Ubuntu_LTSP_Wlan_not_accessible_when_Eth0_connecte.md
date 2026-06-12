---
title: "Ubuntu LTSP: Wlan not accessible when Eth0 connected"
date: 2015-03-31
forum: Networking &amp; Wireless
---

### Post by Bato001 on 2015-03-31
[FONT=arial]I am new to Ubuntu and LTSP. I have had a problem with wireless internet not working on my server running Ubuntu LTS14.04. I was unable to access my wireless internet connection when eth0 was up and running. I have tried to find an easy answer on the forums and internet but only saw other frustrated noobs like myself trying to get answers, but only garnering silence.

_Here is the cause of my problem and the fix that worked for me:_

The problem was caused by following a bad tutorial that instructs you to change the  [/FONT]*"/etc/NetworkManager/NetworkManager.conf file"*[FONT=arial]. 

This tutorial: "https://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients" STEP 1d- tells you to open the "/etc/NetworkManager/NetworkManager.conf" file and change the "managed" setting from "false" to "true".

This is a **huge mistake** as it makes eth0 your default managed connection and you have to either disconnect the cable or go into the managed networks GUI and disconnect eth0 (updown) in order to access the internet using your wireless connection. 

If you followed this tutorial, and I did, you will not be able to use your wireless internet connection on the server or share it with clients until you change managed back to false.

Open a terminal and type: "[/FONT][COLOR=#000000][FONT=Monaco][FONT=arial]*sudo gedit /etc/NetworkManager/NetworkManager.conf*"
At the bottom of the this very short file it will have a line that says:"*managed=true*"
Change this to "*managed=false*"

Reboot your server an you will see that only the wireless connection is showing in your network manager now and you can now connect clients and access the internet at the same time, and your clients can also access the internet. 

As an aside I want to thank the Ubuntu devs here for pointing me in the right direction on some older, closed threads. I hope my post puts this problem to rest permanently for those who followed that tutorial.[/FONT]
[/FONT][/COLOR]

---

