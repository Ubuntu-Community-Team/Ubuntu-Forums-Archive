---
title: "usb wireless adapter (days of trying!)"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by burntt999 on 2011-05-03
ok i've been trying to work on this and not ask for help for almost a week now for hours a day. but this is getting very aggravating. 

installed the rt3070/2870 from website like instructions call forand I finallly got linux to notice the wireless usb netword adaptor(ra0).  when i do ifconfig ra0 up the light starts blinking faster like its going all good but it doesnt find any networks.. if i turned on my other laptop running win7 i would see about 15 networks around.  PLEEEEASE help..

i know i'm gonna have to throw up some info.. when i copy info from my terminal to here what do i type around the info to put the terminal text in its own window??

---

### Post by burntt999 on 2011-05-03
well i'm reinstalling ubuntu now.  i figure as much time as i've spent working on this i've had to have got side tracked somewhere and must have dont something incorrectly..... starting fresh...   if anyone would like to try and help that would be cool. :confused:  i'm sure its something small i'm over looking..

---

### Post by mapes12 on 2011-05-03
Have you tried this:-

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by RobertVarga on 2011-05-03
Hello,
 block rt2800usb ... 
Code:
echo 'blacklist rt2800usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
[U]restart, and try this
Code:
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "0df6 0040" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
sudo iwlist scan
(the first Line allocate the Chipset-ID to the driver rt2870sta)

 If the solution works, activiate it automatically by a new udev-Rule
Code:
sudo gedit /etc/udev/rules.d/10-wlan.rules
Insert the following code and save the file
Code:
# UDEV-Rule for Sitecom WL-344 ID 0df6:0040
SUBSYSTEM=="usb", SYSFS{idVendor}=="0df6", SYSFS{idProduct}=="0040", RUN+="/sbin/modprobe rt2870sta"
Activate it (or restart)
Code:
sudo service udev reload

---

### Post by burntt999 on 2011-05-03
update!!  i can now scan for networks!! but cant connect..  when i get home from work (omw) i'll read ya'll advice and see what i can come up with... i'll be writing back within 2 hours..  (gotta stop by the store for some COLA!!! i'm GOING to get this tonight)

---

### Post by burntt999 on 2011-05-03
> **mapes12 said:**
> Have you tried this:-

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)


i'm reading this now.  which i would've know about this a long time ago lol..

 ok so network manager in the system tray doesnt see the usb wireless modem.  it did see the pci wireless modem in the netbook so i turned it off in the bios.   i open network tools and unknown advice (ra0) under interface information - all info looks good..  theres a hardware address, multicast = enabled, state = active.  and also there is an ip address by IPv6.

strange tho... the light on the usb device isnt flickering like it was..  its just a solid ON light.  ??

i downloaded wicd and tried to connect to my work wireless network and it kept saying bad password.  at home did the same thing...  so now this is what i'm facing..  

so i'll be reading the above till i stumble upon something or i get a reply..

---

### Post by burntt999 on 2011-05-03
truly hope someone helps me with this.  uninstalled network manager.. using wifi radar right now..  it just stays at "Acquiring IP Address (DHCP)"  wont move on...   finds the networks thos..  still happy about this =D   maybe i'll figure this out and get more than 3 hours of sleep tonight ! =)   probably not lol  BUUUUMP

---

### Post by burntt999 on 2011-05-04
glad i asked for help

---

### Post by burntt999 on 2011-05-04
and now i know i can connect to my router if i turn the encryption off... so... guess i'll figure out whatever this means soon....  if anyone wants to chime in dont let me hold you back

---

### Post by burntt999 on 2011-05-04
so i'm using wicd and i turned over to the wlan1 my onboard pci wifi and connected.  switched back to ra0 (usb wifi i'm trying to use) and it says Bad Password.  I didnt change ANY settings except interface used.... so.. if anyone passing by knows how to fix this please leave a comment..

---

### Post by corncob on 2011-05-04
I have no experience with this but do notice if you google rt3070/2870 there are a ton of links including ones to threads in this forum.

---

### Post by wep940 on 2011-05-04
What type of encryption?  Some drivers don't support WPA2, some need some config files set up.
 
lsusb -> post the output back here

---

### Post by burntt999 on 2011-05-04
> **corncob said:**
> I have no experience with this but do notice if you google rt3070/2870 there are a ton of links including ones to threads in this forum.

yea definitely  with the TON of people having problems and my lack of knowledge (but steady growing) of linux i've been at this for days and days trying to set this up..

---

### Post by burntt999 on 2011-05-04
> **wep940 said:**
> What type of encryption?  Some drivers don't support WPA2, some need some config files set up.
 
lsusb -> post the output back here


the encryption is WPA2

hyper@hyperhell:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 001 Device 004: ID 13d3:5702 IMC Networks 
Bus 001 Device 002: ID 111d:0000  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by burntt999 on 2011-05-05
and also:

root@hyperhell:/home/hyper# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

