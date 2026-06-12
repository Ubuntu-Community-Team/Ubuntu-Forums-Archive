---
title: "WPA/WPA2 Problem on a Broadcom BCM4328"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by ninjapenguin on 2008-06-25
I got my wireless driver set up, and it shows that it sees other networks, but when I try to connect to my network that has WPA/WPA2 it just hangs there with out any of the 2 dots turning green, and then after a minute it asks me for my user name and password again.

obel@Linux-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:270 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

obel@Linux-Ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:52:7C:62:C6
                    ESSID:"Obel"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

I installed my wireless driver through "Windows Wireless Drivers"
Do I need to set up wpa_supplicant? And if so how do I do so?

---

### Post by cwbar_1 on 2008-06-25
Yes, you do need the WPA_Supplicant.
System> Administration>Synaptic Package Manager....then search for and  install the supplicant.

As a side note;  You might want to download WICD, completely remove network manager, and install WICD.  (I've found that it works much better with encrypted networks)

---

### Post by ninjapenguin on 2008-06-25
> **cwbar_1 said:**
> Yes, you do need the WPA_Supplicant.
System> Administration>Synaptic Package Manager....then search for and  install the supplicant.

It says I already have version 0.6.0+0.5.8-0ubuntu2 installed.  I mean I can choose if I want to use WPA or WPA2 when I try to connect, but it never actually connects to the network, so I was wondering if I have to configure wpa_supplicant.

---

### Post by cwbar_1 on 2008-06-25
Please see the additional side note. You and I were probably typing responses at the same time!

---

### Post by ninjapenguin on 2008-06-25
> **cwbar_1 said:**
> Please see the additional side note. You and I were probably typing responses at the same time!

Okay I got WICD installed and network manager gone. . . but I am still not being able to connect to my network. . . do I need to have the PSK in hex instead of deca?

---

### Post by cwbar_1 on 2008-06-25
[https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=577210](https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=577210) is where you find the correct WICD to download.  Choose the WICD *****all.deb.  Then you need to completely remove (through synaptics) network-manager & network-manager-gnome. Then double click on the WICD .deb file and it will install.  *******Make sure to read [http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq) **** prior to installation.  It will give the instructions for set-up.

OK! Go to Applications> Internet > WICD... Click on the arrow next to your network. Go to advanced settings and configure from there.  Under preferences.. wext is usually the correct supplicant.  If not, try the others.  Don't forget to reboot after all the changes!

---

### Post by ninjapenguin on 2008-06-25
> **cwbar_1 said:**
> [https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=577210](https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460&release_id=577210) is where you find the correct WICD to download.  Choose the WICD *****all.deb.  Then you need to completely remove (through synaptics) network-manager & network-manager-gnome. Then double click on the WICD .deb file and it will install.  *******Make sure to read [http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq) **** prior to installation.  It will give the instructions for set-up.

Yeah I read through that and tried the whole " " around my psk, but it still doesn't get an IP from my wireless network.  :confused:  I mean my wi-fi works on xp, so I am guessing there might be something weird on my settings.  For wireless supplicant do I choose broadcom, ndiswrapper, or wext?

---

### Post by cwbar_1 on 2008-06-25
Wext is usually the correct supplicant on this card. (I have the same one)  Have you re-booted?

---

### Post by ninjapenguin on 2008-06-25
> **cwbar_1 said:**
> Wext is usually the correct supplicant on this card. (I have the same one)  Have you re-booted?

Yeah I rebooted and tried again with using wext as the supplicant and using " " around my psk and no quotes and no luck

---

### Post by cwbar_1 on 2008-06-25
Bump. Anyone?

---

### Post by ninjapenguin on 2008-06-26
> **cwbar_1 said:**
> Bump. Anyone?
Does anyone know what's wrong with what I am doing or can give some insight of how I can figure it out?

---

### Post by pokipoki08 on 2008-06-26
I'm using a LCD iMac, with the same card (4328 rev. 03), but can't get it to work with WPA2. You may want to try different drivers.

Are you using a Mac by any chance? I have a few different drivers for this card if you want them.

$ sudo lspci -vv

```
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
	Subsystem: Apple Computer Inc. Unknown device 0087
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 256 bytes
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at 88200000 (64-bit, non-prefetchable) [size=16K]
	Region 2: Memory at 88000000 (64-bit, prefetchable) [size=1M]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=2 PME-
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [d0] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
		Device: Latency L0s <4us, L1 unlimited
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM unknown, Port 0
		Link: Latency L0s <4us, L1 <64us
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1

```

---

### Post by ninjapenguin on 2008-06-26
I am using a 24in iMac, and connecting to encrypted wifi is the onlything that i just cannot get working right now.  So if you have any drivers that you have used that worked for you, I would appreciate it a lot if you posted them.

---

### Post by pokipoki08 on 2008-06-26
The drivers install successfully in ndiswrapper and I can join WPA2 networks with wpa_supplicant (or manual config in /etc/network/interfaces) **[COLOR="Red"]BUT[/COLOR]** the connection dies after 10 mins or so.

5 sets of drivers for you to try. These drivers work well in WinXP connecting to WPA2 networks.

[COLOR="Magenta"]**Apple Airport drivers for Broadcom 4328 (multiple sources)**[/COLOR]

```

bcmwl5-unknown
Broadcom (Leopard Bootcamp CD)
Broadcom 802.11n Network Adaptor - WinXP (Leopard Bootcamp CD)
BroadcomXP (Leopard Bootcamp CD)
dell
```

Maybe you will have better luck.

Driver download
[http://rapidshare.com/files/125227252/airport-broadcom-4328.tar.gz.html](http://rapidshare.com/files/125227252/airport-broadcom-4328.tar.gz.html)

PS I gave up on Airport and bought a Edimax EW-7318USg, WPA2 connection is good after using Serial Monkeys driver & module recompile. No problems at all.

---

### Post by ninjapenguin on 2008-06-26
> **pokipoki08 said:**
> The drivers install successfully in ndiswrapper and I can join WPA2 networks with wpa_supplicant (or manual config in /etc/network/interfaces) **[COLOR="Red"]BUT[/COLOR]** the connection dies after 10 mins or so.

5 sets of drivers for you to try. These drivers work well in WinXP connecting to WPA2 networks.

[COLOR="Magenta"]**Apple Airport drivers for Broadcom 4328 (multiple sources)**[/COLOR]

```

bcmwl5-unknown
Broadcom (Leopard Bootcamp CD)
Broadcom 802.11n Network Adaptor - WinXP (Leopard Bootcamp CD)
BroadcomXP (Leopard Bootcamp CD)
dell
```

Maybe you will have better luck.

Driver download
[http://rapidshare.com/files/125227252/airport-broadcom-4328.tar.gz.html](http://rapidshare.com/files/125227252/airport-broadcom-4328.tar.gz.html)

PS I gave up on Airport and bought a Edimax EW-7318USg, WPA2 connection is good after using Serial Monkeys driver & module recompile. No problems at all.

Thank you for your help I will try out these drivers some time soon!!

---

### Post by ninjapenguin on 2008-06-30
Alright I finally got a chance to try out those drivers and none of them work and the dell one froze up my computer . . . so I am still with out wifi on my iMac :(

---

### Post by pravinbravi on 2008-09-13
Hi all,

I have MBP 4th gen, Ubuntu Hardy Heron 8.04 (2.6.24-21) the boot camp drivers for BCM4328 via ndiswrapper work ok, but for the occasional freeze when switching from WPA wifi network to other WPA wifi. Apple uses BCM4328 rev 5 wifi card in the newer  MBPs.

Haven't given a try with WPA2. Its unfortunate but WPA2 doesn't work with ndiswrapper+BCM4328 rev 5.

My advise is stick to the boot camp drivers, since they work fine in winXP.

also refer to these for some insight:
[http://ubuntuforums.org/showthread.php?t=728530](http://ubuntuforums.org/showthread.php?t=728530)
[http://ph.ubuntuforums.com/showthread.php?t=725544](http://ph.ubuntuforums.com/showthread.php?t=725544)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[http://lists.berlios.de/pipermail/bcm43xx-dev/2008-February/006894.html](http://lists.berlios.de/pipermail/bcm43xx-dev/2008-February/006894.html)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg715155.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg715155.html)

---

### Post by sillyxone on 2008-09-14
I have a Macbook with BCM4328 Rev 03, same problem: using bcmwl5 from broadcomxpinstaller.exe with ndiswrapper, connect to unsecured network just fine but not WPA network.

After playing around for 3 hours yesterday, now I have it working with WPA (connect automatically at boot, after suspend, can use it for hours without dropping). The problem is I don't know exactly what made it works so I just document everything I did, see if you can figure out what the problem was.


Before yesterday, I had Wicd 1.4.1 and the bcmwl5 from broadcomxpinstaller. 

- Install Wicd 1.5.1 ([http://voxel.dl.sourceforge.net/sourceforge/wicd/wicd_1.5.1_all.deb](http://voxel.dl.sourceforge.net/sourceforge/wicd/wicd_1.5.1_all.deb)). Still cannot connect (WPA set to wext).

- Download Dell driver R140746.exe, extract to ~/DellBCM using Archive Manager
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R140746&SystemID=INS_PNT_P4_9400&os=WXPX&osl=en&deviceid=9805&devlib=0&typecnt=1&vercnt=2&formatcnt=1&libid=5&fileid=187886](http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R140746&SystemID=INS_PNT_P4_9400&os=WXPX&osl=en&deviceid=9805&devlib=0&typecnt=1&vercnt=2&formatcnt=1&libid=5&fileid=187886)

- run ndiswrapper with option -r and -i to remove the old driver and install the new driver. Restart Wicd (daemon and client). Suddenly it can connect to my WPA network, but when I click Disconnect then Connect, it didn't connect again.
```

pkill wicd-client
sudo ndiswrapper -r bcmwl5
sudo ndiswrapper -i ~/DellBCM/DRIVER/bcmwl5.inf
sudo modprobe ndiswrapper
sudo /etc/init.d/wicd restart
/usr/bin/wicd-client
```

- I knew that the driver is correct, so there must be something to do with initializing it. I tried removing and installing driver with ndiswrapper, modprobe, and stopping/starting Wicd a few times to see the pattern but it appeared to be random success. 

- I edit /etc/modprobe.d/aliases, comment out IPv6 lines
```

#alias net-pf-10 ipv6
#alias net-pf-16-proto-13 ip6_queue
```

- upon rebooting, it got a long pause at the Ubuntu startup screen, with the progress bar somewhere in the middle. Then when logging into Gnome, Wicd has already connected to the network. Disconnect then reconnect work just fine. Wicd automatically connect after suspending. 

- I tried to figure out what made it work by reverting what I did. But when I re-enable IPv6 aliases, restart, it still connect OK. I don't have the broadcomxpinstaller.exe driver with me so I haven't tried to revert back to see if it won't work again. Now I couldn't break it.

I will keep using it for a few day and see if I'll have any update, but at least it is working now.

UPDATE: it stopped connecting after I shut the computer down for 4 hours. However, I found that if Wicd won't connect, it stuck at "Validating authentication". By switching the WPA driver to ndiswrapper (in Wicd preferences), connect, fail, then switch back to wext, it will connect OK 90% of the time.

---

### Post by eanbowman on 2008-09-16
This solution made the adapter show up at least. I used the Dell driver.

Thanks! :D

---

### Post by eanbowman on 2008-09-17
When I try to connect, it always gives me three lines in my dmesg output:

[   58.602745] NET: Registered protocol family 17
[   59.549038] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   63.001767] wlan0: no IPv6 routers present

Now, I know that my ancient wireless router isn't going to likely route IPv6 properly. Why is it even trying? I took the suggestion above and commented out the aliases pointing to IPv6 in the /etc/modprobe.d/aliases file.

Any clues?

---

