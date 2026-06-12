---
title: "Bluetooth speaker sound distorted (ubuntu 18.04)"
date: 2018-10-14
forum: Networking &amp; Wireless
---

### Post by thomas72 on 2018-10-14
In a new laptop, the sound from my usual bt speaker (JBL Flip 3) is distorted: it can be ok  for a few seconds but mainly it's crackling and interrupted  intermittently.
Also the connection process is sometimes tricky... I have to  connect/disconnect several times.  The same speaker is working fine on another Ubuntu 16.04 laptop. 

  What I tried so far:  
  
[LIST]
[*]If I boot with Windows, it is ok 
[*]Within Ubuntu, another bt headset works fine 
[*]The good old trick of switching profile (A2DP/HFP) and then disconnect/reconnect doesn't solve 
[*]I've reinstalled pulseaudio and pulseaudio-module-bluetooth with no luck 
[/LIST]
  Furthermore, my dmesg is full of:  

  Bluetooth: hci0: last event is not cmd complete (0x0f)

  Apparently others are experiencing the same issues: [Ubuntu 18.04 and bluetooth speaker JBL Charge 3]("https://askubuntu.com/questions/1029233/ubuntu-18-04-and-bluetooth-speaker-jbl-charge-3/1036127")

---

### Post by medina12345678910 on 2018-10-14
Try disconnecting it from the bluetooth and reconnecting it again.

---

### Post by thomas72 on 2018-11-25
> **medina12345678910 said:**
> Try disconnecting it from the bluetooth and reconnecting it again.
Well... obviously I've already tried that before posting on the forum, check #3.
I've also updated bluez to v5.50 with no luck

---

