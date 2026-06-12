---
title: "Wireless drops out in 17.04 with kernel 4.10 using RealTek 8821ae"
date: 2017-08-17
forum: Networking &amp; Wireless
---

### Post by pogona on 2017-08-17
Shortly after upgrading from 16.10 to 17.04 my wireless connection became unstable, dropping out a few minutes after the system is booted. Wireless is stable if I boot with kernel 4.8.0 (see wireless-info output from 4.8.0-49 in [http://paste.ubuntu.com/25330890/](http://paste.ubuntu.com/25330890/)), but not with 4.10 (see output from 4.10.0-32 in [http://paste.ubuntu.com/25331008/](http://paste.ubuntu.com/25331008/)).

The computer is a Leader SC562, fitted with a RealTek 8821ae card. I've tested the wireless connections with several different wifi systems, always with the same results. There is no problem with Windows 10 (dual boot on the same machine).

Can anybody suggest what's happened between 4.8.0 and 4.10.0, but more particularly how I can fix this problem? (I'm no technical nerd!)

---

### Post by wildmanne39 on 2017-08-17
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

Please run it from both kernels and post both so we can see the difference.

Thanks

---

### Post by vocx on 2017-08-17
> **wildmanne39 said:**
> 
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

Please run it from both kernels and post both so we can see the difference.

Thanks

He did but the links are not clickable.

> **pogona said:**
> Shortly after upgrading from 16.10 to 17.04 my wireless connection became unstable, dropping out a few minutes after the system is booted. Wireless is stable if I boot with kernel 4.8.0 (see wireless-info output from 4.8.0-49 in [http://paste.ubuntu.com/25330890/](http://paste.ubuntu.com/25330890/)), but not with 4.10 (see output from 4.10.0-32 in [http://paste.ubuntu.com/25331008/](http://paste.ubuntu.com/25331008/)).

The computer is a Leader SC562, fitted with a RealTek 8821ae card. I've tested the wireless connections with several different wifi systems, always with the same results. There is no problem with Windows 10 (dual boot on the same machine).

Can anybody suggest what's happened between 4.8.0 and 4.10.0, but more particularly how I can fix this problem? (I'm no technical nerd!)
See these threads for reference: [https://ubuntuforums.org/showthread.php?t=2368526](https://ubuntuforums.org/showthread.php?t=2368526)
[https://ubuntuforums.org/showthread.php?t=2368005&p=13673251#post13673251](https://ubuntuforums.org/showthread.php?t=2368005&p=13673251#post13673251)
[https://ubuntuforums.org/showthread.php?t=2367093&p=13669924#post13669924](https://ubuntuforums.org/showthread.php?t=2367093&p=13669924#post13669924)

They all recommend installing the newest drivers available.
[https://medium.com/@elmaxx/rtl8821ae...4-4c1286524afa]("https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa")

```

sudo apt-get install linux-headers-generic build-essential git
git clone http://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install

```

"These commands build and install the drivers for rtl8192ce, rtl8192se, rtl8192de, rtl8188ee, rtl8192ee, rtl8723ae, rtl8723be, and rtl8821ae, all in one go. Just in case the system doesn’t load the appropriate kernel module, you can execute the following command from within your rtlwifi_new directory
```

sudo modprobe rtl8821ae

```

---

### Post by pogona on 2017-08-17
Sorry I hadn't made it clear that the I'd already run the wireless script, with the links somewhat shortened in my original post.

For 4.8.0:  [https://paste.ubuntu.com/25330890/](https://paste.ubuntu.com/25330890/)

For 4.10.0:  [https://paste.ubuntu.com/25331008/](https://paste.ubuntu.com/25331008/)

Hope this helps.

---

### Post by pogona on 2017-08-17
Thanks VOCX for your suggestion. As it happens I'd already installed the latest drivers, but it didn't help.

---

### Post by wildmanne39 on 2017-08-17
In 17.04 go into network manager and put a check by enable auto connect.

Then set your network settings to match the settings in the screenshots.

Reboot and let us know if that is better.

---

### Post by pogona on 2017-08-18
Sorry, wildmanne39, but those changes made no difference.

---

### Post by wildmanne39 on 2017-08-18
If you are connecting to:
```
Jack&Gill        <MAC 'Jack<MAC 'Jack<MAC address>Gill' [AN1]>Gill' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Jack&Gill_Guest  <MAC 'Jack<MAC 'Jack<MAC address>Gill_Guest' [AN2]>Gill_Guest' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        

```

First they are both on the same channel so your wifi is confused and can not connect or stay connected, please change one to like 11, set them both to a fixed channel.

Second Use just WPA2 not mixed or WPA1.

Third What Country are you in so we can set your country code?

---

### Post by Hadaka on 2017-08-18
Hi your report shows you were connected by hardwire/cable Ethernet Not
wireless 4.8.0-49-generic..
```
#http://paste.ubuntu.com/25330890/
#Linux 4.8.0-49-generic
#GENERAL.DEVICE:   enp3s0
#GENERAL.TYPE:      ethernet
#GENERAL.STATE:    100 (connected)

#GENERAL.DEVICE:   wlp2s0   Jack&Gill
#GENERAL.TYPE:     wifi
#GENERAL.STATE:    30 (disconnected)
```
Please open a terminal then copy and paste..
```
sudo iw reg set AU
sudo sed -i 's/=.*/=AU/' /etc/default/crda
```
Next.. the ssid of Jack&Gill...and...Jack&Gill_guest
Both have the " **[COLOR=#ff0000]&[/COLOR]** " in the name..This causes an error in reading the ssid correctly.
Please access the router ssid configuration and and modify the ssid to something like..
Jack-n-Gill   Jack-n-Gill_guest ...also the Jack and Gill guest is currently mixed wpa1 - wpa2
and TKIP...Please change the guest connection to wpa2 aes ccmp NO TKIP.
when the above changes are complete, please
disconnect the wired connection, boot and test wireless.
Thanks

---

### Post by pogona on 2017-08-21
[FONT=Liberation Sans, sans-serif][SIZE=2]In response to the suggestions from winldmanne39 and Hadaka I made the following changes:[/SIZE][/FONT]
 
 
 [FONT=Liberation Sans, sans-serif][SIZE=2]1.  The wifi networks renamed to &#8220;JackAndGill&#8221; (and &#8220;JackAndGill_Guest&#8221;) so as to remove the &#8220;&&#8221;.[/SIZE][/FONT]
 
 
 [FONT=Liberation Sans, sans-serif][SIZE=2]2.  Both networks set to WPA2-PSK / AES.[/SIZE][/FONT]
 
 
 [FONT=Liberation Sans, sans-serif][SIZE=2]3.  Network &#8220;JackAndGill&#8221; set to a fixed channel. Because my router (TP-Link Archer C2) does not seem to allow the user to specify a channel for the guest network, I temporarily disabled the guest network so as to avoid any confusion.[/SIZE][/FONT]
 
 
 [FONT=Liberation Sans, sans-serif][SIZE=2]4.  I executed the code suggested by Hadaka:[/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]sudo iw reg set AU[/SIZE][/FONT]
           [FONT=Liberation Sans, sans-serif][SIZE=2]sudo sed -i 's/=.*/=AU/' /etc/default/crda[/SIZE][/FONT]
   [FONT=Liberation Sans, sans-serif][SIZE=2](I presume this sets the country code to Australia.)[/SIZE][/FONT] 
 
 [FONT=Liberation Sans, sans-serif][SIZE=2]5. Finally poowwered down and restarted both rounter and computer.[/SIZE][/FONT]
 
 
 [FONT=Liberation Sans, sans-serif][SIZE=2]Alas, the unstable wireless connection under kernel 4.10.0 is still unstable. Here are links to the new outputs from the wireless-info scripts:[/SIZE][/FONT]
 
 
 [FONT=Liberation Sans, sans-serif][SIZE=2]4.8.0-49:  [http://paste.ubuntu.com/25361256/](http://paste.ubuntu.com/25361256/)[/SIZE][/FONT]
 
 
 [FONT=Liberation Sans, sans-serif][SIZE=2]4.1.0-32:  [http://paste.ubuntu.com/25361295/](http://paste.ubuntu.com/25361295/)[/SIZE][/FONT]
 
 
 [FONT=Liberation Sans, sans-serif][SIZE=2]I should appreciate any further suggestions![/SIZE][/FONT]

---

### Post by pogona on 2017-11-20
No success with 17.04, but after upgrading to 17.10 , with kernel 4:13, and re-installing Larry Finger's drivers, everything seems to be working well.

---

