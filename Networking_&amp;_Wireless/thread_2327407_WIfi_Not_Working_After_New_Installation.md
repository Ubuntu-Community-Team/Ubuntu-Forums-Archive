---
title: "WIfi Not Working After New Installation"
date: 2016-06-10
forum: Networking &amp; Wireless
---

### Post by Akintunde on 2016-06-10
Hello Everyone. 

I installed ubuntu studio on my external hard drive and i did the partition correctly. Now that i booted my pc from my externel hard drive,

My wifi is not working again,

While i doing research on what coursed it. i found a script here that will collect information concerning the hardware devices,

So i uploaded the information here [https://drive.google.com/file/d/0B0Pf0a3PIL2pQjRQTEF4Z0dTZWM/view?usp=sharing](https://drive.google.com/file/d/0B0Pf0a3PIL2pQjRQTEF4Z0dTZWM/view?usp=sharing)

Here is the thread to were i got the script. [http://ubuntuforums.org/showthread.php?t=2228438](http://ubuntuforums.org/showthread.php?t=2228438)

Kindly go through it and let me know how i could solve the issue.

Thanks 

I look forward to your responses

---

### Post by Rick St. George on 2016-06-10
Your posted script / result shows you have the BroadCom 4315/4312 networking device. Here is what worked for me.

Follow the instructions on the following page. Any problems, let us know!
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

Note: you can see what I did here;
[http://ubuntuforums.org/showthread.php?t=2326512&page=3](http://ubuntuforums.org/showthread.php?t=2326512&page=3)

Peace,
Rick

---

### Post by praseodym on 2016-06-10
For the low power chipset LP-PHY you need the missing firmware:

```
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot. If LAN doesn't work, too, change the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.042.00-1_all.deb
sudo dpkg -i r8168-dkms_8.042.00-1_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
and reboot again

---

### Post by Akintunde on 2016-06-11
> **praseodym said:**
> For the low power chipset LP-PHY you need the missing firmware:

```
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot. If LAN doesn't work, too, change the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.042.00-1_all.deb
sudo dpkg -i r8168-dkms_8.042.00-1_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
and reboot again


Wow.... You are a life saver... Thank you very much... 

It worked and am currently using it to reply this....

---

