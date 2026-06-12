---
title: "installing speedtouch`s driver"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by redwinder on 2007-06-14
Hello

i tried this guide [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch) but i run in to a problem,can anyone help me?, i am stuck in this step:

> Preparing the firmware

You now have the needed firmware - but that is not enough - the firmware file needs to be prepared and for this we will use a tool called firmware-extractor. The firmware-extractor splits the firmare file in two pieces so it vcan be loaded into the modem's memory. So download the firmware-extractor and move it to the fresh created working folder: 
mv firmware-extractor speedtouch

Now we will split the firmware using the following commands depending on the modem revision: 
cd speedtouch
chmod +x firmware-extractor
./firmware-extractor KQD6_3.012

if you have a 0 or 2 revision modem or: 
[B]cd speedtouch &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012[/B]

if you have a 4 revision modem. After that you will have two files in the speedtouch folder: speedtch-1.bin & speedtch-2.bin is just the firmware splited in two parts. 

i am supossed to put something in the x?, because when i run it it says that there is no directory, i should extract the firmware extractor `s files too?, please help
__________________

---

### Post by redwinder on 2007-06-15
nvm i got the step to work today, anyway i did all of the steps in the guide and it still didn`t work!, could had something to do with the fact the the guide is for Ubuntu 6.10 (Edgy Eft) because i am using version 7.04. or it can still work?

---

### Post by Rui Pais on 2007-06-15
hi, [try this]("http://ubuntuforums.org/showthread.php?t=445701").

---

