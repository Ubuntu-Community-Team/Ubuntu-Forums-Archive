---
title: "Problem connecting to wifi with ubuntu 16.04 on lenovo Yoga laptop"
date: 2016-06-01
forum: Networking &amp; Wireless
---

### Post by ashwin7 on 2016-06-01
I just switched to ubuntu 16.04 from windows 10. I cannot connect to wifi. I am new to the ubuntu. Please help in this matter.

Processor: Intel® Core™ i3-4030U CPU @ 1.90GHz × 4
Memory: 3873 MB
Ubuntu 16.04 LTS, 64bit

```

lspci ------

01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter

lsusb ----

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 048d:8350 Integrated Technology Express, Inc. 
Bus 002 Device 005: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 04f2:b40f Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 04f3:0303 Elan Microelectronics Corp. 
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig -----

wlp1s0    IEEE 802.11bgn  ESSID:"Windows Phone4230"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: BC:C6:DB:92:55:04   
          Bit Rate=7.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-23 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:131   Missed beacon:0


lo        no wireless extensions.

rfkill -----

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no








```

---

### Post by chili555 on 2016-06-01
> wlp1s0    IEEE 802.11bgn  ESSID:"[COLOR="#FF0000"]Windows Phone4230[/COLOR]"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: [COLOR="#FF0000"]BC:C6:DB:92:55:04  [/COLOR] 
          Bit Rate=7.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-23 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:131   Missed beacon:0It looks as if you are connected right now. Please tell us more about, "... cannot connect to wifi."

---

### Post by ashwin7 on 2016-06-01
The thing is I can connect to my mobile device(using internet sharing feature on Mobile) but when I try connecting to university wifi network it repeatedly gives the window stating authentication required(user id and password), but it never gets connected to wifi. I tried various solution from ubuntuforums but still not getting connected wifi. I have come across one of the post facing the same problem and it stated as:

[http://ubuntuforums.org/showthread.php?t=2326224&p=13496747#post13496747](http://ubuntuforums.org/showthread.php?t=2326224&p=13496747#post13496747)

[COLOR=#333333][FONT=monospace]A number of other Ubuntu users and myself have encountered difficulty when upgrading to Ubuntu 16.04 LTS due to our WiFi chipset not being supported. When I inquired about it on the Ubuntu Forums, I was informed that this chipset was last known to work on Ubuntu 14.04.3, and no longer in Ubuntu 14.04.4.


Is this true. should I switch to older version of ubuntu as it seems there will be no fix for this bug.
My first ubuntu experience is kind of frustrating.... [/FONT][/COLOR]:confused:

---

### Post by chili555 on 2016-06-01
> Is this true.Absolutely not. Obviously, if you can connect at all, in this case to your phone as a hotspot, there is support for the device. 

The default driver has trouble selecting the antenna wire in use. Here is some information about that: [http://ubuntuforums.org/showthread.php?t=2304607&highlight=rtl8723be](http://ubuntuforums.org/showthread.php?t=2304607&highlight=rtl8723be) Especially see post #17. Also check here: [http://askubuntu.com/questions/778589/realtek-wifi-driver-problem-rtl8723be-weak-signal/779604#779604](http://askubuntu.com/questions/778589/realtek-wifi-driver-problem-rtl8723be-weak-signal/779604#779604)

Before we try to fix what may not be broken, I'd love to see this as you are trying to connect at the university:```
sudo iwlist scan
```If we see signal strength that is very low; 25/70 or so, we'll install the newest updated driver that allows antenna selection.> My first ubuntu experience is kind of frustrating..I know it is; if we can just clear this one hurdle, I am confident you'll have clear sailing.

---

### Post by ashwin7 on 2016-06-02
Hey I followed the post (link) given by you and it worked. Thanks for guidance.

---

