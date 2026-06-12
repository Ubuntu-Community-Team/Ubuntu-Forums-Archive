---
title: "Internet Help for a Beginer"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by careyrn on 2009-07-31
Just got my brand new Asus EeePC 1005HA in today and decided on ubuntu after a friend told me how nice it was.  Install went well got it all up and running from a flash drive install.

Only problem I'm having is with the internet.  I have a working wirless network in my house but its not picking it up.  I click on the wireless icon and it has two options No network devices available (in grey) and VPN Connections    >.  Anyone have any suggestions for a huge Ubuntu noob.

Thanks.

---

### Post by Tclarkie on 2009-07-31
is it a hidden network

---

### Post by Humanum on 2009-07-31
Which version of Ubuntu have you installed ?

---

### Post by wojox on 2009-07-31
Here's a page for you to go by:

[https://help.ubuntu.com/community/NetworkDevices#Wireless%20networking](https://help.ubuntu.com/community/NetworkDevices#Wireless%20networking)

---

### Post by Chaosphere on 2009-07-31
I'm having a similar problem. I've gotten as far as discovering that the Broadcom wireless card in my Dell XPS M1330 is disabled, but I can't enable it.

The user guide above may be great for somebody with some advanced knowledge of Ubuntu, but is extremely tedious for a beginner who doesn't want to spend the whole day enabling a basic function like internet access.

Help (in simpler terms) would be greatly appreciated!

---

### Post by lavezarez on 2009-07-31
I'm also having a problem with my Broadcom wifi BCM4318. _**wireless is disabled**_ and I can't enable it.

followed the instructions of this link: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

and did the ***sudo apt-get install **b43-fwcutter* **then restarted after installation was finished.
*[FONT=Lucida Sans Unicode]**lsmod | grep b43**[/FONT]* returns
b43                 131484 0
mac80211        217592 1 b43
input_polldev    11912   1 b43
ssb                  41220   1 b43
led_class          12036   1 b43

---

