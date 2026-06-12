---
title: "Broadcom BCM4401 not working"
date: 2015-07-14
forum: Networking &amp; Wireless
---

### Post by truetech08 on 2015-07-14
Running 14.04LTS. I was having issues with the wireless card as well and got help at the following post: [http://ubuntuforums.org/showthread.php?t=2277124&p=13280357#post13280357](http://ubuntuforums.org/showthread.php?t=2277124&p=13280357#post13280357), but was directed to start a new post for wired, so here we go!

Symptom is no connection via wired network. When plugged in, wireless icon at top animates like it's trying to connect to a wireless network, then a message pops up that I am "disconnected - you are now offline" for the Ethernet network. Continues this indefinitely. I permanently disconnected from the wireless network on purpose so that I'm only working with wired. (Not sure if it matters, but my wireless is pretty flaky even after getting resolved on the other post. Using b43 driver there. Connects for a while, then disconnects. Edit: By disconnect, I mean actual internet access goes away; connection to router remains). Haven't been able to download updates yet, and when trying to do a flashback to use gnome instead of unity, it says it can't find it.)

Back to wired:
Output of lspci says that the driver=b44, driverversion=2.0.

Output of lsmod:

```
user@user-Inspiron-5100:~$ sudo lsmod
Module                  Size  Used by
ctr                    12905  3 
ccm                    17496  3 
snd_intel8x0           33110  2 
joydev                 17101  0 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
gpio_ich               13229  0 
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
arc4                   12536  2 
dell_laptop            17808  0 
b43                   356470  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
dcdbas                 14448  1 dell_laptop
bcma                   42043  1 b43
rfcomm                 53664  0 
radeon               1416373  2 
bnep                   18895  2 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
bluetooth             342263  10 bnep,rfcomm
snd_timer              28584  2 snd_pcm,snd_seq
pcmcia                 51828  0 
mac80211              545990  1 b43
snd                    60871  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
ttm                    72698  1 radeon
yenta_socket           40201  0 
psmouse                91033  0 
drm_kms_helper         46907  1 radeon
serio_raw              13230  0 
soundcore              12600  1 snd
cfg80211              409394  2 b43,mac80211
pcmcia_rsrc            18319  1 yenta_socket
lpc_ich                16864  0 
drm                   243792  4 ttm,drm_kms_helper,radeon
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
i2c_algo_bit           13197  1 radeon
mac_hid                13037  0 
shpchp                 32128  0 
video                  18903  0 
parport_pc             31981  0 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
b44                    31275  0 
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ssb                    51854  2 b43,b44
mii                    13654  1 b44

``` 

Sample of output from dmesg | grep b44:

[1.688...] b44: Broadcom 44xx/47xx 10/100 PCI Ethernet driver version 2.0
[1.708...] b44: ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI Ethernet driver 00:0d:56:37:6d:81
[982.000218] b44 ssb1:0 eth0: Link is up at 10Mbps, full duplex
[982.000226] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[983.000152] b44 ssb1:0 eth0: Link is down
[1000.000214] b44 ssb1:0 eth0: Link is up at 10Mbps, full duplex......from here it cycles through the previous 3 entries.

I'm not sure what I'm looking for here, just giving some of what I know I've been asked in the past. Please let me know what other info might be needed!

---

### Post by praseodym on 2015-07-15
Try loading the wireless and wired drivers in another order:

```
echo -e "blacklist b43\nblacklist b44\nblacklist ssb\nblacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist-test.conf 
sudo sed -i "s/exit 0/# starting order for the broadcom drivers/g" /etc/rc.local
echo -e "modprobe ssb\nmodprobe bcma\nmodprobe b43\nmodprobe b44\nexit 0" | sudo tee -a /etc/rc.local
```
Reboot and check
```

ifconfig -a
route -n
dmesg | grep b4
```

---

### Post by truetech08 on 2015-07-15
Thanks Praseodym. After running all commands, output of the last one shows


[1.756...] b44: Broadcom 44xx/47xx 10/100 PCI Ethernet driver version 2.0
 [1.776...] b44: ssb1:0: eth0: Broadcom 44xx/47xx 10/100 PCI Ethernet driver 00:0d:56:37:6d:81

Still get the disconnected notice every 10-20 seconds, and running dmesg | grep b44 yields same as before.

Anything else I can try?

---

### Post by praseodym on 2015-07-16
Please check
```

sudo apt-get install ethtool
sudo ethtool eth0
```

---

### Post by truetech08 on 2015-07-22
Sorry for the delayed response. I haven't been able to get back to this yet, and I think it'll be about a week before I do, but I will post back as soon as I perform your check. If you think of anything additional you want me to try in the meantime, let me know, I'll do that too. Thanks again!

---

### Post by truetech08 on 2015-07-28
Ok, back again, output for first command was 

```

ethtool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 221 not upgraded.

```

Output for the second command:

```

settings for eth0:
    Supported ports: [ MII ]
    Supported link modes: 10baseT/Half 10baseT/Full
                                      100baseT/Half 100baseT/Full
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes: 10baseT/Half 10baseT/Full
                                      100baseT/Half 100baseT/Full
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 10MB/s
    Duplex: Half
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: g
    Wake-on: d
    Current message level: 0x000000ff (255)
                                      drv probe link timer ifdown ifup rx_err tx_err
    Link detected: no

```

---

### Post by praseodym on 2015-07-29
> 221 not upgraded

Try 

```
sudo ethtool -s eth0 speed 100 autoneg off
```
If it doesn't work, revert it via
```

sudo ethtool -s eth0 speed 10 autoneg off
```

---

### Post by truetech08 on 2015-07-29
Ok, the first command had no effect, i.e. every few seconds I get the disconnected notification, and it appears to try again. The wireless icon at the top flashes while it tries. Running the second command appears to stop it from trying to connect at all. Notifications stop, and the wireless icon becomes empty and unanimated.


Should the wireless icon change from a wireless signal to a wired icon when I plug in? Seems odd that it would use a wireless icon when wired is connected. I hope there's more up your sleeve, but thanks so far for your help.

---

### Post by truetech08 on 2015-08-01
Bump.

---

### Post by truetech08 on 2015-08-05
One more try....bump.

---

