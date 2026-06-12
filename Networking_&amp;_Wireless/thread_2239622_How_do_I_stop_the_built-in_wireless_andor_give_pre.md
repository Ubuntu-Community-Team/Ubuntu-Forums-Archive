---
title: "How do I stop the built-in wireless and/or give preference to a USB wifi adapter???"
date: 2014-08-14
forum: Networking &amp; Wireless
---

### Post by xmbwd on 2014-08-14
I am on 14.04 on a laptop that has the Intel Corporation Wireless 7260 (rev 6b) card.  Because the signal consistently dropped in and out like a yo-yo, and did not have very good distance to boot, I purchased a $9 USB wifi card: the Edimax [FONT=Calibri][SIZE=3][COLOR=black]EW-7811Un[/COLOR][/SIZE][/FONT] (as an aside, this did not plug and play, I had to follow the instructions [here]("https://github.com/pvaret/rtl8192cu-fixes")). 

Now my System Settings>Network shows two wireless cards: 

[IMG]https://dl.dropboxusercontent.com/u/13392425/wifi.png[/IMG]

Unfortunately, Ubuntu is trying to use ***both of them simultaneously***.   And sometimes, the two cards pick **two different** APs in my house:
```
wlan1     IEEE 802.11bgn  ESSID:"dd_wrt"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.457 GHz  **Access Point: bb:bb:bb:bb:bb:AC**   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=76/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"dd_wrt"  
          Mode:Managed  Frequency:2.412 GHz  **Access Point: xx:xx:xx:xx:xx:AB **  
          Bit Rate=13 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:48   Missed beacon:0


```

**[COLOR=#b22222]Is there any way I can just tell my internal card to either (a) turn off or (b) give preference to the adapter???  [/COLOR]**

I have tried this ```
sudo ip link set wlan0 down
``` and this ```
ifconfig wlan
``` to turn the internal card (wlan0) off, but for some reason it kills the entire network connection.  

Any ideas much appreciated!

---

### Post by TheFu on 2014-08-14
rfkill?


chili555's response below is much better.

---

### Post by chili555 on 2014-08-14
You can blacklist the driver for the internal:```
sudo -i
echo "blacklist iwlwifi"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r iwlwifi
exit
```You should be all set.

---

### Post by xmbwd on 2014-08-14
That looks like a win!!  Thanks!

Chili555:  if I wanted to, how could I reinstate the built-in wireless?  I get that I'd remove it from the blacklist.conf.  But I'm not sure what the converse of ```
modprobe -r iwlwifi 
``` is.  That removes the module.  How do I get it back?

---

### Post by chili555 on 2014-08-14
> But I'm not sure what the converse of
Code:
modprobe -r iwlwifiThe converse is:```
sudo modprobe iwlwifi
```To revert to the internal permanently, edit the blacklist file to remove the line we just added.```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Remove the iwlwifi line, save and close.

Please use thread tools at the top to mark Solved.

---

