---
title: "USB WiFi Conundrum"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by Jamesbowden on 2007-10-29
Dues to the way my house is set up and the number of laptops we have. I can not be on a wired network all the time. I have a Belkins USB wifi adaptor that uses the rt73 chipset (I checked the driver CD) That I would like to use to connect to my WiFi network when I need to. However I could not scan or connect to access points. So I opened up hardware information and took a look at the device, it turns out it was using trying to use the rt2500 (i think) drivers. so I did: 

```
echo 'blacklist rt2500usb' | sudo tee -a /etc/modprobe.d/blacklist 
```

to black list the drivers.

I then rebooted. but when I tried to log in gnome complained about being unable to start the settings deamon and all my themes where messed up. Not letting this bother me I just opened up the network manager and checked my WiFi settings. And it worked! it picked up all the networks around me and after I had selected mine and entered the WEP key I could connect to the internet fine.

I thought I would reboot to see if the theme thing was just a login error, so I did. and when I logged in all was fine in the way of the deamon starting and the themes being ok. but when I checked my WiFi...nothing, it had all stopped working again =[ I couldn't pick up or connect to anything.

here is my /etc/modprobe.d/blacklist 

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

#rt2500 wireless drivers stops rt73 from being used with belkins USB wifi
blacklist rt2500usb
```

My ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:01:29:D8:CD:7B  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fed8:cd7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2771 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2499 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2303093 (2.1 MB)  TX bytes:343129 (335.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:992 (992.0 b)  TX bytes:992 (992.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:17:3F:AE:4D:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-AE-4D-26-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

and my iwconfig (which I have noticed is saying ESSID "Wrouter" which is strange since I have never connected to the AP named that.

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Wrouter"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:0B:31:84   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


any body know whats up?

---

