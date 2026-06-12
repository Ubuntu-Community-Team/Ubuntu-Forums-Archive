---
title: "3G wifi inconsistent, drops out."
date: 2016-09-14
forum: Networking &amp; Wireless
---

### Post by bluepicaso2 on 2016-09-14
Same problem since few days,
I have Lenovo Ideapad 300 too and using ubuntu 16.04, as installed 3 months ago on my laptop.
attached is my wireless info file.
The problem is, i have 3G wifi, that works perfect on another laptop (dell), but on mine, downloads are incomplete, and speed goes to 0 kbps.
even system upgrades keep waiting for reconnect and fails. Same for some websites, they just dont open in first go, i have to refresh thrice.

When i first installed 16.04 on my new laptop i then discovered that i had to follow
[http://askubuntu.com/a/708103](http://askubuntu.com/a/708103)
that worked everytime on new kernel, let me know if I should follow it again.

thank you

---

### Post by Bucky Ball on 2016-09-14
Try this. Open a terminal and try these three commands:

```
sudo iwconfig wlp2s0 power off
sudo service network-manager restart
iwconfig
```

Does 'power management' equal 'off' in the output from the last command? How's the wifi?

Not sure what you mean by 'a 3G wifi'. You mean wireless modem and that's what you're connecting to? Has the wireless been this bad the full three months you've had 16.04 or did an update do this, or something else, installing a program, adding another device? Bluetooth device?

---

### Post by bluepicaso2 on 2016-09-14
> **Bucky Ball said:**
> Try this. Open a terminal and try these three commands:

```
sudo iwconfig wlp2s0 power off
sudo service network-manager restart
iwconfig
```

Does 'power management' equal 'off' in the output from the last command? How's the wifi?

Not sure what you mean by 'a 3G wifi'. You mean wireless modem and that's what you're connecting to? Has the wireless been this bad the full three months you've had 16.04 or did an update do this, or something else, installing a program, adding another device? Bluetooth device?

Haven't tried the commands yet, but let me respond to your questions.
Yes its a wireless dongle, connect to a power socket and you have a Wifi. 
No its just became bad since past one week. Signal strength is good too.
I am not sure about the update, I am only one connected to the device via laptop, for phone i have another WIFI for all members at home.
could it be similar wifi channel?

---

### Post by bluepicaso2 on 2016-09-14
command output
```

someone@laptop:~$ sudo service network-manager restart 
[sudo] password for ****: 
someone@laptop :~$ sudo iwconfig wlp2s0 power off
[sudo] password for ****: 
someone@laptop :~$ sudo service network-manager restart
someone@laptop :~$ iwconfig
wlp2s0    IEEE 802.11abgn  ESSID:"MBLAZE-DF800i-12A0"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: FC:DD:55:08:12:A0   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:38   Missed beacon:0

lo        no wireless extensions.

enp1s0    no wireless extensions.



```

---

### Post by bluepicaso2 on 2016-09-14
Internet beahves same. I can confirm that there is something wrong with laptop or OS.
There is a phpmyadmin link our project that use to open just fine on this laptop.
I just connected my wifi to the phone and same web link opens fine.
I tried all browsers 
example this link, does not load completely,
[http://www.quikr.com/cars-bikes/pitstop/2016/06/20/quikr-scanner-a-smarter-way-to-drive/](http://www.quikr.com/cars-bikes/pitstop/2016/06/20/quikr-scanner-a-smarter-way-to-drive/)
I though it was some addon, by i have chrome with no such addons, same result

---

