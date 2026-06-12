---
title: "Have connection but no data (internet). Wifi, Ubuntu 18.04"
date: 2019-07-18
forum: Networking &amp; Wireless
---

### Post by intoxicologist on 2019-07-18
My laptop wifi connected, I can ping and trace websites but nothing will load. Phone connected to the same router and have full internet access. 
resolv.conf shows 'nameserver 127.0.0.53'. If I change it to 8.8.8.8 and restart service with 'service network-manager restart', nothing changes, apart from that resolv.conf resets to 127.0.0.53
Any ideas, please?

---

### Post by alias2234 on 2019-07-19
Try to reboot the machine.
Sometimes that helps.

If you can, try connect directly to internet with cable and no Wifi.

---

### Post by intoxicologist on 2019-07-19
Rebooted the machine and router. Didn't help. Will try cable. The mystery is that I can ping and tracert websites but they won't open in browser

---

### Post by alias2234 on 2019-07-19
Try reinstall browser.
Try another browser.

---

### Post by alias2234 on 2019-07-19
Try to update ubuntu.

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by alias2234 on 2019-07-19
How is it going ?

---

### Post by alias2234 on 2019-07-19
Try to connect with your mobilephone as a modem with tethering, hotspot.

---

### Post by alias2234 on 2019-07-19
Step 1:*Add Google’s (or your favorite) public DNS to /etc/systemd/resolved.conf:

DNS=8.8.8.8 2001:4860:4860::8888
FallbackDNS=8.8.4.4 2001:4860:4860::8844

Step 2:*Restart networking (or reboot the machine)

---

### Post by alias2234 on 2019-07-19
[https://lwn.net/Articles/753079/](https://lwn.net/Articles/753079/)


[https://askubuntu.com/questions/966870/dns-not-working-after-upgrade-17-04-to-17-10](https://askubuntu.com/questions/966870/dns-not-working-after-upgrade-17-04-to-17-10)

---

### Post by alias2234 on 2019-07-19
Have your problem been solved, please tell us what you did, so others can benefit from it. Thanks.

---

### Post by intoxicologist on 2019-07-19
Update: problem solved!
Problem was in Firefox (latest update), not Ubuntu. Fixed by loading Firefox in safe mode.
Thanks everyone!

No, not resolved. 
Connected with cable and mobile phone tethering - exactly the same result. Adding DNS doesn't help.

---

### Post by kurt18947 on 2019-07-21
Could you try a live USB session? The fact that ethernet doesn't work either seems to point to a problem with your Ubuntu install. If you can connect with a live session but can't connect from the installed session that will help to isolate the problem somewhat.

---

### Post by aprilmorone on 2019-07-23
Could be as simple as the NIC card going out on you, or if tethering internet via your smartphone's data, whichever USB port you are using to do so having gone out on you. You can fix the latter problem via buying another USB port, and soldering it via soldering iron to the motherboard. Supplies you'll need to do so: Soldering Iron, Solder, and obviously, the extra USB port. If the NIC card is the issue, just buying a cheap one off Amazon or some other place can help. They aren't expensive at all. I have my Computer Support Specialist AAS degree and had held a 4.0 GPA all throughout. Now, I am a certified mechanic who is also currently in college for Computer Science Engineering to later programme the computers of vehicles, someday. You can trust my skills and advise. And, if for some reason, my suggestions don't work, I will research this info for you and then let you know of alternative good ways that other techs and users have found worked for them.

---

