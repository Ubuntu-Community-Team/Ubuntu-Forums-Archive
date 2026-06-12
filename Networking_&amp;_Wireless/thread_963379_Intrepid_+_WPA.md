---
title: "Intrepid + WPA"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by Gifty85 on 2008-10-30
I've installed Ubuntu 8.04 and then I upgraded to 8.10. Now, when I try to connect to a wireless network with WPA, network manager keeps asking me for the WPA key and just don't connect.

How can I resolve this?

Thanks in advance.

---

### Post by Rommidze on 2008-10-30
If you switch WPA off on your router, does connection success? If it is then it looks like mine problem [here]("http://ubuntuforums.org/forumdisplay.php?f=336"), but no solution yet.

---

### Post by Rommidze on 2008-10-30
I have solved the issue for me. Could you provide ouput of the lsmod command?

---

### Post by Gifty85 on 2008-10-31
I changed the wireless security to WEP and I still can't establish a connection. Maybe the problem isn't about WPA...

lsmod command ouput:

```
Module                  Size  Used by
ipv6                  263972  10 
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
af_packet              25728  4 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  2 
sco                    18308  2 
l2cap                  30464  16 bnep,rfcomm
vboxdrv                71576  0 
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  2 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container              11520  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
arc4                    9984  2 
snd_mixer_oss          22784  1 snd_pcm_oss
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
iwl3945                98804  0 
snd_seq_oss            38528  0 
rfkill                 17176  2 iwl3945
sdhci_pci              15360  0 
snd_seq_midi           14336  0 
mac80211              216820  1 iwl3945
joydev                 18368  0 
sdhci                  23940  1 sdhci_pci
snd_rawmidi            29824  1 snd_seq_midi
btusb                  19736  3 
cfg80211               32392  2 iwl3945,mac80211
serio_raw              13444  0 
mmc_core               58268  1 sdhci
bluetooth              61924  11 bnep,rfcomm,sco,l2cap,btusb
pcspkr                 10624  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
evdev                  17696  15 
psmouse                45200  0 
nvidia               6900560  38 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_core               31892  1 nvidia
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tpm_infineon           17064  0 
tpm                    22848  1 tpm_infineon
tpm_bios               14080  1 tpm
video                  25104  5 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                 11008  1 video
battery                18436  0 
ac                     12292  0 
asus_laptop            24440  0 
soundcore              15328  1 snd
led_class              12164  2 iwl3945,asus_laptop
button                 14224  0 
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 37908  0 
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
pci_hotplug            35236  1 shpchp
ext3                  133256  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  4 
ohci1394               37936  0 
uhci_hcd               30736  0 
libata                177312  3 ata_generic,pata_acpi,ata_piix
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43276  0 
scsi_mod              155212  5 sbp2,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
r8169                  35972  0 
usbcore               148848  5 btusb,usbhid,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

---

### Post by t-timmy on 2008-11-01
Exact same problem here.
Keeps asking for WPA password. Attached lsmod output.

---

### Post by skaboss on 2008-11-01
I use WPA encryption and had the same problem (couldn't pass authentication).
Switching my router from chanel 4 to chanel 12 solved my problem...

---

### Post by nexusnode on 2008-11-01
Think I'm having the same issue.

Ubuntu 8.10 32 bit fresh install, WPA Encryption turned on, Laptop Model is an HP tx1340.

Needed to install the suggested proprietary driver and after that it can scan but not connect to any wireless networks.

I'm no linux whizz but i will do what I can - just say the word.

I saw these three lines in /var/log/wpa_supplicant.log:
> Trying to associate with "Access Point MAC" (SSID='SSIDhere' freq=2422MHz)
Association request to the driver failed
Authentication with "Access Point MAC" timed out.

lsmod dump attached

---

### Post by nexusnode on 2008-11-02
Bit of a bump but....

I have since tried changing the channel on the wireless access point and that had no effect - tried about 6 of them in the end.

I have also tried [This Guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"), I was hoping that the ndiswrapper route would help but it gives me the same results.  (After another fresh install)

Wired networking and even 3G work like a dream but WPA seems out of the question.

---

### Post by nexusnode on 2008-11-02
And just for the record I have reinstalled it again just now, used the automatically suggested driver and tried to connect to an unsecured network and it worked fine...

Looks like a lot of people are having the same problem, any one any ideas?

---

### Post by Chuckels550 on 2008-11-04
I have the same problem.  I upgraded from mythbuntu 8.04-1 to 8.10 and now my wireless connection will not accept any encryption.  I use the madwifi drivers for the card and wicd instead of network manager.  I connect just fine if I turn off the encryption at the router, but if I turn on the encryption mode - whatever encryption mode I try, WEP 64bit, WEP 128 bit, WPA PSK (TKIP) OR WPA2 PSK (AES) - my wireless connection fails.  In mythbuntu 8.04-1, I used WPA2 PSK (AES) and it worked flawlessly.

---

### Post by raiwo on 2008-11-04
having same problem, started today when i booted my machine; can't connect to WPA encrypted network...

---

### Post by t-timmy on 2008-11-04
I couldn't find any solution to this in other related threads.

Can someone please acknowledge the issue and tell us if there's a fix being prepared? Maybe you need more debugging info from us?

Thanks.

---

### Post by nexusnode on 2008-11-04
I don't know what I can possibly add, but I really don't want to let this issue drop - especially the way that this version of ubuntu is supposed to have fantastic wireless.  I can see massive leaps forward have been made, but we seem to have taken a step back in a couple of critical places.

Please could someone with some knowledge on this topic have some input, or at the very least let us know what we can do to help this forward.

---

### Post by brechtvb on 2008-11-04
I have somewhat the same problem. But my wireless network is not even showing up in the list of wireless networks. But i can define it manually and it tries to connect, but always fails. I double checked the SSID and password and everything.

I did not try a connection without encryption, i will try that tomorrow. I will now try to read the wifi-logs. Maybe that answers some questions.

---

### Post by jimv on 2008-11-04
Try using WICD instead.  It's an alternative to NetworkMangler and it works much better.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by brechtvb on 2008-11-04
i tried it also, it also does not shows my own wireless network. But it shows the ones from the other buildings around.

---

### Post by iamthemicrowave on 2008-11-05
I am having the same problem, wpa enterprise keeps saying I need a network key

---

### Post by mikkoko on 2008-11-05
Same here: can't connect to WPA encrypted networks with Ubuntu 8.10 (WICD or Network Manager). 

WICD just fails to connect with no notifications, NetworkManager keeps asking for the passphrase.

This is a Thinkpad X61 with Intel 9565AGN wireless chip. Connecting to an unsecured network works fine.

---

### Post by oyankee on 2008-11-05
Post here
>  lspci -v | less
and
> iwconfig

Please

---

### Post by arossco on 2008-11-05
I've just installed 8.10 and gone through the ndiswrapper stuff to get my Acer Travelmate 212TXV and Linksys WPC11 Ver4 Wireless-B PC Adapter working.

I also can connect to my wireless network with encryption turned off, but I'm not connecting with WPA enabled.

I've noticed that when I enter my password in the "Wireless Network Authentication Required" window with "show password" checked it fails to connect, then the password box contains a 64 character hex number.

lspci -v | less :

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
Subsystem: Linksys Device 0019
Flags: bus master, medium devsel, latency 64, IRQ 11 
I/O ports at 1400 [size=256]
Memory at 34000000 (332-bit non-prefetchable) [size=512]
Capabilities: <access denied>
Kernel driver in use: ndiswrapper
Kernel modules: rtl8180

iwconfig :

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by nexusnode on 2008-11-05
Thanks for the replies.  Here is the info you requested:

---

### Post by Hobgoblin on 2008-11-05
> **Gifty85 said:**
> I've installed Ubuntu 8.04 and then I upgraded to 8.10. Now, when I try to connect to a wireless network with WPA, network manager keeps asking me for the WPA key and just don't connect.


I had the same problem, the only way to get connected was to delete the network from network manager then create it again.  After shutdown/restart/suspend it would need doing again.

I have 
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.

I seem to have fixed it by installing linux-backports-modules-intrepid-generic then changing the driver using System > Administration > Hardware drivers to use the Atheros 5xxx driver.

---

### Post by mikkoko on 2008-11-06
As requested, here is my lspci and iwconfig output. This is a Thinkpad X61, can't connect to WPA secured networks.

lspci:

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
        Subsystem: Intel Corporation Device 1111
        Flags: bus master, fast devsel, latency 0, IRQ 219
        Memory at fdf00000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [e0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Device Serial Number 83-4e-36-ff-ff-3b-1f-00
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn



iwconfig:

wlan0     IEEE 802.11abgn  ESSID:"xxxx"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

(the ESSID iwconfig shows came from an unsecured public network)

---

### Post by t-timmy on 2008-11-06
jimv, thank you for your suggestion, but I think we should help fix the problem in the included network manager.

My files:

---

### Post by Chuckels550 on 2008-11-06
Intrepid (2.6.27-7-generic) seems to be missing the wpasupplicant madwifi configuration.  When I run the following command:

wpa_supplicant -d -c /etc/wpa_supplicant.conf -iath0 -Dmadwifi

I get the following:

Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A' bridge 'N/A'
Unsupported driver 'madwifi'.

Failed to add interface ath0
Cancelling scan request
Cancelling authentication timeout

I have reinstalled wpa_supplicant, but it makes no difference.

How can this be fixed?

---

### Post by t-timmy on 2008-11-07
Exact same output over here.
Even ran update manager through the neighbour's unsecured network (shh :)) but still no connection.
```

Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A' bridge 'N/A'
Unsupported driver 'madwifi'.

