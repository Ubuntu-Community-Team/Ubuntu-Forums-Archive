---
title: "Wireless HELP?"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by dryfly on 2008-11-26
I have searched and worked getting my Dell Inspiron e1505 wireless card working...I have not been successful...I have found various threads that address the problems I am having...but none seem to be the right fix for this machine...please let me know the information that will be helpful in resolving this once and for all...as if you couldn't tell...I am new to Linux...but want to learn/trying to learn...Thank you very much...

---

### Post by CholericKoala on 2008-11-26
There are a ton of threads out there with fixes for wifi cards, but one things I eventually found out, at least for a laptop, is that switching to a different distro with more compatibilities is easier.  Fedora Core 10 just came out and it has quite a bit more compatibility with wifi cards out of the box.  Ubuntu is awesome, but wifi can be a pain.  If you don't find a solution, I would suggest taking a look at Fedora 10.

---

### Post by drclaw on 2008-11-26
I had issues with wireless on my Latitude D520 until I allowed Ubuntu to install the restricted driver for my NIC.  Once that was done it worked flawlessly.

---

### Post by dryfly on 2008-11-26
"I had issues with wireless on my Latitude D520 until I allowed Ubuntu to install the restricted driver for my NIC. Once that was done it worked flawlessly."

how is this accomplished?

---

### Post by drclaw on 2008-11-26
Try looking under **System>Administration>Hardware Drivers**. In my case there was a Broadcom proprietary driver which needed to be downloaded and enabled.  Not sure what make the NIC in your laptop is.

---

### Post by dryfly on 2008-11-26
not there...only driver listed is a graphics driver...

Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

this may also be helpful

lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:8a:2a:0d
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

and...

tim@infected:~$ sudo ifup wlan0
[sudo] password for tim: 
Ignoring unknown interface wlan0=wlan0.

---

### Post by CholericKoala on 2008-11-26
mmmk.  This is the simple way to do generic wifi cards.  Install ndiswrapper though synaptic, then ndisgtk.  That will give you a GUI to install a driver.  Download the windows driver for your wifi card, extract the files in a folder, then go into the ndisgtk GUI and select the .ini file, most likely in an "XP" folder under drivers.

I can't give specific info on what you need to do in terms of the driver download, but get ndiswrapper and ndisgtk from synaptic, and you are ready to install the driver.

---

### Post by drclaw on 2008-11-26
Check this thread for a possible solution:

