---
title: "Slow wireless after increasing bandwidth ISP service"
date: 2014-06-26
forum: Networking &amp; Wireless
---

### Post by pmasson on 2014-06-26
I recently upgraded my internet service from 20Mbs to 50Mbs and since  then have been experiencing extremely poor speed (as low as .1 Mbs).  Previously I was not experiencing any issues. Other machines  running on the same wifi (Windows 8, Mac OS and even a Droid smartphone)  all are seeing increased speed up to 50Mbs+. I've done speedtests  simultaneously and the Mac and Windows machines run great while the Ubuntu  laptop lags.

I have also connected to the modem/router directly and the speed is as expected, 50Mbs+.

I am running 12.04 LTS on an HP EliteBook Folio 9470m.

Running ```
lshw -C network
``` reveals:

```

  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6235
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 24
       serial: b4:b6:76:d7:20:b2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-42-generic firmware=18.168.6.1 ip=192.168.0.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:d0400000-d0401fff

```

Looking at the connection information through the shows:

```

Interface: 802.11 WiFi (wlan0)
Driver:    iwlwifi
Speed:    1 Mb/s
Security: WPA/WPA2

```

Any suggestions or even places to start looking would be appreciated.

Thanks - Patrick

---

### Post by chili555 on 2014-06-27
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or vim if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot the computer and let us hear your report.

---

### Post by pmasson on 2014-06-27
> First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP.
I believe I have "WPA2-PSK" set with "WPA/WPA2 Encryption" set to "AES" (see attached screen shot, "SecConfig.png").

> Second, if your router is capable of N speeds, I have better luck with a  channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40  MHz.
I have:
802.11 n-mode, set to: "Auto" (vs. "Off")
802.11 N Support Required, set to: "On" (vs. "Off")
Bandwidth / Current :  20MHz, set to "20MHz" (vs. "40MHz")    

> I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. 
I have:
Control Channel set to: "1"  

> After making these changes, reboot the router.
Rebooted and logged back in to see that the settings stuck.

> Next, I recommend that your regulatory domain be set explicitly.
```

sudo iw reg get
country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (57240 - 63720 @ 2160), (N/A, 0)

```

> Set it permanently, Change the last line to read: [FONT=courier new]REGDOMAIN=IS[/FONT] 
Set to my country code to "US" in the file.

> Next, I'd set IPv6 to Ignore in Network Manager:
Done (See attached screen shot, "NetworkConnections.png")

Restarting... .. .

---

### Post by chili555 on 2014-06-27
Looks awesome so far!

---

### Post by pmasson on 2014-06-27
> Looks awesome so far!

Sadly, no change. 

I again checked the modem/router to ensure the config was correct after the reboot (and it was), and the [FONT=courier new]sudo iw reg get[/FONT] reveals:
```

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)

```

The "Connection Information" is also confirming IPv6 is "Ignored" (See screen shot, "ConnectionInfo2.png").

Thanks so much for your help - can I impose for any other suggestions?

---

### Post by chili555 on 2014-06-27
As sometimes happens, I'm corn-fused. Your original post says speeds as low as .1 Mb/s. Your attachment, after all the changes, shows 130 Mb/s. Is the real world performance still poor? What does this tell us?```
iwconfig
```

---

### Post by pmasson on 2014-06-27
> Your original post says speeds as low as .1 Mb/s. Your attachment, after  all the changes, shows 130 Mb/s
Yes I have done several speed tests and traceroutes and have seen ranges from 0.1Mbs - 57Mbs, however the majority of the time I have very slow performance or simply time out. See two tests attached. 

Right now (while writing this) for example, my speed has fluctuated from  "65 Mb/s" to "130Mb/s" to "1Mb/s" (see "ConnectionInfo3.png") Sometimes connectivity is speedy, other times non-existent (timing out) so "the real world performance still  poor." (funny thing, when I took the screen shot of the "Connection Information" I saw it switch from "1Mb/s" to "130Mb/s" and thought, "Damn how chili555 is going to think I am a twit.")

While I have seen this fluctuation on my machine, testing a Windows8 and  Mac at the same time as mine shows that they are unaffected and are  connecting fine. Also I have taken my machine out to other "wifi hot  spots" (public places) and am not experiencing connection issues there (although I could have been experiencing one of the good fluctuations).

[FONT=courier new]iwconfig[/FONT] reveals:

```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"NSA Stay Off"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 08:3E:8E:1A:01:57   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-20 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:260   Missed beacon:0