Failed to add interface ath0
Cancelling scan request
Cancelling authentication timeout 
```

---

### Post by nexusnode on 2008-11-07
I get the same as well - does that mean were on to something?

---

### Post by fletschge on 2008-11-09
I have exactely the same problem. Ubuntu 8.10 seems to be unable to connect to WPA networks. After 20 seconds I always get the password prompt again.

Anybody found a solution or do we really have to wait for the new kernel?

thanks,

---

### Post by t-timmy on 2008-11-09
It's been a while and nobody has said anything about a fix or about the status of the problem...
I've uninstalled Ubuntu, will keep an eye on this thread.

---

### Post by nexusnode on 2008-11-09
I don't have the expertise to more forwards with this one.  What I will say though is that I went to a friends who has a WEP wireless network setup and it worked fine.  This would suggest to confirm that its just WPA thats a problem, however....

Just to add another bit of a mix to the problem, a collegue of mine has an older laptop and can connect with an upgraded 8.04 -> 8.10 ubuntu to the same WPA network I can't.

---

### Post by spiderbatdad on 2008-11-09
First read dmesg to see if the kernel advises wireless driver does not support wpa.
To enable wpa support for the driver your card uses, you might try the following:
1. Create the file: /boot/loader.conf
   in it put the line:```
 if_an_load="YES"
```

2. edit /etc/kernel-img.conf
   add the lines: ```
device an
device wlan
```

3. Reboot

---

### Post by t-timmy on 2008-11-09
> **spiderbatdad said:**
> First read dmesg to see if the kernel advises wireless driver does not support wpa.
To enable wpa support for the driver your card uses, you might try the following:
1. Create the file: /boot/loader.conf
   in it put the line:```
 if_an_load="YES"
```

2. edit /etc/kernel-img.conf
   add the lines: ```
device an
device wlan
```

3. Reboot

Hi,

Thanks for the reply.

I don't know what "dmesg" is, but I did the rest, and it still prompts for the password and wouldn't connect.

Anything else I can try?

---

### Post by nexusnode on 2008-11-10
dmesg for me doesnt report anything to do with WPA at all.

Anything else we can try?

---

### Post by majikshoe on 2008-11-10
dmesg prints out your kernel logs.  You can also see your logs in the menu: System -> Administration -> System Log.  Have a look in "debug.log" or "kernel.log" for clues on your wireless problems.

Do your logs show authentication or association to the wireless access point timing out?  I don't have a solution, but the symptoms you are describing (NetworkManager re-prompting for password) are what I'm getting, as described in this thread: [http://ubuntuforums.org/showthread.php?t=977355](http://ubuntuforums.org/showthread.php?t=977355)

Cheers,
Jason

---

### Post by gutsy_user on 2008-11-11
I'm not sure whether this is the problem we are experiencing, but there seems to be a problem with the madwifi drivers (see below).

I do have installed the "backports", but don't know how to switch to the other drivers on "Kubuntu"...



[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Atheros ath5k wireless driver not enabled by default

The version of the ath5k driver for Atheros wireless devices included in Linux 2.6.27 interferes with the use of the madwifi driver for some wireless devices and as a result has been disabled by default. Many Atheros chipsets will work correctly with the madwifi driver, but some newer chipsets may not, and the madwifi driver may not work with WPA authentication. If you have an Atheros device that does not work with madwifi, you will want to install the linux-backports-modules-intrepid-generic package, which includes an updated version of the ath5k driver. While not installed by default, this linux-backports-modules-intrepid-generic package is included on the Ubuntu 8.10 CD and DVD images for ease of installation.

---

### Post by transmition on 2008-11-11
Well, this isn't a solution, but I have experienced the same problem and this is what I noticed:

It prompts me for wireless password, which is a string of random letters and numbers. I enter it and try to connect. After some time, it prompts me again, this time with my password already typed in. I figured that I had made some type of spelling error, so I click the option to reveal password. To my shock, I see that it has been replaced with a completely different string of letters and numbers. 

I suspect that the network manager is not recording our passwords properly, and thus times out because it gets rejected by the router.

---

### Post by transmition on 2008-11-11
Sorry, double Post.

---

### Post by t-timmy on 2008-11-11
> **transmition said:**
> Well, this isn't a solution, but I have experienced the same problem and this is what I noticed:

It prompts me for wireless password, which is a string of random letters and numbers. I enter it and try to connect. After some time, it prompts me again, this time with my password already typed in. I figured that I had made some type of spelling error, so I click the option to reveal password. To my shock, I see that it has been replaced with a completely different string of letters and numbers. 

I suspect that the network manager is not recording our passwords properly, and thus times out because it gets rejected by the router.

I get the same scrambling of letters and numbers, but I think this is normal. The network manager just translated your "human" password to "machine" language. I think this is normal.

The problem is something under the hood.

---

### Post by FTL_Diesel on 2008-11-11
> **t-timmy said:**
> I get the same scrambling of letters and numbers, but I think this is normal. The network manager just translated your "human" password to "machine" language. I think this is normal.

This is exactly what is happening.

---

### Post by nexusnode on 2008-11-11
Has anyone else tried the linux-backports-modules-intrepid-generic package?

---

### Post by t-timmy on 2008-11-12
> **nexusnode said:**
> Has anyone else tried the linux-backports-modules-intrepid-generic package?

The last thing I tried was spiderbatdad's suggestion, which did not solve the problem.

---

### Post by kevdog on 2008-11-12
I appreciate the collaboration in this thread, however I think all of you may be dealing with different chipsets and different drivers.  Also the best way to troubleshoot anything is to attempt to connect using the command line and then build from there.  I've made a post about connecting from the command line in my signature, however you also must know the driver you are using. 

lshw -C network 
in many cases can give a clue -- although it doesnt always spit out the most obvious answer.

---

### Post by herdthat on 2008-11-12
I'm using a Linksys WUSB54GSC adapter, and I'm having the same issue where it asks for me WPA/WPA2 password and it just never connects, just tries to connect then either stops or asks for my password again...

---

### Post by nexusnode on 2008-11-12
well lets find out... for what its worth here is the results from my lshw -C network command:

>   *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 00:1a:73:d1:e0:16
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ba:e2:22:65:cc:5e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by mateuszbaranski on 2008-11-12
I got finally my wireless card working! I have Atheros Communications Inc. AR5212 802.11abg NIC (rev 01) in IBM ThinkPad T42 notebook.

I followed the advise from release notes 
[http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros ath5k wireless driver not enabled by default]("http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros ath5k wireless driver not enabled by default")

So follow these steps:
1) In Synaptic or trough apt-get install the linux-backports-modules-intrepid-generic package.
e.g:
```
sudo apt-get install linux-backports-modules-intrepid-generic
```
2)I reboted now in order the new driver for wireless card was found
3) After reboot my wifi card still didn't work so I went to the Driver Menager  (I have kubuntu so it is in Programs-> system -> Drivers) - I have found that there are two drivers used at the same time:
-Suport for 5xxx series of Atheros 802.11 wireless LAN cards
-Suport for Atheros 802.11 wireless LAN cards

4) I have turned off the latter  and left only the first one (for 5xxx serie)

5) I rebooted again and surprisingly wifi card stared working without further intervention.

If you look into modules loaded into kernel I have now:
```
mbaransk@sardes:~$ lsmod |grep ath
ath5k                 106496  0
lbm_cw_mac80211       210728  1 ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  2 thinkpad_acpi,ath5k

```
Before I installed linux-backports package I had a ath_pci module instead of ath5k (ath_pci is also known as a madwifi driver).

I hope it will help some guys struggling with interpid which I admit needs still much debugging - but I don't want to go back to 8.04 for one reason - I love the look of KDE4.1 :-)

---

### Post by Swagman on 2008-11-12
I've noticed this happens when your isp is Sky

---

### Post by mateuszbaranski on 2008-11-12
> **gutsy_user said:**
> 
I do have installed the "backports", but don't know how to switch to the other drivers on "Kubuntu"...

Thank you gutsy_user for hint - I got finally it working. See my previous post for further information.

---

### Post by gutsy_user on 2008-11-12
> **mateuszbaranski said:**
> I got finally my wireless card working! I have Atheros Communications Inc. AR5212 802.11abg NIC (rev 01) in IBM ThinkPad T42 notebook.

I followed the advise from release notes 
[http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros ath5k wireless driver not enabled by default]("http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros ath5k wireless driver not enabled by default")

So follow these steps:
1) In Synaptic or trough apt-get install the linux-backports-modules-intrepid-generic package.
e.g:
```
sudo apt-get install linux-backports-modules-intrepid-generic
```
2)I reboted now in order the new driver for wireless card was found
3) After reboot my wifi card still didn't work so I went to the Driver Menager  (I have kubuntu so it is in Programs-> system -> Drivers) - I have found that there are two drivers used at the same time:
-Suport for 5xxx series of Atheros 802.11 wireless LAN cards
-Suport for Atheros 802.11 wireless LAN cards

4) I have turned off the latter  and left only the first one (for 5xxx serie)

5) I rebooted again and surprisingly wifi card stared working without further intervention.

If you look into modules loaded into kernel I have now:
```
mbaransk@sardes:~$ lsmod |grep ath
ath5k                 106496  0
lbm_cw_mac80211       210728  1 ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  2 thinkpad_acpi,ath5k

