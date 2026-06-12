---
title: "networkmanager applet doesn't know about wireless"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by dkerlee on 2007-03-03
Hello everyone. I've been able to get wireless network working, but it's sorta a weird setup. My wireless card is not supported out of the box, so I installed the ndiswrapper, then the appropriate .inf driver from ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)). I was able to get the driver present, and the hardware present, then I can modprobe ndiswrapper and it will come up and scan for available wireless networks. I'm able to associate with a wireless network and surf the interwebs, as I'm doing now.

My wireless card does come up in System>Administration>Networking, but when I hit properties on the wireless networking card, the dropdown menu does not show other available networks. I checked the box in System>Administration>Networking>General(tab) Scan for available services and advertise local services, but still to no avail.

I'd like my wireless connection to come up under the Networkmanager applet in the top right by the clock, but all it knows about is the radio button Wired network, which is grayed out.

I'd think that because I can run 'iwlist scan' it should be able to scan for available wireless networks, but for some reason, I can only access the stuff via the terminal.

Here is my relavent configuration pieces:
ubuntu 6.10
ndiswrapper 1.37 (compiled from source, make install)
    bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
/etc/modprobe.d/blacklist
     last line has: blacklist bcm43xx
root@drew-laptop:~# lspci -v | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
        Subsystem: Broadcom Corporation Unknown device 0466

Please let me know if there is any other relevant information I can furnish this post with. Thanks a million!

drew

---

### Post by tgalati4 on 2007-03-03
There's a gui ndiswrapper that you can download from synaptic.

Post the results of:
ifconfig 
iwconfig

It's possible that network manager doesn't respond to a device other than wlan0.

You could remap devices:

sudo link /dev/broadcom /dev/wlan0

---

### Post by dkerlee on 2007-03-04
That might be. I remembered that at one point, I used an older version of ndiswrapper and my wireless card came up as eth1, even though I knew it was the wireless card. When I updated to the latest ndiswrapper with a .inf that I found that seemed to work, it's always been coming up as wlan0. I don't seem to have 'broadcom', 'Broadcom', or a 'wlan0' in my /dev.

Yes, now that you mention it, I saw and tried out the package ndisgtk from Synaptic Package Manger, but it only told me the same thing as ndiswrapper -l. It was only a way to load and unload different drivers to the ndiswrapper. Hopefully, I'll only have to load my driver once, then not have to deal with it again after doing ndiswrapper -m, so I won't have to use the ndisgtk program.

I knew I was forgetting something key... here we go:
drew@drew-laptop:~$ sudo ifconfig
Password:
eth1      Link encap:Ethernet  HWaddr 00:E0:B8:AB:AB:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:14:A5:AA:A7:54  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:feaa:a754/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:653383 (638.0 KiB)  TX bytes:73757 (72.0 KiB)
          Interrupt:169 Memory:d6000000-d6004000 

aaaannnd
drew@drew-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"leech/torres"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:56:59:5B   
          Bit Rate:11 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by tgalati4 on 2007-03-04
It's strange the the Gnome Network Manager doesn't see your card.  Try installing WiFi Radar (from add/remove or from Synaptic) and see if your Access Point shows up.

It's possible that your Windows driver using ndiswrapper has a subtle problem that is tripping up the Network Manager.  It could be as simple as a permission problem.  Did you use sudo ndiswrapper -i mycheesywindowsbroadcomdriver?

Did you set the network monitor preferences (right-click, preferences) to display wlan0?

Bottom line.  If it works, don't worry about it.  Having the network panel is helpful, but it doesn't prevent you from doing your work.

---

### Post by nevermind_quack on 2007-03-16
I have some ideas for you if you're still stuck on this...

Sometimes networkmanager is unhappy if you have entries in your /etc/network/interfaces file... copy it to a backup and comment out everything but your loopback interface then restart.  Right click on the nm-applet and make sure enable wireless is checked.  There is a bug between the proprietary nvidia driver and the ndiswrapper driver for this card, so you may have a problem after its working.

Check whether your bcm43xx driver is loaded by doing lsmod, and 'sudo rmmod bcm43xx' if necessary (it won't hurt if not).  rmmod and modprobe the ndiswrapper driver to give it a hard reload... and good luck.  If you get a kernel message about the irq to your console you're looking at the bug i mentioned and it was a long road getting past that... but best of luck.

---

### Post by hardyn on 2007-03-16
I have been having trouble with mine after 6 months of flawless performance...

network manager will only see the SSID of the single highest strenth un-WEP protected router... 

if you think this sounds like your trouble... please leave a comment here:

[https://launchpad.net/bugs/90896](https://launchpad.net/bugs/90896)

---

### Post by prog101 on 2007-12-07
system -> administration -> network
click on wireless connection -> properties -> enable roaming mode
click on wired connection -> properties -> enable roaming mode

Now, network manager should list of wireless networks and wired network.

Hope this helps.

---

