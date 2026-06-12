---
title: "unable to configure b43-fwcutter while installing softwares"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by samvedan on 2011-06-22
I

---

### Post by samvedan on 2011-06-22
al

---

### Post by Bucky Ball on 2011-06-22
Have you plugged in an ethernet cable, gotten updates, and checked System>Administration>Additional Drivers???

---

### Post by samvedan on 2011-06-22
N

---

### Post by samvedan on 2011-06-22
> **Bucky Ball said:**
> Have you plugged in an ethernet cable, gotten updates, and checked System>Administration>Additional Drivers???

a

---

### Post by samvedan on 2011-06-22
Please reply

---

### Post by samvedan on 2011-06-23
is there anybody online to help me to get the problem solved?

---

### Post by wildmanne39 on 2011-06-23
> **samvedan said:**
> is there anybody online to help me to get the problem solved?Hi, if you gave more information, and not answer with just a letter you might get some help.

---

### Post by josephmills on 2011-06-23
download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

Then transfer it over to your Ubuntu box 

Now in  your Ubuntu Box [computer]  please make your way to your **Home folder ** 

Once you are at your home folder right click on your home folder and ** make a new folder and call it Wireless**
[IMG]http://img862.imageshack.us/img862/8053/screenshotba.png[/IMG]





Now that you have made a new folder called wireless in your home directory. It is time to **move the downloaded file into the new folder called wireless** 
[IMG]http://img850.imageshack.us/img850/4563/screenshot1kl.png[/IMG]






Next we need to move that folder to the firmware directory to do this open your terminal and type in 
```
sudo cp -r ~/Wireless/* /lib/firmware/
``` 
[IMG]http://img101.imageshack.us/img101/5329/screenshot5ei.png[/IMG]






Now lets double check to make sure the download made it to the firmware directory. Too do this type this into the terminal 
```
ls /lib/firmware
```
Do you see it there ? Good if not it did not moved. Go back to the last step and try again. But if you do see it lets move on to the next step
[IMG]http://img151.imageshack.us/img151/5092/screenshot3ln.png[/IMG]





Ok so now that the download is in the firmware dir we are going to have to go there. To go there open your terminal and type in. 
```
cd /lib/firmware 
```
Now that you have moved lets double check to make sure this next code tells us where we are in the computer file dir. This next code stands for "print working directory" ```
pwd
``` are you at /lib/firmware if so good if not go back one step 
[IMG]http://img143.imageshack.us/img143/3945/screenshot4zv.png[/IMG]





Now that we are in the firmware directory. We have to extract the download to do this type in 
```
sudo -s
``` then enter your password then 
```
tar -xzf b43-all-fw.tar_.gz
```
then 
```
exit
```

Now it is time to reboot 
```
sudo reboot 
```

Do you have wireless now ?

---

### Post by dFlyer on 2011-06-23
> **samvedan said:**
> is there anybody online to help me to get the problem solved?

I'm really having a hard time following you post above. Can you provide more information about your modem, ubuntu version, how you currently connect to the network and what you have tried that has not worked. One letter replies don't help.

---

### Post by Bucky Ball on 2011-06-24
Am unsubscribing from this ludicrous thread. If you want some help, post another thread and ***don't*** answer with a single letter. If you have a mischievous goblin who is editing your post, forgiven. If not, what's the caper?  

Bye for now and good luck.

---

### Post by wep940 on 2011-06-24
> **josephmills said:**
> download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)

Then transfer it over to your Ubuntu box ....



I don't know about the clown who opened this thread, but I want to say a BIG *THANK YOU*!!

I had done everything I could find for getting my Broadcom 4306 to work - followed the Wiki's, followed threads in the forum, search the net, etc., including installing some firmware, but it still always said the firmware was missing.

Your solution worked great - extremely easy - and bingo - my wireless was up!

Thank you!

---

### Post by gg48gg on 2011-08-21
> **josephmills said:**
> download this file  [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
...

This firmware package did the trick after trying STA drivers, then NDIS wrappers, and still no glory.  Don't forget to disable the NDIS stuff if you installed it previously.  I can't believe it was this easy.

Joseph, thank you for taking the time to write up such detailed instructions.  The community appreciates it.  Cheers.

-G

---

### Post by iconoclast hero on 2011-08-27
OK, was referred to this thread and I followed everything and when I rebooted, I think for a few seconds it might have been connected...  Oh and as I was typing this, it said connection established, so I pulled the CAT5 out of the NIC and tried to ping but nothing.  Then it said Network Disconnected and I'm back to wired.  A dialog keeps popping up looking for network authentication but it just doesn't connect.  I am sure that I have the password right (it is my name:  I think I'd get it right a large percentage of the time), the SSID, I know the network works with other computers, I've tried it unauthenticated, the card was working in windows, etc.  

Any other thoughts?

BTW, 10.04, and ```
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```.  The outside of the hatch covering the network card says it is a BCM94306MP.  I think that should be all relevant info except:
```
root@emily:/lib/firmware# ndiswrapper
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
apt-get install ndiswrapper-common 
```
and my router is normally running WPA2-PSK, but since I have an older computer I've tried WPA-PSK + WPA2-PSK as well as no encryption but nothing works.

I'm sure I'm forgetting some little detail, and depending on what happens after Irene gets here and has her way with me tonight, I might not be back for a little while...  :)

---

### Post by bkratz on 2011-08-27
Well you have the earlier version of BCM4306 (rev2) so you need the 

b43-fwcutter with the firmware-b43legacy-installer 

to have success. It is all available in synaptic


more info?
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

