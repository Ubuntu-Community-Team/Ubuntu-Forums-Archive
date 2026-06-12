---
title: "Intel wireless card help"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by simcityfreak4 on 2007-06-04
I installed the ndiswrapper packages, but I need to find the NDIS wrapper for my card.  I have an Inter PRO/Wireless 3945 card.

---

### Post by chili555 on 2007-06-05
I wonder why you installed ndiswrapper when, with the installation of *linux-restricted-modules* the ipw3945 is supported perfectly. Post back if you need help getting the built-in module going.

---

### Post by simcityfreak4 on 2007-06-05
Can you please help me get the built-in module going then?

---

### Post by chili555 on 2007-06-05
Sure:```
sudo apt-get install linux-restricted-modules-generic
```Other dependencies will be proposed; you may safely accept them. Then, assuming you are running Feisty, open System -> Administration -> Restricted Driver Manager and enable the Intel Pro Wireless 3945 driver. Check to see if your wireless interface has appeared.```
iwconfig
```You should now have a wireless interface: eth1. You should now go to System -> Administration -> Network and check off Roaming for your wireless interface. You should now be able to go to the Network Manager icon and enable your connection.

---

### Post by simcityfreak4 on 2007-06-05
When I ran the first command in the terminal this is what it says:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I went through the rest of your steps and didnt get anywhere.  Would it be because im try to use it on a Live CD?

---

### Post by chili555 on 2007-06-06
> Would it be because im try to use it on a Live CD?Doubtful. 

Let's try:```
sudo modprobe ipw3945
iwconfig
```Did eth1 appear?

The next most likely issue is called *rf_kill;* in other words, the hardware switch or key combination has turned the wireless card off and it needs to be turned on. Let's take a look at:```
sudo cat /var/log/messages | grep -i Kill
```We'll get it! Thanks.

---

### Post by simcityfreak4 on 2007-06-06
eth1 does appear:

```
eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:433   Missed beacon:0

```

Ran the 2nd thing and nothing happened.

---

### Post by simcityfreak4 on 2007-06-06
Yay! I was able to figure out what was wrong!  I was using the wrong encryption on my key.  Thanks for trying to help me out!

---

### Post by chili555 on 2007-06-06
Glad it's working...without ndiswrapper.

---

