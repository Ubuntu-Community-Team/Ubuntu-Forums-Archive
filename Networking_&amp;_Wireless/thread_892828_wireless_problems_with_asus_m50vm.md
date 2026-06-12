---
title: "wireless problems with asus m50vm"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by themerchant on 2008-08-17
I used this guide:
cd /home/<username>/Desktop/driverReplace <username> with your own username.


To install the driver, type the following: 


Code:
sudo ndiswrapper –i filename.infReplace filename.inf with the name of the .inf file you discovered in the previous steps. 


Next, type the following: 


Code:
sudo ndiswrapper –m 
gksu gedit /etc/modulesThis will open the modules configuration file for editing. On a new line at the bottom, add the following: 


Code:
ndiswrapperEnsure you press Enter after adding the line. 

============================================================
---------------------------------------------------------------

Now my drivers are active by ndiswrapper, but the wireless application won't let me or show me the networks available. Btw this is on a M50VM asus laptop. I'm using ndiswrapper on ubuntu 7.10. The wireless card is a Atheros AR928x.

---

### Post by RaZe42 on 2008-09-10
The Atheros WLAN card won't work with ndiswrapper. You should try the ath9k wireless driver

[http://ubuntuforums.org/showthread.php?t=874097&highlight=ath9k]("http://ubuntuforums.org/showthread.php?t=874097&highlight=ath9k")

---

### Post by ARam1024 on 2009-02-11
I also had problems with wireless on my ASUS M50VM-B1.  I fixed them recently by using the intrepid backports module and deleting /etc/acpi/start.d/60-asus-wireless-led.sh.  You can read about it [here]("http://ubuntuforums.org/showthread.php?p=6719143#post6719143").

---

