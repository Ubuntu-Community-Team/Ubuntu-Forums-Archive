---
title: "External WiFi ariel problem"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by osprey2000 on 2010-04-06
Hi,
 

 I'm  an Ubunto  newbie running Karmic Koala on a Dell Inspiron 1300 laptop. Karmic is the only operating system on the machine, I used to use Windows XP but made a bit of a mistake when loading Ubunto but that's fine I'm getting on fine with and love it! Even though I don't have that much experience at computing.
 

 The internal ariel for Wifi on the Dell has never been that good for connecting unless you are very close to the transmitting station so with XP I used to use a Pheenet 802.11g USB device  that came with a CD for loading the driver etc and had its own external ariel and it worked fine.
 

 As the machine is now I can get on line with Ubunto if I'm close enough to the transmitter but we travel a lot in a motor home and can't always get close  enough to the transmitters on campsites
 

 How do I get that same external ariel to work now or is there a different one I can buy?
 

 I hope I've given you enough info and thank you in advance for any help

---

### Post by patchwork on 2010-04-06
What is the model number of your usb device?  Also, with the device plugged in, can you enter ```
lsusb
``` in a terminal and post the results?

---

### Post by osprey2000 on 2010-04-06
Hi,

The device/ariel is at home, we're out in the motrohome and wont be back until this Saturday, I am sorry but I didn't realise it was needed .....you really can see I'm new at this.
I can see from the install CD which I do have with me that it's either
WLU-703Z or WLU-803G or WLU-804G

I ran that terminal command anyway in case it helped and as you can see I'm on line with an Orange France dongle which works but the contract is too expensive and we'll terminate it soon


owner@bob:~$ lsusb
Bus 002 Device 002: ID 0af0:6600 Option GlobeTrotter 3G+ datacard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
owner@bob:~$ 

many thanks

Bob

---

### Post by patchwork on 2010-04-06
Unfortunately there's not a lot to be done without having the usb device present.  It seems like there is a good possibility of the device being plug-and-play with linux, however.  According to this [website]("http://linuxwireless.org/en/users/Devices/USB"), the 803 model has a linux driver built-in to recent kernel releases.

---

### Post by osprey2000 on 2010-04-06
Hi,

Thanks for replying so quickly and if I may I'll post again on Saturday when I have the device.

How can I check that 803 model has a linux driver built-in to recent kernel releases. I'm still learning Ubunto and am not sure exactly what a kernal release is...I'll go and read the "pocketbook" will that explain??

Bob

---

### Post by audiomick on 2010-04-06
> **osprey2000 said:**
> How can I check that 803 model has a linux driver built-in to recent kernel releases.
The short answer to that, I think, is just plug it in and see if it works.
>  I'm still learning Ubunto and am not sure exactly what a kernal release is...I'll go and read the "pocketbook" will that explain??

The kernel is the heart of the Linux system.
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)
It is updated regularly, and a "kernel release" is a particular version.

---

### Post by osprey2000 on 2010-04-06
Hi,

Thanks for all the great help, I'll get back on Saturday and let you know the result.

Not sure how you post a "Thanks"...but thanks

---

### Post by osprey2000 on 2010-04-11
Hi again,

I now have the Pheenet pligged in and ran that command and here it is

owner@bob:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
owner@bob:~$ 

I would like to attach a screen shot of what also appeared when I left clicked the wireless icon on the top right of my screen should be below

Does this help

---

### Post by osprey2000 on 2010-04-11
Ho,

Forgot to say the Intel Wireless is what I would have expected to see but can't make it "do" anything

---

### Post by RudolfMDLT on 2010-04-11
Hey there,

That device you bought is actually a seperate Wifi card, not just an antenna. As far as I can see, the device should work, the earliest problems I can find are with Ubuntu 8.04.

I just want to confirm that the device is indeed working/not working.

In terminal with the device plugged in AND your intel built in wifi switched on, type, and paste the output of:

> lsusb
> iwconfig

To make life easier, please get close to the access point in question. :)

Regards,

Rudolf

---

### Post by osprey2000 on 2010-04-11
Hi,

Hope this is what you want

owner@bob:~$ lsusb 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ace:1215 ZyDAS WLA-54L WiFi
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
owner@bob:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"wifi h2o 4"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:FB:D3:6C   
          Bit Rate:18 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/100  Signal level=-67 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:17

wmaster0  no wireless extensions.

wlan3     IEEE 802.11bg  ESSID:"wifi h2o 4"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:7E:FB:D3:6C
   

This piece of kit came with a CD and the ariel and I had it working on Windows but the CD does nothing with Ubunto. I dont know how to tell which is connecting me, the Intel or the
ZyDas ( whatever that is??)

