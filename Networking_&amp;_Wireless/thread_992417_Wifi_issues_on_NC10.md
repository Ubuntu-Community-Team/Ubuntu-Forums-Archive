---
title: "Wifi issues on NC10"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by redcaz on 2008-11-24
Please Help. I have just bought a Samsung NC10 and this is the first time I have tried to use Linux. I have managed to set up the linux but cannot get the wireless to work and therefore have no internet access. I am writing this on my old laptop. I have have had a look through the forums but to be honest most of what people have said has gone right over my head. Is there anybody who could give me some advice in fairly simple terms on how I can fix this. I am able to transfer files by external hard drive. 
I really appreciate any help as I bought this laptop with the intention of using linux in the future.
Thanks!
Oh, and my internet is about to be cut off too.

---

### Post by Olivier2371 on 2008-11-24
Hi there,

Which version of Linux are you talking about?

Open the terminal(if you don't know),

Applications-> Accessories->Terminal

type in ( to determine what type of wireless adapter you have)

lspci -v | less  

(post the reply)

Type in : ( to check the status of your wireless connection)

iwconfig

(Post the reply)

---

### Post by Jon Bradbury on 2008-11-29
The answer is out there...

[https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros](https://help.ubuntu.com/community/NC10#Wireless%20Networking%20-%20Atheros)

We got it sorted...

:)

---

### Post by jifop on 2008-12-14
hi there, i tried your guide and i cant seem to get wifi working, maybe i'm doing something wrong but i get the message "E: couldn't find package linux-backports-modules-intrepid"

any ideas whats up?


sudo su
echo "blacklist ath_pci" >> /etc/modprobe.d/blacklist
echo "blacklist ath_hal" >> /etc/modprobe.d/blacklist

Finally, install the Madwifi driver:

sudo apt-get install linux-backports-modules-intrepid
sudo su
echo "ath5k" >> /etc/modules

After rebooting the driver should load and wireless networks should be listed in the Network Manager Applet.

---

