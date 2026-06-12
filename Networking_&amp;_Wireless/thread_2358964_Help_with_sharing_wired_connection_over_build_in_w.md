---
title: "Help with sharing wired connection over build in wlan on RBPi 3"
date: 2017-04-19
forum: Networking &amp; Wireless
---

### Post by l0d3r on 2017-04-19
Hi, 

The goal is to create a personal portable vpn device. In the sense that you would connect it to the interent through cable and send out that connection over the wireless interface as a vpn enabled wifi connection.
I have been trying for hours now to share internet access from ethernet over wifi on the RaspberryPi 3, so far unsuccessful.


I made a new connection, choose "WI-FI" Set the mode to "Hotspot" and selected the Wlan0 device which shows up in the drop down menu. I named it "TEST" And it shows up as a device on the wifi list on my macbook without internet access. I now tried to do the same thing with another wlan USB device (alfa awus36nh). Lubuntu drops the ethernet connection and re-connects again over and over. I have tried multiple solutions I found on the internet. like this: [https://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet](https://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet) and this: [https://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet](https://askubuntu.com/questions/169473/sharing-connection-to-other-pcs-via-wired-ethernet)
I mean can it really be this difficult ? It worked on Kubuntu on my RBP2 (which is in use for another project)


Thank you for you time.

---

### Post by TheFu on 2017-04-20
If you want the wifi to make the connection to the internet, then it is a wifi-client, not "hotspot."  Or did I misread your intention?

---

