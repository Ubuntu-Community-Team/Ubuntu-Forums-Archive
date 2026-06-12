---
title: "Ubuntu losing internet access, forcing me to turn Ethernet off and on again"
date: 2019-04-12
forum: Networking &amp; Wireless
---

### Post by boruno on 2019-04-12
Hello, i'm a "new" linux user (tried to migrate many times in the past without success, but this time i'm committing way more to the OS), and i'm really trying to make things work, but one of the things that keeps bugging me off is the fact that the internet on my machine keeps disconnecting from time to time (maybe once each hour?), and then I have to turn the connection off and on again.
Here is the pastebin with my information [http://paste.ubuntu.com/p/bbpj586gVv/](http://paste.ubuntu.com/p/bbpj586gVv/)
and some relevant information that may be useful:
*I'm running Ubuntu 18.04.2 on a dualboot with windows 10 (each one in a separate HDD)
*I used the "timedatectl set-local-rtc 1 --adjust-system-clock" to keep both systems with the same clock configuration
*my PC is a desktop and doesn't have a wifi adapter. I'm connected via Ethernet

Thanks in advance!

---

### Post by TheFu on 2019-04-12
Does the same issue happen in Windows?

If it does, then look at hardware - the NIC, cables, ports in the switch, router, etc.

Besides that, might take a look at the specific driver being used. The 69 driver might not be the best for the card revision. The 68 driver is sometimes better, but it depends on the card revision. Check into that. Or wait for someone else who knows more specifics to respond.

---

### Post by VMC on 2019-04-13
I never thought it would be any of my OS's causing the issue, but in the past, a few months back, I had issue with my internet resetting. I thought it was my provider. At the time I was using 18.04. I have since moved on to 19.04. 
I'm not sure if Windows ever had the issue. It didn't happen all the time. Just once in a while. Maybe some log file to look at. 'dmesg' and look right after it happens. By the way I have the exact internet hardware as you.

---

### Post by praseodym on 2019-04-14
Change the driver

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/55/13/3005217-r8168-dkms-8.046.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.046.00.tar.gz -C /usr/src
sudo dkms add -m r8168 -v 8.046.00
sudo dkms build -m r8168 -v 8.046.00
sudo dkms install -m r8168 -v 8.046.00
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by boruno on 2019-04-16
Okay, I changed the driver from the __69 to the __68 version, but the problem still persists.
Once every couple hours my internet stops working, and I have to disconnect and then connect again.

---

### Post by TheFu on 2019-04-16
Please re-read post #2.

---

