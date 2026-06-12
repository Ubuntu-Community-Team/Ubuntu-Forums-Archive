---
title: "Wi-Fi Network Adapter"
date: 2016-08-29
forum: Networking &amp; Wireless
---

### Post by smittward on 2016-08-29
Hello everyone!

I'm pretty new to Linux, and need help with installing a driver. Currently, my computer has an internal WiFi adapter that can only connect to 2.4 GHz, so I bought one of those small WiFi adapters that you plug into your USB (here's the link to it: [https://www.amazon.com/Wireless-Network-Adapter-802-11AC-Wholesale/dp/B00W5UHQ8M](https://www.amazon.com/Wireless-Network-Adapter-802-11AC-Wholesale/dp/B00W5UHQ8M)). This one let's me connect to 5.0 GHz which would GREATLY increase my WiFi speed from about 10 Mbps to around 150 Mbps. It works great on my Windows installation (I have Linux dual-booted). When I installed the driver on Windows I noticed an option for Linux, so I'm pretty sure I could get this to work. On the CD that came with it I found two files that might have the drivers in it; one is a tar.bz2 and one is a .zip. The problem is, I can't seem to figure it out how to actually get it to install. Any help is greatly appreciated!

Thanks again!

Here are two photos of the files I found on the CD:

[ATTACH=CONFIG]270924[/ATTACH][ATTACH=CONFIG]270923[/ATTACH]

---

### Post by howefield on 2016-08-29
Thread moved to the "*Networking & Wireless*" forum.

Might be helpful if you could post the output of the wireless script as described in this [sticky thread]("https://ubuntuforums.org/showthread.php?t=370108").

---

### Post by smittward on 2016-08-29
> **howefield said:**
> Thread moved to the "*Networking & Wireless*" forum.

Might be helpful if you could post the output of the wireless script as described in this [sticky thread]("https://ubuntuforums.org/showthread.php?t=370108").


Sure thing! Here's the file that I got:

[ATTACH]270925[/ATTACH]

---

### Post by smittward on 2016-08-30
One thing I've tried is running the install.sh script I found on the CD through terminal, but then I get this:

[http://paste.ubuntu.com/23110386/](http://paste.ubuntu.com/23110386/)

I've tried with and without using "sudo" and it still fails.

---

### Post by Bucky Ball on 2016-08-30
Generally the Linux wireless drivers on the CD that comes with wireless dongle are a waste of time.

Please open a terminal and post the output of these two commands for the moment if you can't get the wirelessinfo working.

```
sudo lshw -C network
iwconfig 
```

Your card may be recognised and have the right drivers already and this may not be related to that but something else.

(* This may be a silly question as I'm sure you've checked, but your router/access point is capable at delivering at the 5Ghz speeds you're looking for? Have you tweaked the router configuration to make sure it is set to work at 5Ghz? You may need to do this manually on the router config. Open a web browser and type the IP address of your router in the address bar, hit enter.)

---

### Post by smittward on 2016-08-30
> **Bucky Ball said:**
> Generally the Linux wireless drivers on the CD that comes with wireless dongle are a waste of time.

Please open a terminal and post the output of these two commands for the moment if you can't get the wirelessinfo working.

```
sudo lshw -C network
iwconfig 
```

Your card may be recognised and have the right drivers already and this may not be related to that but something else.

(* This may be a silly question as I'm sure you've checked, but your router/access point is capable at delivering at the 5Ghz speeds you're looking for? Have you tweaked the router configuration to make sure it is set to work at 5Ghz? You may need to do this manually on the router config. Open a web browser and type the IP address of your router in the address bar, hit enter.)

Alright, here's what I got:

```
patrick@patrick-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Ethernet Connection (2) I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 00
       serial: d0:50:99:4b:7d:1d
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f7200000-f721ffff memory:f7238000-f7238fff ioport:f040(size=32)
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 01
       serial: 68:1c:a2:06:e9:67
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.4.0-34-generic firmware=N/A ip=10.0.0.77 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7100000-f717ffff memory:f7180000-f718ffff
patrick@patrick-desktop:~$ iwconfig
wlp3s0    IEEE 802.11bgn  ESSID:"HOME-24AD-2.4"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 74:85:2A:D1:2F:38   
          Bit Rate=57.8 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1300   Missed beacon:0


lo        no wireless extensions.


enp0s25   no wireless extensions.
```





Also, as for your question about my router, the adapter works perfectly fine in Windows 10. It connects to the 5 GHz and the speed is very good.

---

### Post by chili555 on 2016-08-30
We are confused. Your attempt to compile the circa-2011 driver was for an rtl8192cxx device. The drivers for it are already present in 16.04.

But wait, it gets even better!!!

Your wireless script shows:> ##### lsusb #############################

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 045e:076f Microsoft Corp. 
Bus 003 Device 004: ID [COLOR="#FF0000"]0e8d:7610 MediaTek Inc. [/COLOR]
Bus 003 Device 003: ID 048d:1345 Integrated Technology Express, Inc. Multi Cardreader
Bus 003 Device 002: ID 046d:c24d Logitech, Inc. G710 Gaming Keyboard
Bus 003 Device 007: ID 0d8c:0005 C-Media Electronics, Inc. 
Bus 003 Device 006: ID 046d:c07d Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubThat device uses the driver mt7610 that has to be compiled from source code. I have tried to compile it in 16.04 with a zillion warnings and no assurance that it will work. If it were me, I'd return the device in favor of a fully supported adapter.

---

### Post by smittward on 2016-08-30
> **chili555 said:**
> We are confused. Your attempt to compile the circa-2011 driver was for an rtl8192cxx device. The drivers for it are already present in 16.04.

But wait, it gets even better!!!

Your wireless script shows:That device uses the driver mt7610 that has to be compiled from source code. I have tried to compile it in 16.04 with a zillion warnings and no assurance that it will work. If it were me, I'd return the device in favor of a fully supported adapter.



Aw man, okay well thanks for the help. Not sure if I can return it because I've been using it for a long time on Windows and have just recently installed Ubuntu in a dual boot. Any recommendations for a good adapter?

---

### Post by chili555 on 2016-08-30
> **smittward said:**
> Aw man, okay well thanks for the help. Not sure if I can return it because I've been using it for a long time on Windows and have just recently installed Ubuntu in a dual boot. Any recommendations for a good adapter?Not that I have tried. There are many threads here about supported devices.

---

### Post by smittward on 2016-08-30
> **chili555 said:**
> Not that I have tried. There are many threads here about supported devices.


Alright, I'll look around, thanks again for the help everyone. Do I now just put "solved" as the thread title?

---

### Post by Bucky Ball on 2016-08-31
> **smittward said:**
> Do I now just put "solved" as the thread title?

Not quite. You use Thread Tools at the top of this page and choose 'Mark thread as solved'. :)

If you can't find it there see the last link in my signature below. Thanks and good luck.

---

### Post by kurt18947 on 2016-08-31
> **smittward said:**
> Aw man, okay well thanks for the help. Not sure if I can return it because I've been using it for a long time on Windows and have just recently installed Ubuntu in a dual boot. Any recommendations for a good adapter?

I'll stick my neck out a little bit here. My linux/wifi hardware knowledge is dated so keep that in mind. My wifi devices are mostly Intel these days which is pretty well supported. One USB adapter that seems to have a pretty good rep is Netgear's WNA1100 and may be available in retailers like Staples or Office Depot. It is limited to 150 mb./sec. single band 2.4 ghz. though. Here's a source for hardware that will in all likelihood work with Linux:

```
https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux
```

Another source I've found valuable is wikidevi.com. You can enter a device and find the status of linux support. As Chili555 says, spend some time searching this forum. Adapters that support the latest standards like 802.11 AC tend to be scarce and lists of supported devices tend to not be maintained so are out of date, unfortunately.

---

### Post by smittward on 2016-08-31
> **Bucky Ball said:**
> Not quite. You use Thread Tools at the top of this page and choose 'Mark thread as solved'. :)

If you can't find it there see the last link in my signature below. Thanks and good luck.


Okay, cool I found it. Thanks for the help!

---

### Post by smittward on 2016-08-31
> **kurt18947 said:**
> I'll stick my neck out a little bit here. My linux/wifi hardware knowledge is dated so keep that in mind. My wifi devices are mostly Intel these days which is pretty well supported. One USB adapter that seems to have a pretty good rep is Netgear's WNA1100 and may be available in retailers like Staples or Office Depot. It is limited to 150 mb./sec. single band 2.4 ghz. though. Here's a source for hardware that will in all likelihood work with Linux:

```
https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux
```

Another source I've found valuable is wikidevi.com. You can enter a device and find the status of linux support. As Chili555 says, spend some time searching this forum. Adapters that support the latest standards like 802.11 AC tend to be scarce and lists of supported devices tend to not be maintained so are out of date, unfortunately.


Ah, okay, that makes sense. The thing is though, I've done speed tests on multiple devices connecting to the 2.4 GHz frequency and they all cap out around 10 Mbps. Is it just the router or could this be because of some hardware limitation? The only reason I bought the adapter I did was because it had the ability to connect to 5 GHz which is much faster.

---

### Post by Bucky Ball on 2016-08-31
What speeds are you expecting from your ISP? How are you checking the speed? With a speed test like [this one]("http://www.speedtest.net/")?

If you ISP is only guaranteeing 10Mbps, that's what you'll get, regardless of hardware. You could check this if you don't know on the 'Critical Information Summary' (all ISP plans must have one of these in Australia, not sure about elsewhere) which you'll find online if there is one.

---

### Post by kurt18947 on 2016-08-31
> **smittward said:**
> Ah, okay, that makes sense. The thing is though, I've done speed tests on multiple devices connecting to the 2.4 GHz frequency and they all cap out around 10 Mbps. Is it just the router or could this be because of some hardware limitation? The only reason I bought the adapter I did was because it had the ability to connect to 5 GHz which is much faster.

When I was limited to 2.4 Ghz., I was seeing around 50 mb./sec. even though the devices are theoretically capable of 150 mb./sec. I now have a Netgear router running DD-WRT dual band and iwconfig shows 90 - 108 mb./sec in the 5 Ghz. band. I presume you're aware that range/signal strength in the 5 Ghz. band is weaker than 2.4. I don't use wifi if I have a choice and have a MoCA network courtesy of the ISP's use of MoCA for its channel guide & pay-per-view functions. It so happens that MoCA will also provide 100 Mb./sec ethernet with the addition of an adapter at a coax outlet. Wired ethernet is superior IME if mobility is not required - more stable, more secure. I know all the beautiful girls on TV are using portable wifi devices but oh well:).

---

### Post by smittward on 2016-09-01
> **Bucky Ball said:**
> What speeds are you expecting from your ISP? How are you checking the speed? With a speed test like [this one]("http://www.speedtest.net/")?

If you ISP is only guaranteeing 10Mbps, that's what you'll get, regardless of hardware. You could check this if you don't know on the 'Critical Information Summary' (all ISP plans must have one of these in Australia, not sure about elsewhere) which you'll find online if there is one.


Yeah, I use speedtest.net to check. On 2.4 GHz I get around 10 Mbps. On Windows where the adapter I bought works and can connect to the 5 GHz, I get 100+ Mbps consistently. I have also used speedtest.net to check speeds on my phone which can connect to the 5GHz frequency and it also achieves high speeds of about 170 Mbps.

---

### Post by smittward on 2016-09-01
> **kurt18947 said:**
> When I was limited to 2.4 Ghz., I was seeing around 50 mb./sec. even though the devices are theoretically capable of 150 mb./sec. I now have a Netgear router running DD-WRT dual band and iwconfig shows 90 - 108 mb./sec in the 5 Ghz. band. I presume you're aware that range/signal strength in the 5 Ghz. band is weaker than 2.4. I don't use wifi if I have a choice and have a MoCA network courtesy of the ISP's use of MoCA for its channel guide & pay-per-view functions. It so happens that MoCA will also provide 100 Mb./sec ethernet with the addition of an adapter at a coax outlet. Wired ethernet is superior IME if mobility is not required - more stable, more secure. I know all the beautiful girls on TV are using portable wifi devices but oh well:).


Oh I totally agree, I would use Ethernet if I could. Unfortunately, my PC is on a different floor as my router :(

---

### Post by chili555 on 2016-09-01
Humor an old tinkerer and let's see if we can get the internal device to work better.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. If these changes are ineffective, I suggest that you also experiment with B and G only, disabling N. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

   ```
 sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
gksudo gedit /etc/default/crda
```

Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:

```
sudo modprobe -r ath9k
sudo modprobe ath9k  nohwcrypt=1
```

If it helps, make it permanent:

```
sudo -i
echo "options ath9k  nohwcrypt=1"  >>  /etc/modprobe.d/ath9k.conf
exit
```

---

### Post by smittward on 2016-09-02
> **chili555 said:**
> Humor an old tinkerer and let's see if we can get the internal device to work better.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. If these changes are ineffective, I suggest that you also experiment with B and G only, disabling N. After making these changes, reboot the router. 




Sweet! The first part with changing the router settings helped instantly. I'm getting about 20-25 Mbps now. The encryption was the combined one so I changed it to the AES one and I changed the channel from 6 (which was the automatic one) to 1. I tried all the other commands, but I didn't see any other changes... but thank you for basically doubling my speed!

---

