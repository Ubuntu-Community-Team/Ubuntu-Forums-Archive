---
title: "Intel Corporation Centrino Ultimate-N 6300 (rev 3e), poor performance, win7 works"
date: 2013-09-29
forum: Networking &amp; Wireless
---

### Post by twjohnso on 2013-09-29
I have 13.04 running, dual booting with Win7 (which works without issue.)  Working with a direct network cable connection is fine. I'm fairly inexperienced with Linux.

I seem to be getting really inconsistant performance.  Various other devices in the house (same location, or even further from the wireless router) perform far better (iPads, Droid phone, Wii, other laptops, etc).

I specified the BBSID from the pulldown, and disabled IPV6 as per other suggestions found... but they don't appear to have resolved the problem.  Even loading simple search results from google are agonizingly slow.  I've been using speedtest.net too for testing.

Info as quested from [HOWTO post a Wireless issue (ticket)]("http://ubuntuforums.org/showthread.php?t=982880"):
[LIST=1]
[*]**Model Info**
```
Dell Latitude E6420
``` 
[*]**Wireless Brand, Model and Wireless Chipset**
```
02:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 3e)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at e2d00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
``` 
[*]**Check Interface**
```
wlan0     IEEE 802.11abgn  ESSID:"JohnsonsHome"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:21:91:09:2B:0B   
          Bit Rate=130 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:825  Invalid misc:46   Missed beacon:0
``` 
[*]**Check for modules**
```
Module                  Size  Used by
rfcomm                 37420  12 
bnep                   17669  2 
snd_hda_codec_hdmi     36186  1 
snd_hda_codec_idt      63896  1 
arc4                   12543  2 
iwldvm                220215  0 
mac80211              526519  1 iwldvm
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
joydev                 17097  0 
snd_hda_intel          38307  5 
snd_hda_codec         117617  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
coretemp               13131  0 
snd_pcm                80890  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm_intel             126842  0 
kvm                   376505  1 kvm_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
aesni_intel            18156  1 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
snd_seq_midi           13132  0 
gf128mul               14503  2 lrw,xts
ablk_helper            13357  1 aesni_intel
snd_seq_midi_event     14475  1 snd_seq_midi
cryptd                 15613  1 ablk_helper
snd_rawmidi            25114  1 snd_seq_midi
ppdev                  12817  0 
dell_wmi               12601  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
sparse_keymap          13658  1 dell_wmi
iwlwifi               155108  1 iwldvm
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
parport_pc             27504  0 
i915                  539721  4 
snd                    56485  19 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
wmi                    18590  1 dell_wmi
video                  18894  1 i915
drm_kms_helper         47545  1 i915
dell_laptop            17161  0 
drm                   228489  5 i915,drm_kms_helper
dcdbas                 14021  1 dell_laptop
mei                    36197  0 
psmouse                81065  0 
btusb                  17986  0 
bluetooth             202226  22 bnep,btusb,rfcomm
i2c_algo_bit           13197  1 i915
cfg80211              436243  3 iwlwifi,mac80211,iwldvm
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
microcode              18286  0 
mac_hid                13037  0 
soundcore              12600  1 snd
lpc_ich                16925  0 
serio_raw              13031  0 
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
sdhci_pci              18158  0 
sdhci                  31824  1 sdhci_pci
e1000e                174556  0
``` 
[*]**Kernel Boot Messages**
```
[   10.276627] iwlwifi 0000:02:00.0: irq 42 for MSI/MSI-X
[   10.369723] iwlwifi 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[   10.408866] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.408869] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.408870] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.408871] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   10.408872] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   10.408874] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   10.408976] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   14.534090] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   14.541376] iwlwifi 0000:02:00.0: Radio type=0x0-0x3-0x1
[   14.905600] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   14.912451] iwlwifi 0000:02:00.0: Radio type=0x0-0x3-0x1
[   15.149210] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.149540] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.668599] wlan0: authenticate with 00:21:91:09:2b:0b
[   21.741737] wlan0: send auth to 00:21:91:09:2b:0b (try 1/3)
[   21.744265] wlan0: authenticated
[   21.746310] wlan0: associate with 00:21:91:09:2b:0b (try 1/3)
[   21.749591] wlan0: RX AssocResp from 00:21:91:09:2b:0b (capab=0x431 status=0 aid=3)
[   21.766118] wlan0: associated
[   21.766153] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  244.500536] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  351.500321] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[ 3450.099717] wlan0: deauthenticated from 00:21:91:09:2b:0b (Reason: 6)
[ 3453.441921] wlan0: authenticate with 00:21:91:09:2b:0b
[ 3453.455632] wlan0: send auth to 00:21:91:09:2b:0b (try 1/3)
[ 3453.459275] wlan0: authenticated
[ 3453.461425] wlan0: associate with 00:21:91:09:2b:0b (try 1/3)
[ 3453.464722] wlan0: RX AssocResp from 00:21:91:09:2b:0b (capab=0x431 status=0 aid=3)
[ 3453.482613] wlan0: associated
[ 5138.768725] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[ 8852.653156] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[14905.868503] wlan0: deauthenticating from 00:21:91:09:2b:0b by local choice (reason=3)
[14914.127978] wlan0: authenticate with 00:21:91:09:2b:0b
[14914.147677] wlan0: send auth to 00:21:91:09:2b:0b (try 1/3)
[14914.150966] wlan0: authenticated
[14914.153750] wlan0: associate with 00:21:91:09:2b:0b (try 1/3)
[14914.157212] wlan0: RX AssocResp from 00:21:91:09:2b:0b (capab=0x431 status=0 aid=3)
[14914.167577] wlan0: associated
[15226.858436] wlan0: deauthenticating from 00:21:91:09:2b:0b by local choice (reason=3)
[15240.475733] wlan0: authenticate with 00:21:91:09:2b:0b
[15240.503471] wlan0: send auth to 00:21:91:09:2b:0b (try 1/3)
[15240.506127] wlan0: authenticated
[15240.507294] wlan0: associate with 00:21:91:09:2b:0b (try 1/3)
[15240.510595] wlan0: RX AssocResp from 00:21:91:09:2b:0b (capab=0x431 status=0 aid=3)
[15240.519167] wlan0: associated
``` 
[*]**Network Configuration**
```
  *-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 3e
       serial: 24:77:03:ad:2f:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-31-generic firmware=9.221.4.1 build 25532 ip=192.168.0.174 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:42 memory:e2d00000-e2d01fff
``` 
[*]**Scan for networks**
```
wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:09:2B:0B
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"JohnsonsHome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003064c05180
                    Extra: Last beacon: 1276532ms ago
                    IE: Unknown: 000C4A6F686E736F6E73486F6D65
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A0E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B071A0000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C330E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B07020000000F000000000000000000000000000000
``` 
[*]**Ubuntu Version**
```
Description:    Ubuntu 13.04
``` 
[*]**Kernel/Arch**
```
3.8.0-31-generic i686
``` 
[*][B]Restarting the network
[/B]```
That was amean trick ;)  After I typed that, my desktop crashed (a few windows still open, crash message from Ubuntu, and had to reboot.  The output message was something to the effect that this isn't the proper way to restart the networking system
``` 
[/LIST]