```
Before I installed linux-backports package I had a ath_pci module instead of ath5k (ath_pci is also known as a madwifi driver).

I hope it will help some guys struggling with interpid which I admit needs still much debugging - but I don't want to go back to 8.04 for one reason - I love the look of KDE4.1 :-)

Thanks for the detailed HOWTO -- it now also works fine for me.

As a note to other troubled users:

Don't forget to 'sudo apt-get remove --purge madwifi-tools', otherwise you'll have to issue a 'sudo modprobe ath5k' before the modules load.

---

### Post by thread_au on 2008-11-13
well, i don't have my xubuntu eeepc with me right now, as i updated another package and now connecting to networks seems to hang the machine.

That said, just registering that I had exactly the same problem with eeepc901 card (no secured networks).  I'll see if the solution mentioned above yields results.

---

### Post by Chuckels550 on 2008-11-14
> I got finally my wireless card working! I have Atheros Communications Inc. AR5212 802.11abg NIC (rev 01) in IBM ThinkPad T42 notebook.

I followed the advise from release notes
[http://www.ubuntu.com/getubuntu/rele...led](http://www.ubuntu.com/getubuntu/rele...led) by default

So follow these steps:
1) In Synaptic or trough apt-get install the linux-backports-modules-intrepid-generic package.
e.g:
Code:

sudo apt-get install linux-backports-modules-intrepid-generic

2)I reboted now in order the new driver for wireless card was found
3) After reboot my wifi card still didn't work so I went to the Driver Menager (I have kubuntu so it is in Programs-> system -> Drivers) - I have found that there are two drivers used at the same time:
-Suport for 5xxx series of Atheros 802.11 wireless LAN cards
-Suport for Atheros 802.11 wireless LAN cards

4) I have turned off the latter and left only the first one (for 5xxx serie)

5) I rebooted again and surprisingly wifi card stared working without further intervention.

If you look into modules loaded into kernel I have now:
Code:

mbaransk@sardes:~$ lsmod |grep ath
ath5k                 106496  0
lbm_cw_mac80211       210728  1 ath5k
lbm_cw_cfg80211        39696  2 ath5k,lbm_cw_mac80211
led_class              12164  2 thinkpad_acpi,ath5k

Before I installed linux-backports package I had a ath_pci module instead of ath5k (ath_pci is also known as a madwifi driver).

I hope it will help some guys struggling with interpid which I admit needs still much debugging - but I don't want to go back to 8.04 for one reason - I love the look of KDE4.1 

For me, connecting is not the problem.  The problem is that I cannot connect using encryption.  Were you able to get the connection to work with an encryption mode and if so, which one did you use - WEP 64b?, WEP 128b, WPA PSK or any of the others?

---

### Post by acreech on 2008-11-14
I am also having a similar problem with my wireless. I have my wireless driver installed and I can view all the wireless networks in my area. I just can not connect to my own wireless router.

I have tried changing it from a WPA to a WEP. I also tried changing the channels on my router and that did not have any effect. 

My router is a 2wire router. I have been wondering if this was a problem with the router or with ubuntu.

---

### Post by kevdog on 2008-11-14
This thread has way too many hijackers.  Some of the posters are talking about broadcom chipsets, others are talking about Atheros chipsets.  The solutions for each chipset are completely different.

I'd suggest whomever needs help, repost in a new thread, and make sure no one hijacks that thread.

---

### Post by acreech on 2008-11-14
I still have not found a solution to this problem. I have my wireless card installed and functional. I have tried to connect to my 2wire wireless modem using a WEP-Open, WEP-shared, WPA-PSK, and WPA2-PSK connections. 

I have switched the wireless channel from 1 to 11 and have not seen any change to the problem. 

It seems that this problem may be a problem with the router compatibility with Ubuntu. The router is functioning when using a Windows system, however I can't connect to it using a Linux system. I have not found any threads or files that would indicate which routers are known to be compatible to Ubuntu. I think that this issue has something to do with the router compatibility as opposed to a problem with the network card, because I have connected to a linksys router in the past. 

The system that I am using is a Acer Aspire 7520-5185 with an atheros wireless network card. Here is some other information that may be useful in attempting to get help with this issue. 

```
 iwconfig 
```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

```
 lsmod

```

```
Module                  Size  Used by
ipv6                  263972  10 
binfmt_misc            16904  1 
af_packet              25728  4 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,rfcomm,sco,l2cap
ppdev                  15620  0 
powernow_k8            22148  1 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       9856  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
video                  25104  0 
output                 11008  1 video
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ndiswrapper           196380  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
psmouse                45200  0 
acer_wmi               18880  0 
led_class              12164  1 acer_wmi
pcspkr                 10624  0 
serio_raw              13444  0 
evdev                  17696  11 
nvidia               6900560  42 
agpgart                42184  1 nvidia
k8temp                 12416  0 
uvcvideo               62728  0 
i2c_core               31892  1 nvidia
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
snd_hda_intel         381488  3 
battery                18436  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
ac                     12292  0 
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  1 sdhci
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
wmi                    14504  1 acer_wmi
button                 14224  0 
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
pata_amd               18692  0 
ahci                   37132  3 
pata_acpi              12160  0 
ohci1394               37936  0 
ata_generic            12932  0 
ieee1394               96324  2 sbp2,ohci1394
libata                177312  4 pata_amd,ahci,pata_acpi,ata_generic
ohci_hcd               31888  0 
forcedeth              61328  0 
ehci_hcd               43276  0 
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
usbcore               148848  6 ndiswrapper,uvcvideo,usbhid,ohci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  3 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
acreech@acreech-laptop:~$ lshw -C
Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.13)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

acreech@acreech-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:c8:1c:d2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=75.167.153.163 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:04:bd:7a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.53+,05/02/2007,5.3.0.45 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:d3:b6:18:fa:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Any help would be appreciated.

---

### Post by stanley drew on 2008-11-14
> **kevdog said:**
> This thread has way too many hijackers.  Some of the posters are talking about broadcom chipsets, others are talking about Atheros chipsets.  The solutions for each chipset are completely different.

I'd suggest whomever needs help, repost in a new thread, and make sure no one hijacks that thread.

It just seems like a lot of people are having the same problem regardless of chipset, which makes it appear to be a problem with network-manager or the keyring. If that software really does depend on the chipset then we should have separate threads, but I know that a lot of people (myself included) have posted our own threads and received no attention with much frustration. So we are posting in this thread cause it seems like people are reading it.

You say that the solutions are completely different for each chipset? Then pick one of the configurations above and let's start to solve this thing.

---

### Post by t-timmy on 2008-11-14
> **stanley drew said:**
> It just seems like a lot of people are having the same problem regardless of chipset, which makes it appear to be a problem with network-manager or the keyring. If that software really does depend on the chipset then we should have separate threads, but I know that a lot of people (myself included) have posted our own threads and received no attention with much frustration. So we are posting in this thread cause it seems like people are reading it.

You say that the solutions are completely different for each chipset? Then pick one of the configurations above and let's start to solve this thing.

I agree.
This thread is very active with a lot of reads (4,000+ last time I checked).
This means that people with Wi-fi problems will read this first.
We can fix the issue here and when we're done a patch can be made to the network manager, and a Sticky added to the forum (since people with no network working will have trouble obtaining the fix).

As my machine and/or chipset is one of the few (I assume most computers work fine with 8.10) that suffer from this issue I have re-installed Ubuntu 8.10 and ready to provide more debugging printouts/logs in order to help.

Have a good weekend all, and thank you all for helping :)

---

### Post by nexusnode on 2008-11-14
Agreed, ok so to get the ball rolling...

Fresh install of 8.10 32 bit on an HP tx1340 laptop that has no problems whatsoever connecting to unsecured and WEP networks.  The wireless chipset on this particular is confirmed to be a BCM4328 802.11a/b/g/n.  The WPA network that I am trying to connect to is confirmed working by an 8.04 machine, a windows machine and a windows mobile device.

The troubled device can see the network but repeatedly asks for the network key.

To diagnose this problem any further I am happy to provide the output from any command, log etc - but your going to need to tell me which ones you want.

---

