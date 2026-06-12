---
title: "RTL8723BE problems"
date: 2015-09-30
forum: Networking &amp; Wireless
---

### Post by willy7 on 2015-09-30
Hi guys, I just bought an hp probook 455 g2 which has installed the RTL8723BE wifi adapter.
Well there's no way to get it working, even if I followed instructions at [http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04](http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04) to fix the problem, I still have some trouble to attach to my wifi network.

I've kubuntu 15.04 with kernel 3.19.0-28-generic

```
lsmod | grep wifi               
102400  3 btcoexist,rtl_pci,rtl8723be
mac80211              724992  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              540672  2 mac80211,rtlwifi
```

Can you help?

Thank you

---

### Post by nknwn on 2015-10-01
Run:
  [B]rfkill list
[/B]in the terminal to check whether your network adapter is blocked or not

Also run:
[B]  lshw -C network
[/B]Then paste the results in this thread 
Let's see if **lshw** says your network adapter disabled or something else.

---

### Post by willy7 on 2015-10-02
> **nknwn said:**
> Run:
  [B]rfkill list
[/B]in the terminal to check whether your network adapter is blocked or not

Also run:
[B]  lshw -C network
[/B]Then paste the results in this thread 
Let's see if **lshw** says your network adapter disabled or something else.

Hi **nknwn, **thank you for your reply...
```
$ rfkill list0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
$ lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 3c:a8:2a:7e:df:6c
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.0.10 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:4000(size=256) memory:d5804000-d5804fff memory:d5800000-d5803fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 70:77:81:0f:c2:95
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.19.0-30-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:46 ioport:3000(size=256) memory:d4800000-d4803fff
```

---

### Post by nknwn on 2015-10-02
Looks OK from here ---
Unhook your Ethernet cable and use the following command in the terminal:

sudo nmcli dev wifi connect **yournetworkssid** password [B]yourwifipassword

-----
[/B]I was searching the forum to check the above command syntax when I came across this thread which relates directly to your wireless adapter:
[http://ubuntuforums.org/showthread.php?t=2280428](http://ubuntuforums.org/showthread.php?t=2280428)
It's marked solved. You might want to take a look at it nd I will be reading it later.
:)

---

### Post by willy7 on 2015-10-02
> **nknwn said:**
> Looks OK from here ---
Unhook your Ethernet cable and use the following command in the terminal:

sudo nmcli dev wifi connect **yournetworkssid** password [B]yourwifipassword

-----
[/B]I was searching the forum to check the above command syntax when I came across this thread which relates directly to your wireless adapter:
[http://ubuntuforums.org/showthread.php?t=2280428](http://ubuntuforums.org/showthread.php?t=2280428)
It's marked solved. You might want to take a look at it nd I will be reading it later.
:)

here's the output
```
$ sudo nmcli dev wifi connect WGFLAN password xxx
Errore: rete con SSID «WGFLAN» non trovata.
```

Maybe you know italian, it says that WGFLAN network has not been found :)

Consider that I have no problem connecting to my wifi network with other devices...

thank you for your help

---

### Post by jeremy31 on 2015-10-02
Follow the instructions on running the wireless script and post the results [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by willy7 on 2015-10-03
hi nknwn, here attached the output of the script... I don't see anything strange...

---

### Post by jeremy31 on 2015-10-03
You haven't set the regulatory info ```
sudo iw reg set IT
``` if you are in Italy.  Reboot and see if wireless networks are detected, if no networks are detected, I would shutdown the laptop and remove the cover on the bottom of the laptop and see if the antenna(s) are connected to the wifi card

---

### Post by willy7 on 2015-10-04
bad news... nothing changed, wireless lan is not detected.

I can exlude problems related to the antenna because I have w8 on the same notebook and wileress interface works as expected.

here attached the new wirelessinfo after reg set.

---

### Post by jeremy31 on 2015-10-04
Some times ```
echo "options rtl8723be msi=1" | sudo tee -a /etc/modprobe.d/rtl8723b3.conf
``` Works after a reboot

If that doesn't work, Pilot6's PPA might help
```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware
```

---

### Post by willy7 on 2015-10-05
Hi jeremy, nothing works, even the rtlwifi-new :-( :-(

---

### Post by nknwn on 2015-10-05
Hi Willy7, it looks to me like you created the wireless-info.txt when the computer was connected via the Ethernet cable. The wireless adapter would not try to connect in that situation. Might it be worth running the script again but when the Ethernet cable is disconnected? Let's take a look the modified wireless-info file. Post it here as you did previously. Thanks.

---

### Post by willy7 on 2015-10-05
you're right... here attached the wireless info txt with cabled network disconnected.

thank you

---

### Post by nknwn on 2015-10-05
The file indicates: "Kernel driver in use: rtl8723be"

But that might be OK because also in the file:
[wifi] ssid=WGFLAN | mac-address=<MAC 'wlan0' [IF]>

So the WIFI adapter can see the network now where previously it could not. As reported in post #5

Try the command again?
sudo nmcli dev wifi connect **yournetworkssid** password [B]yourwifipassword

[/B](Disconnect the Ethernet cable first)

---

### Post by willy7 on 2015-10-05
Still bad news... I launched the command again but my WiFi network is not found

---

### Post by jeremy31 on 2015-10-05
I am starting to think there is a different firmware file or something being used in windows for some of the HP RTL8723be cards.  Can you search in windows for rtl8723befw?  There is a chance it doesn't exist and the file Linux uses was somehow extracted from a windows firmware file

---

### Post by willy7 on 2015-10-06
Hi jeremy31, I searched for a file named rtl8723*.* in the Windows partition and your idea is confirmed : no files with that name... 
Do you think there's a chance to get it working?

---

### Post by jeremy31 on 2015-10-06
I don't know if you have tried the msi parameter yet
```
echo "options rtl8723be fwlps=N ips=N msi=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Reboot

For some reason every one of the reports like yours involves a HP computer

---

### Post by nknwn on 2015-10-06
It should work !%"$
"The **HP ProBook 455 G2 Notebook PC** laptop with the components described below has been awarded the status of certified pre-install for Ubuntu."
[http://www.ubuntu.com/certification/hardware/201404-14968/](http://www.ubuntu.com/certification/hardware/201404-14968/)
Includes: "Wireless Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter 
"

---

### Post by howefield on 2015-10-06
> **nknwn said:**
> It should work !%"$
"The **HP ProBook 455 G2 Notebook PC** laptop with the components described below has been awarded the status of certified pre-install for Ubuntu."

And it does... with Ubuntu 12.04, however not with anything more recent, at least not without much pain :)

The OP is running 15.04 :)

