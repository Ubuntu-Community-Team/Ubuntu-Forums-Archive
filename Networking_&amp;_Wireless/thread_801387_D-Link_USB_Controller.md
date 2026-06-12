---
title: "D-Link USB Controller"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by komputes on 2008-05-20
I have this D-Link Wifi USB Adapter and when I plug it in, Ubuntu doesn't configure it automatically in Hardy and keeps disconnecting on Gutsy. here are some specs on the device:


```

$dmesg
May 20 15:52:18 ubuntu kernel: [  103.344578] usb 4-4: new high speed USB device using ehci_hcd and address 3
May 20 15:52:18 ubuntu kernel: [  103.364383] usb 4-4: configuration #1 chosen from 1 choice
May 20 15:52:18 ubuntu kernel: [  103.455967] p54common: Unknown symbol ieee80211_free_hw
May 20 15:52:18 ubuntu kernel: [  103.456013] p54common: Unknown symbol ieee80211_alloc_hw
May 20 15:52:18 ubuntu kernel: [  103.456057] p54common: Unknown symbol ieee80211_wake_queue
May 20 15:52:18 ubuntu kernel: [  103.456127] p54common: Unknown symbol ieee80211_tx_status_irqsafe
May 20 15:52:18 ubuntu kernel: [  103.456203] p54common: Unknown symbol ieee80211_stop_queue
May 20 15:52:18 ubuntu kernel: [  103.456242] p54common: Unknown symbol ieee80211_stop_queues
May 20 15:52:18 ubuntu kernel: [  103.456285] p54common: Unknown symbol ieee80211_register_hwmode
May 20 15:52:18 ubuntu kernel: [  103.456334] p54common: Unknown symbol ieee80211_rx_irqsafe
May 20 15:52:18 ubuntu kernel: [  103.456700] p54usb: Unknown symbol p54_parse_eeprom
May 20 15:52:18 ubuntu kernel: [  103.456826] p54usb: Unknown symbol p54_parse_firmware
May 20 15:52:18 ubuntu kernel: [  103.456882] p54usb: Unknown symbol ieee80211_free_hw
May 20 15:52:18 ubuntu kernel: [  103.456977] p54usb: Unknown symbol ieee80211_register_hw
May 20 15:52:18 ubuntu kernel: [  103.457342] p54usb: Unknown symbol p54_free_common
May 20 15:52:18 ubuntu kernel: [  103.457399] p54usb: Unknown symbol p54_rx
May 20 15:52:18 ubuntu kernel: [  103.457449] p54usb: Unknown symbol ieee80211_unregister_hw
May 20 15:52:18 ubuntu kernel: [  103.457488] p54usb: Unknown symbol p54_init_common
May 20 15:52:18 ubuntu kernel: [  103.457587] p54usb: Unknown symbol p54_fill_eeprom_readback

```It looks like this but i'm unsure of the model number since i have no caps, stickers or documentation.

[IMG]http://images.dlink.com/products/DWL-G122/DWL-G122_main.jpg[/IMG]

---

### Post by mapes12 on 2008-05-20
In a terminal window:

```
sudo lshw
```

what is the output under:

*-network

---

### Post by MaindotC on 2008-05-20
Also ```
lsusb
``` should give a more detailed description of the device.

---

### Post by komputes on 2008-05-21
lsusb 
Reported the device as:
2001:3704 D-Link Corp. [hex] DWL-G122 802.11g rev. A2

lshw
Has been stuck on "PCI (sysfs)" for over half an hour now with absolutely no output


The tricky thing about this adapter is that there were many made with different revision numbers, so instructions for one may not work on the other. Looks like this is the page for this adapter:

[http://support.dlink.ca/products/view.asp?productid=DWL-G122_revA2](http://support.dlink.ca/products/view.asp?productid=DWL-G122_revA2)

and the Ubuntu site which lists user experiences with this controller here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) #SCROLL TO BOTTOM

I also found the following which I believe was made for the original one (revision A1):
[https://help.ubuntu.com/community/WifiDocs/Device/DWL-122](https://help.ubuntu.com/community/WifiDocs/Device/DWL-122)

Should I attempt to use the windows driver through NDISwrapper or do can you guys recommend a native driver that can be used with this device?

---

### Post by mapes12 on 2008-05-21
> lshw
Has been stuck on "PCI (sysfs)" for over half an hour now with absolutely no output

Hhhhmmmm........standard Linux query command not responding?

If I we're you (which I'm not obviously) this is what I would do:

