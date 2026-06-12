---
title: "No WiFi adapter found in Ubuntu 18.04, HP Laptop15-da0058nl"
date: 2018-10-17
forum: Networking &amp; Wireless
---

### Post by chak14 on 2018-10-17
I've installed Ubuntu with normal settings, but i can't use wi-fi since it keeps telling me "no wi-fi adapter found".
I've tried to follow the solution posted on this thread:

[https://ubuntuforums.org/showthread.php?t=2392454](https://ubuntuforums.org/showthread.php?t=2392454)

but it didn't work out for me.

Here there is the pastebin link:

[http://paste.ubuntu.com/p/SsnmX6yYjt/](http://paste.ubuntu.com/p/SsnmX6yYjt/)

thank you for the support.

---

### Post by chili555 on 2018-10-17
> Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
	Subsystem: Hewlett-Packard Company RTL8821CE 802.11ac PCIe Wireless Network Adapter [103c:831a]You need this process instead: [https://askubuntu.com/questions/1070593/lenovo-thinkpad-e480-no-wifi-adaptor-found-in-ubuntu-18-04/1070645#1070645](https://askubuntu.com/questions/1070593/lenovo-thinkpad-e480-no-wifi-adaptor-found-in-ubuntu-18-04/1070645#1070645)

Post back if you need additional guidance.

---

### Post by chak14 on 2018-10-17
i don't know why but it doesn't let me run dkms-install.sh

"lorenzo@lorenzo:~/rtl8821ce$ sudo ./dkms-install.sh
sudo: ./dkms-install.sh: command not found"
i checked and the file is in the rtl8821ce repository.

---

### Post by chili555 on 2018-10-17
Do you have dkms installed? ```
sudo apt update && sudo apt install dkms
```Also, you may need to make the install script executable:```
sudo chmod +x dkms-install.sh
```And while we are at it, in case you ever need it, do the same to the uninstall script:```
sudo chmod +x dkms-remove.sh
```

---

### Post by chak14 on 2018-10-17
this is the output:
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83,2 kB]    
Hit:2 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) bionic InRelease                     
Hit:3 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:4 [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Fetched 83,2 kB in 1s (55,7 kB/s)                             
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version (2.3-3ubuntu9.2).
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.




edit: i've also run the sudo apt list--upgradable command and this is the output if needed:


libssh-4/bionic-security 0.8.0~20170825.94fa1e38-1ubuntu0.1 amd64 [upgradable from: 0.8.0~20170825.94fa1e38-1build1]
N: There is 1 additional version. Please use the '-a' switch to see it

---

### Post by chili555 on 2018-10-17
See my edit above about chmod.

---

### Post by chak14 on 2018-10-17
Now it works, thank you.(the problem is solved)

---

### Post by chili555 on 2018-10-17
> **chak14 said:**
> Now it works, thank you.(the problem is solved)I'm glad to hear it's working!

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

