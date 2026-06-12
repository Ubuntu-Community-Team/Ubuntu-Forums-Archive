---
title: "installing/downloading linux-backports-modules-karmic for wireless connection"
date: 2015-08-30
forum: Networking &amp; Wireless
---

### Post by funman2 on 2015-08-30
Hello,

I am new to ubuntu (14.04) and my wlan does not work. I have an [COLOR=#333333][FONT=Ubuntu]Intel Ultimate-N 6300 wlan card and I read here 

[/FONT][/COLOR][https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

that I have to install linux-backports-modules-karmic to make my wlan work. Unfortunately the link given in the comments section for the thread to do so does not work (error 404). Searching for this package on my own I found 

[https://wiki.ubuntuusers.de/WLAN/linux-backports-modules](https://wiki.ubuntuusers.de/WLAN/linux-backports-modules)

but the description there does not work. I get the error:

E: Unable to locate package linux-backports-modules-cw-3.6-trusty--generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-3.6-trusty--generic'

Can anyone help me to install this package please?

P.S. I am new to this forum so please feel free to correct me.

---

### Post by chili555 on 2015-08-30
This card should work by default in 14.04:> Intel Ultimate-N 6300Is the driver iwlwifi loaded? From a terminal, run:```
lsmod
```Is iwlwifi listed?

Is the switch set to enable wireless?```
rfkill list all
```Are there any clue in the log?```
dmesg | grep iwl
```The pipe symbol | is on the right side of my keyboard on the same key with \.

---

### Post by funman2 on 2015-08-31
Thanks for the fast response! 

The islwifi is listed:

> iwlwifi               188416  1 iwldvm

Wlan is also not soft/hard blocked:

> 0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


The log is probably more interesting since it contains some errors about the iwlwifi-6000:

> [    3.987397] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    4.030374] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-6.ucode failed with error -2
[    4.030417] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[    4.043823] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[    4.077718] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    4.077724] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    4.077726] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    4.077729] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[    4.077794] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    4.113348] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    5.136482] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    5.136808] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[    5.363175] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    5.363478] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1




I am on this problem for almost a week now and so far no "fix" worked. I think I read somewhere that the iwlwifi-6000 is a driver which is contained in the [COLOR=#000000]linux-backports-modules-karmic package.

But maybe a more detailed description of my problem would help:
The wifi connects to the router but I can't ping the router nor any DNS servers and I get no internet access. I got an IP adress and the DNS is the adress of my router. The wired connection works fine and strangely after I pluged in the wired connection and removed it after some short time the wlan connection has internet access for some time. I can even restart the system and wlan still works but after some time (10-30 min I guess) no Internet access is possible.

I hope this will help.[/COLOR]

---

### Post by Bucky Ball on 2015-08-31
Well, this shows one thing. The card works fine when it's working so avoid the Karmic backports. You don't need them and yes, this should work out of the box and consistently. A matter of figuring why its not. The issue is getting the driver to stick in this configuration and chili555 will almost certainly be able to help you with that when they re-emerge. :)

---

### Post by chili555 on 2015-08-31
> [ 4.030374] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-6.ucode failed with error -2
[ 4.030417] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[ 4.043823] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvmAll this means is that the driver looked for firmware version -6 and didn't find it; it looked for -5 and didn't find it; it looked for -4 and found it, loaded and started.

Installing linux-backports-modules-karmic, suggested by a five year old thread, is like trying to install a Pentium II into your i7 laptop. First, it won't work at all and, even if it did, it would actually *degrade* performance!

I doubt that your issue is the driver or even the firmware. Let's have a look at:```
iwconfig
ifconfig
```

---

### Post by funman2 on 2015-08-31
Ok that makes sense. Here is your data:

iwconfig:

> 
eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"sweet-home"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 18:83:BF:84:A3:74   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:17   Missed beacon:0


lo        no wireless extensions.

ifconfig:

> 
eth0      Link encap:Ethernet  HWaddr f0:de:f1:01:08:2c            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f2400000-f2420000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8356 (8.3 KB)  TX bytes:8356 (8.3 KB)


wlan0     Link encap:Ethernet  HWaddr 00:24:d7:39:57:94  
          inet addr:192.168.1.152  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d7ff:fe39:5794/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14668 (14.6 KB)  TX bytes:22911 (22.9 KB)




I also ran the script mentioned in the sticky. I attached the output. At the section "interfaces" it shows some extra lines to the standard, which origin from a try to fix my problem but did not work. I will try to remove them. I also added some lines to auto turn off my bluetooth at startup.

Thanks for your time!

---

### Post by chili555 on 2015-08-31
Please remove the extra lines from /etc/network/interfaces as you suggested.

Next, I suggest:```
sudo -i
echo "options iwlwifi 11n_disable=8  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Next, download this package: [http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.143.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.143.3_all.deb)