### Post by laurentp on 2008-11-14
Hi, 
I have a similar strange problem. I can connect to WPA network, but after some times my computer start disconnecting/reconnecting before there is a complete hard crash with SHIFT key flashing ( can't hit ctrl-alt-del or ctrl-alt-backspace, have to remove power). I can't see anything useful in dmesg or syslog... I can't find any help and this bug is really annoying. 

 ```
*-network
                description: Wireless interface
                product: BCM4322 802.11a/b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth1
                version: 01
                serial: 00:21:00:36:88:e9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl ip=192.168.1.101 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn

```

Here is the syslog from connection to the time of crash :
```

Nov  8 16:28:10 larrylaptop-Intrepid NetworkManager: <WARN>  nm_device_wifi_set_enabled(): not in expected unavailable state! 
Nov  8 16:28:10 larrylaptop-Intrepid NetworkManager: <info>  (eth1): bringing up device. 
Nov  8 16:28:10 larrylaptop-Intrepid NetworkManager: <info>  (eth1): device state change: 2 -> 3 
Nov  8 16:28:10 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant interface state change: 1 -> 2. 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) starting connection 'Auto The Geek Squad' 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  (eth1): device state change: 3 -> 4 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  (eth1): device state change: 4 -> 5 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1/wireless): connection 'Auto The Geek Squad' has security, and secrets exist.  No new secrets needed. 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Config: added 'ssid' value 'The Geek Squad' 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  Config: set interface ap_scan to 1 
Nov  8 16:28:25 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant connection state change: 1 -> 2 
Nov  8 16:28:35 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 3 
Nov  8 16:28:39 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 4 
Nov  8 16:28:39 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant connection state change: 4 -> 5 
Nov  8 16:28:40 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant connection state change: 5 -> 6 
Nov  8 16:28:40 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant connection state change: 6 -> 7 
Nov  8 16:28:40 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'The Geek Squad'. 
Nov  8 16:28:40 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov  8 16:28:40 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Nov  8 16:28:40 larrylaptop-Intrepid NetworkManager: <info>  (eth1): device state change: 5 -> 7 
Nov  8 16:28:40 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Nov  8 16:28:40 larrylaptop-Intrepid NetworkManager: <info>  dhclient started with pid 10578 
Nov  8 16:28:40 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Nov  8 16:28:40 larrylaptop-Intrepid dhclient: Internet Systems Consortium DHCP Client V3.1.1
Nov  8 16:28:40 larrylaptop-Intrepid dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  8 16:28:40 larrylaptop-Intrepid dhclient: All rights reserved.
Nov  8 16:28:40 larrylaptop-Intrepid dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov  8 16:28:40 larrylaptop-Intrepid dhclient: 
Nov  8 16:28:40 larrylaptop-Intrepid NetworkManager: <info>  DHCP: device eth1 state changed (null) -> preinit 
Nov  8 16:28:40 larrylaptop-Intrepid dhclient: Listening on LPF/eth1/00:21:00:36:88:e9
Nov  8 16:28:40 larrylaptop-Intrepid dhclient: Sending on   LPF/eth1/00:21:00:36:88:e9
Nov  8 16:28:40 larrylaptop-Intrepid dhclient: Sending on   Socket/fallback
Nov  8 16:28:42 larrylaptop-Intrepid dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Nov  8 16:28:42 larrylaptop-Intrepid dhclient: DHCPOFFER of 192.168.0.108 from 192.168.0.1
Nov  8 16:28:42 larrylaptop-Intrepid dhclient: DHCPREQUEST of 192.168.0.108 on eth1 to 255.255.255.255 port 67
Nov  8 16:28:42 larrylaptop-Intrepid dhclient: DHCPACK of 192.168.0.108 from 192.168.0.1
Nov  8 16:28:42 larrylaptop-Intrepid dhclient: bound to 192.168.0.108 -- renewal in 275997 seconds.
Nov  8 16:28:42 larrylaptop-Intrepid NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound 
Nov  8 16:28:42 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov  8 16:28:42 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Nov  8 16:28:42 larrylaptop-Intrepid NetworkManager: <info>    address 192.168.0.108 
Nov  8 16:28:42 larrylaptop-Intrepid NetworkManager: <info>    prefix 24 (255.255.255.0) 
Nov  8 16:28:42 larrylaptop-Intrepid NetworkManager: <info>    gateway 192.168.0.1 
Nov  8 16:28:42 larrylaptop-Intrepid NetworkManager: <info>    nameserver '192.168.0.1' 
Nov  8 16:28:42 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov  8 16:28:42 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Nov  8 16:28:42 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Nov  8 16:28:42 larrylaptop-Intrepid avahi-daemon[5086]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.108.
Nov  8 16:28:42 larrylaptop-Intrepid avahi-daemon[5086]: New relevant interface eth1.IPv4 for mDNS.
Nov  8 16:28:42 larrylaptop-Intrepid avahi-daemon[5086]: Registering new address record for 192.168.0.108 on eth1.IPv4.
Nov  8 16:28:43 larrylaptop-Intrepid NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Nov  8 16:28:43 larrylaptop-Intrepid NetworkManager: <debug> [1226179723.074496] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:28:43 larrylaptop-Intrepid NetworkManager: <info>  Policy set 'Auto The Geek Squad' (eth1) as default for routing and DNS. 
Nov  8 16:28:43 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) successful, device activated. 
Nov  8 16:28:43 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  8 16:28:46 larrylaptop-Intrepid ntpdate[10634]: step time server 91.189.94.4 offset 0.668565 sec
Nov  8 16:28:51 larrylaptop-Intrepid NetworkManager: <debug> [1226179731.086040] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:28:53 larrylaptop-Intrepid modprobe: WARNING: Not loading blacklisted module ipv6 
Nov  8 16:29:03 larrylaptop-Intrepid NetworkManager: <debug> [1226179743.094505] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:29:27 larrylaptop-Intrepid NetworkManager: <debug> [1226179767.110436] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:29:33 larrylaptop-Intrepid NetworkManager: <debug> [1226179773.114726] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:33:51 larrylaptop-Intrepid NetworkManager: <debug> [1226180031.293858] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:34:03 larrylaptop-Intrepid NetworkManager: <debug> [1226180043.302081] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:34:15 larrylaptop-Intrepid NetworkManager: <debug> [1226180055.314486] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:34:45 larrylaptop-Intrepid NetworkManager: <debug> [1226180085.342067] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:34:51 larrylaptop-Intrepid NetworkManager: <debug> [1226180091.347155] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:34:57 larrylaptop-Intrepid NetworkManager: <debug> [1226180097.356462] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:37:39 larrylaptop-Intrepid NetworkManager: <debug> [1226180259.466080] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:37:45 larrylaptop-Intrepid NetworkManager: <debug> [1226180265.474895] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:37:57 larrylaptop-Intrepid NetworkManager: <debug> [1226180277.490063] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:38:15 larrylaptop-Intrepid NetworkManager: <debug> [1226180295.502557] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:38:27 larrylaptop-Intrepid NetworkManager: <debug> [1226180307.514561] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:38:33 larrylaptop-Intrepid NetworkManager: <debug> [1226180313.518064] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:40:52 larrylaptop-Intrepid modprobe: WARNING: Not loading blacklisted module ipv6 
Nov  8 16:41:09 larrylaptop-Intrepid NetworkManager: <debug> [1226180469.631629] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:41:15 larrylaptop-Intrepid NetworkManager: <debug> [1226180475.634511] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:41:45 larrylaptop-Intrepid NetworkManager: <debug> [1226180505.654306] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:43:03 larrylaptop-Intrepid NetworkManager: <debug> [1226180583.705885] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:43:09 larrylaptop-Intrepid NetworkManager: <debug> [1226180589.710627] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:43:57 larrylaptop-Intrepid NetworkManager: <debug> [1226180637.746039] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:44:03 larrylaptop-Intrepid NetworkManager: <debug> [1226180643.754698] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:44:09 larrylaptop-Intrepid NetworkManager: <debug> [1226180649.754041] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:46:21 larrylaptop-Intrepid NetworkManager: <debug> [1226180781.842813] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:46:27 larrylaptop-Intrepid NetworkManager: <debug> [1226180787.846078] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:46:45 larrylaptop-Intrepid NetworkManager: <debug> [1226180805.862057] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:46:51 larrylaptop-Intrepid NetworkManager: <debug> [1226180811.866057] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:46:57 larrylaptop-Intrepid NetworkManager: <debug> [1226180817.870157] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:47:21 larrylaptop-Intrepid NetworkManager: <debug> [1226180841.888174] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:47:39 larrylaptop-Intrepid NetworkManager: <debug> [1226180859.898242] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:47:45 larrylaptop-Intrepid NetworkManager: <debug> [1226180865.902535] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:47:51 larrylaptop-Intrepid NetworkManager: <debug> [1226180871.915268] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:48:03 larrylaptop-Intrepid NetworkManager: <debug> [1226180883.922560] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:50:34 larrylaptop-Intrepid NetworkManager: <debug> [1226181034.030372] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:50:46 larrylaptop-Intrepid NetworkManager: <debug> [1226181046.038071] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:51:04 larrylaptop-Intrepid NetworkManager: <debug> [1226181064.054070] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:51:52 larrylaptop-Intrepid NetworkManager: <debug> [1226181112.093928] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:52:04 larrylaptop-Intrepid NetworkManager: <debug> [1226181124.102580] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:52:10 larrylaptop-Intrepid NetworkManager: <debug> [1226181130.106555] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:52:16 larrylaptop-Intrepid NetworkManager: <debug> [1226181136.110646] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:52:22 larrylaptop-Intrepid NetworkManager: <debug> [1226181142.118149] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:52:28 larrylaptop-Intrepid NetworkManager: <debug> [1226181148.122109] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:52:34 larrylaptop-Intrepid NetworkManager: <debug> [1226181154.135515] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:52:40 larrylaptop-Intrepid NetworkManager: <debug> [1226181160.142096] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:52:46 larrylaptop-Intrepid NetworkManager: <debug> [1226181166.146081] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:52:58 larrylaptop-Intrepid NetworkManager: <debug> [1226181178.154069] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:53:22 larrylaptop-Intrepid NetworkManager: <debug> [1226181202.170127] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:53:28 larrylaptop-Intrepid NetworkManager: <debug> [1226181208.174024] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
Nov  8 16:53:40 larrylaptop-Intrepid NetworkManager: <debug> [1226181220.185994] periodic_update(): Roamed from BSSID 00:15:E9:6C:16:02 (The Geek Squad) to (none) ((none)) 
Nov  8 16:53:52 larrylaptop-Intrepid NetworkManager: <debug> [1226181232.194584] periodic_update(): Roamed from BSSID (none) ((none)) to 00:15:E9:6C:16:02 (The Geek Squad) 
```

Thanks for your time,

Laurent

---

### Post by kevdog on 2008-11-14
Ok -- so for the time being this thread is only going to focus on broadcom chipsets since that was what was posted on the last two responses.

There are a few things concerning Broadcom chipsets
Native drivers are the bcm43xx, b43, wl drivers.  The wl driver is only for chipset ID 14e4:4315.  The wl driver is not for any other broadcom chipset.  As you can see, it tends to get quite clumsy for the native set.

My personal recommendation, would be to forget about any native bcm43xx, b43, b43legacy, wl drivers and lean toward the ndiswrapper/winxp driver solution.  The ndiswrapper kernel module wraps the actual windows driver inside and uses this as the driver.  This is technically a third party solution.  

Using ndiswrapper does introduce a new set of challenges -- specifically what windows driver do I use.  The best source for broadcom chipsets is Jamie Jackson's wonderful broadcom wiki (Its applicable to more than just Feisty -- so forget the title):
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

You will need to grab the appropriate windows driver based on the chipset id which you can find from:
lspci -nn
You will also need to install ndiswrapper.  I always recommend compiling from source, however ndiswrapper is available in the repository by:
sudo aptitude install ndiswrapper

Follow the remainder of the instructions to wrap the window's driver within ndiswrapper and install the kernel module, and then blacklist the appropriate bcm or b43 modules as described in the thread to prevent these drivers from taking priority over ndiswrapper at boot.  

Network manager may then correctly interact with this ndiswrapper/windows xp module, however if not, then we can troubleshoot what is not working using the command line, and attempting to make a command line connection independent of ndiswrapper.

Sounds like a lot, however once you go through the process once -- you will be an "expert" at troubleshooting problems in the future:)

