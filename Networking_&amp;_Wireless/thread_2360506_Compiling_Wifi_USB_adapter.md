---
title: "Compiling Wifi USB adapter"
date: 2017-05-05
forum: Networking &amp; Wireless
---

### Post by godlikesonny on 2017-05-05
Hi, im fairly new to ubuntu, however i managed to install the realtek8812au driver without any issues until now.
I was using a patched linuxium kernel before, since im using an asus e200ha, which has no sound in linux as of now.
Because i had alot of stability issues in general in the past few days, i decided to upgrade to 17.04 with 4.11rc5 kernel.
Now im not able to compile the driver anymore.
Im also new to the forum aswell, and for some reason im too retarded to start a new thread. Any help would be greatly appreciated!

Thanks!

---

### Post by howefield on 2017-05-05
Post moved to own thread.

---

### Post by godlikesonny on 2017-05-05
Thanks! Can you tell me how to start a new thread aswell? That would be great!

---

### Post by wildmanne39 on 2017-05-05
If you are still pursuing help with your wifi adapter, then you need to use this thread and do not create another one for the same topic.

You will see at the top left of the forum that you are in a clickable button that says post a new thread you just click on it.

If no one replies I will check later on the driver for this device, I have one too and it gives me a little trouble from time to time, I am almost positive you can not compile the driver for that new of a kernel yet, I suggest if you want to use it you need to use an older kernel and try to find another way to deal with your other issue.

---

### Post by godlikesonny on 2017-05-05
For some reason I'm not able to see that button. Maybe I'm not yet able to create a new thread? Even tho it says I have the permission to do so... doesn't matter atm anyways.

I would really like to use the newest kernel, since I need the hdmi sound.
Would be great if you could look into it. For now I just rerolled my old system and will see if I can fix stuff. Else I'm gonna reinstall from scratch.

Thanks so far tho!

---

### Post by wildmanne39 on 2017-05-05
I am including a screenshot, this is from my computer.

---

### Post by godlikesonny on 2017-05-05
I'm stupid. I found it now, even tho I'm pretty sure it wasn't there when i just created my account. Thanks!

---

### Post by chili555 on 2017-05-05
> Now im not able to compile the driver anymore.There are a variety of driver packages out there, some work well with newer kernel versions and some with older kernel versions. Not everyone runs the bleeding edge kernel. I saw a post on askubuntu yesterday that asked about kernel version 2.6 (!!!), a kernel that was in use when some of us were in high school!

Where did you get the driver package you are trying to compile unsuccessfully? The driver CD? Github? Or...?

---

### Post by godlikesonny on 2017-05-05
2.6 Ridiculous. 

