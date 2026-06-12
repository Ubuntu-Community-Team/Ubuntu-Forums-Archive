---
title: "Ralink RT5372/Lubuntu 13.10/AMD Athlon XP2800+ PC WIFI does not connect"
date: 2014-02-15
forum: Networking &amp; Wireless
---

### Post by alberto8 on 2014-02-15
If I boot from the CD, i can connect to my wifi very easily. but when i boot from the installed lubuntu in my PC, wifi never connects. Am I missing something?

---

### Post by wildmanne39 on 2014-02-15
Hi, from the livecd do the following:

Copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by alberto8 on 2014-02-15
zip file Attached. thanks.

---

### Post by wildmanne39 on 2014-02-15
Please post the file from your installed ubuntu so we can compare the difference.
Thanks

---

### Post by alberto8 on 2014-02-15
attached is the file generated while using the installed lubuntu. please note that my wifi router was disabled while i was generating this file. i can't have both my wired connection and wifi router enabled at the same time, since my cable modem would only allow one enabled.

---

### Post by wildmanne39 on 2014-02-15
> please note that my wifi router was disabled while i was generating this file. i can't have both my wired connection and wifi router enabled at the same time, since my cable modem would only allow one enabled. That should not be the case.

You do need to shut down your computer unplug your usb ehternet adaptor.

Is this your network name conexionwifi ?

Boot back up with your wifi adaptor plugged in but not ethernet.

Now run copy and paste all commands on line at a time for accuracy.

```
echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb 
sudo modprobe -v rt2800usb
```
Then:
```
sudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off 
```
above exit0, then save gedit, close.

Set your wireless settings to match the screenshots.
Reboot with usb ethernet unplugged.
Thanks

---

### Post by alberto8 on 2014-02-20
"echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf  
sudo modprobe -rfv rt2800usb "

the second line freezes my computer, then i can't do anything else.

---

### Post by wildmanne39 on 2014-02-20
I have never known that to happen, did you copy and paste the commands for accuracy one line at a time?
Thanks

---

