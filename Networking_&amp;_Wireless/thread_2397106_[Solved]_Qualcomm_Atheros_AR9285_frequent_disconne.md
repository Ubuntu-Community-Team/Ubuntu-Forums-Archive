---
title: "[Solved] Qualcomm Atheros AR9285 frequent disconnect and reconnect UBUNTU 18.04 lts"
date: 2018-07-25
forum: Networking &amp; Wireless
---

### Post by subhadeep-sengupta on 2018-07-25
Hi guys, I just happened to solve my wireless card frequent disconnection issue. i'm using a Z570 Lenovo laptop and running UBUNTU 18.04.

  1. navigate to  modprobe.d directory as shown below 
cd /etc/modprobe.d/  

2. create a new file  ath9k.conf as shown below  
sudo nano ath9k.conf  

3 paste the below  

options ath9k nohwcrypt=1  

4. run modprobe

sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

5. run the below command 
 
sudo nano /etc/default/crda

REGDOMAIN=IN 

*Note: im in India so i would preferably use IN, you should be using the country code you livein.... for country code, please check the below wiki page

[https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

Save and exit.  reboot your computer.  

you may try this for other Qualcomm Atheros wireless cards aswell.it wont hurt as you can always delete the file in case it doesn't solve your problem.

---

### Post by chrischmbrs5 on 2018-08-05
Thank you Subadeep, seems same problem solved here to. All best, Chris

---

