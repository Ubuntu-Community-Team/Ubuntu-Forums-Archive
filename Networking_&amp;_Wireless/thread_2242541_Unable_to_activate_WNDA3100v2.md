---
title: "Unable to activate WNDA3100v2"
date: 2014-09-02
forum: Networking &amp; Wireless
---

### Post by Trad_dog on 2014-09-02
Hi there, 

Varun suggested I'd post a new thread. 
I have an internal wifi card that chili55 managed to put to work ages ago. However, I realise
I cannot connect to most hot spots through the internal card. 
I thought I should try with a dual band wifi device. The shop where I went had hardly any choice
and it looked like the issue for the Netgear WNDA3100v2 had been solved. So I picked up that
one. 
I came back and proceeded to install ndiswrapper and the driver. At the begining, I had not realised
you could not have both cards activated. Then I switch off the internal card. But I still cannot connect
to the network. I tried a couple of other drivers to no avail. I probably missed a step somewhere and
further trials probably messed up the install. 
Here is what I can see currently:
```

Presario-C700-Notebook-PC:~$ ndiswrapper -l
bcmn43xx64 : driver installed
    device (0846:9011) present

```
```

Presario-C700-Notebook-PC:~$ iwconfig
wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"virginmedia6249288"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 04:A1:51:2D:3C:C8   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```
```

Presario-C700-Notebook-PC:~$ dmesg | grep ndis
[   18.100337] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   18.101805] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   19.586069] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   19.848960] usbcore: registered new interface driver ndiswrapper
[  707.848750] ndiswrapper: device wlan1 removed
[  710.122205] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded

```
Well that almost the status, as I have to switch back to wlan0 -- the internal wifi card -- to be 
able to send this post. 
It looks to me as everything is fine but if I turn wlan0 off and wlan1 up, trying to connect to the wifi
router does not succeed. 

Attached is the output of the wireless-info script as suggested by Varun. 

Any help would be appreciated. 

Best

Trad

---

### Post by chili555 on 2014-09-02
> I realise I cannot connect to most hot spots through the internal card. You are using the wrong driver. Please get a temporary ethernet connection and do:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet and that horrible NetGear and let me hear your report.

---

### Post by Trad_dog on 2014-09-02
Hey Chili555, 

glad to read you. 

So, the situation has worsened slightly. I just noticed that my wired interface did not work anymore.
Besides even before the 
sudo apt-get purge bcmwl-kernel-source

the internal wireless connection did not come back. So no more connection on the laptop. 
I have run out of voddoo tricks (switching the wireless button on/off, rebooting, ifconfig up/down). 
I could not execute your second instruction clearly. 
Can I burn a CD with the linux-firmware-nonfree to be able to reconnect the wireless ?

Best,

---

### Post by chili555 on 2014-09-02
Please load the driver:```
sudo modprobe 8139too
```Does the ethernet come to life?```
ifconfig
```Any clues in the log?```
dmesg | grep -e 8139 -e eth0
```

---

### Post by Trad_dog on 2014-09-03
Hi Chili555, sorry time difference: my eyes were closing 10mn before your message reached me. 

In the brisk morning, I try the new instructions. I cannot copy and paste the results. 
But essentially, dmesg shows that eth0 is down first and then up, then down:
[300] 8139too .... eth0: link up, 100Mbps, full duplex
[603] 8139too .... eth0: link down
 ifconfig states that UP BROADCAST is running on eth0. RX packets: 127 no error. TX packets 16, no error. 
However pinging anything gives: Network unreachable.

---

### Post by varunendra on 2014-09-03
Just filling in while dr. chili is away, for one thing - to help installing the linux-firmware-nonfree package for the internal wifi card

Please follow this post to install it offline : [http://ubuntuforums.org/showpost.php?p=13062169](http://ubuntuforums.org/showpost.php?p=13062169)

Reboot, and see if at least the internal wireless starts working. Although I wonder if the presence of ndiswrapper could cause a conflict with helping drivers, but let's first see a wireless_script report after doing above.

For Ethernet, please separately (in the same post) post the outputs of -
```
sudo lshw -C network
sudo ethtool eth0
```

---

### Post by Trad_dog on 2014-09-03
Hi Varun, 

Thanks for stepping in. Appreciate the support. 

The linux-firmware-nonfree package did the trick. The internal wifi card is now working and I am 
actually writing directly from the laptop. Thanks. 

I attach the additional info. 

Again thanks to the community.

Trad

---

### Post by Trad_dog on 2014-09-03
sorry the wireless-info without a date is the previous one and was not supposed to be attached. 

best

---

### Post by chili555 on 2014-09-03
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

### Post by Trad_dog on 2014-09-03
Hi Chili555, 

A good day to you. 

Thanks for the help. The laptop is undoubtedly back to its previous state. You seem to be confident that the new driver should improve 
the connection in most hot-spots, which I shall duly test it. Hopefully this is the case and I won't need the Netgear
USB dongle. I'll report and close the thread accordingly. 
As an extra, I was wondering if you had any view on the eth0 not working by any chance, although if we have improved 
the Wifi, it will be sufficient.

---

### Post by chili555 on 2014-09-03
> As an extra, I was wondering if you had any view on the eth0 not working by any chance, although if we have improved the Wifi, it will be sufficient.I suggest you start a new thread and I'll be happy to help. Be sure to include:```
lspci -nn | grep 0200
dmesg | grep -e eth0 -e 8139
```We'll probably need more diagnostics depending what these tell us. Be certain to run these tests with the ethernet hooked to a known working cable and the router.

---

### Post by Trad_dog on 2014-09-04
Hi Chili555,

I shall follow your suggestion. 

Thanks

---

### Post by Trad_dog on 2014-09-04
Hi Chili555. Varun,

I confirm that the laptop is now connecting to the hotspot it was stubbornly refusing to connect 
so far. 

Many thanks for your continuous support. 

Best

Trad

---