---

### Post by nknwn on 2015-10-06
It is an interesting puzzle :) 
but frustrating not to find a clue in the wireless-info.txt

---

### Post by jeremy31 on 2015-10-06
We have seen plenty of these cards work in Linux and now we come across some that work fine in Windows but lose signal if they are more than 3 feet from an access point in Linux.  I wonder if a new batch of these cards aren't using a different pre-amp on the rx side and the default settings in the rtl8723be module are now too low

---

### Post by willy7 on 2015-10-07
Hi jeremy, I don't know if the distance from router is the problem, I tried connection a 10cm with no luck.

Even the msi param doesn't solve...

As you said, I think there's a new type of these cards around. 

Another test: I disabled the wlan interface, I disconnected the eth0, and then I reenabled the wlan...
this is what I see in the system log
```
[  896.404138] wlan0: authenticate with 0e:bd:xx:xx:xx:xx
[  896.416186] wlan0: send auth to 0e:bd:xx:xx:xx:xx (try 1/3)
[  896.419592] wlan0: authenticated
[  896.420811] wlan0: associate with 0e:bd:xx:xx:xx:xx (try 1/3)
[  896.426036] wlan0: RX AssocResp from 0e:bd:xx:xx:xx:xx (capab=0x411 status=0 aid=3)
[  896.427330] wlan0: associated
```

This is a little bit confusing; authenticated? where? maybe there is some software conflicting with NetworkManager?

---

### Post by willy7 on 2015-10-07
Hurray! Magic is done by adding the following row to /etc/modprobe.d/iwlwifi.conf
```
[COLOR=#000000]options iwlwifi 11n_disable=0[/COLOR]
```[COLOR=#000000]

Thank you guys for the support :)[/COLOR]

---

### Post by nknwn on 2015-10-08
This is good to hear. Where did you find the solution?

---

### Post by willy7 on 2015-10-08
I found advices here [http://askubuntu.com/questions/616119/unstable-wireless-with-intel-7260-iwlwifi-after-upgrade-to-15-04](http://askubuntu.com/questions/616119/unstable-wireless-with-intel-7260-iwlwifi-after-upgrade-to-15-04)

remains some problem related to the wakeup after standby... the wlan interface does nothing, no connection, no link, so scan...

---

### Post by janmes2 on 2015-11-12
Dont know about other wifi like intel/broadcom etc but I also have the realtek rtl8723be wifi card and tried installing loads of drivers and multiple options but no jy. After about a month, i added this simple line to grub and low and behold all is working well.

here it is....

press Ctrl+Alt+T to open up a terminal 


run the following command: sudo gedit /etc/default/grub


Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"


save changes to grub and exit gedit and the terminal


Open up a new terminal with ctrl+alt+t 


run the following command: sudo update-grub


then exit the terminal using this command: exit


Restart your computer

---

### Post by 20151201random on 2015-12-01
I to have been trying to get my Ebuyer HP455 Ubuntu laptop wifi card to work since I upgraded to 14.04 Lts, with no success until I came across Janmes2  post above and now its working a treat.

I would just like to say thanks Janmes2

John

---

