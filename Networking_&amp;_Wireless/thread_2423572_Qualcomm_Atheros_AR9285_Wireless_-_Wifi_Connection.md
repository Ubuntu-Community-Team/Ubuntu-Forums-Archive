---
title: "Qualcomm Atheros AR9285 Wireless - Wifi Connection stopped working"
date: 2019-07-25
forum: Networking &amp; Wireless
---

### Post by rawjeev on 2019-07-25
Hi,):P

Wifi connection stopped working on my laptop. The applet shows that Wifi is disabled and does not detect any Wifi connections even when I enable it.
Followed instructions on "Before Posting" thread and ran the Pastebin script. The machine has **Qualcomm Atheros AR9285 Wireless Network Adapter** 

This is the pastebin URL after running the script

[http://paste.ubuntu.com/p/rNvcmYFm79/](http://paste.ubuntu.com/p/rNvcmYFm79/)

Please help with this.

Thank You.

---

### Post by jeremy31 on 2019-07-25
Enable the wifi and run ```
./wireless-info
```
Post new URL for results

And what model is this?

---

### Post by rawjeev on 2019-08-03
The computer is a Lenovo Ideapad Z560
And the url for the results of wireless-info

[http://paste.ubuntu.com/p/tHdH5CG7Jm/](http://paste.ubuntu.com/p/tHdH5CG7Jm/)

Thank you.

---

### Post by chili555 on 2019-08-03
Please try:```
sudo modprobe -r ideapad_laptop
sudo rfkill unblock all
```Does your wireless spring to life? If so, let's blacklist the module permanently:```
sudo -i
echo "blacklist ideapad_laptop"  >>  /etc/modprobe.d/blacklist.conf
exit
```

---

### Post by jeremy31 on 2019-08-03
Are there any switches on the front/left/right sides of the keyboard that may enable/disable wifi?  This model appears to be old enough that it should not be affected by the ideapad_laptop module especially if it did work before in ubuntu

---

### Post by rawjeev on 2019-08-11
Thank You Very Much. Very thoughtful of you and stupid of me :razz:.
I finally figured that it was that tiny, invisible switch, that must have been turned off while handling.

---

