---
title: "Cannot get wireless PCMCIA adapter working using ndiswrapper"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by jallajalla on 2005-10-25
I recently installed Breezy and immediately run into the problem of not being able to use my wireless PCMCIA adapter. After reading on the web for hours about ndiswrapper I thought that the solution was found. I still have problems and cannot use wireless internet.

This is what I have done so far:

My wireless adapter is BT Voyager 1060. It is dead when I run Ubuntu (the power diod is off). It works fine in WIndows XP. Writing lspci I get the following information:

...
0000:02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
...

I have tried ndiswrapper and followed the guide at:
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)
I installed ndiswrapper using the Synaptic Package Manager. First I used a .inf-file found on the web, but when it didn't work I thought it was something  wrong with the driver. Therefore I copied the file bcmwl5.inf file from Windows, which is located in the BT Voyager directory in Program Files. It's a 1.3 MB large binary file. I removed the old driver and installed the new one using:

ndiswrapper -i bcmwl5.inf

Now, when typing "ndiswrapper -l" I get:

Installed ndis drivers:
bcmwl5  invalid driver!

Apparently I am stuck here. Using the previous, much smaller, driver from the web, let me install the driver, showing

Installed ndis drivers:
bcmwl5 driver present

when running "ndiswrapper -l". However, it didn't say that the hardware was present. Also, after installing the driver I did:

ndiswrapper -m
modprobe ndiswrapper

and added the word ndiswrapper as the last line of the /etc/modules file with

Then I restarted the computer. No progress.

I am not at all closer to the solutan than before. The adapter is still dead and I cannot use wireless internet. Any ideas of how to solve this, too common, problem?

Thanks.

---

### Post by janne5011 on 2005-10-25
I dont know if this is any help, but look in folder .is the inf and sys file really in it?
I got the same problem and sometimes only folder is created but no files in it,
Dont know why.
can also look here
[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

---

### Post by Tass on 2005-10-29
Hi

I had the same problem.  It seemed that I didn't have the path exactly right, and it didn't install, but I still had the : "invalid driver"

I removed the invalid driver : sudo ndiswrapper -e bcmwl5, then reinstalled it :
to install the new driver : sudo ndiswrapper -i /dev/drivers/bcmwl5.inf.

Maybe just make sure the list is empty (sudo ndiswrapper -l), before you add it, and check that it gives a successful message.

Hope this helps

---

### Post by Tass on 2005-10-29
Hi

I had the same problem.  It seemed that I didn't have the path exactly right, and it didn't install, but I still had the : "invalid driver"

I removed the invalid driver : sudo ndiswrapper -e bcmwl5, then reinstalled it :
to install the new driver : sudo ndiswrapper -i /dev/drivers/bcmwl5.inf.

Maybe just make sure the list is empty (sudo ndiswrapper -l), before you add it, and check that it gives a successful message.

Hope this helps

EDIT : Sorry for the double-post - something went wrong

---

### Post by jallajalla on 2005-10-29
Hi,

Thanks for the tips. However, I took the easy way out and I reinstalled Ubuntu completely. I had probably messed up many things too much... I then followed Janne5011's tip of following the instructions on [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

And, to my surprise, the light now comes on on my wireless adaptor and I can go to the network settings and there is the wireless card! However, I still have problems. I am not able to detect the network, or access the internet.

I enter the WEP key and the SSID. I make sure that the router is configured to WEP and allow all mac-addresses, etc, just to make sure I'm not blocking anything. But still, no detection of network. I've tried this with another wireless adaptor which Ubunto recognised automatically without using ndiswrapper. I am pretty sure I'm enetering the correct WEP key (using the ASCII choice). Is there any things I should consider that I am possibly doing wrong maybe? Any ideas of why I have trouble? Any other settings anywhere else I should be aware of?

---

### Post by Robo on 2005-10-30
I am having the same issue with my usr (Texas Instruments) card.  The card is there, and detected, but will not show any ssid's in the area (there are 2 that I know of, mine and my neighbours).  Even entering the ssid manually, the card will not connect.

---

### Post by jallajalla on 2005-10-31
Of some reason I was suddenly able to detect neighbouring networks including mine!  This happened when I restarted Ubuntu. However, I cannot configure my wireless settings so I can use my own network. I'm going to start a new thread with this issue.

---

### Post by Robo on 2005-10-31
lol, lucky you :)

---

