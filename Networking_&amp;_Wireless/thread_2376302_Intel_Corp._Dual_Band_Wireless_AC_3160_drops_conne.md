---
title: "Intel Corp. Dual Band Wireless AC 3160 drops connection after upgrade to Ubuntu 17"
date: 2017-11-01
forum: Networking &amp; Wireless
---

### Post by makem2 on 2017-11-01
Pastebin successful:

[http://paste.ubuntu.com/25865847/](http://paste.ubuntu.com/25865847/)

Today I upgraded to the latest Ubuntu stable and have had problems. The no keyboard and mouse input has been rectified but I also do not have a stable network connection. It appears to connect and immediately drop constantly.

The network operates correctly in the live instance of Ubuntu which I am now using and in the dual booted windows 10.

As required, I have obtained and posted the results of the wireless script which I obtained whilst in the live system. I hope this is useful but if not I will do as sticky suggests and get the information via a wired connection.

I am able to access the install via chroot if required.

For information, when this wireless issue is solved it will leave remaining problems which appear not related to wireless or input:

1. Error: System program error detected, do you want to report?
2. Multiple instances of Thunderbird
3. Terminal window popping up

I was able in the previous xubuntu, to correct 2 & 3 by renaming the .cache but this time no effect.

Edit:
I have been unable to obtain a wired connection. The wired connection works in the live instance. I will try the instructions in the sticky.

---

### Post by chili555 on 2017-11-01
Do you actually mean:

Intel Corporation Dual Band Wireless AC 3160 dropping connection after upgrade to Ubuntu 17 stable

If so, please edit your post to correct the title so we may better understand.

---

### Post by makem2 on 2017-11-01
> **chili555 said:**
> Do you actually mean:

Intel Corporation Dual Band Wireless AC 3160 dropping connection after upgrade to Ubuntu 17 stable

If so, please edit your post to correct the title so we may better understand.

My apologies. Post title corrected.

I have obtained another output from the wireless-info script whilst in the Ubuntu 17 instance with a not working wired connection. It was obtained by passing the necessary files to the defective system, running it there and passing it back to a live system as no other computer was readily available. I hope this is useful.

[URL="http://paste.ubuntu.com/25866365/"]http://paste.ubuntu.com/25866365/
[/URL]

---

### Post by chili555 on 2017-11-01
I notice that you have your router set to separate 2.4 and 5 gHz segments. That is excellent and is the method I prefer and recommend.

Are you able to easily connect to the 2.4 gHz segment?

How is the 5 gHz segment set up? I recommend 802.11a/n/ac mixed mode. Your Intel should connect at n speeds and if the card and the router agree that conditions are suitable, negotiate to ac. My Intel does so smoothly.

Does your router offer a choice between channel widths, 20- 40- or 80-mHz? Have you tried the narrow as well as the widest channel width?

I recommend that you set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
sudo nano /etc/default/crda
```Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

---

### Post by makem2 on 2017-11-01
I am unable to connect to both 2.4 gHz and 5 gHz segments at the moment but can connect to both in normal circumstances. I am the only one using the 5 gHz, I restrict other users to the 2.4 as they don't need speed. (Actually I don't either!)

I am using the Asuswrt-Merlin firmware.

The 5 gHz segment was set up as 'Auto'. I have further options of: N only, N/AC mixed or legacy. I have changed it to N/AC mixed. I don't know how to check if it negotiates to ac.

The router offers: 20/40/80 MHz, 20, 40 or 80 MHz. It is set at 20/40/80 MHz. I have not tried any other. I will try later if you can tell me how I will know the difference.

My Country code is GB and it is set as such.

I seem to remember being here before. Perhaps you assisted with a Chinese Teclast tablet I had problems finding wireless a driver for? In the end a driver was compiled and I have re-compiled after updates. The tablet is being returned to China.

Ok, having done as requested are we going to approach my current problem?

I said initialy that I was able to chroot into the system but now I get a Segmentation error. I was about to attempt to install a dd backup I made of 16.04, after formatting the sda2 partition. If that failed I intended re-installing 16.04.

All relevant Data partitions for Linux and Windows are regularly backed up to a Raspberry Pi twin drive system so my data is double safe.

Luckily I checked here first!

Edit: I have a live USB of xubuntu 17.01 in addition to the 16.04 one.

---

### Post by chili555 on 2017-11-01
> My Country code is GB and it is set as such.I assume you just set it. It shows as unset in the paste.> I don't know how to check if it negotiates to ac.It ought to give some clues in iwconfig; something like this from your first paste:```
wlp7s0    IEEE 802.11  ESSID:"makem5G"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC 'makem5G' [AC1]>   
          [COLOR="#FF0000"]Bit Rate=433.3 Mb/s  [/COLOR] Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36   Missed beacon:0

```> The router offers: 20/40/80 MHz, 20, 40 or 80 MHz. It is set at 20/40/80 MHz.I would suggest that you try each one separately and reboot the router after each change. You will know because one of the settings will allow a stable connection; or, at least, we hope so. My guess is 20 mHz.> Perhaps you assisted with a Chinese Teclast tablet I had problems finding wireless a driver for?It is very possible. I have tried to help many people in my long (in Linux years!) career both here and at Ask Ubuntu.

---

### Post by makem2 on 2017-11-01
Are you suggesting setting the router to the channel width 20 or 80 may fix my current problem?

> **chili555 said:**
> I assume you just set it. It shows as unset in the paste.It ought to give some clues in iwconfig; something like this from your first paste:```
wlp7s0    IEEE 802.11  ESSID:"makem5G"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC 'makem5G' [AC1]>   
          [COLOR=#FF0000]Bit Rate=433.3 Mb/s  [/COLOR] Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36   Missed beacon:0

```I would suggest that you try each one separately and reboot the router after each change. You will know because one of the settings will allow a stable connection; or, at least, we hope so. My guess is 20 mHz.It is very possible. I have tried to help many people in my long (in Linux years!) career both here and at Ask Ubuntu.


tried 20 and 80 channel width.

Edit: Didn't reboot so ignore (HWMBO is watching streamed TV)

Tried a channel width of 20:

```

xubuntu@xubuntu:~$ iwconfig
wlp7s0    IEEE 802.11  ESSID:"makem5G"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: AC:9E:17:66:5D:5C   
          Bit Rate=86.7 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:97   Missed beacon:0

lo        no wireless extensions.

enp8s0    no wireless extensions.

xubuntu@xubuntu:~$


```

This was done whilst in a live 17.01.

No connection made in 5 gHz whilst in the problem 17.01 instance, although it did allow a disconnect option. It was the same with 2.4. It appeared connected so does this suggest a DNS problem? Perhaps I should have done a cat /etc/resolv.conf whilst in that OS.

EDIT: iwconfig from 17.0 problem install:

```

makem@SSDtosh:~$ iwconfig
enp8s0    no wireless extensions.

lo        no wireless extensions.

wlp7s0    IEEE 802.11  ESSID:"makem5G"  
          Mode:Managed  Frequency:5.24 GHz  Access Point: AC:9E:17:66:5D:5C   
          Bit Rate=86.7 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:12   Missed beacon:0

makem@SSDtosh:~$ 

```

```

root@xubuntu:/# cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search WORKGROUP

nameserver 8.8.8.8
nameserver 208.67.222.222
nameserver 208.67.220.220
root@xubuntu:/#

```

---

### Post by chili555 on 2017-11-01
> It appeared connected so does this suggest a DNS problem? Interesting!! You certainly appear connected:> wlp7s0    IEEE 802.11  ESSID:"makem5G"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: AC:9E:17:66:5D:5C   
          Bit Rate=86.7 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:97   Missed beacon:0Can you ping?```
ping -c3 8.8.8.8
```If so, let's look at:```
sudo resolvconf -u
```


------------

Possible clue: [https://askubuntu.com/questions/966870/dns-not-working-after-upgrade-17-04-to-17-10](https://askubuntu.com/questions/966870/dns-not-working-after-upgrade-17-04-to-17-10)

---

### Post by makem2 on 2017-11-01
> **chili555 said:**
> Interesting!! You certainly appear connected:Can you ping?```
ping -c3 8.8.8.8
```If so, let's look at:```
sudo resolvconf -u
```


------------

Possible clue: [https://askubuntu.com/questions/966870/dns-not-working-after-upgrade-17-04-to-17-10](https://askubuntu.com/questions/966870/dns-not-working-after-upgrade-17-04-to-17-10)

```

makem@SSDtosh:~$ ping -c3 8.8.8.8
connect: Network is unreachable
makem@SSDtosh:~$ sudo resolvconf -u
[sudo] password for makem: 
makem@SSDtosh:~$

```

no ping but I did the resolvconf -u anyway to see what result.

Re. your p0ssible clue url. Iv'e been there today and noted the:

```

sudo resolvconf -u
sudo rm /etc/resolv.conf
sudo ln -s ../run/resolvconf/resolv.conf /etc/resolv.conf
systemctl restart resolvconf

```

for future reference if you were time restricted and not able to help.

---

### Post by jeremy31 on 2017-11-02
I wonder if power management is causing this
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

---

### Post by makem2 on 2017-11-02
I have tried both methods in the link provided above but neither work.

I will try the power management.

> **jeremy31 said:**
> I wonder if power management is causing this
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```

```

makem@SSDtosh:~$ sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
[sudo] password for makem: 
makem@SSDtosh:~$ systemctl restart network-manager.service
makem@SSDtosh:~$

```

The symptoms of no stable connection remain.

The wireless icon spins and while doing so the error message of no connection appears. That goes away for less than a second while the icon continues spinning then the error message returns.

During that time the wireless connection menu shows an automatic connection has been achieved and gives the opportunity to disconnect. If I choose to disconnect, it does so and the connection icon turns to the two arrows. Choosing one of the available connections restarts the unstable connection.

This transpires with both available connections.

---

### Post by chili555 on 2017-11-02
> The network operates correctly in the live instance of Ubuntu Puzzling...

In the live instance, does it load the same firmware version?```
dmesg | grep -i firm
```In your currently installed version, have you been able to do:```
sudo apt update && sudo apt -y upgrade
```...followed by a reboot? 

Can you please compare these readings from both the installed and live versions?```
dmesg | grep iwl
```As they will be lengthy, please: [http://paste.ubuntu.com](http://paste.ubuntu.com)

---

### Post by makem2 on 2017-11-02
> **chili555 said:**
> Puzzling...

In the live instance, does it load the same firmware version?```
dmesg | grep -i firm
```In your currently installed version, have you been able to do:```
sudo apt update && sudo apt -y upgrade
```...followed by a reboot? 

Can you please compare these readings from both the installed and live versions?```
dmesg | grep iwl
```As they will be lengthy, please: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Results from the live instance:

```

xubuntu@xubuntu:~$ dmesg | grep -i firm
[    6.443173] psmouse serio2: elantech: assuming hardware version 4 (with firmware version 0x5e1f02)
[    7.519535] [Firmware Bug]: ACPI(PXSX) defines _DOD but not _DOS
[   16.159766] iwlwifi 0000:07:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
xubuntu@xubuntu:~$ 

```

```

xubuntu@xubuntu:~$ dmesg | grep iwl
[   16.159766] iwlwifi 0000:07:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[   16.264235] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[   16.266544] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   16.267474] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   16.447082] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   17.381242] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
[   17.780317] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   17.780985] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   17.908338] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[   17.908836] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
xubuntu@xubuntu:~$


```

The result from dmesg | grep iwl was not long so I post here. I hope this is acceptable.

I will obtain the results from the installed system and post again.

Thank you for bearing with me.

---

### Post by makem2 on 2017-11-02
> **chili555 said:**
> Puzzling...

In the live instance, does it load the same firmware version?```
dmesg | grep -i firm
```In your currently installed version, have you been able to do:```
sudo apt update && sudo apt -y upgrade
```...followed by a reboot? 

Can you please compare these readings from both the installed and live versions?```
dmesg | grep iwl
```As they will be lengthy, please: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Attempt to install pastebinit:

```

makem@SSDtosh:~$ sudo apt-get install pastebinit
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
makem@SSDtosh:~$

```

Result of update:

```

makem@SSDtosh:~$ sudo apt update && sudo apt -y upgrade
[sudo] password for makem: 
Err:1 http://gb.archive.ubuntu.com/ubuntu zesty InRelease
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err:2 http://security.ubuntu.com/ubuntu zesty-security InRelease
  Could not resolve &#8216;security.ubuntu.com&#8217;
Err:3 http://gb.archive.ubuntu.com/ubuntu zesty-updates InRelease
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Err:4 http://gb.archive.ubuntu.com/ubuntu zesty-backports InRelease
  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/zesty/InRelease  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/zesty-updates/InRelease  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/zesty-backports/InRelease  Could not resolve &#8216;gb.archive.ubuntu.com&#8217;
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/zesty-security/InRelease  Could not resolve &#8216;security.ubuntu.com&#8217;
W: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
makem@SSDtosh:~$

```

Following a reboot I had a working internet connection and am using the installed OS currently.

The reboot took much longer than normal for grub to appear.

At the login screen I entered my password and pressed enter. Nothing happened and the system appeared hung, however after maybe 1 minute it began to start opening the desktop. When the desktop opened fully an empty terminal window appeared. Later Thunderbird appeared.

Prior to the reboot I had saved the results that were requested above so went to install pastebinit. The menu tree opened normally and I selected synaptic package manager which was in my favourites with the result shown at the start of this post. Ubuntu package manager was missing from my favourites so I had to scroll to get to it. Scrolling was very hesitant, stopping at times and it took several attempts to get there. It opened, eventually and after a few seconds I was able to type in the search box. This showed pastebinit already installed. When I later attempted to open the ubuntu menu it opened but was blank. I closed it and opened again. This time it opened correctly.

The system works but is very and I mean very, slow. It appears something is going on in the background - related to the, "E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it"? There are other typing problems.

Result of dmesg | grep iwl from installed OS:

[http://paste.ubuntu.com/25873041/](http://paste.ubuntu.com/25873041/)

EDIT: I forgot to mention that this web page took a long time to load - a reflection on the connection speed?

---

### Post by makem2 on 2017-11-02
Connection lost!

After another reboot, the connection problem had returned with exactly the same symptoms.

In addition to that I was receiving multiple errors the first few lines of which are:

ExcutablePath
/sbin/dhclient

Package
isc-dhcp-client 4.3.5-3ubuntu1

ProblemType
Crash

Title
dhclient crashed with SIGSEGV in_strcasecmp_1_avx()

ApportVersion
2.20.4-0ubuntu4.5

I accepted the request for a report and am now back in the live OS. :-(

The only beneficial changes were that boot up time was normal as was the sign-in and response time and using the desktop appeared normal.

I am concerned at the time and effort being put into this and while it is much appreciated,  would understand if it was suggested to revert to the previous version. However, if anyone wants to continue I am willing for a reasonable length of time.

---

### Post by chili555 on 2017-11-02
From the live session:> iwlwifi 0000:07:00.0: loaded firmware version 17.[COLOR="#FF0000"]352738.0[/COLOR] op_mode iwlmvmNow from the installed version:> iwlwifi 0000:07:00.0: loaded firmware version 17.[COLOR="#FF0000"]459231.0[/COLOR] op_mode iwlmvmWhatt...?? I was unaware that there were more than one version of the -17 firmware! These are from the exact same physical machine, correct?

May we see, from each instance:```
ls -al /lib/firmware | grep 3160
```In my case, it yields:```
-rw-r--r--  1 root root  609892 Mar 29  2017 iwlwifi-3160-10.ucode
-rw-r--r--  1 root root  683996 Mar 29  2017 iwlwifi-3160-12.ucode
-rw-r--r--  1 root root  688616 Mar 29  2017 iwlwifi-3160-13.ucode
-rw-r--r--  1 root root  918212 Mar 29  2017 iwlwifi-3160-16.ucode
[COLOR="#FF0000"]-rw-r--r--  1 root root  918268 Jun  8 12:48 iwlwifi-3160-17.ucode[/COLOR]
-rw-r--r--  1 root root  670484 Mar 29  2017 iwlwifi-3160-7.ucode
-rw-r--r--  1 root root  667284 Mar 29  2017 iwlwifi-3160-8.ucode
-rw-r--r--  1 root root  669872 Mar 29  2017 iwlwifi-3160-9.ucode

```I assume the highlighted file is what is loading. Please notice that it is newer than the other files. That's why I thought an update might be helpful.

As for the attempted update:> $ sudo apt update && sudo apt -y upgrade
[sudo] password for makem: 
Err:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty InRelease
  Could not resolve ‘gb.archive.ubuntu.com’
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease
  Could not resolve ‘security.ubuntu.com’
Err:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty-updates InRelease
  Could not resolve ‘gb.archive.ubuntu.com’
Err:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) zesty-backports InRelease
  Could not resolve ‘gb.archive.ubuntu.com’This suggests that you did not have a working internet connection at the time. Yes? It will be needed.

I am willing to continue as long as needed. If you are getting impatient, then revert and try again in a few weeks; however, I am unaware of any bugs or problems systemically that prevent smooth connection with any Intel.

---

### Post by makem2 on 2017-11-02
Wait!

I thought we were trying to find why the wireless wasn't working and was using 16.04 at that time. Later I was curious and tried making a 17.01 usb  but all the time have used 16 as live for what we were doing.

Do you want me to do the tests again with 17 this time?

---

### Post by makem2 on 2017-11-02
From a live session of 17:

```

xubuntu@xubuntu:~$ dmesg | grep iwl
[   17.274580] iwlwifi 0000:07:00.0: loaded firmware version 17.459231.0 op_mode iwlmvm
[   17.511045] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[   17.531928] iwlwifi 0000:07:00.0: base HW address: 34:e6:ad:ba:1f:d0
[   17.685853] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   17.965191] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
xubuntu@xubuntu:~$

```

```

xubuntu@xubuntu:~$ ls -al /lib/firmware | grep 3160
-rw-r--r--  1 root root  609892 Mar 30  2017 iwlwifi-3160-10.ucode
-rw-r--r--  1 root root  683996 Mar 30  2017 iwlwifi-3160-12.ucode
-rw-r--r--  1 root root  688616 Mar 30  2017 iwlwifi-3160-13.ucode
-rw-r--r--  1 root root  918212 Mar 30  2017 iwlwifi-3160-16.ucode
-rw-r--r--  1 root root  918268 Jun  8 16:48 iwlwifi-3160-17.ucode
-rw-r--r--  1 root root  670484 Mar 30  2017 iwlwifi-3160-7.ucode
-rw-r--r--  1 root root  667284 Mar 30  2017 iwlwifi-3160-8.ucode
-rw-r--r--  1 root root  669872 Mar 30  2017 iwlwifi-3160-9.ucode
xubuntu@xubuntu:~$

```

I did not have a working internet connection at the time of the update but went ahead.

I will stay with the 17 live session now that I know it affects the wireless results. Somewhere we have got crossed wires. Sorry. Please continue.

EDIT: Reading back I can see how the crossed wires occurred. Every test was done in the installed 17, so, until you asked for a comparison the fact that I was using 16 live was unknown to you.

```

xubuntu@xubuntu:~$ dmesg | grep -i firm
[    0.000000] [Firmware Bug]: TSC_DEADLINE disabled due to Errata; please update microcode to version: 0x25 (or later)
[    7.560239] psmouse serio2: elantech: assuming hardware version 4 (with firmware version 0x5e1f02)
[    8.631959] [Firmware Bug]: ACPI(PXSX) defines _DOD but not _DOS
[   16.933337] iwlwifi 0000:07:00.0: loaded firmware version 17.459231.0 op_mode iwlmvm
xubuntu@xubuntu:~$ 

```

---

### Post by makem2 on 2017-11-02
From installed 17:

```

makem@SSDtosh:~$ ls -al /lib/firmware | grep 3160
-rw-r--r--  1 root root  609892 Mar 30  2017 iwlwifi-3160-10.ucode
-rw-r--r--  1 root root  683996 Mar 30  2017 iwlwifi-3160-12.ucode
-rw-r--r--  1 root root  688616 Mar 30  2017 iwlwifi-3160-13.ucode
-rw-r--r--  1 root root  918212 Mar 30  2017 iwlwifi-3160-16.ucode
-rw-r--r--  1 root root  918268 Jun  8 17:48 iwlwifi-3160-17.ucode
-rw-r--r--  1 root root  670484 Mar 30  2017 iwlwifi-3160-7.ucode
-rw-r--r--  1 root root  667284 Mar 30  2017 iwlwifi-3160-8.ucode
-rw-r--r--  1 root root  669872 Mar 30  2017 iwlwifi-3160-9.ucode
makem@SSDtosh:~$

```

```

makem@SSDtosh:~$ dmesg | grep iwl
[    7.650550] iwlwifi 0000:07:00.0: loaded firmware version 17.459231.0 op_mode iwlmvm
[    7.676001] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    7.678981] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    7.679705] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    7.816136] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    7.905812] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
[    9.652884] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    9.653386] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    9.781186] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    9.781685] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    9.815333] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    9.815836] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    9.951010] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    9.951668] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
makem@SSDtosh:~$

```

---

### Post by makem2 on 2017-11-03
After rebooting my laptop for the first time today I had a stable internet connection.

The reboot was slow and windows opened blank to be filled in soon after. This improved slowly. CPU usage was 1 to 3% and only a few MB or the 12 GB memory used.

I used the computer for an hour or so without problems except web pages seemed rather slow loading.

Taking advantage of having a connection, I performed the following in the order given:

iwconfig


sudo apt-get clean && sudo apt-get update


dmesg | grep iwl


sudo apt update && sudo apt -y upgrade

Each completed successfully.

Results from the above are posted here:

[http://paste.ubuntu.com/25879953/](http://paste.ubuntu.com/25879953/)

I rebooted and then did not have an internet connection. The connection was made but not connected as before with disconnect messages. I had system error messages as previously.

I rebooted and had an stable internet connection but everything seemed slower than previous. I rebooted and lost the internet connection but things seemed quicker. A further reboot brought the connection back but still apparently slow.

At each reboot there are messages and file checking going on before login which may be of assistance.

```

makem@SSDtosh:~$ iwconfig
lo        no wireless extensions.


wlp7s0    IEEE 802.11  ESSID:"makem5G"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: AC:9E:17:66:5D:5C   
          Bit Rate=86.7 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:124   Missed beacon:0


enp8s0    no wireless extensions.


makem@SSDtosh:~$

```

I have a 50 MB cable connection and have previously seen 400+ Mb/s

EDIT: Wireless info:

[http://paste.ubuntu.com/25880064/](http://paste.ubuntu.com/25880064/)

Getting numerous errors in dmesg:

[http://paste.ubuntu.com/25880363/](http://paste.ubuntu.com/25880363/)

---

### Post by chili555 on 2017-11-03
The errors you see in dmesg are very interesting; here is a snip:

[COLOR="#FF0000"]cupsd[/COLOR][1169]: segfault at 0 ip 00007f6bbc212715 sp 00007ffd7bcffee8 [COLOR="#FF0000"]error 4 in libc-2.24.so[/COLOR][7f6bbc0c5000+1be000]
[COLOR="#FF0000"]ntpd[/COLOR][1304]: segfault at 0 ip 00007f3085dfc715 sp 00007ffd656b96d8[COLOR="#FF0000"] error 4 in libc-2.24.so[/COLOR][7f3085caf000+1be000]
[COLOR="#FF0000"]dhclient[/COLOR][1724]: segfault at 0 ip 00007fec3fd0b715 sp 00007ffcff5ee378[COLOR="#FF0000"] error 4 in libc-2.24.so[/COLOR][7fec3fbbe000+1be000]

All of these are networking related. I am somewhat suspicious that at least the dhclient part stops connection. dhclient is the process that says, very roughly, to your router, "I have the SSID name and the WPA2 password, may I please have a DHCP lease? Please, oh please??" A DHCP lease gives your computer an IP address, DNS nameservers and access to the connected WAN; namely, the internet.

Just when you need dhclient the most, it crashes (segfault). 

Unfortunately, I haven't any ideas as to what can be done to fix it. I suggest that you ask the question here: [https://askubuntu.com/questions](https://askubuntu.com/questions) and here: [https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331) I suggest that you refer in the title to error 4 in libc-2.24.

I wish I had a better solution.

---

### Post by makem2 on 2017-11-03
The DNS addresses are fixed in each pc.

I cannot see the point in trying to fix this when there are many errors. I think it best to install a fresh install on 17.

Do you agree that as the system works live it would work with a fresh install, or better to back to 16 until later?

---

### Post by chili555 on 2017-11-03
> Do you agree that as the system works live it would work with a fresh install,Yes, that's what I'd if it were me.

---

### Post by makem2 on 2017-11-03
Ok, I reinstalled 16 and have everything back. However and this involves you I think.

I have a stable full speed internet connection but.....................the icon indicating that is the two arrows which suggest no connection!!!!

It fooled me for a while but I checked the router and saw I was connected.

Any ideas how I can clear up this annoyance?

EDIT: Now I find from wireless properties that makem5G 1 was connected 4 minutes ago; makem5G 2 never connected and wired connection 14 minutes ago.

All is untrue. IAM connected to maken5G and have not connected to ethernet today.

After a reboot the icon has returned to normal. panic? over thank you.

---

