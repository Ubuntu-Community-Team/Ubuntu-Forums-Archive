---
title: "D-Link G650M PCMCIA Wifi card not recognized by Ubuntu Feisty?"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by amadorc on 2007-08-29
Hello,
I've installed recently Ubuntu Feisty in my notebook, and the wireless networking doesn't work. I've searched for help in several web pages and forums, and found that for some people this card works almost "out of the box". I have Windows 2000 installed in the same computer, and the card works properly, so it is not a hardware problem. It looks like the card is detected, the **lspci** command shows it:
[INDENT][I]00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 88)
02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 88)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5005VL 802.11bg Wireless NIC (rev 01)[/I][/INDENT]
On the other hand, Network Manager shows only modem and ethernet connections. The ouptut for **iwconfig** command is:
[INDENT][I]lo no wireless extensions.

eth0 no wireless extensions.[/I][/INDENT].
Executing **dmesg** command shows no error messages. I've also tried using Windows drivers (several versions) with **ndiswrapper**, without any result. Maybe there is a problem with PCMCIA drivers? Any idea about what can I do to find where the error is?
Thanks in advance.

---

### Post by bmartin on 2007-08-29
There are a couple of options you have. You can try [MadWifi]("http://ubuntuforums.org/showthread.php?t=485579") which was written specifically for Atheros chipsets. I can't find your specific chipset listed; it **might** work. I have an AR5007EG, which is listed as working... but it doesn't.

I highly recommend ndiswrapper. It's the only way I could get my Atheros chipset to work. Grab the correct wireless drivers for your card (get the newest XP ones, **not Vista**) and I can walk you through the process of uninstalling any existing ndiswrapper drivers and installing the appropriate one for your card.

---

### Post by amadorc on 2007-08-30
Thanks for you answer.
I've tried **madwifi**, and it doesn't work. With **ndiswrapper** I've tried all the drivers I could get. The one that came in the card CD couldn't be installed, showing an error. I've downloaded several versions from DLink support, the drivers install correctly but the card didn't work.
I'm now thinking that it could be a PCMCIA driver problem. **dmesg** shows no error, but...
Do you know any command I could try or config file to look into to see if PCMCIA is working correctly?

---

### Post by bmartin on 2007-08-30
There is a **pccardctl** command. If you type **pccardctl ls** you should see a list of your PCMCIA devices. **lspci** seems to show your chipset, though, so I imagine it's working.

What I would do is the following (from a terminal):
This should remove all of the installed ndiswrapper drivers:
```
for dr in $(ndiswrapper -l | grep -o "\w* :" | grep -o "\w*" ); do sudo ndiswrapper -e $dr; done
```
Then, check to see if there are any ndiswrapper drivers still installed.
```
ndiswrapper -l
```
If any ndiswrapper drivers remain, perform the following command for each one:
```
sudo ndiswrapper -e (driver)
```
Lastly, grab, extract, and install the Windows driver:
```
wget "http://us.zyxel.com/upload/download_library/M-102 Drivers.zip"
unzip "M-102 Drivers.zip"
cd "M-102 Drivers"
sudo ndiswrapper -i net5513.inf
```

Those are the correct drivers for you wireless card, according to [this page]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/").

---

### Post by amadorc on 2007-08-31
I see you're searched the driver based on the chipset. I had searched with the card name, and the result in **ndiswrapper** web was:
[INDENT][I]47. Card: D-Link DWL-G650M
    * Chipset: Atheros
    * Driver: No madwifi support yet. Use ndiswrapper and net5513.inf found on driver CD.[/I][/INDENT]
