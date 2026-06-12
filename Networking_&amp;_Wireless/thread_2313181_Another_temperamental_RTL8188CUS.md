---
title: "Another temperamental RTL8188CUS"
date: 2016-02-10
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2016-02-10
Hi all,

Week old install of Xubuntu-core 15.10 on week old machine. Have been up every gumtree with this off and on over the last week and getting nowhere. Currently on ethernet cable which is not convenient. 

Wireless dongle shows up in lsusb as the problematic:

```
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
```

It connects, but to 'Wifi Networks', not my network name. I am running a static IP and it is using that IP and shows it is using the connection I set up when I look in 'Edit Connections'. 

The dongle can see only two other available networks, mine and another nearby (neighbour). When working well wireless shows about eight existing networks. When I disconnect and try to connect to my network name rather than 'Wifi Networks', it also connects, but nothing changes. I still see 'Wifi Networks' as the connection, not my network name.

Anyhow, the speeds on both are lousy and erratic (around 10-90ms and when it's working properly this little dongle gets between 1.* and 2.*ms) and eventually, randomly, it drops out completely. Also, when I check 'Connection Information' it shows speed as 'unknown' on both connections (almost always shows 72mbs when fully functional). 

I got this dongle flying fine in 14.04 using one of the fixes I found online. I can probably find it again, but enough to say that I tried that same fix first up (and then a bunch of other things) on 15.10 and it did nothing (and nor has anything else, although at one point I did manage to kill the wired connection but thankfully resurrected that within about ten minutes thanks to cherry pickin' some commands from one of chili555's support posts elsewhere). ;)

sudo lshw -C network shows:

```
 *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:13
       logical name: wlxe84e060dc5a4
       serial: e8:4e:06:0d:c5:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated
```

lsmod gives me:

```

bucky@UStudio:~$ lsmod
Module                  Size  Used by
cfg80211              548864  0
8192cu                532480  0
snd_hda_codec_hdmi     49152  1
nls_iso8859_1          16384  1
intel_rapl             20480  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             167936  0
kvm                   512000  1 kvm_intel
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
nvidia               8646656  35
serio_raw              16384  0
snd_ice1712            77824  2
snd_cs8427             16384  1 snd_ice1712
snd_hda_intel          36864  2
snd_i2c                16384  2 snd_ice1712,snd_cs8427
snd_ice17xx_ak4xxx     16384  1 snd_ice1712
snd_ak4xxx_adda        20480  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_hda_codec         135168  2 snd_hda_codec_hdmi,snd_hda_intel
snd_mpu401_uart        16384  1 snd_ice1712
joydev                 20480  0
snd_ac97_codec        131072  1 snd_ice1712
input_leds             16384  0
snd_hda_core           65536  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
ac97_bus               16384  1 snd_ac97_codec
snd_pcm               106496  6 snd_ice1712,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_mpu401_uart,snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
mei_me                 32768  0
drm                   356352  4 nvidia
snd                    81920  23 snd_ice1712,snd_ac97_codec,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_i2c,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_ak4xxx_adda,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_cs8427
mei                    98304  1 mei_me
soundcore              16384  1 snd
shpchp                 36864  0
8250_fintek            16384  0
wmi                    20480  0
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
acpi_pad               20480  0
tpm_infineon           20480  0
mac_hid                16384  0
industrialio           61440  2 acpi_als,kfifo_buf
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
uas                    24576  0
usb_storage            69632  1 uas
psmouse               126976  0
r8169                  81920  0
ahci                   36864  5
mii                    16384  1 r8169
libahci                32768  1 ahci
pinctrl_sunrisepoint    28672  0
video                  36864  0
i2c_hid                20480  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
hid                   118784  3 i2c_hid,hid_generic,usbhid
```

And wireless.info attached. If there's anything else required, just ask. I've researched a heap and done what I can, which is not a lot apart from blacklist a mod here and there and follow instructions, so now it's over to the community ... :)

---

### Post by Bucky Ball on 2016-02-11
Tried the following [from here]("http://askubuntu.com/questions/625987/does-tp-link-wn822n-work-on-ubuntu/625989#625989"):

```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192cu-dkms
```

Result:

```
E: Unable to locate package rtl8192cu-dkms
```

It's old. Pretty sure [this was the link that fixed it in 14.04 LTS]("http://askubuntu.com/questions/551522/netis-wf2120-wifi-adapter-drops-signal-within-seconds/551648#551648"), that I mentioned in last post, that hasn't worked in 15.10.

---

### Post by kurt18947 on 2016-02-11
How about this one? I used it with 16.04 gnome-shell and it worked.

[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)

I'm somewhat doubtful about the above fix because when I've used it in the past the default module was 'rtl8192cu'
The 'fixed' module was '8192cu', no rtl to start. You already have '8192cu' so I'm not certain. Install it and check the color of the resulting smoke?:p

---

### Post by Bucky Ball on 2016-02-11
Thanks for the input, kurt18047. Yes, tried that one already. Will try again a bit later, but no good last time. I'm going for anything at the moment, so who know? Might be different coloured smoke this time around.

---

### Post by Bucky Ball on 2016-02-13
* Just an update: I did run the routine in the link in post #3 from kurt again, rebooted, and it had completely killed the dongle. Shows up in lsusb, but that's it. 

Here's 'lshw -c network'

 ```
*-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:13
       logical name: wlxe84e060dc5a4
       serial: e8:4e:06:0d:c5:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated
```

iwconfig

```
wlxe84e060dc5a4  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Maybe the card is working now, hopefully someone can tell from this info, but I do see that it is disabled, not associated and the nickname is not my network's. Will begin further digging to rectify as I have a couple of hours for it.

* Major problem. [I followed this]("http://pkadetiloye.blogspot.com.au/2010/11/ubuntu-wireless-disabled-siocsifflags.html") as I was getting that error when inputting a command previously, and now there are options missing from network icon drop down and the problems I was having with the keyboard dropping out have come back. That is a major issue. Desperate now. 

(Below's the wireless.info again, the wireless dongle plugged in only, no cable.)

---

### Post by Bucky Ball on 2016-02-13
And just like that, bingo! Back to square one. I switched the machine off, rebooted, the keyboard works fine again and the wireless is back to square one. 

Plug dongle in, tells me it's connected to my network, shows in network drop-down as connected to 'Wifi Networks' with my network still available and 'Connection Information' gives all the correct information for my network connection, not 'Wifi-Networks', but 'unknown' connection speed. Truly puzzled, but at least I have a keyboard. 

I wouldn't be persisting with this except for the fact that it was working faultlessly on 14.04 LTS less than two weeks ago. I've been avoiding getting another but it might be my only option. Might install 16.04 and see if that has the same issues first.

* Ok. Think I'm getting somewhere, at least conceptually. There have been a few changes in 15.10, one being the way wireless is named. It is no longer wlan0 and all that. Wondering if the way it shows in the drop down has changed also which is confusing me. Another thing:

> Nickname:"<WIFI@REALTEK>"

Does this in anyway relate to why it is showing as 'Wifi-networks' when connected? Has there been wholesale changes to the wifi config that I'm unaware of and thus barking up wrong trees? Is it why my network still appears in the selection list even though I'm apparently connected to it and using it (confirmed in 'Edit Connections')? Apologies for what may seem like basic questions, but having come from 14.04 I've probably missed some changes.  

Anyhow, its working fine at the moment. Let's see if it lasts. If connection persists, I'm happy to go with it, regardless of what the network is called. :|

---

### Post by kurt18947 on 2016-02-13
True about wireless network naming and I've never seen a reason behind it. Were the people behind network manager bored and felt the need to stir something up? I hope the lil' critter will continue to behave for you.

---

### Post by Bucky Ball on 2016-02-13
No such luck. It has been complete chaos since running that command and I'm now back to using a wired keyboard and a wired connection. I have no idea what's going on. I have two wireless keyboards and neither work right from boot. 

Things improved after my last post. I switched the machine off again and when I switched back on, wireless came up and even showed connection bars in the wireless icon (which it didn't show previously, even when connected to 'wifi-networks'). The keyboard was starting to die just before I switched it off and had dinner, dying then coming back to life, but when I got back and booted up, nothing works. No USB wireless anything. Perhaps there is more to this than just a networking issue. External USB hard drive, camera and audio recorder all work AOK though. Just USB wireless.

This is an oddity.

---

### Post by sudodus on 2016-02-13
> Have been up every gumtree with this off and on over the last week and getting nowhere.

Have you been up the LTS gumtrees (14.04.1 and Xenial Xerus)?

---

### Post by chili555 on 2016-02-13
I'd fix this first:```
[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
[COLOR="#FF0000"]blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi[/COLOR]
blacklist rtl8187
```Since you are assumed to be an advanced user, I will assume a step-by-step isn't needed.

As well, I see two conf files that appear to be attempts to fix the issue. I doubt that they are needed and so I'd remove them:```
[/etc/modprobe.d/8192cu-disable-power-management.conf]
options 8192cu rtw_power_mgnt=0 rtw_enusbss=0
```And also:```
[/etc/modprobe.d/blacklist-native-rtl8192.conf]
install rtl8192cu /bin/false
install rtl8192c_common /bin/false
install rtlwifi /bin/false
```I believe the latter is needed if you install the after-market 8192cu and not if you use either the in-kernel (read:faulty) rtl8192cu or the github version. dmesg tells us you have:> [COLOR="#FF0000"]rtl8192cu[/COLOR] 1-13:1.0 wlxe84e060dc5a4: renamed from wlan0After these changes, reboot and let us hear the result.

---

### Post by Bucky Ball on 2016-02-13
Thanks for the input, chili555. Yes, that worked, to a degree. 

The wireless is up when I get to the desktop, bars showing, Connection Information is showing the right speed (72mb/s) but when I click the desktop icon, I only get four options: Enable networking, enable wifi, Connection Info, and Edit connections. No sign of any available networks. The only indications I get it is using the right network is that Edit Connections tells me it is connected to the correct network name 'now' and Connection Information tells me the connection is using the correct static IP. 

* After all that, I tried to post this and even though nothing had visibly changed, the connection had died. I plugged a cable in and it all came back to life immediately, and ... the drop down menu from the network icon has gone back to normal showing available networks (and that I am connected to my network, even though the connection is dead) and everything else that you'd normally expect there.

Just to clarify, I hashed out these lines in /etc/modprobe.d/blacklist.conf:

blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi

And also the lines in the two files you mentioned. Did you want me to delete those last two files completely?

---

### Post by chili555 on 2016-02-13
I don't think you need to remove the files entirely. Hashes are fine.

Are there any clues in the log?```
dmesg | grep -e rtl -e wlx
```Or else:```
cat /var/log/syslog | grep etwork | tail -n20
```As these may be lengthy, I recommend: [http://paste.ubuntu.com](http://paste.ubuntu.com)

Something is dropping out. I wonder if it is, in fact, power management? After a fresh boot, does power say on or off here?```
iwconfig
```For example, in my machine, it says:```
wlp3s0    IEEE 802.11bgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:2B:B0:DC:45:xx   
          Bit Rate=144.4 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          [COLOR="#FF0000"]Power Management:off[/COLOR]
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:1613   Missed beacon:0

```After your wireless conks out, does the state change?

---

### Post by Bucky Ball on 2016-02-13
Thanks again. Amazing what a good night's sleep can do, not that I've had one, but my machine must have. Switched on, wireless faultless, this time with network icon menu items present and correct (actually tells me I am connected to my network!) and connection bars in the icon, iwconfig tells me Power Management is 'off'. 

No, outputs not overly huge so here they are:

```
bucky@UStudio:~$ dmesg | grep -e rtl -e wlx
[    3.115667] rtl8192cu: Chip version 0x10
[    3.143721] rtl8192cu: MAC address: e8:4e:06:0d:c5:a4
[    3.143722] rtl8192cu: Board Type 0
[    3.143800] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[    3.143830] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[    3.145804] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    3.145960] usbcore: registered new interface driver rtl8192cu
[    3.148857] Error: Driver 'rtl8192cu' is already registered, aborting...
[    3.381478] Error: Driver 'rtl8192cu' is already registered, aborting...
[    3.414266] rtl8192cu 1-9:1.0 wlxe84e060dc5a4: renamed from wlan0
[    3.552229] IPv6: ADDRCONF(NETDEV_UP): wlxe84e060dc5a4: link is not ready
[    3.554849] rtl8192cu: MAC auto ON okay!
[    3.566221] rtl8192cu: Tx queue select: 0x05
[    3.943608] IPv6: ADDRCONF(NETDEV_UP): wlxe84e060dc5a4: link is not ready
[    4.013248] IPv6: ADDRCONF(NETDEV_UP): wlxe84e060dc5a4: link is not ready
[    4.854765] wlxe84e060dc5a4: authenticate with 10:0d:7f:de:92:ba
[    4.868839] wlxe84e060dc5a4: send auth to 10:0d:7f:de:92:ba (try 1/3)
[    4.892121] wlxe84e060dc5a4: authenticated
[    4.894933] wlxe84e060dc5a4: associate with 10:0d:7f:de:92:ba (try 1/3)
[    4.907414] wlxe84e060dc5a4: RX AssocResp from 10:0d:7f:de:92:ba (capab=0x411 status=0 aid=4)
[    4.908416] wlxe84e060dc5a4: associated
[    4.908433] IPv6: ADDRCONF(NETDEV_CHANGE): wlxe84e060dc5a4: link becomes ready
```

```
bucky@UStudio:~$ cat /var/log/syslog | grep etwork | tail -n20
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  (wlxe84e060dc5a4): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  (wlxe84e060dc5a4): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  (wlxe84e060dc5a4): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  (wlxe84e060dc5a4): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  NetworkManager state is now CONNECTED_LOCAL
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  Policy set 'Jetsons' (wlxe84e060dc5a4) as default for IPv4 routing and DNS.
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  DNS: starting dnsmasq...
Apr  2 12:18:31 UStudio NetworkManager[649]: <warn>  dnsmasq not available on the bus, can't update servers.
Apr  2 12:18:31 UStudio NetworkManager[649]: <error> [1459561711.884696] [dns-manager/nm-dns-dnsmasq.c:387] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr  2 12:18:31 UStudio NetworkManager[649]: <warn>  DNS: plugin dnsmasq update failed
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  Writing DNS information to /sbin/resolvconf
Apr  2 12:18:43 UStudio NetworkManager[649]: <info>  (wlxe84e060dc5a4): Activation: successful, device activated.
Apr  2 12:18:43 UStudio NetworkManager[649]: <info>  WiFi hardware radio set enabled
Apr  2 12:18:43 UStudio NetworkManager[649]: <info>  WWAN hardware radio set enabled
Apr  2 12:18:43 UStudio NetworkManager[649]: <info>  startup complete
Apr  2 12:18:43 UStudio systemd[1]: Starting Network Manager Script Dispatcher Service...
Apr  2 12:18:43 UStudio NetworkManager[649]: <warn>  dnsmasq appeared on DBus: :1.23
Apr  2 12:18:43 UStudio NetworkManager[649]: <info>  Writing DNS information to /sbin/resolvconf
Apr  2 12:18:43 UStudio systemd[1]: Started Network Manager Script Dispatcher Service.
```

And that is all she wrote. Could be the calm before the storm as only been online for five or ten minutes, but will be leaving the machine on for some hours so will report back and check power management if and/or when it dies. Progress at last at least. :)

---

### Post by Bucky Ball on 2016-02-13
* Update: Well, just let the machine sit for an hour. Came back, nothing has visibly changed at all. Still saying connected to my network and giving everything else accurately, but ... the wheel just keeps spinning. Plug in the ethernet cable again and bingo, back to life. Strange. iwconfig tells me power management is still off. End of dmesg shows I've plugged the ethernet cable in but nothing about wireless except the final message:

```
[    4.908433] IPv6: ADDRCONF(NETDEV_CHANGE): wlxe84e060dc5a4: link becomes ready
[ 5614.999318] r8169 0000:05:00.0 enp5s0: link up
[ 5614.999335] IPv6: ADDRCONF(NETDEV_CHANGE): enp5s0: link becomes ready
```

Just noticed something about the above. IPv6? I have wireless and wired set to 'Ignore' IPv6 in network manager setup. Don't know if that has anything to do with it.

Here's the outputs again with the wireless in the 'dead' state.

```
bucky@UStudio:~$ cat /var/log/syslog | grep etwork | tail -n20
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  (wlxe84e060dc5a4): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  (wlxe84e060dc5a4): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  (wlxe84e060dc5a4): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  (wlxe84e060dc5a4): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  NetworkManager state is now CONNECTED_LOCAL
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  Policy set 'Jetsons' (wlxe84e060dc5a4) as default for IPv4 routing and DNS.
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  DNS: starting dnsmasq...
Apr  2 12:18:31 UStudio NetworkManager[649]: <warn>  dnsmasq not available on the bus, can't update servers.
Apr  2 12:18:31 UStudio NetworkManager[649]: <error> [1459561711.884696] [dns-manager/nm-dns-dnsmasq.c:387] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr  2 12:18:31 UStudio NetworkManager[649]: <warn>  DNS: plugin dnsmasq update failed
Apr  2 12:18:31 UStudio NetworkManager[649]: <info>  Writing DNS information to /sbin/resolvconf
Apr  2 12:18:43 UStudio NetworkManager[649]: <info>  (wlxe84e060dc5a4): Activation: successful, device activated.
Apr  2 12:18:43 UStudio NetworkManager[649]: <info>  WiFi hardware radio set enabled
Apr  2 12:18:43 UStudio NetworkManager[649]: <info>  WWAN hardware radio set enabled
Apr  2 12:18:43 UStudio NetworkManager[649]: <info>  startup complete
Apr  2 12:18:43 UStudio systemd[1]: Starting Network Manager Script Dispatcher Service...
Apr  2 12:18:43 UStudio NetworkManager[649]: <warn>  dnsmasq appeared on DBus: :1.23
Apr  2 12:18:43 UStudio NetworkManager[649]: <info>  Writing DNS information to /sbin/resolvconf
Apr  2 12:18:43 UStudio systemd[1]: Started Network Manager Script Dispatcher Service.
```

---

### Post by chili555 on 2016-02-13
Most of the syslog deals with the ethernet, not wireless, because you plugged it in before you pulled the log. I'd love to see the wireless die out, pull the log and then plug in the ethernet to post it. > iwconfig tells me Power Management is 'off'.And after the wireless quits:> Strange. iwconfig tells me power management is still off.That seems to rule out power management as a contributor to the problem.

It seems that you've tried several driver versions. Which is in place now?```
modinfo rtl8192cu
```You might also get a clue as to the last version you installed from:```
history | less
```Generally, I'd favor this: [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)

It is a bit tricky if you aren't git savvy and if you'd prefer a step-by-step, I'll be happy to help, although I am now about to retire for the evening.

---

### Post by Bucky Ball on 2016-02-13
This is the last entry pertaining to installing wifi driver in 'history | less':

```
339  sudo apt-get install git linux-headers-generic build-essential dkms
  340  git clone https://github.com/pvaret/rtl8192cu-fixes.git
  341  sudo dkms add ./rtl8192cu-fixes
  342  sudo dkms install 8192cu/1.10
  343  sudo depmod -a
  344  sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
  345  sudo cp ./rtl8192cu-fixes/8192cu-disable-power-management.conf /etc/modpr
