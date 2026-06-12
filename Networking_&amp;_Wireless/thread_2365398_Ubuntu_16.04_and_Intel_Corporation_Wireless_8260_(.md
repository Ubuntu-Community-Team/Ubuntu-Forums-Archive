---
title: "Ubuntu 16.04 and Intel Corporation Wireless 8260 (rev 3a): deconection issue"
date: 2017-07-06
forum: Networking &amp; Wireless
---

### Post by doisyg on 2017-07-06
Hi all,
I am struggling with wireless reliability on  Ubuntu 16.04 with Intel Corporation Wireless 8260 (rev 3a) wifi card from a Intel NUC  

 The problem: I get randomly disconnected from the wifi network and the computer is not reconnecting by itself. I have to disable/re-enable wifi in the network manager to be able to reconnect. Note that if I force a disconnection by switching off and on the APs, the computer reconnects normaly.

 Wifi infrastructure: Several APs (professional and high end Fortinet FortiWifi) with the same SSID that provide a transparent and unified network.
 
 I disabled wifi N, power management and IPv6 and it still happens (once every 2 to 3 days). After changing the AP wifi configuration from hidden SSID to regular SSID, it happens much less frequently (about once every 3 weeks), which make it really hard to reproduce.
 What can I do to make sure that the computer will reconnect by itself? I started thinking about a script that will disable and re-enable the wifi card in case of a loss of conenctivity.
 Below is a pastebin of the wireless-info script.  
 
 [https://paste.ubuntu.com/25032012/](https://paste.ubuntu.com/25032012/)
 
 You can see a disconnection:
 
 ```

[2474443.420276] wlp1s0: disassociated from <MAC 'ZebraboxRobot' [AC1]> (Reason: 8)
[2474458.876848] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
 
```
 
 followed by a manual reconnection (by disabling and re-enabling the wifi).

---

### Post by chili555 on 2017-07-06
We see, as we expected we would, that Network Manager roams from among all the instances of ZebraboxRobot looking for a better connection.

> [2509387.285037] wlp1s0: associate with <MAC 'ZebraboxRobot' [[COLOR="#FF0000"]AC17[/COLOR]]> (try 1/3)
[2509387.286688] wlp1s0: RX AssocResp from <MAC 'ZebraboxRobot' [AC17]> (capab=0x411 status=27 aid=33)
[2509387.286696] wlp1s0: <MAC 'ZebraboxRobot' [AC17]> denied association (code=27)
[2509387.506897] wlp1s0: authenticate with <MAC 'ZebraboxRobot' [AC1]>
[2509387.517272] wlp1s0: send auth to <MAC 'ZebraboxRobot' [AC1]> (try 1/3)
[2509387.524600] wlp1s0: authenticated
[2509387.529040] wlp1s0: associate with <MAC 'ZebraboxRobot' [[COLOR="#FF0000"]AC1[/COLOR]]> (try 1/3)
[2509387.533630] wlp1s0: RX AssocResp from <MAC 'ZebraboxRobot' [AC1]> (capab=0x431 status=0 aid=1)
[2509387.543501] wlp1s0: associated
[2509387.543598] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes readyYou might try binding NM to the strongest by referencing its MAC address: [https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by doisyg on 2017-07-07
Thanks for your answer.
Actually, the series of event you quoted correspond to a manual disable/re-enable of the wifi (from time [2509387.285037]). No problem from there. I don't know exactly what's going on, but in less than 30ms, we have a connection.
The problem comes from the earlier series of event:

```

[2474443.420276] wlp1s0: disassociated from <MAC 'ZebraboxRobot' [AC1]> (Reason: 8)
[2474458.876848] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)

```

How come the network manager cannot reconnect by itself for hours and I have to disable/re-enable it to regain connectivity?

Selecting only one AP is not a solution. This computer is embedded in a moving robot and has to switch from one AP to another when it moves. We never had an issue when it moves around. The problem logged above happened in the middle of the night, when the computer was completely static and with no other wifi client around.

---

### Post by BenginM on 2017-07-07
Reason Code 8 is due to client leaving the BSS by means of AP moving the client to another access point using non-aggressive load balance.

##

are you connected to a 2.4 or 5 GHz band! is it connected to a specific channel or is it set to auto!


[RIGHT]
[/RIGHT]
which kernel version are you running! $ uname -a

what's the output of : [B]dmesg | grep iwlwifi
[/B]
and what's in: $ ls -l /lib/firmware/iwlwifi-8000C*

also, run apt-cache policy [B]linux-firmware

i won't be surpries if this is an Intel [/B]microcode frimware issue ! considering that the wireless chip in question is still quite modern.

##

The 8260 card uses the **iwlwifi** kernel module, and the microcode for that is stored in **/lib/firmware**. The iwlwifi module is part of the &#8216;linux-firmware&#8217; package.
Specifically, you&#8217;re looking for the files: **iwlwifi-8000C-***SOME_NUMBER***.ucode**. The kernel seems to pick the highest number in the 8000C range , if the one in use is broken, you can rename it and let the kernel pick another one!

---

### Post by Hadaka on 2017-07-07
Hi, from your diagnostic report from
[https://paste.ubuntu.com/25032012/](https://paste.ubuntu.com/25032012/) shows several ZebraboxRobot AP's
 
```
CONNECTIONS.AVAILABLE-CONNECTION-PATHS:  

ZebraboxRobot   <MAC 'ZebraboxRobot' [AC17]>  Infra  40    5200 MHz  54 Mbit/s  95      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
ZebraboxRobot   <MAC 'ZebraboxRobot' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  78      &#9602;&#9604;&#9606;_  WPA2       yes     * 
ZebraboxRobot   <MAC 'ZebraboxRobot' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
ZebraboxRobot   <MAC 'ZebraboxRobot' [AC13]>  Infra  36    5180 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no 
```

The 'ZebraboxRobot' [AC17] 5200 MHz and the 'ZebraboxRobot' [AC1] 2437 MHz appear to be your router
Your wifi card is seeing a stronger signal at ZebraboxRobot' [AC17] 5200 MHz 95 <- SIGNAL STRENGTH 
and is leaving ZebraboxRobot' [AC1] 78 <- SIGNAL STRENGTH.
*Edit the wifi connection configuration settings and un-check "Connect Automaticlly"
*If you only have ONE access point to ZebraboxRobot, please follow Dr. chili555's post. #2
*If you have access to the routers configuration, please change your 5200 MHz ssid to ZebraboxRobot-5G

```
  ##### dmesg #############################
[2474443.420276] wlp1s0: disassociated from <MAC 'ZebraboxRobot' [AC1]> (Reason: 8)
[2509387.265316] wlp1s0: authenticate with <MAC 'ZebraboxRobot' [AC17]>
[2509387.273211] wlp1s0: send auth to <MAC 'ZebraboxRobot' [AC17]> (try 1/3)
[2509387.285037] wlp1s0: associate with <MAC 'ZebraboxRobot' [AC17]> (try 1/3)
[2509387.286688] wlp1s0: RX AssocResp from <MAC 'ZebraboxRobot' [AC17]> (capab=0x411 status=27 aid=33)
[2509387.286696] wlp1s0: <MAC 'ZebraboxRobot' [AC17]> denied association (code=27)
[2509387.506897] wlp1s0: authenticate with <MAC 'ZebraboxRobot' [AC1]>
[2509387.517272] wlp1s0: send auth to <MAC 'ZebraboxRobot' [AC1]> (try 1/3)
[2509387.529040] wlp1s0: associate with <MAC 'ZebraboxRobot' [AC1]> (try 1/3)
[2509387.533630] wlp1s0: RX AssocResp from <MAC 'ZebraboxRobot' [AC1]> (capab=0x431 status=0 aid=1)
```

Let's see if this helps the prolem..please COPY and paste..

```
echo 'options iwlwifi 11n_disable=8' | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
*To restore to original configuration...
```
sudo rm -rf  /etc/modprobe.d/iwlwifi.conf
```

 This will also cause drops and disconnects..
```
##### iw reg get ########################
Region: Europe/Paris (based on set time zone)
country 00: DFS-UNSET
```  
To correcrt please COPY and paste...
```
sudo iw reg set FR
sudo sed -i 's/=.*/=FR/' /etc/default/crda
```

remove any hardwired connection, boot and test wireless.
Thanks

---

### Post by doisyg on 2017-07-10
Thanks all for your help.
 Replying to Sary.sa first:
 
 > are you connected to a 2.4 or 5 GHz band! is it connected to a specific channel or is it set to auto!
 The 5Ghz band is disabled (11n_disable=1). And the channel is set to auto.
 
 > which kernel version are you running! $ uname -a
 Linux k****-nuc 4.4.0-78-generic #99-Ubuntu SMP Thu Apr 27 15:29:09 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
 
> what's the output of : **dmesg | grep iwlwifi**
 [https://paste.ubuntu.com/25059885/](https://paste.ubuntu.com/25059885/)
 The first lines are very interesting:
 [    5.319001] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8000C-19.ucode failed with error -2
```
[    5.319517] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8000C-18.ucode failed with error -2
[    5.319683] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8000C-17.ucode failed with error -2
[    5.338114] iwlwifi 0000:01:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    5.371645] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208 
```
So there is a problem with the firmware in use?
 
> and what's in: $ ls -l /lib/firmware/iwlwifi-8000C*
 ```
-rw-r--r-- 1 root root 1745176 Dec  1  2016 /lib/firmware/iwlwifi-8000C-13.ucode
 -rw-r--r-- 1 root root 2351636 Dec  1  2016 /lib/firmware/iwlwifi-8000C-16.ucode
 -rw-r--r-- 1 root root 2394060 Dec  9  2016 /lib/firmware/iwlwifi-8000C-21.ucode
 
```
 
 > also, run apt-cache policy **linux-firmware**
  ```
linux-firmware:
    Installed: 1.157.8
    Candidate: 1.157.11
    Version table:
       1.157.11 500
          500 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
          500 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages
   *** 1.157.8 500
          500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
          500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages
          100 /var/lib/dpkg/status
       1.157 500
          500 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
          500 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) xenial/main i386 Packages
```

---

### Post by doisyg on 2017-07-10
Now Hadaka:
  
 
 >  Let's see if this helps the prolem..please COPY and paste..

  
 
 echo 'options iwlwifi 11n_disable=8' | sudo tee -a /etc/modprobe.d/iwlwifi.conf I already had set 11n_disable=1 to disable the 5Ghz, but maybe that was not enough. Now I realize that if it tried to connect to [AC17], it means that it was not really disabled.
 I am going to set  11n_disable=8 and the regional setting and will keep you posted. But it can takes time before a disconnection appears.
 Thanks!

---

### Post by BenginM on 2017-07-10
[QUOTE=doisyg;13664368] Thanks all for your help.
 Replying to Sary.sa first:
 
 
 The 5Ghz band is disabled (11n_disable=1). And the channel is set to auto.
 
[COLOR=#ff0000][FONT=courier new][FONT=arial]OK! to keep things right from your part .. I strongly suggest you change your router's security to pure WPA2-PSK with AES (CCMP). No WEP, no WPA/WPA2 mixed mode, and no TKIP. Reboot the router after saving the change.[/FONT]
[/FONT][/COLOR]
 
 Linux k****-nuc 4.4.0-78-generic #99-Ubuntu SMP Thu Apr 27 15:29:09 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
 

 [https://paste.ubuntu.com/25059885/](https://paste.ubuntu.com/25059885/)
 The first lines are very interesting:
 [    5.319001] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8000C-19.ucode failed with error -2
```
[    5.319517] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8000C-18.ucode failed with error -2
[    5.319683] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8000C-17.ucode failed with error -2
[    5.338114] iwlwifi 0000:01:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    5.371645] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208 
```
So there is a problem with the firmware in use?
 
[FONT=arial][COLOR=#FF0000]Those first three lines means the files don't exist... which is fine! but the kernel 4.4 is loading the Intel firmware 16 "iwlwifi-8000C-16.ucode" .  here is a bug report with a similar issue:
##[/COLOR][/FONT] 
[https://bugzilla.kernel.org/show_bug.cgi?id=117391](https://bugzilla.kernel.org/show_bug.cgi?id=117391)
[FONT=arial]
[COLOR=#FF0000]IF you look in:[/COLOR][/FONT]
[https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release)

[FONT=arial][COLOR=#FF0000]Core13 16.ucode hit end of life ... even thought Core18  21.ucode have the same status and it's the highest in your /lib/frimware , i would try to let the kerenl pick it up .. to switch to 21.ucode rename 16 as follow :
[/COLOR][/FONT]
```
 sudo mv /lib/firmware/iwlwifi-8000C-22.ucode /lib/firmware/iwlwifi-8000C-16.ucode.BORKEN 
```
[TABLE="class: inline"]
[TR="class: row12"]
[TD="class: col0 leftalign"][/TD]
[TD="class: col2 leftalign"][/TD]
[TD="class: col3 leftalign"][FONT=arial][COLOR=#FF0000]Reboot and run dmesg | grep iwl .. to see if the 21.ucode Intel frimware is loadded , if so run:
[/COLOR][/FONT]```
[B] 
tail -f /var/log/syslog

tail -f /var/log/dmesg [/B]
```[FONT=arial][COLOR=#FF0000]in two separated terminal windows to catch logs when it disconnect and then test the wifi stabablity for a week or so. if the Intel frimware 21.ucode gives you the same issue .. the best thing to do then is to upgrade the kernel to 4.10 with an updated linux-frimware version which should give you the maintained 27.ucode .

## for future reference, to upgrade/install a kernel:

First update the system:
[/COLOR][/FONT]```
[B][COLOR=#ff0000][FONT=courier new]
[/FONT][/COLOR][/B]sudo apt update && sudo apt dist-upgrade
```

[COLOR=#ff0000]you can install a new kernel manually. currently linux kernel 4.10 is available in the repo. [/COLOR][COLOR=#ff0000]You could always do the following in terminal run:
[/COLOR]
[COLOR=#000000]apt-cache search linux-image[/COLOR][COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]Pick the one you want and then do:
[/COLOR]
[COLOR=#000000]sudo apt-get install linux-image-your_version_choice
[/COLOR]
[COLOR=#ff0000]and
[/COLOR][COLOR=#000000]
sudo apt-get install linux-image-extra-your_version_choice[/COLOR][COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]
[/COLOR][COLOR=#ff0000]#See:[/COLOR]
 [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
 [URL="http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/"]http://kernel.ubuntu.com/~kernel-ppa/mainline/

[/URL]

  [COLOR=#ff0000]## Or use Ukuu:[/COLOR]

[http://www.noobslab.com/2017/04/ukuu-kernel-manager-utility-lets-you.html](http://www.noobslab.com/2017/04/ukuu-kernel-manager-utility-lets-you.html)

[COLOR=#ff0000]## always keep at least two previous working kernels , and remove the ones you don't need so the the /boot direcory won't be full! to remove kernels safely use Ukuu or  #See:[/COLOR]

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)
[/TD]
[/TR]
[/TABLE]

---

### Post by doisyg on 2017-07-11
So, I updated the kernel to 4.8 as it is officially supported for ubuntu 16.04 by using the following command:
```
sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04
```

The firmware loaded is now version 21.302800.0 (instead of [FONT=arial]16.242414.0):
[/FONT]

[HTML][    4.114243] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8000C-24.ucode failed with error -2
[    4.114263] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8000C-23.ucode failed with error -2
[    4.115396] iwlwifi 0000:01:00.0: Direct firmware load for iwlwifi-8000C-22.ucode failed with error -2
[    4.152002] iwlwifi 0000:01:00.0: loaded firmware version 21.302800.0 op_mode iwlmvm
[    4.214670] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[    4.216489] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    4.217420] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    4.375137] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    7.068821] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.069183] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.200013] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled
[    7.200676] iwlwifi 0000:01:00.0: L1 Enabled - LTR Enabled[/HTML]

Then, I tried to install the latest stable version of backport-iwlwifi as described here: [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release) but i get a "iwlwifi no suitable firmware found" error.
So I am going to test the stability with the firmware 21.302800.0, the kernel 4.8 on ubuntu 16.04 for the next weeks.
Thanks all for the help.

---

### Post by chili555 on 2017-07-11
Here is how you can get -22, -23 and -24. As well, this poster reports improvement when -22 loads. > iwlwifi 0000:03:00.0: loaded firmware version[COLOR="#FF0000"] 22[/COLOR].361476.0 And also:> Huge improvement so far

[https://askubuntu.com/questions/933237/slow-intermittent-wifi-on-ubuntu-16-04-intel-nuc-are-my-drivers-up-to-date/933254#933254](https://askubuntu.com/questions/933237/slow-intermittent-wifi-on-ubuntu-16-04-intel-nuc-are-my-drivers-up-to-date/933254#933254)

---

### Post by doisyg on 2017-07-13
Ok, so with the kernel 4.8 (and the iwlwifi version that comes along), I can get the firmware 22 to load by downloading it to /lib/firmware:
```
cd /lib/firmware
sudo wget https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8000C-22.ucode
```
But not above, because the iwlwifi version that comes with the kernel 4.8 doesn't accept it (and it is a bad idea to rename a newer one to force it, i tried and i could not boot properly):
From [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi/core_release)
[HTML]The fact that Intel published a backport tree for its WLAN drivers  doesn't impact its commitment to upstream all the code to the mainline  kernel. It simply allows users who can't choose their kernel to work  with a more recent driver. The backport tree allows us to provide a  combo of the driver / firmware that has been fully validated. For a  simple reason of capacity, we cannot test as thoroughly all the kernel  versions / firmwares / devices matrix. There is code in the backport  tree that is not in the mainline kernel, but this is transient.[/HTML]

So I downloaded, compiled and installed the last maintained version of backport-iwlwifi, but I had to download before the latest firmware otherwise the driver won't find a compatible one. Here is a script that I wrote that worked for me:
```
#!/bin/bash
# Wifi update
echo Upgrading Wifi firmware and driver
cd /lib/firmware
sudo wget https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8000C-31.ucode
cd ~/
git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git -b release/LinuxCore28
cd backport-iwlwifi
make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4
sudo make install
echo firmware downloaded and driver updated, please reboot
exit 0

```

And now the firmware version, 31.532993.0 loads properly!

 ```
dmesg | grep iwlwifi
[    2.797533] Loading modules backported from iwlwifi
[    2.797534] iwlwifi-stack-public:release/LinuxCore28:6182:f34e8897
[    2.854088] iwlwifi 0000:02:00.0: Direct firmware load for iwl-dbg-cfg.ini failed with error -2
[    2.869082] iwlwifi 0000:02:00.0: capa flags index 3 larger than supported by driver
[    2.869544] iwlwifi 0000:02:00.0: loaded firmware version 31.532993.0 op_mode iwlmvm
[    2.885206] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
```

---

### Post by doisyg on 2017-07-23
So after more that one week without issue, the connection droped and so far, after 24h, did not automatically reconnect.
The only two suggestions that I did not try are:
[LIST]
[*]Setting the country code. Can't manage to make the change, I still get the 00 country code
[*]Changing the router configuration as I don't own it and it is very complicated to push a change. But could be possible if there is a strong rational.
[/LIST]

So I am returning to the idea of writing a script that will detect a drop of connection and force a disable/re-enable of the wifi card. Any suggestions on how to do that?

---

### Post by KayoLango on 2017-11-28
Thanks for the post. I have the same problem. 
I created a 1 line script with "sudo ifconfig wlp4s0 up; sudo service network-manager restart", that works for me. I just restart it when it doesn't wake up - don't care enough to add if-else around it (partially because I sometimes disable WLAN in hardware and don't want it up while other times I don't want WiFi because I prefer to use LAN if I can).

---