1. Buy myself a laptop wireless adaptor (USB or PCMCIA) that is supported in Linux natively). I had to do this to get my Thinkpad T23 working. Get back to me if you want a recommendation. Mine cost me the princely sum of £10 and it works flawleslly straight out of the box. No configuring. No ndiswrapper hassle.

2. Given that ```
sudo lshw
```does nothing on your machine I would start to wonder if any of my filesystem files had become corrupted somewhere along the way. Therefore, I would carry out a fresh install of Ubuntu with the natively supported wireless card installed so that Ubuntu detected and configured it.

There may be other forum members that can offer alternative solutions but the above is my humble opinion.

---

### Post by pedrodonte on 2008-05-21
Step 1
need to download the device driver from
[http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)

Step 2
decompress the package with:
  # tar xvfz rt73-cvs-daily.tar.gz

Step 3
enter the directory Modules
  # cd rt73-cvs-2008051215
  # cd Module

Step 4
Compiling and Installing
  # make
  # make install

Step 5
run
  # modprobe rt73

Step 6
  # iwconfig
wlan1     **RT73** WLAN  ESSID:"WiFiUNACH-II"  
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:18:0A:50:00:F7   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=56/100  Signal level:-66 dBm  Noise level:-99 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by komputes on 2008-05-22
@mapes12
1. I always welcome working 802.11 cards, although I am pretty anal about what I want on it. WEP/WPA/WPA2 all out of the box G standard (no a, b or n).

2. No corruption, just Hardy. Same PC in Gutsy, sudo lshw works fine.


@pedrodonte
How did you come to the conclusion that Revision A2 contains a rt73 compatible chipset. Please note that not all revisions have the same chipset, but I'll still test this. Have your tried this yourself with an  DWL-G122 802.11g rev. A2? Can you possibly post the same instructions in pastebin (to avoid emoticons). Thanks again!

---

### Post by komputes on 2008-05-23
I remembered that for some reason this was being detected and could see AP's and connect for a little while before it gets disconnected on Ubuntu 7.10. So I put it in and it uses the p54 driver in Gutsy and network manager take care of it, but nothing in Hardy. 


Pedrodonte,
After loading the rt73 module, I unplugged the device and plugged it back in and I believe that it is still using the p54 driver. I'm afraid your solution did not work.

```

$dmesg
May 24 00:08:41 ubuntu kernel: [ 2798.040235] usb 3-5: new high speed USB device using ehci_hcd and address 5
May 24 00:08:41 ubuntu kernel: [ 2798.177368] usb 3-5: configuration #1 chosen from 1 choice
May 24 00:08:41 ubuntu kernel: [ 2798.197540] p54: LM86 firmware
May 24 00:08:41 ubuntu kernel: [ 2798.636238] phy1: hwaddr 00:11:95:8e:2c:b3, isl3887
May 24 00:08:41 ubuntu kernel: [ 2798.674640] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

```
$lsmod
Module                  Size  Used by
rt73                  215808  0 
p54usb                 16256  0 
p54common              13312  1 p54usb
mac80211              171016  3 rc80211_simple,p54usb,p54common
cfg80211                7304  1 mac80211
```

Any recommendations?

---

### Post by komputes on 2008-05-23
I also tried the instructions for ndiswrapper here:

[https://wiki.ubuntu.com/NdisWrapper_DWL-G122](https://wiki.ubuntu.com/NdisWrapper_DWL-G122)


Doesn't seem to work either:
```

