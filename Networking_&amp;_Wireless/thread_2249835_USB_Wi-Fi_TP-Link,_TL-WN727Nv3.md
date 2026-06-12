---
title: "USB Wi-Fi TP-Link, TL-WN727Nv3"
date: 2014-10-24
forum: Networking &amp; Wireless
---

### Post by blizzard87 on 2014-10-24
Hi Ubuntu Geeks,
I'm new Lubuntu User. I'm using Lubuntu 14.04 LTS. Migrating from Windows OS for purpose of utilising my old netbook.
After doing several research for finding solution with regards to USB Wi-Fi TP-Link [TL-WN727Nv3] I'm totally lost.
I don't know which script/code/driver or whatever suitable for this device to working on.
I'm afraid I'll conflicting the system just because I install all drivers that I found over the net.
I also tried using ndiswrapper. The hardware is present but no wifi connection found.
I know this post would be redundent from the previous post. I'm sorry for that.
I hope someone would guide me to solve this problem.
Thank you.

---

### Post by mörgæs on 2014-10-25
> **blizzard87 said:**
> 
I'm afraid I'll conflicting the system just because I install all drivers that I found over the net.

So am I. Ndiswrapper could add even more trouble. 

Do you have anything of value on the computer or would it be possible to reinstall (using wired internet access) to begin on a clean slate?

---

### Post by praseodym on 2014-10-25
Hi,

remove Ndiswrapper and try this driver instead:
```

sudo apt-get remove --purge ndiswrapper* ndisgtk
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget media.cdn.ubuntu-de.org/forum/attachments/13/16/4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz
sudo tar xvf 4365112-Ralink_5370sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5370sta -v 2.5.0.3
sudo dkms build -m Ralink_5370sta -v 2.5.0.3
sudo dkms install -m Ralink_5370sta -v 2.5.0.3 
sudo mkdir -p /etc/Wireless/RT2870STA
sudo cp /usr/src/Ralink_5370sta-2.5.0.3/src/RT2870STA.dat /etc/Wireless/RT2870STA 
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist-rt2800usb.conf
```
Reboot.

---

### Post by praseodym on 2014-11-15
Please show
```

lsusb
iwconfig
rfkill list
```

---

### Post by blizzard87 on 2014-11-22
safuan@safuan-H-S30N:~$ lsusb
Bus 001 Device 003: ID 0603:8124 Novatek Microelectronics Corp. 
Bus 001 Device 005: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 03f0:a407 Hewlett-Packard 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
safuan@safuan-H-S30N:~$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


eth0      no wireless extensions.
safuan@safuan-H-S30N:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by praseodym on 2014-11-22
Your wireless is off. Any button, switch, key combination? Checked the BIOS if it can be turned on there?
```

sudo rfkill unblock all
rfkill list
```
What kind of computer is it?

---

### Post by blizzard87 on 2015-03-06
Thanks everybody. All the commands can be executed.
Now, I can enable the Wi-Fi and use this netbook to connect the Internet. 

p/s: Sorry for the late, late, late, late response and feedback.

---

