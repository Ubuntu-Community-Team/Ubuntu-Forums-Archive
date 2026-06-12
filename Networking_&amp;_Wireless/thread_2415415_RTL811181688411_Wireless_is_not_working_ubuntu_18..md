---
title: "RTL8111/8168/8411 Wireless is not working ubuntu 18.10"
date: 2019-03-25
forum: Networking &amp; Wireless
---

### Post by alekz7 on 2019-03-25
Ethernet is ok but the wireless is not working, this is my information:
[http://paste.ubuntu.com/p/7xPSC4FtpF/](http://paste.ubuntu.com/p/7xPSC4FtpF/)
please help me, i dont want to come back Windows :P
```
########## wireless info START ##########

Report from: 25 Mar 2019 09:34 CST -0600

Booted last: 25 Mar 2019 00:00 CST -0600

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.10
Release:	18.10
Codename:	cosmic

##### kernel ############################

Linux 4.18.0-16-generic #17-Ubuntu SMP Fri Feb 8 00:06:57 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:84b2]
	Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:d723]
	Subsystem: Hewlett-Packard Company Device [103c:8319]
```

---

### Post by jeremy31 on 2019-03-25
First step is to reboot, go into BIOS and disable Secure Boot, leave any Secure Boot keys alone
Then in terminal do
```
sudo apt-get install dkms git build-essential
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
sudo cp -r rtlwifi_new/firmware/rtlwifi/ /lib/firmware/rtlwifi/
echo "options rtl8723de ant_sel=2" | sudo tee /etc/modprobe.d/rtl8723de.conf
```
Reboot

---

### Post by alekz7 on 2019-03-25
Thank you, the wireless and ethernet are working,

Why if I made a ping to [www.google.com.mx](www.google.com.mx) the same ip is responding,

It make me think a kind of "man in the middle", is this normal?

~ &#57520; ping [www.google.com.mx](www.google.com.mx)
PING [www.google.com.mx](www.google.com.mx) (172.217.14.163) 56(84) bytes of data.
64 bytes from zzzzzz.net (172.217.14.163): icmp_seq=1 ttl=50 time=85.9 ms
64 bytes from zzzzzz.net (172.217.14.163): icmp_seq=2 ttl=50 time=90.3 ms
^C
--- [www.google.com.mx](www.google.com.mx) ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 2ms
rtt min/avg/max/mdev = 85.942/88.112/90.282/2.170 ms
~ &#57520; ping [www.google.com.mx](www.google.com.mx)
PING [www.google.com.mx](www.google.com.mx) (172.217.14.163) 56(84) bytes of data.
64 bytes from zzzzzz.net (172.217.14.163): icmp_seq=1 ttl=50 time=268 ms
64 bytes from zzzzzz.net (172.217.14.163): icmp_seq=2 ttl=50 time=89.3 ms

---

### Post by jeremy31 on 2019-03-25
Are you saying the same IP responds if you ping google.com or google.com.mx?

---