I tried several versions of the driver. The one from github
[https://github.com/diederikdehaas/rtl8812AU](https://github.com/diederikdehaas/rtl8812AU)
,8812-dkms and the one from the disc.
Neither of them seemed to work

---

### Post by chili555 on 2017-05-05
First, find out which version may be (mis)installed:```
sudo dkms status
```Remove any or all related to 8812au; for instance, if you see this:```
rtl8812au, 4.3.14, 4.10.0-19-generic, x86_64: installed
rtl8812au, 4.3.14, 4.10.0-20-generic, x86_64: installed
rtl8812au, 4.3.14, 4.9.0-040900-generic, x86_64: installed

```Then remove them with:```
sudo dkms remove rtl8812au/4.3.14 --all
```Now, let's find one that works. 

[https://github.com/diederikdehaas/rtl8812AU](https://github.com/diederikdehaas/rtl8812AU) This version 'makes' for me on my 4.10.0-20 kernel, albeit with a couple of possibly harmless warnings. Would you try a fresh clone and try make and let's see what happens. In the terminal:```
sudo rm -r rtl8812AU
git clone https://github.com/diederikdehaas/rtl8812AU
cd rtl8812AU
make 
```Does it end in an error or like this?> <snip>
 Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/chili/Desktop/Forum/rtl8812AU/8812au.mod.o
  LD [M]  /home/chili/Desktop/Forum/rtl8812AU/[COLOR="#FF0000"]8812au.ko[/COLOR]
make[1]: Leaving directory '/usr/src/linux-headers-4.10.0-20-generic'
If it ends in an error, please post it.

If it builds the module, let's load it and see if there is an error. ```
sudo insmod 8812au.ko
```

---

### Post by godlikesonny on 2017-05-06
Not at home atm, will post everything needed when I am in like 4 hours.

---

### Post by godlikesonny on 2017-05-06
Since i already rerolled my last system,i tried compiling it on a live usb with 4.11 kernel. Driver was cloned from git [https://www.github.com/diederikdehaas/rtl8812au](https://www.github.com/diederikdehaas/rtl8812au) . Heres the output:

ubuntu@ubuntu:/media/ubuntu/USB/E200HA/rtl8812AU$ make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.11.0-041100-generic/build M=/media/ubuntu/USB/E200HA/rtl8812AU  modules
make[1]: Entering directory '/usr/src/linux-headers-4.11.0-041100-generic'
  CC [M]  /media/ubuntu/USB/E200HA/rtl8812AU/core/rtw_cmd.o
In file included from /media/ubuntu/USB/E200HA/rtl8812AU/include/drv_types.h:32:0,
                 from /media/ubuntu/USB/E200HA/rtl8812AU/core/rtw_cmd.c:22:
/media/ubuntu/USB/E200HA/rtl8812AU/include/osdep_service.h: In function &#8216;thread_enter&#8217;:
/media/ubuntu/USB/E200HA/rtl8812AU/include/osdep_service.h:343:2: error: implicit declaration of function &#8216;allow_signal&#8217; [-Werror=implicit-function-declaration]
  allow_signal(SIGTERM);
  ^~~~~~~~~~~~
/media/ubuntu/USB/E200HA/rtl8812AU/include/osdep_service.h: In function &#8216;flush_signals_thread&#8217;:
/media/ubuntu/USB/E200HA/rtl8812AU/include/osdep_service.h:353:6: error: implicit declaration of function &#8216;signal_pending&#8217; [-Werror=implicit-function-declaration]
  if (signal_pending (current))
      ^~~~~~~~~~~~~~
/media/ubuntu/USB/E200HA/rtl8812AU/include/osdep_service.h:355:3: error: implicit declaration of function &#8216;flush_signals&#8217; [-Werror=implicit-function-declaration]
   flush_signals(current);
   ^~~~~~~~~~~~~
cc1: some warnings being treated as errors
scripts/Makefile.build:294: recipe for target '/media/ubuntu/USB/E200HA/rtl8812AU/core/rtw_cmd.o' failed
make[2]: *** [/media/ubuntu/USB/E200HA/rtl8812AU/core/rtw_cmd.o] Error 1
Makefile:1498: recipe for target '_module_/media/ubuntu/USB/E200HA/rtl8812AU' failed
make[1]: *** [_module_/media/ubuntu/USB/E200HA/rtl8812AU] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.11.0-041100-generic'
Makefile:1576: recipe for target 'modules' failed
make: *** [modules] Error 2

---

### Post by chili555 on 2017-05-06
You might try this: [https://github.com/diederikdehaas/rtl8812AU/archive/driver-4.3.22-beta.zip](https://github.com/diederikdehaas/rtl8812AU/archive/driver-4.3.22-beta.zip)

I am not sure what to suggest. All of the github files 'make' on my 4.10.0-xx system, albeit with a couple of warnings. I have no experience with 4.11 and haven't any idea why it fails.

---

### Post by godlikesonny on 2017-05-06
I already tried all versions on 4.11-rc5 and neither of them worked. They dont work on 4.11 either. Same output.

---

### Post by chili555 on 2017-05-07
Then we are left with but a very few alternatives. Try a 4.10 kernel, get a different device or file an issue at github and ask for a fix. [https://github.com/diederikdehaas/rtl8812au/issues](https://github.com/diederikdehaas/rtl8812au/issues)

---

### Post by godlikesonny on 2017-05-07
The problem with the 4.10 kernel is the missing hdmi audio on cherrytrail which I really need. Gonna file an issue on github later. Thanks for the help tho!

---

### Post by godlikesonny on 2017-05-13
Thanks to maurossi: [https://github.com/maurossi/rtl8812au/tree/1d3af1e8e931f6fee3ceb26cee4c8b214bb8384c](https://github.com/maurossi/rtl8812au/tree/1d3af1e8e931f6fee3ceb26cee4c8b214bb8384c) the driver is now able to be compiled on at least 4.12 rc1 kernel.
However i am not able to connect to my network. System log says key may be incorrect, even tho im sure its right.

```
May 13 23:04:51 ubuntu NetworkManager[1428]: [1494716691.8860] keyfile: update /etc/NetworkManager/system-connections/Sonny (2de61c5b-cab2-43a2-92aa-fc2ca016bd9d,"Sonny")
May 13 23:04:51 ubuntu NetworkManager[1428]: [1494716691.8913] device (wlx00e04c3280e2): state change: need-auth -> prepare (reason 'none') [60 40 0]
May 13 23:04:51 ubuntu NetworkManager[1428]: [1494716691.8926] device (wlx00e04c3280e2): state change: prepare -> config (reason 'none') [40 50 0]
May 13 23:04:51 ubuntu NetworkManager[1428]: [1494716691.8932] device (wlx00e04c3280e2): Activation: (wifi) connection 'Sonny' has security, and secrets exist. No new secrets needed.
May 13 23:04:51 ubuntu NetworkManager[1428]: [1494716691.8934] Config: added 'ssid' value 'Sonny'
May 13 23:04:51 ubuntu NetworkManager[1428]: [1494716691.8934] Config: added 'scan_ssid' value '1'
May 13 23:04:51 ubuntu NetworkManager[1428]: [1494716691.8935] Config: added 'key_mgmt' value 'WPA-PSK'
May 13 23:04:51 ubuntu NetworkManager[1428]: [1494716691.8935] Config: added 'auth_alg' value 'OPEN'
May 13 23:04:51 ubuntu NetworkManager[1428]: [1494716691.8935] Config: added 'psk' value ''
May 13 23:04:51 ubuntu NetworkManager[1428]: [1494716691.9048] sup-iface[0x563feb891ce0,wlx00e04c3280e2]: config: set interface ap_scan to 1
May 13 23:04:52 ubuntu NetworkManager[1428]: [1494716692.3344] device (wlx00e04c3280e2): supplicant interface state: inactive -> scanning
May 13 23:04:52 ubuntu kernel: [ 791.247496] RTL871X: nolinked power save leave
May 13 23:04:56 ubuntu wpa_supplicant[1922]: wlx00e04c3280e2: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
May 13 23:04:56 ubuntu wpa_supplicant[1922]: wlx00e04c3280e2: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
May 13 23:04:56 ubuntu wpa_supplicant[1922]: wlx00e04c3280e2: Trying to associate with c4:27:95:bb:8a:ae (SSID='Sonny' freq=2437 MHz)
May 13 23:04:56 ubuntu kernel: [ 795.300101] RTL871X: rtw_set_802_11_connect(wlx00e04c3280e2) fw_state=0x00000008
May 13 23:04:56 ubuntu NetworkManager[1428]: [1494716696.4101] device (wlx00e04c3280e2): supplicant interface state: scanning -> associating
May 13 23:04:56 ubuntu kernel: [ 795.388653] RTL871X: start auth
May 13 23:04:56 ubuntu kernel: [ 795.391407] RTL871X: auth success, start assoc
May 13 23:04:56 ubuntu kernel: [ 795.397204] RTL871X: rtw_cfg80211_indicate_connect(wlx00e04c3280e2) BSS not found !!
May 13 23:04:56 ubuntu kernel: [ 795.397222] RTL871X: assoc success
May 13 23:04:56 ubuntu wpa_supplicant[1922]: wlx00e04c3280e2: Associated with c4:27:95:bb:8a:ae
May 13 23:04:56 ubuntu NetworkManager[1428]: [1494716696.4898] device (wlx00e04c3280e2): supplicant interface state: associating -> associated
May 13 23:04:56 ubuntu kernel: [ 795.409097] ath: EEPROM regdomain: 0x8114
May 13 23:04:56 ubuntu kernel: [ 795.409104] ath: EEPROM indicates we should expect a country code
May 13 23:04:56 ubuntu kernel: [ 795.409106] ath: doing EEPROM country->regdmn map search
May 13 23:04:56 ubuntu kernel: [ 795.409108] ath: country maps to regdmn code: 0x37
May 13 23:04:56 ubuntu kernel: [ 795.409110] ath: Country alpha2 being used: DE
May 13 23:04:56 ubuntu kernel: [ 795.409111] ath: Regpair used: 0x37
May 13 23:04:56 ubuntu kernel: [ 795.409115] ath: regdomain 0x8114 dynamically updated by country IE
May 13 23:04:56 ubuntu wpa_supplicant[1922]: wlx00e04c3280e2: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=DE
May 13 23:04:56 ubuntu kernel: [ 795.414316] RTL871X: recv eapol packet
May 13 23:04:56 ubuntu kernel: [ 795.414909] RTL871X: send eapol packet
May 13 23:04:56 ubuntu NetworkManager[1428]: [1494716696.5064] device (wlx00e04c3280e2): supplicant interface state: associated -> 4-way handshake
May 13 23:04:57 ubuntu kernel: [ 796.251929] RTL871X: recv eapol packet
May 13 23:04:57 ubuntu kernel: [ 796.252643] RTL871X: send eapol packet
May 13 23:04:58 ubuntu kernel: [ 797.152673] RTL871X: recv eapol packet
May 13 23:04:58 ubuntu kernel: [ 797.153368] RTL871X: send eapol packet
May 13 23:04:59 ubuntu kernel: [ 798.052594] RTL871X: recv eapol packet
May 13 23:04:59 ubuntu kernel: [ 798.053344] RTL871X: send eapol packet
May 13 23:05:00 ubuntu kernel: [ 798.952400] RTL871X: recv eapol packet
May 13 23:05:00 ubuntu kernel: [ 798.952931] RTL871X: send eapol packet
May 13 23:05:00 ubuntu kernel: [ 799.852811] RTL871X: recv eapol packet
May 13 23:05:00 ubuntu kernel: [ 799.853315] RTL871X: send eapol packet
May 13 23:05:01 ubuntu kernel: [ 800.752436] RTL871X: recv eapol packet
May 13 23:05:01 ubuntu kernel: [ 800.752923] RTL871X: send eapol packet
May 13 23:05:02 ubuntu kernel: [ 801.652347] RTL871X: recv eapol packet
May 13 23:05:02 ubuntu kernel: [ 801.653287] RTL871X: send eapol packet
May 13 23:05:03 ubuntu kernel: [ 802.550398] RTL871X: OnDeAuth(wlx00e04c3280e2) reason=15, ta=c4:27:95:bb:8a:ae, ignore=0
May 13 23:05:03 ubuntu wpa_supplicant[1922]: wlx00e04c3280e2: CTRL-EVENT-DISCONNECTED bssid=c4:27:95:bb:8a:ae reason=0 locally_generated=1
May 13 23:05:03 ubuntu wpa_supplicant[1922]: wlx00e04c3280e2: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
May 13 23:05:03 ubuntu wpa_supplicant[1922]: wlx00e04c3280e2: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Sonny" auth_failures=1 duration=10 reason=WRONG_KEY
May 13 23:05:03 ubuntu wpa_supplicant[1922]: wlx00e04c3280e2: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="Sonny" auth_failures=2 duration=20 reason=CONN_FAILED
May 13 23:05:03 ubuntu NetworkManager[1428]: [1494716703.6456] device (wlx00e04c3280e2): supplicant interface state: 4-way handshake -> disconnected
May 13 23:05:03 ubuntu NetworkManager[1428]: [1494716703.6485] device (wlx00e04c3280e2): Activation: (wifi) disconnected during association, asking for new key
May 13 23:05:03 ubuntu NetworkManager[1428]: [1494716703.6493] device (wlx00e04c3280e2): state change: config -> need-auth (reason 'supplicant-disconnect') [50 60 8]
May 13 23:05:03 ubuntu wpa_supplicant[1922]: wlx00e04c3280e2: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
May 13 23:05:03 ubuntu NetworkManager[1428]: [1494716703.7469] device (wlx00e04c3280e2): supplicant interface state: disconnected -> inactive
May 13 23:05:03 ubuntu nm-applet[2501]: No keyring secrets found for Sonny/802-11-wireless-security; asking user.

```
Any clues?

---

### Post by wildmanne39 on 2017-05-14
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by godlikesonny on 2017-05-14
Alright, i will remember that for the next time. 

I did all the steps from the linked thread and ran the wireless script.

[https://pastebin.com/nEJtYAdk](https://pastebin.com/nEJtYAdk)

---