---

### Post by nexusnode on 2008-11-15
Ok that sounds plausible.  I will try the ndiswrapper route however.  Given that mine is the 4328 and its loading the wl module - shouldn't I try blocking that one first and seeing if one of the other native drivers does the job?  I would just try this however I'm not sure how to start.

---

### Post by acreech on 2008-11-15
If the drivers are installed and the network manager is able to detect the wireless networks in the area, I don't understand why they would need to install new drivers. Especially when some of the previous posters have stated that they can connect to networks who are not using a WPA connection. 

I am confused?

---

### Post by t-timmy on 2008-11-15
> **acreech said:**
> If the drivers are installed and the network manager is able to detect the wireless networks in the area, I don't understand why they would need to install new drivers. Especially when some of the previous posters have stated that they can connect to networks who are not using a WPA connection. 

I am confused?

I agree, this doesn't seem to be a problematic driver issue, especially since it worked fine in 8.04.
However, we are not experts here, so maybe we should follow kevdog's directions.

In any case I'm putting my problem on hold here, because I don't have a broadcom chipset, I have an Edimax USB adapter. We'll try to solve mine later.

---

### Post by kevdog on 2008-11-15
Although the b43 driver family works for some people, you are going to find the b43 built-in driver's buggy.  That has been my experience over many versions.  If you want a true built-in experience, you need an Atheros chipset.  Broadcom's are reliable, however personally I think the b43 family of drivers is poor.  If you want to keep using the b43 driver family, then that's OK.  Proceed to manual configuring the driver using the command line, as per the link in my signature.  I would first recommend turning off all encryption at the router, and then build in encryption when you get a working connection.  WPA or WEP (particularly WEP) builds in another layer of complexity.  Try not to take a huge bite of pie all at once -- just proceed in steps.  Network Manager although a very nice GUI, is sometimes very buggy (at least past versions).  Here is the command line version:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by nexusnode on 2008-11-15
But thats what we have been saying - we can connect to encryptionless wireless networks without a problem.  I personally can even connect to WEP networks fine, its WPA thats a problem...  Thanks for the suggestion though

---

### Post by ckjackson on 2008-11-16
I have had similar problems with an HP 2517cl with the BCM4322 - I am running Intrepid with kernel 2.6.27-8 and ndiswrapper.
 
After reading the workaround at [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/276980](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/276980) which was to disable WPA/WPA2 on the accesspoint and use only WPA, I when to my AP and and found only an option to do "WPA/WPA2" or only WPA2", so I set it to "only WPA2" and NM connected great!

The problem seems to be with driver handling the AP announcing it takes either WPA or WPA2 instead of just advertising only one or the other.

---

### Post by acreech on 2008-11-16
I have been attempting to connect to a 2wire wireless modem for over 4 months now and have just now figured out the problem that I was having. 

On my modem/wireless router setting I had the "Mac Filter" enabled. I went in and disabled this feature and the computer connect up to the wireless router. 

You might check your wireless router settings for a "Mac Filter" and then disable it. 

Best of luck with this.

---

### Post by maria1992 on 2008-11-16
> **ckjackson said:**
> I have had similar problems with an HP 2517cl with the BCM4322 - I am running Intrepid with kernel 2.6.27-8 and ndiswrapper.
 
After reading the workaround at [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/276980](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/276980) which was to disable WPA/WPA2 on the accesspoint and use only WPA, I when to my AP and and found only an option to do "WPA/WPA2" or only WPA2", so I set it to "only WPA2" and NM connected great!

The problem seems to be with driver handling the AP announcing it takes either WPA or WPA2 instead of just advertising only one or the other.


Same as here. It looks like that access point and network 
interface card can't negotiate what they shall use wpa or wpa2.
So forcing the access point to wpa2-psk/aes is working well.
However using wpa-psk/tkip seems to be impossible, unless you 
like annoying questions for the correct password over and over 
again ;-).

System: HP nx6325
kernel 2.6.27-7
broadcom bcm43xx - proprietary driver bt43

---

### Post by brechtvb on 2008-11-16
I also have a crappy problem with 8.10 and intel 3945.

I install ubuntu at my student apartment. Wifi works.
I get home and we have the same wifi router as at my student apartment. Wifi works.
I go back to my student apartment, i cannot get a connection, i see all surrounding networks, but not my own.
I get back home, wifi works.

Windows has no problems.

Tomorrow, i shall post some command outputs.

---

### Post by Olivier2371 on 2008-11-16
Hi there, 

Do you use wpa tkp or wpa automatic?

---

### Post by kevdog on 2008-11-16
If you have the capabilities try using wpa2 with aes due to the recent security exploit that has been advertised with tkip/wpa

---

### Post by stanley drew on 2008-11-16
for what it's worth i am having no problems now that i've set up my router to broadcast only on a particular channel rather than "auto." i have an atheros 5xxx chipset and i'm running 8.10 x86_64 connecting to a wpa2 encrypted network.

---

### Post by t-timmy on 2008-11-16
> **kevdog said:**
> If you have the capabilities try using wpa2 with aes due to the recent security exploit that has been advertised with tkip/wpa

That exploit is not fully effective, but future developments may lead to a functional exploit. Yes, change to wpa2 if u can.

---

### Post by nexusnode on 2008-11-17
Sad to report that forcing to AES, although worthy of a few mins for security purposes - doesn't help my connectivity.  Anyone else better luck?

---

### Post by kevdog on 2008-11-17
What method are you trying to use to connect to your WPA network?

I hope you've tried methods beyond Network Manager!

Will your card connect to an unsecured network?  

Have you tried manually modifying the /etc/network/interfaces file (a method written by weiman01) or as an alternative creating a wpa_supplicant.conf file and then trying to use this in establishing a manual connection from the command line?

What parameters are you using on your router?

What does iwlist scan show?

---

### Post by ~Blissard~ on 2008-11-17
i'v found that but cannot try until this evening :

The problem is the EU channels are not enabled by default. They have to be enabled with the following in /etc/modprobe.d/options:

options cfg80211 ieee80211_regdom=EU

---

