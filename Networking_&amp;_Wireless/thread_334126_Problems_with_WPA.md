---
title: "Problems with WPA"
date: 2007-01-08
forum: Networking &amp; Wireless
---

### Post by Trinity001 on 2007-01-08
Hi there,

I'm trying to get the USB-Wlan-Stick (rt73) running under Ubuntu 6.10 to connect to D-Link DI 524. It recently worked with WEP but as I switched to WPA it won't connect any more. For WindowsXP and PalmOS it worked so it can't be a problem with the router or Wlan-Stick. Probably I did something wrong. I configured the wpa_supplicant and this is what is configured and the outputs after configuration:

root@Deepthought:/home/trinity# iwlist rausb0 scan
rausb0 Scan completed :
Cell 01 - Address: 00:18:9A:6A:0A:A7
ESSID:"WLAN"
Mode:Managed
Channel:6
Encryption key:on
Bit Rates:0 kb/s

root@Deepthought:/home/trinity# iwconfig rausb0
rausb0 RT73 WLAN ESSID:""
Mode:Auto Frequency=1 MHz Bit Rate=54 Mb/s
RTS thr:off Fragment thr:off
Encryption key:off
Link Quality=0/100 Signal level:-121 dBm Noise level:-115 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


root@Deepthought:/home/trinity# less /etc/network/interfaces
auto rausb0
iface rausb0 inet dhcp
wpa-conf /root/wpa_supplicant.conf



root@Deepthought:/home/trinity# less /root/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
ssid="WLAN"
proto=WPA WPA2
key_mgmt=WPA-PSK
pairwise=CCMP TKIP
group=CCMP TKIP WEP104 WEP40
auth_alg=OPEN
priority=2
psk=XXXXXXXXXXXXXXXXX
}
/root/wpa_supplicant.conf (END)


root@Deepthought:/home/trinity# dmesg | grep rt73
[17179595.956000] usbcore: registered new driver rt73
[17179596.412000] Loading module: rt73usb - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[17179596.412000] usbcore: registered new driver rt73usb
[17179596.816000] rt73 driver version - 1.0.3.6


It seems as if the driver is loaded properly, it should, because it was working before I switched to WPA. The SSID is always empty on 'iwconfig rausb0' but I can't set it manually.
What about the mode? It is auto shouldn't it be 'managed'. But I also cannot set it manually. On scanning via the device it finds the AccessPoint.

Thanks for any help.

-- a desperate Trinity

---

### Post by wieman01 on 2007-01-08
If you want to go for a manual solution, try the HOWTO in my signature. There is a sample configuration for WPA-PSK using TKIP further down in the thread (DHCP). Give it go and post a message if you get stuck.

---

### Post by Trinity001 on 2007-01-08
Thanks, I found it after repost - sorry. I need to reboot my computer to check it and give it a try.

---

### Post by Trinity001 on 2007-01-08
It doesn't work :-(.

Here is the manual configuration now:

auto rausb0
iface rausb0 inet dhcp
	wpa-driver wext
	wpa-conf managed
	wpa-ssid WLAN
	wpa-ap-scan 1
	wpa-proto WPA
	wpa-pairwise TKIP
	wpa-group TKIP
	wpa-key-mgmt WPA-PSK
	wpa-psk MyPassphrase


And this is what restart of networking says:

Listening on LPF/rausb0/00:0e:e8:f8:19:15
Sending on   LPF/rausb0/00:0e:e8:f8:19:15
Sending on   Socket/fallback
DHCPRELEASE on rausb0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device rausb0 ; Network is down.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Sorry for my stupid question, but what does it mean by 'network is down'? It is runninf and shown in ifconfig. And a scan does show my AccessPoint

---

### Post by wieman01 on 2007-01-08
Can you show me the whole file please? 
> sudo gedit /etc/network/interfaces
Not quite sure what's going on.

---

### Post by Trinity001 on 2007-01-08
There is not  much more in the file. This is the complete one:

auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto rausb0
iface rausb0 inet dhcp
	wpa-driver wext
	wpa-conf managed
	wpa-ssid WLAN
	wpa-ap-scan 1
	wpa-proto WPA
	wpa-pairwise TKIP
	wpa-group TKIP
	wpa-key-mgmt WPA-PSK
	wpa-psk MyPassphrase


Maybe I should deactivate the ones I don't need...all but rausb0

---

### Post by wieman01 on 2007-01-08
Are you sure your network is set to WPA and DHCP? I don't quite understand the error message. To shed some light on it, use this command to start up your network:
> sudo ifup -v rausb0
Please post the output.

---

### Post by Trinity001 on 2007-01-08
Yes I'm sure, because I'm currently running it this way for Windows now. DHCP and WPA-PSK/TKIP.

