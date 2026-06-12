---
title: "Huawei E220 on Hardy"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by khalid1100 on 2008-05-16
My old system was Gutsy and I was connecting to the internet using Vodafone mobile broadband on Huawei E220 USB modem. I used vodafone connect card program to make the connection.
My problem now after upgrading to Hardy the program stopped working all together. It showes the startup window and then crashes. I removed it with all the dependencies packages and reinstalled them again and still did not work.
I would like to know if there is anyother programs can be used to connect using Huawei E220 USB modem.
Thank you.

---

### Post by jorgen99 on 2008-05-16
I also had problems in Hardy.

I unplugged my E220, did: ```
tail -f /var/log/messages
``` and plugged it in again and i got a number of these:
```
[ 1402.045579] airprime 3-2:1.0: airprime converter detected
[ 1402.045974] usb 3-2: airprime converter now attached to ttyUSB0
[ 1402.046354] usb 3-2: airprime converter now attached to ttyUSB1
[ 1402.046762] usb 3-2: airprime converter now attached to ttyUSB2
[ 1402.047044] usbcore: registered new interface driver airprime

```
and further down:
```

[ 1407.252519] airprime ttyUSB0: airprime_open - failed submitting read urb 0 for port 0, error -2

```

So airprime (I don't know what it is) seems to be causing some problems. So after removing the airprime kernel module with:
```
sudo modprobe -r airprime
```
I could use wvdial without errors again.

As far as I understand it doing modprobe -r doesn't remove the module permanently. If you want to disable it (since I don't know what airprime is, maybe it's not something you should do) you can for instance follow the advise in this post: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105545]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105545")
> 

After upgrading to Hardy, my modem was recognized as a airprime converter and was initializes incorrectly.

Adding:
# remove e220-conflicting airprime
blacklist airprime

To the bottom of /etc/modprobe.d/blacklist and rebooting seems to have solved the problem for me.


---

### Post by khalid1100 on 2008-05-17
Thank you for the reply I will try your method and keep you posted.

---

