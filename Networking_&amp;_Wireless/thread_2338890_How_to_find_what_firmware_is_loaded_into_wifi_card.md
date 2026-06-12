---
title: "How to find what firmware is loaded into wifi card"
date: 2016-10-02
forum: Networking &amp; Wireless
---

### Post by Ralph L on 2016-10-02
I am trying to install a new wifi card and having trouble making it run.  I want to check that the correct firmware is loaded.  From what I have read the firmware should be rt2860.bin, which I see in /lib/firmware.  I have tried sudo dmesg | grep rt2860, but nothing says that anything about loading firmware.  Is there any way I can know for certain what firmware was loaded into my Ralink rt3062 wifi card??

---

### Post by jeremy31 on 2016-10-02
*Thread moved to **Networking & Wireless**.*
The firmware might be revealed in ```
lshw -c net
```
If not reboot and see the wireless script link in my signature and post results

---

### Post by Ralph L on 2016-10-02
jeremy31,  Thanks for responding.
I have added 2 files with the output you requested.

---

### Post by chili555 on 2016-10-03
> ##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu [COLOR="#FF0000"]10.04.1[/COLOR] LTS
Release:	10.04
Codename:	lucid

##### kernel ############################

Linux [COLOR="#FF0000"]2.6.32[/COLOR]-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC [COLOR="#FF0000"]2010[/COLOR] i686 unknown unknown GNU/Linux
We've made a lot of progress is wireless in the last* SIX *years. I suggest that you upgrade.

---

