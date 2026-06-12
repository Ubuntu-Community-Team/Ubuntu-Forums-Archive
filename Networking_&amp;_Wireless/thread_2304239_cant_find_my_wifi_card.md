---
title: "cant find my wifi card :/"
date: 2015-11-25
forum: Networking &amp; Wireless
---

### Post by haxerius on 2015-11-25
Hi i have my cable connected right now to get internet but i thought i would use my wifi but cant seem to find my card what to do? 

did ifconfig got my local and eth0 but nothing else using broadcom btw

---

### Post by slickymaster on 2015-11-25
*Moved to the ***Networking & Wireless*** sub-forum*

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by haxerius on 2015-11-25
How do i run the script? 

I did the ifconfig wlan0 up
error while getting interface flags "unit cant be found" "translation from my language"

---

### Post by slickymaster on 2015-11-25
Open a terminal window and run the following command```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
chmod +x wireless-info
./wireless-info
```

---

### Post by haxerius on 2015-11-25
My bad

---

### Post by slickymaster on 2015-11-25
Click the paperclip icon in the top of the **Reply to Thread**. It will take you directly to the Manage Attachments dialog. In the Manage Attachments dialog box, you will see an "Upload files from your Computer" section that allows you browse for attachments. Click on the Browse button and select the files you wish to attach. When ready, click on the associated Upload button to initiate the upload. When complete, you can close the Manage Attachments window box.

---

### Post by haxerius on 2015-11-25
done and done! :) but i still need help to get my wifi working!

---

### Post by chili555 on 2015-11-25
Here is you wireless card!> Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
	Subsystem: Broadcom Corporation Device [14e4:0607]Please check here for instructions:  [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by haxerius on 2015-11-26
Thanks mate! :) did the trick for me! :)

---

### Post by haxerius on 2015-11-26
Only problem now when i click to login at my home network through wifi it doesnt promp me for password.... So i can try to connect but without password nothing will happen :D

Solved it with "create new wireless connection" thought it would do something completly different but it did the trick! :) 

Case closed, thanks for the help!

---