obe.d/
```

Just for good measure, the relevant bit of lsmod again:

```
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              733184  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              548864  2 mac80211,rtlwifi
```


The modinfo [is here]("http://paste.ubuntu.com/15051351/"), and from that output:

```
91     parm:           swenc:Set to 1 for software crypto (default 0)
```

Pretty sure I changed the swenc value along the way, not that I remember how (might have found that in one of your or Hadaka's old posts, chili55. :-k). 
___

(Back on wireless again, working faultlessly of course, and about to go out, but just noticed. Is this a typo? 
> cat /var/log/syslog | grep **etwork** | tail -n20

I'm presuming so and have a terminal window open with the command ready for wireless death and have changed to 'grep network'. Hope that's correct.

Also, here's a little slab of a ping. Overall excellent. Not exactly consistent but perhaps it's normal. 

```
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=1.97 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=1.89 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=2.80 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=2.28 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=**7.06 ms**
64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=2.85 ms
64 bytes from 192.168.0.1: icmp_seq=11 ttl=64 time=1.97 ms
64 bytes from 192.168.0.1: icmp_seq=12 ttl=64 time=1.92 ms
64 bytes from 192.168.0.1: icmp_seq=14 ttl=64 time=1.82 ms
64 bytes from 192.168.0.1: icmp_seq=15 ttl=64 time=1.87 ms
64 bytes from 192.168.0.1: icmp_seq=16 ttl=64 time=2.06 ms
64 bytes from 192.168.0.1: icmp_seq=17 ttl=64 time=**5.37 ms**
64 bytes from 192.168.0.1: icmp_seq=18 ttl=64 time=**21.7 ms**
64 bytes from 192.168.0.1: icmp_seq=19 ttl=64 time=1.86 ms
64 bytes from 192.168.0.1: icmp_seq=20 ttl=64 time=2.62 ms
64 bytes from 192.168.0.1: icmp_seq=21 ttl=64 time=1.98 ms
64 bytes from 192.168.0.1: icmp_seq=22 ttl=64 time=1.71 ms
64 bytes from 192.168.0.1: icmp_seq=23 ttl=64 time=2.25 ms
```

---

### Post by Bucky Ball on 2016-02-14
Ok. Wireless died, here's the syslog, and interesting.

```
bucky@UStudio:~$ cat /var/log/syslog | grep network | tail -n20
Apr  2 12:18:29 UStudio systemd[1]: Starting LSB: Raise network interfaces....
Apr  2 12:18:29 UStudio networking[570]: * Configuring network interfaces...
Apr  2 12:18:29 UStudio networking[570]: ...done.
Apr  2 12:18:29 UStudio systemd[1]: Started LSB: Raise network interfaces..
Apr  2 12:18:29 UStudio systemd[1]: Started Trigger resolvconf update for networkd DNS.
Apr  2 12:18:29 UStudio NetworkManager[649]: <info>        interface-parser: parsing file /etc/network/interfaces
Apr  2 12:18:29 UStudio NetworkManager[649]: <info>        interface-parser: finished parsing file /etc/network/interfaces
Apr  2 12:18:29 UStudio NetworkManager[649]: <info>  monitoring ifupdown state file '/run/network/ifstate'.
**Apr  2 12:18:31** UStudio NetworkManager[649]: <info>  (wlxe84e060dc5a4): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '*****'.
**Apr  2 15:25:48** UStudio systemd[1]: Starting Wait for all "auto" /etc/network/interfaces to be up for network-online.target...
Apr  2 15:25:48 UStudio systemd[1]: Started Wait for all "auto" /etc/network/interfaces to be up for network-online.target.
Apr  2 15:25:48 UStudio systemd[1]: Starting LSB: Raise network interfaces....
Apr  2 15:25:48 UStudio networking[564]: * Configuring network interfaces...
Apr  2 15:25:48 UStudio networking[564]: ...done.
Apr  2 15:25:48 UStudio systemd[1]: Started LSB: Raise network interfaces..
Apr  2 15:25:48 UStudio systemd[1]: Started Trigger resolvconf update for networkd DNS.
Apr  2 15:25:48 UStudio NetworkManager[651]: <info>        interface-parser: parsing file /etc/network/interfaces
Apr  2 15:25:48 UStudio NetworkManager[651]: <info>        interface-parser: finished parsing file /etc/network/interfaces
Apr  2 15:25:48 UStudio NetworkManager[651]: <info>  monitoring ifupdown state file '/run/network/ifstate'.
Apr  2 15:25:50 UStudio NetworkManager[651]: <info>  (wlxe84e060dc5a4): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '*****'.
```

'*****' is the blanked out correct network. Connected as expected. The last message, connected to wireless network, is confusing. It shows it is, but no ping response to the router, no connecting on any webpage. Just the spinning wheel of wait forever. Again, plug in ethernet, gets back to the page it was loading and loads it immediately.

I've bolded what I see as an anomaly. The wireless had been sitting there working quite fine for 17 minutes, then out of nowhere, I wasn't even in the room and computer not touched, the event at Apr  2 15:25:48 occurs. It decides to reconnect and runs through the previous connection routine (missing a few items), says it is connected, but it actually isn't. Just a very good impersonation which is only skin-deep. :-k ?

---

### Post by Bucky Ball on 2016-02-14
Per the link you provided, thanks. Not git savvy but [found this]("https://github.com/vrkansagara/rtlwifi_new/commit/8c5ab142e254a709df397d5d3121acc2d783d2d2"). :) At the top of that page it says this:

> How can you find <<YOUR WIRELESS DRIVER CODE>> using `lspci | grep Wireless`

I run that command and nothing, which is odd, as I'm posting from the wireless connection now. Consequently, no idea what to do at the two lines that ask for that info.  

I have a feeling I may have been down that path with rtlwifi-new, but perhaps not. Anything's worth a go. Maybe the dongle itself is faulty. Fun fact: A bit of ping and in bold where I plug the cable in to override wireless:

```
64 bytes from 192.168.0.1: icmp_seq=73 ttl=64 time=511 ms
64 bytes from 192.168.0.1: icmp_seq=75 ttl=64 time=17.9 ms
64 bytes from 192.168.0.1: icmp_seq=76 ttl=64 time=2.84 ms
64 bytes from 192.168.0.1: icmp_seq=77 ttl=64 time=4.30 ms
64 bytes from 192.168.0.1: icmp_seq=78 ttl=64 time=2.78 ms
64 bytes from 192.168.0.1: icmp_seq=79 ttl=64 time=1.88 ms
64 bytes from 192.168.0.1: icmp_seq=81 ttl=64 time=12.4 ms
64 bytes from 192.168.0.1: icmp_seq=82 ttl=64 time=6.31 ms
64 bytes from 192.168.0.1: icmp_seq=84 ttl=64 time=492 ms
[B]64 bytes from 192.168.0.1: icmp_seq=86 ttl=64 time=3.67 ms
64 bytes from 192.168.0.1: icmp_seq=87 ttl=64 time=0.448 ms[/B]
64 bytes from 192.168.0.1: icmp_seq=88 ttl=64 time=0.562 ms
64 bytes from 192.168.0.1: icmp_seq=89 ttl=64 time=0.613 ms
64 bytes from 192.168.0.1: icmp_seq=90 ttl=64 time=0.569 ms
64 bytes from 192.168.0.1: icmp_seq=91 ttl=64 time=0.580 ms
```

Well-behaved wireless doesn't get 0.5s, but generally 1.0 or around 2 is expected. Looks a bit ill. I have wired plugged in and the wireless is dropping out then connecting again randomly.

---

### Post by chili555 on 2016-02-14
> Starting Wait for all "auto" /etc/network/interfaces to be up for network-online.target...Whhuuutt??

Normally, the file /etc/network/interfaces should be sparse if Network Manager is doing the job for us. Let's check:```
sudo gedit /etc/network/interfaces
```Use nano or kate or leafpad if you don't have the text editor gedit. 

It ought to contain no more than:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```If it contains more, please hash the extra lines out.