```

---

### Post by praseodym on 2014-06-27
Check the mtu value of your ISP and add it as number instead of "Automatic" in your network manager profile. Did you try to deactivate IPv6 ("Ignore")? Reconnect after each step. Check
```

ifconfig -a
```

---

### Post by pmasson on 2014-06-27
> Check the mtu value of your ISP and add it as number instead of "Automatic" in your network manager profile.

Not sure this is right, but set MTU to 1600 based on, "Maximum frame size: ELAN supports a Maximum Transmission Unit (MTU)  packet size of 1600 bytes to support untagged or 802.1Q tagged packet  sizes."  ([http://www.timewarnercable.com/services/network-services/ethernet/ethernet-local-area-network/tech-specs.html](http://www.timewarnercable.com/services/network-services/ethernet/ethernet-local-area-network/tech-specs.html))

Disconnected/reconnected and it "feels" better. Ran speed test. Results:
[LIST]
[*]Ping: 19ms
[*]Download: 55.74Mbs
[*]Upload: 5.63Mbs
[/LIST]

> Did you try to deactivate IPv6 ("Ignore")?
Yes, IPvG in Connection information is shown as "ignored."

[FONT=courier new]ifconfig -a[/FONT] reveals:

```

eth0    Link encap:Ethernet  HWaddr a0:48:1c:df:a7:a2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:21793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17697296 (17.6 MB)  TX bytes:3296510 (3.2 MB)
          Interrupt:17 Memory:d0700000-d0720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:712578 (712.5 KB)  TX bytes:712578 (712.5 KB)

wlan0  Link encap:Ethernet  HWaddr b4:b6:76:d7:20:b2  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b6b6:76ff:fed7:20b2/64 Scope:Link
          inet6 addr: 2604:6000:f801:5200:b969:7c3e:370f:60a1/64 Scope:Global
          inet6 addr: 2604:6000:f801:5200:b6b6:76ff:fed7:20b2/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1600  Metric:1
          RX packets:262305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101392 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:353621006 (353.6 MB)  TX bytes:44037459 (44.0 MB)

```

(BTW - Thank you for your help! I think I am actually picking up a few bits of knowledge as well)

---

### Post by praseodym on 2014-06-27
```
wlan0  Link encap:Ethernet  HWaddr b4:b6:76:d7:20:b2  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          [COLOR="#FF0000"]inet6[/COLOR] addr: fe80::b6b6:76ff:fed7:20b2/64 Scope:Link
          [COLOR="#FF0000"]inet6[/COLOR] addr: 2604:6000:f801:5200:b969:7c3e:370f:60a1/64 Scope:Global
          [COLOR="#FF0000"]inet6[/COLOR] addr: 2604:6000:f801:5200:b6b6:76ff:fed7:20b2/64 Scope:Global
```
Did you reconnect?
```

sudo service network-manager restart
```
Alternatively, try to deactivate it system-wide:

```
net.ipv6.conf.all.disable_ipv6=1  
net.ipv6.conf.default.disable_ipv6=1  
net.ipv6.conf.lo.disable_ipv6=1
```
Add these lines to the file ```
/etc/sysctl.conf
``` and reboot.

---

### Post by pmasson on 2014-06-27
Regarding the [COLOR=#FF0000]inet6[/COLOR] addr, I saw that but thought perhaps--although it was addressed--it was ignored (maybe I am wrong - I generally am).

> Did you reconnect?
Yes. And did again (in both the terminal and in the GUI), but still see:

```

