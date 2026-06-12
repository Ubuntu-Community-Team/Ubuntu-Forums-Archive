---
title: "D-Link DWA-171 AC600 wifi dongle not detected at all in Ubuntu 20.04"
date: 2021-05-17
forum: Networking &amp; Wireless
---

### Post by surya.durgaputra on 2021-05-17
Hello,
 I am trying to get D-Link DWA-171 AC600 wifi dongle to work in  Ubuntu 20.04. The dongle works fine when I dual-boot into windows. So the issue has to be related to drivers.

I tried many options: like here : [https://github.com/whitebatman2/rtl8821CU](https://github.com/whitebatman2/rtl8821CU)

and here: [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux)

But the dongle simple does not get detected by the OS. 

Here is the result of lsusb:
```
Bus 001 Device 007: ID 0bda:c811 Realtek Semiconductor Corp. 802.11ac NIC
```

Here is the result of lsmod | grep rtl
```
rtl8812au    1347584  0
cfg80211     704512   2  rtl8812au,8821cu
```

Note that before I installed the drivers from  the above mentioned two github links, ```
lsmod | grep rtl
``` returned blank.

Any help is appreciated.
Thanks,
Surya

---

### Post by chili555 on 2021-05-17
Please run and post:

```
sudo dkms status
modinfo rtl8812au | grep C811
modinfo 8821cu | grep C811

```
Thanks.

---

### Post by surya.durgaputra on 2021-05-17
Hello chili555,
Many thanks for replying.

Here is what I get when I ran the commands:

```
helios@helios:~
(i)$ [COLOR=#0000ff]sudo dkms status[/COLOR]
[sudo] password for helios: 
[COLOR=#008000]rtl8192eu, 1.0, 5.4.0-72-generic, x86_64: installed
rtl8192eu, 1.0, 5.4.0-73-generic, x86_64: installed
rtl8812au, 4.3.14, 5.4.0-73-generic, x86_64: installed (WARNING! Diff between built and installed module!)
rtl8821CU, 5.2.5.3, 5.4.0-73-generic, x86_64: built
rtl8821CU, 5.4.1, 5.4.0-73-generic, x86_64: installed (WARNING! Diff between built and installed module!)[/COLOR]
```

```
helios@helios:~
(i)$ [COLOR=#0000ff]modinfo rtl8812au | grep C811[/COLOR]
```
i.e. the above command returned blank

```
helios@helios:~
(i)$ [COLOR=#0000ff]modinfo 8821cu | grep C811[/COLOR]
[COLOR=#008000]alias:          usb:v0BDApC811d*dc*dsc*dp*icFFiscFFipFFin*[/COLOR]

```


Best Regards,
Surya

---

### Post by morrownr on 2021-05-18
Surya,

Not meaning to step on chili555's toes because he know his stuff but please allow me to put my 2 cents into the mix.

sudo is a weapon of mass destruction. I say this with respect so please don't take it the wrong way. Please don't just start installing out-of-kernel drivers until you find one that works. There are several experts here that can put you on a driver that will work. Ask before, not after.

Before I give you hints about how to clean up the mess, here is a link with information about wifi adapters that "just work" and do not require you to hunt down, compile, pray and seek help:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Okay, to your system. You have several wifi drivers installed. Two of them are for an adapter with a 8811cu chipset and the drivers are different versions, neither of which I recognize but the version numbers indicate the drivers are dated. This is not good.

How 'bout we look at cleaning this up a bit. The best way to uninstall a driver is to follow the uninstall instructions for the driver you installed... if there are good uninstall instructions. If there are no good uninstall instructions, I suggest using dkms to clean one driver at a time followed by destroying the folder that was created to download the driver. Let's start with the following driver:

rtl8821CU, 5.4.1, 5.4.0-73-generic, x86_64

To uninstall it with dkms:

Code:
sudo dkms  remove -m rtl8821CU -v 5.4.1 --all

You can repeat the removal line for the other drivers but change the name and version as appropriate and you can check progress with:

Code:
dkms status

Once you have cleaned things up, go here:

[https://github.com/morrownr/8821cu](https://github.com/morrownr/8821cu)

That driver is very well documented. The installation process is tested hundreds of times per week. It is a popular site. And the driver is the latest version available with numerous updates.

Good luck.

---

### Post by surya.durgaputra on 2021-05-18
Hello morrownr,
 Thanks for your help. The link describing the WiFi  dongle support among vendors and recommendations are spot on. My  previous dongle was TP-link, works on Windows.. does not work on Linux. I  had to create a thread here and chilli555 helped me out to get it  working properly. This time I got D-Link and am ruing my purchase  decision. If I had known about the **** poor Linux support among D-Link,  I would have never bought it. Anyways, lesson learned. Many thanks for  sending me the link with Wifi dongles with good Linux support.

Coming  back to cleanup and installation of driver you recommended, I did it.  Managed to get rid of the previous drivers (thankfully they had good  uninstall steps). After uninstallation and cleanup of my bad drivers (and before installing the new driver), I did 
```
helios@helios:~
(i)$ [COLOR=#0000ff]sudo dkms status[/COLOR]
[sudo] password for helios: 
[COLOR=#008000]rtl8192eu, 1.0, 5.4.0-72-generic, x86_64: installed
rtl8192eu, 1.0, 5.4.0-73-generic, x86_64: installed[/COLOR]
```

So, the earlier bad drivers were truly gone.

Then I followed the install steps in the link sent by you: [https://github.com/morrownr/8821cu](https://github.com/morrownr/8821cu)
after successful installation, I did this:
```
helios@helios:~
(i)$ [COLOR=#0000ff]sudo dkms status[/COLOR]
[sudo] password for helios: 
[COLOR=#008000]rtl8192eu, 1.0, 5.4.0-72-generic, x86_64: installed
rtl8192eu, 1.0, 5.4.0-73-generic, x86_64: installed
rtl8821cu, 5.8.1.7, 5.4.0-73-generic, x86_64: installed[/COLOR]
helios@helios:~
(i)$[COLOR=#0000ff] lsusb[/COLOR]
[COLOR=#008000]Bus 001 Device 006: ID 0bda:c811 Realtek Semiconductor Corp. 802.11ac NIC[/COLOR]
helios@helios:~
(i)$ [COLOR=#0000ff]lsmod | grep rtl[/COLOR]
helios@helios:~
(i)$ 

```

Looks like the new driver got installed fine. But the dongle still does not show up as wifi. 
It is still not installed as wifi and I do not see the wifi icon at top right in the ubuntu's system status bar.
Please advice what to do next.

Best Regards,
Surya

---

### Post by chili555 on 2021-05-18
> It is still not installed as wifi and I do not see the wifi icon at top right in the ubuntu's system status bar.
Please advice what to do next.Let's check the log:

```
sudo dmesg | grep -i -e 8821 -e rtl
rfkill list all
```

---

### Post by surya.durgaputra on 2021-05-18
Hello chili555,
 Thanks for your reply. Here is what I got when I ran the commands:
```
helios@helios:~
(i)$ [COLOR=#0000ff]sudo dmesg | grep -i -e 8821 -e rtl[/COLOR]
[sudo] password for helios: 
[COLOR=#008000][    0.732556] r8169 0000:02:00.0 eth0: [/COLOR][COLOR=#ff0000]RTL[/COLOR][COLOR=#008000]8168h/8111h, 2c:4d:54:50:8d:3c, XID 541, IRQ 132[/COLOR][COLOR=#00ff00]
[/COLOR][COLOR=#008000][   24.13[/COLOR][COLOR=#00ff00][/COLOR][COLOR=#ff0000]8821[/COLOR][COLOR=#008000]] videodev: Linux video capture interface: v2.00[/COLOR][COLOR=#00ff00]
[/COLOR][COLOR=#008000][   24.885908] [/COLOR][COLOR=#00ff00][/COLOR][COLOR=#ff0000]8821[/COLOR][COLOR=#008000]cu: loading out-of-tree module taints kernel.[/COLOR][COLOR=#00ff00]
[/COLOR][COLOR=#008000][   24.886535] [/COLOR][COLOR=#00ff00][/COLOR][COLOR=#ff0000]8821[/COLOR][COLOR=#008000]cu: module verification failed: signature and/or required key missing - tainting kernel[/COLOR][COLOR=#00ff00]
[/COLOR][COLOR=#008000][   25.027466] usbcore: registered new interface driver [/COLOR][COLOR=#00ff00][/COLOR][COLOR=#ff0000]rtl8821[/COLOR][COLOR=#008000]cu[/COLOR][COLOR=#00ff00]
[/COLOR][COLOR=#008000][   25.167366] [/COLOR][COLOR=#00ff00][/COLOR][COLOR=#ff0000]rtl8821[/COLOR][COLOR=#008000]cu 1-12:1.0 wlxbc0f9af583ad: renamed from wlan0[/COLOR]
helios@helios:~
(i)$ [COLOR=#0000ff]rfkill list all[/COLOR]
[COLOR=#008000]0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no[/COLOR]
helios@helios:~
(i)$ 

```

Best Regards,
Surya

---

### Post by praseodym on 2021-05-18
SecureBoot is disabled?

---

### Post by morrownr on 2021-05-18
Surya,

Have you tried removing the adapter and putting it in another usb port? That is a usb2 adapter so give preference to a usb2 port.

It is a multi-state adapter but it appears usb_modeswitch is doing its job.

What do you get with the following?

```
iw dev
```

Oh, on a different subject. I think we need a laugh. My main box:

$ dkms status
rtl8812au, 5.9.3.2, 5.4.0-72-generic, x86_64: installed
rtl8814au, 5.8.5.1, 5.4.0-72-generic, x86_64: installed
rtl8814au, 5.8.5.1, 5.4.0-73-generic, x86_64: installed
rtl8821au, 5.8.2.3, 5.4.0-72-generic, x86_64: installed
rtl8821au, 5.8.2.3, 5.4.0-73-generic, x86_64: installed
rtl8821cu, 5.8.1.7, 5.4.0-72-generic, x86_64: installed
rtl88x2bu, 5.8.7.4, 5.4.0-72-generic, x86_64: installed
rtl88x2bu, 5.8.7.4, 5.4.0-73-generic, x86_64: installed

The really funny part is the adapter in use right now doesn't even use any of those drivers as it is based on a mt7612u chipset and the driver is in the kernel so it doesn't show up in dkms. That may look like a mess but it isn't so it is okay to for us to get a good laugh out of it.

---

### Post by surya.durgaputra on 2021-05-18
Hello Praseodym,
Thank you for your reply.
 I tried this:

```

helios@helios:~
(i)$ [COLOR=#0000ff]sudo mokutil --sb-state[/COLOR]
[sudo] password for helios: 
[COLOR=#008000]SecureBoot disabled[/COLOR]
helios@helios:~
(i)$ 


```

Looks like Secure Boot is disabled.

Best Regards,
Surya

---

### Post by surya.durgaputra on 2021-05-18
Hello morrownr,

Thanks for your reply.
I removed the dongle from previous USB slot and put in another slot that I think is USB2.0.

Here is what I get when I run the command:
```

(i)$[COLOR=#0000ff] iw dev[/COLOR]
[COLOR=#008000]phy#0
    Interface wlxbc0f9af583ad
        ifindex 3
        wdev 0x1
        addr bc:0f:9a:f5:83:ad
        type managed
        txpower 12.00 dBm[/COLOR]
helios@helios:~
(i)$ 


```
Best Regards,
Surya

---

### Post by chili555 on 2021-05-18
Does it scan and see networks?

```
sudo iwlist scan
```

Is Network Manager running correctly?

```
sudo service NetworkManager status
```

Is networking improperly declared here?

```
cat /etc/network/interfaces

```
Or here?

```
cat /etc/netplan/*.yaml
```

Are there any clues in the log?

```
sudo dmesg | grep wlx
```

---

### Post by surya.durgaputra on 2021-05-19
Hello chili555,
Thank you for your reply.

The dongle is certainly seeing wireless networks.
```

helios@helios:~
(i)$ [COLOR=#0000ff]sudo iwlist scan[/COLOR]
[COLOR=#008000]lo        Interface doesn't support scanning.

docker0   Interface doesn't support scanning.

wlxbc0f9af583ad  Scan completed :
          Cell 01 - Address: 48:AD:08:D5:39:14
                    ESSID:"HUAWEI-tbrh"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD700050F204104A0001101044000102103B0001031047001022850F441E1895E5D64FDD8435F1C2A1102100064875617765691023000648756177656910240007484738323435481042000233391054000800060050F2040001101100094875617765694F4E54100800020080103C000101
                    Quality=81/100  Signal level=-77 dBm  
                    Extra:fm=0003
          Cell 02 - Address: E4:E7:49:EC:AC:66
                    ESSID:"DIRECT-65-HP DeskJet 2600 series"
                    Protocol:IEEE 802.11gn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:72 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDA10050F204104A000110104400010210570001011041000100103B000103104700105AB68143009B59AA88A1D93988B407711021000248501023000130102400013010420001301054000800030050F2040005101100204449524543542D36352D4850204465736B4A65742032363030207365726965731008000200001049000600372A00012010490017000137100600105AB68143009B59AA88A1D93988B40771
                    Quality=74/100  Signal level=-44 dBm  
                    Extra:fm=0003
          Cell 03 - Address: 48:AD:08:D6:40:28
                    ESSID:"HUAWEI-BUSG"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD700050F204104A0001101044000102103B00010310470010018A3243126B644CEF524AABFD38253F102100064875617765691023000648756177656910240007484738323435481042000233391054000800060050F2040001101100094875617765694F4E54100800020080103C000101
                    Quality=72/100  Signal level=-72 dBm  
                    Extra:fm=0003

enp2s0    Interface doesn't support scanning.

virbr0-nic  Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.[/COLOR]

helios@helios:~
(i)$ 


```


Here is the Network Manager output:
```

helios@helios:~
(i)$ [COLOR=#0000ff]sudo service NetworkManager status[/COLOR]
[COLOR=#daa520]&#9679;[/COLOR][COLOR=#008000] NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
     Active: [/COLOR][COLOR=#daa520]active (running)[/COLOR][COLOR=#008000] since Wed 2021-05-19 08:27:35 +04; 10min ago
       Docs: man:NetworkManager(8)
   Main PID: 1037 (NetworkManager)
      Tasks: 3 (limit: 28626)
     Memory: 13.8M
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;1037 /usr/sbin/NetworkManager --no-daemon

May 19 08:35:02 helios NetworkManager[1037]: <info>  [1621398902.5361] device (wlan0): interface index 7 renamed iface from 'wlan0' to 'wlxbc0f9af583ad'
May 19 08:35:02 helios NetworkManager[1037]: <info>  [1621398902.5459] device (wlxbc0f9af583ad): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
May 19 08:35:03 helios NetworkManager[1037]: <info>  [1621398903.2668] sup-iface[0x56424ebcf210,wlxbc0f9af583ad]: supports 5 scan SSIDs
May 19 08:35:03 helios NetworkManager[1037]: <info>  [1621398903.2674] device (wlxbc0f9af583ad): supplicant interface state: starting -> ready
May 19 08:35:03 helios NetworkManager[1037]: <info>  [1621398903.2675] Wi-Fi P2P device controlled by interface wlxbc0f9af583ad created
May 19 08:35:03 helios NetworkManager[1037]: <info>  [1621398903.2677] manager: (p2p-dev-wlxbc0f9af583ad): new 802.11 Wi-Fi P2P device (/org/freedesktop/NetworkManager/Devices/9)
May 19 08:35:03 helios NetworkManager[1037]: <info>  [1621398903.2679] device (p2p-dev-wlxbc0f9af583ad): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'e>
May 19 08:35:03 helios NetworkManager[1037]: <info>  [1621398903.2684] device (p2p-dev-wlxbc0f9af583ad): state change: unavailable -> disconnected (reason 'none', sys-iface-state: 'm>
May 19 08:35:03 helios NetworkManager[1037]: <info>  [1621398903.2689] device (wlxbc0f9af583ad): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-s>
May 19 08:35:03 helios NetworkManager[1037]: [/COLOR][COLOR=#ffd700]<warn>  [1621398903.2756] sup-iface: failed to cancel p2p connect: P2P cancel failed[/COLOR][COLOR=#008000]
lines 1-20/20 (END)[/COLOR]

```


Rest of the commands are here:
```

helios@helios:~
(i)$ [COLOR=#0000ff]cat /etc/network/interfaces[/COLOR]
[COLOR=#008000]# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback[/COLOR]
helios@helios:~
(i)$ [COLOR=#0000ff]cat /etc/netplan/*.yaml[/COLOR]
[COLOR=#008000]# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager[/COLOR]
helios@helios:~
(i)$ [COLOR=#0000ff]sudo dmesg | grep wlx[/COLOR]
[COLOR=#008000][   37.068146] rtl8821cu 1-10:1.0 [/COLOR][COLOR=#ff0000]wlx[/COLOR][COLOR=#008000]bc0f9af583ad: renamed from wlan0
[   84.630244] IPv6: ADDRCONF(NETDEV_CHANGE): [/COLOR][COLOR=#ff0000]wlx[/COLOR][COLOR=#008000]bc0f9af583ad: link becomes ready
[  524.599675] rtl8821cu 1-12:1.0 [/COLOR][COLOR=#ff0000]wlx[/COLOR][COLOR=#008000]bc0f9af583ad: renamed from wlan0
[  525.282764] IPv6: ADDRCONF(NETDEV_CHANGE): [/COLOR][COLOR=#ff0000]wlx[/COLOR][COLOR=#008000]bc0f9af583ad: link becomes ready[/COLOR]
helios@helios:~
(i)$ 

```

Best Regards,
Surya

---

### Post by surya.durgaputra on 2021-05-19
Also, I picked up another D-Link wifi dongle from work, just to check why D-Link is acting so strange with Linux. Its a bit old chipset - DWA-111 H/W Ver A1

And sure enough, exact same issues that I am facing with my current D-Link dongle I purchased two days ago. Does not get detected at all. D-Link seems to be a repeat offender.

---

### Post by chili555 on 2021-05-19
> Wi-Fi P2P device controlled by interface wlxbc0f9af583ad createdThis suggests that, in Network Manager, you have set the method of connection as 'Shared to other computers' and it should be 'Automatic (DHCP).' Please check and correct.

[IMG]https://i.postimg.cc/ydPL2vsM/Screenshot-from-2021-05-19-09-50-53.png[/IMG]

---

### Post by Yellow Pasque on 2021-05-19
> **surya.durgaputra said:**
> D-Link seems to be a repeat offender.

The chipset used is far more important than the vendor's logo on it. In fact, even the same model number can have different versions (V1, V2) with different chipsets, where one works perfectly on Linux and the other is a struggle (Netgear WNA-1100 comes to mind).

There is no reason that a D-Link product with chipset X should behave differently on Linux than any other vendor's product with chipset X.

---

### Post by surya.durgaputra on 2021-05-19
Hello chili555,
Thanks for your reply. I had those settings already enabled (the DNS was set to only Google public DNS 8.8.8.8, I added 8.8.4.4 as well, as indicated in your posting).
But now wifi is working and I think I know what happened. Am writing this here as I am sure others might face similar issue.

Per your and morrownr's fantastic help and suggestions, I installed the right driver from morrownr's link ([https://github.com/morrownr/8821cu](https://github.com/morrownr/8821cu)). Then the wifi dongle started working but it did not show up as an icon on top right ubuntu system tray area (showing available networks to connect). I am pretty sure that this happened because when you asked me to check if available networks are getting scanned (```
[COLOR=#0000ff]sudo iwlist scan
```[/COLOR]), they were in-fact getting scanned and the command output showed it. It was my own stupid mistake to not check settings->**Wi-Fi** section (it was not showing available networks to connect before I installed the right drivers). 

It was your last post, recommending me to check my connection method (Automatic DHCP) that made me goto settings ->Wi-Fi and there I saw the available networks to connect. It was only after I connected to a network, that the wifi icon appeared in top-right ubuntu system tray. Usually, when I put a dongle in the USB slot, the icon appears (whether a wifi icon with connection bars or wifi icon with **?** inside) but this time, with this D-Link dongle it did not happen even after I had the drivers installed and working correctly.

I see the signal strength captured by this dongle as quite weak, but at least I have wifi now. 

In the middle of all this D-Link vs Linux drama, I picked up another wavlink ac1200 router/range-extender that provides wired-ethernet connectivity to my desktop. This one works OK on Linux with no issues. If D-Link keeps giving me dramas, it will goto landfill and will switch to wavlink. Will definitely check recommendations here before getting another wifi adapter.

**Thank You** all for your support and help. You guys rock.

Best Regards,
Surya

---

### Post by morrownr on 2021-05-19
> **surya.durgaputra said:**
> Hello chili555,

Will definitely check recommendations here before getting another wifi adapter.

**Thank You** all for your support and help. You guys rock.



Surya,

Glad to hear you are on the air again. I had pulled most of my hair out because after the clean up and installation of the correct driver, everything you posted told me it was working. Glad chili555 came to the rescue.

About that quote above about checking recommendations before getting another wifi adapter...

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

You can also find that link in the very top sticky post if you forget it. That link has everything you ever want to know about wifi and Linux... well, maybe not but it is recommended reading for those looking to buy a usb wifi adapter. 

Good luck and take care.

morrownr

---

