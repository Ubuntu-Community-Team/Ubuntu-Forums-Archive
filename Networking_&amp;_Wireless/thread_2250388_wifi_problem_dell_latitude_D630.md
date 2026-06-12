---
title: "wifi problem dell latitude D630"
date: 2014-10-28
forum: Networking &amp; Wireless
---

### Post by carval444 on 2014-10-28
Hello,

I am a new linux(ubuntu) user and I have some trouble with the wifi drivers(ubuntu).
Before I tried ubuntu I installed windows 7, but there was also no drivers for the wifi card. It said it was unsupported.
A friend of mine had problems with diffrent hardware but he said that i need to try linux because linux supports almost any driver(or something like that)
Only with Ethernet I can go online.

my specs:
dell latitude D630
intel core 2 duo cpu T7500 @ 2.2GHz
1.5Gb ram
NVIDIA Quadro NVS 135M
(and I think)Intel 3945 802.11g Wireless

(my other d630 with intel graphic have a dell wireless 1390 WLAN Mini-Card so it's possible that the cards are the same)

I have also problems with my grapics card(nvidia)
when I click on ubuntu logo, my pc is freaking out like a test screen on tv but then moving

I hope you can help me?
Greets carval444
sorrry for bad english

---

### Post by wildmanne39 on 2014-10-28
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz)depending on the size of the file and it will be placed in your home folder. The wireless information will help to diagnose your wireless issue, the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the (wireless-info.txt, or wireless-info.txt.tar.gz) file as a zip file. 

If you do not have ethernet connection then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385).
Thanks

---

### Post by carval444 on 2014-10-28
[ATTACH]257560[/ATTACH]

hi, thanks for the help. i have uploaded the file.

greets carval444

---

### Post by wildmanne39 on 2014-10-28
The issue is that your wireless card is not showing up at all. You can check in the bios and see if it is turned off, you can reset the bios, you can check if the card is seated good if possible. It is also possible that the card has went bad.

---

### Post by QIII on 2014-10-28
Also check for a hardware switch, which is probably on the left side of the machine.

---

### Post by wildmanne39 on 2014-10-28
Even if the switch is turned off the card would show up in the output of the file, but it was a good thought.

---

### Post by carval444 on 2014-10-28
thanks everyone. -_- The option in the bios was turnd off. I should saw that... 
But now i have the problem that the wifi led is blinking. any solution?

greets carval444

---

### Post by wildmanne39 on 2014-10-28
Run the script again and post a new file.
Thanks

---

### Post by carval444 on 2014-10-28
Here it is:[ATTACH]257562[/ATTACH]

greets carval444

---

### Post by wildmanne39 on 2014-10-28
You can connect to the internet correct? The light flashing just means it is working, the setting might can be changed but I don't  see the point it does not effect connection at all. There is a driver parameter that might can be set to make it solid but it does not always work. That driver is very old and someimes needs a parameter to be able to connect good, let us know if you are having connection issues.

---

### Post by carval444 on 2014-10-28
At this moment i don't have issues. But I have Problems with the graphics card. But I wil post that in another thread.
Thanks for all the help everybody

---

### Post by wildmanne39 on 2014-10-28
Glad it is working! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

