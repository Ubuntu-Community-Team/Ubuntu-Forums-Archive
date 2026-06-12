---
title: "Ubuntu Trusty Tahr - Wifi not working"
date: 2015-08-17
forum: Networking &amp; Wireless
---

### Post by mster on 2015-08-17
Hello all
I hope you can help us!

My husband has a desktop computer (It's a Dell Vostro 400) with Trusty Tahr installed on it.
It was running fine until this afternoon when the wifi just stopped working. He uses a usb wifi stick (TP-Link 150Mbps) to connect to our wifi.

We have two sticks and have tried both.

But now when he plugs in the wifi stick it says that there are networks available but does now show or connect to any of them.
No settings have been changed. It's like the router is just ignoring him!

I can connect to the wifi fine with my netbook. Nothing has changed for me.

We have a cable that he can connect with, but it's pretty short and terribly inconvenient to have it inserted.

I hope that someone can help!

Thanks

Marianne

---

### Post by chili555 on 2015-08-17
Please plug in the USB wireless, open a terminal Ctrl+Alt+t and run and post the result of these two commands:```
lsusb
rfkill list all
```Thanks.

---

### Post by mster on 2015-08-17
Hello, thanks for responding.
lsusb gave this:

[IMG]http://i.imgur.com/HH9yOvM.jpg[/IMG]

and the other command gave no output

---

### Post by chili555 on 2015-08-17
I see no usb wifi stick (TP-Link 150Mbps) there. Are you certain it was plugged in when you ran the command?

---

### Post by mster on 2015-08-17
You're correct, the stick did not come up in the text output.

But yes, it was plugged in.

---

### Post by chili555 on 2015-08-17
Does the other stick show up when inserted and then running:```
lsusb
```We may have a bigger problem than networking.

---

### Post by mster on 2015-08-18
Hi chili555

I tried a different wifi stick and got this:

[IMG]http://i.imgur.com/nVLKL0n.png[/IMG]

---

### Post by mster on 2015-08-18
Thank you so much for helping me by the way, I really appreciate it.

---

### Post by praseodym on 2015-08-18
For THIS stick change the driver via LAN:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot. Checked another USB slot for the first one?

```
lsusb

```
'ing again with that?!

---

### Post by mster on 2015-08-21
Hi there, I typed all of the above into the terminal and rebooted. This is what lsusb now brings:

[img]http://i.imgur.com/Avikyjt.png[/img]

---

### Post by mster on 2015-08-21
When I insert the stick, I get the message (same as before) that wifi is available but when I scan with WCID nothing is found.

---

### Post by mster on 2015-08-24
Does anyone have an idea what I can try next?

Pretty please?

---

### Post by praseodym on 2015-08-24
Obviously, it is not recognised, only the other one. Broken?

---

### Post by mster on 2015-08-24
the computer recognises it. yes. but not the other one.

---