### Post by cutOff on 2008-11-17
To all having problems with wpasupplicant package in Intrepid, downgrade to Hardy version: [http://packages.ubuntu.com/hardy/i386/wpasupplicant/download](http://packages.ubuntu.com/hardy/i386/wpasupplicant/download)

Just did the trick.

---

### Post by kevdog on 2008-11-17
Where did you discover or read about the conflict with intel devices and wpa_supplicant?  Ive been unable to find a link thoroughly discussing this.

---

### Post by fogelfink on 2008-11-17
Just to return to the first post of this thread I would like to add that in my case network manager keeps asking for a network key after rebooting and is unable to connect to the network with the given key, even though it is not a WPA, but a WEP connection.
The only way to reconnect is to edit the connections, delete the existing entry and create a new one, which will last for the current session.

---

### Post by iamthemicrowave on 2008-11-17
Hi, I am running the broadcom sta driver for my bcm4311 card, and have had no luck in getting WPA to work yet.  I can connect to unsecure networks, but not my school's WPA(hidden) enterprise network.

Has anyone tried wicd with success?  From gauging the replies this appears to be a kernel problem, and I do not know if wicd would help.  It will be my next troubleshooting option, regardless.  I just want wireless to work...it worked fine in hardy!!

---

### Post by ~Blissard~ on 2008-11-17
It work now, but i'm not change anything...mysterius thing

---

### Post by dhoang417 on 2008-11-17
> **iamthemicrowave said:**
> Hi, I am running the broadcom sta driver for my bcm4311 card, and have had no luck in getting WPA to work yet.  I can connect to unsecure networks, but not my school's WPA(hidden) enterprise network.

Has anyone tried wicd with success?  From gauging the replies this appears to be a kernel problem, and I do not know if wicd would help.  It will be my next troubleshooting option, regardless.  I just want wireless to work...it worked fine in hardy!!

same here. However, 8.04 works fine. I might just go back to it.

---

### Post by nexusnode on 2008-11-18
Hi All, any one any joy yet?

@KevDog - yes I am just using the network manager... I haven't had a chance to really spend much time on this problem over the last few days, but will do eventually.  I kinda still hope we find out a way of getting it to work with the lease amount of butchering the original OS but I guess time will tell...

Although I identified it as probably not working because my chipset is covered by the wl driver I tried installing the linux-backports-modules-intrepid-generic but sadly it didnt make the foggiest of difference.

@cutOff - call me stupid but I can't work out how to downgrade and the how to [here]("http://ubuntuforums.org/showthread.php?t=321156") that I followed suggests to panic if apt-cache doesnt suggest anything sensible... Need I say anymore - please can someone advise.

@~Blissard~ - I have added that line to the /etc/modprobe.d/options file but after a restart its not helped.  To be honest I am fairly sure I am missing a command or two here as this sounds very familiar - am I supposed to "re-modprobe" it or something?

Thanks everyone!!

---

### Post by jshein on 2008-11-19
Using wicd to replace network-manager solved the problem in my environment.

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

sudo apt-get update; sudo apt-get install wicd


JS

---

### Post by Womble2008 on 2008-11-19
I Think I may have solved this one, anyway it works for me

step one
          use network manager to set up the connection as normal
step two
          open "Applications"/"Accessories"/"passwords and encryption keys"
step three
          click on the passwords tab
step four
          click on the entry that starts with the words "network secret"
step five 
          click on the word "password" and enter your network key
I had three entries here for some reason so I changed all of them

and now it works! I have tried rebooting several time and it still works

hope this is a help.
:)

---

### Post by nexusnode on 2008-11-19
Thought I would give your idea a go Womble2008 - sadly didnt do the trick for me.  If I get a chance Im also going to give wicd a try as well shortly...

---

### Post by stanley drew on 2008-11-19
wicd worked for me. i had it in hardy and i'm using it now in intrepid. just beware that it won't start automatically after it's installed, so you have to select it from applications > internet > wicd. it should start up on reboot after that. also it didn't automatically recognize my wireless interface so i had to enter it in the preferences section (wlan0 for me). good luck everyone.

---

### Post by alienseer23 on 2008-11-20
wicd for wep 64 bit hex as well..works like a charm

---

### Post by Womble2008 on 2008-11-20
Sorry my idea did not work. All I can say is this is typed using a dlink router connected using WPA2 on Intrepid

---

### Post by stella_n_ozzy on 2008-11-20
first all, thanks for everyone who has posted and helped with this thread. I just got into linux a couple days ago, so i probably won't be able to provide a thorough explanation.

I have a broadcom 4306 PCMIA card in my laptop.
I have been testing with a Asus WL500w router, Actiontek MI424WR router, and a very cheap rosewill router.

after doing some research into my wireless card's chipset, i followed: _[COLOR="Blue"][https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)[/COLOR]_ to install the Ndiswrapper driver. Yet my card still didn't connect to any of the routers with WPA encryption.

After tweaking the routers, I found that I was able to connect to open wireless networks.  Then after playing with it further, i found i was able to use an open network using WEP encryption with a passphrase.

I prefered to use WPA after reading about how easily WEP is cracked.  I followed Kevdog's link- _[COLOR="Blue"][https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)[/COLOR]_ and reinstalled the Ndiswrapper drivers with the one specified in that guide.

This allowed me to connect to the rosewill router with WPA. (I didn't have the settings available since this was at someone elses house)

Since i knew I could connect to something with WPA, i was determined to get it to work on my new asus router. 

I downloaded WICD since so many people recommended it.  And it did work, but only after alot of router-side tweaking.

First of all, not all the wireless channels work, after some iterations, I found channel 7 to allow for a connection.

Additionally, AES style WPA doesn't work, nor does AES+TKIP, only TKIP works.

so to sum it up, i my situation I required- Ndiswrapper, WICD, channel 7, and TKIP inorder to get WPA to work for me.

Hopefully this helps someone :)

PS- only my asus router connects, i'm too tired at the moment to determine what magic formula the actiontek router needs.

---

### Post by kevdog on 2008-11-21
Stella 

Hmm that seems crazy to me but what the heck do I know?

---

### Post by yipperzz on 2008-11-21
that's funny because i have a 4306 with the asus too.  but it's with the dd-wrt firmware on it.  

i'm able to connect by wpa (tkip) on the asus if i use ndiswrapper.  i have a netgear n router (aes and tkip) and a buffalo g router (tkip) and can't connect to them.  with encryption off, it can connect fine.  

if i use b43legacy i can connect to the buffalo router but the speed is extremely slow.  and i can't connect to anything else.  i'm trying to figure out what's going on but haven't really had too much time to look at it.  

the b43-fwcutter that i installed was from synaptic.  i tried installing the restricted driver and it didn't seem to help.

---

### Post by paolo.pani on 2008-11-21
Hi everybody. It seems that a lot of people (including me!) is having trouble with this.
I tried everything that for some of you worked:

-I changed the wireless channel 
-I changed the Atheros drivers (from 802.11 to 5xxx)
-I installed wicd

None of these helped me. What really make me unpleased is not the bug by itself (it could happen in a new release) but it is the fact the a lot of user are in my same situation and I wasn't able to find any patch or upgrade to solve this important problem. I didn't expect this from a major distribution.

---

### Post by zi0mek on 2008-11-22
I also was having the same problem. Couldn't connect to WPA or WPA2, but WEP worked flowlessly.

Lenovo T400, Intel 5300 Wireless using compat-wireless.

I have changed the setting on my router D-LINK DIR625 to limit my wireless transmission rate to 54Mbit/s and was able to connect to WPA2. I was trying TKIP and AES using WPA and WPA2 as well and it didn't change a thing. As a temporary fix a simple transmission rate limit fixed this issue for me. Maybe this will work for you too. Good Luck!

---

### Post by Patrick404 on 2008-11-22
Yes, the whole world has this problem.
And since sometimes it works for me, sometimes not, I can't even say if it's a driver or knetwork or networkmanager or wpa_supplicant thing. But I strongly think it's wpa_supplicant related!
This howto works for me on my Atheros AR5211 card.
If you don't know your card, go for:
> lspci | grep Ethernet

First of all: It works here. But I went through the hell:

Applications->System->Hardware Settings:
The 5xxx must be disabled
The Atheros Support must be enabled.
Remember that it makes sense to reboot once in a while. The settings seem to take place only after reboots..

lsmod should give NO mention of ath5k, only ath_pci and ath_hal

