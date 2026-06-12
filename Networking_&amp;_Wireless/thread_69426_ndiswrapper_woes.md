---
title: "ndiswrapper woes"
date: 2005-09-26
forum: Networking &amp; Wireless
---

### Post by augereffect on 2005-09-26
I have just been trying to install ndiswrapper according to the instructions at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation).
I have gotten to the point of installing the windows driver with ndiswrapper -i <driver>.inf, and it will give me this:
Installing <driver>
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter RadioState|0 to RadioState|1
Forcing parameter RadioState|0 to RadioState|1
Then, when I try ndiswrapper -l, it tells me 
Installed ndis drivers:
<driver> invalid driver!
What do I do now?  I know this is probably very simple, but I know almost nothing of Ubuntu.

Thanks.

---

### Post by mlomker on 2005-09-26
> What do I do now?  I know this is probably very simple, but I know almost nothing of Ubuntu.

Is this a laptop with a BIOS or hardware switch that turns on the wireless card?  It sounds like it is failing to turn on the card.

---

### Post by lordofkhemenu on 2005-09-26
[quote=mlomker]Is this a laptop with a BIOS or hardware switch that turns on the wireless card?  It sounds like it is failing to turn on the card.[/quote]
I second that. I had a laptop that had a hardware switch to turn the wifi on/off. A "d'oh" moment when i finally looked and saw it was off

---

### Post by Zelut on 2005-09-26
I get "driver present, hardware present" but when I run 'sudo modprobe ndiswrapper' I get this error.

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

### Post by augereffect on 2005-09-27
I don't think there is a BIOS or hardware switch, because I have used this card with windows on the same computer.  Is this some kind of really obvious linux thing that needs to be adjusted?

---

### Post by mlomker on 2005-09-27
> I have used this card with windows on the same computer.

Well, that doesn't mean a lot.  The driver is designed for Windows, so it'd turn the card on when it is loaded...ndiswrapper won't do that.

I have yet to see a laptop that didn't have a BIOS setting, hardware switch, or a Function hotkey that enabled/disabled the card.  My previous laptop used a Function key and my current one has the button.

> 
Is this some kind of really obvious linux thing that needs to be adjusted?

Unfortunately you won't know until after you find it.  I've scoured the forums on issues like this because people post about them every day and I haven't found a magic setting that'll fix every card.  All the laptops are a little different.  You can often discover a lot by searching Google for you machine's **model# linux**.  Even if it's a different version of linux, ndiswrapper is still the same.

---

### Post by Zelut on 2005-09-27
I just got mine working again and I noticed that I had to reinstall for it to work.  My guess is it has something to do with the latest kernel updates we've been getting.  I had originally updated with the latest kernels & then tried ndiswrapper with no success.

Last nite I did a fresh install & did the ndiswrapper config before I did the updates.  Everything worked perfectly on the first try...

---

### Post by augereffect on 2005-09-27
Big breakthrough!

I successfully installed a different version of the driver, and it seems to work fine.  It says the hardware is present.  I'm having issues with configuration now.  I have been following the instructions at [http://ubuntuforums.org/showthread.php?t=19978](http://ubuntuforums.org/showthread.php?t=19978) 
and I have gotten to step 6, where you put in "iwconfig"  Here's what I get:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3
          RTS thr:2432 B   Fragment thr:2432 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-95 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So far, this seems good.  The computer seems to acknowledge the existance of the card.  Then I put in "ifconfig" and it gives me this:

wlan0     Link encap:Ethernet  HWaddr 00:90:47:07:2A:33
          inet6 addr: fe80::290:47ff:fe07:2a33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:11000000-110000ff

Supposedly this is supposed to show me whether I have a connection to an access point and an IP address.  "iwconfig wan0 essid <00:90:47:07:2A:33 - what I think is the access point> gives me this:
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wan0 ; No such device.

Someone said that from this point, I just needed to use "networking" from system administration, but I don't know what to do with that.  I don't know what my access point is called, (news to me that it had any designation at all) and it has no WEP key.  It is also worth noting that the LEDs on the card are not lighting up.  Could anyone enlighten me as to how to make this work?

Thanks

---

### Post by mlomker on 2005-09-27
> "iwconfig wan0 essid <00:90:47:07:2A:33 - what I think is the access point> gives me this:
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wan0 ; No such device.


**wlan0**

The essid is whatever name you configured in your access point.  You'll have to look at the settings if you don't know.  The default is often *linksys* or similar.  The **iwlist wlan0 scan** command is supposed to give you a list (I've had mixed results with that).

---

### Post by Zelut on 2005-09-27
You can find your access point name by going to [http://192.168.0.1](http://192.168.0.1) or sometimes [http://192.168.1.100](http://192.168.1.100) (depending on the make/model).  If you haven't changed the settings it'll most likely be the default name (ie; linksys, netgear, etc).

If you look in the network settings in System > Admin you may need to set 'this card is configured' and activate it.  That may be all you need to do..

---

### Post by augereffect on 2005-09-27
One more piece of progress.  It now gives me this when I use dhclient:

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:a0:c5:94:75:8d
Sending on   LPF/wlan0/00:a0:c5:94:75:8d
Sending on   Socket/fallback
the ip here looks wrong should it not be my routers ip?
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

The doodad in the corner of the screen registers the wireless network, but says its disconnected.  What do I do now?  And what's the ESSID thing?  And what if my network doesn't have a wep key?

Thank you very much for your patience.


P.S. Similar problem:  [http://ubuntuforums.org/showthread.php?t=69669](http://ubuntuforums.org/showthread.php?t=69669)

---

### Post by mlomker on 2005-09-27
Post the output of **iwconfig** and **ifconfig wlan0** at the least.

Haven't you looked at the configuration of your access point yet?  You installed it and that's something we can't check for you.

The link that you provide is a guy who has encryption turned on in his access point, I'm sure.

---

