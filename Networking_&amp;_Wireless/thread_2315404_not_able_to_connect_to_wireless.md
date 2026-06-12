---
title: "not able to connect to wireless"
date: 2016-02-28
forum: Networking &amp; Wireless
---

### Post by jerry_3 on 2016-02-28
Sorry for my ignorance. My friend replaced Ubuntu with my Windows XP OS.  I don't know much about this stuff at all. When I got home with my laptop, I was unable to log into my wifi.  I found this website: [http://linux-drivers.net/](http://linux-drivers.net/), hoping I needed to add my wifi driver and that would give me wifi again. However, I can't seem to find anything or at least I'm not understanding what I have to do to load a driver on Ubuntu. 

I have a Dell D630 laptop.   My router is a Linksys E2500.  I tried inputting my router disc into my drive, but after it loaded I didn't know what to do. I didn't see anything that I am familiar with like in Windows to download the files.  

I read the two messages in the start of this forum about running something prior to trying to access the wifi, but I don't understand what they are trying to say. Load it onto where?  

Can someone please walk me thru this? I am completely loss at this point. I even had a horrible time getting this dumb orange Open New Thread button to show up. I had clicked on open SSO login several times, but it didn't seem to work or something or I was doing something wrong. I thought I had logged in, but obviously not until about the 3rd or 4th time. Finally the little button came up.  Very frustrated right now. 

Anyways, can someone please help me figure out what I need to do to get my laptop to connect to my wifi?  Thank you.

---

### Post by Hadaka on 2016-02-28
Hi, please open a terminal...ctrl/alt/t and then Copy and paste
one line at a time.
```
lspci -nnk | grep -iA2 net
lsmod | egrep 'wl|b43|iwl|ath'
rfkill list all
```
please post the output
thanks.

---

### Post by jerry_3 on 2016-02-28
Hadaka, when I press the ctrl alt t, should I erase what comes up first?  It came up as follow:  jerry@jerry-Latitude-D630:~$      I was just wondering if I should erase that before I copy and paste each line you provided.  Thanks.  

When I pressed the ctrl alt t and it pulled up, it gave me the message above.  I copied and pasted the first line you provided above and then pressed enter.  I went back to this message board and copied the second line. When I pressed ctrl alt t again, it came up and the old stuff was gone besides the jerry@ part. I pasted and pressed enter again. Like the last time it printed out some additional info. I went back to the forum to copy the third line and again when I went back to ctrl alt t, only the jerry@jerry... part was there. I pasted the third line again and it printed out some stuff again.  I disconnected my ethernet cable, but still wasn't able to get wifi at all.

---

### Post by jerry_3 on 2016-02-28
jerry@jerry-Latitude-D630:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell Device [1028:01f9]
    Kernel driver in use: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge
jerry@jerry-Latitude-D630:~$ lsmod | egrep 'wl|b43|iwl|ath'
b43                   397312  0 
bcma                   49152  1 b43
mac80211              647168  1 b43
cfg80211              471040  2 b43,mac80211
ssb                    57344  2 b43,ssb_hcd
jerry@jerry-Latitude-D630:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jerry@jerry-Latitude-D630:~$

---

### Post by Hadaka on 2016-02-28
Hi jerry_3, it looks like you have the correct driver loaded.,b43
and nothing in the blocked list so let try the easy fix first. Again
open a terminal..ctrl/alt/t...and please copy and paste one line at a time.
*Note the "sudo" command requires you to type in your password...
you will not see anything you type when you type the password..this is normal
just carefully enter your password and press return. you will only have to do that one time this time.
Be sure your wired ethernet is connected and active.
please copy and paste one line at a time.
```
sudo apt-get install linux-firmware
sudo apt get update
sudo apt get dist-upgrade
sudo apt-get --remove purge firmware-b43-installer
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```

*IMPORTANT the 2nd command above.."sudo apt-get update"....may take some time to complete. do not inturpt it, let it complete
then do the next commands untill done,.
when all commands are finished...remove your wired connection...boot and test wireless
thanks.

---

### Post by jerry_3 on 2016-02-29
This is what I got with the second line "sudo apt get update":  What should I do?  Should I just keep going?  

jerry@jerry-Latitude-D630:~$ sudo apt get update
E: Invalid operation get
jerry@jerry-Latitude-D630:~$

---

### Post by jerry_3 on 2016-02-29
This is what all I got so far: 

jerry@jerry-Latitude-D630:~$ sudo apt-get install linux-firmware
[sudo] password for jerry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
linux-firmware set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
jerry@jerry-Latitude-D630:~$ sudo apt get update
E: Invalid operation get
jerry@jerry-Latitude-D630:~$

---

### Post by Hadaka on 2016-02-29
Hi, that was a typo on my part,sorry for that, it should be..
```
sudo apt-get update
```
i had forgotten the "-" in apt get....apt-get
please try the correct command.
thanks.

---

### Post by jerry_3 on 2016-02-29
Sorry, but I got another error on #3: 

jerry@jerry-Latitude-D630:~$ sudo apt get dist-upgrade
E: Invalid operation get
jerry@jerry-Latitude-D630:~$

---

### Post by X-RED_Tech on 2016-03-01
You're missing the "-" in **apt-get** again. Keep that in mind for the future.

---

### Post by jerry_3 on 2016-03-01
LOL. I guess I didn't pay that much attention to it.  Of course I don't want to screw anything up either. I got all the way to the last link to copy and paste. Not sure if it actually did anything or not.  I guess it did something, but it didn't give an error nor did it ask for password. It just instantly gave me another line item to type into. Does this look okay?  Should I just reboot and see if my internet works?

jerry@jerry-Latitude-D630:~$ sudo modprobe b43
jerry@jerry-Latitude-D630:~$

---

### Post by Hadaka on 2016-03-01
yes boot and report the results
thanks

---

### Post by jerry_3 on 2016-03-01
Thank you, thank you, thank you. That did the trick. My internet (wifi) is working well. Thanks again.  

Oh, did I forget to say "Thank You"? 

:)

---

### Post by Hadaka on 2016-03-01
You are welcome, sorry about forgetting the "-" in apt-get
not once but twice, i guess my "-" key must have been out of ink.
please take time to mark your thread solved.
log in to your thread,go to your first post. click [B]Thread Tools  
then choose SOLVED

[/B]

---