---

### Post by twjohnso on 2013-10-01
As a follow up, I was just having some issues browsing and tried to do a ping...
> *user@computername*:~$ ping facebook.com
PING facebook.com (173.252.110.27) 56(84) bytes of data.
**ping: sendmsg: No buffer space available**
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=1 ttl=79 time=**25991** ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=2 ttl=79 time=**27023** ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=3 ttl=79 time=**26574** ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=4 ttl=79 time=26362 ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=5 ttl=79 time=25438 ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=6 ttl=79 time=25079 ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=8 ttl=79 time=**123** ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=9 ttl=79 time=**90.6** ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=10 ttl=79 time=145 ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=11 ttl=79 time=89.6 ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=12 ttl=79 time=89.2 ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=13 ttl=79 time=88.6 ms
64 bytes from edge-star-shv-13-frc1.facebook.com (173.252.110.27): icmp_req=14 ttl=79 time=103 ms
^C
--- facebook.com ping statistics ---
14 packets transmitted, 13 received, 7% packet loss, time 41336ms
rtt min/avg/max/mdev = 88.691/12092.346/27023.077/12956.249 ms, pipe 7

...any ideas?

---

### Post by varunendra on 2013-10-03
> **twjohnso said:**
> 
**Scan for networks**
```

                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
```

Please try changing the Encryption algorithm from TKIP to AES in the router. TKIP is not as efficient and adds to poor performance problem sometimes. Reboot the router after making the change.

With (or without) the above change, please try this in Ubuntu -
```
echo "options iwlwifi 11n_disable=1 swcrypto=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
This will add two parameters to an existing conf file "iwlwifi.conf". After that, remove and reload the driver -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwldvm
```
Watch the output of the last command. It should show something like "insmod ..... iwlwifi .... nohwcrypt=1 swcrypto=1", among a few other lines. If you get any errors instead, or don't see that line, post back the error, or else confirm the output.

If the module is correctly loaded with the given two parameters, post back if it improved the speed.

---

### Post by twjohnso on 2013-10-03
I changed the encryption setting, didn't seem to necessarily resolve the problem (was going to try each one, rather than all at once so I know which solution, if any, works.)

Checking the scan again, I see the following info... which doesn't seem to say "AES", does it?
```
    IE: IEEE 802.11i/WPA2 Version 1
        Group Cipher : **[COLOR=#ff0000]CCMP[/COLOR]**
        Pairwise Ciphers (1) : CCMP
        Authentication Suites (1) : PSK
    IE: WPA Version 1
        Group Cipher : [COLOR=#ff0000]**CCMP**[/COLOR]
        Pairwise Ciphers (1) : CCMP
        Authentication Suites (1) : PSK
```

---

### Post by twjohnso on 2013-10-03
Output of cong/modprobe steps...
```
rmmod iwldvm
rmmod mac80211
rmmod iwlwifi
rmmod cfg80211
travisjohnson@tjohnson-mobl:~$ sudo modprobe -v iwldvm
insmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=1 swcrypto=1 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
```

