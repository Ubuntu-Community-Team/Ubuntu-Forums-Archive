---
title: "Setup RaLink RT3062 wifi card in xubuntu"
date: 2016-06-12
forum: Networking &amp; Wireless
---

### Post by Ralph L on 2016-06-12
I am trying to install an RaLink RT3062 wifi card in my Dell Latitude D610.  I am running xubuntu 14.04 with the latest updates.  The card seems to install fine and will run ok for a while, but then it disconnects from my router and won't reconnect.  I see a number of linux websites discussing the driver for this card, but most of them are rather old.  The older ones (circa 2012) say to run the rt3562sta driver and to blacklist the rt2800pci drivers. One site says to use the rt2860.bin firmware.  The newer postings say that the default rt2800 driver will work with newer linux kernels.  My xubuntu 14.04 kernel is 3.16.0-71, which I think is new enough.  So I just installed the hardware and booted up.  However, as I said above, the card works only intermittently.

The output of "lspci" says I have Kernel driver "rt2800pci" in use.
"lsmod" lists rt2800pci, rt2800lib, rt2x00pci, rt2x00mmio, rt2x00lib, mac80211.  
I also looked for firmware for the RT3062, but I don't know how to list that.  Could somebody tell me how to do that in xubuntu????

Any help on what driver I should run, what firmware I should run (with my kernel) would be greatly appreciated.  Also, detailed instructions would be appreciated, since I don't really understand xubuntu.

Thanks

