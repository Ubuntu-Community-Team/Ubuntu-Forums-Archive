---
title: "SSID showing but failling to connect to wifi BCM43224 Probook 6555b"
date: 2015-10-18
forum: Networking &amp; Wireless
---

### Post by danielbr2 on 2015-10-18
Hi. I have previously experienced some wifi-issues with ubuntu, but today i'm at a loss. 
I did run the wifi-script and i have looked at countless askubuntu suggestions and similar regarding other broadcom-cards, including the solutions provided in the sticky.
The first problem was that my WIFI-card did not show up. I fixed that problem only to discover another one. The problem is that i can't connect to my two networks "W@H" or "W@H_5". Both are not encrypted and it should be a piece of cake to connect to them

-i have tried the open and closed source drivers both in the GUI and in terminal.
-i have attempted to purge and reinstall both open source and closed source drivers according to the sticky tutorials
-I tried to connect to my SSID using relevant terminal commands, to see if i could find any error messages
-i have scanned the output from dmesg to determine if there is any problems there to the best of my knowledge.

I would be very thankful for any assistance. Luckily the wired connection works. 
My current Ubuntu version is 15.04

Enclosed is the results from the WIFI-script.
What is most annoying about this specific computer is that the BIOS blocks any upgrade attempts to a newer WIFI-card. Any suggestions there? 
Let me know if any additional info is needed.

[ATTACH]265038[/ATTACH]

---

### Post by Hadaka on 2015-10-18
Hi from a working wired connection please do..
```
sudo apt-get remove --purge firmware-b43-installer
sudo apt-get remove --purge brcmsmac
sudo apt-get update && sudo apt-get upgrade
```
then do
```
sudo iw reg set NO
sudo sed -i 's/^REG.*=$/&NO/' /etc/default/crda
```
and..
```
sudo apt-get autoremove && sudo apt-get autoclean
```
reboot,remove wired connection,test wireless

---

### Post by danielbr2 on 2015-10-19
Thank you for your assistance. Can you briefly outline what the problem was so i can gain some insight from this? 
I will mark the issue as solved. Thank you for your time!

---

### Post by Hadaka on 2015-10-19
Glad it's working ! The main reason it wasnt was due to
the b43 module being loaded. So what we did was remove that
along with the needed default driver. then did the updates-this
is very important to get many features that are under constant
changes/ next we set your country code. it was set at 00, this can
cause issues. finally we cleaned up any junk that might have been
created by the updates or our deletion of drivers. Just read each line
carefully and it will make more sense to you.
have fun !

---

