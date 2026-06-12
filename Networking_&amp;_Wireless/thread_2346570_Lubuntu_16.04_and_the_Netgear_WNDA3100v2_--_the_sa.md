---
title: "Lubuntu 16.04 and the Netgear WNDA3100v2 -- the saga continues"
date: 2016-12-16
forum: Networking &amp; Wireless
---

### Post by Louie IV on 2016-12-16
Howdy,

I'm trying to get lubuntu 16.04 to use a Netgear WNDA3100v2 on my Acer AspireOne 722. 

The reasons: The onboard 2.5 ghz wireless g adapter on this thing is abysmally slow. I can't watch a youtube video at 420 without it halting. As to the reason I chose this netgear device that doesn't play nice with ubuntu -- it's the one I already had from a previous windows PC.

So: I have installed the drivers from #6 on this thread [https://ubuntuforums.org/showthread.php?t=2052594](https://ubuntuforums.org/showthread.php?t=2052594) using the process through #17 on this thread [https://ubuntuforums.org/showthread.php?t=1964173&highlight=wnda3100](https://ubuntuforums.org/showthread.php?t=1964173&highlight=wnda3100).

Network Manager doesn't recognize the new interface -- and if it did, I'm not sure how to tell lubuntu to ignore the onboard.

Here are all the outputs I have checked:

> louie@louie-AO722:~$ lsusb
Bus 002 Device 002: ID 04f2:b209 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

louie@louie-AO722:~$ iwconfig
lo        no wireless extensions.

enx803773b880c7  IEEE 802.11g  ESSID:off/any  ### This is the netgear device
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

enp6s0    no wireless extensions.

wlp7s0    IEEE 802.11abg  ESSID:"ArgosNet" ### This is the onboard device
          Mode:Managed  Frequency:2.462 GHz  Access Point: 48:5D:36:AF:07:B2   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

louie@louie-AO722:~$ ifconfig
enp6s0    Link encap:Ethernet  HWaddr b8:88:e3:04:ee:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:22825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:5546129 (5.5 MB)  TX bytes:5546129 (5.5 MB)

wlp7s0    Link encap:Ethernet  HWaddr 08:ed:b9:41:ef:d0  
          inet addr:192.168.1.157  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1ace:c688:45ca:2d07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3780439 errors:0 dropped:0 overruns:0 frame:291654
          TX packets:367241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1372056800 (1.3 GB)  TX bytes:34122949 (34.1 MB)
          Interrupt:19 

If this is a sisyphean task, just let me know and I'll live with choppy video -- or start a new thread to try to make this onboard card run faster.

Thanks,

---

### Post by chili555 on 2016-12-16
> try to make this onboard card run faster.
Let's try it first. For the time-being, leave the Netgear (mercifully) unplugged. 

What is the internal device?```
lspci -nnk | grep 0280 -A2
```Have you tried all the usual tweaks?

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by Louie IV on 2016-12-16
Hi, got it. 

lspci is:
>  louie@louie-AO722:~$ lspci -nnk | grep 0280 -A2
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Foxconn International, Inc. BCM4313 802.11bgn Wireless Network Adapter [105b:e042]
	Kernel driver in use: wl 

As to dealing with the router, I have limited ability to change the settings. It's a Verizon fiOs router, and I don't have the option to fine tune. I know it's capable of N speeds, because my other laptop runs like a top.

As to the regulatory domain (which is new ground for me. I've been learning linux from reading forums) here's the output.

> louie@louie-AO722:~$ sudo iw reg get
[sudo] password for louie: 
country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)


I haven't followed the next steps for that, because I don't know what I'm doing.

I have set the Network manager to ignore ipv6.

---