Almost imediately, the signal indicator in my notifications bar wandered a bar higher (though still gravitates towards a bar just beyond the "dot" at the bottom).  However, running a speedtest against the same server as before and the results have nearly doubled!!  That alone is an improvement (thanks!)

But, am I understanding the commands provided correctly in that they disabled N for my connection (I guess that means my laptop is now using G?)

Is this a driver/Linux thing (as I have little issue in Windows)?

Thanks so much for your help thus far!  I'll wait to hear back if there are further steps to try (now that at least it seems I have a stable connection) before marking as solved.

---

### Post by varunendra on 2013-10-04
> **twjohnso said:**
> Checking the scan again, I see the following info... which doesn't seem to say "AES", does it?
```
    IE: IEEE 802.11i/**WPA2** Version 1
        Group Cipher : **[COLOR=#ff0000]CCMP[/COLOR]**
        Pairwise Ciphers (1) : CCMP
        Authentication Suites (1) : PSK
    IE: **[COLOR="#FF0000"]WPA[/COLOR]** Version 1
        Group Cipher : [COLOR=#ff0000]**CCMP**[/COLOR]
        Pairwise Ciphers (1) : CCMP
        Authentication Suites (1) : PSK
```
CCMP is good. It is [based on]("http://en.wikipedia.org/wiki/CCMP#Technical_details") AES standard and as such, is an implementation of it.

However, only now I noticed that you are also using WPA/WPA2 mixed mode, which is also something to be avoided when using Linux. I should have noticed that in the first sight. Anyway, please change it now to pure WPA2-PSK (AES or CCMP). Even if it doesn't help, keep it that way unless you are sure it is adversely affecting the connectivity/speed (you may try WPA as a test if you doubt the speed, but never WEP, never TKIP please).

> **twjohnso said:**
> But, am I understanding the commands provided correctly in that they disabled N for my connection (I guess that means my laptop is now using G?)
Yes, you got it right. The N-channel/speed is not necessarily a problem in Linux, but very often it is. Some people get flawless full N-channel speeds on Intel cards (as well as some others), while on the same cards and OS versions, other do not. It has been found to be causing trouble very often (indicating that linux drivers have to improvise a lot yet), and when it does, disabling it on the driver, even on the router sometimes too, helps definitively.

Experience of some senior members here suggests that the performance with the N-channel probably depends on the overall wifi setup in a place (whether all the involved devices - router, APs etc. are compatible to the new standards?). But we don't yet have a clear idea of how and when it works properly, and why it doesn't when it doesn't.

But now that you have experienced a clear gain in speed/stability, I think you should definitely try with N-channel enabled.

Change the encryption in the router as suggested above, reboot the router, then to remove the "11n_disable=1" parameter from the conf file -
```
sudo sed -i 's/11n_disable=1 //' /etc/modprobe.d/iwlwifi.conf
```

Then remove --> reload the driver again -
```
sudo modprobe -rv iwldvm
sudo modprobe -v iwldvm
```
Take a look at the output. You shouldn't see the "11n_disable=1" parameter this time. Does it further improve speed? If yes, does it remain stable for considerably long period?

---

### Post by twjohnso on 2013-10-10
Unfortunately I was having the problem again (seemingly randomly) over the last couple days.  Last night my speeds were down around 1mb/s (and the connection was barely usable.)

I've now made the latest changes you recommended...
```
user@host:~$ sudo sed -i 's/11n_disable=1 //' /etc/modprobe.d/iwlwifi.conf
[sudo] password for user: 
user@host:~$ sudo modprobe -rv iwldvm
rmmod iwldvm
rmmod mac80211
rmmod iwlwifi
rmmod cfg80211
user@hostl:~$ sudo modprobe -v iwldvm
insmod /lib/modules/3.8.0-31-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko swcrypto=1 
insmod /lib/modules/3.8.0-31-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko 
user@host:~$
```

I've also now set to WPA2/AES only (seems like this caused a problem with other clients, can't remember if it was my kids laptop, or the Wii).  We'll see how it goes.

---

### Post by varunendra on 2013-10-10
Well, the 11n_disable=1 option only limits the speed to under n speeds, doesn't affect it so adversely to make it go down to 1 Mb/s. So I don't think it may help with that. If it does, I'd call it a coincidence.

If the problem persists, make sure the power management is turned "off" in the output of iwconfig. If not, you may try -
```
sudo iwconfig wlan0 power off
```
..and see if it makes the connection any better.

There are a few other things we may try as and if required. But first make sure any external factors are not affecting the speeds (like bandwidth consumed by torrents running on another system, AP overload (although this is highly unlikely for a home network) etc.).

Oh, and the problem with WPA2/AES may occur if the client has 'remembered' the encryption type and trying the older one. Deleting the existing connection and recreating a new one is usually the easiest fix.

---

### Post by twjohnso on 2013-10-10
Understood, I'll keep an eye on it for a bit and report back.  Currently it is staying around 20-30 Mb/s (as reported by network manager).

---

