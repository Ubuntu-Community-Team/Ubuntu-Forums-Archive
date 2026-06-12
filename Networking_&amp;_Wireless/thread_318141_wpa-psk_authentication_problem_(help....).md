---
title: "wpa-psk authentication problem (help....)"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by hydroman_al on 2006-12-13
Hello everybody!
This is my problem:I have already connected a D-link usb adapter DWL-122 on my computer(It works properly).I have linux ubuntu and an access point D-link which uses wpa-psk authentication as connection protocol.On my network control panel i checked my authentication to be wpa and used the encryption key needed but i still cannot have my linux software to identify wpa protocol and get connected with the access point.Any suggestions?I count on you...

---

### Post by n00b@linux on 2006-12-13
[Read this thread](http://www.ubuntuforums.org/showthread.php?t=202834).  You won't be disappointed.

I wasted hours trying to get WPA-PSK working on my Intel PRO/Wireless 3945ABG network adapter.  I read the thread and had it up and running in 5 mins.

---

### Post by hydroman_al on 2006-12-22
First of all...I want to thank you n00b@linuxfor your reply.Secondly I would like to say to you that I checked your proposed thread,I followed the instructions and it seems that I had followed correctly the steps.The problem is that I still cannot have my usb adapter working on wpa-psk....Could you reply with the ndiswrapper  command line for my adapter?If you have it of course...Thanks a lot!(your proposed thread was really great....)

---

### Post by n00b@linux on 2007-01-04
Are you using Edgy or Dapper?  There is a problem with ndiswrapper in Edgy: [https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983).
Also, if you read this document: [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb) you'll see that the prism2_usb kernel module works on your DWL-112 BUT this kernel module does not support WPA!  Therefore, you only hope IS to try ndiswrapper and see if you can get WPA working that way.
Could you post the result of ```
sudo lsusb -v
``` so that I can double check the chipset used in your DWL-112?

---

