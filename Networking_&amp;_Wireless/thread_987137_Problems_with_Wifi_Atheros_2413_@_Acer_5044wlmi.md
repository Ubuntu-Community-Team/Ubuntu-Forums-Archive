---
title: "Problems with Wifi Atheros 2413 @ Acer 5044wlmi"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by pigouina on 2008-11-19
Hi all!

I'm very new to linux, I installed Ubuntu 8.10 yesterday on my laptop Acer 5044WLMi.

When i first logged in, i was asked to activate some drivers that are propietary for my Wireless card, but i don't which ones they are.

When i tried to set up the network, nothing came up autodetecting it.

That wouldn't work, so i started searching with google and i found people trying to use ndiswrapper or madwifi.. and even someone saying that if you press the wireless button before GRUB loads it will work !



I tried installing ndiskgtk, and downloading the windows drivers for my card AR5005G,  AR2413, Version: 7.6.0.200

But it says Hardware present: no, and i can't remove the drivers :(

i tried to install madwifi, first compiling it but it was throwing lots of errors with headers, so i downloaded madwifi-source from Debian, and after downloading every dependency (using a usbkey from another computer with internet),now i have them.

i tried to set it up using the instructions, but it wouldn't work.

this is all the data i managed to find.

> 

Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)


:~$ lspci | grep Atheros
06:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
:~$ sudo dmesg | grep ath_hal
[   13.457417] ath_hal: module license 'Proprietary' taints kernel.
[   13.471865] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



:~$ sudo lshw -C network
**  *-network:0 UNCLAIMED   **
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:47:43:02
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:22:07:18:49:50
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
pigouina@pigouina:~$ 


i don't know what do i have to do.

Does anybody have any ideas?

Thank you!!!

pigouina

---

### Post by austozi on 2008-11-22
Hi pigouina,

I'm having a similar problem. I have an Acer 5044NWLCi (Aspire 5040). We have the same wireless card. The same dead one which doesn't work on my machine, either.

I do not mean to hijack your thread but I have a feeling our problems are identical, so I'll explain what I've done. Maybe it will shed some light on your problem. And hopefully someone out there will be able to help us both.

I've been able to make the wireless network configurator appear in my network configuration tool (no sign of life though). This was after I installed the 'linux-backports-modules-intrepid' package from within Synaptic (I think package source is in Ubuntu installer CD) and rebooted, as per this thread: 

