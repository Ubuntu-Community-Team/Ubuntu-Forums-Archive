---
title: "Ethernet not recognized"
date: 2015-02-20
forum: Networking &amp; Wireless
---

### Post by klipa-nikola on 2015-02-20
I just installed Ubuntu on my PC and my ethernet cable is not recognized by Ubuntu. On my laptop ethernet works correctly under Windows. I will provide any information you need.

---

### Post by Hadaka on 2015-02-20
Hi, please post the output of..
```
lspci -nnk | grep -iA2 net
rfkill list all
lsmod
```
thanks

---

### Post by klipa-nikola on 2015-02-21
lspci -nnk | grep -iA2 net
> 
00:19.0 Ethernet controller [0200]: Intel Corporation 82566DM-2 Gigabit Network Connection [8086:10bd] (rev 02)    Subsystem: Dell OptiPlex 755 [1028:0211]
    Kernel driver in use: e1000e



rfkill list all
nothing

lsmod
> 
Module                  Size  Used by
nls_iso8859_1          12713  0 
usb_storage            62209  0 
bnep                   19624  2 
rfcomm                 69160  0 
bluetooth             391196  10 bnep,rfcomm
snd_hda_codec_analog    15049  1 
dcdbas                 14928  0 
snd_hda_intel          52355  3 
snd_hda_codec         192906  2 snd_hda_intel,snd_hda_codec_analog
snd_hwdep              13602  1 snd_hda_codec
coretemp               13435  0 
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm                   451511  0 
snd_rawmidi            30144  1 snd_seq_midi
serio_raw              13462  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  16 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog,snd_seq_midi
lpc_ich                21080  0 
soundcore              12680  1 snd
mei_me                 18627  0 
parport_pc             32701  1 
mac_hid                13205  0 
mei                    82276  1 mei_me
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
xts                    12914  1 
gf128mul               14951  1 xts
dm_crypt               23177  1 
hid_generic            12548  0 
usbhid                 52570  0 
hid                   106148  2 hid_generic,usbhid
i915                  783805  3 
video                  19476  1 i915
i2c_algo_bit           13413  1 i915
drm_kms_helper         53081  1 i915
psmouse               106678  0 
e1000e                254433  0 
ahci                   25819  2 
libahci                32560  1 ahci
drm                   303102  4 i915,drm_kms_helper
ptp                    18933  1 e1000e
pps_core               19382  1 ptp




---

### Post by Hadaka on 2015-02-21
Hi, nothing jumping out, go here and post the wireless info  text.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
this will provide additional information.
thanks.

---

### Post by klipa-nikola on 2015-02-21
```



########## wireless info START ##########


Report from: 08 Nov 2007 18:49 CET +0100


Booted last: 05 Nov 2007 08:24 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82566DM-2 Gigabit Network Connection [8086:10bd] (rev 02)
	Subsystem: Dell OptiPlex 755 [1028:0211]
	Kernel driver in use: e1000e


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 004: ID 04f2:0402 Chicony Electronics Co., Ltd Genius LuxeMate i200 Keyboard
Bus 007 Device 005: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID abcd:1234 Unknown 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Memory:fe9e0000-fea00000 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### nm-tool ###########################


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: Europe/Belgrade (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


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
blacklist r8169


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x10bd (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


########## wireless info END ############



```

---

### Post by Hadaka on 2015-02-21
Hi, please do..
```
sudo iw reg set RS
sudo sed -i 's/^REG.*=$/&RS/' /etc/default/crda
```
boot
then do..
```
sudo modprobe -rf e1000e
sudo modprobe e1000e
```

---

### Post by klipa-nikola on 2015-02-21
After last command "sudo modprobe e1000e" wrote "Disconected - you are now offline" and thats it. 
New wireless-info now looks like this
```



########## wireless info START ##########


Report from: 08 Nov 2007 20:17 CET +0100


Booted last: 08 Nov 2007 20:16 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82566DM-2 Gigabit Network Connection [8086:10bd] (rev 02)
    Subsystem: Dell OptiPlex 755 [1028:0211]
    Kernel driver in use: e1000e


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 04f2:0402 Chicony Electronics Co., Ltd Genius LuxeMate i200 Keyboard
Bus 007 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Memory:fe9e0000-fea00000 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### nm-tool ###########################


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: Europe/Belgrade (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


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
blacklist r8169


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x10bd (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


########## wireless info END ############



```

---