### Post by chili555 on 2016-12-16
This guy suggests that the best driver is not wl, the Broadcom STA driver, but brcmsmac. [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

On the off chance that he's right, let's try it:```
sudo -i
apt-get purge bcmwl-kernel-source
echo "blacklist b43"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us hear your report.

---

### Post by Louie IV on 2016-12-16
We may be on to something. There's improvement in general browser speed. Video streaming at 480p is mostly seemless, although 720+ still stutters. My internet connection is 100 mbs fiber, but my download speed on this machine tops out at 30 mbs, and uploads top out at 8 mbs. Not sure if that's just the limit of the hardware or a driver issue.

---

### Post by chili555 on 2016-12-16
Let's have a look at how the router is set up:```
sudo iwlist scan
```Please just show us your network and obscure the MAC address: xx:xx:etc.

---

### Post by Louie IV on 2016-12-16
ha, whelp, that produced a huge output of every wifi network within range, I think. I didn't find my ESSID listed though. anyway to pull an abbreviated scan, or get a prompt so I can go through them?

---

### Post by chili555 on 2016-12-16
Your network should be very apparent by name and signal strength. Here is a sample from my machine:```

wlp3s0    Scan completed :
          Cell 01 - Address: xx:2B:B0:DC:45:xx
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    [COLOR="#FF0000"]ESSID:"GBR5"[/COLOR]
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002723098457c
                    Extra: Last beacon: 676ms ago
                    IE: Unknown: 000447425235
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 030195
                    IE: Unknown: 07425553202401112801112C01113001113401173801173C01174001176401176801176C01177001177401178401178801178C011795011E99011E9D011EA1011EA5011E
                    IE: Unknown: 200103
                    IE: Unknown: 2D1AEF091BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D16950D0600000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: Unknown: BF0CB2018033EAFF0000EAFF0000
                    IE: Unknown: C005019B00FCFF
                    IE: Unknown: C30402C4C4C4
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```And, of course, when I click the Network Manager icon, it says I'm connected to GBR5.

You can scroll through them with:```
sudo iwlist scan | less
```

---

### Post by Louie IV on 2016-12-16
That was the ticket. I'm in a large apartment building, so the output was more than terminal would allow me to scroll. Here's my info:

> wlp7s0b1  Scan completed :
          Cell 01 - Address: 48:5D:36:AF:07:B2
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-20 dBm  
                    Encryption key:on
                    ESSID:"ArgosNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001773f22e7da
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 00084172676F734E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000


---

### Post by chili555 on 2016-12-16
Better news than I expected! You are using WPA2-CCMP (aka AES) on channel 11. No need so far for laser surgery.

Let's see what the logs say:```
dmesg | grep -e wlp -e brcm
```What does this report for speed?

[https://fast.com/](https://fast.com/)

---

### Post by Louie IV on 2016-12-16
Great news. 

Here's the log: 

> 
louie@louie-AO722:~$ dmesg | grep -e wlp -e brcm
[   19.823818] brcmsmac bcma0:1: mfg 4bf core 812 rev 24 class 0 irq 19
[   19.840927] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 499
[   19.847730] brcmsmac bcma0:1 wlp7s0b1: renamed from wlan0
[   24.205800] IPv6: ADDRCONF(NETDEV_UP): wlp7s0b1: link is not ready
[   24.563831] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   24.563855] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[   24.564503] IPv6: ADDRCONF(NETDEV_UP): wlp7s0b1: link is not ready
[   25.165696] IPv6: ADDRCONF(NETDEV_UP): wlp7s0b1: link is not ready
[   26.465617] wlp7s0b1: authenticate with 48:5d:36:af:07:b2
[   26.469887] wlp7s0b1: send auth to 48:5d:36:af:07:b2 (try 1/3)
[   26.473731] wlp7s0b1: authenticated
[   26.485108] wlp7s0b1: associate with 48:5d:36:af:07:b2 (try 1/3)
[   26.494391] wlp7s0b1: RX AssocResp from 48:5d:36:af:07:b2 (capab=0x431 status=0 aid=1)
[   26.494965] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[   26.494977] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   26.495008] wlp7s0b1: associated
[   26.495126] IPv6: ADDRCONF(NETDEV_CHANGE): wlp7s0b1: link becomes ready
[   26.509812] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 159/256 dur 1778/1504
[   26.525809] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 137/256 dur 1602/1504
[   27.063652] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 2321.044972] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 153/256 dur 1730/1504
[ 5918.814807] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 153/256 dur 1730/1504
[ 9517.262629] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 153/256 dur 1730/1504
[13116.121740] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 153/256 dur 1730/1504
[16714.920472] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 153/256 dur 1730/1504
[16715.920175] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 153/256 dur 1730/1504
[20310.321535] brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211:  txop exceeded phylen 153/256 dur 1730/1504


And I ran fast.com three times over a minute or so. It registered at 3.8 mbs, 2.4 mbs and 4.8 mbs. Womp, womp, woooommmmp.

Thanks for all the help.

---

### Post by Louie IV on 2016-12-16
Ahh -- scratch that. At the time of writing, my lovely wife was downloading a massive file in the other room. Fast.com clocks this at 33 mbs.

---

### Post by chili555 on 2016-12-16
> Fast.com clocks this at 33 mbs.That should certainly be fast enough for 720p streaming...however, we see:> brcmsmac bcma0:1: wl0: brcms_c_d11hdrs_mac80211: txop exceeded phylen 153/256 dur 1730/1504A Google search finds a few complaints about the partly-working driver brcmsmac but no resolution. 

If 33 Mbps does well enough for you, we're all set. If not, we can blacklist it and work on the Netgear, about which I have little hope.

There are also a few fully  supported USB wireless devices that sell for $12-15 US that we can recommend.

What is your preference?

---

### Post by Louie IV on 2016-12-17
Yes, I see. 720p is still a out of reach, but I will not subject you to further Netgear hell. What inexpensive usb devices do you recommend?

Thanks again for all your help,

---

### Post by chili555 on 2016-12-17
I have and recommend one of these: [https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/ref=sr_1_1?s=electronics&ie=UTF8&qid=1481987305&sr=1-1&keywords=tl-wn722n](https://www.amazon.com/TP-Link-N150-Wireless-Adapter-TL-WN722N/dp/B002SZEOLG/ref=sr_1_1?s=electronics&ie=UTF8&qid=1481987305&sr=1-1&keywords=tl-wn722n)

---

### Post by Louie IV on 2016-12-24
Thanks, i will definitely check it out. Merry Christmas!

---

