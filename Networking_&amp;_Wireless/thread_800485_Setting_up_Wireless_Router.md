---
title: "Setting up Wireless Router"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by hanzj on 2008-05-19
Hello,
I'm running Ubuntu 8.04 on my computer. Currently, my computer is directly connected to a (wired) cable modem.

I would like to share my internet connection with another person in the house. He has a laptop and he would like to do wireless internet.

I have a Dell Wireless Broadband 2350 Router. As for me, I would like to continue using Wired internet.

How do I go setting this thing up?

Some points:
1. I would like to enable password protection, so that only the other person with the password can access the wireless internet.
2. If possible, I would like to be able to monitor the internet activity, at least  bandwidth is being used by that wireless surfer.

I have tried doing a physical "rewiring" (the end of cable that went to the back of my computer now goes to the Internet port on the wireless router. Then, with another cable, I connect the back of my computer to "LAN1" at the back of the wireless router) but that doesn't work).

&#65279; i can connect with the router, but even the router's Device Status page says that internet is not active.

Thank you.

---

### Post by hanzj on 2008-05-19
More pics here.

---

### Post by hanzj on 2008-05-19
I got the wired internet working. I turned on MAC address (see [http://ubuntuforums.org/attachment.php?attachmentid=70796&d=1211254706](http://ubuntuforums.org/attachment.php?attachmentid=70796&d=1211254706) ... "Your ISP requires you to input WAN ethernet MAC"). I shut off computer for a few minutes. I shut off Cable Modem for a few minutes.
I don't know which of the above was the solution.

---

### Post by vorgusa on 2008-05-20
Most of this is simple.  I would go for WPA or WPA2 wireless security, since WEP is easily cracked.  Don't worry about MAC filtering or No broadcast of SSID, unless you want to deal with the hassel, if people know what they are doing they can get around this quickly.  You can come up with any password you want for WPA and it should be in the wireless security section of your router.  
      As for monitoring, the only way to do that will probably be SNMP if your router supports it.  I know routing OS's will give you graphs but I do not think most home routers will give you that sort of interface. You would have to create a server/Service on your desktop to collect the data.  I do not have any experience with this unfortunately, but I have always been interested in this.

---

### Post by hanzj on 2008-05-20
I powered off my computer after the first night of using the wireless router. But today, when I powered on the computer again, the router was not working. 
EVen the router's ISP address in the browser wasn't working.


What I did to make it work were power off the router and modem for a few seconds and then power them on again (I didn't power off the computer itself this time).

---

