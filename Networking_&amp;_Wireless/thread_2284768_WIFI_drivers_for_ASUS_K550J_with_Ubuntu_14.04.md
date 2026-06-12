---
title: "WIFI drivers for ASUS K550J with Ubuntu 14.04"
date: 2015-07-01
forum: Networking &amp; Wireless
---

### Post by PedroPV on 2015-07-01
I have a ASUS K550J with Ubuntu 14.04. Works very well, but wifi connections are very unstable. Is there any good driver for this?
Thanks
PedroPV

---

### Post by PedroPV on 2015-07-02
In fact the laptop is **ASUS K550J**
PedroPV

---

### Post by slickymaster on 2015-07-02
*Moved to the ***Networking & Wireless*** sub-forum*

Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by PedroPV on 2015-07-08
Sorry, but I could not understand and make any use of the text,
I would like to know whether there is or cam be obtained a driver for wifi for ASUS K550J.
I would hate to have to go back to Microsoft, just because of WIFI
Thanks
PedroPV

---

### Post by Vladlenin5000 on 2015-07-08
You're suppose to run it and post the results here.
There's no "driver for Asus K550J" - and is it K550JD, K550JK or K550JX? - simply because any one of the aforementioned models shipped with 4 different wifi cards. In order to get support you need to know which one.

---

### Post by slickymaster on 2015-07-09
> **PedroPV said:**
> Sorry, but I could not understand and make any use of the text,
I would like to know whether there is or cam be obtained a driver for wifi for ASUS K550J.
I would hate to have to go back to Microsoft, just because of WIFI
Thanks
PedroPV

Just follow the instructions [here]("https://github.com/UbuntuForums/wireless-info").

---

### Post by PedroPV on 2015-07-10
The laptop is ASUS K550JK with Ubuntu 14.04
Does anyone know about drivers for WIFI
Thanks 
PedroPV

---

### Post by Vladlenin5000 on 2015-07-10
> **PedroPV said:**
> The laptop is ASUS K550JK with Ubuntu 14.04

Thanks but it isn't really helpful as I explained before: That laptop can have up to 4 different wireless cards (Realtek, Ralink/Mediatek, Broadcom or Atheros). **We need to know which one in order to help you. **The troubleshooting and solutions are different according to the hardware.
Please follow the instructions above and provide the results of the wrieless script. Otherwise, **no help is possible.** I hope you understand and proceed accordingly.

---

### Post by Vladlenin5000 on 2015-07-10
Oh and, by the way, if you no longer need help with [http://ubuntuforums.org/showthread.php?t=2276422](http://ubuntuforums.org/showthread.php?t=2276422) then please post your solution (if any) and use the thread tools to mark it as solved. Thank you.

---

### Post by PedroPV on 2015-07-10
I'll try to find out which wifi card  is it

---

### Post by Vladlenin5000 on 2015-07-10
> **PedroPV said:**
> I'll try to find out which wifi card  is it

PLEASE run the script as instructed. Knowing the hardware is *conditio sine qua non* but not enough!
The script will get all the information needed for troubleshooting.

---

### Post by PedroPV on 2015-07-24
**Problem solved**. 
This can be useful for many.
I did two thing: instaled Ubuntu 15.04 and substitute the original Realtech wifi card for the** Intel Centrino Advanced-N 6230**
Thanks for all the help.
PedroPV

---

### Post by Vladlenin5000 on 2015-07-24
You're welcome but no need to thank anyone...
Since you didn't provide any useful information, we actually didn't help you at all, we couldn't.

PS - It's **Realtek**. And no, you didn't solve anything. What you did is a typical example of the typical Portuguese behavior called "desenrascar-se" but don't fool yourserlf. Replacing the card for one natively supported isn't "a solution". You solve nothing and, unfortunately, also learned nothing in the process. And, at least, you should have learned you need to provide complete and pertinent information when you ask for help.

---

### Post by PedroPV on 2015-09-05
I solved the problem wuth a wifi Itell card.

---

