---
title: "Cannot connect to my wireless network. Please Help."
date: 2011-04-22
forum: New to Ubuntu
---

### Post by crob26 on 2011-04-22
Hello! I am running ubuntu 10.10 off of my USB on my dell inspiron desktop. I have a Broadcom BCM4318 AirForce One wireless card, and i cannot get ubuntu to connect to the network. Any help is appreciated, thanks.

---

### Post by Hippytaff on 2011-04-22
Hi and welcome to the forums

The first thing you could try is going to system -> administration -> additional drivers. If there is a BCM type option try installing it. If that doesn't work people here will be better able to assist you if you download and run the wireless script (link below) and post the wireless-results.txt... to save time :-)

[This link]("http://ubuntuforums.org/showthread.php?t=1604868") might also help

---

### Post by BertN45 on 2011-04-22
I had the same problem with the BCM4311. 

In my case the driver from "additional drivers" was recommended after the boot, but did not work. 

In that case:
- deactivate the Broadcom STA driver again, go system -> administration -> additional drivers
- go to the Synaptic Package Manager in the same menu
- type b43 in the filter box 
- install "firmware- b43-installer" and the "b43-fwcutter"

That solved my problem and that driver should also work with the BCM4318

---

### Post by crob26 on 2011-04-22
> **Hippytaff said:**
> Hi and welcome to the forums

The first thing you could try is going to system -> administration -> additional drivers. If there is a BCM type option try installing it. If that doesn't work people here will be better able to assist you if you download and run the wireless script (link below) and post the wireless-results.txt... to save time :-)

[This link]("http://ubuntuforums.org/showthread.php?t=1604868") might also help

i ran this in the terminal, and this is what happened...

Performing initial enviroment tests.....
rfkill is not installed!...rfkill can unblock wireless blocks should there be any, would you like to install it?  y/n
y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package rfkill
Error installing rfkill




This script will seek to return as much relevant information as possible to help diagnose the problem

Please select from the following options
1. Retrieve network status information
2. Retrieve network status information and perform a single connectivity check
3. Retrieve network status information and repeatedly perform connectivity checking
    >>>>>> To exit continual connectivity checking hit the <enter> key <<<<<<
4. Try to reconnect to disabled interface
5. Exit

...and then it suddenly crashed when i chose an option (being the first one)

---

### Post by Hippytaff on 2011-04-22
Thats a bug that needs sorting...thanks for bringing that to my attention. can you open a terminal and do```
sudo apt-get install rfkill
```then run the script again. It should do the job then...apologies.

Edit - it is odd, just tried to re-create the problem - are you online on that pc (via ethernet?) if so can you post the output of ```
cat /etc/apt/sources.list
```

---

### Post by crob26 on 2011-04-22
> **Hippytaff said:**
> Edit - it is odd, just tried to re-create the problem - are you online on that pc (via ethernet?) if so can you post the output of ```
cat /etc/apt/sources.list
```

no im just switching back from windows to ubuntu, but ill do that and let you know how it goes.

---

### Post by crob26 on 2011-04-22
> **Hippytaff said:**
> Thats a bug that needs sorting...thanks for bringing that to my attention. can you open a terminal and do```
sudo apt-get install rfkill
```then run the script again. It should do the job then...apologies.

Edit - it is odd, just tried to re-create the problem - are you online on that pc (via ethernet?) if so can you post the output of ```
cat /etc/apt/sources.list
```

well this is odd.. when i started ubuntu, it showed a list of wireless networks, which its never done before. and now im connected to my network just fine. i think it might be because earlier i installed "ndisgtk" from synaptic and downloaded my wireless card driver from the Internet and installed it, but i did that hours ago and it didnt seem to work. but thank you very much for your help anyway. i also had another question that is off topic but i was hoping you could answer. if i reinstall ubuntu on my flash drive, and copy the casper-rw folder from before, and put it on the flash drive with the new ubuntu i installed, will all my persistent files like my settings and such be on the new ubuntu? thanks.

---

### Post by Hippytaff on 2011-04-22
Glad you got the wireless thing sorted...I wouldn't like to say for sure about your files...I don't know :-)

---

### Post by crob26 on 2011-04-22
alright thanks!!

---

### Post by Hippytaff on 2011-04-22
maybe start a new thread.

and remember to mark this thread as solved in the thread tools at the top of the page :-)

---

