---
title: "Ubuntu 22.04 - RTL8821CE 802.11ac PCIe Wireless Network Adapter"
date: 2023-09-12
forum: Networking &amp; Wireless
---

### Post by ScorpioTiger on 2023-09-12
I've purchased a new all-in-one and rebuilt it as dual-boot Windows 10 and Ubuntu 22.04.

At the time of install, I couldn't get the WiFi to connect, so the install was done offline.

It appears that I'm missing some drivers or config somewhere as I have issues with the back-light brightness configuration not working, the WiFi dropping every few seconds, and the Ethernet is not working at all.

This post focuses on the Wifi, but wanted to make everyone aware that this is not the only issue, and there could be something underlying all of the issues I'm having.

I am able to connect to WiFi and browse the internet, however it stops working every few seconds and I can only load a page about half the time. Curiously if I have an SSH session open, it stays open through this (though unusable as keystrokes aren't transmitted). On a different machine on 18.04, a dropped WiFi connection resulted in a terminated session. I don't know if this is something in my config that persists sessions, so this observation might not be relevant.

I've tried disabling the power saving as has been suggested on various forums, but this make no difference.

I tried specifying a driver in the Additional Drivers dialog. Again, this doesn't make any difference.

I've tried [HTML]sudo ubuntu-drivers autoinstall[/HTML], but it says "All the available drivers are already installed."

Output from the wireless info script attached:
[ATTACH]292710[/ATTACH]

---

### Post by chili555 on 2023-09-13
You may find some helpful suggestions here: [https://askubuntu.com/questions/1032703/wi-fi-frequently-disconnecting-timeout/1353723#1353723](https://askubuntu.com/questions/1032703/wi-fi-frequently-disconnecting-timeout/1353723#1353723)

---

### Post by ScorpioTiger on 2023-09-13
> **chili555 said:**
> You may find some helpful suggestions here: [https://askubuntu.com/questions/1032703/wi-fi-frequently-disconnecting-timeout/1353723#1353723](https://askubuntu.com/questions/1032703/wi-fi-frequently-disconnecting-timeout/1353723#1353723)

I'd already tried that. Didn't make a difference.

I should also add that i don't have control over the router, so I can't change any config there. The same WiFi works for a laptop with Ubuntu 18.04 and an Android mobile, so I'm sure that the problem is at my end on this new PC.

---

### Post by chili555 on 2023-09-13
I'd check to see if the wireless is roaming from the 2.4 gHz segment to the 5 gHz segment of the router by checking the message log. First, find the name of your wireless interface:

```
iwconfig
```

It will probably be something like wlpxxx or wloxxx. Then search the log for the interface name you found:

```
sudo dmesg | grep wlp3s0  
```
Of course, substitue your interface name if not wlp3s0.

You might also find some interesting clues looking at the driver name:
```
sudo dmesg | grep -i 8821c
```

Look for disconnects from one MAC address like 12:34:56:99 to try to reconnect to 12:34:56:98. Consecutive numbers almost always signify the 2.4 gHz and the 5gHz segments of the same router. If that's the case, bind Network Manager to the 5gHz segment by its MAC address like this: [https://askubuntu.com/questions/1084033/wifi-on-dell-xps-9560-is-unstable-and-drops-frequently/1084046#1084046](https://askubuntu.com/questions/1084033/wifi-on-dell-xps-9560-is-unstable-and-drops-frequently/1084046#1084046)

---

### Post by ScorpioTiger on 2023-09-15
Thanks for the guidance. 

[HTML]sudo dmesg | grep wlp1s0[/HTML]

Gives me repeating output like below. The following occurred over a short space of time;

[ 1438.166548] wlp1s0: associating to AP 88:d7:f6:80:24:ec with corrupt probe response
[ 1438.168171] wlp1s0: associate with 88:d7:f6:80:24:ec (try 1/3)
[ 1438.176951] wlp1s0: RX AssocResp from 88:d7:f6:80:24:ec (capab=0xc31 status=0 aid=1)
[ 1438.177257] wlp1s0: associated
[ 1483.068820] wlp1s0: deauthenticating from 88:d7:f6:80:24:ec by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1491.989139] wlp1s0: authenticate with 88:d7:f6:80:24:ec
[ 1492.636174] wlp1s0: send auth to 88:d7:f6:80:24:ec (try 1/3)
[ 1492.638343] wlp1s0: authenticated
[ 1492.638599] wlp1s0: associating to AP 88:d7:f6:80:24:ec with corrupt probe response
[ 1492.640170] wlp1s0: associate with 88:d7:f6:80:24:ec (try 1/3)
[ 1492.652010] wlp1s0: RX AssocResp from 88:d7:f6:80:24:ec (capab=0xc31 status=0 aid=1)
[ 1492.652343] wlp1s0: associated
[ 1529.537447] wlp1s0: authenticate with 88:d7:f6:80:24:ec
[ 1530.184169] wlp1s0: send auth to 88:d7:f6:80:24:ec (try 1/3)
[ 1530.188172] wlp1s0: authenticated
[ 1530.188373] wlp1s0: associating to AP 88:d7:f6:80:24:ec with corrupt probe response
[ 1530.192179] wlp1s0: associate with 88:d7:f6:80:24:ec (try 1/3)
[ 1530.197786] wlp1s0: RX AssocResp from 88:d7:f6:80:24:ec (capab=0xc31 status=0 aid=1)
[ 1530.198093] wlp1s0: associated
[ 1575.105015] wlp1s0: deauthenticating from 88:d7:f6:80:24:ec by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1583.989145] wlp1s0: authenticate with 88:d7:f6:80:24:ec
[ 1584.636169] wlp1s0: send auth to 88:d7:f6:80:24:ec (try 1/3)
[ 1584.637893] wlp1s0: authenticated
[ 1584.638059] wlp1s0: associating to AP 88:d7:f6:80:24:ec with corrupt probe response
[ 1584.644206] wlp1s0: associate with 88:d7:f6:80:24:ec (try 1/3)
[ 1584.649805] wlp1s0: RX AssocResp from 88:d7:f6:80:24:ec (capab=0xc31 status=0 aid=1)
[ 1584.650122] wlp1s0: associated
[ 1985.525450] wlp1s0: authenticate with 88:d7:f6:80:24:ec
[ 1986.172151] wlp1s0: send auth to 88:d7:f6:80:24:ec (try 1/3)
[ 1986.177287] wlp1s0: authenticated
[ 1986.177576] wlp1s0: associating to AP 88:d7:f6:80:24:ec with corrupt probe response
[ 1986.184126] wlp1s0: associate with 88:d7:f6:80:24:ec (try 1/3)
[ 1986.191716] wlp1s0: RX AssocResp from 88:d7:f6:80:24:ec (capab=0xc31 status=0 aid=1)
[ 1986.192019] wlp1s0: associated
[ 2031.088679] wlp1s0: deauthenticating from 88:d7:f6:80:24:ec by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2039.985247] wlp1s0: authenticate with 88:d7:f6:80:24:ec
[ 2040.632141] wlp1s0: send auth to 88:d7:f6:80:24:ec (try 1/3)
[ 2040.634160] wlp1s0: authenticated
[ 2040.634461] wlp1s0: associating to AP 88:d7:f6:80:24:ec with corrupt probe response
[ 2040.636108] wlp1s0: associate with 88:d7:f6:80:24:ec (try 1/3)
[ 2040.641695] wlp1s0: RX AssocResp from 88:d7:f6:80:24:ec (capab=0xc31 status=0 aid=1)
[ 2040.641999] wlp1s0: associated