shoot out knetworkmanager by installing wicd,
installing wicd works easy: Just enable the source:
> [http://apt.wicd.net](http://apt.wicd.net) intrepid extras
and go
> apt-get install wicd
this will remove knetworkmanager and the kde network-manager.

Now a pitfall I found is: wicd and also knetworkmanager need to be fed with the HEX representation of the WPA-passphrase.
For a conversion go:
> wpa_passphrase YOUR_ESSID
and then paste your ascii passphrase. After that you'll get the HEX representation for it.

In wicd make sure, your wlan device is ath0 and not wlan0 (which it is, when you activate ath5k, and it won't switch back from alone, you only see that it's wrong because your scan of networks gives no output). Btw: If you went the ath5k way before, make sure, that ath5k is blacklisted again and ath_pci and ath_hal unblacklisted within the folder /etc/modprobe.d


So to conclude:
DON'T go for ath5k
USE wicd with HEX representation of your wpa-passphrase.

Now I will try some reboots to test the reproducibility of that and come back later.
- Okay, it works!
What I have to say, is that if you position your client so that you get less than 30% reception (should be sth. like -5dB = -35dBm), you will get no association, sadly...


Cheers
Patrick

---

### Post by Chuckels550 on 2008-11-25
I discovered that the support for Atheros wireless chipsets in wpasupplicant has been amalgamated in the wext support.  

If you have an atheros wireless card change the wpasupplicant setting from madwifi to wext.  You should now be able to connect using whatever encryption mode is supported by your wireless nic.

---

### Post by kevdog on 2008-11-25
> I discovered that the support for Atheros wireless chipsets in wpasupplicant has been amalgamated in the wext support.

If you have an atheros wireless card change the wpasupplicant setting from madwifi to wext. You should now be able to connect using whatever encryption mode is supported by your wireless nic.

This isn't exactly a totally accurate statement of what is going on.  It is true that with the Ibex release of wpasupplicant, you need to use the driver wext rather than specifically madwifi as the manual would make you believe.

The reason for this however is that wpa_supplicant was not compiled against the madwifi sources.  If you ever compile wpa_supplicant, you need to compile against source driver files, such as madwifi.  During the configuring of the build you can choose whether to compile against madwifi sources or not.

If you do a 
wpa_supplicant -h

This will list the possible drivers that are compatible with against wpa_supplicant.  Notice by default only wext,atmel,wired are included -- hence this is the reason you can't use ipw,madwifi,broadcom, etc as options.

You could compile wpa_supplicant yourself however and add the capabilities for other drivers.  The reason for the change is that the new version of the Linux wireless extensions (v18) allows driver_wext.c to be used as is without requiring driver
specific changes in wpa_supplicant.


You can specifically compile wpa_supplicant against ndiswrapper and/or madifi or intel sources.  This doesn't need to be done however with the more recent kernel releases, however I thought I would just clarify the record.

---

### Post by nexusnode on 2008-12-03
Bump

---

### Post by t-timmy on 2008-12-05
> **nexusnode said:**
> Bump

Yes.
I'm keeping track of this thread.
I want to thank everyone who've tried to help.

My Ubuntu is still installed but I'm never booting into it because it's useless without wi-fi. I'm still waiting for a solution that involves installing some sort of fix or detailed instructions on how to fix this on my own.

I am a technical user but I don't have much time to spare to dig into this on my own.

Thanks again

---

### Post by flatline on 2008-12-12
I'm not sure if this will help you guys, but I was able to get my WPA-based network working on my Intrepid netbook today.  I used gconf-editor, [_thread here_]("http://ubuntuforums.org/showthread.php?t=1009180"). YMMV - I had the good fortune of having a corporate IT friend willing to help me even though Linux "is not officially supported."  Knowing in detail what the settings *should* be made it easier.  If your aren't quite sure what your parameters need to be it might be trickier.

---

### Post by readams on 2008-12-12
Same problem here.  Can't use WPA with PEAP at work.  Worked fine with hardy before upgrade.  I tried booting from a hardy live CD and connected just fine.  Booted with intrepid live CD and utter failure.

I tried editing the gconf settings as shown above but this had no effect.

This seems to be such a widespread issue I'm shocked that nobody has any solution at all for it.

---

### Post by readams on 2008-12-12
Also, I had no luck getting it to connect using wpa_supplicant directly, bypassing network-manager.  This sounds like a kernel issue.

---

### Post by Favux on 2008-12-13
Eureka!

Flatline's advice works!  For the first time since updating to Intrepid I have wireless!

I went to gconf editor Applications>System Tools>Configuration Editor.  Then I went to system>networking>connections>1>802-11-wireless-security.

There I saw:
```
group       [wep40,wep104,tkip,ccmp]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip,ccmp]
proto       [wpa,rsn]

```

I edited it to look like:
```
group       [tkip]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip]
proto       [wpa]
```


And tried to connect, and it did!  I rebooted and tried to connect again.  And it did.  I had decided this was a wpa_supplicant certificate issue and was hoping for a network manager update that would fix it.   I just guessed at the parameters, knowing what I had set up in my router.  Surprise, surprise.

Thank you flatline.

---

### Post by Favux on 2008-12-13
Fascinating!

I right clicked on the Network Manager applet and went to Edit Connections.  I then deleted a duplicate entry and checked the box for automatically connect, since the connection now worked again.  I rebooted and the connection failed.  Again the password box filled with hex.  Again the asking for a password and reconnection.  I went back go Gconf editor and found:
```
group       [wep40,wep104,tkip,ccmp]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip,ccmp]
proto       [wpa,rsn]
```
I again started editing, and after correcting the second line it automatically connected and so I was left with:
```
group       [tkip]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip]
proto       [wpa,rsn]
```
I rebooted and it connected automatically and flawlessly.

Think about it for a minute.  Just going into Edit Connections and checking the auto-connect box was enough for Network Manager to re-add the extraneous, and some clearly erroneous, entries.  Boy is Network Manager messed up!

So as long as I don't use Network Manager to edit connections I'm good to go?  I suppose I could experiment further and find out just which of the extraneous entries are the erroneous ones.  But I don't want to.  Having wireless again is just too precious and new to further mess with.

---

### Post by Favux on 2008-12-13
Further thoughts,

In Gconf editor if you right click a key there are several options.  Among them are "set as default" and "set as mandatory".  If I selected one of these two options for the keys that NetworkManager is messing up would this prevent it?  In other words could one or the other of these settings block NetworkManager from altering the key?  If so which one?  I don't know enough about Gconf editor and what these options do to risk it.

Any help would be appreciated.

---

### Post by mickey57 on 2008-12-13
[SIZE="5"][COLOR="DarkRed"]:guitar: Thank You..Worked like a charm:biggrin:
So follow these steps:
1) In Synaptic or trough apt-get install the linux-backports-modules-intrepid-generic package.
e.g:
Code:

sudo apt-get install linux-backports-modules-intrepid-generic

2)I reboted now in order the new driver for wireless card was found
3) After reboot my wifi card still didn't work so I went to the Driver Menager (I have kubuntu so it is in Programs-> system -> Drivers) - I have found that there are two drivers used at the same time:
-Suport for 5xxx series of Atheros 802.11 wireless LAN cards
-Suport for Atheros 802.11 wireless LAN cards

4) I have turned off the latter and left only the first one (for 5xxx serie)

5) I rebooted again and surprisingly wifi card stared working without further intervention.
[/COLOR][/SIZE]
*-network
description: Wireless interface
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:14:00.0
logical name: wmaster0
version: 01
serial: 00:xx:xx:xx:xx:xx
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath5k_pci ip=192.168.x.xx latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

---

### Post by eyefragment on 2008-12-15
I haven't read through this full thread, but I installed wicd and it allows me to connect using WPA2 encrpytion.  One thing I did need to modify in wicd was to change "use passphrase" to "use preshared key".  Is it possible that gnome network manager is having a similar problem?  I didn't see anywhere in network manager that allowed me to choose which of the two I was using (admittedly, I don't know the difference between the two)...

---

### Post by foresto on 2008-12-15
> **transmition said:**
> Well, this isn't a solution, but I have experienced the same problem and this is what I noticed:

It prompts me for wireless password, which is a string of random letters and numbers. I enter it and try to connect. After some time, it prompts me again, this time with my password already typed in. I figured that I had made some type of spelling error, so I click the option to reveal password. To my shock, I see that it has been replaced with a completely different string of letters and numbers. 

I suspect that the network manager is not recording our passwords properly, and thus times out because it gets rejected by the router.

That reminds me of the problem I had.  In my case, it was with WEP (not WPA).  The Network Manager applet allowed me to enter an ASCII key, but it seemed to convert it into binary values in some way that didn't match the access point's conversion.  It didn't tell me that the field it offered was not for ASCII keys (though they are used in the world), and it didn't tell me that they key I entered (which I knew was correct) had failed authentication.  Switching to a hex key on both the access point and the computer worked around the problem.

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/269534](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/269534)

---

### Post by Favux on 2008-12-15
Hi foresto and transmition,

The network manager problem with WPA passwords is exactly the problem flatline (and I) posted a solution to above.  foresto, even in the first post in the bug report you refer to he fixes (or works around) his problem using gconf.

