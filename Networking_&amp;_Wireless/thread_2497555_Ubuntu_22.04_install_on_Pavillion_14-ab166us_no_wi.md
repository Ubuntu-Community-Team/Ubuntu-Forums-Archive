---
title: "Ubuntu 22.04 install on Pavillion 14-ab166us: no wifi or ethernet: Where do I start?"
date: 2024-05-09
forum: Networking &amp; Wireless
---

### Post by deh6 on 2024-05-09
Pavillion `14-ab166us (born date: 08.25.2015) had Windows 10 with a lot of free space. I shrank the windows partition and added U22.04. I am able to boot U22.04, but the ethernet and wifi will not reach the internet, so 'apt-get install' is not possible. The ethernet, when plugged into my newer router, does show a connection, but doesn't reach the internet. Plugged into an older router it doesn't even show a connection. I have a number of other machines that will connect to the Internet via ethernet when plugged in to either router.

The wifi and ethernet both work when it is running Windows 10.

During the install the live USB was not able to connect by either wifi or ethernet. Hence, packages such as network-manager. iwconfig apparently are missing. 'ifconfig' only shows 'lo; and 'eno1'

It looks like I need some way to get the networking packages and drivers installed, such as downloading on another machine and transferring them via thumb drive, but I don't know where to start.

---

### Post by gezzer2 on 2024-05-10
just asking ..
have you checked within settings/network the DNS settings.

change the DNS (IP4)  settings from auto to 1.1.1.1 or 8.8.8.8

see if the connection works now. i've had it several times no internet but it was just the DNS settings for some reason ..

---

### Post by deh6 on 2024-05-10
Thanks for the response. The problem is that there appears to be no drivers or network support, so changing DNS settings doesn't exist.

---

### Post by gezzer2 on 2024-05-10
if there is network installed it maybe worthwhile going back into the live system using the USB and re-check the network to see if its working.
if its not then maybe post a list of the network components that are in the system so someone can have a look at them ..

---

### Post by deh6 on 2024-05-10
I'm giving up. Amongst the many attempts, the following addresses the problem, and is quite extensive, however I wasn't successful--

[https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers?page=2&tab=scoredesc#tab-top](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers?page=2&tab=scoredesc#tab-top)

---

