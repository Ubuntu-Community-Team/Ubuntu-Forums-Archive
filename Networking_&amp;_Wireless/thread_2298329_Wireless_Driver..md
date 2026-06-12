---
title: "Wireless Driver."
date: 2015-10-10
forum: Networking &amp; Wireless
---

### Post by Samir_Ahuja on 2015-10-10
Hey all. I have a Dell inspiron 1720 with a Dell 1395 Wireless card. I read it has some driver problem in ubuntu which is fixed by going to additional drivers and enabling the propriety driver. So with UTMOST CARE I tried this out in Ubuntu live session. It worked like a charm so I installed Ubuntu dual boot with my windows 7. But now after installing still this card is not detected. I went back to the Additional Drivers window and tried to enable the propriety driver but IT IS NOT WORKING! If I click apply changes, it asks me my password. I entered it. Now it gets greyed out nothing happens. I can't access the internet! Please help me!

---

### Post by howefield on 2015-10-10
Hello Samir_Ahuja, I have moved your post to the "*Networking & Wireless*" forum where the gurus may be better able to help. In the meantime have a read at this [sticky]("http://ubuntuforums.org/showthread.php?t=370108").

---

### Post by Samir_Ahuja on 2015-10-10
thanks admin

---

### Post by Samir_Ahuja on 2015-10-10
UPDATE
After rebooting I tried the method again. This time the orange progress bar appeared at 1/8th progress and is not moving at all. But when I had done the same in Live session my wireless was running in 5 seconds. Please help ASAP.

---

### Post by Hadaka on 2015-10-10
Hi please go here -> [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

read carefully and then post the **wireless-info.text** file.

thanks.

---

### Post by Samir_Ahuja on 2015-10-10
Trying to attach but I am getting an error like this:
[ATTACH=CONFIG]264890[/ATTACH]

---

### Post by jeremy31 on 2015-10-10
You should be able to attach the wireless-info.tar.gz file

---

### Post by Samir_Ahuja on 2015-10-10
Jeremy, I only have the txt file. Can someone please give me the step by step instructions to get the tar file? 
Thanks.

---

### Post by jeremy31 on 2015-10-10
If you only have text file, copy the contents and paste into a post using [ code] before the paste and [ /code] after, remove the extra space in the tags so the formatting of the file is preserved, see [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168) to read about code tags

You could also paste the contents at paste.ubuntu.com and post the URL

---

### Post by Samir_Ahuja on 2015-10-10
jeremy,
[http://paste.ubuntu.com/12733961/](http://paste.ubuntu.com/12733961/)
Thanks.!

---

### Post by jeremy31 on 2015-10-10
That is the wireless-info file not the wireless-info.**txt**
Perhaps it did not run
```
chmod +x wireless-info && ./wireless-info
```

Then see if you have the wireless-info.txt or the tar.gz file

---

### Post by Hadaka on 2015-10-10
Hi,let's try this...open a terminal ctrl/alt/t then COPY and paste these
commands one at a time..
```
lspci -n | awk '/0280/ {print$3}'
lsmod | awk '/b43|wl/ {print}'
rfkill list all
```
post the output 
thanks

---

### Post by Samir_Ahuja on 2015-10-10
jeremy,
It is attached.
Thanks.[ATTACH]264892[/ATTACH]

---

### Post by Samir_Ahuja on 2015-10-10
Hadaka,
first command output:
14e4:4315

second output:
b43                   421888  0 
bcma                   57344  1 b43
mac80211              720896  1 b43
cfg80211              540672  2 b43,mac80211
ssb                    65536  2 b43,b44
third command has no output.(Nothing happens it just goes to the next line ready to take another command)
Thanks.[ATTACH=CONFIG]264893[/ATTACH]

---

### Post by Hadaka on 2015-10-11
Hi, from a working wired connection,
open a terminal and do..
```
sudo apt-get update
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
then do...
dont worry if the commands have errors...do them anyway
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
remove the ethernet cable....reboot and test wireless
thanks

---

### Post by Samir_Ahuja on 2015-10-11
Hadaka, I LOVE YOU!!!!
It worked!! (Thank you so much)whole powered 1billion times. 
Thanks everyone for helping. This is the best thing about ubuntu isn't it? Help is always given to those who seek it.;)
Thanks again!!!

---

### Post by Hadaka on 2015-10-11
Glad that worked for you !!
Please mark this thread SOLVED
thanks.

---

### Post by Samir_Ahuja on 2015-10-12
Done. Thanks again!

---

