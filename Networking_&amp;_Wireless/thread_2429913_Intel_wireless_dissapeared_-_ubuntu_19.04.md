---
title: "Intel wireless dissapeared - ubuntu 19.04"
date: 2019-10-24
forum: Networking &amp; Wireless
---

### Post by picrazydude on 2019-10-24
Hi all. I had a crash and did the recovery where you have to hit y like three thousand times, but then my wireless driver seems to have been corrupted as the computer isn't seeing it. I'm on an asus vivobook.   Used the script:

[http://paste.ubuntu.com/p/fBmKQSBFr4/](http://paste.ubuntu.com/p/fBmKQSBFr4/)

I'm connected right now through one of my pi generic internet bugs.  I plugged it in and it just worked, but the intel card is still dead.  The network is coming up as unclaimed. I've googled around and tried some stuff but nothing has worked. 

*-network UNCLAIMED       
       description: Network controller
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:ef000000-ef001fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:3
       logical name: wlx8c882b00078d
       serial: 8c:88:2b:00:07:8d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu ip=10.1.10.79 multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by picrazydude on 2019-10-25
Oh and it isn't hardware. I can boot from a USB and the wifi works fine.

---

### Post by jeremy31 on 2019-10-25
I would try ```
sudo apt install --reinstall linux-modules-extra-$(uname -r)
```
Then reboot

---

### Post by picrazydude on 2019-10-25
Thankyou for answering 

I tried it and this is what I got. Did a ping afterward to show you that I'm online. 

 sudo apt install --reinstall linux-modules-extra-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-modules-extra-5.0.0-20-generic is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@user-X510UAR:~$ ping zerohedge.com
PING zerohedge.com (35.227.58.252) 56(84) bytes of data.
64 bytes from 252.58.227.35.bc.googleusercontent.com (35.227.58.252): icmp_seq=1 ttl=39 time=46.7 ms
64 bytes from 252.58.227.35.bc.googleusercontent.com (35.227.58.252): icmp_seq=2 ttl=39 time=53.1 ms

---

### Post by jeremy31 on 2019-10-25
Install all updates using the GUI and reboot

---

### Post by picrazydude on 2019-10-28
Thankyou again. It worked. I had disabled updates to prevent unexpected  upstream headaches and when I turned them back on it updated. On reboot  the intel card is back.

---