Network Manager has a mechanism to use, or not, any listings in /etc/network/interfaces. Let's check and reset:```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```By default, it contains:```
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

```If yours contains otherwise, please correct, save and close the text editor.

Finally, your *history* shows the installation of two different drivers; 8192cu and rtl8192cu. That is why we found earlier that the driver loaded was also blacklisted!!

I recommend that we install the version I consider the latest and best. With a working internet connection, please do:```
git clone https://github.com/lwfinger/rtlwifi_new.git
```If the terminal reports that the file exists and is not empty, remove the old files:```
rm -rf rtlwifi_new
```Then continue:```
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install

```Reboot and let us hear your report.

---

### Post by Bucky Ball on 2016-02-15
Rebooting after 'make installing' and I can't log in. At the login screen the keyboard is dropping in and out or simply freezing, making it impossible to do anything. Or I type in the password and 'enter' does nothing. Then the mouse becomes visible but ineffective or invisible on the login screen. Tried rebooting numerous times to be greeted by the weirdest behaviour. Don't know what's going on there but it and uni commitments put a halt to any further investigations. 

Oh, well. The behaviour is probably coincidental and not to do with the wireless as there have been odd issues and I posted another thread about the keyboard probs awhile ago. 

Will get back to the 15.10 issues a bit later once I can actually log in to it. :|
____

***** Update**: and it's not good. 16.04 LTS had so far been faultless. I had barely touched it and only just spent twenty minutes giving it a spit and polish while posting the above. I forgot to mention that the wireless is exactly the same in 16.04 as in 15.10, so I tried the finger fix.

Wrong. It did the same. Crashed the install, but in a different way. I can log in, gets to a desktop fine, but as it's trying to connect and the  network icon's spinning, the icon freezes and so does everything else; keyboard, mouse, spinning. That's it. Unplug the wireless dongle, reboot, not an issue. Working desktop.

I'm now going to see if unplugging the dongle in 15.10 does the trick there and hope for a remedy. Thought it was coincidental in 15.10, but after this experience, don't think so, but peculiar. 

As I have mentioned, this is a brand new custom designed box with fairly new model hardware (which is why I didn't install 14.04 LTS, my preference) so it may be some obscure hardware quirk because it's not just the wireless that's been playing silly possums. Or maybe I'm missing a hardware driver other than for wireless. 
___

I know I have mentioned being on 16.04 LTS as well, but I have used that as an example in this case only and we should probably stick to fixing the 15.10 connection (dev version stuff doesn't belong here). ;)

---

### Post by Bucky Ball on 2016-02-15
Yep. If I boot 15.10 without the wireless dongle in, everything is as normal. Works fine. Except wireless, naturally. 

Went to /etc/modprobe.d/blacklist.conf and made it look like this:

```
# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
blacklist rtl8187
```

Now I can get in fine, wireless back to connected, but no signal bars, speed unknown, drops out whenever, and connected to 'wireless network'. But I can login. Phew. :)
___

PS: Hadaka wondered about this, and now, so do I:

```
bucky@UStudio:~$ grep '' /sys/module/rtl8192cu*/parameters/*
grep: /sys/module/rtl8192cu*/parameters/*: No such file or directory
```

I punched the same into 16.04 earlier by accident and it spat out something, one of the lines was swenc related.

---

### Post by chili555 on 2016-02-15
> Went to /etc/modprobe.d/blacklist.conf and made it look like this:

Code:

# Blacklist native RealTek 8188CUs drivers
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
blacklist rtl8187

Now I can get in fine, wireless back to connected, but no signal bars, speed unknown, drops out whenever, and connected to 'wireless network'. But I can login. Phew. I am stumped! If you blacklisted rtl8192cu, then what driver is actually driving the wireless? The alternative 8192cu? Or...??```
lsmod
```May I have a look at:```
sudo iwlist scan
```Just show me your network and obscure your MAC address something like this:```
Cell 03 - Address: [COLOR="#FF0000"]xx[/COLOR]:95:2A:A1:C0:[COLOR="#FF0000"]xx[/COLOR]
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"TC8715D53"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b7142a66bd
                    Extra: Last beacon: 168ms ago
                    IE: Unknown: 0009544338373135443533
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B0500001D0000
                    IE: Unknown: 2D1AAD1917FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD8C0050F204104A0001101044000102103B000103104700107EA198F1B8F81834138282D8BBC7DBB61021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 46057208010000
                    IE: Unknown: DD1E00904C0408BF0CB259820FEAFF0000EAFF0000C0050006000000C3020002

```I am wondering if there may be some things we can tweak in the router settings.

Also, I notice this in your wireless script:> Region: Australia/Adelaide (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set AU
```Of course, substitute your country code if not Australia. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=AU
```Proofread carefully, save and close the text editor.

---

### Post by Bucky Ball on 2016-02-16
This worked fine in 14.04 so don't know if it's router related (and eight other devices are  connecting without issue). I changed to 'REGDOMAIN=AU' and rebooted. In that file after reboot it is:

```
REGDOMAIN=AU
```

It was previously 'REGDOMAIN='. But when I run 'sudo iw reg get' I get this:

```
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)
```

I rebooted with the dongle and cable out, offline. Get to a desktop, all good. Plug the dongle in, icon starts to spin, then locks and so does the machine; mouse, keyboard. Have to hit the restart button on the box. :|

This is all with the </etc/modprobe.d/blacklist.conf> file looking like this:

```
# Blacklist native RealTek 8188CUs drivers
# blacklist rtl8192cu
# blacklist rtl8192c_common
# blacklist rtlwifi
blacklist rtl8187
```

---

### Post by chili555 on 2016-02-16
I am, frankly, stunned. Several of us, the crazed wireless cult, have suggested rtlwifi_new dozens of times and this is the first hard freeze I've ever heard about. I suggest two things. First, let it hard freeze and note the time. After you reboot, check here:```
cat /var/log/syslog | less
```Find what went wrong at the time you inserted the dongle and let's google it together and see if we can fix it.

May I see, from a fresh boot, with the dongle not inserted:```
lsmod
```[http://paste.ubuntu.com](http://paste.ubuntu.com)

If you uninstall rtlwifi_new, does the freeze remain?```
cd rtlwifi_new
sudo make uninstall
```And then reboot and insert the dongle. Does it freeze?

---

### Post by Hadaka on 2016-02-16
Hi Bucky Ball, please copy and paste..
```
sudo iw reg set AU
sudo sed -i 's/^REG.*=$/&AU/' /etc/default/crda
echo -e "iw reg set AU\nexit 0" | sudo tee /etc/rc.local
```
boot then do and post
to verify it set this time.
```
iw reg get
```
thanks.

*back to the cheif surgen.

---

### Post by Bucky Ball on 2016-02-17
Hadaka, after setting REG domain:
```

bucky@UStudio:~$ sudo iw reg set AU
[sudo] password for bucky: 
bucky@UStudio:~$ sudo sed -i 's/^REG.*=$/&AU/' /etc/default/crda
bucky@UStudio:~$ echo -e "iw reg set AU\nexit 0" | sudo tee /etc/rc.local
iw reg set AU
exit 0
bucky@UStudio:~$ iw reg get
country AU: DFS-UNSET
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 24), (0 ms), DFS
	(5490 - 5710 @ 160), (N/A, 24), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
```

Coincidentally glanced at this on the other screen:

```
Feb 17 19:23:17 UStudio kernel: [  181.016219] cfg80211: World regulatory domain updated:
Feb 17 19:23:17 UStudio kernel: [  181.016220] cfg80211:  DFS Master region: unset
Feb 17 19:23:17 UStudio kernel: [  181.016221] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb 17 19:23:17 UStudio kernel: [  181.016222] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.016223] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.016224] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.016225] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.016226] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Feb 17 19:23:17 UStudio kernel: [  181.016226] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Feb 17 19:23:17 UStudio kernel: [  181.016227] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.016228] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
```

... from the output prior to setting REG domain.
_____

Only just spat out the other stuff, chili555, and so far, interesting reading. There's a lot so will abridge and post shortly. Here's this though with dongle out and I just uninstalled that driver for now (I am avoiding that for the moment):

```
bucky@UStudio:~$ lsmod
Module                  Size  Used by
cfg80211              548864  0
snd_hda_codec_hdmi     49152  1
nls_iso8859_1          16384  1
intel_rapl             20480  0
nvidia               8646656  35
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             167936  0
kvm                   512000  1 kvm_intel
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  0
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
snd_ice1712            77824  2
snd_hda_intel          36864  2
snd_cs8427             16384  1 snd_ice1712
snd_hda_codec         135168  2 snd_hda_codec_hdmi,snd_hda_intel
snd_i2c                16384  2 snd_ice1712,snd_cs8427
snd_ice17xx_ak4xxx     16384  1 snd_ice1712
snd_ak4xxx_adda        20480  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_hda_core           65536  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_mpu401_uart        16384  1 snd_ice1712
snd_ac97_codec        131072  1 snd_ice1712
snd_hwdep              16384  1 snd_hda_codec
serio_raw              16384  0
ac97_bus               16384  1 snd_ac97_codec
snd_seq_midi           16384  0
joydev                 20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
input_leds             16384  0
snd_rawmidi            32768  2 snd_mpu401_uart,snd_seq_midi
snd_pcm               106496  6 snd_ice1712,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
drm                   356352  4 nvidia
snd                    81920  23 snd_ice1712,snd_ac97_codec,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_i2c,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_ak4xxx_adda,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_cs8427
mei_me                 32768  0
mei                    98304  1 mei_me
soundcore              16384  1 snd
shpchp                 36864  0
8250_fintek            16384  0
wmi                    20480  0
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
acpi_pad               20480  0
tpm_infineon           20480  0
mac_hid                16384  0
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
industrialio           61440  2 acpi_als,kfifo_buf
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
psmouse               126976  0
r8169                  81920  0
ahci                   36864  3
mii                    16384  1 r8169
libahci                32768  1 ahci
video                  36864  0
pinctrl_sunrisepoint    28672  0
i2c_hid                20480  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
hid                   118784  3 i2c_hid,hid_generic,usbhid
```

Looks like there's nothing there for the card, which is probably a good thing at this point. 

Before all this, I got in, booted the machine, no cable, plugged the dongle in, spin spin spin, faster spin as though about to connect, back to slower, keeps repeating this routine until I receive the a message about 'Disconnect Failure - Device disconnect failed' (I took a photo but it is not worth posting, rubbish, there was more info), and that is that, all froze. There's something new. So I rebooted with cable and ran the other command. Will post in separate post.

---

### Post by Bucky Ball on 2016-02-17
Here you go. The first part is the interesting bit. Plug in, wheel spins then the crash I described previously are the visuals that go with it.

I've included all of this, and there's a ton of it, and once crashed I have no option but to hit the restart button on the tower. 

```

Feb 17 19:23:15 UStudio kernel: [  179.695845] usb 1-13: new high-speed USB device number 3 using xhci_hcd
Feb 17 19:23:15 UStudio kernel: [  179.825970] usb 1-13: New USB device found, idVendor=0bda, idProduct=8176
Feb 17 19:23:15 UStudio kernel: [  179.825977] usb 1-13: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 17 19:23:15 UStudio kernel: [  179.825980] usb 1-13: Manufacturer: Realtek
Feb 17 19:23:15 UStudio kernel: [  179.825983] usb 1-13: SerialNumber: 00e04c000001
Feb 17 19:23:15 UStudio mtp-probe: checking bus 1, device 3: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-13"
Feb 17 19:23:15 UStudio mtp-probe: bus: 1, device: 3 was not an MTP device
Feb 17 19:23:17 UStudio kernel: [  181.016219] cfg80211: World regulatory domain updated:
Feb 17 19:23:17 UStudio kernel: [  181.016220] cfg80211:  DFS Master region: unset
Feb 17 19:23:17 UStudio kernel: [  181.016221] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb 17 19:23:17 UStudio kernel: [  181.016222] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.016223] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.016224] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.016225] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.016226] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Feb 17 19:23:17 UStudio kernel: [  181.016226] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Feb 17 19:23:17 UStudio kernel: [  181.016227] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.016228] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.023813] Chip version 0x10
Feb 17 19:23:17 UStudio kernel: [  181.051848] MAC address: e8:4e:06:0d:c5:a4
Feb 17 19:23:17 UStudio kernel: [  181.051850] Board Type 0
Feb 17 19:23:17 UStudio kernel: [  181.051927] rx_max_size 15360, rx_urb_num 8, in_ep 1
Feb 17 19:23:17 UStudio kernel: [  181.051928] rtlwifi: channel plan 0x0
Feb 17 19:23:17 UStudio kernel: [  181.051928] rtlwifi: bad channel plan 0x0
Feb 17 19:23:17 UStudio kernel: [  181.051929] rtlwifi: country code 11
Feb 17 19:23:17 UStudio kernel: [  181.051960] Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
Feb 17 19:23:17 UStudio NetworkManager[638]: <info>  (wlan0): using nl80211 for WiFi device control
Feb 17 19:23:17 UStudio NetworkManager[638]: <info>  (wlan0): driver supports Access Point (AP) mode
Feb 17 19:23:17 UStudio NetworkManager[638]: <info>  (wlan0): new 802.11 WiFi device (carrier: UNKNOWN, driver: 'rtl8192cu', ifindex: 3)
Feb 17 19:23:17 UStudio kernel: [  181.054242] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
Feb 17 19:23:17 UStudio kernel: [  181.054378] usbcore: registered new interface driver rtl8192cu
Feb 17 19:23:17 UStudio kernel: [  181.057923] Error: Driver 'rtl8192cu' is already registered, aborting...
Feb 17 19:23:17 UStudio kernel: [  181.087421] Error: Driver 'rtl8192cu' is already registered, aborting...
Feb 17 19:23:17 UStudio kernel: [  181.121586] rtl8192cu 1-13:1.0 wlxe84e060dc5a4: renamed from wlan0
Feb 17 19:23:17 UStudio NetworkManager[638]: <info>  rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.0/ieee80211/phy0/rfkill0) (driver rtl8192cu)
Feb 17 19:23:17 UStudio systemd[1]: Created slice system-systemd\x2drfkill.slice.
Feb 17 19:23:17 UStudio systemd[1]: Starting Load/Save RF Kill Switch Status of rfkill0...
Feb 17 19:23:17 UStudio systemd[1]: Started Load/Save RF Kill Switch Status of rfkill0.
Feb 17 19:23:17 UStudio NetworkManager[638]: <info>  (wlan0): interface index 3 renamed iface from 'wlan0' to 'wlxe84e060dc5a4'
Feb 17 19:23:17 UStudio NetworkManager[638]: <info>  devices added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.0/net/wlxe84e060dc5a4, iface: wlxe84e060dc5a4)
Feb 17 19:23:17 UStudio NetworkManager[638]: <info>  device added (path: /sys/devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.0/net/wlxe84e060dc5a4, iface: wlxe84e060dc5a4): no ifupdown configuration found.
Feb 17 19:23:17 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 17 19:23:17 UStudio kernel: [  181.143680] cfg80211: Regulatory domain changed to country: AU
Feb 17 19:23:17 UStudio kernel: [  181.143682] cfg80211:  DFS Master region: unset
Feb 17 19:23:17 UStudio kernel: [  181.143683] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Feb 17 19:23:17 UStudio kernel: [  181.143684] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.143685] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 1700 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.143686] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2400 mBm), (0 s)
Feb 17 19:23:17 UStudio kernel: [  181.143687] cfg80211:   (5490000 KHz - 5710000 KHz @ 160000 KHz), (N/A, 2400 mBm), (0 s)
Feb 17 19:23:17 UStudio kernel: [  181.143688] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
Feb 17 19:23:17 UStudio kernel: [  181.145347] IPv6: ADDRCONF(NETDEV_UP): wlxe84e060dc5a4: link is not ready
Feb 17 19:23:17 UStudio kernel: [  181.146828] MAC auto ON okay!
Feb 17 19:23:17 UStudio kernel: [  181.157495] Tx queue select: 0x05
Feb 17 19:23:17 UStudio kernel: [  181.534513] IPv6: ADDRCONF(NETDEV_UP): wlxe84e060dc5a4: link is not ready
Feb 17 19:23:17 UStudio wpa_supplicant[740]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Feb 17 19:23:17 UStudio wpa_supplicant[740]: dbus: Failed to construct signal
Feb 17 19:23:17 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): supplicant interface state: starting -> ready
Feb 17 19:23:17 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 17 19:23:17 UStudio NetworkManager[638]: <info>  Device 'wlxe84e060dc5a4' has no connection; scheduling activate_check in 0 seconds.
Feb 17 19:23:17 UStudio kernel: [  181.571727] IPv6: ADDRCONF(NETDEV_UP): wlxe84e060dc5a4: link is not ready
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): supplicant interface state: ready -> inactive
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  Auto-activating connection 'Jetsons'.
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): Activation: starting connection 'Jetsons' (cf6fccff-5511-4660-923d-af09789d0ee8)
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  NetworkManager state is now CONNECTING
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): Activation: (wifi) connection 'Jetsons' has security, and secrets exist.  No new secrets needed.
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  Config: added 'ssid' value 'Jetsons'
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  Config: added 'scan_ssid' value '1'
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  Config: added 'psk' value '<omitted>'
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  Config: set interface ap_scan to 1
Feb 17 19:23:18 UStudio wpa_supplicant[740]: wlxe84e060dc5a4: SME: Trying to authenticate with 10:0d:7f:de:92:ba (SSID='Jetsons' freq=2437 MHz)
Feb 17 19:23:18 UStudio kernel: [  182.417890] wlxe84e060dc5a4: authenticate with 10:0d:7f:de:92:ba
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): supplicant interface state: inactive -> authenticating
Feb 17 19:23:18 UStudio kernel: [  182.430251] wlxe84e060dc5a4: send auth to 10:0d:7f:de:92:ba (try 1/3)
Feb 17 19:23:18 UStudio wpa_supplicant[740]: wlxe84e060dc5a4: Trying to associate with 10:0d:7f:de:92:ba (SSID='Jetsons' freq=2437 MHz)
Feb 17 19:23:18 UStudio kernel: [  182.441147] wlxe84e060dc5a4: authenticated
Feb 17 19:23:18 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): supplicant interface state: authenticating -> associating
Feb 17 19:23:18 UStudio kernel: [  182.444474] wlxe84e060dc5a4: associate with 10:0d:7f:de:92:ba (try 1/3)
Feb 17 19:23:19 UStudio ModemManager[630]: <info>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:14.0/usb1/1-13': not supported by any plugin
Feb 17 19:23:19 UStudio colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 17 19:23:43 UStudio NetworkManager[638]: <warn>  (wlxe84e060dc5a4): Activation: (wifi) association took too long
Feb 17 19:23:43 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 17 19:23:43 UStudio NetworkManager[638]: <warn>  (wlxe84e060dc5a4): Activation: (wifi) asking for new secrets
Feb 17 19:23:43 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 17 19:23:43 UStudio NetworkManager[638]: <info>  (wlxe84e060dc5a4): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 17 19:24:05 UStudio systemd[1]: systemd-timesyncd.service: Watchdog timeout (limit 1min)!
Feb 17 19:24:18 UStudio kernel: [  182.454666] wlxe84e060dc5a4: RX AssocResp from 10:0d:7f:de:92:ba (capab=0x411 status=0 aid=4)
Feb 17 19:24:18 UStudio kernel: [  182.454674] rtl8192c_common:rtl92c_fill_h2c_cmd(): return H2C cmd because of Fw download fail!!!
Feb 17 19:24:18 UStudio kernel: [  182.454682] rtl8192cu:rtl92cu_set_hw_reg():<0-0> switch case not processed
Feb 17 19:24:18 UStudio kernel: [  182.454683] rtl8192c_common:rtl92c_fill_h2c_cmd(): return H2C cmd because of Fw download fail!!!
Feb 17 19:24:18 UStudio kernel: [  182.455113] BUG: unable to handle kernel NULL pointer dereference at           (null)
Feb 17 19:24:18 UStudio kernel: [  182.455116] IP: [<ffffffffc0e72e61>] rtl_cmd_send_packet+0xb1/0x100 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  182.455121] PGD 0 
Feb 17 19:24:18 UStudio kernel: [  182.455122] Oops: 0002 [#1] SMP 
Feb 17 19:24:18 UStudio kernel: [  182.455123] Modules linked in: arc4 rtl8192cu(OE) rtl_usb(OE) rtl8192c_common(OE) rtlwifi(OE) mac80211 cfg80211 snd_hda_codec_hdmi nls_iso8859_1 nvidia(POE) intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd joydev snd_ice1712 snd_hda_intel snd_cs8427 snd_i2c snd_hda_codec snd_ice17xx_ak4xxx snd_ak4xxx_adda snd_hda_core snd_mpu401_uart snd_hwdep snd_ac97_codec snd_seq_midi input_leds ac97_bus snd_seq_midi_event serio_raw snd_rawmidi snd_pcm snd_seq snd_seq_device snd_timer snd mei_me drm soundcore mei shpchp 8250_fintek wmi intel_lpss_acpi intel_lpss tpm_infineon acpi_pad acpi_als mac_hid kfifo_buf industrialio parport_pc ppdev lp parport autofs4 hid_generic usbhid psmouse r8169 ahci mii libahci video pinctrl_sunrisepoint i2c_hid pinctrl_intel hid
Feb 17 19:24:18 UStudio kernel: [  182.455143] CPU: 7 PID: 183 Comm: kworker/u16:4 Tainted: P           OE   4.2.0-27-generic #32-Ubuntu
Feb 17 19:24:18 UStudio kernel: [  182.455144] Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./H170-HD3-CF, BIOS F4 10/16/2015
Feb 17 19:24:18 UStudio kernel: [  182.455152] Workqueue: phy0 ieee80211_iface_work [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455153] task: ffff88045d772c40 ti: ffff88045d788000 task.ti: ffff88045d788000
Feb 17 19:24:18 UStudio kernel: [  182.455154] RIP: 0010:[<ffffffffc0e72e61>]  [<ffffffffc0e72e61>] rtl_cmd_send_packet+0xb1/0x100 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  182.455156] RSP: 0018:ffff88045d78b558  EFLAGS: 00010093
Feb 17 19:24:18 UStudio kernel: [  182.455157] RAX: 0000000000000000 RBX: ffff88045f5e1440 RCX: 0000000080000000
Feb 17 19:24:18 UStudio kernel: [  182.455157] RDX: 0000000000000080 RSI: 0000000000000292 RDI: ffff88045f5e14dc
Feb 17 19:24:18 UStudio kernel: [  182.455158] RBP: ffff88045d78b598 R08: ffff88045df29700 R09: 0000000000000080
Feb 17 19:24:18 UStudio kernel: [  182.455159] R10: 00000000000000c5 R11: 000000000000000d R12: ffff88045f5e06a0
Feb 17 19:24:18 UStudio kernel: [  182.455159] R13: ffff88045f5e14dc R14: ffff88045f5e8620 R15: ffff88045df29700
Feb 17 19:24:18 UStudio kernel: [  182.455160] FS:  0000000000000000(0000) GS:ffff8804765c0000(0000) knlGS:0000000000000000
Feb 17 19:24:18 UStudio kernel: [  182.455161] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 17 19:24:18 UStudio kernel: [  182.455161] CR2: 0000000000000000 CR3: 0000000002c0c000 CR4: 00000000003406e0
Feb 17 19:24:18 UStudio kernel: [  182.455162] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 17 19:24:18 UStudio kernel: [  182.455163] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
Feb 17 19:24:18 UStudio kernel: [  182.455163] Stack:
Feb 17 19:24:18 UStudio kernel: [  182.455164]  ffff88045d78b598 0000000000000292 ffff88045d78b578 ffff88045f5e1440
Feb 17 19:24:18 UStudio kernel: [  182.455165]  000000000000c004 ffffffffc0e94000 ffff88045df29700 00000000000000e8
Feb 17 19:24:18 UStudio kernel: [  182.455166]  ffff88045d78b5f8 ffffffffc0e8ae53 0000000162bed3b8 ffff88045f5e06a0
Feb 17 19:24:18 UStudio kernel: [  182.455167] Call Trace:
Feb 17 19:24:18 UStudio kernel: [  182.455170]  [<ffffffffc0e8ae53>] rtl92c_set_fw_rsvdpagepkt+0x2b3/0x6a0 [rtl8192c_common]
Feb 17 19:24:18 UStudio kernel: [  182.455172]  [<ffffffffc0e9ed67>] rtl92cu_set_hw_reg+0xdd7/0x1150 [rtl8192cu]
Feb 17 19:24:18 UStudio kernel: [  182.455174]  [<ffffffffc0e71be0>] rtl_op_bss_info_changed+0x130/0xa60 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  182.455178]  [<ffffffffc0506ebc>] ieee80211_bss_info_change_notify+0xcc/0x1a0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455185]  [<ffffffffc055678a>] ieee80211_assoc_success+0x6ea/0xb00 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455187]  [<ffffffff810d25de>] ? vprintk_emit+0x2de/0x530
Feb 17 19:24:18 UStudio kernel: [  182.455189]  [<ffffffff810d29b9>] ? vprintk_default+0x29/0x40
Feb 17 19:24:18 UStudio kernel: [  182.455190]  [<ffffffff817e8546>] ? printk+0x55/0x6b
Feb 17 19:24:18 UStudio kernel: [  182.455197]  [<ffffffffc0550614>] ? __sdata_info+0x64/0xb0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455203]  [<ffffffffc0556d06>] ieee80211_rx_mgmt_assoc_resp+0x166/0x440 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455209]  [<ffffffffc0557de9>] ieee80211_sta_rx_queued_mgmt+0x349/0x670 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455215]  [<ffffffffc05327fb>] ? ieee80211_xmit+0x9b/0xf0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455220]  [<ffffffffc0533c2b>] ? __ieee80211_tx_skb_tid_band+0x7b/0x80 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455225]  [<ffffffffc055351f>] ? ieee80211_send_assoc+0x45f/0xb50 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455227]  [<ffffffff810e59e8>] ? lock_timer_base.isra.22+0x58/0x80
Feb 17 19:24:18 UStudio kernel: [  182.455228]  [<ffffffff810e5c01>] ? internal_add_timer+0x71/0x80
Feb 17 19:24:18 UStudio kernel: [  182.455229]  [<ffffffff810aed09>] ? update_curr+0x119/0x150
Feb 17 19:24:18 UStudio kernel: [  182.455230]  [<ffffffff810b0cd4>] ? dequeue_entity+0x144/0x690
Feb 17 19:24:18 UStudio kernel: [  182.455236]  [<ffffffffc0558339>] ? ieee80211_sta_work+0x1e9/0x720 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455238]  [<ffffffff816d0780>] ? skb_release_data+0xd0/0xe0
Feb 17 19:24:18 UStudio kernel: [  182.455242]  [<ffffffffc051bbfa>] ieee80211_iface_work+0x32a/0x3f0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455245]  [<ffffffff810947ba>] process_one_work+0x1aa/0x440
Feb 17 19:24:18 UStudio kernel: [  182.455246]  [<ffffffff81094a9b>] worker_thread+0x4b/0x4c0
Feb 17 19:24:18 UStudio kernel: [  182.455247]  [<ffffffff81094a50>] ? process_one_work+0x440/0x440
Feb 17 19:24:18 UStudio kernel: [  182.455249]  [<ffffffff8109ae38>] kthread+0xd8/0xf0
Feb 17 19:24:18 UStudio kernel: [  182.455250]  [<ffffffff8109ad60>] ? kthread_create_on_node+0x1f0/0x1f0
Feb 17 19:24:18 UStudio kernel: [  182.455251]  [<ffffffff817f209f>] ret_from_fork+0x3f/0x70
Feb 17 19:24:18 UStudio kernel: [  182.455252]  [<ffffffff8109ad60>] ? kthread_create_on_node+0x1f0/0x1f0
Feb 17 19:24:18 UStudio kernel: [  182.455253] Code: 01 00 00 00 ba 01 00 00 00 4c 89 e7 48 8b 40 20 ff 90 e0 00 00 00 48 8b 83 e8 71 00 00 4d 89 37 4c 89 ef 48 8b 75 c8 49 89 47 08 <4c> 89 38 83 83 f0 71 00 00 01 4c 89 bb e8 71 00 00 e8 29 e8 97 
Feb 17 19:24:18 UStudio kernel: [  182.455265] RIP  [<ffffffffc0e72e61>] rtl_cmd_send_packet+0xb1/0x100 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  182.455267]  RSP <ffff88045d78b558>
Feb 17 19:24:18 UStudio kernel: [  182.455268] CR2: 0000000000000000
Feb 17 19:24:18 UStudio kernel: [  182.455269] ---[ end trace 9259f3b7b1cb0a96 ]---
Feb 17 19:24:18 UStudio kernel: [  182.455290] BUG: unable to handle kernel paging request at ffffffffffffffd8
Feb 17 19:24:18 UStudio kernel: [  182.455290] IP: [<ffffffff8109b460>] kthread_data+0x10/0x20
Feb 17 19:24:18 UStudio kernel: [  182.455292] PGD 2c0f067 PUD 2c11067 PMD 0 
Feb 17 19:24:18 UStudio kernel: [  182.455293] Oops: 0000 [#2] SMP 
Feb 17 19:24:18 UStudio kernel: [  182.455294] Modules linked in: arc4 rtl8192cu(OE) rtl_usb(OE) rtl8192c_common(OE) rtlwifi(OE) mac80211 cfg80211 snd_hda_codec_hdmi nls_iso8859_1 nvidia(POE) intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd joydev snd_ice1712 snd_hda_intel snd_cs8427 snd_i2c snd_hda_codec snd_ice17xx_ak4xxx snd_ak4xxx_adda snd_hda_core snd_mpu401_uart snd_hwdep snd_ac97_codec snd_seq_midi input_leds ac97_bus snd_seq_midi_event serio_raw snd_rawmidi snd_pcm snd_seq snd_seq_device snd_timer snd mei_me drm soundcore mei shpchp 8250_fintek wmi intel_lpss_acpi intel_lpss tpm_infineon acpi_pad acpi_als mac_hid kfifo_buf industrialio parport_pc ppdev lp parport autofs4 hid_generic usbhid psmouse r8169 ahci mii libahci video pinctrl_sunrisepoint i2c_hid pinctrl_intel hid
Feb 17 19:24:18 UStudio kernel: [  182.455326] CPU: 7 PID: 183 Comm: kworker/u16:4 Tainted: P      D    OE   4.2.0-27-generic #32-Ubuntu
Feb 17 19:24:18 UStudio kernel: [  182.455326] Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./H170-HD3-CF, BIOS F4 10/16/2015
Feb 17 19:24:18 UStudio kernel: [  182.455331] task: ffff88045d772c40 ti: ffff88045d788000 task.ti: ffff88045d788000
Feb 17 19:24:18 UStudio kernel: [  182.455332] RIP: 0010:[<ffffffff8109b460>]  [<ffffffff8109b460>] kthread_data+0x10/0x20
Feb 17 19:24:18 UStudio kernel: [  182.455346] RSP: 0018:ffff88045d78b208  EFLAGS: 00010096
Feb 17 19:24:18 UStudio kernel: [  182.455347] RAX: 0000000000000000 RBX: 0000000000000007 RCX: 0000000000000003
Feb 17 19:24:18 UStudio kernel: [  182.455347] RDX: 0000000000000003 RSI: 0000000000000007 RDI: ffff88045d772c40
Feb 17 19:24:18 UStudio kernel: [  182.455348] RBP: ffff88045d78b208 R08: 00000000ffffffff R09: 0000000000000000
Feb 17 19:24:18 UStudio kernel: [  182.455348] R10: ffff880085ad2c98 R11: 000000000000001a R12: 0000000000016640
Feb 17 19:24:18 UStudio kernel: [  182.455349] R13: ffff8804765d6640 R14: ffff88045d772c40 R15: 0000000000000007
Feb 17 19:24:18 UStudio kernel: [  182.455349] FS:  0000000000000000(0000) GS:ffff8804765c0000(0000) knlGS:0000000000000000
Feb 17 19:24:18 UStudio kernel: [  182.455350] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb 17 19:24:18 UStudio kernel: [  182.455351] CR2: 0000000000000028 CR3: 0000000002c0c000 CR4: 00000000003406e0
Feb 17 19:24:18 UStudio kernel: [  182.455351] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 17 19:24:18 UStudio kernel: [  182.455352] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
Feb 17 19:24:18 UStudio kernel: [  182.455352] Stack:
Feb 17 19:24:18 UStudio kernel: [  182.455353]  ffff88045d78b228 ffffffff81095ae5 ffff88045d78b228 ffff8804765d6640
Feb 17 19:24:18 UStudio kernel: [  182.455354]  ffff88045d78b278 ffffffff817ed8bd ffff880000000000 ffff88045d772c40
Feb 17 19:24:18 UStudio kernel: [  182.455355]  ffff88045d78b278 ffff88045d78c000 ffff88045d773308 ffff88045d78ae40
Feb 17 19:24:18 UStudio kernel: [  182.455356] Call Trace:
Feb 17 19:24:18 UStudio kernel: [  182.455358]  [<ffffffff81095ae5>] wq_worker_sleeping+0x15/0xa0
Feb 17 19:24:18 UStudio kernel: [  182.455360]  [<ffffffff817ed8bd>] __schedule+0x60d/0x950
Feb 17 19:24:18 UStudio kernel: [  182.455361]  [<ffffffff817edc37>] schedule+0x37/0x80
Feb 17 19:24:18 UStudio kernel: [  182.455362]  [<ffffffff8107e5f2>] do_exit+0x822/0xb10
Feb 17 19:24:18 UStudio kernel: [  182.455364]  [<ffffffff81017e35>] oops_end+0xa5/0xe0
Feb 17 19:24:18 UStudio kernel: [  182.455366]  [<ffffffff81067275>] no_context+0x135/0x380
Feb 17 19:24:18 UStudio kernel: [  182.455367]  [<ffffffff81067540>] __bad_area_nosemaphore+0x80/0x1f0
Feb 17 19:24:18 UStudio kernel: [  182.455368]  [<ffffffff810676c3>] bad_area_nosemaphore+0x13/0x20
Feb 17 19:24:18 UStudio kernel: [  182.455370]  [<ffffffff810679a7>] __do_page_fault+0xb7/0x400
Feb 17 19:24:18 UStudio kernel: [  182.455371]  [<ffffffff817ee8d7>] ? wait_for_completion_timeout+0xb7/0x140
Feb 17 19:24:18 UStudio kernel: [  182.455373]  [<ffffffff81067d12>] do_page_fault+0x22/0x30
Feb 17 19:24:18 UStudio kernel: [  182.455374]  [<ffffffff817f3bc8>] page_fault+0x28/0x30
Feb 17 19:24:18 UStudio kernel: [  182.455376]  [<ffffffffc0e72e61>] ? rtl_cmd_send_packet+0xb1/0x100 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  182.455377]  [<ffffffffc0e72e4c>] ? rtl_cmd_send_packet+0x9c/0x100 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  182.455379]  [<ffffffffc0e8ae53>] rtl92c_set_fw_rsvdpagepkt+0x2b3/0x6a0 [rtl8192c_common]
Feb 17 19:24:18 UStudio kernel: [  182.455381]  [<ffffffffc0e9ed67>] rtl92cu_set_hw_reg+0xdd7/0x1150 [rtl8192cu]
Feb 17 19:24:18 UStudio kernel: [  182.455383]  [<ffffffffc0e71be0>] rtl_op_bss_info_changed+0x130/0xa60 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  182.455386]  [<ffffffffc0506ebc>] ieee80211_bss_info_change_notify+0xcc/0x1a0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455392]  [<ffffffffc055678a>] ieee80211_assoc_success+0x6ea/0xb00 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455394]  [<ffffffff810d25de>] ? vprintk_emit+0x2de/0x530
Feb 17 19:24:18 UStudio kernel: [  182.455395]  [<ffffffff810d29b9>] ? vprintk_default+0x29/0x40
Feb 17 19:24:18 UStudio kernel: [  182.455396]  [<ffffffff817e8546>] ? printk+0x55/0x6b
Feb 17 19:24:18 UStudio kernel: [  182.455402]  [<ffffffffc0550614>] ? __sdata_info+0x64/0xb0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455407]  [<ffffffffc0556d06>] ieee80211_rx_mgmt_assoc_resp+0x166/0x440 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455413]  [<ffffffffc0557de9>] ieee80211_sta_rx_queued_mgmt+0x349/0x670 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455418]  [<ffffffffc05327fb>] ? ieee80211_xmit+0x9b/0xf0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455423]  [<ffffffffc0533c2b>] ? __ieee80211_tx_skb_tid_band+0x7b/0x80 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455428]  [<ffffffffc055351f>] ? ieee80211_send_assoc+0x45f/0xb50 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455429]  [<ffffffff810e59e8>] ? lock_timer_base.isra.22+0x58/0x80
Feb 17 19:24:18 UStudio kernel: [  182.455430]  [<ffffffff810e5c01>] ? internal_add_timer+0x71/0x80
Feb 17 19:24:18 UStudio kernel: [  182.455431]  [<ffffffff810aed09>] ? update_curr+0x119/0x150
Feb 17 19:24:18 UStudio kernel: [  182.455432]  [<ffffffff810b0cd4>] ? dequeue_entity+0x144/0x690
Feb 17 19:24:18 UStudio kernel: [  182.455437]  [<ffffffffc0558339>] ? ieee80211_sta_work+0x1e9/0x720 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455439]  [<ffffffff816d0780>] ? skb_release_data+0xd0/0xe0
Feb 17 19:24:18 UStudio kernel: [  182.455444]  [<ffffffffc051bbfa>] ieee80211_iface_work+0x32a/0x3f0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  182.455445]  [<ffffffff810947ba>] process_one_work+0x1aa/0x440
Feb 17 19:24:18 UStudio kernel: [  182.455447]  [<ffffffff81094a9b>] worker_thread+0x4b/0x4c0
Feb 17 19:24:18 UStudio kernel: [  182.455448]  [<ffffffff81094a50>] ? process_one_work+0x440/0x440
Feb 17 19:24:18 UStudio kernel: [  182.455449]  [<ffffffff8109ae38>] kthread+0xd8/0xf0
Feb 17 19:24:18 UStudio kernel: [  182.455450]  [<ffffffff8109ad60>] ? kthread_create_on_node+0x1f0/0x1f0
Feb 17 19:24:18 UStudio kernel: [  182.455451]  [<ffffffff817f209f>] ret_from_fork+0x3f/0x70
Feb 17 19:24:18 UStudio kernel: [  182.455452]  [<ffffffff8109ad60>] ? kthread_create_on_node+0x1f0/0x1f0
Feb 17 19:24:18 UStudio kernel: [  182.455453] Code: ff ff ff be 37 02 00 00 48 c7 c7 b0 ad a9 81 e8 97 06 fe ff e9 a6 fe ff ff 66 90 0f 1f 44 00 00 48 8b 87 08 05 00 00 55 48 89 e5 <48> 8b 40 d8 5d c3 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 44 00 00 
Feb 17 19:24:18 UStudio kernel: [  182.455465] RIP  [<ffffffff8109b460>] kthread_data+0x10/0x20
Feb 17 19:24:18 UStudio kernel: [  182.455466]  RSP <ffff88045d78b208>
Feb 17 19:24:18 UStudio kernel: [  182.455466] CR2: ffffffffffffffd8
Feb 17 19:24:18 UStudio kernel: [  182.455467] ---[ end trace 9259f3b7b1cb0a97 ]---
Feb 17 19:24:18 UStudio kernel: [  182.455468] Fixing recursive fault but reboot is needed!
Feb 17 19:24:18 UStudio kernel: [  207.015552] ------------[ cut here ]------------
Feb 17 19:24:18 UStudio kernel: [  207.015558] WARNING: CPU: 7 PID: 183 at /build/linux-NgsOGa/linux-4.2.0/kernel/watchdog.c:311 watchdog_overflow_callback+0x79/0xa0()
Feb 17 19:24:18 UStudio kernel: [  207.015559] Watchdog detected hard LOCKUP on cpu 7
Feb 17 19:24:18 UStudio kernel: [  207.015559] Modules linked in: arc4 rtl8192cu(OE) rtl_usb(OE) rtl8192c_common(OE) rtlwifi(OE) mac80211 cfg80211 snd_hda_codec_hdmi nls_iso8859_1 nvidia(POE) intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd joydev snd_ice1712 snd_hda_intel snd_cs8427 snd_i2c snd_hda_codec snd_ice17xx_ak4xxx snd_ak4xxx_adda snd_hda_core snd_mpu401_uart snd_hwdep snd_ac97_codec snd_seq_midi input_leds ac97_bus snd_seq_midi_event serio_raw snd_rawmidi snd_pcm snd_seq snd_seq_device snd_timer snd mei_me drm soundcore mei shpchp 8250_fintek wmi intel_lpss_acpi intel_lpss tpm_infineon acpi_pad acpi_als mac_hid kfifo_buf industrialio parport_pc ppdev lp parport autofs4 hid_generic usbhid psmouse r8169 ahci mii libahci video pinctrl_sunrisepoint i2c_hid pinctrl_intel hid
Feb 17 19:24:18 UStudio kernel: [  207.015588] CPU: 7 PID: 183 Comm: kworker/u16:4 Tainted: P      D    OE   4.2.0-27-generic #32-Ubuntu
Feb 17 19:24:18 UStudio kernel: [  207.015589] Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./H170-HD3-CF, BIOS F4 10/16/2015
Feb 17 19:24:18 UStudio kernel: [  207.015595]  0000000000000000 000000004667244e ffff8804765c5aa0 ffffffff817eae99
Feb 17 19:24:18 UStudio kernel: [  207.015596]  0000000000000000 ffff8804765c5af8 ffff8804765c5ae0 ffffffff8107b9c6
Feb 17 19:24:18 UStudio kernel: [  207.015597]  0000000000000000 ffff880463b90000 0000000000000000 ffff8804765c5c00
Feb 17 19:24:18 UStudio kernel: [  207.015599] Call Trace:
Feb 17 19:24:18 UStudio kernel: [  207.015599]  <NMI>  [<ffffffff817eae99>] dump_stack+0x45/0x57
Feb 17 19:24:18 UStudio kernel: [  207.015604]  [<ffffffff8107b9c6>] warn_slowpath_common+0x86/0xc0
Feb 17 19:24:18 UStudio kernel: [  207.015605]  [<ffffffff8107ba55>] warn_slowpath_fmt+0x55/0x70
Feb 17 19:24:18 UStudio kernel: [  207.015607]  [<ffffffff81132ff9>] watchdog_overflow_callback+0x79/0xa0
Feb 17 19:24:18 UStudio kernel: [  207.015609]  [<ffffffff81178310>] __perf_event_overflow+0x90/0x1c0
Feb 17 19:24:18 UStudio kernel: [  207.015610]  [<ffffffff81178ee4>] perf_event_overflow+0x14/0x20
Feb 17 19:24:18 UStudio kernel: [  207.015612]  [<ffffffff81034561>] intel_pmu_handle_irq+0x1e1/0x460
Feb 17 19:24:18 UStudio kernel: [  207.015614]  [<ffffffff8102ad36>] perf_event_nmi_handler+0x26/0x40
Feb 17 19:24:18 UStudio kernel: [  207.015616]  [<ffffffff810185f3>] nmi_handle+0x83/0x120
Feb 17 19:24:18 UStudio kernel: [  207.015617]  [<ffffffff81018bdd>] default_do_nmi+0xbd/0x100
Feb 17 19:24:18 UStudio kernel: [  207.015618]  [<ffffffff81018d0a>] do_nmi+0xea/0x140
Feb 17 19:24:18 UStudio kernel: [  207.015619]  [<ffffffff817f3f51>] end_repeat_nmi+0x1a/0x1e
Feb 17 19:24:18 UStudio kernel: [  207.015621]  [<ffffffff810c47fc>] ? native_queued_spin_lock_slowpath+0x15c/0x170
Feb 17 19:24:18 UStudio kernel: [  207.015623]  [<ffffffff810c47fc>] ? native_queued_spin_lock_slowpath+0x15c/0x170
Feb 17 19:24:18 UStudio kernel: [  207.015624]  [<ffffffff810c47fc>] ? native_queued_spin_lock_slowpath+0x15c/0x170
Feb 17 19:24:18 UStudio kernel: [  207.015624]  <<EOE>>  [<ffffffff817f19c8>] _raw_spin_lock_irq+0x28/0x30
Feb 17 19:24:18 UStudio kernel: [  207.015627]  [<ffffffff817ed363>] __schedule+0xb3/0x950
Feb 17 19:24:18 UStudio kernel: [  207.015628]  [<ffffffff817edc37>] schedule+0x37/0x80
Feb 17 19:24:18 UStudio kernel: [  207.015629]  [<ffffffff8107e6e0>] do_exit+0x910/0xb10
Feb 17 19:24:18 UStudio kernel: [  207.015630]  [<ffffffff81017e35>] oops_end+0xa5/0xe0
Feb 17 19:24:18 UStudio kernel: [  207.015632]  [<ffffffff81067275>] no_context+0x135/0x380
Feb 17 19:24:18 UStudio kernel: [  207.015634]  [<ffffffff81067540>] __bad_area_nosemaphore+0x80/0x1f0
Feb 17 19:24:18 UStudio kernel: [  207.015635]  [<ffffffff810676c3>] bad_area_nosemaphore+0x13/0x20
Feb 17 19:24:18 UStudio kernel: [  207.015637]  [<ffffffff810679a7>] __do_page_fault+0xb7/0x400
Feb 17 19:24:18 UStudio kernel: [  207.015638]  [<ffffffff810aed09>] ? update_curr+0x119/0x150
Feb 17 19:24:18 UStudio kernel: [  207.015639]  [<ffffffff81067d12>] do_page_fault+0x22/0x30
Feb 17 19:24:18 UStudio kernel: [  207.015640]  [<ffffffff817f3bc8>] page_fault+0x28/0x30
Feb 17 19:24:18 UStudio kernel: [  207.015642]  [<ffffffff8109b460>] ? kthread_data+0x10/0x20
Feb 17 19:24:18 UStudio kernel: [  207.015644]  [<ffffffff81095ae5>] wq_worker_sleeping+0x15/0xa0
Feb 17 19:24:18 UStudio kernel: [  207.015645]  [<ffffffff817ed8bd>] __schedule+0x60d/0x950
Feb 17 19:24:18 UStudio kernel: [  207.015647]  [<ffffffff817edc37>] schedule+0x37/0x80
Feb 17 19:24:18 UStudio kernel: [  207.015647]  [<ffffffff8107e5f2>] do_exit+0x822/0xb10
Feb 17 19:24:18 UStudio kernel: [  207.015648]  [<ffffffff81017e35>] oops_end+0xa5/0xe0
Feb 17 19:24:18 UStudio kernel: [  207.015650]  [<ffffffff81067275>] no_context+0x135/0x380
Feb 17 19:24:18 UStudio kernel: [  207.015651]  [<ffffffff81067540>] __bad_area_nosemaphore+0x80/0x1f0
Feb 17 19:24:18 UStudio kernel: [  207.015652]  [<ffffffff810676c3>] bad_area_nosemaphore+0x13/0x20
Feb 17 19:24:18 UStudio kernel: [  207.015654]  [<ffffffff810679a7>] __do_page_fault+0xb7/0x400
Feb 17 19:24:18 UStudio kernel: [  207.015655]  [<ffffffff817ee8d7>] ? wait_for_completion_timeout+0xb7/0x140
Feb 17 19:24:18 UStudio kernel: [  207.015656]  [<ffffffff81067d12>] do_page_fault+0x22/0x30
Feb 17 19:24:18 UStudio kernel: [  207.015657]  [<ffffffff817f3bc8>] page_fault+0x28/0x30
Feb 17 19:24:18 UStudio kernel: [  207.015661]  [<ffffffffc0e72e61>] ? rtl_cmd_send_packet+0xb1/0x100 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  207.015663]  [<ffffffffc0e72e4c>] ? rtl_cmd_send_packet+0x9c/0x100 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  207.015665]  [<ffffffffc0e8ae53>] rtl92c_set_fw_rsvdpagepkt+0x2b3/0x6a0 [rtl8192c_common]
Feb 17 19:24:18 UStudio kernel: [  207.015667]  [<ffffffffc0e9ed67>] rtl92cu_set_hw_reg+0xdd7/0x1150 [rtl8192cu]
Feb 17 19:24:18 UStudio kernel: [  207.015669]  [<ffffffffc0e71be0>] rtl_op_bss_info_changed+0x130/0xa60 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  207.015675]  [<ffffffffc0506ebc>] ieee80211_bss_info_change_notify+0xcc/0x1a0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  207.015682]  [<ffffffffc055678a>] ieee80211_assoc_success+0x6ea/0xb00 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  207.015684]  [<ffffffff810d25de>] ? vprintk_emit+0x2de/0x530
Feb 17 19:24:18 UStudio kernel: [  207.015685]  [<ffffffff810d29b9>] ? vprintk_default+0x29/0x40
Feb 17 19:24:18 UStudio kernel: [  207.015686]  [<ffffffff817e8546>] ? printk+0x55/0x6b
Feb 17 19:24:18 UStudio kernel: [  207.015693]  [<ffffffffc0550614>] ? __sdata_info+0x64/0xb0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  207.015699]  [<ffffffffc0556d06>] ieee80211_rx_mgmt_assoc_resp+0x166/0x440 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  207.015706]  [<ffffffffc0557de9>] ieee80211_sta_rx_queued_mgmt+0x349/0x670 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  207.015711]  [<ffffffffc05327fb>] ? ieee80211_xmit+0x9b/0xf0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  207.015717]  [<ffffffffc0533c2b>] ? __ieee80211_tx_skb_tid_band+0x7b/0x80 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  207.015723]  [<ffffffffc055351f>] ? ieee80211_send_assoc+0x45f/0xb50 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  207.015724]  [<ffffffff810e59e8>] ? lock_timer_base.isra.22+0x58/0x80
Feb 17 19:24:18 UStudio kernel: [  207.015725]  [<ffffffff810e5c01>] ? internal_add_timer+0x71/0x80
Feb 17 19:24:18 UStudio kernel: [  207.015726]  [<ffffffff810aed09>] ? update_curr+0x119/0x150
Feb 17 19:24:18 UStudio kernel: [  207.015727]  [<ffffffff810b0cd4>] ? dequeue_entity+0x144/0x690
Feb 17 19:24:18 UStudio kernel: [  207.015733]  [<ffffffffc0558339>] ? ieee80211_sta_work+0x1e9/0x720 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  207.015735]  [<ffffffff816d0780>] ? skb_release_data+0xd0/0xe0
Feb 17 19:24:18 UStudio kernel: [  207.015740]  [<ffffffffc051bbfa>] ieee80211_iface_work+0x32a/0x3f0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  207.015742]  [<ffffffff810947ba>] process_one_work+0x1aa/0x440
Feb 17 19:24:18 UStudio kernel: [  207.015743]  [<ffffffff81094a9b>] worker_thread+0x4b/0x4c0
Feb 17 19:24:18 UStudio kernel: [  207.015744]  [<ffffffff81094a50>] ? process_one_work+0x440/0x440
Feb 17 19:24:18 UStudio kernel: [  207.015745]  [<ffffffff8109ae38>] kthread+0xd8/0xf0
Feb 17 19:24:18 UStudio kernel: [  207.015747]  [<ffffffff8109ad60>] ? kthread_create_on_node+0x1f0/0x1f0
Feb 17 19:24:18 UStudio kernel: [  207.015748]  [<ffffffff817f209f>] ret_from_fork+0x3f/0x70
Feb 17 19:24:18 UStudio kernel: [  207.015749]  [<ffffffff8109ad60>] ? kthread_create_on_node+0x1f0/0x1f0
Feb 17 19:24:18 UStudio kernel: [  207.015750] ---[ end trace 9259f3b7b1cb0a98 ]---
Feb 17 19:24:18 UStudio kernel: [  207.081024] ------------[ cut here ]------------
Feb 17 19:24:18 UStudio kernel: [  207.081029] WARNING: CPU: 0 PID: 0 at /build/linux-NgsOGa/linux-4.2.0/kernel/watchdog.c:311 watchdog_overflow_callback+0x79/0xa0()
Feb 17 19:24:18 UStudio kernel: [  207.081030] Watchdog detected hard LOCKUP on cpu 0
Feb 17 19:24:18 UStudio kernel: [  207.081031] Modules linked in: arc4 rtl8192cu(OE) rtl_usb(OE) rtl8192c_common(OE) rtlwifi(OE) mac80211 cfg80211 snd_hda_codec_hdmi nls_iso8859_1 nvidia(POE) intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd joydev snd_ice1712 snd_hda_intel snd_cs8427 snd_i2c snd_hda_codec snd_ice17xx_ak4xxx snd_ak4xxx_adda snd_hda_core snd_mpu401_uart snd_hwdep snd_ac97_codec snd_seq_midi input_leds ac97_bus snd_seq_midi_event serio_raw snd_rawmidi snd_pcm snd_seq snd_seq_device snd_timer snd mei_me drm soundcore mei shpchp 8250_fintek wmi intel_lpss_acpi intel_lpss tpm_infineon acpi_pad acpi_als mac_hid kfifo_buf industrialio parport_pc ppdev lp parport autofs4 hid_generic usbhid psmouse r8169 ahci mii libahci video pinctrl_sunrisepoint i2c_hid pinctrl_intel hid
Feb 17 19:24:18 UStudio kernel: [  207.081059] CPU: 0 PID: 0 Comm: swapper/0 Tainted: P      D W  OE   4.2.0-27-generic #32-Ubuntu
Feb 17 19:24:18 UStudio kernel: [  207.081060] Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./H170-HD3-CF, BIOS F4 10/16/2015
Feb 17 19:24:18 UStudio kernel: [  207.081061]  0000000000000000 33250911d902ab35 ffff880476405aa0 ffffffff817eae99
Feb 17 19:24:18 UStudio kernel: [  207.081062]  0000000000000000 ffff880476405af8 ffff880476405ae0 ffffffff8107b9c6
Feb 17 19:24:18 UStudio kernel: [  207.081063]  0000000000000000 ffff880465814800 0000000000000000 ffff880476405c00
Feb 17 19:24:18 UStudio kernel: [  207.081065] Call Trace:
Feb 17 19:24:18 UStudio kernel: [  207.081065]  <NMI>  [<ffffffff817eae99>] dump_stack+0x45/0x57
Feb 17 19:24:18 UStudio kernel: [  207.081070]  [<ffffffff8107b9c6>] warn_slowpath_common+0x86/0xc0
Feb 17 19:24:18 UStudio kernel: [  207.081071]  [<ffffffff8107ba55>] warn_slowpath_fmt+0x55/0x70
Feb 17 19:24:18 UStudio kernel: [  207.081073]  [<ffffffff81132ff9>] watchdog_overflow_callback+0x79/0xa0
Feb 17 19:24:18 UStudio kernel: [  207.081075]  [<ffffffff81178310>] __perf_event_overflow+0x90/0x1c0
Feb 17 19:24:18 UStudio kernel: [  207.081076]  [<ffffffff81178ee4>] perf_event_overflow+0x14/0x20
Feb 17 19:24:18 UStudio kernel: [  207.081078]  [<ffffffff81034561>] intel_pmu_handle_irq+0x1e1/0x460
Feb 17 19:24:18 UStudio kernel: [  207.081081]  [<ffffffff8102ad36>] perf_event_nmi_handler+0x26/0x40
Feb 17 19:24:18 UStudio kernel: [  207.081082]  [<ffffffff810185f3>] nmi_handle+0x83/0x120
Feb 17 19:24:18 UStudio kernel: [  207.081083]  [<ffffffff81018b62>] default_do_nmi+0x42/0x100
Feb 17 19:24:18 UStudio kernel: [  207.081084]  [<ffffffff81018d0a>] do_nmi+0xea/0x140
Feb 17 19:24:18 UStudio kernel: [  207.081085]  [<ffffffff817f3f51>] end_repeat_nmi+0x1a/0x1e
Feb 17 19:24:18 UStudio kernel: [  207.081087]  [<ffffffff810c47b7>] ? native_queued_spin_lock_slowpath+0x117/0x170
Feb 17 19:24:18 UStudio kernel: [  207.081089]  [<ffffffff810c47b7>] ? native_queued_spin_lock_slowpath+0x117/0x170
Feb 17 19:24:18 UStudio kernel: [  207.081090]  [<ffffffff810c47b7>] ? native_queued_spin_lock_slowpath+0x117/0x170
Feb 17 19:24:18 UStudio kernel: [  207.081090]  <<EOE>>  <IRQ>  [<ffffffff817f19f1>] _raw_spin_lock+0x21/0x30
Feb 17 19:24:18 UStudio kernel: [  207.081093]  [<ffffffff810b990c>] sched_rt_period_timer+0xec/0x2d0
Feb 17 19:24:18 UStudio kernel: [  207.081094]  [<ffffffff810b9820>] ? put_prev_task_rt+0x40/0x40
Feb 17 19:24:18 UStudio kernel: [  207.081096]  [<ffffffff810e8603>] __hrtimer_run_queues+0xf3/0x220
Feb 17 19:24:18 UStudio kernel: [  207.081097]  [<ffffffff810e8d38>] hrtimer_interrupt+0xa8/0x1a0
Feb 17 19:24:18 UStudio kernel: [  207.081099]  [<ffffffff8104efac>] local_apic_timer_interrupt+0x3c/0x70
Feb 17 19:24:18 UStudio kernel: [  207.081100]  [<ffffffff817f4941>] smp_apic_timer_interrupt+0x41/0x60
Feb 17 19:24:18 UStudio kernel: [  207.081101]  [<ffffffff817f2adb>] apic_timer_interrupt+0x6b/0x70
Feb 17 19:24:18 UStudio kernel: [  207.081101]  <EOI>  [<ffffffff810e7ec4>] ? enqueue_hrtimer+0x44/0x80
Feb 17 19:24:18 UStudio kernel: [  207.081104]  [<ffffffff816879e0>] ? cpuidle_enter_state+0x130/0x270
Feb 17 19:24:18 UStudio kernel: [  207.081106]  [<ffffffff816879bb>] ? cpuidle_enter_state+0x10b/0x270
Feb 17 19:24:18 UStudio kernel: [  207.081107]  [<ffffffff81687b57>] cpuidle_enter+0x17/0x20
Feb 17 19:24:18 UStudio kernel: [  207.081108]  [<ffffffff810bdac2>] call_cpuidle+0x32/0x60
Feb 17 19:24:18 UStudio kernel: [  207.081109]  [<ffffffff81687b33>] ? cpuidle_select+0x13/0x20
Feb 17 19:24:18 UStudio kernel: [  207.081110]  [<ffffffff810bdd58>] cpu_startup_entry+0x268/0x320
Feb 17 19:24:18 UStudio kernel: [  207.081112]  [<ffffffff817df3fc>] rest_init+0x7c/0x80
Feb 17 19:24:18 UStudio kernel: [  207.081114]  [<ffffffff81d50025>] start_kernel+0x48b/0x4ac
Feb 17 19:24:18 UStudio kernel: [  207.081115]  [<ffffffff81d4f120>] ? early_idt_handler_array+0x120/0x120
Feb 17 19:24:18 UStudio kernel: [  207.081117]  [<ffffffff81d4f339>] x86_64_start_reservations+0x2a/0x2c
Feb 17 19:24:18 UStudio kernel: [  207.081118]  [<ffffffff81d4f485>] x86_64_start_kernel+0x14a/0x16d
Feb 17 19:24:18 UStudio kernel: [  207.081119] ---[ end trace 9259f3b7b1cb0a99 ]---
Feb 17 19:24:18 UStudio kernel: [  242.565869] INFO: rcu_sched detected stalls on CPUs/tasks: { 7} (detected by 2, t=15002 jiffies, g=1689, c=1688, q=0)
Feb 17 19:24:18 UStudio kernel: [  242.565873] Task dump for CPU 7:
Feb 17 19:24:18 UStudio kernel: [  242.565875] kworker/u16:4   D 0000000000000009     0   183      0 0x00000000
Feb 17 19:24:18 UStudio kernel: [  242.565882]  0000000000000046 ffff88045d78b4a8 0000000000000046 0000000000000000
Feb 17 19:24:18 UStudio kernel: [  242.565884]  ffff88045d78b348 ffffffff81017e35 0000000000000000 ffff88045d78b4a8
Feb 17 19:24:18 UStudio kernel: [  242.565885]  0000000000000009 0000000000000002 ffff88045d78b3b8 ffffffff81067275
Feb 17 19:24:18 UStudio kernel: [  242.565886] Call Trace:
Feb 17 19:24:18 UStudio kernel: [  242.565891]  [<ffffffff81017e35>] ? oops_end+0xa5/0xe0
Feb 17 19:24:18 UStudio kernel: [  242.565893]  [<ffffffff81067275>] ? no_context+0x135/0x380
Feb 17 19:24:18 UStudio kernel: [  242.565895]  [<ffffffff81067540>] ? __bad_area_nosemaphore+0x80/0x1f0
Feb 17 19:24:18 UStudio kernel: [  242.565896]  [<ffffffff810676c3>] ? bad_area_nosemaphore+0x13/0x20
Feb 17 19:24:18 UStudio kernel: [  242.565898]  [<ffffffff810679a7>] ? __do_page_fault+0xb7/0x400
Feb 17 19:24:18 UStudio kernel: [  242.565900]  [<ffffffff817ee8d7>] ? wait_for_completion_timeout+0xb7/0x140
Feb 17 19:24:18 UStudio kernel: [  242.565902]  [<ffffffff81067d12>] ? do_page_fault+0x22/0x30
Feb 17 19:24:18 UStudio kernel: [  242.565903]  [<ffffffff817f3bc8>] ? page_fault+0x28/0x30
Feb 17 19:24:18 UStudio kernel: [  242.565907]  [<ffffffffc0e72e61>] ? rtl_cmd_send_packet+0xb1/0x100 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  242.565909]  [<ffffffffc0e72e4c>] ? rtl_cmd_send_packet+0x9c/0x100 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  242.565912]  [<ffffffffc0e8ae53>] ? rtl92c_set_fw_rsvdpagepkt+0x2b3/0x6a0 [rtl8192c_common]
Feb 17 19:24:18 UStudio kernel: [  242.565914]  [<ffffffffc0e9ed67>] ? rtl92cu_set_hw_reg+0xdd7/0x1150 [rtl8192cu]
Feb 17 19:24:18 UStudio kernel: [  242.565916]  [<ffffffffc0e71be0>] ? rtl_op_bss_info_changed+0x130/0xa60 [rtlwifi]
Feb 17 19:24:18 UStudio kernel: [  242.565922]  [<ffffffffc0506ebc>] ? ieee80211_bss_info_change_notify+0xcc/0x1a0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  242.565931]  [<ffffffffc055678a>] ? ieee80211_assoc_success+0x6ea/0xb00 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  242.565933]  [<ffffffff810d25de>] ? vprintk_emit+0x2de/0x530
Feb 17 19:24:18 UStudio kernel: [  242.565934]  [<ffffffff810d29b9>] ? vprintk_default+0x29/0x40
Feb 17 19:24:18 UStudio kernel: [  242.565935]  [<ffffffff817e8546>] ? printk+0x55/0x6b
Feb 17 19:24:18 UStudio kernel: [  242.565942]  [<ffffffffc0550614>] ? __sdata_info+0x64/0xb0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  242.565949]  [<ffffffffc0556d06>] ? ieee80211_rx_mgmt_assoc_resp+0x166/0x440 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  242.565957]  [<ffffffffc0557de9>] ? ieee80211_sta_rx_queued_mgmt+0x349/0x670 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  242.565962]  [<ffffffffc05327fb>] ? ieee80211_xmit+0x9b/0xf0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  242.565968]  [<ffffffffc0533c2b>] ? __ieee80211_tx_skb_tid_band+0x7b/0x80 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  242.565974]  [<ffffffffc055351f>] ? ieee80211_send_assoc+0x45f/0xb50 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  242.565976]  [<ffffffff810e59e8>] ? lock_timer_base.isra.22+0x58/0x80
Feb 17 19:24:18 UStudio kernel: [  242.565977]  [<ffffffff810e5c01>] ? internal_add_timer+0x71/0x80
Feb 17 19:24:18 UStudio kernel: [  242.565978]  [<ffffffff810aed09>] ? update_curr+0x119/0x150
Feb 17 19:24:18 UStudio kernel: [  242.565979]  [<ffffffff810b0cd4>] ? dequeue_entity+0x144/0x690
Feb 17 19:24:18 UStudio kernel: [  242.565986]  [<ffffffffc0558339>] ? ieee80211_sta_work+0x1e9/0x720 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  242.565988]  [<ffffffff816d0780>] ? skb_release_data+0xd0/0xe0
Feb 17 19:24:18 UStudio kernel: [  242.565993]  [<ffffffffc051bbfa>] ? ieee80211_iface_work+0x32a/0x3f0 [mac80211]
Feb 17 19:24:18 UStudio kernel: [  242.565995]  [<ffffffff810947ba>] ? process_one_work+0x1aa/0x440
Feb 17 19:24:18 UStudio kernel: [  242.565997]  [<ffffffff81094a9b>] ? worker_thread+0x4b/0x4c0
Feb 17 19:24:18 UStudio kernel: [  242.565998]  [<ffffffff81094a50>] ? process_one_work+0x440/0x440
Feb 17 19:24:18 UStudio kernel: [  242.565999]  [<ffffffff8109ae38>] ? kthread+0xd8/0xf0
Feb 17 19:24:18 UStudio kernel: [  242.566001]  [<ffffffff8109ad60>] ? kthread_create_on_node+0x1f0/0x1f0
Feb 17 19:24:18 UStudio kernel: [  242.566002]  [<ffffffff817f209f>] ? ret_from_fork+0x3f/0x70
Feb 17 19:24:18 UStudio kernel: [  242.566003]  [<ffffffff8109ad60>] ? kthread_create_on_node+0x1f0/0x1f0
Feb 17 19:25:18 UStudio anacron[637]: Job `cron.daily' started
Feb 17 19:25:19 UStudio kernel: [  303.270880] usb 1-13: USB disconnect, device number 3
```

PS: With driver removed, I unplugged wired connection, plugged in dongle, popped straight up, connection bars are in the icon and connected to the correct network automatically, static IP being used. Pings are fine with the occasional not fine so still a bit erratic and I'll wait and see if it drops out. Here's this. 

```
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:13
       logical name: wlxe84e060dc5a4
       serial: e8:4e:06:0d:c5:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=4.2.0-27-generic firmware=N/A ip=192.168.0.112 link=yes multicast=yes wireless=IEEE 802.11bgn
```

```
wlxe84e060dc5a4  IEEE 802.11bgn  ESSID:"Jetsons"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 10:0D:7F:DE:92:BA   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0
```

```
bucky@UStudio:~$ lsmod
Module                  Size  Used by
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
arc4                   16384  2
rtl8192cu              69632  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              733184  3 rtl_usb,rtlwifi,rtl8192cu
uas                    24576  0
usb_storage            69632  2 uas
cfg80211              548864  2 mac80211,rtlwifi
snd_hda_codec_hdmi     49152  1
nls_iso8859_1          16384  2
intel_rapl             20480  0
nvidia               8646656  35
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             167936  0
kvm                   512000  1 kvm_intel
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
aesni_intel           167936  2
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  2 aesni_intel,ablk_helper
snd_ice1712            77824  2
snd_hda_intel          36864  2
snd_cs8427             16384  1 snd_ice1712
snd_hda_codec         135168  2 snd_hda_codec_hdmi,snd_hda_intel
snd_i2c                16384  2 snd_ice1712,snd_cs8427
snd_ice17xx_ak4xxx     16384  1 snd_ice1712
snd_ak4xxx_adda        20480  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_hda_core           65536  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_mpu401_uart        16384  1 snd_ice1712
snd_ac97_codec        131072  1 snd_ice1712
snd_hwdep              16384  1 snd_hda_codec
serio_raw              16384  0
ac97_bus               16384  1 snd_ac97_codec
snd_seq_midi           16384  0
joydev                 20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
input_leds             16384  0
snd_rawmidi            32768  2 snd_mpu401_uart,snd_seq_midi
snd_pcm               106496  6 snd_ice1712,snd_ac97_codec,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
drm                   356352  4 nvidia
snd                    81920  23 snd_ice1712,snd_ac97_codec,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_i2c,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_ak4xxx_adda,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_cs8427
mei_me                 32768  0
mei                    98304  1 mei_me
soundcore              16384  1 snd
shpchp                 36864  0
8250_fintek            16384  0
wmi                    20480  0
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
acpi_pad               20480  0
tpm_infineon           20480  0
mac_hid                16384  0
acpi_als               16384  0
kfifo_buf              16384  1 acpi_als
industrialio           61440  2 acpi_als,kfifo_buf
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
psmouse               126976  0
r8169                  81920  0
ahci                   36864  3
mii                    16384  1 r8169
libahci                32768  1 ahci
video                  36864  0
pinctrl_sunrisepoint    28672  0
i2c_hid                20480  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
hid
```

I did use one of your previous posts to install rtlwifi-new in the first place from memory so I'm as suprised as you are at the odd reaction. On all my trawling about this I've never seen a total freeze like this as a consequence of any attempt at fixage. :-k

---

### Post by Bucky Ball on 2016-02-17
I just power cycled the router and I'm now getting this from a ping:

```
64 bytes from 192.168.0.1: icmp_seq=910 ttl=64 time=1.35 ms
64 bytes from 192.168.0.1: icmp_seq=911 ttl=64 time=2.26 ms
64 bytes from 192.168.0.1: icmp_seq=912 ttl=64 time=1.53 ms
64 bytes from 192.168.0.1: icmp_seq=913 ttl=64 time=1.46 ms
64 bytes from 192.168.0.1: icmp_seq=914 ttl=64 time=1.56 ms
64 bytes from 192.168.0.1: icmp_seq=915 ttl=64 time=1.46 ms
64 bytes from 192.168.0.1: icmp_seq=916 ttl=64 time=1.41 ms
64 bytes from 192.168.0.1: icmp_seq=917 ttl=64 time=1.89 ms
64 bytes from 192.168.0.1: icmp_seq=918 ttl=64 time=1.46 ms
64 bytes from 192.168.0.1: icmp_seq=919 ttl=64 time=1.67 ms
64 bytes from 192.168.0.1: icmp_seq=920 ttl=64 time=1.47 ms
64 bytes from 192.168.0.1: icmp_seq=921 ttl=64 time=4.37 ms
64 bytes from 192.168.0.1: icmp_seq=922 ttl=64 time=1.39 ms
64 bytes from 192.168.0.1: icmp_seq=923 ttl=64 time=1.56 ms
64 bytes from 192.168.0.1: icmp_seq=924 ttl=64 time=1.58 ms
64 bytes from 192.168.0.1: icmp_seq=925 ttl=64 time=1.61 ms
64 bytes from 192.168.0.1: icmp_seq=926 ttl=64 time=1.49 ms
64 bytes from 192.168.0.1: icmp_seq=927 ttl=64 time=1.57 ms
64 bytes from 192.168.0.1: icmp_seq=928 ttl=64 time=1.46 ms
64 bytes from 192.168.0.1: icmp_seq=929 ttl=64 time=2.76 ms
64 bytes from 192.168.0.1: icmp_seq=930 ttl=64 time=1.55 ms
64 bytes from 192.168.0.1: icmp_seq=931 ttl=64 time=1.49 ms
64 bytes from 192.168.0.1: icmp_seq=932 ttl=64 time=2.14 ms
64 bytes from 192.168.0.1: icmp_seq=933 ttl=64 time=1.40 ms
64 bytes from 192.168.0.1: icmp_seq=934 ttl=64 time=1.62 ms
64 bytes from 192.168.0.1: icmp_seq=935 ttl=64 time=1.84 ms
64 bytes from 192.168.0.1: icmp_seq=936 ttl=64 time=1.65 ms
64 bytes from 192.168.0.1: icmp_seq=937 ttl=64 time=1.56 ms
64 bytes from 192.168.0.1: icmp_seq=938 ttl=64 time=1.82 ms
64 bytes from 192.168.0.1: icmp_seq=939 ttl=64 time=1.51 ms
64 bytes from 192.168.0.1: icmp_seq=940 ttl=64 time=3.09 ms
64 bytes from 192.168.0.1: icmp_seq=941 ttl=64 time=2.19 ms
64 bytes from 192.168.0.1: icmp_seq=942 ttl=64 time=1.62 ms
64 bytes from 192.168.0.1: icmp_seq=943 ttl=64 time=1.66 ms
64 bytes from 192.168.0.1: icmp_seq=944 ttl=64 time=3.39 ms
64 bytes from 192.168.0.1: icmp_seq=945 ttl=64 time=1.66 ms
64 bytes from 192.168.0.1: icmp_seq=946 ttl=64 time=1.85 ms
```

Happy enough. If it dies completely again, I'll advise, but looking promising for now. Might have hit the right combination.

---

### Post by Bucky Ball on 2016-02-17
Ok, dropping in and out again, but once it drops out the first time, it then says it's connected, but it's not. For a pastebin of the relevant part of cat /var/log/syslog | less [see here]("http://pastebin.com/wSr47pYr"). It drop out and reconnected straight away at 23:29 then again at 23:40. I wasn't using the net, I was typing on the other screen so I could observe the messages as they happened and see what happened. 

I tried to post this with wireless apparently connected at about 11:59 but the wheels kept spinning on any website. Cable in, up they come.

I'm almost ready to  go buy another and mail this one to you guys (happy to) so you can experiment, but not having an identical setup to me, probably not much point. You may plug it and works fine.

 chili555, I noticed on another thread you said you had the TP-Link 722. That is about the only one I can't get! But I can get just about any other TP-Link. [Any suggestions from this lot]("http://www.msy.com.au/saonline/182-wireless") from your good self or Hadaka?

---

### Post by chili555 on 2016-02-17
I remain both stunned and stumped. I see this, which is encouraging:> [14960.073087] cfg80211: Regulatory domain changed to country: AUSo, the crda setting does take place. A careful comparison of the available frequencies shows differences between the UNSET and AU setting. I assume your router was purchased in AU and so the best match is to get your wireless device to use the same frequency arrangement.

Next, I can't tell you how much I hate this:> wlxe84e060dc5a4: WPA: Key negotiation completed with 10:0d:7f:de:92:ba [PTK=CCMP GTK=[COLOR="#FF0000"]TKIP[/COLOR]]If you have a setting in the router that is not an automatic CCMP (also known as AES) or TKIP selection, I suggest you select CCMP/AES only. In my experience, many Linux drivers do not work well, if at all with TKIP and, moreover, stumble when faced with an auto-select setting. I suspect that our routers are switching about to find the most noise-free, stable and fastest encryption, channel, bandwidth, et al settings and I think some driver/hardware combinations lose track and drop out.

I also see this and I wonder if it suggests that the hardware is defective:> Feb 17 23:29:28 UStudio NetworkManager[663]: <info>  (wlxe84e060dc5a4): device state change: activated -> [COLOR="#FF0000"]failed (reason 'ssid-not-found')[/COLOR] [100 120 53]
Feb 17 23:29:28 UStudio NetworkManager[663]: <info>  NetworkManager state is now CONNECTED_LOCAL
Feb 17 23:29:28 UStudio NetworkManager[663]: <info>  NetworkManager state is now DISCONNECTED
Feb 17 23:29:28 UStudio NetworkManager[663]: <info>  Connection 'Jetsons' failed to autoconnect; 4 tries left
Feb 17 23:29:28 UStudio NetworkManager[663]: <warn>  (wlxe84e060dc5a4): Activation: failed for connection 'Jetsons'
Feb 17 23:29:28 UStudio dbus[633]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Feb 17 23:29:28 UStudio NetworkManager[663]: <info>  (wlxe84e060dc5a4): [COLOR="#FF0000"]device state change: failed -> disconnected [/COLOR](reason 'none') [120 30 0]I wonder if this means that the device saw the SSID and, a few minutes later, did not. Or, perhaps the router decided to auto-select some setting and the wireless device lost track.

We might try bumping up the time that it takes to disconnect upon a lost beacon and see if it helps.```
sudo -i
echo "options mac80211 probe_wait_ms=3000"  >  /etc/modprobe.d/mac80211.conf
exit
```Reboot.

As for the devices you linked, I can tell you about a few. The Tenda W311M has been through several versions. One version uses the MT7601 chipset and is fully supported in 15.10 but needs a firmware blob; easy enough.

In all of these devices, unless you know there was one and only one version and chipset and know what it is, it is a bit of a roll of the dice.

The Edimax EW-7811Un is apparently an rtl8192cu; so, no thanks.

The Tenda W322U has also been available in several versions: [http://www.linux-hardware-guide.com/2014-03-10-tenda-w322u-wifi-n300-adapter-300mbps-usb-2-0](http://www.linux-hardware-guide.com/2014-03-10-tenda-w322u-wifi-n300-adapter-300mbps-usb-2-0) All use a variation of rt2800usb. I don't like it.

The TP-LINK TL-WN727N has been available in four (!!!) versions; maybe the same chipset, probably not. One, at least, is also the MT7601. As I said, unless you know what version and chipset, it is a bit risky.

The TP-LINK TL-WN723N has two versions, the V3 is driven by the tricky rtl8188eu; no thanks.

Maybe some of the other wireless gurus will drop in and add to the list.

---

### Post by Hadaka on 2016-02-17
Hi, Bucky Ball
```
Trying to associate with 10:0d:7f:de:92:ba (SSID='Jetsons' freq=2437 MHz)
NetworkManager[638]: <info>  (wlan0): new 802.11 WiFi device (carrier: UNKNOWN,...')
NetworkManager[663]: <warn> (wlxe84e060dc5a4): Activation: failed for connection 'Jetsons'
```
i noticed these messages associated with your ssid of Jetsons, I am curious if perhaps you may have
uppercase " J " Jetsons defined in your NM setings and lowercase " j " in your router settings, let's check.
please do and post..
```
ls /etc/NetworkManager/system-connections
sudo iwlist wlan0 scan | grep ESSID
```
thanks.

---

### Post by Bucky Ball on 2016-02-17
Thanks Hadaka. No need to check. Upper-case 'J' in both and all, router and the eight or nine devices connecting wirelessly to the router, but worth a shot trying anything at the moment so worth a check. :)

```
[sudo] password for plimple: 
                    ESSID:"Jetsons"
                    ESSID:"D-Link DSL-2900AL"
                    ESSID:"JohnAndTracy"
                    ESSID:"NM&CP"
                    ESSID:"NM Home"
                    ESSID:"bob"
                    ESSID:"Telstra1037"
                    ESSID:"BigPond4BE3"
                    ESSID:"NetComm Wireless"
                    ESSID:"Mythical Emu"
```

On my laptop at the moment, but when the card was fine in 14.04 LTS on the desktop (a 14.04 which is now obliterated and no longer) it saw most of these networks. When it connects now it sees three, mine and a couple of others.

Will have a more careful read and get on to the other stuff, chili555, when I wake up a bit, but thanks for that and the info re. wifi. Yes, wish they'd advertise the chipset of these dongles instead of just make and model. Researching the things is a two step process. Find one, dig around to discover what card's in the thing, and then, as you say, the one you're going to buy may be a different version of same model. :|

PS: [I spotted this]("http://ubuntuforums.org/showthread.php?t=2313931&p=13441457#post13441457") last night. Another user having fun with an rtl8188, this time the eu, but perhaps for slightly different reasons, though. I do see a couple of similarities, but installing the rtlwifi-new might not drop a bomb or their install.

---

