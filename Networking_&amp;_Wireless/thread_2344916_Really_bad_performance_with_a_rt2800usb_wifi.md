---
title: "Really bad performance with a rt2800usb wifi"
date: 2016-11-29
forum: Networking &amp; Wireless
---

### Post by kingpenguin on 2016-11-29
I have a wireless N wifi dongle that uses the rt2800usb module to my knowledge. If I plug this dongle into other computers i get great speeds and signal. This machine that I am using this for is a permanent kodi box and nas. My problem is that this machine has no way of hardwiring in to the ethernet and the wifi signal/speed is really slow and keeps disconnecting every few seconds. I have no objections to trying anything. I have updated the machine and made sure that all firmware for ralink is fully up to date.

---

### Post by kingpenguin on 2016-11-29
Bump

---

### Post by wildmanne39 on 2016-11-29
*Thread moved to **Networking & Wireless**.*

Please do:
```
echo "options rt2800usb nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800usb.conf 
sudo modprobe -rfv rt2800usb 
sudo modprobe -v rt2800usb
```
That will probably help.

---

### Post by kingpenguin on 2016-11-29
I'm not getting the horrible disconnects any more :D But i am still not getting great speed all the time. Don't get me wrong at least now i sometimes get full speed but it just doesn't seem steady. its list when im downing im getting almost 1Mbp per sec which is decent for the server i am getting from but then i drop to 122Kbps or less for long periods of time. Same happens when i am trying to download from the Ubuntu software center as well. I almost forgot to mention that when i do a iwconfig i get tx excessive retries = 182 and invalid misc = 765. I have only had this connected to the internet for less than 2 mins so far

---

### Post by wildmanne39 on 2016-11-29
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by kingpenguin on 2016-11-30
Ok i have ran the script but it wont let me paste here in the quick reply. It says something about you have 9 images in your messages. They can be code [img] or html <img>. I put it in a text editor and ctl+f and typed img but found nothing so i pasted in pastebin here [http://pastebin.com/PWyKweAV](http://pastebin.com/PWyKweAV)

---

### Post by wildmanne39 on 2016-11-30
Since you are not using ubuntu the script gave me only a small amount of the information it should have but it will help some.

Check the settings in the router. WPA2-AES is what you want to set it too; not WPA and WPA2 mixed mode and not TKIP. Set your router to a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After make the changes, reboot the router.

In network manager change your settings to match the screenshots.

Then reboot computer.
[ATTACH=CONFIG]272460[/ATTACH][ATTACH=CONFIG]272461[/ATTACH]

---

### Post by kingpenguin on 2016-11-30
Ok that seemed to really fix it. I went from almost 1Mbps to around 20Mbps on almost everything. You are really awesome ty so much. I'm got to continue testing but for now i'll mark as solved.

---

### Post by wildmanne39 on 2016-11-30
Glad it worked!
Enjoy!

---