root@hyperhell:/home/hyper# dmesg | grep -e rt2 -e rt3
[11987.978344] rtusb init rt2870 --->
[11987.987124] usbcore: registered new interface driver rt2870
root@hyperhell:/home/hyper#

---

### Post by burntt999 on 2011-05-05
and just in case: 

root@hyperhell:/home/hyper# lsmod | grep -e rt2 -e rt3
rt3070sta             564155  1

---

### Post by burntt999 on 2011-05-05
root@hyperhell:/home/hyper# cat /etc/network/interfaces
auto lo
iface lo inet loopback

????? anything anyone   ???????

---

### Post by wep940 on 2011-05-05
It's okay to post if you are adding information, but please remember this is an all-volunteer forum so it may take more than just a few hours or few days to get your problem solved.
 
This is just one of MANY threads about getting this chipset working, according to the usb manufacturer and device id - your case 148f:2070, which comes back as the RaLink 2070. I have this same chipset in my EDIT: Tenda (not my current Trendnet)- USB wireless G adapter (it was extremely cheap). This is an old and I'm sure outdated by now thread, but it gives an example of what can be found on the net.
 
[http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828)
 
For 10.04, 10.10 and 11.04 mine has installed fine by default. However, if you are having problems, I would suggest: 
 

[LIST]
[*]checking the net for threads for your adapter via a Google/Yahoo/Bing whatever search with ubuntu+11.04+148f:2070+driver in the search string
[*]check the following bug report on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765606](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765606)
[*]when you think you may have found the valid solution, be sure to ask more questions here.
[*]be prepared to re-install, so that everything is working from a "clean slate". The biggest problem people run into when messing with the drivers is that they do something, it doesn' work, the don't back it out, then they try something else. It just compounds problems.
[/LIST]Be sure you are looking at posts for the 2070 chipset.

---

### Post by burntt999 on 2011-05-05
yeah... sure was cheap lol.. 

thank u thanku thank u for the info.. i'll be reading up on all this and get back with ya =D

---

### Post by burntt999 on 2011-05-05
ok ok few questions::

> **wep940 said:**
>  This is an old and I'm sure outdated by now thread, but it gives an example of what can be found on the net.

[http://ubuntuforums.org/showthread.php?t=1285828](http://ubuntuforums.org/showthread.php?t=1285828) 

whoa! so this is actually the first thread i used to try to install the drive.  it didnt work for me tho.. BUT he uses a rt3070sta driver and what actually ended up working all the way to the point i'm at now is an updated 2011 rt3070sta driver from the ralink support page. 

> **wep940 said:**
> 
For 10.04, 10.10 and 11.04 mine has installed fine by default.  However, if you are having problems, I would suggest: 
the above link got your usb wifi working fine?  hmm... wonder if i did something wrong.. i AM on 10.10. that means it should've worked for me right?

> **wep940 said:**
> checking the net for threads for your adapter via a Google/Yahoo/Bing whatever search with ubuntu+11.04+148f:2070+driver in the search string
I keep the "+" signs in the search statement???

> **wep940 said:**
> 
be prepared to re-install, so that everything is working from a "clean slate".  The biggest problem people run into when messing with the drivers is that they do something, it doesn' work, the don't back it out, then they try something else.  It just compounds problems.Be sure you are looking at posts for the 2070 chipset. 

Oh yeah.. i'm on my 3rd install lol

---

### Post by wep940 on 2011-05-05
Mine just worked by default in 11.04 - can't remember for sure for 10.x. you do need to keep the "+"'s in the search string - it tells the engine it the result must include all the strings.
 
EDIT:  My Trendnet worked out of the box - forgot that the Tenda adapter was the one that had this chipset - I modified my other post to reflect that as well.

---

### Post by burntt999 on 2011-05-05
ok cool cool

---

### Post by wep940 on 2011-05-05
Towards the end of this link are instructions, a little cryptic, on getting this working in 10.10.   One thing I have noticed in all of these threads is that you have to modify a file to change WPA from no to yes, then recompile the driver.
 
Since you seem to have the driver working - you can see networks - but your WPA apparently isn't - you can't get your password accepted - I would assume you are having the WPA problem.
 
If possible, temporarily reset your router to no encryption and see if you can connect.  If so, temporarily set it to WEP and see if you can connect.  If so, set it to WPA and see if you can connect (right now I think it will fail at this step).  If it fails at this step, please post back with that and we'll go from there.

---

### Post by burntt999 on 2011-05-08
ok so since distros arent really a big deal with the machine i'm trying to get this to work on.. i installed 11.04 just to see if it would work.. i JUST got this done (had quite alot of hickups trying to reinstall the OS.)  plus i just installed ubuntu on my main desktop and i was configuring it so i had a little break from the modem but its time to get this thing working.

i'm going over to the 11.04 on my net book now to try a few things..  i have taking off encryption on my router and i could connect.. i didn't however put WEP on... i'll try that in a moment and get back with ya

---

### Post by burntt999 on 2011-05-08
well i'm on the wireless usb router now...  what i did... nothing....     i just installed 11.04 and then everyhthing worked.  sheesh..  thank ya for all the help!!!

---