### Post by chili555 on 2015-02-21
The only thing that jumps out at me is:```
Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    [COLOR="#FF0000"]Carrier:         off[/COLOR]
```This suggests that the ethernet card doesn't detect a carrier signal from the router or switch. Please swap in a known working ethernet cable. Please try a different port of the router or switch and then try again:```
nm-tool
```Let's also see what's going on in the PCI bus:```
dmesg | grep 19.0
```

---

### Post by klipa-nikola on 2015-02-21
I again tried to put ethernet in my laptop and it works under Windows as I said. When cable is in my PC there is no signal between router and PC, the lamp is off. Only possible way is that my entry on PC is not working, but I know it worked 2 weeks ago under Windows.

dmesg | grep 19.0
```

[23802.192018] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[23802.192023] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[24806.196031] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[24806.196036] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[25305.192021] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[25305.192025] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[26219.016051] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[26219.016056] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[26309.196051] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[26309.196056] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[26808.192020] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[26808.192024] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[27812.196022] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[27812.196027] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[28311.192020] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[28311.192024] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[29219.004020] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[29219.004024] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[29315.196019] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[29315.196024] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[29814.196019] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[29814.196023] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[30313.192020] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[30313.192024] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED



```

---

### Post by chili555 on 2015-02-21
Interesting. All we got, probably because of the structure of my grep, was timestamps with 19 in them; not what we needed! As for the message itself, please see here: [http://askubuntu.com/questions/419853/mei-me-unexpected-reset](http://askubuntu.com/questions/419853/mei-me-unexpected-reset)

I know nothing about the subject, aside from what I read there. If you read it and agree, open a terminal and do:```
sudo -i
echo "blacklist mei-me"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r mei-me
exit
```Now let's try again:```
dmesg | grep 00:19
```Here, for comparison, is nm-tool from one of my machines:```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        XX:60:77:1B:50:XX

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    [COLOR="#FF0000"]Carrier:         on[/COLOR]
```

---

### Post by klipa-nikola on 2015-02-21
So now I have that last line with serial number, not sure what is that. I will try to find some other cable in next few days and then write here again if I dont solve the problem. Thanks for your time anyway..

```

[23802.192018] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[23802.192023] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[24806.196031] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[24806.196036] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[25305.192021] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[25305.192025] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[26219.016051] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[26219.016056] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[26309.196051] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[26309.196056] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[26808.192020] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[26808.192024] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[27812.196022] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[27812.196027] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[28311.192020] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[28311.192024] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[29219.004020] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[29219.004024] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[29315.196019] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[29315.196024] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[29814.196019] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[29814.196023] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[30313.192020] mei_me 0000:00:03.0: timer: connect/disconnect timeout.
[30313.192024] mei_me 0000:00:03.0: unexpected reset: dev_state = ENABLED
[37425.632915] usb 1-3: SerialNumber: 0201011059192063632810

```

---

### Post by chili555 on 2015-02-21
Please reboot so we have a clean slate. Open a terminal and run:```
dmesg  >  ethernet.txt
```Find the file ethernet.txt and paste it here: [http://paste.ubuntu.com](http://paste.ubuntu.com) Give us the link in your reply. Thanks.

---

### Post by klipa-nikola on 2015-02-21
[http://paste.ubuntu.com/10347286/](http://paste.ubuntu.com/10347286/)

Here it is

---

### Post by chili555 on 2015-02-21
I love a mystery; and by 'love,' I mean hate.

We see nothing wrong and therefore nothing fixable. Let's see what Network Manager is doing all this time.```
cat /var/log/syslog | grep -e eth0 -e etwork | tail -n20
```[http://paste.ubuntu.com](http://paste.ubuntu.com) please.

Our old friend mei-me is quiet.

---

### Post by klipa-nikola on 2015-02-21
[http://paste.ubuntu.com/10347667/](http://paste.ubuntu.com/10347667/)

I just really hope that its not hardware problem because I`m wasting your time then..

---

### Post by chili555 on 2015-02-21
> <info> (eth0): carrier is OFFThat is the same as nm-tool reports.

If you unplug and re-plug the ethernet cable, do the lights flicker? How about if you do:```
sudo modprobe -r e1000e
sudo modprobe e1000e
```Anything??

The log files do not appear to me to indicate a hardware problem at the ethernet device. Although you report it is unlikely, it seems more like a faulty cable or ethernet port on the router.

---

### Post by klipa-nikola on 2015-02-22
The light doesnt flicker. I would say same as you but the problem is that when I put cable in laptop, the light flicker and connection via ethernet is ok. So for me there is two options: its not working under Ubuntu for some reason or port on my PC was broken in last two weeks, I dont know how.

---

### Post by chili555 on 2015-02-25
Do the lights flicker as it boots from a cold start and then go out? Let's try something:```
sudo ethtool -s eth0 autoneg off
```Any lights or other changes?

---