wlan0     Link encap:Ethernet  HWaddr b4:b6:76:d7:20:b2  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b6b6:76ff:fed7:20b2/64 Scope:Link
          inet6 addr: 2604:6000:f801:5200:b969:7c3e:370f:60a1/64 Scope:Global
          inet6 addr: 2604:6000:f801:5200:b6b6:76ff:fed7:20b2/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1600  Metric:1
          RX packets:272004 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:359735690 (359.7 MB)  TX bytes:48441361 (48.4 MB)

```

Added to [FONT=courier new]/etc/sysctl.conf[/FONT]

```

net.ipv6.conf.all.disable_ipv6=1   
net.ipv6.conf.default.disable_ipv6=1   
net.ipv6.conf.lo.disable_ipv6=1

```

Rebooting... .. .

(Actually things seem to be humming right now. I am tempted to hold on for a while to see if the issues come back.)

---

### Post by pmasson on 2014-06-27
HMMMMM!!!! Actually no, not good. I was just playing Minecraft with my son and initially we were both humming, then I started lagging, then timed out.

However, by disabling the ipv6 in [FONT=courier new]/etc/sysctl.conf[/FONT], and now running [FONT=courier new]ifconfig -a[/FONT] I see that the ipv6 info is no longer there.

```

wlan0     Link encap:Ethernet  HWaddr b4:b6:76:d7:20:b2  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1600  Metric:1
          RX packets:164212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17430376 (17.4 MB)  TX bytes:2815364 (2.8 MB)

