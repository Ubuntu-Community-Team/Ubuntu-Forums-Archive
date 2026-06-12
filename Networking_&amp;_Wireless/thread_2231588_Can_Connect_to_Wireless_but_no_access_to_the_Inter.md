---
title: "Can Connect to Wireless but no access to the Internet"
date: 2014-06-26
forum: Networking &amp; Wireless
---

### Post by william36 on 2014-06-26
I have just installed ubuntu 14.04 onto a dell inspiron 1420 and while i can connect to the wifi i have no access to the internet. any help would be appreciated.

Specs: [http://www.pcworld.com/product/30465/inspiron-1420-notebook.html](http://www.pcworld.com/product/30465/inspiron-1420-notebook.html)

---

### Post by papibe on 2014-06-26
Hi william36. Welcome to the forum ):P

Edit: are you able to connect using a ethernet cable? If so:

Please open a terminal, and paste this command in the terminal:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If not, you would have to download the script, move it to your machine with a USB stick, and then run it

Regards.

---

### Post by william36 on 2014-06-26
managed to find an ethernet cable and here is the file that came out of the cript.


[ATTACH]254264[/ATTACH]

---

### Post by papibe on 2014-06-26
Thanks.

Do you have Internet with the wired connection?

I see that you have a Broadcom wireless adaptor. Did you check 'Additional Drivers' to see if there's a newer driver?

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
nslookup ubuntu.com

dig ubuntuforums.org
```
Regards.

---

### Post by william36 on 2014-06-26
okay so the internet works over a wired  connection. I went  to the additional drivers section but there was nothing so i went to their website and downloaded and installed the drivers. problem is  now my wirelesscard doesnt seem to be turning on at all.

---

### Post by Hadaka on 2014-06-26
Hi
Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
your card: will probably work best with the linux-firmware-nonfree driver
it is currently using the wl driver. so lets remove that and load the nonfree
please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf #ignore any error message
```
then load..
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
BOOT
remove the cable and test  wireless

---