### Post by Ralph L on 2016-10-04
Chili555:  Thanks for responding!!  Yes, I am upgrading to xubuntu 16.04.  The reason I used the very old system is because, when I did the "make" on DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 (as specified here: [https://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/](https://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/) and here [https://ubuntuforums.org/showthread.php?t=1850267](https://ubuntuforums.org/showthread.php?t=1850267)), it wouldn't compile.  I think I was missing some header files, but I haven't figured out which ones.  So I did the "make" (and "make install") on the old system and it compiled ok, but with some warnings.

However, I still haven't got the ralink 3062 card to work.  It works for a while and then disconnects.  I think the problem is that the driver is compiled into the kernel, and according to [https://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/](https://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/), it is the wrong driver.  See [http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=0f93c79404e1eaa5207f6d8a7aea14119808d382](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/commit/?id=0f93c79404e1eaa5207f6d8a7aea14119808d382) .  I think that the kernel driver is being always used in spite of the fact that I have installed a new driver module.

Do you know of any way I can be certain that the driver I install (rt3562sta.ko) is being used, and not the driver compiled into the kernel?????????

---

### Post by chili555 on 2016-10-04
Ahhh! The old 3062! We love it and hate it, however, building a circa-2010 driver isn't likely to help at all. We no longer use wooden wheels on our sleek, black BMWs.

I suggest that you run the live USB or DVD session for 16.04 and let the native driver rt2800pci load and try to connect. Check the log for clues:```
dmesg | grep rt2
```In more than a few cases, this driver starts to work well, perfectly even, when 802.11N is turned off in the router.

We'll be interested in your logs.

---

### Post by Ralph L on 2016-10-05
chili555, Thanks again for responding.
Did as you suggested. Started xubuntu 16.04 from usb stick and let it try to connect.  It connected briefly and then disconnected, never to reconnect.  Here is the result of dmesg:```
xubuntu@xubuntu:~$ dmesg | grep rt2
[   36.500037] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[   36.516848] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0008 detected
[   40.217079] rt2800pci 0000:03:03.0 wlp3s3: renamed from wlan0
[   40.840118] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   40.849332] ieee8021
```Note that my chipset is rt3062 while dmesg says it found rt3572.  However, the firmware loaded is what the various web sites on this subject say is the correct firmware.  Look forward to any other suggestions you might have.

---

### Post by chili555 on 2016-10-05
> [   36.500037] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[   36.516848] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0008 detected
[   40.217079] rt2800pci 0000:03:03.0 wlp3s3: renamed from wlan0
[   40.840118] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   40.849332] ieee8021  [COLOR="#FF0000"]...and then...??[/COLOR]It looks like there was more text. Was there? What did it say?

While booted into 16.04, what does this report?```
sudo iwlist scan
```Please omit your neighbors, etc. All we'd like to see is your own access point or router.

Is 802.11N active? Have you considered turning it off?

---

### Post by Ralph L on 2016-10-05
chili555:  Thank you for responding!!
Again I booted the system from the usb drive which is exactly what was downloaded for xubuntu 16.04.1  Again the rt3062 connected fine with a strong signal showing on the panel for a few minutes.  Gradually the signal strength decreased and finally the rt3062 dropped off line.  Here is the output of dmesg.  It was taken after the rt3062 dropped off line. ```
root@xubuntu:/media/xubuntu/Shared_Data/documents_ralph/2temp# sudo dmesg | grep rt2
[   37.476825] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3572, rev 0223 detected
[   37.493671] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0008 detected
[   41.397635] rt2800pci 0000:03:03.0 wlp3s3: renamed from wlan0
[   41.924102] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   41.943677] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[  144.464181] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  208.316195] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
root@xubuntu:/media/xubuntu/Shared_Data/documents_ralph/2temp# 
``` The output from sudo iwlist scan is included as an attachment.

You say to omit my neighbors.  Please tell me how to do that.  Do you just want me to edit the output file, or is there some way to get these programs to ignore other wifis?  Also, I tried to shut of the 802.11N capability, but I can't find any parameter to do that.  The router is a Linksys wrt 110.  Could you give me instructions on how to turn off N capability?  I also posted the output of the wireless script and wireless_script-_2.1.sh.  The output of wireless_script-_2.1.sh monitored the rt3062 disconnecting and I think I restarted network-manager and it reconnected.  There may be some information there, although I don't understand it.

---

### Post by chili555 on 2016-10-06
First, the 802.11N question; please see page 13 here: [http://downloads.linksys.com/downloads/userguide/1224638679131/WRT110-V10_UG_81201A-WEB.pdf](http://downloads.linksys.com/downloads/userguide/1224638679131/WRT110-V10_UG_81201A-WEB.pdf)> **Network Mode**
From this drop-down menu, you can
select the wireless standards running on your network. If
you have Wireless-N, Wireless-G, and Wireless-B devices in
your network, keep the default setting, Mixed. If you have
only Wireless-G and Wireless-B devices in your network,
select BG-Mixed. Please select BG-Mixed.

Assuming that your router is ESSID:"Langley", then I believe that, aside from the 802.11N issue, your settings are correct: WPA2 only and AES, also known as CCMP, only. I suggest that you change from channel 9 to channel 11 where there is less overlap.

After you address the 802.11N change and the channel, reboot the router.

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

With these changes, I suspect you will connect properly.

---

### Post by Ralph L on 2016-10-07
chili555,  Thanks again for responding.  I think we are making some progress, although I don't understand why.  First I did sudo iw reg get and found the country code to be TW (Taiwan). I changed it using sudo iw reg set US for the U.S.  However, it wouldn't let me make the change unless I disabled Networking.  Then when I re-enabled Networking the country code reverted to TW.  I then changed the last line in /etc/default/crda to REGDOMAIN=US, but it didn't help.  I rebooted and did sudo iw reg get and country code was TW.  So I never really got the country code changed.

On the router I changed Mixed to Mixed (bg).  I changed to channel 11.  I rebooted the router.  And things began to work!!! I went a good part of the day without getting disconnected.  Then I decided to try to find the exact change that made things worked.  One at a time, I changed back to auto rather setting channel 11--still worked.  I changed back to Mixed mode (bgn)--things still worked.  I changed to N mode only--things still worked, although my 802.11 g computer stopped working.  So I changed back to mixed mode (bgn) and left it.  And the country setting according to sudo iw reg get is TW.  So now with no changes made--things seem to be working.  Off course I need to test more.  It could be that tomorrow the rt3062 will be sporadically disconnecting again.  We'll see!!

I would like to find a way to make permanent the country code change.  I tried to research it on the web, but none of it made sense to me.  Do you know how to do that.  Setting REGDOMAIN=US was not enough.  This site [http://askubuntu.com/questions/464590/14-04-b43-and-de-regulatory-domain](http://askubuntu.com/questions/464590/14-04-b43-and-de-regulatory-domain) said to add COUNTRY=US to /etc/environment, so I tried that, but it didn't help.

Any help appreciated.

Edit:  I spoke too soon.  It just disconnected and won't reconnect (unless I reboot).  Maybe if we can get the correct country code in it will work.  And I am going back to channel 11 only.

---

### Post by Hadaka on 2016-10-07
Hi please see if this works for you, open a terminal then copy and paste one line at time
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
sudo sed -i '/^exit 0/ d' /etc/rc.local
echo -e "iw reg set US\nexit 0" | sudo tee -a /etc/rc.local
```
**Note: If you do NOT have a /etc/rc.local file already then please do..
```
sudo touch /etc/rc.local
echo -e "iw reg set US\nexit 0" | sudo tee -a /etc/rc.local
```
boot and then verifiy the change.
```
iw reg get
```
thanks.

---

### Post by Ralph L on 2016-10-07
Hadaka,  Thanks for responding.  I really appreciate the help I am getting!!
I tried putting "iw reg set US" into /etc/rc.local. (I had previously set /etc/default/crda to REGDOMAIN=US.)  It didn't help.  Here is the output of doing sudo iw reg get immediately after reboot, and then again after disconnecting Langley (Note: immediately after boot Langley connected) and reconnecting it (from the network manager panel icon).  ```
ralph@Lat2:~$ sudo iw reg get
[sudo] password for ralph: 
country 98: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5270 - 5330 @ 40), (N/A, 17), (0 ms), DFS
	(5490 - 5590 @ 80), (N/A, 23), (0 ms), DFS
	(5650 - 5710 @ 40), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)

Note:  I disconnected and then reconnected Langley (wifi) at this point.  Note that country code changed back to TW (Taiwan).
ralph@Lat2:~$ sudo iw reg get
country TW: DFS-JP
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5270 - 5330 @ 40), (N/A, 17), (0 ms), DFS
	(5490 - 5590 @ 80), (N/A, 30), (0 ms), DFS
	(5650 - 5710 @ 40), (N/A, 30), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
