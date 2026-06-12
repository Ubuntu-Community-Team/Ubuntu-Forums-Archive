---
title: "Upgrade wireless problem"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by amazoohwawa on 2008-04-25
Just upgraded to 8.04 and now my wireless is not working:( i have a lenovo 3000 N100 laptop with centrino duo chip.

please help

---

### Post by imakeart on 2008-04-25
Same thing has happened to me. I'm on an Acer Aspire 3680. 

I love the Hardy Heron wallpaper though!!


Amanda

---

### Post by Antimethod on 2008-04-28
I have a Lenovo 3000 N100 and my wireless doesn't work either.

---

### Post by Galls on 2008-04-28
I have an HP Pavilion laptop and my wireless after the upgrade does not work either.  It sees the network, but eve with security off, cannot connect.

---

### Post by hbaer on 2008-04-29
Same here. Worked like a charm before, but now it sucks ... wireless network is visible and configured (checked with iwconfig), but I cannot get it to acquire the IP address, neither with DHCP nor with a static setting ...

Running a THinkpad Z61t

---

### Post by LauraSakura on 2008-04-29
Same here... HP dv1170us. ipw2200 driver. I upgraded through update manager while connected through lan, and now my wireless won't work anymore :(

---

### Post by chili555 on 2008-04-29
Good job, Laura! You are the only person who actually mentions their chipset! You are the only one I can really help. Please let me see:```
dmesg | grep 1pw
```Let's see if we can see what's going wrong here.

The others of you, we will be very glad to help if we know what we are trying to fix. We are not familiar with every laptop ever made, nor are we going to try to guess which of two or three wireless cards you have that were supplied in your lappy. Simply run:```
sudo lshw | grep Wireless
```You might see something like this:> chili@LAPTOP60:~$ sudo lshw | grep Wireless
[sudo] password for chili: 
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network ConnectionNow we know what we are trying to fix! If you have a 3945ABG, you might try:```
 sudo apt-get install linux-backports-modules-hardy-generic
```See if your 3945ABG springs to life.

If you have someting else, tell us about it.

---

### Post by hbaer on 2008-04-29
Uhmm .. my bet, should have mentioned the chipset as well .. I have 3945ABG as well and fixed the problem with activating the NDIS wrapper (and obviously disabling iwl3945). IT is perfectly documented in the following thread: 

[http://ubuntuforums.org/showthread.php?t=765647](http://ubuntuforums.org/showthread.php?t=765647), starting with Hyronimus' advice. 

I grabbed the driver for my built-in wireless card (PRO/Wireless 3945ABG Network Connection) from the intel download page ( [http://downloadmirror.intel.com/13000/eng/V11.1.1.0_XP_DRIVERS.ZIP](http://downloadmirror.intel.com/13000/eng/V11.1.1.0_XP_DRIVERS.ZIP)), using NETw4x32.INF.

Rebooted (complete switch off was necessary, for whatever reason), and voila, here I am .. working again remotely from the sofa .. :)

---

### Post by zzandeamos on 2008-06-10
Well I got mine working or I should say a work-around.  I tried NDIS Wrapper, backporting and about 3 other suggestions but no joy.
So I put in a Puppy linux live disk and it took off like gangbusters. So I just made a bootable flash drive and it works like a champ.  I'll just wait til they get ubuntu working then try it again.  The wired ethernet is bullit proof, works great but that Wifi iwl3945 intel bugger just sits there.

I wanted to add a thank you for the input you guys provide here.  There are some really interesting ideas and I really get pumped.

---

### Post by Juhla Mokka on 2008-08-13
> **chili555 said:**
> Good job, Laura! You are the only person who actually mentions their chipset! You are the only one I can really help. Please let me see:```
dmesg | grep 1pw
```Let's see if we can see what's going wrong here.

The others of you, we will be very glad to help if we know what we are trying to fix. We are not familiar with every laptop ever made, nor are we going to try to guess which of two or three wireless cards you have that were supplied in your lappy. Simply run:```
sudo lshw | grep Wireless
```You might see something like this:Now we know what we are trying to fix! If you have a 3945ABG, you might try:```
 sudo apt-get install linux-backports-modules-hardy-generic
```See if your 3945ABG springs to life.

If you have someting else, tell us about it.

Hi.. when I type that grep Wireless code, only this comes up:
```
description: Wireless interface
``` Not much info there! 
I plugged ethernet cable in but I am still out of Internet. Any ideas?

---

### Post by Juhla Mokka on 2008-08-13
I hope somebody could help. I have surfed around the whole day and tried all sorts of codes, but it has not helped. I do not know Linux well, so I am afraid I will damage my system even more... :oops:
[B]
Upgraded to Hardy. Wireless gone.[/B] 

Here are some codes that may help in helping

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Toad"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:E0:10:DA:68   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:78:ba:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.100 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:9f:f8:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

---

### Post by Juhla Mokka on 2008-08-14
Here is an update:

**1. I can see my network but problem with security**
I am using RutilT, which finds my wireless network. It shows it as WEP secured, which is not correct - I use WPA2/PSK. I have tried taking the security down (no passwords at all) - and Once (only once, sheer luck) I managed to connect to it and use the Internet. Rebooting does not seem to make difference. :confused:
I have not succeeded second time. Plus I want to use WPA2/PSK.

**2. Strange name avahi comes up**
Typing some code (don't remeber what) gave me a list of networking hardware on my computer. There was lo, eth0, wlan0 and wlan0:avahi
Avahi is new, never seen before. It also appeared after eth0 on Ubuntu's network monitor as eth0:avahi. Ubuntu network monitor sometimes shows lo, eth0 and *sometimes* also wlan0 or wlan0:avahi. When it showed like that I could not connect using eth0.
[B]
3. Possible solution difficult to me[/B]
I tried to follow this ARCHIVED thread post #10 [http://ubuntuforums.org/showthread.php?t=843398](http://ubuntuforums.org/showthread.php?t=843398) to install a driver (do I need to? Someone said it is part of 'kernel'?) The driver behind the link has been updated and the patch does not apply (I think? Or does it?). I found the old version with same name as the patch. However, I do not know how to apply a patch, and instructions I have read do not make sense.. 

Any help, any ideas? :-k

---

### Post by chili555 on 2008-08-14
> ip=192.168.1.100It looks like your wired ethernet connection has an IP address and is, or may be connected. If you do:```
ping -c3 192.168.1.1
```do you get ping returns? I assume 192.168.1.1 is the IP address of your router.

Your ethernet driver *r8169* is fine, as far as I can tell. Before we address the wireless, let's get the wired going. 

If your wireless sees networks, it probably doesn't need a different driver, either. I know; compiling a three-year-old .tar.gz, applying patches and manually rewriting the Makefile is tons of fun, but we may not get the chance today.

---

### Post by Juhla Mokka on 2008-08-14
Hi and thanks a lot for looking into this

ping returns
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.42 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.539 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.538 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.538/0.833/1.423/0.417 ms

```

192.168.1.1 is my router address
I guess this means the wired eth0 is all ok. Well, it must be because I am using it now. It did not however, work when it was not plugged in before boot. Had to boot it plugged in. (I read about this problem somewhere on this forum, but do not worry about it too much because I am using a laptop, so will be using wireless, not wired).

---

### Post by chili555 on 2008-08-14
Great! Now let's take a look at:```
sudo iwlist wlan0 scan
```Also, do you have any encryption; WPA, WEP, etc.? Please have those details at your fingertips as we proceed. Do *not *post your key or password unless it's obscured: 092*******3, for example.

---

### Post by Juhla Mokka on 2008-08-15
Hi, It's nice sunny morning here in the UK!

sudo iwlist wlan0 scan
```
wlan0     Scan completed :
          Cell 01 - Address: 00:19:E0:10:DA:68
                    ESSID:"Toad"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Signal level=-44 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000001af6776

```
I take the code scans for wireless networks. This one "Toad" is mine. I managed to connect to it once (but don't know how) when I had taken the WPA2/PSK down (which I prefer not to do). 
I hope I will be able to use a GUI to find & connect networks, but just now I'd be really happy with a wireless that works, even configured via terminal!
:)

---

### Post by chili555 on 2008-08-15
It's a partly cloudy morning here in South Carolina, after a much-needed rain last night! Your wireless looks healthy and ready to rock. > I hope I will be able to use a GUI to find & connect networksThere is such a GUI. Network Manager is installed by default! [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

Network Manager will manage your connections if you go to System -> Administration -> Network and mark your wireless interface to enable Roaming. Also, please note this from the link:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managedThat means your wireless is not going to connect while the wired ethernet is active, so unplug the cable before you try to connect wirelessly.

You should see an icon in your panel at the top right that looks like two computers trying to communicate. Click it and see if you can select your network, Toad. You should then be presented a drop-down menu to select your encryption type and then you will be presented a box to fill in your key. You should then connect.

---

### Post by Juhla Mokka on 2008-08-15
Hi, excellent - that you think the wireless is OK. :) Closer to the solution now, I hope.
I just tried unplugging the cable but the wireless does _not_ switch on. I don't think I have network manager installed. Looking at Synaptic Package manager the boxes next to network-manager and network-manager-gnome are not ticked. I will try to install them (which one of them?). 

Under System > Administration I have 'Network' and 'Network tools'. Neither of them has the option to scan for networks. I have RutilT program that can do that. This is because I could not connect to internet wirelessly on Gutsy - the strange solution was installing RT73 driver, getting rid of network-manager and using RutilT instead (If i remember correctly). I think it is strange that my wireless driver comes up as RTL8101E because I don't think it did on Gutsy? For some reason I figured that RT73 was the answer. I can see it under System > Admin > Hardware Drivers. It is in use.

A bit messy situation ! 

Anyway, now thinking about it, I will try the following: install network-manager via synaptic. Disable RT73 driver. Forget about using RutilT. Maybe that helps? I will report back... :)

---

### Post by Juhla Mokka on 2008-08-15
> Anyway, now thinking about it, I will try the following: install network-manager via synaptic. Disable RT73 driver. Forget about using RutilT. Maybe that helps? I will report back... 
Wow, it worked! Maybe it was the RT73 driver that caused trouble? I will reboot and see if it still works after that. :guitar:

[B]
Two questions remaining:[/B]

**1.** How can I find the GUI that shows networks? I typed network-manager in terminal but it did not recognise the command.
[B]
2. [/B]Out of interest, is this ping normal (packet loss 0% under wired but 100% wireless, both connections work)?

wireless
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, **100% packet loss**, time 1999ms

```
wired
```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=4.65 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.531 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.538 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, **0% packet loss**, time 1998ms
rtt min/avg/max/mdev = 0.531/1.909/4.658/1.943 ms

```

Thank you so much chili555 for pointing me to the right direction with this! I'd still be trying all strange terminal commands other wise! =D>

---

### Post by Juhla Mokka on 2008-08-15
I rebooted. When I plug the cable, the connection does not seem to switch to wired. Is there a command that checks which one am I using? Also, the wireless on/off switch does not turn the wireless off (but all this does not really matter because wireless is working & I am happy!).

---

### Post by Juhla Mokka on 2008-08-15
**[COLOR="Red"]Too Happy Too Soon[/COLOR]**
I was surfing on the wireless, but suddenly was cut out. My boyfriend is using the same connection next to me with no problem. It has not come back. What could cause this? It has not behaved like that before (on Vista or Gutsy).

---

### Post by chili555 on 2008-08-15
Wow! If you disabled rt73, what driver do you think it's using? Let's check with:```
lsmod | grep rt
```The command that *should* tell you accurately which interface is being used is:```
ifconfig
```The interface with an IP address is the one in use. If, heaven forbid, both have IP addresses, then Network Manager is having a bad day. If the cable is detached and eth0 still has an address, kill it with:```
sudo ifdown eth0
```Please let us see:```
sudo lshw -C network
```You can skip all the wired, ethernet stuff, if it's easy for you to see which is which.

---

### Post by Juhla Mokka on 2008-08-16
I have messed it up even more, cannot see wireless at all ](*,) All my network connections seems so random. Different messages, works, doesn't work... 

lsmod | grep rt
```
parport_pc             37412  0 
parport                37448  3 ppdev,parport_pc,lp
agpgart                35016  3 drm,intel_agp

```
But it returned something else last time, much longer list, inlcluding entries that said rt73. Don't know why they don't come up now.

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:78:ba:00
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.101 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
```
I thought it was OK to disable RT73 driver, because this seemed to use r8169, and I thought the wireless and wired are both the same hardware & using the same driver?

When I booted last 2 times, I got 3 different warning messages on the black screen:
```
*Loading hardware drivers...
modprobe: WARNING: Error inserting iwlwifi_rc80211_simple (/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/mac80211/origin/net/mac80211/iwlwifi_rc80211_simple.ko): Unknown symbol in module or unknown parameter (see dmesg)
```
```
*Setting kernel variable...
error "vm.mmap_min_addr" is an unkniwn key         [fail]
```
also...something like this, but did not have time to write it down. It was error regarding avahi
```
The AVAHI_DAEMON_START 
```

and when I click the network connections icon, a warning comes up
> Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device

---

### Post by chili555 on 2008-08-16
*r8169* is the module that drives your ethernet card and *rt73* is the module that drives your wireless card. They are two separate and distinct devices. In order to get your wireless back in the picture, re-enable *rt73*.> SIOCGIFFLAGS error: No such device Since your wireless device has no driver (since you disabled *rt73*) it is not recognized and no interface, wlan0, is assigned. Then when you try to connect wirelessly through wlan0, the system reports it has no such device.> I got 3 different warning messages on the black screen:Your machine has thoughtfully created a log of all the boot messages. If you open a terminal and do:```
dmesg | less
```you will be able to scroll back and forth through the messages with the arrow keys and see the ones that seem alarming. Troubleshoot as needed.

I have no clue why any part of iwlwifi is getting loaded; I don't believe you have any equipment that needs it.

If you want help troubleshooting, you can do:```
dmesg | grep -i error > dmesgerrs.txt
```This will create a text file in your /home/user directory listing only the boot messages that had errors. You can post here as an attachment and we'll be glad to look it over.

Please check your private messages.

---

### Post by Juhla Mokka on 2008-08-16
Hi, I just booted my machine and typed the same stuff again, and it looks completely different:

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:03:0d:78:ba:00  
          inet addr:192.168.1.101  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5652 (5.5 KB)  TX bytes:5831 (5.6 KB)
          Interrupt:18 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1500 (1.4 KB)  TX bytes:1500 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:db:9f:f8:7b  
          inet addr:192.168.1.102  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5154 (5.0 KB)  TX bytes:4198 (4.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-DB-9F-F8-7B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

lsmod | grep rt
```
parport_pc             37412  0 
parport                37448  3 ppdev,parport_pc,lp
rt73usb                25344  0 
rt2x00usb              12032  1 rt73usb
rt2x00lib              19584  2 rt73usb,rt2x00usb
rfkill                  8208  1 rt2x00lib
mac80211              171016  3 rc80211_simple,rt2x00usb,rt2x00lib
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
agpgart                35016  3 drm,intel_agp
usbcore               138632  5 rt73usb,rt2x00usb,uhci_hcd,ehci_hcd

```

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:78:ba:00
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.101 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:db:9f:f8:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11g

```

---

### Post by stevebag on 2008-08-30
There is a page with the Lenovo 3000 n100 specs and problems listed, with a particular solution for wifi at the following link

[https://wiki.ubuntu.com/LaptopTestin...o3000N100_0768](https://wiki.ubuntu.com/LaptopTestin...o3000N100_0768)

I followed the directions there with success.

---

### Post by chili555 on 2008-08-31
@stevebag-

I think your link is broken. Can you please fix it for us? Thanks.

---

