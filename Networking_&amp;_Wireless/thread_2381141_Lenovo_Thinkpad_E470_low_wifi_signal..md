---
title: "Lenovo Thinkpad E470 low wifi signal."
date: 2017-12-27
forum: Networking &amp; Wireless
---

### Post by Furycd001 on 2017-12-27
HI Guys....

Just installed xubuntu on a Thinkpad E470 and cannot get a decent wifi signal. Laptop isn't far from the router and other devices receive decent signal from same spot. There is nothing in the way that would be blocking the signal either. Thank you for taking the time to read my post. 

[Here's my wireless info script]("https://paste.ubuntu.com/26264456/")

---

### Post by Hadaka on 2017-12-27
Hi, the wireless diagnostic report shows a few issues..

The ESSID is named the same for thr 2.4 and the 5 GHz connections..
```
BTHub5-R8XK  [AC4]>  Infra  11 2462 MHz  54 Mbit/s  42  &#9602;&#9604;__  WPA2  no        
BTHub5-R8XK  [AC1]>  Infra  44 5220 MHz  54 Mbit/s  42  &#9602;&#9604;__  WPA2  yes * 
```
As you can see in the *DMESG. section of the report,the connection roams between the two access points.
suggest you name them differently. something like ..BTHub5-R8XK and BTHub2-R8XK..to stop the roaming.

*IWCONFIG..
  Power Managemen is ON it should be OFF
 ```
wlp5s0    IEEE 802.11  ESSID:"BTHub5-R8XK"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: <MAC 'BTHub5-R8XK' [AC1]>   
          Power Management-[COLOR=#ff0000]**on**[/COLOR]
          Link Quality=31/70  Signal level=-79 dBm
```
*To Correct please do..
  ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
*Country Code UNSET 00..
   ```
Region: Europe/London (based on set time zone)
    country [COLOR=#ff0000]**00**[/COLOR]: DFS-UNSET
```
*To Correct please Copy and Paste..
 ```
sudo iw reg set GB
sudo sed -i 's/=.*/=GB/' /etc/default/crda
```
*This parameter should be set to 8...
 Please do..
```
echo options iwlwifi nohwcrypt=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
*Tripple check your antenna connections on router and verify the computer wifi card is properly seated
if possible..
Thanks.

---

### Post by Furycd001 on 2017-12-27
HI....

Thank you very much for replying :-) I have done everything that you suggested above, and I still have low wifi signal. I have separated the essid giving them both separate names and have also entered all of the commands you provided. I have also rebooted the machine and still the signal stays the same. Would you happen to have any more suggestions ??

---

### Post by Hadaka on 2017-12-27
Hi, please be sure to make the suggested changes to both 2.4 and 5 MHz ESSID's

Then click the wifi icon..and select Edit Connections
please set the IPv6 tab in both connections to IGNORE
see attached...
[ATTACH=CONFIG]277943[/ATTACH][ATTACH=CONFIG]277944[/ATTACH]
If you are still having difficulties, please attach a NEW wireless-info report
Thanks.

---

### Post by Furycd001 on 2017-12-28
[Here is a new wireless-info report....]("https://paste.ubuntu.com/26270293/")

My network now appears on all my devices as two different essids, though neither has a strong signal still on my laptop. Other devices seem to be fine in this same location. BTW thank you very much for all of this help. It is much appreciated.

---

### Post by praseodym on 2017-12-28
Try this also:

```
echo options iwlwifi 11n_disable=1 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot

---

### Post by Furycd001 on 2017-12-28
Thank you for commenting. I have tried what you suggested and rebooted the system but the wifi icon is still showing low signal. After trying everything in this thread so far my wifi does seem a tad better as webpages now seem to be loading faster.

---

### Post by Hadaka on 2017-12-28
Hi,thanks for renaming the ESSID's, that stopped the roaming.
While it is a big improvement, Ubuntu linux prefers NO open spaces in the
ESSID wifi name..so..single name or underscore to replace space would work.
Some of the commands i suggested took effect..some did not. After the changes
are made to both ESSID's, Please run ALL commands again for BOTH the essid's
2.4 connection and 5 MHz connection..be sure to boot after the commands are completed
for one essid BEFORE doing the other. Please Copy and Paste..one line at a time..BOTH connections.
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo iw reg set GB
sudo sed -i 's/=.*/=GB/' /etc/default/crda
echo options iwlwifi nohwcrypt=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Once complete for BOTH connections.Please test both connections.
*If still NO improvement..please do and post for BOTH connections..
```
cat /sys/module/iwlwifi/parameters/power_save
```
Thanks

---

### Post by Furycd001 on 2017-12-28
Again thank you for your totally awesome reply. I re-entered those four commands for both essids and rebooted with no joy. I also tried the power_save command but it did nothing either. The signal in the wifi icon is still low, though my browsing experience is noticeably faster. [Here is another new wireless-info report....]("https://paste.ubuntu.com/26271249/")

---

### Post by Hadaka on 2017-12-28
Hi, ok...I know all your other devices don't have this problem.
But, they are'nt Ubuntu linux. so first let's try this..
Connect with the 2.4 MHz connection only...is the signal stronger ?
*If NO..then go into the router configuration and  play with the B/G/N
settings. Try just b/g...no n...or set n...b/g/n if  it isn't set. and test.
if messing about with those settings does'nt increase the signal level then
it's highly likely you have a loose or broken antennea wire in that computer.
please post back your findings on the b/g/n settings...BOTH connections.
Thanks.

---

### Post by Furycd001 on 2017-12-28
Ok so my signal is all good now. The wifi icon is showing a strong signal. Was about to login and change some router settings when I noticed the icon update it's signal strength. Don't know what happened to make it changed all of a sudden but it seems to be sorted now. Thank you very much for all of the help and comments.

---

### Post by Hadaka on 2017-12-28
That is Great news !
I did however notice i gave you an incorrect command.
I apologize for not catching it sooner. It will have no effect
on your now good signal..so let's correct it.
Please open a terminal and then copy and paste..
*First command deletes the entries..
  second 2 commands correctly set the parameters.
```
sudo sed -i '/noh\|11n/ d' /etc/modprobe.d/iwlwifi.conf
echo options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo options iwlwifi nohwcrypt=1 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Thanks for supplying great data and...
Thank You for marking your thread Solved.

---

