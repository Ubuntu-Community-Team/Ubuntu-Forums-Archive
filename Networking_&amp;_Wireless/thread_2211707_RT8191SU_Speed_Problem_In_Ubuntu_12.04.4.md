---
title: "RT8191SU Speed Problem In Ubuntu 12.04.4?"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by Akacheebe on 2014-03-17
I've had problems with N speeds being slow starting with an N13 Asus adapter that I had last year.  Never did get that issue resolved and finally gave up and just went back to the wired connection.  I recently purchased a newer RT8191SU adapter to see if it was any better and have a couple of questions concerning that hardware, which is slow also.

When I did this clean install a few weeks ago Ubuntu 12.04.4 saw the RT8191SU adapter and I did the install along with updates from the internet with no problems.  However I noticed that the connect speed is much lower than Windows XP on this same hardware, ie, this is a dual boot system with two hard drives, one for Ubuntu and one for Windows.  Windows will consistently connect at 145 Mb/s while Ubuntu 12.04 will show me 150Mb/s when the adapter is first connected but within 30 seconds or so it will fall back to 72Mb/s and stay there, effectively running at half speed.  The driver listed is r8712u which is "suppose" to be the current driver for this RT8191SU chipset.  The wireless router I'm using is a Cradlepoint MBR1000 which is capable of 150Mb/s speed, which Windows shows.  

So my question is, is there some setting in the driver configuration that's causing this adapter to drop back to 72Mb/s and if so, is there an easy fix for that?  Oh, and please keep in mind that I'm not very good with command line stuff!

Here's some info from this system:

```
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        XX:XX:XX:37:5E:1E

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [MBR-57d] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             connected
  Default:           yes
  HW Address:        XX:XX:XX:AC:B4:XX

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *MBR-57d:        Infra, XX:XX:44:XX:FF:EF, Freq 2452 MHz, Rate 54 Mb/s, Strength 96 WPA2

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
 
```

```
dmesg | tail
[   28.878615] type=1400 audit(1395066987.600:48): apparmor="STATUS" operation="profile_replace" parent=994 profile="unconfined" name="sanitized_helper" pid=1001 comm="apparmor_parser"
[   29.800470] r8712u 1-2:1.0 wlan0: 1 RCR=0x153f00e
[   29.801207] r8712u 1-2:1.0 wlan0: 2 RCR=0x553f00e
[   29.908515] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.909025] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.916441] sky2 0000:02:00.0 eth0: enabling interface
[   29.916579] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.917312] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.419249] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1227.001758] r8712u 1-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = XX:XX:XX:06:ff:ef, seq = 41840, tid = 0
ken@UbuntuYB:~$ 
ken@UbuntuYB:~$ 
ken@UbuntuYB:~$ lsusb
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
```

Thanks

---

### Post by chili555 on 2014-03-18
What is the real-world result, instead of the theoretical result? In other words, when you are transferring data across your own network, what does *iwconfig* report? Do the driver and the router negotiate a higher speed? The reason I'm asking about an internal transfer is that I assume you haven't a fiber connection to your ISP capable of 150 Mb/s speeds or higher.

I saw a nice increase in speeds when I switched my router to only use 20 MHz in the 2.4 GHz band, instead of Auto 20/40. I suggest you experiment with all three methods; 20 only, 40 only and auto.

The driver has quite a few parameters available:```
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)

```The usual method is to try some parameter temporarily:```
sudo modprobe -r r8712u
sudo modprobe r8712u <some_parameter>=1
```If it helps, write a conf file to make it permanent.

Sounds great, eh? The only trouble is that I haven't yet been able to find any documentation of what all these do and the defaults. I have seen many a case where a person read some random forum post and wrote a beautiful conf file that loaded the module with a parameter set to default! For example, I don't like <some_parameter>=1 so I'm going to carefully create an /etc file to use <some_parameter>=1. Makes no sense, does it?

We don't know, until we find some documentation, for example, what video_mode does or if it is germaine to our situation. Also, without documentation, we don't know if the driver default is video_mode=1 or =0 or ... what.

Finally, is power management on or off when the speed drops?```
iwconfig
```Here is a sample from my machine:```
wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:5.805 GHz  Access Point: xx:D7:19:41:54:xx
          Bit Rate=120 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [COLOR="#FF0000"]Power Management:off[/COLOR]
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3833  Invalid misc:178   Missed beacon:0
```Does the speed drop when power management kicks in? If you start a big transfer, does power management kick off and allow those tasty 150 Mb/s speeds?

I suggest we both search for r8712u video_mode and see if we can find a document that tells us more than what we already know above.

We are on the far frontier of my limited experience here.

---

### Post by Akacheebe on 2014-03-18
Humm, don't quite understand all that but what it seems to mean to me is there's no easy solution?  Yes/no?

FYI I've got "several" computers on my LAN and I record a lot of FTA TV from satellite feeds, which are usually HD and a one hour TV program is between 6 and 7 GB in size.  I usually edit those and reduce the size quite a bit but when moving them between computers at 72Mb/s it's really slow.  

That and one of my systems seems to be a lightning rod as that computer lost 2 gigabit PCI network cards last year and I'm afraid that it's going to take the motherboard when the next one gets fried, hence the need for wireless on that system.  

Ennywho, I ordered one of these last weekend as this is the replacement Atheros chipset for the one that's recommended in the networking wiki that's no longer available.  If there's no easy fix for this RTL8191SU I guess I'll just wait for that new one to get here and see how it works.  Since it's coming from China it's going to take a couple of weeks for it to show up.  The price was right though.

[http://www.ebay.com/itm/141222684247?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649](http://www.ebay.com/itm/141222684247?ssPageName=STRK:MEWNX:IT&_trksid=p3984.m1439.l2649)

Thanks for your help!!

---

### Post by chili555 on 2014-03-18
> what it seems to mean to me is there's no easy solution? Yes/no?What at least part of it was intended to convey is that there may well be a quick, free and easy solution if you'll try a different setting or two in the router. Did you try?

It also tried to convey that power management may be a factor and to monitor it. Did you?

---

### Post by Akacheebe on 2014-03-19
Power Management is off!

Looks like setting the router to 20/40MHz instead of 20MHz (only 2 settings) doubled the speed that was displayed not only on this card but also on the N13 adapter in the other computer.  Throughput didn't double though and it still will take over 40 minutes to transfer a 6.6GB file from one to the other.  At the 20MHz setting that same file takes 55 minutes.  

The N-13 wireless adapter is showing me a connect speed up at 270Mb/s which isn't possible because the router won't go above 150Mb/s and I've got the same problem with a Linksys wireless adapter in m Dell 1100 laptop.  So there is "some" increase in speed but nothing to write home about.  I'm beginning to think that part of the problem lies with the router which I plan to upgrade this summer.  

So bottom line is switching the settings in the router did help some but it's still a long way from being fixed as throughput is only 2.8Mb/s on a good day and that's really way off of the "rated" 150Mb/s it's suppose to do.

---

