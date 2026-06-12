---
title: "Internet not working: No DHCPOFFERS recieved"
date: 2017-08-15
forum: Networking &amp; Wireless
---

### Post by needles6 on 2017-08-15
Hello, the wifi on my laptop has not been working ever since I unsucessfuly tried to connect to a network through the cli.
 I have done:
 sudo ifconfig wlp3s0 down
sudo dhclient -r wlp3s0
sudo dhclient wlp3s0, which returned multiple lines of DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 17 (xid=0xe3ffca49), and then:
No DHCOFFERS recieved.
No working leases in persistent database - sleeping. 

I tried using wicd-curses, but it said No wireless networks found.
What can I do to fix this?
Edit: After waiting a while, Wicd shows the networks, but when I connect, it only says obtaining ip adress untill eventually saying no wireless networks found

---

### Post by wildmanne39 on 2017-08-15
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by needles6 on 2017-08-15
I tried to connect to a wired connection but a window opened saying:
Connection Failure
(2) Active connection removed before it was initialized

---

### Post by needles6 on 2017-08-15
I followed the instructions for running the script offline. I pasted the script to the desktop, double-clicked it, and pressed "execute". Nothing appeared to happen so I waited ~20 minutes. After nothing had still happened, I double-clicked the file and all it said was ######wireless-info start#########. I opened the original that was on the flashdrive, and it still had the original script. I deleated the one on the desktop, pasted the original from the flashdrive to the desktop, restarted the computer, and ran it, but got the same result.

---

