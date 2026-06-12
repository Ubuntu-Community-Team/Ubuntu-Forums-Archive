---
title: "D-link dwa 140 on 17.04"
date: 2017-04-25
forum: Networking &amp; Wireless
---

### Post by supahstar42 on 2017-04-25
So I've seen many posts about this but from years ago. I am trying to use a d-link usb wifi adapter but when trying to connect to wifi, it hangs in the "connecting" stage then immediately disconnects.

Has anyone found a solution or have solved this on their own?

---

### Post by wildmanne39 on 2017-04-25
Click on the wireless script in my signature and follow the directions for running it and posting the link created to pastebin here.

---

### Post by supahstar42 on 2017-04-26
Sorry it took me so long got busy. Here's the link [https://pastebin.com/beBdU3EH](https://pastebin.com/beBdU3EH)

---

### Post by wildmanne39 on 2017-04-26
Please do:
```
echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb 
sudo modprobe -v rt2800usb

```
Then:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Then open the file with your text editor, if you need more directions just ask:
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0

```
Save and close file then reboot.

Unplug your wired connection.

---

### Post by supahstar42 on 2017-04-26
Worked flawlessly. Thank you so much, I'm trying to save an old custom PC and there is no wifi card. ](*,)

---

### Post by wildmanne39 on 2017-04-26
Another computer?

---

### Post by wildmanne39 on 2017-04-27
Your welcome! please go to the top of the page and use thread tools to mark this thread solved.
Enjoy!:)

---