```

Thanks again to you both. Any other ideas? Am I annoying yet?

---

### Post by chili555 on 2014-06-27
Annoying? Not at all. We aren't yet over 100 replies!

I really hate to sink this low, but please try:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot.

Do you have the latest firmware?```
sudo dpkg -s linux-firmware | grep -i version
```I have Version: 1.127.4. If yours is not the latest, then:```
sudo apt-get update && sudo apt-get upgrade
```...and then reboot.

---

### Post by pmasson on 2014-06-28
OK, created [FONT=courier new]/etc/modprobe.d/iwlwifi.conf[/FONT] with the line [FONT=courier new]options iwlwifi 11n_disable=1[/FONT] (it's the only line in the file--not sure if [FONT=courier new]iwlwifi.conf [/FONT]should already have existed)

Rebooted 

[FONT=courier new]sudo dpkg -s linux-firmware | grep -i version[/FONT] reveals: "Version: 1.79.16"

Ran [FONT=courier new]sudo apt-get update && sudo apt-get upgrade[/FONT] then [FONT=courier new]sudo dpkg -s linux-firmware | grep -i version[/FONT]. Still reporting I am running "Version: 1.79.16"

Rebooting... .. .

---

### Post by pmasson on 2014-06-28
Again thank you (only 85 posts to go!).

I am on wireless now, let me see how things go and I will report back.

---

### Post by pmasson on 2014-06-29
I'm tempted to mark this [SOLVED] as I have not been experiencing any  issues, even with three other users in the house. Just wanted to give an  update to let you know your advice might have just done the trick. I'd  be curious what each of the recommended steps did and how that affects  service (I'd just like to learn--maybe I can help someone else later).

I'll keep monitoring and if in a couple days there are no more problems I will give a final update and close the thread.

---

### Post by pmasson on 2014-07-02
I have not experienced any problems with my wireless and my connectivity is actually very good now. Many thanks to "chili555" for his/her help.

I'm  not sure if the solution to my problem(s) required all of the steps  suggested throughout the thread--maybe it was one particular change that  made the difference. So in order to help others who may come later,  I'll simply share my current environmental settings so that if you're  running something close to what I am and experiencing the same issues,  you can try and match my configuration.

**Primary complaint**: Slow or no connectivity to wireless network.
**Symptoms**: Lagging on video games, slow to load web pages, poor connectivity reported through Network Connection Information. 
**Antecedent**:  Upgraded from 20Mbs "Turbo" to 50 Mbs "Extreme" through Time Warner  Cable. Swapped out Netgear router and Arris modem for Ubee combination  router modem (told by TWC this was required in order to handle increased  bandwidth). To be honest, I was experiencing poor connectivity prior to  the upgrade, so my personal issue could have been affecting me before  the move to a new modem/router. However, my choice to upgrade was based  on generally poor performance due to an increased number of users at  home (wife, on a Mac and two children, one on Windows8 and one on an  iPad, all online) and because everyone was experiencing poor  connectivity, I contacted our ISP to increase speed. After the upgrade I  was the only user still experiencing poor performance. So I am  confident the updrade in speed addressed the other users' issues and  mine was a local problem on my machine.

I believe (hope) these are all of the settings that were touched while working  through the problems. If there are other configuration settings you are  interested in for a similar environment, feel free to ask and I will look  up what I have.

Sorry if you're reading this - hope this helps to figure out your issue(s).

**_Physical Hardware_**
[B]
Laptop[/B]: 
[LIST]
[*][HP EliteBook Folio 6470m]("http://shopping1.hp.com/is-bin/INTERSHOP.enfinity/WFS/WW-USSMBPublicStore-Site/en_US/-/USD/ViewStandardCatalog-Browse?CatalogCategoryID=8TkQ7habav8AAAFD_OYsvqtR")
[LIST]
[*]Intel Core™ i7-3687U CPU @ 2.10GHz × 4
[*][Intel Centrino Advanced-N 6235 Wi-Fi plus Bluetooth Adapter]("http://www.intel.com/content/www/us/en/wireless-products/centrino-advanced-n-6235.html")
[/LIST]
[/LIST]

**Cable Modem**:
[LIST]
[*][Ubee/Ambit DVW3201B Advanced Wireless Voice Gateway]("http://www.timewarnercable.com/en/residential-home/support/faqs/faqs-equipment-and-instruction-manuals/modems/thomsonrca1/ubee-ambitdvw3201B.html"): DOCSIS 3.0 Compliant
[*]Hardware Version : 3.7.5
[/LIST]


**_Software_**
[B]
Laptop[/B]: 
[LIST]
[*]Ubuntu 12.04 LTS
[/LIST]

**Cable Modem**:
[LIST]
[*]Boot Code Version : 10.2.1a
[*]Software Version : 9.9.2013R2SIP
[*]CA Key : Installed
[/LIST]

**Wireless LAN:**
[LIST]
[*]logical name: wlan0
[*]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
[*]configuration:
[LIST]
[*]broadcast=yes
[*]driver=iwlwifi
[*]driverversion=3.8.0-42-generic
[*]firmware=18.168.6.1
[*]ip=192.168.0.8
[*]latency=0
[*]link=yes
[*]multicast=yes
[*]wireless=IEEE 802.11abg
[/LIST]
[/LIST]


[U][B]Current Configuration

[/B][/U]**Laptop Connection Information:**
[LIST]
[*]Interface: 802.11 WiFi (wlan0)
[*]Driver: iwlwifi
[*]Security: WPA/WPA2
[*]IPv4: Active (IP infomration displays)
[*]IPv6: Ignored
[/LIST]

**Laptop Devices - Network Tools**:
[LIST]
[*]Wireless Interface (wlan0)
[*]Multicast: Enabled
[*]MTU 1600 (as recomended by ISP - yours may vary)
[*]Link speed: yours will vary
[*]State: Active
[/LIST]

**sudo iw reg get**[INDENT][FONT=courier new]country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)[/FONT]
[/INDENT]

**iwconfig**[INDENT][FONT=courier new]eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"YOUR SSID NAME HERE"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: "YOUR INFO HERE"   
          Bit Rate=54 Mb/s <YOURs WILL VARY>   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:2   Missed beacon:0[/FONT]
[/INDENT]
[B]
more /etc/sysctl.conf[/B][INDENT][FONT=courier new]#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See [http://lwn.net/Articles/277146/](http://lwn.net/Articles/277146/)
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#

# Added by passon on 6/27/14 to ignore IPv6
# Advice from [http://ubuntuforums.org/newreply.php?do=postreply&t=2231649](http://ubuntuforums.org/newreply.php?do=postreply&t=2231649)
net.ipv6.conf.all.disable_ipv6=1  
net.ipv6.conf.default.disable_ipv6=1  
net.ipv6.conf.lo.disable_ipv6=1[/FONT]
[/INDENT]

**ifconfig -a**[INDENT][FONT=courier new]wlan0     Link encap:Ethernet  HWaddr b4:b6:76:d7:20:b2  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1600  Metric:1
          RX packets:2247727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1807575 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1060157767 (1.0 GB)  TX bytes:293126641 (293.1 MB)[/FONT]
[/INDENT]

**/etc/modprobe.d/iwlwifi.conf**[INDENT][FONT=courier new]options iwlwifi 11n_disable=1[/FONT][/INDENT]
[B]
sudo dpkg -s linux-firmware | grep -i version[/B][INDENT][FONT=courier new]Version: 1.79.16[/FONT]
[/INDENT]


**_Cable Model Configuration_**
[B]
Wireless Radio[/B]
[LIST]
[*]Wireless Interfaces: [Name of your wireless SSID]
[*]Wireless: Enabled
[*]Country: [Find your country]
[*]802.11 Band: [2.4 GHz] | Current :  2.4 GHz
[*]802.11 n-mode: [Auto]
[*]802.11 N Support Required: [On]
[*]Bandwidth: [20MHz] | Current: 20MHz
[*]Sideband for Control Channel (40 Mhz only): [None]
[*]Control Channel: Current: [1] ***Interference Level: Acceptable
[*]Regulatory Mode: [Off]
[*]TPC Mitigation (db): [0 (Off)]
[*]OBSS Coexistence: [1 (Enabled]
[*]STBC Tx: [Auto]
[/LIST]

**Wireless Primary Network**
[LIST]
[*]Primary Network: [Enabled]
[*]Network Name (SSID): [Name of your wireless SSID]
[*]Closed Network: [Disabled]
[*]AP Isolate: [Disabled]
[*]WPA: [Disabled]
[*]WPA-PSK: [Disabled]
[*]WPA2: [Disabled]
[*]WPA2-PSK: [Enabled]
[*]WPA/WPA2 Encryption: [AES]
[*]WPA Pre-Shared Key: [Your key]
[*]Show Key [Unchecked]
[*]RADIUS Server [0.0.0.0]
[*]RADIUS Port [1812]
[*]RADIUS Key: [Blank]
[*]Group Key Rotation Interval: [0]
[*]WPA/WPA2 Re-auth Interval: [3600] Value Range: 1~65535
[*]WEP Encryption: [Disabled]
[*]Shared Key Authentication: [Optional]
[*]802.1x Authentication: [Disabled]
[*]Network Key 1: [0]
[*]Network Key 2: [0]
[*]Network Key 3: [0]
[*]Network Key 4: [0]
[*]Current Network Key: [1]
[*]PassPhras: [Blank]
[/LIST]

**Automatic Security Configuration:**
[LIST]
[*][WPS]
[*]WPS Config State: Configured
[SIZE=1]The physical button on the AP will
provision wireless clients using
 Wi-Fi Protected Setup (WPS)[/SIZE]
[*]Device Name: [UbeeAP]
[/LIST]

**WPS Setup AP:**
[LIST]
[*]UUID:[Your UUID]
[*]PIN [Your PIN]
[/LIST]

**WPS Add Client:**
[LIST]
[*]Add a client:
[*]Client ID: [Blank]
[*]Authorized Client MAC: [Blank]
[/LIST]

---

