---
title: "DSL problem"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by smartAgent on 2015-08-23
Hello everybody ... 

I have bought a DSL connection and a DSL modem .. On windows d modem worka fine and internet is smooth .. But on ubuntu something is not correct .. On ubuntu the internet works but while syncing a repository or fetching or cloning via terminal the internet is very slow .. It does not fetch properly .. Several times i get this error "fetch: unable to create <repo name>" sometimes i get "could not resolve host <repowebsite> .. Before DSL i had a local ISP connection and the syncing of repos would go rapid smooth without any errors .. Bt in DSL i get these errors .. So please can someone help me on fixing this issue .. I am new to DSL on ubuntu otherwise i ws working with broadband local isp connection .. 

II hope someone replies to this thread very soon .. 
Thank You So Much

---

### Post by praseodym on 2015-08-23
Please run the wireless script from the sticky thread and show the outputs.

---

### Post by smartAgent on 2015-08-23
Thanx for your reply sir .. i have attatched the wirelss-info file ..

---

### Post by praseodym on 2015-08-24
Download these 2 files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb)

[http://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz](http://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz)

Installation

```
cd ~/Downloads
sudo dpkg -i *.deb
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by smartAgent on 2015-08-24
Sir in this command "[COLOR=#000000][FONT=Ubuntu Mono]sudo dkms add -m r8168-dkms -v 8.040.00" i get "sudo: command not found" .. i have downloaded those two files saved them in Downloads .. 

Sir will this solve my issue ?

Thanks For Your Reply [/FONT][/COLOR]

---

### Post by praseodym on 2015-08-25
Sorry, first install the *.deb via

```
sudo dpkg -i ~/Downloads/*.deb
```

then proceed as described, I corrected the post above

---