ralph@Lat2:~$ 

```Note that rc.local left the country code at 98 and DFS-UNSET.  From my experience the network must be disabled for sudo iw reg set US to work.  I think, during boot, Langley had already been connected, when rc.local ran.  Hence, the error in setting country code.  Moreover, as I said earlier in this thread, disconnecting and reconnecting the network also causes the country code to be reset to TW, so more than just setting rc.local (run only during boot) is needed to really solve this.  I think that the problem may lie in network-manager--that it resets the country code each time it is run.

Also, as I said 2 posts ago, the rt3062 has now run for fairly long hours (8 hours) without dropping.  However, when it drops, it often won't reconnect.  In fact it may drop Langley and not even sense it again and not list it in the pull down menu from the panel network icon.  And sometimes it won't sense any networks at all--even though I am surrounded by them.  Again, this looks to me like it may be a network manager problem.

I appreciate your and Chili555 efforts in helping me very much!!  Any other ideas??

---

### Post by Hadaka on 2016-10-07
Hi,the TW you are getting is because it is embedded on the EEPROM of the wifi card.
it is possible to modify that value with developer skills and tools that are beyond my
knowledge, so let's try this...Please back up the following file before making any changes.
please copy and paste to avoid typo's.
BACK-UP
```
cd /usr/share/dbus-1/system-services
sudo cp fi.epitest.hostap.WPASupplicant.service fi.epitest.hostap.WPASupplicant.service.old
##VERIFY
cat fi.epitest.hostap.WPASupplicant.service.old
```
Insert country code US
```
sudo gedit /usr/share/dbus-1/system-services
#Enter one line of code at the bottom of the list.
country=US
#save and close gedit
cd
```
Then please enter all the code from the last reply.
boot and do
```
iw reg get
```
thanks.

---

### Post by Ralph L on 2016-10-07
Hadaka,
Did as you suggested. Still didn't have country set to US.  Here is the Terminal output immediately after rebooting:```
ralph@Lat2:~$ sudo iw reg get
[sudo] password for ralph: 
country 98: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5270 - 5330 @ 40), (N/A, 17), (0 ms), DFS
	(5490 - 5590 @ 80), (N/A, 23), (0 ms), DFS
	(5650 - 5710 @ 40), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