[http://ubuntuforums.org/showthread.php?t=987955](http://ubuntuforums.org/showthread.php?t=987955)

I also followed the instructions found here in the documentation:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

From what I've read and understand, that's all that's necessary. My wireless card was supposed to scream to life.

Bus, alas, my wireless still doesn't work. With my computer, there's a wireless switch cum LED at the front panel. It doesn't light up however I try to push or shout at it. And I guess that's the problem. All the software is in place, but the hardware isn't ready. I know that in Windows, the wireless card is switched on via software (WButton.exe which loads at Windows startup). A Linux equivalent of WButton.exe is probably what I need.

I also happen to know that Acer has a Phoenix BIOS update to version 1.06 (downloadable from their website) which will switch on the wireless button at boot time. I thought that must be the answer, so I tried to flash my BIOS but the update software ran into an error before it managed to do anything, damage or otherwise (phew!). I've emailed Acer support about it but haven't got a reply.

Would be great if someone out there could give me a hand at this.

---

### Post by Olivier2371 on 2008-11-22
Ok guys first rule, if you don't know what you are doing, ask or buy a book on ubuntu. Do not try to mess things up because it will only get worse.

I am kind of new to ubuntu but I didn't try fiddle with my system, I bought an excellent book which gave me a bit more insight.(sorry if i am a bit harsh.), And I have no problem with ubuntu 8.04.

Now to come back to your problem, have you tried to install Ubuntu Hardy(8.04)?

Since it is a stable version of ubuntu you should have less problem.
Ubuntu 8.10 is still unstable and you should only use it when your knowledge
has grown.

I apologies to anyone that feels hurt by what I just said above.

---

### Post by austozi on 2008-11-22
Hi Olivier2371,

Thanks for your reply. I'm not hurt but just feel that you missed my point.

I'm kinda new to Ubuntu too, but obviously this is a very specific problem to our wireless card chipset that is very unlikely to be found in any Ubuntu book. Which is why we're now having to do the fiddling ourselves.

Yes, I have installed 8.04 and had the same problem. I upgraded to 8.10 (clean install actually) because I read that it had better support for wireless cards. I used 7.1 for some time too. Same problem. Let's put it this way, my wireless card has never known Ubuntu in its life.

There are numerous posts out there reporting similar problems with similar cards, some complete with solutions, but I have not seen any solution pertaining to my specific card, which is an Atheros AR2413 running on an AR5211 driver in Windows.

> **Olivier2371 said:**
> Ok guys first rule, if you don't know what you are doing, ask or buy a book on ubuntu. Do not try to mess things up because it will only get worse.

I am kind of new to ubuntu but I didn't try fiddle with my system, I bought an excellent book which gave me a bit more insight.(sorry if i am a bit harsh.), And I have no problem with ubuntu 8.04.

Now to come back to your problem, have you tried to install Ubuntu Hardy(8.04)?

Since it is a stable version of ubuntu you should have less problem.
Ubuntu 8.10 is still unstable and you should only use it when your knowledge
has grown.

I apologies to anyone that feels hurt by what I just said above.

---

### Post by Olivier2371 on 2008-11-22
Well, if you want i will explain how i connected my wireless.

1rst I installed ubuntu 8.04, then i updated ubuntu (304 updates). I was connected to my router through nic interface. After i rebooted the laptop,
then i went to the router setup program to make sure of the wireless settings. After that i went back to ubuntu to System->Administration-> Hardware drivers. I found my wireless adapter driver, enabled it. I restarted the computer and then clicked on the network icon, switched to my wireless, entered the encryption mode my router uses, the password and the mode for the encryption. And I was connected.

I am now installing ubuntu 8.04 because the wireless adapter is different make. I will let you know which adapter I use for the destop.

---

### Post by pigouina on 2008-11-22
Olivier, Do you have an Atheros 2413?

im  new to linux and saying that it should work or that a book is what i need doesn't help

pigouina

---

### Post by austozi on 2008-11-22
Hi Olivier2371,

I can tell you the same up to the point "... and the mode for the encryption." And this is the simplest of all things I've attempted to try to bring my wireless card to life. Except then the outcome was unfortunately still negative for me.

The wireless LED has never lit up under Ubuntu (which it does under Windows) no matter what I try. Never mind that the wireless option is available under network configuration. I can enter the right credentials but connection always ends in vain, even when no encryption is set. My hunch is that's because the hardware isn't responding because it's not switched on.

As far as I know this wireless card is only used in certain models of Acer laptops. So to be honest, I'm not optimistic that what adaptor you use on your desktop system will be of any relevance to my problem. But I appreciate your trying to help anyway.


> **Olivier2371 said:**
> Well, if you want i will explain how i connected my wireless.

1rst I installed ubuntu 8.04, then i updated ubuntu (304 updates). I was connected to my router through nic interface. After i rebooted the laptop,
then i went to the router setup program to make sure of the wireless settings. After that i went back to ubuntu to System->Administration-> Hardware drivers. I found my wireless adapter driver, enabled it. I restarted the computer and then clicked on the network icon, switched to my wireless, entered the encryption mode my router uses, the password and the mode for the encryption. And I was connected.

I am now installing ubuntu 8.04 because the wireless adapter is different make. I will let you know which adapter I use for the destop.

---

### Post by Olivier2371 on 2008-11-22
My wireless led isn't lit under unbuntu. It still work. On the other hand it is lit under windows.

I am checking right now what type of adapter i have on my destop.

The led for the adapter is designed to work under windows not linux.

Well I have just checked my desktop and it a libertas 88w8335 from Marvell Technology Group.

Sorry I can't be more helpful.

---

### Post by austozi on 2008-11-22
Hi Oliver2371,

Now this is interesting information, that the LED doesn't have to be lit to work. From the forum threads I've researched thus far, people have always associated the LED failing to light up with their non-functioning wireless connections. I guess I have a reason to be hopeful then.

I wish to know what laptop make and model you have, and what wireless chipset? I know that the wireless adapters on some Acer laptops are switched on at boot (programmed in BIOS) while others are not. Unfortunately mine isn't. If you could tell me the make and model of your laptop that may shed some light on the problem.

Thanks.

---

### Post by Olivier2371 on 2008-11-22
Hi Austozi

Acer Aspire 9302 AWSMI

specifications:

AMD Turion 64 Mobile Technology MK38 (2.2 GHZ, 512KB L2 cache)
17" WXGA+ Acer CrystalBrite LCD
up to 384 MB NVIDIA Geforce Go Xpress 6100 TurboCache
120 GB HDD
DVD-Super Multi double layer
4 GB DDR2 Memory
802.11 b/g Wireless Lan Broadcom 4311
Mini pci extension slot for BlueTooth card
Windows Vista premium & Ubuntu 8.04 Lts

for your information when I start the laptop, the led is on but as soon as i boot into unbuntu the led is not lit anymore.

---

### Post by austozi on 2008-11-22
I've decided to post a few lines of code to illustrate my problem:

```
iwconfig wlan0
```

gives

```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
iwlist wlan0 scan
```

gives

```
wlan0     No scan results
```

Like I said in my first post in this thread, I installed the 'linux-backports-modules-intrepid' package to use the ath5k driver, then blacklisted ath_pci and ath_hal in /etc/modprobe.d/blacklist. Rebooted and wireless options appeared in the network configuration tool.

I can confirm the driver is loaded. Nothing seems to work though, no network detected, LED doesn't light up (not during boot time, not in Ubuntu, never). Clicking on the network manager applet icon (located near the clock on top right corner by default) shows the option 'Wireless networks' grayed out. I am able to manually specify a network to connect to using the network configuration tool but nothing connects. No scanning activity as far as I can see.


To pigouina:

Have you got as far as I have? Does your wireless LED light up? If you have and it does I would be interested to know if doing what I've done works for you. That would kinda confirm my suspicion that my hardware isn't ready.


To Oliver2371:

It is clear that we are using completely different hardware. You are lucky that your hardware has received support since older versions of Ubuntu. So I guess you may not understand our frustration. Appreciate your effort though.

---

### Post by Olivier2371 on 2008-11-22
Hi austozi,

Yes believe me I do understand your frustration. It was the same for me in the beginning. 

What seems strange to is that you do not have an ESSID.

I have used different laptop with different wireless adapter and router but I always had a ESSID name. 

Here is what I get below from my connection:

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:E5:8E:C1:22   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=86/100  Signal level=-45 dBm  Noise level=-66 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Maybe your router is not broadcasting. My router is on mode "managed", while yours is on mode "Ad-hoc".

---

### Post by austozi on 2008-11-22
Hi Olivier2371,

I could set the mode to 'Managed' by specifying a home network access point and it wouldn't change the situation. It doesn't matter how I name my home network, this is what I always get:

```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

My mode was on Ad-hoc because that was the last setting I played with in trying to get my wireless to connect to a peer-to-peer network. You would try anything if you were in my shoes :)

I guess the fact that I don't have an ESSID isn't that strange after all because Ubuntu hasn't found any network nearby, which is precisely my problem. My router is broadcasting for sure. There are also more than half a dozen home networks nearby (detected within Windows) but none shows up on my Ubuntu box.

---

### Post by Joe2Shoe on 2008-11-22
pigouina, I have the Atheros AR5001X+ wifi card.
I am running Ubuntu v8.10.
In the wireless configuration area, under mode, choose 'infrastructure', not 'ad-hoc'!
Go to System/Administration/Hardware Drivers.
If your Atheros driver is listed, click on it, then click the 'activate' button below.
Reboot, if required.
That worked for me.
Good luck.
Joe2Shoe.

---

### Post by Joe2Shoe on 2008-11-22
pigouina,
Here's my 'configuration' settings.

Under "Edit Connections"
Connect automatically: is checked
System setting: is not checked

Under "Wireless" tab
SSID: name of my network
Mode: Infrastructure
BSSID: blank
MAC address: blank
MTU: automatic

Under "Wireless Security" tab
Security: WPA & WPA2 Personal
Password: my network's password

Under "IPv4 Settings" tab
Method: Automatic (DHCP) or "Automatic DHCP (with address only"), whichever works)

Under "Address" section
Address: my IP Address
Netmask: 24
Gateway: 0.0.0.0

DNS Servers: my DNS Server Address
Search Domains: blank

Hope this helps.
Joe2Shoe.

---

### Post by eks on 2008-11-22
> **Olivier2371 said:**
> Ok guys first rule, if you don't know what you are doing, ask or buy a book on ubuntu. Do not try to mess things up because it will only get worse.

Sorry, but I have to disagree. I would say, make a backup, and blow your system up tweaking it. If you break it beyond repair, just install it again. Make /home on a separate partition and heavily use Google and the forums and you are set. :mrgreen:

Regarding the LED for the wifi, on most computer it DOES NOT work. But the switch DOES WORK. On some computers you can Google for a solution to make the led work, generally is just a couple of lines in some config file. But generally, the wifi switch button does work. So try to check that.

Regarding the wifi working or not, post the result of this command:

```
dmesg | grep ath
```

In short, if you have more than one ath being executed during boot, there's your problem, it should be only one.

---

### Post by austozi on 2008-11-22
Thanks eks. Here's my output for 'dmesg | grep ath':

```
[   14.499087] ath5k_pci 0000:06:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.499156] ath5k_pci 0000:06:05.0: registered as 'phy0'
[   15.603856] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[ 8052.167171] ath5k phy0: noise floor calibration timeout (2412MHz)

