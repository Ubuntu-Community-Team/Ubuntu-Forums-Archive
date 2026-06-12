---
title: "Linux driver or ndiswrapper for RTL8180L chipset?"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by ljk on 2007-06-22
This is about wireless networking  but it is also an "Absolute Beginners" problem.
 
I have been trying to get my laptop wireless card to work with Ubuntu Feisty (7.04) without success.

The card is a "BUFFALOW WLI-CB-B11 Wireless LAN Adapter" which uses the RealTec  RTL8180L 802.11b MAC (rev 20) chipset. This information was obtained from a terminal command called "lspci". The first column read "02.00.0"

"lspci -n" informed me that the PCI ID was "10ec : 8180 rev 20"

This information pointed me to Realtec - the supplier of the chipset and also a company acknowledged as being "friendly" by the Free Software Foundation.

RealTec have different drivers for this chipset. There's one for Linux and another for ndiswrapper using a Windows driver and more that I don't understand.
 
_**How do I install the Linux driver?**_ The "read me" assumes expertise which I can only hope to acquire in the distant future.

I have made several attempts to use ndiswrapper, following instructions on the Ubuntu documentation site
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check")
all of which have failed.

Some of these failures must be attributed to my ignorance. I installed the ndiswrapper packages (-common & utilities) without knowing they were already included in Feisty. I also installed the GUI package which seems to be inconsistent (now you see it / now you don't???).

This is a fresh installation. If I can get wireless to work I can stop using Windows. Please help.

---

### Post by killdragon on 2007-06-22
Hi, try the following I used it and it works for me. And this is the the title of the thread

            that I found it at. The only reason is that you have a realtek  card that I think it might

            work.



        Linksys WUSB 11 v. 2.6 and WPC11 v. 4 don't work in Feisty 

        


    To use the native driver, you need to remove the r818x blacklist entry, like so:
 
    Code:

     sudo editor /etc/modprobe.d/blacklist

     Page down to the bottom, and you'll find some lines that look like this:

      Code:

      # buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
      blacklist r818x
      blacklist r8187

      Any line that begins with "#" is ignored, so add "#" in front of the r818x line to turn off  the    blacklisting of this module. Save the file, eject and re-insert the card, and it                                      should be recognized. Again, see the thread I linked above for more info.


Additionally, another thread discovered that for the essid, an additional character needs to be appended to the end (any character will do, although 'x' seems to be the current favorite). Thus, if your essid is "ducky", you'll need to use "duckyx".

So, without further delay, here is what is currently working well for me (after I plug in the card):

Code:

sudo modprobe r818x
sudo iwconfig wlan0 essid duckyx
sudo dhclient wlan0

---

### Post by ljk on 2007-06-27
[QUOTE=killdragon;2896167]Hi, try the following I used it and it works for me. And this is the the title of the thread

            that I found it at. The only reason is that you have a realtek  card that I think it might

            work.



        Linksys WUSB 11 v. 2.6 and WPC11 v. 4 don't work in Feisty 

        


 Thanks. I followed the posts and tried to copy every suggestion but nothing worked. I'll give it another go when I can get back to a clean re-install. I've entered so many commands in the terminal on this and many other problems that I think it might be best to start again from scratch.

Much obliged & best regards.

---

### Post by ljk on 2007-06-30
Many thanks to Killdragon - I am posting this from a wireless laptop using Ubuntu.

I used  [Wubi]("http://wubi-installer.org/") for theUbuntu installation.

I followed the advice you gave me and "unblacklisted" the driver for the RTL8180 chipset.
At first there were no results.
I restarted and the wireless LAN card started flashing. This was progress indeed but, although the wireless network was recognised, I could not connect to the Internet.

I added an "x" to the end of the wireless network name in the "Network" panel and restarted - bingo!

Thank you very much indeed.


> **ljk said:**
> [QUOTE=killdragon;2896167]Hi, try the following I used it and it works for me. And this is the the title of the thread

            that I found it at. The only reason is that you have a realtek  card that I think it might

            work.



        Linksys WUSB 11 v. 2.6 and WPC11 v. 4 don't work in Feisty 

        


 Thanks. I followed the posts and tried to copy every suggestion but nothing worked. I'll give it another go when I can get back to a clean re-install. I've entered so many commands in the terminal on this and many other problems that I think it might be best to start again from scratch.

Much obliged & best regards.

---

### Post by ljk on 2007-06-30
Note - after my last message I switched everything off and on restart the next day the wireless lan card was not detected.

I disabled "roaming" mode for WIRED network; restarted & it worked again.

I had to do the same after allowing "software update" to do its updating and another restart.

I have no idea why this worked but it did.

Hope this helps anyone looking for info on the same chipset.

Many thanks again.

---

### Post by killdragon on 2007-11-18
> **killdragon said:**
> Hi, try the following I used it and it works for me. And this is the the title of the thread

            that I found it at. The only reason is that you have a realtek  card that I think it might

            work.




        Linksys WUSB 11 v. 2.6 and WPC11 v. 4 don't work in Feisty 

        


    To use the native driver, you need to remove the r818x blacklist entry, like so:
 
    Code:

     sudo editor /etc/modprobe.d/blacklist

     Page down to the bottom, and you'll find some lines that look like this:

      Code:

      # buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
      blacklist r818x
      blacklist r8187

      Any line that begins with "#" is ignored, so add "#" in front of the r818x line to turn off  the    blacklisting of this module. Save the file, eject and re-insert the card, and it                                      should be recognized. Again, see the thread I linked above for more info.


Additionally, another thread discovered that for the essid, an additional character needs to be appended to the end (any character will do, although 'x' seems to be the current favorite). Thus, if your essid is "ducky", you'll need to use "duckyx".

So, without further delay, here is what is currently working well for me (after I plug in the card):

Code:

sudo modprobe r818x
sudo iwconfig wlan0 essid duckyx
sudo dhclient wlan0





I have also found that you should only use Ubuntu's network tool.

---

### Post by gecky on 2007-11-29
Hi,
I installed the ubuntu 7.10 Gutsy Gibbon and I haven't problem.
The installation had finded the Realtek 8180 Wireless.
Finally, I've tried three linux version (Fedora, Debian and Ubuntu but not the last version), for playing i've installed the Gusty version and, GREAT ... the wireless had started now, I've must change the properties in Network settings for my lan.

Sorry for my english

---