---

### Post by chili555 on 2023-09-15
> associating to AP 88:xxxx:ec with corrupt probe responseI am very worried about this.
> I should also add that i don't have control over the router, so I can't change any config there. And I'm very sorry about this.

A google search for 'associating to AP with corrupt probe response' yields all kinds of answers, some of which suggest that the router is not operating properly, needs a firmware update, etc. Some suggest that the encryption method is wrong, usually the deprecated and insecure TKIP, and more. I suspect it is the 2.4 gHz vs. 5 gHz issue I pointed out before, auto channel select and the bizarre name of the network: >>>FULAY<<<. I am puzzled that it seems to work properly in Ubuntu 18.04.

I think there are two things we might try. First, try a live session of Ubuntu 20.04 LTS with an older kernel (by default) and see if it works. If so, install it. Second, we could try the later and, I assume, newer driver version from here: [https://github.com/lwfinger/rtw88](https://github.com/lwfinger/rtw88) 

If you'd like to try the latter, I'll be happy to provide a step-by-step.

---

### Post by ScorpioTiger on 2023-09-16
I've just tried with the ubuntu 20.04 on USB as you've suggested. I get the same result. Looking at a sample of output from [COLOR=#000000][FONT=&quot]sudo dmesg | grep wlp3s0[/FONT][/COLOR], it's cycling on average every 36 seconds. I ran the same on my Ubuntu 18.04 laptop and the same cycle is there, but the average is 16870 seconds.

I should also add, that if I boot to Windows 10 on the same machine, the Wifi is fine, so I think we can discount dodgy hardware.

It's also worth noting that I can't connect Ethernet either. I don't know if it could be related.

---

### Post by chili555 on 2023-09-16
I suggest that we try the newer driver. With a reliable internet connection, open a terminal and do:

```
sudo apt update
sudo apt install --reinstall git bc build-essential
git clone [https://github.com/lwfinger/rtw88.git](https://github.com/lwfinger/rtw88.git)
cd rtw88
make -j4
sudo -i
make install
echo "blacklist rtw88_8821ce" >>  /etc/modprobe.d/blacklist.conf
exit
```

Reboot. Is there any improvement?

---

### Post by ScorpioTiger on 2023-09-16
It's still going through the same cycle, though the frequency is slightly less; not significantly so however.

It might only be anecdotal; but it seems as though it doesn't happen as much if I'm actively using the connection; ie; not more than a few seconds between requests.

---

### Post by chili555 on 2023-09-16
Is there anything in the log about firmware?

```
sudo dmesg | grep -e rtw -e firm
```

---

### Post by ScorpioTiger on 2023-09-16
sudo dmesg | grep -e rtw -e firm
[    0.133491] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    3.043621] rtw_core: loading out-of-tree module taints kernel.
[    3.043833] rtw_core: module verification failed: signature and/or required key missing - tainting kernel
[    3.143611] rtw_8821ce 0000:01:00.0: enabling device (0100 -> 0103)
[    3.159811] rtw_8821ce 0000:01:00.0: Firmware version 24.11.0, H2C version 12
[    3.571384] rtw_8821ce 0000:01:00.0 wlp1s0: renamed from wlan0
[   40.652251] rtw_8821ce 0000:01:00.0: timed out to flush queue 1
[   41.168233] rtw_8821ce 0000:01:00.0: timed out to flush queue 1
[   44.992258] rtw_8821ce 0000:01:00.0: timed out to flush queue 1
[   46.196224] rtw_8821ce 0000:01:00.0: timed out to flush queue 1
[ 1662.188321] rtw_8821ce 0000:01:00.0: timed out to flush queue 1
[ 4227.208433] rtw_8821ce 0000:01:00.0: timed out to flush queue 1
[ 4285.172440] rtw_8821ce 0000:01:00.0: timed out to flush queue 1
[ 5833.620479] rtw_8821ce 0000:01:00.0: failed to get tx report from firmware

---

### Post by chili555 on 2023-09-16
Please try:

```
sudo -i
echo "options rtw_pci disable_aspm=Y"  >  /etc/modprobe.d/rtw_pci.conf
sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
exit
```

Reboot and tell us if there is any improvement.

---

### Post by ScorpioTiger on 2023-09-18
Tried it. No change.

Really out of my league on this one.

I'm going to take the PC somewhere else and try another WiFi. Will post the result.

---

### Post by ScorpioTiger on 2023-09-19
Ok. I've tried with another WiFi and I'm getting a much better result. I have better connectivity, but it seems to be frequently reauthenticating. I don't know if this is normal or not.

The question still remains of how I can stay connected to the WiFi where I am. Physically carrying the PC to a cafe every time I want to do something isn't a preferred solution.

Does the output below shed any light?

sudo dmesg | grep wlp1s0 
[    3.718272] rtw_8821ce 0000:01:00.0 wlp1s0: renamed from wlan0
[  103.666552] wlp1s0: authenticate with 20:25:64:11:3c:15
[  104.312281] wlp1s0: send auth to 20:25:64:11:3c:15 (try 1/3)
[  104.313996] wlp1s0: authenticated
[  104.316234] wlp1s0: associate with 20:25:64:11:3c:15 (try 1/3)
[  104.321858] wlp1s0: RX AssocResp from 20:25:64:11:3c:15 (capab=0x411 status=0 aid=6)
[  104.322175] wlp1s0: associated
[  104.428433] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[  238.742131] wlp1s0: deauthenticated from 20:25:64:11:3c:15 (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[  239.412547] wlp1s0: authenticate with 20:25:64:11:3c:15
[  240.060329] wlp1s0: send auth to 20:25:64:11:3c:15 (try 1/3)
[  240.061982] wlp1s0: authenticated
[  240.064273] wlp1s0: associate with 20:25:64:11:3c:15 (try 1/3)
[  240.069213] wlp1s0: RX AssocResp from 20:25:64:11:3c:15 (capab=0x411 status=0 aid=6)
[  240.069535] wlp1s0: associated
[  389.596728] wlp1s0: authenticate with 20:25:64:11:3c:15
[  390.240300] wlp1s0: send auth to 20:25:64:11:3c:15 (try 1/3)
[  390.242133] wlp1s0: authenticated
[  390.244289] wlp1s0: associate with 20:25:64:11:3c:15 (try 1/3)
[  390.252446] wlp1s0: RX AssocResp from 20:25:64:11:3c:15 (capab=0x411 status=0 aid=6)
[  390.252749] wlp1s0: associated
[  409.701924] wlp1s0: authenticate with 20:25:64:11:3c:15
[  410.356304] wlp1s0: send auth to 20:25:64:11:3c:15 (try 1/3)
[  410.358694] wlp1s0: authenticated
[  410.360277] wlp1s0: associate with 20:25:64:11:3c:15 (try 1/3)
[  410.366019] wlp1s0: RX AssocResp from 20:25:64:11:3c:15 (capab=0x411 status=0 aid=6)
[  410.366344] wlp1s0: associated
[  418.613714] wlp1s0: authenticate with 20:25:64:11:3c:15
[  419.260302] wlp1s0: send auth to 20:25:64:11:3c:15 (try 1/3)
[  419.265619] wlp1s0: authenticated
[  419.268277] wlp1s0: associate with 20:25:64:11:3c:15 (try 1/3)
[  419.271631] wlp1s0: RX AssocResp from 20:25:64:11:3c:15 (capab=0x411 status=0 aid=6)
[  419.271918] wlp1s0: associated

---

### Post by chili555 on 2023-09-19
What does the signal strength look like? ```
sudo iwlist wlp1s0 scan
```If it is low, say Quality=40/70 or so, then you'd have trouble staying connected. If you are fairly close to the router, then I'd wonder if both antenna connectors are firmly snapped in place.

[https://qph.cf2.quoracdn.net/main-qimg-bf0ff35c07c4dbbbdc81142ddd749807-lq](https://qph.cf2.quoracdn.net/main-qimg-bf0ff35c07c4dbbbdc81142ddd749807-lq)

---

### Post by SeijiSensei on 2023-09-19
Do you have physical access to the router? If so, plug an Ethernet cable between your computer and one of the router's "LAN" ports and turn off any wireless devices. Then you should have a reliable high-speed connection while you get your other problems sorted out.

---

### Post by ScorpioTiger on 2023-09-19
This is from the machine in  question;
Quality=48/70  Signal level=-62 dBm
Quality=50/70  Signal level=-60 dBm
Quality=48/70  Signal level=-62 dBm
Quality=38/70  Signal level=-72 dBm
Quality=48/70  Signal level=-62 dBm

And this is from an 18.04 laptop sitting on the same desk;
Quality=40/70  Signal level=-70 dBm
Quality=33/70  Signal level=-77 dBm
Quality=44/70  Signal level=-66 dBm
Quality=32/70  Signal level=-78 dBm
Quality=27/70  Signal level=-83 dBm
Quality=41/70  Signal level=-69 dBm

I've been able to work on the 18.04 laptop for several months now without issue; even hour long VOIP sessions go without problems.

I should also restate, that if I boot the machine into Windows 10, I don't have issues. If I connect to another WiFi it's fine. It seems to be something specific to this router and the Ubuntu 20.04 install, and something that isn't an issue on my 18.04 install.

---

### Post by ScorpioTiger on 2023-09-19
> **SeijiSensei said:**
> Do you have physical access to the router? If so, plug an Ethernet cable between your computer and one of the router's "LAN" ports and turn off any wireless devices. Then you should have a reliable high-speed connection while you get your other problems sorted out.
Two problems with that. 1) the router is outside on a different building and a cable run isn't going to be practical. 2) Ethernet on the machine also doesn't work.

---

### Post by ScorpioTiger on 2023-09-21
> **chili555 said:**
> What does the signal strength look like? ```
sudo iwlist wlp1s0 scan
```If it is low, say Quality=40/70 or so, then you'd have trouble staying connected. If you are fairly close to the router, then I'd wonder if both antenna connectors are firmly snapped in place.

[https://qph.cf2.quoracdn.net/main-qimg-bf0ff35c07c4dbbbdc81142ddd749807-lq](https://qph.cf2.quoracdn.net/main-qimg-bf0ff35c07c4dbbbdc81142ddd749807-lq)

Given that the signal strength is similar between the two machines and one has no issue, that would not seem to be the problem. I'm now starting to look at the Ethernet which is also not working. Is it possible the two problems are related?

---

### Post by chili555 on 2023-09-21
> I'm now starting to look at the Ethernet which is also not working. Is it possible the two problems are related?They are certainly related by Network Manager. Let's have a look:

```
sudo dmesg | grep -e etwork -e enp
```I wonder if your docker container is a culprit:

> docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether <MAC 'docker0' [IF3]> brd <MAC address>
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft foreverI'm sorry, but I know nothing, nada, zero about docker.

---

### Post by ScorpioTiger on 2023-09-22
Finally got the Ethernet working. Was my lack of knowledge. The network is local through a switch and I had DHCP set for the connection. I changed it to local and it now works.

I have however now lost WiFi all-together. There's no WiFi option on the top right menu, and no menu item under settings. I've done a lot of Googling and found rfkill which doesn't show WiFi as existing. sudo lshw -c network says that the network is "UNCLAIMED". It was working, so I know the hardware is ok and the drivers are installed. Something has changed during all the messing about that's crippled it. Any ideas?

---

### Post by chili555 on 2023-09-23
Did the driver fail to load on boot? Let's check for interesting clues:

```
sudo modprobe rtw_8821ce
sudo dmesg | grep rtw

```One or both of those is likely to throw an error that we can, hopefully, fix.

---

### Post by ScorpioTiger on 2023-09-23
> **chili555 said:**
> Did the driver fail to load on boot? Let's check for interesting clues:

```
sudo modprobe rtw_8821ce
sudo dmesg | grep rtw

```One or both of those is likely to throw an error that we can, hopefully, fix.

```
sudo modprobe rtw_8821ce
```
modprobe: FATAL: Module rtw_8821ce not found in directory /lib/modules/6.2.0-33-generic

```
sudo dmesg | grep rtw
```
Nothing returned.

It's interesting that I got the error. In trying to resolve it myself I found a conversation on StackExchange that included yourself, so I tried reinstalling linux-generic, so it didn't make any difference.
[https://chat.stackexchange.com/transcript/126867/2021/6/25/19-22](https://chat.stackexchange.com/transcript/126867/2021/6/25/19-22)

Edit:
This seems like it might be relevant (see the answer from yourself);
[https://askubuntu.com/questions/1401475/why-rtl8821ce-or-wifi-is-removed-during-kernel-update-on-20-04-4-lts](https://askubuntu.com/questions/1401475/why-rtl8821ce-or-wifi-is-removed-during-kernel-update-on-20-04-4-lts)

---

### Post by chili555 on 2023-09-23
The probable answer is that you've had a kernel update. Please do:

```
cd rtw88
make clean 
git pull
make -j4
sudo -i
make install
modprobe rtw_8821ce
exit
```

---

### Post by ScorpioTiger on 2023-09-23
> **chili555 said:**
> The probable answer is that you've had a kernel update. Please do:

```
cd rtw88
make clean 
git pull
make -j4
sudo -i
make install
modprobe rtw_8821ce
exit
```

Tried this and got a load of errors like;
Skipping BTF generation for /home/genesys/rtw88/rtw_8723du.ko due to unavailability of vmlinux

DId;
sudo cp /sys/kernel/btf/vmlinux /usr/lib/modules/6.2.0-33-generic/build

Tried again and got
/bin/sh: 1: pahole: not found

Did;
sudo apt install dwarves

On install, I got;
make -C /lib/modules/6.2.0-33-generic/build M=/home/genesys/rtw88 modules
make[1]: Entering directory '/usr/src/linux-headers-6.2.0-33-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-11 (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
  You are using:           gcc-11 (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
make[1]: Leaving directory '/usr/src/linux-headers-6.2.0-33-generic'
Install rtw88 SUCCESS

It seems to be working, but I don't know what the consequences will be for the last warning.

Will now see if it sticks after a reboot.
Ok. Fine after reboot.

Now, back top the original problem. I still have the situation where the connection drops every 20 seconds or so. I've been able to test with two other networks now and it's fine with those. Unfortunately, the network where I'm located is the one I'm having issues with. It's find if I boot into Windows 10, or on my Ubuntu 18.04 laptop. So, it's an issue of this machine combined with this network. Anything else I can try?

---

### Post by chili555 on 2023-09-24
> DId;
sudo cp /sys/kernel/btf/vmlinux /usr/lib/modules/6.2.0-33-generic/build

Tried again and got
/bin/sh: 1: pahole: not found

Did;
sudo apt install dwarvesNobody ever suggested that. I strongly suspect these steps are useless.

> Tried this and got a load of errors like;
Skipping BTF generation for /home/genesys/rtw88/rtw_8723du.ko due to unavailability of vmlinux
Does that say 'error'? It is informational only.

I regret that I have no further suggestions.

---

