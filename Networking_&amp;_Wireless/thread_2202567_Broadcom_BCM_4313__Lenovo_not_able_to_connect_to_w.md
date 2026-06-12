---
title: "Broadcom BCM 4313 / Lenovo not able to connect to wifi after installing ubuntu 12.04"
date: 2014-01-29
forum: Networking &amp; Wireless
---

### Post by roshan5 on 2014-01-29
Hi,

I installed ubuntu 12.04 and I am not able to connect wifi. I dont have any other way of connecting to internet from ubuntu. Wifi works fine from Windows which is my dual OS
I checked other threads and tried, but couldn't get it working. Below are some outputs which might help:

rosh@rosh-ub:~$ dmesg | grep iwl
rosh@rosh-ub:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2014-01-29
Please add this output:```
lspci -nn | grep 0280
```

---

### Post by roshan5 on 2014-01-29
here is the output:

[http://www.picpaste.com/IMG_20140129_221426_1_-Ofxyvy2p.jpg](http://www.picpaste.com/IMG_20140129_221426_1_-Ofxyvy2p.jpg)

---

### Post by chili555 on 2014-01-29
For reference, you have a Broadcom 14e4:4727. Please open a terminal and do:```
sudo modprobe brcmsmac
```See if the wireless comes to life:```
iwconfig
```Is the hardware switch on or off?```
rfkill list all
```Are there any errors in the log?```
dmesg | grep brcm
```Off for the evening; I'll check in tomorrow.

---

### Post by roshan5 on 2014-01-30
Yes not my wifi is working...thanks a lot!!!!


rosh@rosh-ub:~$ sudo modprobe brcmsmac
[sudo] password for rosh: 
rosh@rosh-ub:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Rogers48432"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 38:60:77:74:DD:AA   
          Bit Rate=65 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36   Missed beacon:0



rosh@rosh-ub:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
rosh@rosh-ub:~$ dmesg | grep brcm
[  201.790316] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[  201.916834] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  201.916848] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[  204.534108] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  204.534115] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  204.534119] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  208.526597] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
rosh@rosh-ub:~$

---

### Post by roshan5 on 2014-01-30
but when i restart...it doesn't work and I have to run the command again....any idea??

---

### Post by roshan5 on 2014-01-30
it doesn't connect now...it keeps asking me for password....after i  enter the password and click connect...it attempts to connect and keeps  asking me for password...

---

### Post by chili555 on 2014-01-30
Let's try something different now:```
sudo modprobe bcma
```Also show me:```
lsmod
```Does simply loading *bcma* result in a proper connection?

---

### Post by roshan5 on 2014-01-30
No it doesn't

---

### Post by chili555 on 2014-01-30
What does the log say is happening?```
cat /var/log/syslog | grep -e bcma -e etwork | tail -n20
```

---

### Post by roshan5 on 2014-01-30
i have uploaded it here:

[http://www.picpaste.com/IMG_20140130_120420_1_-EU10Ycq5.jpg](http://www.picpaste.com/IMG_20140130_120420_1_-EU10Ycq5.jpg)

---

### Post by chili555 on 2014-01-30
It may be quite a bit easier to post your findings by transferring the result to a text file:```
terminal_command > wifi.txt
```And then find the file wifi.txt in your user directory and transfer it on a USB stick to another computer so you can post it here. In that vein, let's see:```
iwconfig > wifi.txt
dmesg | grep -e wlan -e bcma >> wifi.txt
sudo iwlist wlan0 scan >> wifi.txt
```Find wifi.txt and post it here.

The results you posted just above are puzzling, we see no meaningful wireless data at all.

---

### Post by roshan5 on 2014-01-30
I am sorry...I tried that way too...but unfortunately the file i created and I copied to usb stick is not visible when I check in windows system....It sounds creepy though....don't why..

anyways I have uploaded the picture again:

[http://www.picpaste.com/IMG_20140130_175350_1_-FQnxFGtk.jpg](http://www.picpaste.com/IMG_20140130_175350_1_-FQnxFGtk.jpg)

Please excuse for the inconvenience

---

### Post by chili555 on 2014-01-30
Please try again. Most of what we need to see is missing. Please do this first:```
sudo modprobe bcma
sudo modprobe brcmsmac

```

---

### Post by roshan5 on 2014-01-30
i tried the commands...and its connecting now...infact I just repied from ubuntu

---

### Post by chili555 on 2014-01-30
Awesome! Let's get the modules to load on boot:```
sudo -i
echo bcma  >>  /etc/modules
echo brcmsmac  >>  /etc/modules
exit
```

---

### Post by roshan5 on 2014-01-30
awesome I did as you said....restarted...and its working!!!!

dont know how you figured it out!!!!

---

### Post by roshan5 on 2014-01-30
I hope it doesn't give me any more problems...

---