Edit:  This website [https://wiki.debian.org/rt2800pci](https://wiki.debian.org/rt2800pci) gives instructions for loading the drivers and firmware from a debian site.  However, when I tried to do the update, it said:
```
W: GPG error: [http://httpredir.debian.org](http://httpredir.debian.org) jessie Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553 NO_PUBKEY 7638D0442B90D010 NO_PUBKEY CBF8D6FD518E17E1
```

Can anybody tell me how to fix this????

---

### Post by Ralph L on 2016-06-14
Hey everybody,

I really could use some help on getting this RT3062 card running on a recent (14.04) linux.  

Even if you don't know anything about the RT3062 driver/firmware, somebody must know how to solve the problem I am having executing the instructions in [https://wiki.debian.org/rt2800pci](https://wiki.debian.org/rt2800pci) , where I am getting an error message about not having the Public Key for Debian Jessie.

Sure could use some help!!!

Thanks again......

---

### Post by jeremy31 on 2016-06-14
*Thread moved to **Networking & Wireless**.*

Please see the wireless script link in my signature and post results

---

### Post by Ralph L on 2016-06-14
Jeremy31

Thank you very much for responding. I really appreciate it.

1.  I moved the RT3062 wifi card from my xubuntu 14.04 computer to my Ubuntu 12.04 computer.  Both computers are Dell Latitude D610, so there shouldn't be a difference except for the OS.  However, the RT3062 runs better under xubuntu 14.04 than under ubuntu 12.04.  Under xubuntu it came up and I was able to run a speed test on it before it stopped working.  Under ubuntu it won't actually connect to anything, although the signal strength looked good.  The reason I moved the RT3062 was that I needed the xubuntu system available for my daily work, but the ubuntu system I don't use much.  I can move the RT3062 back to the xubuntu system if necessary, just takes a little while.
2.  I updated the ubuntu 12.04 system as you instructed.
3.  Attached is the wireless-info.tar.gz file that was created with the script.  I could see nothing wrong.
4.As I said in an earlier post [https://wiki.debian.org/rt2800pci](https://wiki.debian.org/rt2800pci) shows how to install the RT cards (including the RT3062) for Debian, but I couldn't do it, because the Public Key was not available.  The error message is shown in the earlier post.

Thanks again...

---

### Post by jeremy31 on 2016-06-14
Somehow, I do not see the wireless-info attachment.  If you have issues doing that just copy the contents of the wireless-info.**txt** file and paste at paste.ubuntu.com and post the URL

---

### Post by Ralph L on 2016-06-14
Jeremy31

My bad--forgot the file.  If I did it right it should be there now.

---

### Post by jeremy31 on 2016-06-14
I would change encryption settings on the wifi router to WPA2 only as it has TKIP enabled now and move it to channel 9

Second, as it appears you are in the USA, set the correct regulatory info with
```

sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```

Note: Thanks Hadaka for that script

Go into Network Manager settings and set IPv6 to ignore or disable- it has been a while since I used 12.04

Reboot

---

### Post by Ralph L on 2016-06-14
Jeremy31

I did the operations you requested (or at least I think I did), but still no joy. Wifi appears to connect to Langley, but no data gets through.  Attached is a rerun of the script after I made the changes.

Thanks for the help...........

---

### Post by Hadaka on 2016-06-14
Hi Ralph, from a working wired connection please open a terminal ctrl/alt/t 
Your country code currently shows..country TW .. TW    +2503+12130    Asia/Taipei
your wireless report shows..America/Los_Angeles..US    +340308-1181434    America/Los_Angeles    Pacific
*If US is correct then copy and paste one line at a time,
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
Next, your udev file is confused by all the attempts you have made to connect and that is why your wlan is wlan1 instead of wlan0
to correct that please do..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
Please click the wifi icon...network manager and configure your connection like the attached.
[ATTACH=CONFIG]269581[/ATTACH][ATTACH=CONFIG]269582[/ATTACH]
remove wired connection ..boot and test wireless

---

### Post by Ralph L on 2016-06-15
Hadaka

Thank you for your response.  I followed your directions, but no change.  Wifi looks like it is connected, but no data seems to flow.  Here is the wireless info.

---

### Post by Ralph L on 2016-06-15
I noticed the wireless-info.txt still shows my country as TW.  However, /etc/default/crda shows:```
# Set REGDOMAIN to a ISO/IEC 3166-1 alpha2 country code so that iw(8) may set
# the initial regulatory domain setting for IEEE 802.11 devices which operate
# on this system.
#
# Governments assert the right to regulate usage of radio spectrum within
# their respective territories so make sure you select a ISO/IEC 3166-1 alpha2
# country code suitable for your location or you may infringe on local
# legislature. See `/usr/share/zoneinfo/zone.tab' for a table of timezone
# descriptions containing ISO/IEC 3166-1 alpha2 country codes.

REGDOMAIN=US
```

Is the script getting its country code from some place other than /etc/default/crda???

---

### Post by chili555 on 2016-06-15
CRDA is probably getting TW from the card itself; it's where the card came from, no doubt.

It appears that you are well and truly connected:> wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.2.108  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10424 (10.4 KB)  TX bytes:82035 (82.0 KB)Can you ping the router?```
ping -c3 192.168.2.1
```The world?```
ping -c3 www.ubuntu.com
```

---

### Post by Ralph L on 2016-06-15
chili555
Thank you for responding. I definitely need help!!! Here is the output of doing a ping: ```
ralph@Lat1:~$ ping -c3 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2001ms

ralph@Lat1:~$ 

``` Obviously the ping to the outside world didn't work either.

Here is the contents of /etc/udev/rules.d/70-persistent-net.rules after I deleted it and it was reconstructed:  ```

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:03.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="48:02:2a:f8:c9:7c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
``` is it significant that DRIVERS=="?*"   ??????????

---

### Post by chili555 on 2016-06-16
> is it significant that DRIVERS=="?*" ?????????? Not at all.

Earlier in this thread, you said:> The newer postings say that the default rt2800 driver will work with newer linux kernels. My xubuntu 14.04 kernel is 3.16.0-71, which I think is new enough. Then you proceeded to do:>  I moved the RT3062 wifi card from my xubuntu 14.04 computer to my Ubuntu 12.04 computer. And now you are running the kernel version:> Linux 3.2.0-104-generic-paeSo your strategy, when advised that the device works with* newer *kernel versions is to move to an ***older*** kernel version!!!

Please move back and give us an updated wireless script.

---

### Post by Ralph L on 2016-06-16
Chili555

Thanks again for responding.

1.  The newer kernels I was talking about were ones newer than Lucid, or something like that, so I thought that Precise would be new enough.

2. I moved the network card back to my 14.04 system.  Wifi does actually work sometimes on 14.04, however, it drops out frequently and will sometimes not come back up until I reboot.  The strange thing is that it seems to have some sort of a "learning" system in the driver.  The longer it stays up the better it gets.  But when I sleep the computer, the wifi will usually not restart, although sometimes it does.  Even stranger, in the list of wifi's that are displayed by the network manager. My Langley wifi will sometimes not even be displayed after it drops out, and it will not even try to reconnect.  And I can't force it to try to reconnect, because the Langley wifi is not displayed. Rebooting usually restores Langely to the wifi list, but not always.  This strange behavior (not listing Langley) hints to me of a driver bug.

3.  I edited the files and made the changes to network manager that you and others requested in the 14.04 system.  However, network manager simply created a new "profile" called Langley 2 and used that instead of Langley (with the changes you requested).  So far I haven't been able to get it to run under Langley (with your changes).

4.  So attached in the wireless-info file for 14.04.  I was able to keep Langley running (under 14.04--this system) long enough that the wireless info script was completely run with Langley working.

---

### Post by Ralph L on 2016-06-16
Chili555

Here is a wireless-info file taken just after Langley stopped working.  Note that it had previously been running on Langley 2.  Note that Langley wasn't even listed under the selection space on network manager.  However, after a few minutes it reconnected to Langley 2 and continued dropping out and reconnecting.

---

### Post by chili555 on 2016-06-17
I suggest you try a driver parameter:```
sudo -i
echo "options rt2800pci nohwcrypt=Y"  >  /etc/modprobe.d/rt2800pci.conf
exit
```Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot and tell us if there is any improvement.

---

### Post by Ralph L on 2016-06-18
Chili555 
1. Added file /etc/modprobe.d/rt2800pci.conf with the contents you suggested.  Didn't help.  Wifi ran for a while and then dropped out just like before.

2.  I changed rt2800pci.conf permission to read-only for other.  All the other files in this directory have that permission.

3.  Attached is the output of the wireless-info script run after wifi quit.  Note that Langley (my wifi) did not even appear in the network-manager list of detected wifi's.  What causes that???  Even more mysterious is that sometimes after 5 or 10 minutes, Langley will reappear and will run again.  It is like something shuts off Langley and then over time allows it to be re-detected.  Could this be a firmware bug??

---

### Post by chili555 on 2016-06-20
> eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.2.111  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12446 (12.4 KB)  TX bytes:13425 (13.4 KB)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.2.108  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35483695 (35.4 MB)  TX bytes:862451 (862.4 KB)Why is it that you have both the wireless and the ethernet connected? I suspect this may be leading to problems. Please try all diagnostics with the ethernet detached. Run the wireless script and then, if the wireless is not working, turn off the wireless and connect the ethernet to post it.> Even more mysterious is that sometimes after 5 or 10 minutes, Langley will reappear and will run again. It is like something shuts off Langley and then over time allows it to be re-detected. Could this be a firmware bug?? The firmware for the wireless driver or the firmware for the router? Is the router firmware up to date? Does Langley reappear if you power-cycle the router by unplugging and replugging it?

It seems that if there is a problem with the router and your wireless card looks for and can't find the beacon, that might be a contributer to the issue.

---

### Post by Ralph L on 2016-06-25
Chili555,
Sorry to be so slow in responding but I have been busy.

1. Attached are the results for 2 different runs of wireless-info.  In neither is the ethernet connected.  In the first attachment (as the name indicates) the card was working fine on wireless.  In the second attachment the wireless refused to connect.

2. The router works fine on 5 other devices I have running on it, so I doubt there is a router problem.

3. I finally managed to find a Windows XP driver for the RT3062.  Under XP the card behaved very similar to its behavior under xubuntu.  It ran only intermittently.  So either the xp firmware and drivers have the same bugs as the linux firmware and drivers, or the card has a hardware problem.  I am working on getting a replacement card.

4. I came across your post #40 in [http://ubuntuforums.org/showthread.php?t=2304607&page=4](http://ubuntuforums.org/showthread.php?t=2304607&page=4) . The weak wifi signal with wifi dropping in and out sounds very much like my problem. As near as I can tell the rtlwifi_new drivers described in your post have not been installed into xubuntu 14.04? It was a problem with the rt8723b that prompted the thread, but when I look at the firmware (firmware-realtek) installed in my system (using synaptic), and I believe used for my rt3062, I see that it is listed as the firmware for the rt8723b.  This makes me think that the same fix (rtwifi_new) might work for my problem. [https://github.com/lwfinger/rtlwifi_new/issues/34](https://github.com/lwfinger/rtlwifi_new/issues/34) (next to last post) says that the updated rt8723 driver/firmware will be in Kernel 4.7.  From what I can see xubuntu 16.04 has Kernel 4.4 so if I want to get the rtwifi_new fix I will have to compile it.  What do you think??? 

Thank you very much for your help on this.  I will add to this thread, when I get new hardware.

---

### Post by Ralph L on 2017-01-18
See [https://ubuntuforums.org/showthread.php?t=2338890](https://ubuntuforums.org/showthread.php?t=2338890) for how I finally got an 802.11 a/b/g/n wifi card to work on my Dell Latitude D610.

---

### Post by wildmanne39 on 2017-01-18
Please do not cross post, thread closed!

From posting guidelines.
> Do not cross post, or post the same thing in multiple locations.

---

