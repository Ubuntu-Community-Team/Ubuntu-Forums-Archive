---
title: "Slow download speed on Ubuntu 12.10 vs Windows"
date: 2013-11-30
forum: Networking &amp; Wireless
---

### Post by dani.rab on 2013-11-30
Hey great community, I need your help with understanding why my internet speed (especially the download speed) is so slow on my Ubuntu machine. check this speed differences between my Windows and Ubuntu machines:

Windows:

[ATTACH=CONFIG]248214[/ATTACH]

Ubuntu:

[ATTACH=CONFIG]248215[/ATTACH]

it used to be ok a few days ago, I don't have a clue what changed that now it's so slow.
I tried searching for a solution but everything I tried did not work.

The Ubuntu machine is connected with a wired and wireless connection, I tried disabling one of them but it did not help.

---

### Post by varunendra on 2013-12-03
Welcome to the forums dani.rab !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by dani.rab on 2013-12-03
thanks for the help Varunendra, here's the output of the wireless script:
[http://goo.gl/Un6p8Z](http://goo.gl/Un6p8Z)

---

### Post by coffeecat on 2013-12-03
*Thread moved to **Networking & Wireless**.*

---

### Post by varunendra on 2013-12-03
Have you checked the speed with only the wifi connected (and wired disconnected)?

Because both are currently connected, both have (same) gateway defined but different DNS servers. This *may* cause some confusion about routing table preferences unless we check "route -n" as well along with other outputs. Besides, Network Manager is designed to prefer the Wired connection if available.

If using only the wireless connection gives you the same slow speeds, try this first -

Open a terminal (Ctrl-Alt-T) and run the following command -
```
sudo modprobe -rv rt61pci
sudo modprobe -v rt61pci nohwcrypt=Y
```
Then connect again and see if it helps improving the speed. This will be a temporary change that will be lost at next boot. If it seems to help, we can make it permanent.

If the above trick doesn't help, try changing the encryption type in your router to pure WPA-PSK, AES/CCMP. Currently it is set to use WPA/WPA2 mixed mode with TKIP, which should be avoided at all costs.

Additionally, you may (probably should) also try changing the channel to 1 or 11. These usually work better with Linux drivers.

Try one at a time (nohwcrypt=Y first, change of encryption and channel next), and if neither seem to make any significant difference, try the nohwcrypt=Y option WITH the changed encryption too.

Let us know the outcome.

---

### Post by dani.rab on 2013-12-03
we're making progress, using only the wireless connection improved the speed significantly. I got these results:
[COLOR=#000000][FONT=Times New Roman]Download Speed: [/FONT][/COLOR]**11.6**[COLOR=#000000][FONT=Times New Roman] Mbps (1.45 MB/sec transfer rate)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Upload Speed: [/FONT][/COLOR]**4.24**[COLOR=#000000][FONT=Times New Roman] Mbps (0.53 MB/sec transfer rate)

[/FONT][/COLOR]Changing the nohwcrypt or the encryption had a very small affect.

Still the download speed is much lower than windows (40 Mbps vs 12 Mbps).

Is there something else I can try?
why is the wired connection so slow? shouldn't it be faster?

---

### Post by varunendra on 2013-12-03
> **dani.rab said:**
> why is the wired connection so slow? shouldn't it be faster?

Yes it should. But there can be many things that can go wrong. I have no reason so far to believe that it was the wired connection alone that was itself slow. It could be some confusion/conflict at the OS level as well.

If using only the wired connection alone gives the same slow speed again, we can try a few things to make it faster. That would be a whole different issue, and should be kept entirely separate from the wireless issue currently at hand.

As for the wifi, did you also change the encryption as suggested? The TKIP encryption is not nearly as efficient as the AES/CCMP I suggested, and is often the cause for slow speeds.

---

### Post by dani.rab on 2013-12-03
> **varunendra said:**
> As for the wifi, did you also change the encryption as suggested? The TKIP encryption is not nearly as efficient as the AES/CCMP I suggested, and is often the cause for slow speeds.

Yes, I tried the AES encryption, I saw a very small improvement.

If I just use a wired connection, the speed is very slow.

basically I prefer using the wired connection, but currently I'm connected by WIFI because of the slow speed issue.

---

### Post by varunendra on 2013-12-03
Hmm.. let's see if there is anything we can do to further improve the speed.

For the wireless, please re-run the script (with all the recommended changes applied and ethernet disconnected) and post back the result along with the outputs of -
```
ifconfig
route -n
ping -c4 google.com
```
And a fresh speedtest result (screenshots aren't necessary, your description would be enough).

For the wired connection, please install ethtool (sudo apt-get install ethtool) and post back the outputs of (while Only the ethernet is connected and wifi disabled) -
```
ifconfig
route -n
ping -c4 google.com
sudo ethtool eth0
```

---

### Post by dani.rab on 2013-12-04
**wireless results:**
[COLOR=#000000][FONT=Times New Roman]Download Speed: [/FONT][/COLOR]**13.75**[COLOR=#000000][FONT=Times New Roman] Mbps (1.72 MB/sec transfer rate)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Upload Speed: [/FONT][/COLOR]**4.22**[COLOR=#000000][FONT=Times New Roman] Mbps (0.53 MB/sec transfer rate)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Latency: [/FONT][/COLOR]**11**[COLOR=#000000][FONT=Times New Roman] ms
[/FONT][/COLOR]
output of script:
[http://goo.gl/5K9xkX](http://goo.gl/5K9xkX)

output of commands:

```

dan@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr <REMOVED>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:411421 (411.4 KB)  TX bytes:411421 (411.4 KB)


wlan0     Link encap:Ethernet  HWaddr <REMOVED>  
          inet addr:192.168.11.54  Bcast:192.168.11.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44719985 (44.7 MB)  TX bytes:13014912 (13.0 MB)


dan@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.11.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0
dan@ubuntu:~$ ping -c4 google.com
PING google.com (74.125.224.130) 56(84) bytes of data.
64 bytes from lax02s20-in-f2.1e100.net (74.125.224.130): icmp_req=1 ttl=52 time=14.9 ms
64 bytes from lax02s20-in-f2.1e100.net (74.125.224.130): icmp_req=2 ttl=52 time=23.3 ms
64 bytes from lax02s20-in-f2.1e100.net (74.125.224.130): icmp_req=3 ttl=52 time=22.8 ms
64 bytes from lax02s20-in-f2.1e100.net (74.125.224.130): icmp_req=4 ttl=54 time=14.5 ms


--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 14.582/18.927/23.370/4.178 ms

```

**wired connection results:**
[COLOR=#000000][FONT=Times New Roman]Download Speed: [/FONT][/COLOR]**0.45**[COLOR=#000000][FONT=Times New Roman] Mbps (0.06 MB/sec transfer rate)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Upload Speed: [/FONT][/COLOR]**0.89**[COLOR=#000000][FONT=Times New Roman] Mbps (0.11 MB/sec transfer rate)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Latency: [/FONT][/COLOR]**12**[COLOR=#000000][FONT=Times New Roman] ms[/FONT][/COLOR]

```

dan@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr <REMOVED>  
          inet addr:192.168.11.2  Bcast:192.168.11.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20837 (20.8 KB)  TX bytes:28471 (28.4 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1431 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:449928 (449.9 KB)  TX bytes:449928 (449.9 KB)


wlan0     Link encap:Ethernet  HWaddr <REMOVED>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:68525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84336975 (84.3 MB)  TX bytes:25652632 (25.6 MB)


dan@ubuntu~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.11.1    0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.11.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0


dan@ubuntu:~$ ping -c4 google.com
PING google.com (74.125.224.225) 56(84) bytes of data.
64 bytes from lax04s08-in-f1.1e100.net (74.125.224.225): icmp_req=2 ttl=52 time=20.4 ms
64 bytes from lax04s08-in-f1.1e100.net (74.125.224.225): icmp_req=3 ttl=50 time=14.7 ms
64 bytes from lax04s08-in-f1.1e100.net (74.125.224.225): icmp_req=4 ttl=54 time=10.8 ms


--- google.com ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 7037ms
rtt min/avg/max/mdev = 10.806/15.326/20.463/3.966 ms

dan@ubuntu:~$ sudo ethtool eth0 
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes

```

---

### Post by varunendra on 2013-12-04
These associated --> deauthenticated loops are interesting -
```
....
[  429.146320] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=5)
[  429.146577] wlan0: associated
[  429.404572] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  433.128353] wlan0: authenticate with <MAC address removed>
....
```
Were you disconnecting it manually or was it happening by itself? Does the wireless connection seems stable (even if with slower speeds)?

Even if the effect is small, I suggest making the "nohwcrypt=Y" parameter permanent -
```
echo "options rt61pci nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt61pci.conf
```
This will make the driver always load with the parameter since next boot.

A few other things to try (one at a time) -

1) Try changing the band mode in the router to g-only if that option is available in its settings interface. Currently it seems to be in b/g mode which is okay, but the change may be worth a try.

2) Try fixing the speed to a suitable value (the highest value that seems stable and best for speed) -
```
sudo iwconfig wlan0 rate 36M
```
The other supported speeds, as per the scan results, are - 18 Mb/s; 24 Mb/s; 48 Mb/s; 54 Mb/s that are higher than what you are currently getting. You may try from the lowest of these values (18M) to highest (54M) and stop & step back where the practical throughput seems to get worse or connection becomes unstable.


For the Ethernet, we can try a similar approach, that is, trying a lower speed which is most widely supported -
```
sudo ethtool eth0 -s eth0 speed 100 duplex full autoneg off
```

Additionally, try changing the DNS to same as wifi (8.8.8.8 and 8.8.4.4) for the ethernet. Currently it is using the router as DNS which is then forwarding the requests to a real DNS.

Any improvement with these changes?

---

### Post by dani.rab on 2013-12-04
> **varunendra said:**
> Were you disconnecting it manually or was it happening by itself? Does the wireless connection seems stable (even if with slower speeds)?


it was happening by itself and the wireless connection seems stable.

didn't see a big change when running this:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo iwconfig wlan0 rate 36M[/FONT][/COLOR]
```

but this: ```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```
improved the wired connection speed to:
[COLOR=#000000][FONT=Times New Roman]Download Speed: [/FONT][/COLOR]**4.81**[COLOR=#000000][FONT=Times New Roman] Mbps (0.6 MB/sec transfer rate)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Upload Speed: [/FONT][/COLOR]**4.23**[COLOR=#000000][FONT=Times New Roman] Mbps (0.53 MB/sec transfer rate)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Latency: [/FONT][/COLOR]**14**[COLOR=#000000][FONT=Times New Roman] ms[/FONT]

[FONT=Times New Roman]still not close to the windows speed but a big improvement to the speeds I was getting before that.[/FONT][/COLOR]

---

### Post by varunendra on 2013-12-04
> **dani.rab said:**
> ..improved the wired connection speed to:
Download Speed: 4.81 Mbps (0.6 MB/sec transfer rate)
Upload Speed: 4.23 Mbps (0.53 MB/sec transfer rate)
Latency: 14 ms

still not close to the windows speed but a big improvement to the speeds I was getting before that.

Yeah, compared to the previous ridiculous speed, the current one may be a big improvement. But needless to say, it is still ridiculous. :(

In network manager settings for your wired connection, try changing the MTU value from "automatic" to 1492 > Save > Close. Does it make any positive difference?

For wireless, did you try other values? Do so if not so far. Testing is the only possible way to find the most optimal setting. If none of them seem to help, or even make the speed/stability worse, you can reset the speed to "auto" by -
```
sudo iwconfig wlan0 rate auto
```

---

### Post by dani.rab on 2013-12-05
> **varunendra said:**
> 
In network manager settings for your wired connection, try changing the MTU value from "automatic" to 1492 > Save > Close. Does it make any positive difference?


I already set my MTU manually to 1500, once I changed it to 1492 the speed was worse so I returned it to 1500.

> **varunendra said:**
> 
For wireless, did you try other values? Do so if not so far. Testing is the only possible way to find the most optimal setting.


I tried the other values but I didn't see a noticeable difference in speed.

thanks for trying to help, this issue is really frustrating, especially the wired connection.

---

### Post by varunendra on 2013-12-05
1500 is default value in Ubuntu, you don't need to set it manually. You can (probably should) set it back to "automatic" again.

The forcedeth driver in my setup has some parameters that seem to be able to optimize its performance. Let us see if the same parameters are available in the version you are using. Please post back the output of :
```
modinfo -p forcedeth
```
And also post the current output of "sudo ethtool eth0" along with it.

For WiFi, the current speeds (practical ones) seem to be what can be expected from a b-band router. Just for a test, could you try setting your router to use g-only mode? Currently it seems to be in b/g mode. Make the changes > Save & Close the management interface > physically power off both the router and your computer (disconnect the router from its power source) > wait for about 4 minutes > power them back on > connect and test the speed with WiFi.

If it seems to make things worse (it can, if the driver happens to have problem with g-band), revert back the settings and reboot it again. And if it supports N-channel, definitely turn it off, and keep it off.

Try these and let me know how it goes.

---

### Post by dani.rab on 2013-12-06
> **varunendra said:**
> 
The forcedeth driver in my setup has some parameters that seem to be able to optimize its performance. Let us see if the same parameters are available in the version you are using. Please post back the output of :
```
modinfo -p forcedeth
```
And also post the current output of "sudo ethtool eth0" along with it.


here's the output:

```

dan@ubuntu:~$ modinfo -p forcedeth
max_interrupt_work:forcedeth maximum events handled per interrupt (int)
optimization_mode:In throughput mode (0), every tx & rx packet will generate an interrupt. In CPU mode (1), interrupts are controlled by a timer. In dynamic mode (2), the mode toggles between throughput and CPU mode based on network load. (int)
poll_interval:Interval determines how frequent timer interrupt is generated by [(time_in_micro_secs * 100) / (2^10)]. Min is 0 and Max is 65535. (int)
msi:MSI interrupts are enabled by setting to 1 and disabled by setting to 0. (int)
msix:MSIX interrupts are enabled by setting to 1 and disabled by setting to 0. (int)
dma_64bit:High DMA is enabled by setting to 1 and disabled by setting to 0. (int)
phy_cross:Phy crossover detection for Realtek 8201 phy is enabled by setting to 1 and disabled by setting to 0. (int)
phy_power_down:Power down phy and disable link when interface is down (1), or leave phy powered up (0). (int)
debug_tx_timeout:Dump tx related registers and ring when tx_timeout happens (bool)

dan@ubuntu:~$ sudo ethtool eth0 
Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  Not reported
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: external
    Auto-negotiation: off
    Supports Wake-on: g
    Wake-on: g
    Link detected: yes

```

changing the band to G didn't make a big difference.

BTW, how do I make this change permanent?
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```

---

### Post by varunendra on 2013-12-06
> **dani.rab said:**
> BTW, how do I make this change permanent?
There are three common ways -
[COLOR="#800000"]**1.**[/COLOR]
The usual and most common way to run commands at startup is to add them to /etc/rc.local file, as mentioned in this thread : [http://ubuntuforums.org/showthread.php?t=1481321](http://ubuntuforums.org/showthread.php?t=1481321)

But I personally think a better way to automate something like this is adding it to upstart jobs as follows (source : [http://www.cyberciti.biz/tips/howto-linux-add-ethtool-duplex-settings-permanent.html](http://www.cyberciti.biz/tips/howto-linux-add-ethtool-duplex-settings-permanent.html)) -

[COLOR="#800000"]**2.**[/COLOR]
[indent]
1) Open your text editor and put the following contents in it -
```
#!/bin/sh

case "$1" in
start)
/sbin/ethtool -s eth0 speed 100 duplex full autoneg off;

stop)
;;
esac
exit 0
```

2) Save this file as "EthFix" (or whatever you wish, just make sure the name doesn't contain blank spaces or other special characters).

3) Run the following commands to place it in correct location and make effective -
```
sudo cp EthFix /etc/inid.d/
sudo chmod -x /etc/init.d/EthFix
sudo update-rc.d EthFix defaults
```[/indent]

[COLOR="#800000"]**3.**[/COLOR]
A much easier (and better than /etc/rc.local) place for automating this particular stuff is adding the command to /etc/network/interfaces file as mentioned here : [http://www.thegeekstuff.com/2010/10/ethtool-command/](http://www.thegeekstuff.com/2010/10/ethtool-command/)
Although I am a bit skeptical about using "interfaces" file and Network Manager for the same interface at the same time, so my personal preference is Method 2.
----------------------------------

That being answered, let's try a few parameters available with your 'forcedeth' driver, and see **if they stick** (I'm not sure if they will) and can help. If they did, it would be much more easier to make permanent (all the changes suggested below are temporary as of now, will be lost at next boot or at driver's reload).

Please try first -
```
sudo modprobe -rv forcedeth
sudo modprobe -v forcedeth optimization_mode=1
```
..and test its performance. The other values this parameter can take are 0 and 2. Try all and see if any of them does the trick.

If the above doesn't help, try this -
```
sudo modprobe -rv forcedeth
sudo modprobe -v forcedeth msi=0
```
The other value it can take is 1. Again, try both and let me know the difference if there is any.

Just like "msi=0", also try the above command set with two other available parameters "msix" and "dma_64bit". These also take values 0 and 1, try both.

Since I don't have a clear idea of what these parameters do or what their default values are, try them all and stop if any of them gives us the pleasant surprise we are craving for.

Be aware though that some of them (perhaps msi and msix) ***may*** also break the connection or cause a kernel panic with a wrong value. The good thing is that it will be temporary and everything will be reset to default on next boot (or a next cycle of driver load/unload if a restart doesn't become the only option).

Obviously, I am now trying things I have never tried before, so trust your own knowledge/instincts instead of trusting me at this point. :)

**PS:**
If anyone watching this thread has any better ideas, please join us !

---

### Post by dani.rab on 2013-12-07
I tried all the options you mentioned but it didn't seem to make a big difference, always the download speed is really low until I run
```
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```
and then it jumps to around 6-7 Mbps

---

### Post by varunendra on 2013-12-07
Hmm.. looks like I must give up on it now. One more attempt -

You mentioned in the first post that "it used to be ok a few days ago". I was wondering if it is a bug in the current kernel or the current driver that is causing the trouble.

Can you try booting with a previous kernel? In the grub menu, you can choose to boot with an older kernel. Choose this option to boot into a previous one and see if the Ethernet works at better speeds again.

Whether or not, I think it is time to submit a bug report at launchpad against the forcedeth driver or the current kernel for slow speeds, or add yourself as "Affected" to an already existing bug (although I couldn't find a bug report with same symptoms). To collect information for reporting, use the command -
```
apport-bug
```
..and proceed with prompts.

How to Report Bugs Effectively : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by coffeecat on 2013-12-07
@dani.rab, I've been following this thread with interest. If booting into an earlier kernel as varunendra suggests doesn't give you decent speeds with the forcedeth driver and ethernet, I wonder if it's worth looking at things outside your Ubuntu machine. Apologies if you've already done this and I've missed it.

You mention Ubuntu and Windows machines suggesting they are different machines. Am I correct? If so, is there any significant difference in the way they are connected to your router? For example, is the Windows machine plugged directly into the router with an ethernet cable and the Ubuntu one via an ethernet switch or perhaps even via ethernet over mains? If so, it would be worth checking to see if any of the differences are affecting your download speed in Ubuntu. You said Ubuntu used to be OK until a few days ago. Do you remember changing any networking hardware? 

Or even if the two machines are near each other, it would be a useful exercise to swap them around to each other's cables to see if the speed in either or both changes.

---

### Post by varunendra on 2013-12-07
> **coffeecat said:**
> You mention Ubuntu and Windows machines suggesting they are different machines. Am I correct?

Wow! I don't know when and why I made the assumption that it is the same machine dual booting Windows and Ubuntu.

I re-read the first post and they are clearly two different machines. That's a really strong point, and coffeecat has already given the best suggestion to test external factors.

**PS:**
@dani.rab
If the machine is Ubuntu only, you'll have to press 'Shift' or 'Esc' key during bootup to get the grub boot menu.

---

### Post by dani.rab on 2013-12-08
I connected my windows laptop to the same Ethernet cable and the speeds I got there were normal (35-40 Mbps),
but with the same cable the ubuntu machine was slow as usual.

I tried also a few older kernels but that also didn't fix the issue.

I also tried starting the same problematic machine with a Knoppix live CD and the speeds were also slow.
should I've tried a different linux distribution?

maybe it's just a hardware failure (I guess that only if I install windows on the same machine i'll know if it's a hardware or software failure).

---

### Post by coffeecat on 2013-12-08
> **dani.rab said:**
> 
maybe it's just a hardware failure (I guess that only if I install windows on the same machine i'll know if it's a hardware or software failure).

It would be interesting to know what Windows does on that machine. Somewhat tedious having to do a full install just to test that though.

I was going to suggest running a live Ubuntu session on the Windows machine, although I am not sure what that would achieve, except for proving or otherwise that Ubuntu can achieve the same download speeds as Windows on your network.

The Knoppix kernel will be compiled differently from the Ubuntu one, but will have essentially the same forcedeth driver. However, it would probably be better to test with the same Ubuntu version of the live CD/USB - 12.10 - as you are running from your Ubuntu machine. It will be the original version of the kernel, of course.

In case you do not have the 12.10 ISO and can't find the download link, here it is:

[http://releases.ubuntu.com/12.10/](http://releases.ubuntu.com/12.10/)

---

### Post by varunendra on 2013-12-09
You may try HBCD ([Hiren's Boot CD]("http://www.hiren.info/pages/bootcd")) as a "Live Windows XP" CD and see if it can recognize your Ethernet chip. It contains a PE (PreInstalled Environment) of Windows XP which provides a very limited functionality of Windows XP that runs in Live mode. The networking has to be initialized manually, for which there is a wizard icon on its desktop.

If it has driver for your card, it will be same or almost same as the one in original Windows XP, giving you the same performance. If not, external drivers can be easily added to it (of course windows XP compatible only).

---

### Post by dani.rab on 2013-12-11
I was frustrated and didn't see the reply on the "live windows xp" cd and went ahead and installed windows 7 on the machine,
after the installation the wireless speeds I got where the same as on Ubuntu but I couldn't get the wired connection to work (no internet access, seemed like I couldn't get a valid IP from DHCP), searched some more online and found this interesting post [http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489) (I also have a Realtek ethernet chip) where one of the posts said

> [COLOR=#000000]However, after reading dozens of forum articles, it seemed like the problem is that the RealTek driver doesn't reset the NIC internal configuration upon reboot. I disconnected the charger from my laptop, popped out the battery, pressed the on button a few times (to drain residual charge in capacitors), put it back together, rebooted, and it worked fine.[/COLOR]

[COLOR=#000000]Even on a desktop, where the NIC is powered when the machine is off (necessary for wake-on-lan functionality), you can reboot until the cows come home, and the NIC internal settings may not be reset. You have to disconnect the power cable to de-power the NIC. My problem surfaced while running Windows 7, but once it happened, rebooting numerous times in Windows 7 or Ubuntu 10.04 did not resolve the problem. Downgrading to r8168, as described in this article did not resolve the problem.[/COLOR]

[COLOR=#000000]So, my suggestion is to try the simple workaround of disconnecting power from the machine before subjecting yourself to the trauma of all the procedures listed above.[/COLOR]

I don't know why I didn't think of it but like he said I shutdown my computer and disconnect the power cable and suddenly next restart the ethernet started working again and I got the speeds I expected, hooray  :P.

thanks everyone for your suggestions and help finally this issue is solved (not on Ubuntu but at least it's working).

---

