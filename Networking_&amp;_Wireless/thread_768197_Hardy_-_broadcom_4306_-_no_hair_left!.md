---
title: "Hardy - broadcom 4306 - no hair left!"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by goslings on 2008-04-26
upgraded from 7.1 to 8.04 - now wireless does not function
Device manager says BSM4306 is there
00:0e.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
wireless just loops round asking for wireless key - which i know is ok
but hardware drivers does not list bcm43xx just NVIDIA
utterly confused as I was in 7.10 - which I did get work (maybe fluke)
any help much appreciated 
thanks

---

### Post by kai60 on 2008-04-26
Try this

[http://ubuntuforums.org/showthread.php?p=4798063#post4798063](http://ubuntuforums.org/showthread.php?p=4798063#post4798063)

---

### Post by Mad_Gouki on 2008-04-26
I just got it working in Hardy for my bcm4311 by plugging my laptop into my network via ethernet and going to the package manager.

at the top click system>administration>synaptic package manager
then update the repositories(click reload), and look for b43-fwcutter

when it opens up the window, click on the button the download and extract the firmware, and then click next or finish (i forget what the button says)

after that, it will do some stuff in the terminal and then your card should be working.

Also, it did not show up in the hardware manager for me(formerly the restricted drivers manager) either, but it did in Gutsy.
Hope this helps!

---

### Post by goslings on 2008-04-26
> **kai60 said:**
> Try this

[http://ubuntuforums.org/showthread.php?p=4798063#post4798063](http://ubuntuforums.org/showthread.php?p=4798063#post4798063)

Not really sure I understand the italic part of this line  
root@ubulap:/*home/denarced/Desktop/tar/kmod# b43-fwcutter* -w /lib/firmware/2.6.24-16-generic wl_apsta.o 

thanks

---

### Post by kai60 on 2008-04-26
Sorry mate,

[http://ubuntuforums.org/showpost.php?p=4797697&postcount=2](http://ubuntuforums.org/showpost.php?p=4797697&postcount=2)

this is the link to what worked for me. Let me know how you go and I'll see if I can help any further.

Good luck!

---

### Post by goslings on 2008-04-26
> **kai60 said:**
> Sorry mate,

[http://ubuntuforums.org/showpost.php?p=4797697&postcount=2](http://ubuntuforums.org/showpost.php?p=4797697&postcount=2)

this is the link to what worked for me. Let me know how you go and I'll see if I can help any further.

Good luck!

Thanks -  I have already tried this but still no joy 
when I look at hardware drivers after the reboot it just lists my NVIDA and no sign of bcm43xx
ian@goslinux:~$ lspci | grep Broadcom\ Corporation
00:0e.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

thanks again

---

### Post by sridenour on 2008-04-26
> **goslings said:**
> Thanks -  I have already tried this but still no joy 
when I look at hardware drivers after the reboot it just lists my NVIDA and no sign of bcm43xx
ian@goslinux:~$ lspci | grep Broadcom\ Corporation
00:0e.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

thanks again
I would look at this.
[http://ubuntuforums.org/showpost.php?p=4793983&postcount=1](http://ubuntuforums.org/showpost.php?p=4793983&postcount=1)

I figured r all the hoops and rings of fire I jumped through to loose the card after every reboot (like you seem to be doing), that anything as simple as what was written there wouldn't work. Yet it did and the card shows up after several reboots.

---

### Post by kai60 on 2008-04-26
Alright, that is absolutely no problem. I had the same issue and for some reason the restricted driver manager isn't handling the broadcom chipset well this time around.

Can you check to make sure that you have the b43 directory somewhere in your /lib/firmware folder, if you do, then you have to check that you have several ucode*.fw. If you have these then you should be set.

Just reboot and check to make sure that you are not getting any errors that are network related, such as "couldn't find /b43/ucode5.fw". No errors? Great.

Then go to your nm-applet and select the network of your choice and configure it.

Good luck and let me know how you go...

---

### Post by goslings on 2008-04-26
> **kai60 said:**
> 
Good luck and let me know how you go...

have to dash will be trying in an hour or so 
thanks

---

### Post by goslings on 2008-04-26
> **kai60 said:**
> Alright, that is absolutely no problem. I had the same issue and for some reason the restricted driver manager isn't handling the broadcom chipset well this time around.

Can you check to make sure that you have the b43 directory somewhere in your /lib/firmware folder, if you do, then you have to check that you have several ucode*.fw. If you have these then you should be set.

Just reboot and check to make sure that you are not getting any errors that are network related, such as "couldn't find /b43/ucode5.fw". No errors? Great.

Then go to your nm-applet and select the network of your choice and configure it.

Good luck and let me know how you go...

ian@goslinux:/lib/firmware/b43$ ls -la
total 176
drwxr-xr-x 2 root root  4096 2008-04-26 09:12 .
drwxr-xr-x 6 root root  4096 2008-04-26 09:12 ..
-rw-r--r-- 1 root root    18 2008-04-26 09:12 a0g0bsinitvals4.fw
-rw-r--r-- 1 root root   158 2008-04-26 09:12 a0g0bsinitvals5.fw
-rw-r--r-- 1 root root  2680 2008-04-26 09:12 a0g0initvals4.fw
-rw-r--r-- 1 root root  1858 2008-04-26 09:12 a0g0initvals5.fw
-rw-r--r-- 1 root root   158 2008-04-26 09:12 a0g1bsinitvals13.fw
-rw-r--r-- 1 root root   158 2008-04-26 09:12 a0g1bsinitvals5.fw
-rw-r--r-- 1 root root  2056 2008-04-26 09:12 a0g1initvals13.fw
-rw-r--r-- 1 root root  1858 2008-04-26 09:12 a0g1initvals5.fw
-rw-r--r-- 1 root root   158 2008-04-26 09:12 b0g0bsinitvals13.fw
-rw-r--r-- 1 root root    18 2008-04-26 09:12 b0g0bsinitvals4.fw
-rw-r--r-- 1 root root   158 2008-04-26 09:12 b0g0bsinitvals5.fw
-rw-r--r-- 1 root root  2056 2008-04-26 09:12 b0g0initvals13.fw
-rw-r--r-- 1 root root  2680 2008-04-26 09:12 b0g0initvals4.fw
-rw-r--r-- 1 root root  1858 2008-04-26 09:12 b0g0initvals5.fw
-rw-r--r-- 1 root root   158 2008-04-26 09:12 lp0bsinitvals13.fw
-rw-r--r-- 1 root root  2052 2008-04-26 09:12 lp0initvals13.fw
-rw-r--r-- 1 root root  1320 2008-04-26 09:12 pcm4.fw
-rw-r--r-- 1 root root  1320 2008-04-26 09:12 pcm5.fw
-rw-r--r-- 1 root root 26600 2008-04-26 09:12 ucode11.fw
-rw-r--r-- 1 root root 24424 2008-04-26 09:12 ucode13.fw
-rw-r--r-- 1 root root 20080 2008-04-26 09:12 ucode4.fw
-rw-r--r-- 1 root root 22088 2008-04-26 09:12 ucode5.fw

No errors when I reboot - or none that I can tell because ubuntu does not support sgi 1600SW monitor pre -login screen (flickers and jumps about, login screen stable ) I can see enought to see grub & dual boot selection of ubuntu

is there sylog file somewhere under ubuntu (old sgi unix man)

Next step i'm not sure about 
any attempt to connect to wireless (thru top right scrren icon) just keeps repeating itself 
where is the nm-applet you talk of ?
thanks

---

### Post by fishyf on 2008-04-26
Simplest and fastest solution is Mad_Gouki's. You need a network connection (presumably wired), start Synaptic package manager, press reload, then find b43-fwcutter, install it, and when asked, search for new firmware.
Worked for me with 4306 Version 2 broadcom wireless card.

Edit: Actually, this only works intermittently.
Edit 2: This on a Dell D400

---

### Post by goslings on 2008-04-26
> **kai60 said:**
> 

Good luck and let me know how you go...

found a syslog !

---

### Post by goslings on 2008-04-26
> **fishyf said:**
> Simplest and fastest solution is Mad_Gouki's. You need a network connection (presumably wired), start Synaptic package manager, press reload, then find b43-fwcutter, install it, and when asked, search for new firmware.
Worked for me with 4306 Version 2 broadcom wireless card.

just tried this - it did not ask me to search for new firmware ???

---

### Post by fishyf on 2008-04-26
I don't know why you weren't asked for new firmware, but the point is moot. It only works intermittently. Every time I try to setup wireless in linux, I forget what a nightmare it is.

It certainly didn't seem this bad last time.

---

### Post by Ayuthia on 2008-04-26
> **goslings said:**
> just tried this - it did not ask me to search for new firmware ???

The script that actually grabs the file and installs it (it is not GUI) should be found in /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh.  All you need to do is run:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

---

### Post by sbrbot on 2008-04-26
> **goslings said:**
> upgraded from 7.1 to 8.04 - now wireless does not function
Device manager says BSM4306 is there
00:0e.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
wireless just loops round asking for wireless key - which i know is ok
but hardware drivers does not list bcm43xx just NVIDIA
utterly confused as I was in 7.10 - which I did get work (maybe fluke)
any help much appreciated 
thanks

I had probably the same problem. My Broadcom BSM4306 wireless network worked on Fedora Core 6 with ndiswrapper fine. When I upgraded to new version of kernel my wireless card suddenly stop to respond. Problem was that new kernel expected firmware ver. 4 while older kernel worked fine with ver. 3. When I changed the wireless firmware everything was fine again.

---

### Post by goslings on 2008-04-26
> **Ayuthia said:**
> The script that actually grabs the file and installs it (it is not GUI) should be found in /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh.  All you need to do is run:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

thanks
this put up all the right info (i think)
but sadly goes no further after a reboot

NO sign of bcm43 in system-admin-hardware drives 

I feel sure this info from the syslog has the clue constantly punmping out the line 

Apr 26 18:42:50 goslinux kernel: [ 1025.687168] APIC error on CPU0: 40(40)

and 

Apr 26 18:36:19 goslinux kernel: [  635.317264] APIC error on CPU0: 40(40)
Apr 26 18:36:20 goslinux kernel: [  636.564143] APIC error on CPU0: 40(40)
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) New wireless user key for network 'BTVOYAGER2110-BA' received. 
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 26 18:36:20 goslinux firmware_helper[6553]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/devices/pci0000:00/0000:00:0e.0/firmware/0000:00:0e.0' with driver '(unknown)'
Apr 26 18:36:20 goslinux kernel: [  637.184116] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Apr 26 18:36:20 goslinux kernel: [  637.248667] APIC error on CPU0: 40(40)
Apr 26 18:36:21 goslinux NetworkManager: <info>  Activation (eth1/wireless): access point 'BTVOYAGER2110-BA' is encrypted, and a key exists.  No new key needed. 
Apr 26 18:36:21 goslinux kernel: [  637.792851] APIC error on CPU0: 40(40)
Apr 26 18:36:22 goslinux kernel: [  638.309752] APIC error on CPU0: 40(40)
Apr 26 18:36:22 goslinux kernel: [  638.588967] APIC error on CPU0: 40(40)
Apr 26 18:36:22 goslinux NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Apr 26 18:36:22 goslinux kernel: [  638.841771] APIC error on CPU0: 40(40)
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Apr 26 18:36:22 goslinux firmware_helper[6559]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/devices/pci0000:00/0000:00:0e.0/firmware/0000:00:0e.0' with driver '(unknown)'
Apr 26 18:36:22 goslinux kernel: [  638.944006] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  kernel_driver for non broadcast check: bcm43xx (has_scan_capa_ssid=0) 
Apr 26 18:36:22 goslinux NetworkManager: <info>  Using plain AP_SCAN 2 for bcm43xx 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'AP_SCAN 2' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was '0' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4254564f5941474552323131302d4241' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 26 18:36:22 goslinux kernel: [  639.290630] APIC error on CPU0: 40(40)
Apr 26 18:36:25 goslinux kernel: [  641.889131] APIC error on CPU0: 40(40)
Apr 26 18:36:25 goslinux kernel: [  642.194690] APIC error on CPU0: 40(40)

I may have forgotten how difficult this was under 7.10 
totally stumped 
is there a reinstall 8.04 option or reset to 7.10 and re-update ?
feel sure it is a slight of hand and all would be well with 8.04 
but stumped
thanks for everyones help - seems looking at the posts I am not alone on this - still no yet completely out of the box software - as it was working under 7.10 

sorry long

---

### Post by brew1brew on 2008-04-26
I have theBCM94311MCG wlan mini-PCI (rev 02) in my laptop, I  had to compile ndiswrapper to make it work in fiesty. when I upgraded to Hardy it wasn't working, I followed the "hardy fix" instructions from the following page [WifiDocs/Driver/bcm43xx/Feisty No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). all is working fine now. these instructions work great.

Les

---

### Post by jazzman83 on 2008-04-26
I just installed hardy and my bmc4318 wireless wasn't working nor was it part of the restricted drivers area like it was in 7.10.  Anyway, I installed b43-fwcutter from repositories and rebooted and now it works perfectly without any issue.

---

### Post by hankchinaski on 2008-04-26
Mad_Gouki:   awesome!   thanks man!  that totaly worked.

-me, the ubuntu noob.

---

### Post by ImpressMe on 2008-04-26
Well, working but how FAST? I finally got it working (just reinstalling Hardy and letting it do the work), but if I right click the icon in the systray and select Connection Information I see that the speed is... 1 mb/s!

WTF? It was 24 mb/s in Gutsy, and when using Windows always 54 mb/s. I have a 4/4 mbit internet connection so there is no way in hell I am going to accept 1. What to do?

---

### Post by kai60 on 2008-04-26
If you use b43-fwcutter, you should comfortably get 24mb/s as I have, just make sure that you are using the 4 series firmware from linuxwireless.org. Hope that helps.

---

### Post by kai60 on 2008-04-26
Sorry, had to sleep mate. try moving the b43 folder into /lib/firmware/2.6.24-16-* and reboot. For some reason Ubuntu stores all of its wireless firmware there, but you certainly have the right fw installed.

---

### Post by goslings on 2008-04-27
push original thread(er)...

> **goslings said:**
> thanks
this put up all the right info (i think)
but sadly goes no further after a reboot

NO sign of bcm43 in system-admin-hardware drives 

I feel sure this info from the syslog has the clue constantly punmping out the line 

Apr 26 18:42:50 goslinux kernel: [ 1025.687168] APIC error on CPU0: 40(40)

and 

Apr 26 18:36:19 goslinux kernel: [  635.317264] APIC error on CPU0: 40(40)
Apr 26 18:36:20 goslinux kernel: [  636.564143] APIC error on CPU0: 40(40)
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) New wireless user key for network 'BTVOYAGER2110-BA' received. 
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 26 18:36:20 goslinux NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 26 18:36:20 goslinux firmware_helper[6553]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/devices/pci0000:00/0000:00:0e.0/firmware/0000:00:0e.0' with driver '(unknown)'
Apr 26 18:36:20 goslinux kernel: [  637.184116] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Apr 26 18:36:20 goslinux kernel: [  637.248667] APIC error on CPU0: 40(40)
Apr 26 18:36:21 goslinux NetworkManager: <info>  Activation (eth1/wireless): access point 'BTVOYAGER2110-BA' is encrypted, and a key exists.  No new key needed. 
Apr 26 18:36:21 goslinux kernel: [  637.792851] APIC error on CPU0: 40(40)
Apr 26 18:36:22 goslinux kernel: [  638.309752] APIC error on CPU0: 40(40)
Apr 26 18:36:22 goslinux kernel: [  638.588967] APIC error on CPU0: 40(40)
Apr 26 18:36:22 goslinux NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Apr 26 18:36:22 goslinux kernel: [  638.841771] APIC error on CPU0: 40(40)
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Apr 26 18:36:22 goslinux firmware_helper[6559]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/devices/pci0000:00/0000:00:0e.0/firmware/0000:00:0e.0' with driver '(unknown)'
Apr 26 18:36:22 goslinux kernel: [  638.944006] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  kernel_driver for non broadcast check: bcm43xx (has_scan_capa_ssid=0) 
Apr 26 18:36:22 goslinux NetworkManager: <info>  Using plain AP_SCAN 2 for bcm43xx 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'AP_SCAN 2' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was '0' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4254564f5941474552323131302d4241' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 scan_ssid 1' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  SUP: response was 'OK' 
Apr 26 18:36:22 goslinux NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 26 18:36:22 goslinux kernel: [  639.290630] APIC error on CPU0: 40(40)
Apr 26 18:36:25 goslinux kernel: [  641.889131] APIC error on CPU0: 40(40)
Apr 26 18:36:25 goslinux kernel: [  642.194690] APIC error on CPU0: 40(40)

I may have forgotten how difficult this was under 7.10 
totally stumped 
is there a reinstall 8.04 option or reset to 7.10 and re-update ?
feel sure it is a slight of hand and all would be well with 8.04 
but stumped
thanks for everyones help - seems looking at the posts I am not alone on this - still no yet completely out of the box software - as it was working under 7.10 

sorry long

---

### Post by kai60 on 2008-04-27
Hi mate,

sorry about taking so long to return to the forums, however my Ubuntu 8.04 had several errors that eventually forced me to concede that I would have to go back to 7.10 as I needed a stable working system.

I wiped my harddisk and re-installed 7.10 in order to get a system that works again. All is back to the way that it should be for me now. It does look like it is searching for your old driver, even though it should be looking for your new driver. Have you tried to blacklist your bcm43xx firmware?

---

### Post by goslings on 2008-04-27
> **kai60 said:**
> Hi mate,

sorry about taking so long to return to the forums, however my Ubuntu 8.04 had several errors that eventually forced me to concede that I would have to go back to 7.10 as I needed a stable working system.

I wiped my harddisk and re-installed 7.10 in order to get a system that works again. All is back to the way that it should be for me now. It does look like it is searching for your old driver, even though it should be looking for your new driver. Have you tried to blacklist your bcm43xx firmware?

no worries was wrapped up in the F1 GP
trying now - on reboot
Ian

---

### Post by goslings on 2008-04-27
> **kai60 said:**
> Hi mate,
...snip .... It does look like it is searching for your old driver, even though it should be looking for your new driver. Have you tried to blacklist your bcm43xx firmware?

Sadly blacklist makes no difference

Apr 27 22:41:39 goslinux kernel: [ 4813.704858] APIC error on CPU0: 40(40)
Apr 27 22:41:42 goslinux kernel: [ 4816.830324] APIC error on CPU0: 40(40)
Apr 27 22:41:43 goslinux firmware_helper[6614]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/devices/pci0000:00/0000:00:0e.0/firmware/0000:00:0e.0' with driver '(unknown)'
Apr 27 22:41:43 goslinux kernel: [ 4817.441547] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
Apr 27 22:41:45 goslinux NetworkManager: <WARN>  nm_device_802_11_wireless_scan(): (eth1): could not trigger wireless scan: No such device 
Apr 27 22:41:45 goslinux firmware_helper[6617]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/devices/pci0000:00/0000:00:0e.0/firmware/0000:00:0e.0' with driver '(unknown)' 

No matter what I try and i've tried several threads I still do not have a bcm43 under system - hardware drivers - just the NVIDA driver 

Absolutely stumped 
Now I'll have to leave it for a week as I work away - but i'll check in to see if anyone has any ideas
regards
Ian

---

### Post by lswest on 2008-05-02
try doing this ```
sudo modprobe -r bcm43xx
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe b43
sudo modprobe ssb
``` if that gives you wireless let us know and we can get it run at every boot.

Also, if it doesn't work, can you post the output of ```
lshw -C network
``` just so we can check it's actually using the right driver.

---

### Post by herrison on 2008-05-02
I appear to have a similar problem. Dell Latitude D600. Been running Ubuntu on it through (I think) 3 upgrades without wireless problem. Had to use fwcutter originally. Hardy 8.04 has killed it. I have been playing with the various options, and the laptop is now scanning and seeing wifis, but not connecting (it eventually times out).

The sudo steps above give me:

mike@mike-laptop:~$ sudo modprobe -r bcm43xx
[sudo] password for mike: 
mike@mike-laptop:~$ sudo modprobe -r b43
mike@mike-laptop:~$ sudo modprobe -r ssb
FATAL: Module ssb is in use.
mike@mike-laptop:~$ sudo modprobe b43
mike@mike-laptop:~$ sudo modprobe ssb

>> no wireless resulted

mike@mike-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:05:65:db
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5702-v2.25 ip=192.168.2.2 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:90:4b:b1:c5:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

I am prepared to do a clean install, either to 8.04 or 7.

Thanks, in advance, for the help

---

### Post by Ayuthia on 2008-05-02
> **herrison said:**
> 
mike@mike-laptop:~$ sudo modprobe -r ssb
FATAL: Module ssb is in use.


Can you post your lsmod|grep ssb?

---

### Post by herrison on 2008-05-02
Thanks

ssb   32260  2  b43,b43legacy

---

### Post by Ayuthia on 2008-05-02
The ssb module is current being used by b43 and b43legacy.  You will need to do the following:
```
sudo modprobe -r b43 b43legacy
sudo modprobe -r ssb
```My next question is if you ever loaded the b43legacy module?  If your answer is no, it might be possible that your 4306 card uses the b43legacy module which means that your next step is to do:
```
sudo modprobe b43legacy
```
otherwise do:
```
sudo modprobe b43
```
Some 4306 cards do use the b43legacy cards and most of the others use the b43.  If the b43legacy does not work, just do the moprobe -r steps over again and then do the sudo modprobe b43.

---

### Post by herrison on 2008-05-02
Both modules unsuccessful, I'm afraid - but I think I'm following the logic of listing the relevant modules (lsmod), removing them with the -r and adding.

When I remove them all, and load the b43legacy module, I can see wifi, but times out on trying to join. I list the modules, I can see that b43legacy is loaded. 

To try the b43 module, I remove them again - get an empty list - and then run sudo modbprobe b43. Having *only* done this, when I do a list - I'm back to 

ssb  32260 2 b43legacy, b43 - even though I've removed both and only added b43

This also sees wifi but refuses to attach.

---

### Post by Ayuthia on 2008-05-02
When you have the modules loaded, can you post your ifconfig, iwconfig information?  Also, are you using any encryption for your wireless?  And can you tell me which channel your router is on (you can get it by using iwlist scan)?  Since you are doing the iwlist scan, can you see if there are other access points out there that are using the same channel?

---

### Post by herrison on 2008-05-02
I'm not using encryption at the moment. There are a bunch of networks around, I'm on 12 - there are several up at the moment - another four in the gui (all with encryption), but i'm not getting the same number consistently in iwlist - the ones I can see are 1, 9, 11 - thanks again

===========

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:05:65:db  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe05:65db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2419878 (2.3 MB)  TX bytes:520467 (508.2 KB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:90:4b:b1:c5:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:175900 (171.7 KB)  TX bytes:175900 (171.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-B1-C5-12-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

========
iwlist

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Elephart"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:50:35:DE:7F   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Ayuthia on 2008-05-02
Why don't you try a different channel instead of 12.  I have heard that some people having problems with channels in the double-digit range (I can't remember if it was higher than 11 or 12).

---

### Post by herrison on 2008-05-02
Ayuthia - that is amazing. Channel 5 working strong and loud. I am ... slackjawed. Thank you so very, very much.

---

### Post by Ayuthia on 2008-05-02
Wonderful!  Can you tell me which modules you are using (b43 & b43legacy or just b43)?

EDIT:  Can you also supply your lspci -nn?  I am keeping track of the Broadcom chipsets and this is the first b43legcay one that I have run into.

---

### Post by herrison on 2008-05-02
it says it's running both of them

ssb                    32260  2 b43legacy,b43

---

### Post by herrison on 2008-05-02
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 01)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet [14e4:16a6] (rev 02)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

---

### Post by Ayuthia on 2008-05-02
Thanks and in case you did not see my edit, can you provide your lspci -nn?

Edit: Nevermind.  I am living in the world of dialup...

---

### Post by herrison on 2008-05-02
Sorry, just lost my connection for a while. Rebooted, and I'm back on - list of mods now

ssb                    32260  1 b43legacy

i take it you saw my lspci

thanks for you help again. I've learnt something as well.

---

### Post by mnomady on 2008-05-02
ok, I am new to linux and have the same problem.  Hardy with a Broadcom 4306 on a Presario 2500 that doesn't see any networks.  I have read this thread, but it sounds like Chinese algebra thus far... Could someone please help explain to me a bit more step-by-step of how to get wireless up and running...?  Everything else is great...

---

### Post by goslings on 2008-05-02
The original poster - 
BINGO!
Thanks lswest this below has worked !
Had to wait a week to try it out
just what has it done and as you say how do I ."get it to run every boot
Thanks again 
Ian

> **lswest said:**
> try doing this ```
sudo modprobe -r bcm43xx
sudo modprobe -r b43
sudo modprobe -r ssb
sudo modprobe b43
sudo modprobe ssb
``` if that gives you wireless let us know and we can get it run at every boot.

Also, if it doesn't work, can you post the output of ```
lshw -C network
``` just so we can check it's actually using the right driver.

---

### Post by Ayuthia on 2008-05-02
Sorry for using your post.  Here is a link to some options on how to make it permanent:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c)

I prefer version 0.3, but the other should work also.  Just remove the b44 part if it does not apply to you (if you did not have to remove b44 for ssb, then it does not apply).

Here is a modified snip of version 0.3 from the site without the b44 added:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r bcm43xx b43 ssb; modprobe --ignore-install ndiswrapper' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

---

### Post by lswest on 2008-05-03
the commands remove the modules (the lines that go "modprobe -r [module name]") and then re-start the ones you need.  I'll attach a script i wrote and how to make it occur at every boot.

Place the script somewhere in a directory (i keep my scripts in ~/scripts, but that's your preference) then run ```
cd [path to script]
sudo cp startNetwork.sh /etc/init.d
sudo chmod 755 /etc/init.d/startNetwork.sh
sudo update-rc.d startNetwork.sh defaults
``` that should make the corresponding entries for boot up.

Also, you can just put the script in /etc/init.d if you want, but i keep backups of all the scripts i use on my laptop in the above mentioned scripts folder.  An explanation on the code is: change directory to where the script is saved, copy it to the /etc/init.d/ folder, then make it executable and the right permissions, then create links in autostart folders, so that it is run every boot.

Glad it works and thanks for the thanks,
Lswest

---

### Post by Ayuthia on 2008-05-03
> **goslings said:**
> The original poster - 
BINGO!
Thanks lswest this below has worked !
Had to wait a week to try it out
just what has it done and as you say how do I ."get it to run every boot
Thanks again 
Ian
I was just thinking about it further, but if you don't have a Broadcom ethernet controller (wired connection), you just need to blacklist b43 and ssb.

If you are not sure if you have b44, when you boot up and before you load ndiswrapper, do a lsmod|grep b44 in the terminal.  If the prompt just comes back, then you don't have it.  If it does, then you need to add a script.

---

### Post by lswest on 2008-05-03
> **Ayuthia said:**
> I was just thinking about it further, but if you don't have a Broadcom ethernet controller (wired connection), you just need to blacklist b43 and ssb.

If you are not sure if you have b44, when you boot up and before you load ndiswrapper, do a lsmod|grep b44 in the terminal.  If the prompt just comes back, then you don't have it.  If it does, then you need to add a script.

he's trying to use the b43 driver, if you look at the command i had him run i just remove the b43xx module and then the b43 and ssb drivers, but then i start the b43 and ssb modules again, which seems to work.  Blacklisting what you're trying to use won't help ;)

---

### Post by Ayuthia on 2008-05-03
> **lswest said:**
> he's trying to use the b43 driver, if you look at the command i had him run i just remove the b43xx module and then the b43 and ssb drivers, but then i start the b43 and ssb modules again, which seems to work.  Blacklisting what you're trying to use won't help ;)
Sorry about that!  I am so used to seeing steps/scripts like that for ndiswrapper.

---

### Post by goslings on 2008-05-03
worked :KS
Its these little things that make Ubuntu a little tricky out of the box (and I have 20+ years experience of sgi irix)
Now to get the back/forward buttons to work again on my mouse, another thing that 8.04 upgrade removed from my 7.10!
thanks again.
Ian

> **lswest said:**
> the commands remove the modules (the lines that go "modprobe -r [module name]") and then re-start the ones you need.  I'll attach a script i wrote and how to make it occur at every boot.
Glad it works and thanks for the thanks,
Lswest

---

### Post by lswest on 2008-05-03
no problem, glad we got it working, and yeah...sorry, but I won't be able to help you with your mouse, i never bother with extra buttons.  Good luck with it though, i'm sure you'll find some answers.

---

### Post by Errrwin on 2008-05-03
Instead of making a new thread, I&#314;l keep it in this one. :)

My wireless network does not get past 

```
May  3 14:07:42 desktop kernel: [  537.807625] wlan0: Initial auth_alg=0
May  3 14:07:42 desktop kernel: [  537.807635] wlan0: authenticate with AP 00:19:cb:17:9e:0f
May  3 14:07:42 desktop kernel: [  537.808025] wlan0: Initial auth_alg=0
May  3 14:07:42 desktop kernel: [  537.808031] wlan0: authenticate with AP 00:19:cb:17:9e:0f
May  3 14:07:42 desktop kernel: [  538.006407] wlan0: authenticate with AP 00:19:cb:17:9e:0f
May  3 14:07:42 desktop kernel: [  538.205409] wlan0: authenticate with AP 00:19:cb:17:9e:0f
May  3 14:07:42 desktop kernel: [  538.404909] wlan0: authentication with AP 00:19:cb:17:9e:0f timed out
May  3 14:07:47 desktop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
```

I can see wireless networks, just not connect. While my laptop (on XP) has not trouble at all connecting to my AP.

```
*-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
```

Any thoughts? :)

---

### Post by lswest on 2008-05-03
have you tried running the modprobe commands i have mentioned above?  also, can you post the output of ```
cat /etc/network/interfaces
```, somehow it seems to have more than one entry somewhere for device "wlan0".

Also, can you configure it manually?
```
sudo iwconfig wlan0 essid [name of your network] key [network key] && sudo dhclient wlan0
``` where you replace the things in square brackets with the corresponding info, e.g. replace "[name of your network]" with "Home" (without the quotes) if that's what your network is called.

---

### Post by Errrwin on 2008-05-03
```
erwin@desktop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

erwin@desktop:~$ 
erwin@desktop:~$ sudo modprobe -r bcm43xx
erwin@desktop:~$ sudo modprobe -r b43
erwin@desktop:~$ sudo modprobe -r ssb
erwin@desktop:~$ sudo modprobe b43
erwin@desktop:~$ sudo modprobe ssb
erwin@desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:b4:74:c1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.33 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0f:66:1d:72:f5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```


> Also, can you configure it manually?
```
sudo iwconfig wlan0 essid [name of your network] key [network key] && sudo dhclient wlan0
``` where you replace the things in square brackets with the corresponding info, e.g. replace "[name of your network]" with "Home" (without the quotes) if that's what your network is called.

I keep getting errors when trying to do that. Replaced my networkkey with the always appropriate "wah". :P

```
erwin@desktop:~$ sudo iwconfig wlan0 essid errrwin@gmail.com key wah && sudo dhclient wlan0
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "wah".
erwin@desktop:~$ 

```

I tried connecting with my AP wide open, no security whatsoever, but that ends up in the same error: timed out.

---

### Post by lswest on 2008-05-03
what kind of encryption are you using?  WEP hex/ascii, or WPA? if it's WPA i'm not sure of the command to specify that in the terminal.  And i assume you were unable to connect via the network manager after running the modprobe commands?

---

### Post by Errrwin on 2008-05-03
> **lswest said:**
> what kind of encryption are you using?  WEP hex/ascii, or WPA? if it's WPA i'm not sure of the command to specify that in the terminal.  And i assume you were unable to connect via the network manager after running the modprobe commands?

I'm using WPA-PSK, nothing fancy. ;)

I have not been able to connect at all, the modprobe commands didn't help either.

I might just do another clean install (as it doesn't take very long at all) and try again on a fresh install.

That will however not be today, I'm going to enjoy the sun. But I'll be back... ;)

---

### Post by sixsmith on 2008-06-10
> **goslings said:**
> 
No errors when I reboot - or none that I can tell

First, re: errors: you can see many errors from during and after bootup at _System_Administration_System Log.

OK, I just got through this myself, getting a TrueMobile 1300 (=Broadcom 4306) working on my Dell Inspiron 5100. 

Did you try both ndiswrapper+windows drivers and b43xx? If so, I would recommend to remove ndiswrapper and then redo the b43xx install. That worked for me.

Best of luck!

---

### Post by R-C-S on 2008-07-29
> **sixsmith said:**
> First, re: errors: you can see many errors from during and after bootup at _System_Administration_System Log.

OK, I just got through this myself, getting a TrueMobile 1300 (=Broadcom 4306) working on my Dell Inspiron 5100. 

Did you try both ndiswrapper+windows drivers and b43xx? If so, I would recommend to remove ndiswrapper and then redo the b43xx install. That worked for me.

Best of luck!

The one thing about forums is trying to get through the entire one and figure out what steps did and did not work for someone with the same hardware.

I was wondering what steps actually did work for you. I have a Dell Inspiron 5100 with the Broadcom 4306 wireless card. I think it is also known as the TrueMobile 1300 rev02.

I've tried the forums for using bcm43xx as well as ndiswrapper and I have yet to get the wireless to connect. This whole episode almost makes me want to return to Windows.

---

### Post by adept_king on 2008-08-16
> **sridenour said:**
> I would look at this.
[http://ubuntuforums.org/showpost.php?p=4793983&postcount=1](http://ubuntuforums.org/showpost.php?p=4793983&postcount=1)

I figured r all the hoops and rings of fire I jumped through to loose the card after every reboot (like you seem to be doing), that anything as simple as what was written there wouldn't work. Yet it did and the card shows up after several reboots.

the file at that page "http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2"

returns the following when the command line "tar xjf broadcom-wl-4.80.53.0.tar.bz2" is run:

bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors

it wont extract.  cannot proceed further.

---

### Post by Ayuthia on 2008-08-16
> **adept_king said:**
> the file at that page "http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2"

returns the following when the command line "tar xjf broadcom-wl-4.80.53.0.tar.bz2" is run:

bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors

it wont extract.  cannot proceed further.

If you have a working wired connection in Ubuntu, you might try deleting that file and downloading it again by doing the following:
```
wget -c http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
```
I am guessing that the file is corrupt.  I just downloaded the file and was able to extract the file.

If you don't have a working connection in Ubuntu, you should try downloading the file again.

---

