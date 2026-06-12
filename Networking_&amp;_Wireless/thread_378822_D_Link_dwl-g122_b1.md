---
title: "D Link dwl-g122 b1"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by dcj65 on 2007-03-07
I have been trying to get a Dlink dwl-g122 to work for some time now,I have tried to follow other posts to no avail. When I do iwconfig this is what I get:

rausb0    RT2500USB WLAN  ESSID:""  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-120 dBm  Noise level:-208 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 I should also state that I do have an old linksys pci  card working, but the range is not good and it is awful slow. So I can see my router through the linksys card fine. I have also changed the settings through iwconig and they do not save. Here is my blacklist from when I tried to get a netgear usb wireless working (which I was unable to)

blacklist i2c_i801

rmmod bcm43xx
rmmod ndiswrapper
cd to /lib/modules/kernel[6.10]/kernel/drivers/net/wireless
mv acx /root/
depmod -a
cd ~/desktop
dpkg -i ndiswrapper-utils_1.8-0ubuntu2_1386.deb
cd ~/desktop/xp
ndiswrapper -i1.8-0ubuntu2.inf
modprobe ndiswrapper
ndiswrapper -m
blacklist bcm43xx
#wg111v2 conflicting drivers
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b

Any thoughts ?

---

### Post by Floppyjoe on 2007-03-07
What is the output of:
```
ndiswrapper -l
```
It looks like from your previous post you were trying to install the ndiswrapper file using ndiswrapper. I am trying hard not to laugh :biggrin: 
Maybe I'm just not understanding what I'm reading.
If you have an Invalid driver listed you will need to delete it with:
```
sudo ndiswrapper -e drivername
```
Then locate the driver files for your network device and put the .inf and .sys and possibly .bin file in the same directory. Then cd to that directory and run the:
```
sudo ndiswrapper -i drivername.inf
```
again.

Hope this helps.

---

