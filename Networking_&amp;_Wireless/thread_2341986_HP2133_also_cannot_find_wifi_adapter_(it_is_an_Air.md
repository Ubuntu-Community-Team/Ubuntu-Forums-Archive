---
title: "HP2133 also cannot find wifi adapter (it is an Airlink 101 N 300 USB adapter)"
date: 2016-11-02
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2016-11-02
The rains continue so I have hauled out my HP 2133 netbook which has Lubuntu 12.04 on it. It also has a problem with wifi. Clicking on the network connections symbol on the lower right, everything is greyed out except VPN connections. Wired says: "Wired Network disconnected" and Wireless says "Device not ready (Firmware missing)" 

lsusb returns:

Bus 001 Device 001: ID Id6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID Id6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID Id6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID Id6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b107 Chicony Electronics Co CNF7070 Webcam
Bus 003 Device 003: ID 03f0:171d H-P Bluetooth 2.0 Interface [Broadcom BCM2045]

What other info can I gather?

---

### Post by jeremy31 on 2016-11-02
Strange that the device isn't listed in your results.  Perhaps ```
lshw -c net
``` or ```
dmesg | grep firm
```
Will reveal more about this device and what firmware it needs

---

### Post by Odyssey1942 on 2016-11-02
Jeremy, ran the first command and got three screenfulls of info none of which I can make heads or tails of. The very last of it has a bit about "Wireless interface, physical id: 2 yada yada, capabilities ethernet physical wireless yada yada. Is this of interest and do you need the yada yada? (I have to type it on a second computer and I am a dreadful typist but happy to post anything needed)

Am posting this much while I restart the terminal (it seems to have stopped responding) or maybe also the netbook. Let me know about the above while I try to run the second command. Thanks.

Killed and restarted terminal, ran the dmesg which basically said I neet to go to (URL) and download the correct driver version, but how do I do this if I can't reach the internet on the netbook?

---

### Post by jeremy31 on 2016-11-02
Do you have a USB thumb drive or some other way to transfer a text file from the Ubuntu computer to one with internet access?  If so you can
```
lshw -c net > info.txt
```
```
dmesg | grep firm >> info.txt
```
Then copy the info.txt file and post the contents using code tags if it is that long and it might be better to paste at paste.ubuntu.com and post the URL

The lshw -c net results usually shows the driver for any ethernet/wireless device on the computer along with the firmware version if firmware is loaded

---

### Post by Odyssey1942 on 2016-11-02
This is really embarrassing. I have spent the entire time since your last post making a text file with the output of both commands. I copied the info.txt file onto a thumb drive, move the thumb drive over to this computer and open it (for info when I copy it to the thumb drive, the ".txt" extension is lost and when I open it, all formatting is lost and it is a massive jumble.) 

Can you imagine what I am doing wrong and suggest a modification of this procedure that might assist this tech challenged newbie to create a file that retains the formatting so that I can post it as you suggested?

---

### Post by jeremy31 on 2016-11-02
Just paste the contents at paste.ubuntu.com and post a URL.  I will see if something sticks out

---

### Post by Odyssey1942 on 2016-11-02
Lucked out! On a whim, opened the file with Wordpad instead of Notepad and voila'

[http://paste.ubuntu.com/23418459/]("http://paste.ubuntu.com/23418459/")

---

### Post by jeremy31 on 2016-11-02
See Hadaka's post [https://ubuntuforums.org/showthread.php?t=2316978](https://ubuntuforums.org/showthread.php?t=2316978)

The attached zip file contains the firmware you need for the internal wifi to work

---

### Post by Odyssey1942 on 2016-11-02
Hot Damn! Have internet! I didn't know where to start and you make it seem so easy.

Apology for disappearing but the little lady demanded my presence at a nearby restaurant. Good dinner too!

I am most appreciative of all your good help. And if you are half as much a whiz on computer freezes as you are on networking would love to have your input at:

[https://ubuntuforums.org/showthread.php?t=2342001]("https://ubuntuforums.org/showthread.php?t=2342001")

Thanks again.

---

