---
title: "Can't Connect to the Internet"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by aldago on 2007-03-17
I'm using kubuntu 6.06.1 installed as dual boot with WindowsXP Pro. My computer is directly connecting via USB to a Westell DSL modem which connects to my ISP Bellsouth.net. WindowsXP connects with no problem so I know that I'm connected properly but kubuntu refuses to connect to the internet. I've tried to configure the modem by opening a terminal an using the command: sudo pppoeconf. The installed PPPoE package finds three ethernet devices: eth0, eth1 and eth2. (Note: When I pull the DSL cable and run the command in the terminal eth1 is gone.) It then scans the devices looking for a "PPPoE Access Concentrator". I get a message "Sorry. I scanned 3 interfaces, but the Access Concentrator of your provider did not respond". Anyone have an idea what I can try next???

---

### Post by johnc4510 on 2007-03-17
Look at this thread:
[http://ubuntuforums.org/showthread.php?t=385515&highlight=Westell+modem](http://ubuntuforums.org/showthread.php?t=385515&highlight=Westell+modem)

I believe it relates to your modem

---

### Post by Floppyjoe on 2007-03-17
Have you tried to follow this wiki?

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

