---
title: "WPA2-PSK problem"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by newnet on 2007-12-06
Okay, the connection was fine before.  But now there is WPA2-PSK involved.  I tried to follow these how-tos: 

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=21546&sid=c5e02ed97dde07681fb564639e9f50c5](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?p=21546&sid=c5e02ed97dde07681fb564639e9f50c5)

I have been trying different how-tos  here and there.  I have the correct driver (rt2500).  I doubled-checked all the steps.  Made sure I typed in the passphrase correctly.  But in the end, I would not even get a ping.

Please help me!!!

---

### Post by kevdog on 2007-12-06
Try this in your /etc/network/interfaces file

auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
    pre-up iwpriv wlan0 set SSID="YOUR_SSID"
    pre-up iwpriv wlan0 set NetworkType=Infra

I got this from [http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

---

### Post by newnet on 2007-12-06
Still not working.

No matter what configuration I use, one of the lines it prompts is:
```
Interface doesn't accept private ioctl...
```
Does that mean anything?

---

### Post by kevdog on 2007-12-06
OK try this:

auto wlan0
iface wlan0 inet dhcp
wireless-essid "ESSID in QUOTES"
pre-up ifconfig wlan0 up
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
pre-up iwpriv wlan0 set NetworkType=Infra

Have you tried connecting from the command line (link in my post)?

---

### Post by newnet on 2007-12-06
Still does not work.

Your how-to does not support WPA2 for the Ralink chipset.

---

### Post by kevdog on 2007-12-06
I know, however TKIP is for WPA1.  I dont know is serial monkey does wpa2. Im looking for some confirmation.

If it does work I think it would need to be the following:

pre-up iwpriv wlan0 set EncrypType=CCMP

pre-up iwpriv wlan0 set NetworkType=Infra  <-- Not sure if this line is needed

---