[http://ubuntuforums.org/showthread.php?t=321045&page=3](http://ubuntuforums.org/showthread.php?t=321045&page=3)

Looks like this user was able to get it working.

---

### Post by dryfly on 2008-11-26
this appears to me to be relevant only to earlier distros and older kernels...is that a correct?

---

### Post by drclaw on 2008-11-26
Possibly.  Maybe a little information on your setup would be helpful.  What version of Ubuntu are you using and what kernel?

```
cat /proc/version
```

It looks like at one time there was a project aimed at developing a driver for this card.  The driver has since been merged with the mainline kernel as of 2.6.24.  So Hardy or later should already have the **iwlwifi** driver.

---

### Post by dryfly on 2008-11-26
it looks to me like the driver is installed...but the card won't come up?

---

### Post by dryfly on 2008-11-26
> **drclaw said:**
> Possibly.  Maybe a little information on your setup would be helpful.  What version of Ubuntu are you using and what kernel?

```
cat /proc/version
```

It looks like at one time there was a project aimed at developing a driver for this card.  The driver has since been merged with the mainline kernel as of 2.6.24.  So Hardy or later should already have the **iwlwifi** driver.

tim@infected:/$ cat /proc/version
Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:43:45 UTC 2008

---

### Post by david_lynch on 2008-11-26
> **dryfly said:**
> I have searched and worked getting my Dell Inspiron e1505 wireless card working...I have not been successful...I have found various threads that address the problems I am having...but none seem to be the right fix for this machine...please let me know the information that will be helpful in resolving this once and for all...as if you couldn't tell...I am new to Linux...but want to learn/trying to learn...Thank you very much...
Did your computer not come with ubuntu pre-installed and fully operational? 

If you started with ms windows and installed ubuntu after the fact, then it should still be fairly straightforward. The intel drivers are generally well supported - if the driver is loaded, but the card is not coming up, then re-check your settings for your wifi connection.

---

### Post by drclaw on 2008-11-26
What is the output if you run

```
iwconfig
```

Also, possibly a stupid question, but is your wireless radio on?  Can you toggle it with a **Fn F2** for example?

---

### Post by dryfly on 2008-11-26
NOT a stupid question...I have the "wifi" light on now...need to scan for my wireless signal now...

---

### Post by dryfly on 2008-11-26
> **drclaw said:**
> What is the output if you run

```
iwconfig
```

Also, possibly a stupid question, but is your wireless radio on?  Can you toggle it with a **Fn F2** for example?


tim@infected:/etc/init.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by drclaw on 2008-11-26
Well the interface is there but not associated with an AP.

I may be in a bit over my head on this one.

I assume you have a wired connection hooked up now.  If you click on the network icon at the top are you able to select a wireless network?  Initially I did not have this option after installation, but after installing all of the available updates from update manager and rebooting I could pick a network to connect to.

---

### Post by dryfly on 2008-11-26
> **drclaw said:**
> What is the output if you run

```
iwconfig
```

Also, possibly a stupid question, but is your wireless radio on?  Can you toggle it with a **Fn F2** for example?


tim@infected:/etc/init.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ok...getting closer...I configured my wireless network...and it appears to see it...but still now IP...and unable to ping...restarted networking as well...

tim@infected:/etc/init.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"My Wireless Network A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:20:A6:5D:8C:EB   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=96/100  Signal level:-32 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tim@infected:/etc/init.d$ ping google.com
ping: unknown host google.com

---

### Post by dryfly on 2008-11-26
> **drclaw said:**
> What is the output if you run

```
iwconfig
```

Also, possibly a stupid question, but is your wireless radio on?  Can you toggle it with a **Fn F2** for example?


tim@infected:/etc/init.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ok...getting closer...I configured my wireless network...and it appears to see it...but still now IP...and unable to ping...restarted networking as well...

tim@infected:/etc/init.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"My Wireless Network A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:20:A6:5D:8C:EB   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=96/100  Signal level:-32 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tim@infected:/etc/init.d$ ping google.com
ping: unknown host google.com

---

### Post by dryfly on 2008-11-26
> **drclaw said:**
> What is the output if you run

```
iwconfig
```

Also, possibly a stupid question, but is your wireless radio on?  Can you toggle it with a **Fn F2** for example?


tim@infected:/etc/init.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ok...getting closer...I configured my wireless network...and it appears to see it...but still now IP...and unable to ping...restarted networking as well...

tim@infected:/etc/init.d$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"My Wireless Network A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:20:A6:5D:8C:EB   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Link Quality=96/100  Signal level:-32 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tim@infected:/etc/init.d$ ping google.com
ping: unknown host google.com

---

### Post by drclaw on 2008-11-26
That's progress.  Does wlan0 have an IP address assigned to it?

```
ifconfig
```

---

### Post by dryfly on 2008-11-26
> **drclaw said:**
> That's progress.  Does wlan0 have an IP address assigned to it?

```
ifconfig
```


tim@infected:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:b3:a1:33  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feb3:a133/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8017198 (7.6 MB)  TX bytes:929641 (907.8 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92100 (89.9 KB)  TX bytes:92100 (89.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:8a:2a:0d  
          inet6 addr: fe80::218:deff:fe8a:2a0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95940 (93.6 KB)  TX bytes:576 (576.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-8A-2A-0D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



I rebooted (Too long in the Windoze world I suppose?) I lost the essid setting...but used the "any" option and it is definitely finding the router...is there a trick to switching what card is being used (between wired connection and wireless connection) Thank you VERY much for your help thus far by the way!

---

### Post by dryfly on 2008-11-26
Success! Working now! Kept plugging away at it...and LOTS of good info from this community! Thanks A LOT!

---

### Post by drclaw on 2008-11-26
Glad to hear it!  With that, I'm off for a long weekend.

---

