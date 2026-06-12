---
title: "Wirelees adapter Drivers?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by SArcasm Inc on 2009-07-17
Hi all

This is my second attempt at ditching windows, however the same problem gets me everytime.

There never seems to be much driver support.

I just installed Ubuntu 9.04 , I have a WUSB600N adapter.

After searching the web all i get is compile this change that and so forth. Honestly about all i know how to do when it comes to Linux is to install it and stumble around the OS

Is there anyone out there that has a driver that i could just install and it would work?

I downloaded the Linux driver from Ralink R2870 but i have now idea how to make it work.

Is there a step bye step guide somewhere that a complete Linux noob could follow to get this thing to work?

Thanks
Jesse

---

### Post by nothingspecial on 2009-07-17
See [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=972060&highlight=wusb600n")

Anything you don`t understand post back

---

### Post by pedro3005 on 2009-07-17
EDITED: My post was worthless now seeing the above link. Follow it :)

---

### Post by SArcasm Inc on 2009-07-19
Thanks nothingspecial for the reply


Step 1 - Download the modified driver source here: [http://rapidshare.com/files/160951015/WUSB600N.tar](http://rapidshare.com/files/160951015/WUSB600N.tar)
Step 2 - Extract WUSB600N.tar to a folder
Step 3 - Open a terminal and navigate to the newly created WUSB600N folder
Step 4 - type "sudo make" without quotes
Step 5 - Copy the file:
[LIST]
[*]sudo mkdir /etc/Wireless
[*]sudo mkdir /etc/Wireless/RT2870STA
[*]sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
[/LIST]
Step 6 - open the WUSB600N/os/linux folder and type "sudo insmod rt2870sta.ko" again without quotes.


anyhow, i got as far as step 5 copy the file 

what file am i copying?, i typed the sudo commands making the directories but at the end it is saying RT2870STA.dat could not be found type deal. 


Any help would be great 

Thanks 
Jesse

---

### Post by nothingspecial on 2009-07-20
Where exactly is the WUSB600N folder?

Your Desktop? Home folder?

---