So I used the driver on the card CD, but it was net5522.inf (not net5513.inf), and failed to install. Then I searched in D-Link support web page and found this one: [http://www.dlink.com/products/support.asp?pid=386&sec=0#drivers]("http://www.dlink.com/products/support.asp?pid=386&sec=0#drivers")
It installs correctly, but didn't work. I also tried with another driver found with Google, with the same result.

As you suggest, it could a good idea to use the driver for the same chipset but from different brand. I've searched again in the **ndiswrapper** site and found this:
[INDENT]25. Card: D-Link DWL-G520M Wireless 108G MIMO Desktop Adapter (bought in UK)
    * Chipset: Atheros Communications, Inc. AR5005VL 802.11bg Wireless Chipset (rev 01)
    * pciid: 168c:0020 (rev 01)
    * Driver: ar5513.sys and net5513.inf from [ftp://ftp.dlink.co.uk/wireless/dwl-g520m/dwl-g520m_drv_v1-1b3.zip](ftp://ftp.dlink.co.uk/wireless/dwl-g520m/dwl-g520m_drv_v1-1b3.zip)
    * Other: Fedora Core 5 and ndiswrapper from livna repository (utils: 1.8, driver: 1.13, vermagic: 2.6.16-1.2122_FC5 686 REGPARM 4KSTACKS gcc-4.1). Works with WEP. Not tested beyond a few hours of continuous operation.
[/INDENT]
It's from the same brand and family, but different model. I think I'll try this one first (the inf file says it is also for DWL-G650M, and date is newer); if it fails, I'll try the Zyxel driver you stated. 
I'll tell you if this works. Thanks!

---

### Post by amadorc on 2007-09-03
I've already tried both drivers, without any success. The Zyxel driver didn't worked. As the drivers I tried before, it does nothing.

The D-Link G520 driver (that is suposed to support also the G650M card) freezes my Ubuntu! I restarted the computer, and it freezed again by the half of start progress bar. It only started correctly when I removed the PCMCIA card from the computer. If I try to insert the card when running, Ubuntu freezes again. This makes me think that there should be some kind of driver conflict here, but I don't know how to find it...

---

### Post by bmartin on 2007-09-03
I think you're right. The D-Link G520 driver seems like it's probably the correct one. You'll have to try blacklisting drivers until you figure out which one it is. My guess is that it's **ath_pci** or **ath_usb** or something like that. You can blacklist it with the following:
```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```
To remove it from the list of blacklisted drivers, edit /etc/modprobe.d/blacklist and comment out or remove that line.

---

### Post by amadorc on 2007-09-05
I couldn't find **ath_pci** nor **ath_usb** nor any **ath*** in loaded driver list. They are madwifi drivers, isn't it? Well, I uninstalled madwifi when started trying with ndiswrapper, that's why they're not present. In any case, I've searched through **lsmod** results trying to guess which driver could cause the conflict, without result. So, I decided to start from scratch. I've removed the **net5513** driver from **ndiswrapper** and went back to the very beginning...
- the hardware is recognized, as it appears on **lshw** results:
```
     *-network UNCLAIMED
          description: Ethernet controller
          product: AR5005VL 802.11bg Wireless NIC
          vendor: Atheros Communications, Inc.
          physical id: 1
          bus info: pci@03:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0 maxlatency=28 mingnt=10
          resources: iomemory:3c000000-3c01ffff irq:11
```
  as I can see, there is no driver attached.
- the card is listed in **lspci** output.
- the card is not listed in **sudo pccardctl ident**:
```
Socket 0:
  no product info available
Socket 1:
  no product info available
```
- As I've seen in [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")
there could be a problem with PCI bridge. The output of **sudo lspci -v | grep subordinate** shows:
```
 Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
 Bus: primary=00, secondary=02, subordinate=0a, sec-latency=32
 Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
 Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
```
and the output of **dmesg | grep assign-busses** shows:
```
[   41.844738] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[   41.844801] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
```
so I added **pci=assign-busses** to the boot line and restarted. Nothing changed, except the **dmesg** output.
- now the PCI bridge seems to be OK, I've tried to load again the Windows driver with **ndiswrapper**. No success.

I think tomorrow I will try again **madwifi** drivers, but I have no hope it makes my card run...

---

### Post by amadorc on 2007-09-16
Some good news.

Inspired by some readings about PCMCIA card problems, I've added the option **pci=noacpi** to the boot line. After restarting, I've tried again to load all the drivers available with **ndiswrapper**, one by one, until with one of them... the *wlan0* interface appeared in **iwconfig** output!
Hope this can help to someone with the same problem.

However, there's a little fault: if I start the computer with the card inserted, the computer freezes by about the half of the start progress bar. I can start without the card and insert it once the system has started. It seems to work, so this is only a little inconvenience.

Now I've installed wpa_supplicant, and I'll try to make my card work with WPA-PSK encryption as I have it configured in Windows. Wish me luck!

---

### Post by W. Irving on 2007-09-17
I just bought one of these cards myself, and am having trouble getting it to work. So far only with ndiswrapper using the driver available at Dlink.com (net5513). Having the driver loaded and inserting the card hangs the system.
Going to try with madwifi now.

```
     *-network UNCLAIMED
          description: Ethernet controller
          product: AR5005VL 802.11bg Wireless NIC
          vendor: Atheros Communications, Inc.
          physical id: 1
          bus info: pci@07:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          configuration: latency=0 maxlatency=28 mingnt=10
          resources: iomemory:c8000000-c801ffff irq:11

```

---

### Post by W. Irving on 2007-09-17
It occurred to me I hadn't tried the driver on the CD, so this is what I did, and found three files this time - an extra net5513.cat - as opposed to two which were what I got from the download. After restoring ndiswrapper (downloading and compiling 1.47) and installing the driver the system no longer hangs when inserting the card.
But no luck connecting, so executed wpa_supplicant and noticed this line:

```
Driver does not support WPA.
```

If ndiswrapper and the driver are set up properly at my end, then we can probably assume that ndiswrapper is not the way forward - at least not if you require WPA.
Most peculiar.

Switching off the encryption in my router does let me associate with it.

---

### Post by W. Irving on 2007-09-17
[http://madwifi.org/ticket/181](http://madwifi.org/ticket/181)

In short - looks like there's nothing we can do to get this working at the moment.

---

### Post by amadorc on 2007-09-19
Hi W.Irving,
a quick summary: I had to add **pci=assign-busses** and **pci=noacpi** to the boot line in order to get my card properly recognized. I'm using **ndiswrapper** as installed with Synaptic, not compiled by myself. I tried 3 drivers:
[LIST]
[*]the one that cames in the card CD. It was **net5522**, no **net5513**, and it didn't worked.
[*]the one downloaded from the spanish support site. The card shown has blue label, as mine. It didn't worked. The link, if you want to try it: [[COLOR="RoyalBlue"]ftp://ftp.dlink.es/Wireless%20MIMO/DWL-G650M/Drivers/Ver.%203.00/DWL-G650M_Driver%203-00%20WHQL.rar[/COLOR]]("ftp://ftp.dlink.es/Wireless%20MIMO/DWL-G650M/Drivers/Ver.%203.00/DWL-G650M_Driver%203-00%20WHQL.rar")
[*]the one downloaded from the general support site. This site states that there are 2 versions of the card, one with blue label as mine (Revision B2) that has no drivers to download, and one with green label (Revision A1 & B1) which has the following drivers to download: [[COLOR="RoyalBlue"]ftp://ftp.dlink.com/Wireless/dwlg650M/Drivers/dwlg650m_driver_101.zip[/COLOR]]("ftp://ftp.dlink.com/Wireless/dwlg650M/Drivers/dwlg650m_driver_101.zip").
This is the driver I'm using now, and it seems to work.
[/LIST]
Now I'm trying to configure WPA security. I 've get it working, but not in a stable manner: it seems to be a problem with some parameter and the order the lan and wpa_supplicant are loaded. Thus, I still haven't been able to configure it properly to run from boot, I must reconfigure it every time the computer is restarted. Sometimes it work, sometimes not.

---

### Post by W. Irving on 2007-09-19
Mine's a version B3 (pictured below), and nowhere have I found hardware version dependant drivers for download.
[IMG]http://www.dlink.se/archivos/2333-845-Imagen/dwl-g650m.jpg[/IMG]

These are the drivers I have found so far, with md5 checksums and dates:

**CD** (marked Version 3.00)
[LIST]
[*]ar5513.sys (fbe18577f160f0d3ca79234c317729d9), 2005-09-13 00:48
[*]net5513.cat (5483e62c9de8f2ff08947ba3070d3c17), 2005-10-13 22:22
[*]net5513.inf (4364d03afda97043aff10676c605b3de), 2005-09-26 12:29
[/LIST]

**Dlink.se** (2.1b7, 18-01-2006)
[LIST]
[*]ar5513.sys (fbe18577f160f0d3ca79234c317729d9), 2005-09-13 06:48
[*]net5513.cat (5483e62c9de8f2ff08947ba3070d3c17), 2005-10-14 04:22
[*]net5513.inf (4364d03afda97043aff10676c605b3de), 2005-09-26 18:29
[/LIST]

**Dlink.com** (1.01, "Shipping Version", 7/12/2005)
[LIST]
[*]ar5513.sys (7fe7c1958b27dc9a92873df24485701b), 2004-12-24 16:34
[*]net5513.inf (0efacf519a4ef80132e6611286938271), 2004-12-30 19:31
[/LIST]

So the Dlink.se and CD versions are the same, but they do not mention any hardware version.
I can't get ndiswrapper in the repos to install properly (complaining about a missing file), but compiling and using 1.47 works great. I'm not touching the Dlink.com driver again though, but the other works well enough for me to be able to set mode, ESSID and channel (when unencryption is off on my router). I was wrong when claiming I was able to associate with the router - I can't. The problem seems to be the bit rate - my router is a vanilla 54Mbit Zyxel router, and the Dlink card defaults to 108Mbit - so;
```
elias@trotsky:~/Desktop/dlinkcd$ sudo iwconfig wlan0 rate 54M
elias@trotsky:~/Desktop/dlinkcd$ iwconfig 
lo        no wireless extensions.

irda0     no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Eter"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Bit Rate=108 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

elias@trotsky:~/Desktop/dlinkcd$ sudo dmesg -c
[80953.100000] ndiswrapper (iw_set_bitrate:493): setting bit rate failed (C0010017)
elias@trotsky:~/Desktop/dlinkcd$
```

And that's pretty much a cul-de-sac for me.
Left to try: pci=assign-busses pci=noacpi kernel params, and having a stab at getting the Ubuntu ndiswrapper to work.
Perhaps 7.10 holds any surprises, if not I guess I'll have to wait for the ath_hal. Over a year and a half now. Serves me right for not researching compatibility for making a purchase. ](*,)

And for the record, this is what my card is reported as by lshw:
```
     *-network DISABLED
          description: Wireless interface
          product: AR5005VL 802.11bg Wireless NIC
          vendor: Atheros Communications, Inc.
          physical id: 1
          bus info: pci@07:00.0
          logical name: wlan0
          version: 01
          serial: 00:15:e9:d6:e5:5a
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper+net5513 driverversion=1.47+D-Link,09/12/2005,1.0.0.56 latency=128 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
          resources: iomemory:c8000000-c801ffff irq:11

```
..and lspci...
```
07:00.0 Ethernet controller: Atheros Communications, Inc. AR5005VL 802.11bg Wireless NIC (rev 01)
07:00.0 0200: 168c:0020 (rev 01)

```

---

