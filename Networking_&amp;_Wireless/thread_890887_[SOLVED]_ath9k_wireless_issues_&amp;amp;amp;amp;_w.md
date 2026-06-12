---
title: "[SOLVED] ath9k wireless issues &amp;amp;amp;amp; wicd"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by TDragon on 2008-08-15
[FONT=Arial][SIZE=2]I've been trying to get my system to work w/ the ath9k driver to work from this thread, [http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097). Since this was primarily a Mac thread, I decided to open one here to catch the attention of a greater audience.

Let me give you some background:
[/SIZE][/FONT]  
[LIST]
[*][FONT=Arial][SIZE=2]I'm using the latest version of Ubuntu w/ th[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]e [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black]v2.6.24-21[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=Black] ke[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2]rnel.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]I have already tried ndiswrapper - which led to OS issues & a fresh install of the OS[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]I have tried the madwifi driver - got sick of the random wifi drops and the need to reinitialize the driver. Was able to get onto the internet.
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]I've installed wicd to attempt to improve the reliability of the wireless w/ WPA.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]DNS is configured to use the OpenDNS service.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]I lowered the MTU of my router to under 1500, which I read may help in another thread. Hasn't helped much.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Wireless Card: D-Link DWA-552[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Router: D-Link DGL-4500. Set at: 2.4GHz, [/SIZE][/FONT][FONT=Arial][SIZE=2]802.11 b/g/n, 2.4ghz (5GHz @ 802.11a are disabled; not simultaneous bands) **WPA-Personal 1 & 2, AES & TKIP (For compatibility reasons w/ other devices)**.
[/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=2]After reading about this being a more pure form of the ath9k driver that can actually support 802.11a through 802.11n, I decided to install it.

Here's where it gets weird, driver works, but under the 3rd-party drivers control panel, it is unchecked even though it states "in use". When I attempt to get the box to stay checked, the OS crashes. So, I leave it be.

I can see local wireless networks, including my own, and when I attempt to connect to the network w/ the correct settings, it will say that its trying to get an IP address and then fails (times out). I've even attempted to connect w/ static IP settings and the connection times out.

Now, I have noticed that the Network control panel still exists. If this is related to the network-manager app, it could be causing a conflict.

Currently, I'm stuck with wired and I would like to move my desktop back to the remote part of my house where I originally had it. Addidionally, D-Link has released new firmware for the router. So, I'm going to see if it makes a difference.[/SIZE][/FONT]

---

### Post by TDragon on 2008-08-15
*** bump ***

---

### Post by TDragon on 2008-08-16
*** bump ***

---

### Post by CupricReki on 2008-08-16
im sorry to ask a question in here, but it seems like your the one to ask, my drivers wont read my card, but i notice when making the MAKE file i get this error:

WARNING: you are running a kernel >= 2.6.23, you should enable in it CONFIG_NETDEVICES_MULTIQUEUE for 802.11[ne] support


what does this mean i should do?

---

### Post by TDragon on 2008-08-16
> **CupricReki said:**
> im sorry to ask a question in here, but it seems like your the one to ask, my drivers wont read my card, but i notice when making the MAKE file i get this error:

WARNING: you are running a kernel >= 2.6.23, you should enable in it CONFIG_NETDEVICES_MULTIQUEUE for 802.11[ne] support


what does this mean i should do?


If you are running the driver set I'm talking about, it is compiled to work with the latest kernel, 2.6.24. Go to System > Administration > Update Manager and download all of the latest updates (which should put you at 2.6.24). However, you will not get the absolute latest kernel, 2.6.24-21, w/o enabling all of the install sources, etc.

---

### Post by ktechman on 2008-08-16
TDragon, would you happen to know if the ath5k driver, from MadWifi, would give me any wireless on the AR9281 chipset?

---

### Post by TDragon on 2008-08-16
> **ktechman said:**
> TDragon, would you happen to know if the ath5k driver, from MadWifi, would give me any wireless on the AR9281 chipset?
 
 
According to the [MadWifi]("http://madwifi.org/") site, the following are supported in the **ath5k** driver:
[INDENT]
MAC chips
[LIST]
[*]AR5210
[*]AR5211
[*]AR5212
[/LIST]PHY chips
[LIST]
[*]RF5110
[*]RF5111/2111
[*]RF5112/2112
[*]RF2413
[*]RF5413
[*]RF2425
[/LIST]
[/INDENT]In the **ath9k** driver, the following are supported:
[INDENT]
[LIST]
[*]AR5418+AR5133
[*]AR5416+AR5133
[*]AR5416+AR2133
[*]AR9160
[*]AR9280
[*]**[COLOR=red]AR9281[/COLOR]**
[/LIST]
[/INDENT]

---

### Post by ktechman on 2008-08-16
Am I dead in the water?

---

### Post by TDragon on 2008-08-16
> **ktechman said:**
> Am I dead in the water?

No, just use the ath9k driver for your chipset.



Check this post out: [http://ubuntuforums.org/showpost.php?p=5597068&postcount=49](http://ubuntuforums.org/showpost.php?p=5597068&postcount=49)

In fact, it just worked for me. Also, make sure you are using the wext WPA driver with it, this is easily done in the wicd connection program.

---

### Post by ktechman on 2008-08-16
I see the directions you pointed me to but some of the steps are missing for complete noobes like myself.  Can you help? 
I see it now it is unpacking and installing....

---

### Post by ktechman on 2008-08-16
TDragon I get this output with "iwconfig" what gives? 

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Green"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
The wireless network is not being detected by "Wicd"

Thanks for your help.

I ran this code as root

Run:

iwpriv wlan0 network_type g
iwconfig wlan0 essid "any"
ifconfig wlan0 up
iwlist wlan0 scan

and received this result

```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:01:91:30:64
                    ESSID:"Green"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=103/100  Signal level:-29 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003fc41ac49e
                    Extra: Last beacon: 212ms ago

```

But I am still confused why isn't my wireless up if it sees the network?

---

### Post by CupricReki on 2008-08-16
Well thanks alot for your help, but i dont understand what i have to do for it to "install from all sources". I dont see an option for that. Also, i updated what i could (to 2.6.24-19), and now the driver is being read, and when i run this command:
lshw -C network
i get this:
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=168

Does this mean it is reading my PCI card, whats the next step here?

---

### Post by ktechman on 2008-08-16
In reply to the ? Install from all sources navigate to System>Administration>Software Sources when prompted enter your password and on the "Updates" tab check all of the "Ubuntu Updates"
check boxes then reload and don't forget to add the new source just as it is listed.  As far as the super-user ? just run this  ```
sudo su
```and enter your password when prompted.

                  Cheers

PS You need Kernel 2.6.24-21

---