ralph@Lat2:~$
```Here is the listing of /etc/rc.local:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

iw reg set US
exit 0
```Here is the listing of /etc/default/crda:```
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=US

```Here is the output of /usr/share/dbus-1/system-services/fi.epitest.hostap.WPASupplicant.service ```
[D-BUS Service]
Name=fi.epitest.hostap.WPASupplicant
Exec=/sbin/wpa_supplicant -u -s -O /run/wpa_supplicant
User=root
SystemdService=wpa_supplicant.service
country=US
``` Also, attempting to fix the problem where all networks disappear from nm applet list I followed the directions from [http://askubuntu.com/questions/213806/ubuntu-12-10-network-manager-not-listing-wireless-networks](http://askubuntu.com/questions/213806/ubuntu-12-10-network-manager-not-listing-wireless-networks) .  In /etc/NetworkManager/NetworkManager.conf I changed managed=false to managed=true.  Whether this helps the disappearing network list, we will see.
  Any other ideas??

---

### Post by Hadaka on 2016-10-07
Since i dont have the skills to hack the wifi eeprom and overwrite the
bits that are making it say TW, the only thing i can suggest is to replace
that "unique" wifi card of yours with an intel or something that is just plug 
and play.Sorry i dont have any other suggestions.

---

### Post by chili555 on 2016-10-08
> On the router I changed Mixed to Mixed (bg). I changed to channel 11. I rebooted the router. And things began to work!!! I went a good part of the day without getting disconnected. Then I decided to try to find the exact change that made things worked. Why not just leave it at BG-Mixed and see what happens? I am also a bit suspicious that rebooting the router seems to have had a beneficial effect. I wonder if part or all of the problem is an old router and that the wireless card and your router struggle to stay connected until, swamped with data it can't or won't use, the wireless card gives up.

Here is one more thing to try as to the country code. I agree with Hadaka; if this doesn't work and help, we really haven't any options left but to look elsewhere for tweaks and fixes.```
sudo -i
echo "options cfg80211 ieee80211_regdom=US cfg80211_disable_40mhz_24ghz=Y"  >  /etc/modprobe.d/cfg80211.conf
exit

```Reboot and check:```
sudo iw reg get
```Note to Hadaka: Yes, I put a little experiment in there!

---

### Post by Ralph L on 2016-10-10
Chili555, Hadaka:  Thank you again for responding.  Chili555, I see your suggestion and will try it soon.  However, I am about to give up on the rt3062 wifi card, and have purchased another bgn wifi card.  This one is an atheros AR5008 AR5416 card that boot up (dmesg) identifies as 1684:0023.  Again it is an older wifi card.  That is because my older computer (Dell Latitude d610) has a pci (not pci-e) slot for the wifi card.  This makes it hard to find wifi cards.  Anyway I currently have the atheros card installed in the test computer, so it will delay my trying out your latest suggestion.

And, as you may have guessed, I am having trouble installing the driver and firmware for the atheros card. As near as I can tell Xubuntu 16.04 does not have the driver and (maybe) the firmware installed so I have to install it myself.  Xubuntu 16.04 does have installed in /lib/firmware/ath9k_htc/ 2 files named htc7010-1.4.0.fw and htc9271-1.4.0.fw.  However, I don't think they are the correct firmware for my wifi card.  I think the correct driver/firmware for my card is ath9k or ath5k. I tried to install ath9k as directed here: [http://askubuntu.com/questions/708061/qualcomm-atheros-device-168c0042-rev-30-wi-fi-driver-installation](http://askubuntu.com/questions/708061/qualcomm-atheros-device-168c0042-rev-30-wi-fi-driver-installation) as answered by jeremy31. (I changed ath10 to ath9.)  I was able to wget and "make" the downloaded driver ok. (It did have a couple of warnings at the beginning).  However, when I did the sudo make install, I got this a  message similar to this repeatedly:  "At main.c:222- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175".  So I couldn't install the driver.  This thread shows the same problem and mentions that Chili555 gave them some help: [http://askubuntu.com/questions/760610/wifi-driver-installation-fails-ssl-error02001002system-libraryfopenno-such](http://askubuntu.com/questions/760610/wifi-driver-installation-fails-ssl-error02001002system-libraryfopenno-such)
 I then tried installing the firmware and on the git I got ```
ralph@Lat2:~/backports-4.4.2-1/backports-4.4.2-1$ git clone https://github.com/kvalo/ath9k-firmware.git
Cloning into 'ath9k-firmware'...
Username for 'https://github.com': 

``` Do either of you know where I can get a username/password.  Also, I would appreciate any other suggestions you might have to get the driver/firmware loaded.  Maybe there is a better way than recompiling all the drivers.

---

### Post by Hadaka on 2016-10-10
Hi, the ath5k and ath9k are already built into the kernel
so you should not have to compile them, first let's verify that your pci-id
is 1684:0023
please open a terminal and do..
```
;spci -nnk | grep -iA2 net
```
then do..
```
modinfo ath9k | grep 0023
modinfo ath5k | grep 0023
```
post the output and we will go from there...
thanks.
    * if your computer is indeed a Dell Latitude d610 there are tons of broadcom cards that will work very well in it.
you arnt going to get N speed out of that vintage machine anyway. Broadcom card 4318 and 4311 i know for a fact
will work in that computer no problem.

---

### Post by chili555 on 2016-10-10
Wow. Just wow. I'm not sure I even know where to start!!!

First, I think Hadaka means:```
lspci -nnk | grep -iA2 net
```Second, I think the device ID will turn out to be 168[COLOR="#FF0000"]c[/COLOR]:0023. Next:> As near as I can tell Xubuntu 16.04 does not have the driver and (maybe) the firmware installedBut it does:```
chili@T440p:~$ modinfo ath9k 
filename:       /lib/modules/4.4.6-040406-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F7E3AF932B15681132EA595
<snip>
alias:          pci:v0000[COLOR="#FF0000"]168C[/COLOR]d0000[COLOR="#FF0000"]0023[/COLOR]sv*sd*bc*sc*i*
alias:          platform:qca956x_wmac
alias:          platform:qca953x_wmac
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.6-040406-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)
```Also, in modinfo for this particular driver, you see no mention of firmware. Some drivers require it; some, including ath9k, do not. Compare, for an example:```
chili@T440p:~$ modinfo iwlwifi
filename:       /lib/modules/4.4.6-040406-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
[COLOR="#FF0000"]firmware: [/COLOR]      iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
<snip>
```

Next:>  (I changed ath10 to ath9.)You can't do that with any hope of success. Perhaps I can draw a parallel. Suppose you need an air filter for your Ford but all they have at the parts store is an air filter for a Chevy. Suppose the parts clerk simply takes a marker and crosses out 'Ford' and writes in 'Chevy.' Does the filter now fit??> git clone [https://github.com/kvalo/ath9k-firmware.git](https://github.com/kvalo/ath9k-firmware.git)Since your driver doesn't require any firmware, this is not needed. 

Is any driver loaded when you boot the computer?```
lsmod | grep ath
```If not, load it:```
sudo modprobe ath9k
```Any signs of life here?```
iwconfig
rfkill list all
sudo iwlist scan
```

---

### Post by Ralph L on 2016-10-10
Hadaka, Chili555,  Thank you.  Here are the outputs of the various items you asked for: ```
xubuntu@xubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Dell Latitude D610 [1028:0182]
	Kernel driver in use: tg3
--
03:03.0 Network controller [0280]: Device [1684:0023] (rev 8c)
	Subsystem: Device [0008:0000]
xubuntu@xubuntu:~$
```  ```
xubuntu@xubuntu:~$ sudo dmesg | grep 1684:0023
[    0.152017] pci 0000:03:03.0: [1684:0023] type 00 class 0x028000
xubuntu@xubuntu:~$ 

``` ```
xubuntu@xubuntu:~$ modinfo ath9k | grep 0023
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
xubuntu@xubuntu:~$ 

``````
xubuntu@xubuntu:~$ modinfo ath5k | grep 0023
xubuntu@xubuntu:~$ 

```
[/CODE] ```
xubuntu@xubuntu:~$ modinfo ath9k
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     323EDC06388A3D0920FD7FC
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv00001043sd000085F2bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00004026bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E099bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E091bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E081bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E08Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E07Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A120bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd000028A4bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd000028A2bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002813bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002F82bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000218Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000218Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002182bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000813bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000803bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000692bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00001832bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000832bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000412Abc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd00004129bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd00002005bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000682bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd000006A2bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002F8Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000218Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd000028A3bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd000028A1bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00001842bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000842bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd000006B2bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv00001A56sd00002003bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv00001A56sd00002001bc*sc*i*
alias:          pci:v0000168Cd00000030sv00001A56sd00002000bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv0000168Csd00002096bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
alias:          platform:qca956x_wmac
alias:          platform:qca953x_wmac
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)
xubuntu@xubuntu:~$ 

``` ```
xubuntu@xubuntu:~$ lsmod | grep ath
xubuntu@xubuntu:~$ 

``` ```
xubuntu@xubuntu:~$ sudo modprobe ath9k
xubuntu@xubuntu:~$ lsmod | grep ath
ath9k                 135168  0
ath9k_common           36864  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    24576  3 ath9k_common,ath9k,ath9k_hw
mac80211              659456  1 ath9k
cfg80211              499712  4 ath,ath9k_common,ath9k,mac80211
xubuntu@xubuntu:~$ 

``` ```
xubuntu@xubuntu:~$ iwconfig
lo        no wireless extensions.

enp2s0    no wireless extensions.

xubuntu@xubuntu:~$ 

``` ```
xubuntu@xubuntu:~$ rfkill list all
xubuntu@xubuntu:~$ 

``` ```
xubuntu@xubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

xubuntu@xubuntu:~$ 

``` Note that in the first and second "code boxes above" the device number 1684:0023 was found.  This site [https://wiki.debian.org/ath9k](https://wiki.debian.org/ath9k) says that ath9k supports PCI: 168C:0023 Qualcomm Atheros AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn], which (I believe) is the wifi board that I have.  I don't know how to explain the discrepancy between the "1684:0023" from lspci -nnk, and the 168C:0023 from the debian web site.  This site [http://pcidatabase.com/vendors.php?sort=id](http://pcidatabase.com/vendors.php?sort=id) is a pc-id site and it doesn't even list a 1684 manufacturer id.  Maybe the wifi card I bought is a knock off that isn't recognized by linux.

Atheros items I find in the downloaded xubuntu 16.04.1 are /lib/firmware/ath6k, ath9k_htc, and ath10k, but not ath9k which is what I think the firmware for this wifi card should be.  I don't find any "ath"stuff in /lib/modules/4.4.0-31-generic/kernel/net/wireless/, but I do see ath9k, ath9k_common, ath9k_hw, ath, when I do lsmod. I think this should run an atheros 168C:0023 card, but maybe not a 1684:0023.  I would like to take one more shot at getting the ath9k firmware loaded if you could help me with that.

---

### Post by chili555 on 2016-10-10
> 03:03.0 Network controller [0280]: Device [1684:0023] (rev 8c)
	Subsystem: Device [0008:0000]So it is, indeed, 168**4**:0023. Very interesting.

A Google search reveals nothing whatever about this device. You evidently have the only one ever built. Since there is no information whatever, I don't know how you or Hadaka or I deduce that it is an ath9k chipset or any other for that matter. To make a long story short, since there are no clues available as to its chipset, I know of no way to get it working. 

If it were me, I'd spin the big Ebay wheel and try again.

---

### Post by Ralph L on 2016-10-10
I have found some additional 802.11 bgn mini-pci cards.  They are:
1.  Broadcom 4322AGN BCM94322MC BCM4322 N Dual Band Wireless Mini Pci MINIPCI Card.  Broadcom is kind of nuisance, because I have to use fwcutter to get the firmware.
2.  Atheros AR5008 AR5416 Mini PCI N 802.11N 300M WIFI Wireless Card For Dell.  Same card I thought I was buying, but from different vendor--still from china.
3.  300M 802.11 a/b/g/n Atheros AR9223 Mini PCI WIFI WLAN Card for Acer Toshiba Dell.  This one has a "larger" model number so I presume its newer.  Uses the merlin architecture??? Delivered from New York.  Sounds like the best one to me.  What do you think?

Do either of you know if any of these, particularly No. 3, would be a problem to install  in xubuntu 16.04??  Or do you know of any other problems that I would have with one of them?

On another issue:  Should I change the title of this thread to "Trying to install wifi N mini pci card in Dell D610 running xubuntu 16.04"?  The current title is somewhat misleading.

---

### Post by chili555 on 2016-10-10
> Do either of you know if any of these, particularly No. 3, would be a problem to install in xubuntu 16.04?? The latter seems like the best bet to me. It is evidently also an ath9k device.

If the Broadcom is indeed this, then installation is easy and trivial: [https://wikidevi.com/wiki/Broadcom_BCM94322MC](https://wikidevi.com/wiki/Broadcom_BCM94322MC)> BCM94322MC - [COLOR="#FF0000"]14e4:432b[/COLOR] 802.11abgn 2T2RNo fwcutter needed.

[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Ralph L on 2016-10-30
Thanks again to everybody that helped me on this.  I really appreciate it!!

1.  I seem to have gotten my problem at least 98% solved.  I gave up on the Realtec RT3062 (loses connection too often) and AR5008 802.11(a)bgn (unrecognized device id 1684:0023)  wifi cards, and bought a  "300M 802.11 a/b/g/n Atheros AR9223 Mini PCI WIFI WLAN Card for Acer Toshiba Dell".  This card seems to be working right out of the box on Xubuntu 16.04 without any need to install drivers or firmware.  Apparently the necessary drivers and firmware are already in the 16.04 system.
2.  Because of the problem of network-manager seeming to lose the wifi list under the panel icon, when the wifi loses connection, I upgraded my xubuntu 16.04 with the latest update.  So far I haven't had a problem with xubuntu 16.04 (latest update) losing the list.
3.  Having the a/b/g/n card rather the the a/b/g network card has sped up my wifi from about 12 mbps to about 22 mbps download.  So I am happy with my wifi speed now.  I know an a/b/g wifi card is supposed to run at over 50 mbps, but I could never get mine to do so.

Thanks again!!!

---