I think it will probably install on your system, although it's originally for 15.04. Please try:```
cd ~/Downloads
```...or wherever you downloaded the package.```
sudo dpkg -i linux-firmware*.deb
```If it balks, we'll get the -5 and -6 firmware another way to see if it helps.

Reboot and let us know if there is any improvement.

---

### Post by funman2 on 2015-08-31
I removed the extra lines and could install the package without error, but the installation was only 3-4 lines in the terminal and it felt somehow too short. Unfortunatly the wlan still can't get any internet connection after reboot (browser can't load pages; can't ping router nor 8.8.8.8).

---

### Post by chili555 on 2015-08-31
Let's see if it installed correctly:```
ls /lib/firmware | grep 6000
```We hope we see:```
iwlwifi-6000-4.ucode
iwlwifi-6000g2a-5.ucode
iwlwifi-6000g2a-6.ucode
iwlwifi-6000g2b-6.ucode

```Are there any clues in the log?```
dmesg | grep -e wlan -e iwl
```

---

### Post by funman2 on 2015-08-31
The package installed correctly, I can see exactly what you expected. The log gives a clue:

> 
[ 3754.326350] wlan0: authenticate with 18:83:bf:84:a3:74[ 3754.329640] wlan0: send auth to 18:83:bf:84:a3:74 (try 1/3)
[ 3754.332139] wlan0: authenticated
[ 3754.336193] wlan0: associate with 18:83:bf:84:a3:74 (try 1/3)
[ 3754.368435] wlan0: RX AssocResp from 18:83:bf:84:a3:74 (capab=0x411 status=0 aid=2)
[ 3754.378638] wlan0: associated
[ 3796.505865] wlan0: deauthenticated from 18:83:bf:84:a3:74 (Reason: 3=DEAUTH_LEAVING)




He does this endlessly. I googled the "Reason: 3=DEAUTH_LEAVING" and found this link:

[http://ubuntuforums.org/showthread.php?t=2259037](http://ubuntuforums.org/showthread.php?t=2259037)

Someone suggested:

> 
[COLOR=#000000][FONT=Ubuntu Mono]sudo iw reg set IN
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
[/FONT][/COLOR]

, but it was not confimed if it worked. Should I try it?

---

### Post by chili555 on 2015-08-31
I doubt you are in India. Moreover, your crda is already set:> Region: Europe/Berlin (based on set time zone)

[COLOR="#FF0000"]country DE[/COLOR]:
	(2400 - 2483 @ 40), (N/A, 20)
	(5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
	(5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
	(5470 - 5725 @ 40), (N/A, 26), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOORAssuming you are actually situated in Germany, then there is nothing to be done there. 

Edit: First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

I believe your CRDA is already set correctly.

Reboot the computer and tell us if there is any improvement.

---

### Post by funman2 on 2015-09-01
Great now my Wifi works! In the router I only had to change to a fixed channel and the 20/40 MHz to the flat 20 MHz setting, the rest was already set as you suggested. I also changed the IPv6 setting. 

The only thing I wonder is whether I it will also work with the University network, since I can't change router settings there. I will try that tomorrow and give you the results.

Thank you very much for your help so far! At least having wlan connection at home is already a big improvement :).

---

### Post by Bucky Ball on 2015-09-01
Good news. Please see the first link in my signature.

If you can't get online at uni the first stop is the uni IT department. The way unis set up their networks varies widely and this often makes it difficult for us to help much. The IT people will be able to give specific advice and support as they are familiar with the uni network setup. :)

If they bring no joy, post a new thread with a descriptive title and as much info as you can muster an see what pops up. Good luck. :D

---

### Post by funman2 on 2015-09-01
Thanks for the advice! :) I marked the thread as solved.

Edit:

P.S.: My university wlan works aswell!! Thank you so much for your help! :)

---

