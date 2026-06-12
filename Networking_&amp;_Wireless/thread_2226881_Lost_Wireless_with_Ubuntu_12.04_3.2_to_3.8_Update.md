---
title: "Lost Wireless with Ubuntu 12.04 3.2 to 3.8 Update"
date: 2014-05-29
forum: Networking &amp; Wireless
---

### Post by matthew41 on 2014-05-29
I bought a 10.1 Asus laptop with Ubuntu 12.04 to use with my 3D Printer. Got a great deal on it I thought, $244 on Amazon. I have never used Linux before but have heard so many great things about it I really wanted to try it.


I followed instructions by Makerbot to install Makerware on this system. 

 It told me to do this...

[I][U]If you are using a version of Ubuntu 12.04 downloaded before April 2013,  you may need to update your kernel in order to run MakerWare 2.3 or  later. 
To find out whether you need to update your kernel, run the  following command:  uname -r  [/U][/I]*_If the result begins with a number smaller than 3.8, you will need to update. To update, enter the following command:_*
*_  sudo apt-get install linux-image-generic-lts-raring_*

After I did this I now have no wireless. It says under the wireless menu *_"wireless is disabled by hardware switch"_*

Do I need to update something else? If yes, then I will have to wait till I get home since I dont have a hardline to connect to here at work.

Any help greatly appreciated.

---

### Post by praseodym on 2014-05-29
Run this command and reboot:

```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
Check the buttons.

---

### Post by matthew41 on 2014-05-29
Connected! Thank you Praseodym!

---