I aggregated my results in a "demo" at:

   [http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

on the first page.  I'm not claiming to know the exact terms to edit in each case, not knowing enough wireless stuff.  But I hit it on my first attempt.  So it can't be that hard (if I could do it)!

This seems to be a way to work around whatever the problem in networkmanager is.

---

### Post by Hercynium on 2008-12-17
This worked for me, THANKS!!!

Update: I had installed linux-backports-modules-intrepid-generic and changed my driver to ath5xxx.
 
After rebooting everything seemed great, but then I noticed the connection getting slower and slower, until it was unusable.

I rebooted again and got a great connection... but it degraded the same way.


I only started having these problems since I upgraded to (then installed clean) Intrepid Ibex from Hardy. This and some other (minor) issues have made Intrepid quite a disappointment for me... I'm on the verge of wiping my root partition and re-installing Hardy! :(

---

### Post by Favux on 2008-12-17
Hi Hercynium,

Do you mean the gconf editor work around in the "demo"?  If so great!  Nice having wireless again, huh?

---

### Post by Hercynium on 2008-12-17
Nope... where can I get instructions for trying that?

---

### Post by Favux on 2008-12-17
Hi Hercynium,

Post #106 above.  Doesn't sound like you're having the same problem though.

---

### Post by madsmaddad on 2008-12-18
I need to go through all the posts here. I jumped to end to get my two-bits in. I have two wireless USB cards. I installed Intrepid from CD on one PC, and it found everything and worked. One click to input WPA key. 

My main PC running 7.1 I did an over-the-Internet upgrade, and now the wireless does not work. Under 7.10 I was using Wpa_supplicant. 

Bit stuffed because of Catch 22. No wireless so cannot download any fixes.

---

### Post by madsmaddad on 2008-12-19
Sorted. Thanks to all you guys. I did a ps -ef|grep wpa and found a number of wpa files.

I looked through my notes from when I got wpa supplicant working under 7.1, and found that I had created an rc.local file in /etc that ran at startup and ran all the commands to start the wireless config. I deleted this file and rebooted, and lo, I am writing this from Kubuntu.

One happy guy.

It was just a matter of the system having a conflict because the wireless  was already configured, and I had to get rid of the old configuration. 


mmd.

---

### Post by madsmaddad on 2008-12-21
Don't do it, as said above. Today it didn't work. and Hung KDE4 with a message 'could not start KSMserver' 

Square 1 again.

---

### Post by madsmaddad on 2008-12-21
Don't do it, as said above. Today it didn't work. and Hung KDE4 with a message 'could not start KSMserver' 

Square 1 again.

mmd

---

### Post by t-timmy on 2008-12-21
Tried to edit the configurations like someone suggested (gconf-editor), but it didn't solve it.

---

### Post by nexusnode on 2008-12-22
Just at a friends, they have sky internet and their b/g only routers come with an 8 char wpa key on the bottom, just thought i would try it and it works flawlessly with no changes...  Is it something to do with draft N stuff?

---

### Post by thread_au on 2008-12-22
My router is b/g only as well, and I still have issues.

---

### Post by nexusnode on 2008-12-23
perhaps something to do with the character sets in the key?  Length of key maybe?

Here its an 8 char code with uppercase letters and numbers at home I have a 63 char code with upper lower numbers and specials.

is it WPA vs WPA2/TKIP vs AES?

---

### Post by fx78 on 2008-12-25
> **~Blissard~ said:**
> i'v found that but cannot try until this evening :

The problem is the EU channels are not enabled by default. They have to be enabled with the following in /etc/modprobe.d/options:

options cfg80211 ieee80211_regdom=EU

Just wanted to confirm that this solved all my problems ! \\:D/
Wireless was Intel 4965AGN
Symptoms: 
Not all access points visible in the list (I assume only access points that are on a frequency that is the same in US and EU are visible) and networkmanager kept prompting me for my password

---

### Post by nexusnode on 2008-12-26
> options cfg80211 ieee80211_regdom=EU

I will try it when I get home - just to be sure though, what do I do with that line, add it to the bottom of this file:

/etc/modprobe.d/options

---

### Post by t-timmy on 2008-12-26
> **nexusnode said:**
> I will try it when I get home - just to be sure though, what do I do with that line, add it to the bottom of this file:

/etc/modprobe.d/options

I did exactly that and, even after rebooting, problem remains.
No wireless in Ubuntu.

---

### Post by fx78 on 2008-12-27
Just appending the line to /etc/modprobe.d/options should be fine (reboot afterwards) If you are using a different wireless chipset it might explain why it's not working

---

### Post by lurchnz on 2009-01-06
Well after trying everything this thread and a few things that I found via Google I managed to get connected once with 8.10 I then restarted and it was back to the same tricks prompting for the WPA key. 

I decided to try Ubuntu 9.04 (Jaunty Jackalope) same issue, constantly asking for the WPA key. So wiped everything off and have gone back to 8.04.1 and guess what it connects first time with no issues.

After googling this issue I can see that several people are affected by this issue. So going to be staying with 8.04 until they can sort the problem.

---

### Post by t-timmy on 2009-01-11
Just thought about linking to a suitable bug I've found in Launchpad, just for consistency:

[https://bugs.launchpad.net/bugs/299822](https://bugs.launchpad.net/bugs/299822)

I'm trying to install 8.10 on another machine just out of curiosity, I'll post here the results...

---

### Post by t-timmy on 2009-01-18
> **t-timmy said:**
> Just thought about linking to a suitable bug I've found in Launchpad, just for consistency:

[https://bugs.launchpad.net/bugs/299822](https://bugs.launchpad.net/bugs/299822)

I'm trying to install 8.10 on another machine just out of curiosity, I'll post here the results...

Wasn't able to install on another machine, Wubi troubles.
BUT, I did run in the exact same problem with a 8.04 installation, which I solved. More info here: [http://ubuntuforums.org/showthread.php?p=6573880#post6573880]("http://ubuntuforums.org/showthread.php?p=6573880#post6573880").

---

### Post by sergueik on 2009-01-18
You all need to try switching fro Netwok-Manager-Gnome (comes standard with Ubuntu) to Wicd network Manager (available from repository). See my post in here,

[http://ubuntuforums.org/showthread.php?t=1024731&highlight=ideapad]("http://ubuntuforums.org/showthread.php?t=1024731&highlight=ideapad")

---

### Post by tegnoto89 on 2009-01-18
Ughh this issue gave me such a hard time.  I finally gave up and downgraded to Hardy - all problems solved.

---

### Post by vsound on 2009-01-20
Awesome, it worked for me. You saved my day, thanks a lot!

Edit: It apparently dint, after several updates. I dont know which kernel broke, but nothing works for me now :(.

---

### Post by Sportingfan on 2009-01-20
I 've got the same issue. I was thinking of installing 8.04, so tried the live cd which couldn't connect to wireless either.

Would it be possible to downgrade network manager-applet to the previous version?!

Wicd didn't work for me. I've also got a thread here: [http://ubuntuforums.org/showthread.php?t=1045143](http://ubuntuforums.org/showthread.php?t=1045143)

---

### Post by t-timmy on 2009-01-20
> **vsound said:**
> Awesome, it worked for me. You saved my day, thanks a lot!

What worked for you? Changing network managers or the thread I posted about upgrading router's firmware?

---

### Post by Sportingfan on 2009-01-20
I tried installing Network manager 0.6.5 and 0.6.0 but there were some errors while compiling.

I'm going to try hardy in combination with wicp.

---

### Post by Fudoublez on 2009-01-20
I'm having problems with authentication as well. It used to work fine untill I flashed my rother with dd-wrt. My Windows box is running it fine and this machine works w/o encryption.

Im using ndiswrapper and wiicd with a Zonet ZEW1602. What could have changed other than just the router firmware?

---

### Post by meirellm on 2009-01-20
This was driving me nuts. I have Windows, Wii, iPod, iPhone, Blackberry, Mac, Chumby all connecting to my WPA and my notebook wasn't... 

New Ubuntu user... Using 8.10. Old IBM T30. Ailink G card.

Read every thread and tried all suggestions under the sun... This is what I figured out...

With Network Manager I could not connect right away. If I tried 5-10 times it would eventually connect to my network.

Removed Network Manager and installed wicd. Rebooted, made sure that wicd was working ok.

Open my password manager. There were 7 entries for my network there probably from all my tries. Deleted all. Rebooted just for the heck.

Open wicd and setup my network to connect automatically.

Connected right away and have been connecting ever since.

Not technical enough but it seems that Network Manager is writing too many entries on password manager and somehow things get messed up because of that.

---

### Post by Favux on 2009-01-21
Hi Fudoublez and meirellm,

You might want to look at:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

Or look at flatline's post (#97) on this thread, and my answers starting on #100.

The authentication issue is not necessarily the same bug.  hasinasi has a fix for that at the end of the thread linked above.  He backports NM from Jaunty.  I can't tell if that's any different from Alexander Sack's ppa of NM (0.7 final) linked on the HOW TO.

---

### Post by Sportingfan on 2009-01-21
> **Sportingfan said:**
> I 've got the same issue. I was thinking of installing 8.04, so tried the live cd which couldn't connect to wireless either.

Would it be possible to downgrade network manager-applet to the previous version?!

Wicd didn't work for me. I've also got a thread here: [http://ubuntuforums.org/showthread.php?t=1045143](http://ubuntuforums.org/showthread.php?t=1045143)

I Solved my problem. See the thread I created.

Success to everybody who's struggling with these wireless issues.

---

### Post by James_Kube on 2009-02-03
I'm a newb when it comes to Linux, and am not sure/have not checked to see if this is a fix for Network Manager not being able to authenticate with WPA/WPA2, but this fix works for WICD:

Essentially all you have to do is enable SSID broadcast on your router.  Again, this worked for me using WICD on an Asus Aspire 5515; not sure of what affect it will have on a system running Network Manager.

[https://bugs.launchpad.net/wicd/+bug/244095](https://bugs.launchpad.net/wicd/+bug/244095)

LOL, of course, me being me and being all psched over getting back onto the inter-web, I didn't read over everyone's post in detail...

This fix works, but is far less elegant than other methods posted before.

---