Module                  Size  Used by
ndiswrapper           185240  0
```

---

### Post by alpage2 on 2008-05-24
> **komputes said:**
> lsusb 
Reported the device as:
2001:3704 D-Link Corp. [hex] DWL-G122 802.11g rev. A2

....and the Ubuntu site which lists user experiences with this controller here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) #SCROLL TO BOTTOM

....Should I attempt to use the windows driver through NDISwrapper or do can you guys recommend a native driver that can be used with this device?

Your link above for the list of supported wifi adapters contains an entry for the A2 revision:

> 
USB stick - works well in Breezy with ndiswrapper (the one provided in synaptic), with the drivers provided on the CD. Also works with Feisty but you need to blacklist prism54usb driver.


So it looks like ndiswrapper is the way to go, not forgetting to blacklist any other prism drivers present that could interfere.

Good luck
Alan

---

### Post by komputes on 2008-05-24
On the Linux p54usb Driver it says the following:

If you have a second-generation device, please use this firmware: 2.5.8.0 firmware and copy it to /usr/lib/hotplug/firmware/isl3887usb_bare.

[http://jbnote.free.fr/prism54usb/IdentifyYourDevice.html](http://jbnote.free.fr/prism54usb/IdentifyYourDevice.html)


I have confirmed that mine is a 2nd generation Prism54USB type card. I can't seem to find the directory structure that was explained in the "updating firmware" part of this web page, so I skipped over that part. Must I create every level of this structure /usr/lib/hotplug/firmware/isl3887usb_bare since I only have /usr/bin/.


--
What I have done
--

1) Went to the D-Link website and downloaded the driver. And went to [http://jbnote.free.fr/prism54usb/](http://jbnote.free.fr/prism54usb/) and downloaded p54 usb driver.

2) Put the .sys file in the Windows XP directory and the .inf file in the same directory (Please note that this driver comes with two .sys files).

3) 
  sudo ndiswrapper -i ~/drivers/drivername.inf
  sudo depmod -a
  sudo modprobe ndiswrapper

$ndiswrapper -l
prisma02 : driver installed
    device (2001:3704) present (alternate driver: p54usb)

Now that I have native and ndiswrapper drivers installed, how can I switch to ndiswrapper and back again to test which driver works better. I will try backlisting p54usb. Do I have to blacklist it or is the a way to manually swap one for another?

---

### Post by Bikerbob on 2008-09-08
HOw has your luck been with this issue?

I have the rev. A1 card.. and I am not having much luck getting it working on my desktop at all.

The A1 uses the p54usb for sure.. and I know the windows driver does work with ndiswrapper.. I just need to get the commands straight.. and hope it works in 8.0.4 I tried it in 7.10 I think.

James

---

### Post by komputes on 2008-09-09
Hi James, I gave up on this one, but I think I still have the hardware somewhere. I just ended up purchasing a compatible (works out of the box) adapter for my friend. If you have any luck making this work, feel free to update me, otherwise I'll just be waiting for a future version to support it (if this is possible).

---

### Post by Bikerbob on 2008-09-09
Well I know that this is supposed to work both with ndiswrapper and with the p54usb driver.

Now the driver seems to be a little more tricky as to the hardware.. but I have heard success with ndiswrapper.. where the problem comes in is with the security, I dont think you can get WPA with ndiswrapper.

But yeah.. I will post here.. I am going to try Xubuntu as well.. as I think with a little slimer less chucky linux that was designed to be used on less than brand new hardware it will be easier to work with.

James

---

### Post by mscdex on 2008-09-09
I just installed (xubuntu) hardy (8.04.1) and out of the box my dwl-g122 A2 seems to be recognized and working. However, I notice that as soon as it tries to query the dns server (?) the driver craps out and i'm no longer able to ping anything on the network.

I did some searching and found most people simply used ndiswrapper to get it working but I didn't want to have to resort to that unless absolutely necessary. So, I went to the prism54 driver site and attempted to download and copy over the "wireless-testing" firmware version (for second-gen usb, and renaming the file accordingly as mentioned at the bottom of [here]("http://www.linuxwireless.org/en/users/Drivers/p54")) to /lib/firmware/<kernel version>/. However that firmware was rejected by p54usb, so I tried the "old firmware" link and it worked! I can now download updates and whatnot just fine, and no ndiswrapper!

The direct link to the firmware I used is [here]("http://www.prism54.org/firmware/2.5.8.0.arm").

Hope this helps someone else out there having similar issues (at least with this A2 revision).

EDIT: Spoke too soon, however the connection lasted much longer than the firmware that ships with hardy. Hmmm...

---

### Post by Bikerbob on 2008-09-09
yeah.. I have found that 804 would load a non-compatible firmware with my dongle.

I get an connot read eeprom error.

I need to get other firmware.. but 804 includes a whole bunch of the p54usb firmwares.. I looked.. so not sure why its not picking the correct one.. and I am not sure how to force it to pick another.

James

---