I need to reboot (it's a dual boot) - be back in a minute.

---

### Post by Trinity001 on 2007-01-08
This it what you requested:

trinity@Deepthought:~$ sudo ifup -v rausb0
Password:
ifup: interface rausb0 already configured


A ping still says that the network is unreachable:

trinity@Deepthought:~$ ping 192.1.1.1
connect: Network is unreachable

---

### Post by wieman01 on 2007-01-08
Please try this after booting:
> route
Then this:
> sudo ifdown rausb0
Finally:
> sudo ifup -v rausb0
Please post the output.

---

### Post by Trinity001 on 2007-01-08
This is it. I changed the  wpa-driver  to madwifi, because I saw in the other thread that it is more suitable for my D-Link router.

There is  no interface for rausb0 in the routing table :-/.

trinity@Deepthought:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.196.0   *               255.255.255.0   U     0      0        0 vmnet1
192.168.90.0    *               255.255.255.0   U     0      0        0 vmnet8

trinity@Deepthought:~$ sudo ifdown rausb0
Password:
There is already a pid file /var/run/dhclient.rausb0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/rausb0/00:0e:e8:f8:19:15
Sending on   LPF/rausb0/00:0e:e8:f8:19:15
Sending on   Socket/fallback
DHCPRELEASE on rausb0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device rausb0 ; Network is down.

trinity@Deepthought:~$ sudo ifup -v rausb0
Configuring interface rausb0=rausb0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device rausb0 ; Network is down.
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: wpa-driver madwifi
wpa_supplicant: /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.rausb0.pid -i rausb0 -D madwifi -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
ioctl[SIOCSIWPMKSA]: Network is down
ioctl[SIOCSIWMODE]: Network is down
Could not configure driver to use managed mode
ioctl[IEEE80211_IOCTL_SETPARAM]: Operation not supported
Failed to initialize driver interface
wpa_supplicant: waiting for "/var/run/wpa_supplicant/rausb0": 0 (max. 5)
wpa_supplicant: waiting for "/var/run/wpa_supplicant/rausb0": 1 (max. 5)
wpa_supplicant: waiting for "/var/run/wpa_supplicant/rausb0": 2 (max. 5)
wpa_supplicant: waiting for "/var/run/wpa_supplicant/rausb0": 3 (max. 5)
wpa_supplicant: waiting for "/var/run/wpa_supplicant/rausb0": 4 (max. 5)
wpa_supplicant: ctrl_interface socket not found at /var/run/wpa_supplicant/rausb0...aborting!
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1

dhclient3 -pf /var/run/dhclient.rausb0.pid -lf /var/lib/dhcp3/dhclient.rausb0.leases rausb0
There is already a pid file /var/run/dhclient.rausb0.pid with pid 5083
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/rausb0/00:0e:e8:f8:19:15
Sending on   LPF/rausb0/00:0e:e8:f8:19:15
Sending on   Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 7

---

### Post by wieman01 on 2007-01-08
I am not sure about the driver, but the driver has nothing to do with the router. It should correspond to your wireless adapter.

It appears there is driver issue. Can you connect to your wireless network when disabling all security? I would try that first.

---

### Post by Trinity001 on 2007-01-08
I used the USB-WLan-Stick for about three weeks now with ubuntu and WEP perfectly. Only switching to WPA destroyed everything :-/.

---

### Post by wieman01 on 2007-01-08
Going back to WEP is a easy, we can do that right away. I think there is an issue with the native driver for RT73. I don't think it really supports WPA. I used to have RT2570 and dropped it by replacing it with "ndiswrapper" and the native Windows driver. The Linux drivers are not ready yet.

Want to go back to WEP? I don't think WPA will work...

---

### Post by Trinity001 on 2007-01-08
Ok then. I guess it's easy for me to go back to WEP. Since I did it once, I could do it again on my own. Don't want to bother you with that.

There's no need to say, that I'm pretty disappointed :-(. Unfortunately WEP is not that secure as WPA, this is why I wanted to change that.

Is there any chance to get the WPA stuff runing with ndiswrapper?

I definitely won't do that today. I'm tired and it late and I have to get up early tomorrow.

Anyway, thank you very very much for your help.

---

### Post by wieman01 on 2007-01-08
You're welcome.

"ndiswrapper" should work. Check if you card is list [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"). If so, you could give it a go... There should be something concerning it in the forum, if not, drop me a message.

I am using "ndiswrapper" for the exact same reason... The drivers developed by "serialmonkey" are still fairly basic if not insufficient. But maybe you find something on their website that works for you: 

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page")

Talk to you then.

---

### Post by Trinity001 on 2007-01-08
Ok, I will try as soon as I have the time again. This Linux stuff robbed me so much time now :-(.

I'll keep you informed.

---

### Post by wieman01 on 2007-01-09
There is something concerning RT61 and WPA. Check it out:  

[http://www.ubuntuforums.org/showthread.php?t=296822]("http://www.ubuntuforums.org/showthread.php?t=296822")

---

### Post by Trinity001 on 2007-01-09
Thanks. I will check that after finishing work...and spend another afternoon and evening for Linux :-).

---

### Post by Trinity001 on 2007-01-09
I don't have the time (and nerves) to do it over and over again. I will use the ndiswrapper now, hoping, that it would help soon. 

Is there anything I need to take care of? I never used ndiswrapper and only found an instruction for it on the internet. Do I have to deactivate the old driver? And how should I do this?

Thanks...

---

### Post by wieman01 on 2007-01-09
You need to deactivate the old driver by blacklisting it. So please try to find out what your driver name is first... Then follow this howto:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

If you get stuck, post here, I will try to help you. Please note that "ndiswrapper" requires the correct Windows driver for your adapter. Makes sure that you have the latest one so that it supports WPA 1/2.

The HOWTO mentions "blacklist bcm43xx"... you need to replace "bcm43xx" with the correct driver that you are currently using.

---

### Post by Trinity001 on 2007-01-09
To find the appropriate driver is the first problem that occured. It says that the driver is not correct :-(. I don't know which one to use then.

I've found another instruction of how to install wpa with the rt73 device. I will try that first.

---

### Post by wieman01 on 2007-01-09
I think it's...
> RT2571
Quote:

[http://www.qbik.ch/usb/devices/drivers.php]("http://www.qbik.ch/usb/devices/drivers.php")

---

### Post by Trinity001 on 2007-01-09
So, the other instruction also doesn't work.

Thanks for the information. But what do I do with it now? I've found two *.inf-Files on my Windows distribution - both didn't work. One called rt73.inf and the other rt2500usb.inf.

BTW: What do ou mean by backlisting the old driver. Do you mean that I should delete it from modprobe.conf?

---

### Post by Trinity001 on 2007-01-09
Sorry, I didn't read you posting correctly. I know how to blacklist ist now. But nevertheless wouldn't it be enough to remove it from modprobe.conf?

---

### Post by Trinity001 on 2007-01-09
So this is it. I give it up for now. Obviously it would NEVER work. ndiwrapper doesn't work, the native driver doesn't work - and I've still other work to do, than messing around with this ubuntu stuff.

Thank you once again for your kind help. It's really good to know that there are still people out there, that intend to help others. Although it didn't help me :-(.

I will get back to WEP or use another AccessPoint instead of this USB-Device or try it once again in some days. Or throw the complete ubuntu-stuff away and switch back to Windows. I don't even know if I completely misconfigured my Linux distribution now, so that it wouldn't work in any case.

I'm really upset, because it keeps me busy for several weeks now. It's not your fault, but as I said: There's still more to do than this WLAN-stuff.

Thank you. I may be back in some days, but for now, it's enough ](*,) .

---

### Post by wieman01 on 2007-01-09
Understand your frustration, been through it myself. Sadly support for wireless networks & security in Ubuntu has yet to catch up with other operating systems.

If you want to give "ndiswrapper" a go nonetheless, drop me a note. I can guide you through the process. See you then.

---

### Post by Trinity001 on 2007-01-09
Yes, the frustration is bigger than expected, because everybody says that it's SO easy.

I WILL give ndiswrapper another try. Because I'm not satisfied and I WANT it to be working. But for now it's enough. In some days - when my frustration is gone - I will be back. The page is bookmarked :-).

Good to know that you are here then...

---

### Post by wieman01 on 2007-01-09
See you then! Some things are easier than others...

---

### Post by Trinity001 on 2007-01-09
But my things are always the hardest :-).

---

### Post by wieman01 on 2007-01-09
> **Trinity001 said:**
> But my things are always the hardest :-).
I am sure they are... But never ever give up. ;-)

---

### Post by Trinity001 on 2007-01-09
No, I will never give up forever. And when I'm finished with all my tasks I will be the wisest woman on earth \\:D/.

---

### Post by wieman01 on 2007-01-09
> **Trinity001 said:**
> No, I will never give up forever. And when I'm finished with all my tasks I will be the wisest woman on earth \\:D/.
Exactly. :-) May the Ubuntu be with you. ;-)

---

### Post by TheCaptain2000 on 2007-01-19
Hi, I have got it working  :-D  by following this post: 

[http://wiki.ubuntu-it.org/RalinkRT73](http://wiki.ubuntu-it.org/RalinkRT73)

It is in Italian, forget ht language and just execute the commands. If you have any problem give me a shout fvdrenato at gmail com
Cheers

---

### Post by Trinity001 on 2007-01-22
I solved the problem via another accesspoint. Now, the two accesspoints are connected to eachother and do the work for Windows and Ubuntu.

Thanks for the kind help.

The USB-Wlan-Stick will go back to the manufacturer or be sold at eBay.

---

### Post by wieman01 on 2007-01-22
> **Trinity001 said:**
> I solved the problem via another accesspoint. Now, the two accesspoints are connected to eachother and do the work for Windows and Ubuntu.

Thanks for the kind help.

The USB-Wlan-Stick will go back to the manufacturer or be sold at eBay.
What card have you got now?

---

### Post by Trinity001 on 2007-01-23
I do not have any card now. I'm using two AccessPoints as a bridge. The one is configured to be a client using WPS-PSK and the other one stays the same as with the WLan-USB-Stick.

I works perfectly as you can see - because I'm posting under Linux  now :-).

---

