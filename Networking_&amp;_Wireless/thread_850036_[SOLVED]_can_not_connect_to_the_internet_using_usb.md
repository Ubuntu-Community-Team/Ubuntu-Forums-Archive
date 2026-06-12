---
title: "[SOLVED] can not connect to the internet using usb cable modem"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by nir2000 on 2008-07-05
Hello everybody 
I'm totally new to Linux but I decided to give it a try since it was very easy to download it from the internet. I downloaded ubuntu version 8.04 and everything went quite smoothly with the installation, but no matter how hard I have tried I could not establish an internet connection. I'm using a cable modem via a USB connection which works just fine with window xp. I read few suggestions to solve this problem but all of which were very complicated to implement. I simply can't believe that the programmers of Linux made so simple a task such as connecting a USB cable modem a difficult one. If it's possible I would need a detailed answer on how to connect to the internet.
I would greatly appreciate any help given to me on this issue.
Thank you in advance.
Nir

---

### Post by superprash2003 on 2008-07-05
assuming that your modem is recognized, its required to know whether you are getting an ip from your router.. go to the terminal(applications->accessories) and type ifconfig and post output here

---

### Post by nir2000 on 2008-07-08
Problem solved!
The problem was very simple to solve as I suspected from the begining.I called to my ISP and he simply told me to erase the dialer from xp(since I have also xp on this machine).also my ISP phoned to my cable company and told them to connect me constantly to the internet so that my pc would be able to draw an IP. after that we made sure that I can surf the internet in xp without a dialer, I closed xp opened ubuntu and in Network I simply highlighted the first option("connecting two lines", after I unlock the window)and in properties i choose dhcp. that is all now I have internet.

---

