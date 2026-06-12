---
title: "How do I install the Atheros driver Package I downloaded?"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by Lupgaru on 2008-06-21
I am trying to get my wireless (Atheros AR 5007EG Wireless Network Adapter to work on my ACER 3680). I am currently using a Linksys USB Wireless Modem for Internet access. 
    I downloaded a Linux Package from Atheros (madwifi-0.9.4tar.gz) but I don't know how to install it. Anyone have advice? E-mail is [email]lupgaru@gmail.com[/email]
    By the way, is this the right package?

---

### Post by Midwest-Linux on 2008-06-21
NOTE>>>>>
Just be aware at this time the mad wi-fi site is down. I tried to re install my wireless. It would not install and found out its because the site is down. 

But you open up the terminal and type this in script in. (Just cut and paste it)


sudo apt-get install build-essential


(After that is taken care of, then use this script)

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make 

sudo make install

sudo modprobe ath_pci

sudo reboot

---