```

> **eks said:**
> Sorry, but I have to disagree. I would say, make a backup, and blow your system up tweaking it. If you break it beyond repair, just install it again. Make /home on a separate partition and heavily use Google and the forums and you are set. :mrgreen:

Regarding the LED for the wifi, on most computer it DOES NOT work. But the switch DOES WORK. On some computers you can Google for a solution to make the led work, generally is just a couple of lines in some config file. But generally, the wifi switch button does work. So try to check that.

Regarding the wifi working or not, post the result of this command:

```
dmesg | grep ath
```

In short, if you have more than one ath being executed during boot, there's your problem, it should be only one.

---

### Post by eks on 2008-11-22
As for the driver working or not, it seems everything is ok. But why it's not seeing anything is beyond me. :(

Have you tried searching for networks with the switch on both positions? Or maybe even closer to the wifi router?

---

### Post by austozi on 2008-11-22
The router is within 2-3 meters from where my laptop is, in the same room, as I type. No sign of it picking up any signal. In Windows I get excellent signals (full bars). No sign of scanning activity so no networks to select from. Which is what led me to think the hardware wasn't switched on. Thanks for your response anyway, at least now I know the driver looks like it's working fine.

And the button is a simple push button which usually shows it's ON by lighting up (the switch doubles as the LED). There's no 'position' as such that you can tell by just looking at it otherwise. I've tried pushing the button, holding it down, or releasing it altogether during boot time and within Ubuntu. No luck.

---

### Post by Joe2Shoe on 2008-11-22
[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

Even though the driver seems to be activated and 'working fine', it isn't.  That was my case, also.

Copy the .inf Window's driver file for your wifi's card to a flash drive or cd, then copy it to your desktop in Ubuntu.
After installing NDISwrapper per the above link, locate the driver file and install it.
Then go to System/Administration/Hardware Drivers, and the driver should be listed, activate it, reboot if necessary (most often is), and check wifi connection.
Joe2Shoe.

---

### Post by Olivier2371 on 2008-11-22
eks,

Thanks for your disagreeing with me.

On the other hand asking for people to tweak their system beyond repair could be a good idea even if by doing so, it's going to take them years to actually get thing sorted.

---

### Post by austozi on 2008-11-24
Thanks Joe2Shoe for the suggestion. Have done so, still not working. In fact doing so seems to make the wireless configuration interface disappear, and the wireless card would not be detected by Ubuntu.


> **Joe2Shoe said:**
> [https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

Even though the driver seems to be activated and 'working fine', it isn't.  That was my case, also.

Copy the .inf Window's driver file for your wifi's card to a flash drive or cd, then copy it to your desktop in Ubuntu.
After installing NDISwrapper per the above link, locate the driver file and install it.
Then go to System/Administration/Hardware Drivers, and the driver should be listed, activate it, reboot if necessary (most often is), and check wifi connection.
Joe2Shoe.

---

### Post by gbuonfiglio on 2008-11-25
Hi,

this is what I did to make it work:
[LIST]
[*]Installed backport modules to use ath5k instead of current Atheros modules:
```
sudo apt-get install linux-backports-modules-intrepid
```
[*]Added both lines below to /etc/modprobe.d/blacklist
```
blacklist ath_pci
blacklist ath_hal