---

### Post by RudolfMDLT on 2010-04-11
Well, it does seem to be working. :)

Does your laptop have a button to switch off the wireless? Most laptops have a button that powers the bluetooth and wireless on or off.

With both the wireless devices connected and on, enter the command "ifconfig". Paste the output.

Now, try and turn your onboard wireless off. wait a couple of seconds, then do "ifconfig" again. There should be one less adapter? paste the output anyway.

Using the network manager, try and connect to the access point.

If the connection is successful, open your web browser and confirm the internet is working. If it is working, unplug the USB device. This in effect will turn off both wireless adapters. Your internet connection should now fail. If however you still can surf the web, your onboard wireless is still connected. switch the onboard off, plug the usb Wifi back and repeat the above steps.

Post back with the results. :)

Rudolf

PS: If you look at your screen shot, the wireless network is picked up twice... The device IS working, I just want you to identify it in terminal and confirm that it is indeed working and find an easy way to disable the onboard wireless and force the connection on the external wifi.

---

### Post by osprey2000 on 2010-04-11
Hi

This is the first, with both devices on

owner@bob:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:6b:c5:7b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:b3:96:78  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:feb3:9678/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9221117 (9.2 MB)  TX bytes:1403441 (1.4 MB)
          Interrupt:17 Base address:0x8000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15114 (15.1 KB)  TX bytes:15114 (15.1 KB)

wlan3     Link encap:Ethernet  HWaddr 00:11:a3:03:6e:61  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:a3ff:fe03:6e61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:491383 (491.3 KB)  TX bytes:12862 (12.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-A3-03-6E-61-30-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

owner@bob:~$

---

### Post by osprey2000 on 2010-04-11
This is with "wireless turned off" ( Fn +F2)owner@bob:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:6b:c5:7b  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:b3:96:78  
          inet6 addr: fe80::216:6fff:feb3:9678/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9508665 (9.5 MB)  TX bytes:1430949 (1.4 MB)
          Interrupt:17 Base address:0x8000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15114 (15.1 KB)  TX bytes:15114 (15.1 KB)

wlan3     Link encap:Ethernet  HWaddr 00:11:a3:03:6e:61  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:a3ff:fe03:6e61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:494088 (494.0 KB)  TX bytes:12862 (12.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-A3-03-6E-61-30-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

owner@bob:~$

---

### Post by osprey2000 on 2010-04-11
Network manager still seems to be offering two choices Intel and ZyDAS, have I done something wong. If  Iunplug the device I'm still offered the option to connect to the source but cannot connect

---

### Post by patchwork on 2010-04-11
What is happening when you try to connect to the available network in Network Manager?

Your device does seem to be operational (It is obtaining an IP address).

---

### Post by osprey2000 on 2010-04-11
Hi,

Ok I was being a bit slow but I think I have it.....

If I right click on Network Manager > Connection information I can see which device is working, with both connected and on I get two tabs of info. If I then turn one off or disconnect the info changes so I'm sure that my ext.device is working.

Ubunto is wonderful, trouble is my friends think I'm becoming a bit of a bore telling them how good it is then I find out some of them are either changing or looking seriously at ti



many, many thanks for all the help


How do  Imark as solved? is it needed??

---

### Post by patchwork on 2010-04-11
It's in the thread tools near the top right of the page.  Good to see you've got it working!

EDIT: Marking the thread solved can help others with the same problem find their way easier, and is encouraged.

---

### Post by RudolfMDLT on 2010-04-11
With Wireless on, you have two devices connected to a network:
eth1 Link encap:Ethernet HWaddr 00:16:6f:b3:96:78
inet addr:**192.168.1.104** Bcast:192.168.1.255 Mask:255.255.255.0

wlan3 Link encap:Ethernet HWaddr 00:11:a3:03:6e:61
inet addr:**192.168.1.105** Bcast:192.168.1.255 Mask:255.255.255.0

With the wireless off, only one is connected, so switching the wireless off does change the connection. :)

Some of the buttons are "soft switches" which don't physically switch the device off, only command it to not communicate - so it will still show up in the hardware list.

So, to confirm, with the onboard wireless off, the external unit does work? With the onboard off, the external unit plugged in, and by selecting a wireless network under the heading "Wireless Network( ZyDAS USDB2 ect..)", your internet connection works? Then, when unplugging the device, you experience some error to do with connection? That is perfect. :) 

I'm sorry for this round-about way of testing, but it is fool proof and doesn't leave much to question. :)

Rudolf

---

### Post by osprey2000 on 2010-04-11
Hi,

Yes I can confirm what you say is what happens , again thank you very much

---

