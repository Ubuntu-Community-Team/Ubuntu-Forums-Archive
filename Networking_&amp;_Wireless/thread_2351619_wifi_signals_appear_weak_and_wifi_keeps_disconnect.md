---
title: "wifi signals appear weak and wifi keeps disconnecting"
date: 2017-02-05
forum: Networking &amp; Wireless
---

### Post by aliole4731 on 2017-02-05
Hi i just joined the UBUNTU family so i don't know much .I know a lot of people have asked the same question but I read somewhere that although my problem might seem similar to others it may be completely different.So here is the problem:the wi-fi keeps disconnecting.
 I tried the steps given here "https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers".
It turns out I have a wl driver,i think:o.I have ubuntu 16.04

---

### Post by ajgreeny on 2017-02-05
Go to Wireless-Info in my signature below and run the script, then paste back here the report you get from that. It will help us to find a solution for you.

---

### Post by aliole4731 on 2017-02-05
this is from running the script

---

### Post by ajgreeny on 2017-02-05
This is not an adapter I have any experience of but go to the thread at [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) and follow the processes there to see if that helps you.

If still no go, come back again and I'm sure someone who knows more about wifi problems than I do will try to help you.

---

### Post by aliole4731 on 2017-02-05
I went through the thread and it looks like I already have the correct driver :D(bcmwl-kernel-source).So I'm thinking its not a driver problem?)

---

### Post by praseodym on 2017-02-05
This driver may be too old. Additionally, it still loads the wrong native one:
```

sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://ubuntu-master.mirror.tudos.de/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-5_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-5_all.deb 
sudo apt-get remove --purge bcmwl-kernel-source
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by aliole4731 on 2017-02-06
thank you

---

### Post by wildmanne39 on 2017-02-06
If your issue is resolved please use thread tools at the top of the page to mark it solved, if not run the wireless script again and post the results here.

---