```
[*]Added the line below to /etc/rc.local just above "exit 0" so the wireless interface is enabled on boot:
```
echo 1 > /sys/devices/platform/acer-wmi/wireless
```
[/LIST]
Sending "1" to */sys/devices/platform/acer-wmi/wireless* enables the interface and "0" disables it.

To improve it, when using the wireless button it should echo "0" or "1" alternately to */sys/devices/platform/acer-wmi/wireless*, or maybe enabling/disabling wireless through Network Manager applet that should trigger it, but I have no idea on how to do it. :(

[]s,
Guilherme Buonfiglio de Castro Monteiro

---

### Post by austozi on 2008-11-28
gbuonfiglio:

Thanks, that worked! This was exactly what I needed:

echo 1 > /sys/devices/platform/acer-wmi/wireless

---

### Post by austozi on 2008-11-29
OK, here's where I'm with my wireless issue on my Ubuntu box.

I've managed to get the wireless hardware to switch on upon boot. This solved the previous problem where no network was ever detected. I am now able to connect to my home wireless network just fine. 

However, as soon as I restart (or shutdown then start anew) my computer, the "Enable Wireless" option disappears from the Network Manager applet while the hardware is switched on (the wireless LED is lit). I am disconnected from my home network, and indeed the applet lists no wireless network to connect to. I will then need to go to System > Hardware drivers and deactivate the restricted ath5k driver, then activate it again, to make the "Enable wireless" option reappear in the Network Manager applet before I am connected to my home wireless network.

Does anybody have any idea on how to make the wireless feature persist across boot sessions? It is not a major problem at the moment, but having to manually deactivate then activate the driver every time the computer boots up just sounds plain silly and it would be nice to get rid of the need to do so.

---

### Post by nygamma on 2009-02-22
I've been struggling for some time to get my wireless to work on Ubuntu 8.10. I followed every piece of advice I could find, with no success. Finally, I have just fixed it! Here is what I did, in case it is of any help to anyone.

In the directory

/etc/modprobe.d

edit (as an administrator) the file

madwifi

so that the ath5k driver is NOT blacklisted (comment # at the beginning of the line), and the ath_hal and ath_pci drivers ARE blacklisted (no # at the beginning of the two lines). Here is what it looks like in my case:

## ath5k (mac80211)
#blacklist ath5k

## madwifi (non-free)
blacklist ath_hal
blacklist ath_pci
#blacklist ath_rate_amrr
#blacklist ath_rate_onoe
#blacklist ath_rate_sample
#blacklist wlan
#blacklist wlan_acl
#blacklist wlan_ccmp
#blacklist wlan_scan_ap
#blacklist wlan_scan_sta
#blacklist wlan_tkip
#blacklist wlan_wep
#blacklist wlan_xauth

Best,

nygamma

---

