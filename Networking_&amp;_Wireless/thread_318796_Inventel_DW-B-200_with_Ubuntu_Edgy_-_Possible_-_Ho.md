---
title: "Inventel DW-B-200 with Ubuntu Edgy - Possible? - How?"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by 2CV67 on 2006-12-14
Hi Network & Wireless Forum!

I posted on Absolute Beginners forum (where I REALLY belong) but after a few tries, they sent me over here for a more-expert diagnosis...
...or just to get rid of me?

Please forgive me if I sound as though I don't fully grasp either Linux or WiFi - that's where I am today, but I am trying.

I have been using WiFi with XP/SP2 for a couple of years now, with no real problems, but without needing to understand much of what was going on.
Now I have just installed Ubuntu 6.10 Edgy on the same PC in dual-boot configuration & Ubuntu & XP seem to work OK except no WiFi with Ubuntu.

My WiFi is:
Tiscali/Inventel DW-B-200 ADSL modem 
WEP security
WLAN Dongle is PQP-WU221L S/N24W0097350.
I think Windows sees it as: ATMEL USB FastVNET(505A)

I assume (but that’s dangerous for me) that the first step in diagnosis is to check if Ubuntu can see the Dongle?

Should I be able to see something under: System > Administration > Device Manager & if so, what should it look like?
I see “RTL-8139….” & under that “Networking interface” but nothing that sounds like ATMEL or anything.

Following leads given in the Beginner's forum, I went to:
System > Administration > Networking > Network Settings > Wireless Connection > Properties:
I Ticked “Enable the connection”
Network name (ESSID): I put DW-B-200-3d555
Network password: I put the 26-digit WEP key
Password type: Hexadecimal
Configuration: Automatic Configuration (DHCP)
Click “OK”

System > Administration > Network Tools > Devices > Network device….
Select “Wireless Interface (wlan0) : the “Configure” button stays grayed out & all the information is blank or 0. 

iwconfig gives:
:::::::::::::::::::::::::::::::::
[I]chris@salon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"DW-B-200-3d555"  Nickname:"DW-B-200-3d555"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality=0/0  Signal level=55/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.[/I]
::::::::::::::::::::::::::::::::::::::

I downloaded (via XP) & installed "wifi-radar_1.9.7-0ubuntu2_all.deb" but when I run it, it does not find any signals (I assume??) as it's screen stays blank with just a remark underneath:
"Connected to  DW-B-200-3d555 ip(192.168.1.9)" which looks encouraging! - see attached 1

Without really knowing what I was doing, I tried "forcing" a connection in WiFi-Radar by "Disconnect" & "New" - adding whatever info I could (maybe wrong...).
This produced a pretty screen in WiFi-Radar - attached 2 - but no other progress.

I have read enough threads & sites to realize that Ubuntu & USB WiFi do not go together well, & seen a lot of "Inventel/Linux" threads which seem to peter out with no solution, but I still would like to think it was possible...

Can anybody help?
...in simple terms if at all possible!

Thanks Guys!

---

### Post by 2CV67 on 2006-12-16
Nobody there? :(

---

### Post by tturrisi on 2006-12-16
post the results of:
~# lsusb

also, try using Administration > Networking > select the wifi adapter > Properties > enter ssid, Hexadecimal, wepkey & see if can connect.

---

### Post by 2CV67 on 2006-12-16
Delighted to know there IS somebody there!
Thanks for taking the trouble to deal 'blind' with somebody 'dumb'!

1. Here are the results of lsusb (looks promising to me, I see Atmel...)
:::::::::::::::::::::::[I]
chris@salon:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:0029 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 002: ID 03eb:7614 Atmel Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 1019:0c55  
Bus 001 Device 004: ID 03f0:0805 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
chris@salon:~$ [/I]
:::::::::::::::::::::::::::::

2. I already had been through your suggested: *"Administration > Networking > select the wifi adapter > Properties > enter ssid, Hexadecimal, wepkey"*

I just rechecked that I had all that, but still no connection, as far as I can see.

Open for all suggestions...

---

### Post by 2CV67 on 2006-12-17
Following some blind poking around, for some reason "Device Manager" now sees the WLAN Interface, which it did not earlier.

There is lots of information under the "Detail" headings (see attached).

Is this good news or bad?

I still have no connection.  :(

---

### Post by tturrisi on 2006-12-17
OK, now do:
lsmod
and post results, need to see if the actual wifi driver is loaded.  (probably is)
Also, go back to Admin>Networking and setup the wifi as you did earlier, but this time use a hypen AFTER EVERY 4 wep characters:
xxxx-xxxx-xxxx-xxxx-xxxx-xxxx etc

if no joy, disable wifi security at router/access point, resetup the wifi again in Networking & try to connect using the ssid, Plain (ascii), dhcp.  Then try w/ 64 but wep, and so on...

---

### Post by 2CV67 on 2006-12-17
Thanks for your continuing interest!

Here is the output from lsmod:

:::::::::::::::::::::::::::[I]
chris@DESKTOP:~$ lsmod
Module                  Size  Used by
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
radeon                118816  3 
drm                    74644  4 radeon
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
nls_iso8859_1           5248  2 
nls_cp437               6912  2 
vfat                   14720  2 
fat                    56348  1 vfat
sg                     37404  0 
sd_mod                 22656  1 
sbp2                   24584  0 
lp                     12964  0 
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            30360  1 
gameport               17160  1 snd_via82xx
snd_ac97_codec         97696  1 snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
tsdev                   9152  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
af_packet              24584  2 
i2c_viapro              9876  0 
snd_pcm                84612  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_seq,snd_pcm
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart        10240  1 snd_via82xx
i2c_core               23424  2 i2c_ec,i2c_viapro
snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
usb_storage            75072  1 
scsi_mod              144648  4 sg,sd_mod,sbp2,usb_storage
via_ircc               28948  0 
psmouse                41352  0 
pcspkr                  4352  0 
usbhid                 45152  0 
irda                  214332  1 via_ircc
snd                    58372  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
at76c505a_rfmd2958      5900  0 
at76c503               92896  1 at76c505a_rfmd2958
at76_usbdfu             6532  1 at76c503
evdev                  11392  1 
serio_raw               8452  0 
libusual               17040  1 usb_storage
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
floppy                 63044  0 
soundcore              11232  1 snd
crc_ccitt               3200  1 irda
via_agp                11264  1 
agpgart                34888  2 drm,via_agp
8139cp                 24832  0 
8139too                29056  0 
mii                     6912  2 8139cp,8139too
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  9 usb_storage,usbhid,at76c505a_rfmd2958,at76c503,at76_usbdfu,libusual,ehci_hcd,uhci_hcd
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  5 
via82cxxx              10500  0 [permanent]
generic                 5764  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
chris@DESKTOP:~$ [/I]
:::::::::::::::::::::::::::::::

Hope this means more to you than it does to me!
What does it indicate, for this problem?

I tried separating the WEP key with dashes, but it did not seem to make any difference, positive or negative.
I also did the same in WiFi-Radar > Edit, again with no perceptible effect.
Should I leave all those dashes in, or remove them, before going further?

I guess I will wait for those answers before trying your further suggestions....

Thanks again!

---

### Post by tturrisi on 2006-12-17
It appears that the driver is not loaded.  Run Synaptic, enable the multi-universe repositories, search for atmel-firmware & install it.

---

### Post by 2CV67 on 2006-12-17
Yeah - that's the whole problem.
I can't run Synaptic because I don't have internet access from Ubuntu (can I ?).
Ubuntu is dead in the water until I can get WiFi up...

So far, I have had to download stuff (like WiFi-Radar) through XP then shift it to Ubuntu then try to install it manually, which is stretching my current competence somewhat & presumably prone to errors.

All that stuff under "Device Manager" a couple of posts back did not indicate a driver was present then?
Quote: "*info.linux.driver...strlist...at76c505a-rfmd2958*" etc...
I see long lists, but they don't mean anything to me yet.

Without internet from Ubuntu, how should I approach getting this driver & whatever else is needed?

Sorry to sound negative, but I have been at this for a week now, and at my end, everybody is telling me to just forget Linux until it gets more user-friendly!

I don't want to give up!!

---

### Post by tturrisi on 2006-12-17
get the deb here:
[http://rpm.rutgers.edu/repository/ubuntu/pool/multiverse/a/atmel-firmware/](http://rpm.rutgers.edu/repository/ubuntu/pool/multiverse/a/atmel-firmware/)
Can't you connect via a wire, at least to use synaptic?

---

### Post by 2CV67 on 2006-12-17
Thanks for that spoon-feeding! Much appreciated!

I have been resisting the wire solution as it means moving furniture etc (desktop PC half a house away from phone point - that's why I use WiFi) and because getting WiFi up was my first priority, exactly so I could then use Synaptic for all the other things - I never imagined it could take so long or be so obscure.

If I don't get a breakthrough soon I shall have to reconsider that & try wire.

On the other hand, if WiFi is not going to work anyway, then there is no point in spending further time on it...
It has been frustrating not knowing whether I have a fatal incompatibility or just a couple of typos.

OK - I am off to see the link you so kindly sent.

Thanks!

---

### Post by tturrisi on 2006-12-17
OH, I thought you had a laptop!
Anyway, go out and get a 50' or 100' cat5 cable for a few bucks...I have a few laying around plus a box w/ a thousand feet left...

---

### Post by 2CV67 on 2006-12-17
I'll try wire tomorrow (I'm in Europe - it's night) but still need to get WiFi up.

In the meantime, I downloaded "*atmel-firmware_1.3-2_all.deb*" and installed it (I hope).
I have not noticed any difference, inspite of firing up the modem then the PC etc.

Here are the logs from trying to install & from re-runnung lsmod.

Does this suggest I now have the driver loaded, or still not?
I looked all through, but could not see anything obviously new...

::::::::::::::::::::::::::
[I]chris@DESKTOP:~$ cd Desktop
chris@DESKTOP:~/Desktop$ sudo dpkg -i atmel-firmware_1.3-2_all.deb
Password:
Selecting previously deselected package atmel-firmware.
(Reading database ... 88208 files and directories currently installed.)
Unpacking atmel-firmware (from atmel-firmware_1.3-2_all.deb) ...
Setting up atmel-firmware (1.3-2) ...

chris@DESKTOP:~/Desktop$ 

chris@DESKTOP:~$ lsmod
Module                  Size  Used by
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
radeon                118816  2 
drm                    74644  3 radeon
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
nls_iso8859_1           5248  2 
nls_cp437               6912  2 
vfat                   14720  2 
fat                    56348  1 vfat
sg                     37404  0 
sd_mod                 22656  0 
sbp2                   24584  0 
lp                     12964  0 
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
af_packet              24584  2 
snd_via82xx            30360  1 
gameport               17160  1 snd_via82xx
snd_ac97_codec         97696  1 snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
tsdev                   9152  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
usb_storage            75072  0 
scsi_mod              144648  4 sg,sd_mod,sbp2,usb_storage
snd_pcm                84612  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_seq,snd_pcm
snd_page_alloc         11400  2 snd_via82xx,snd_pcm
snd_mpu401_uart        10240  1 snd_via82xx
at76c505a_rfmd2958      5900  0 
at76c503               92896  1 at76c505a_rfmd2958
at76_usbdfu             6532  1 at76c503
snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
libusual               17040  1 usb_storage
usbhid                 45152  0 
psmouse                41352  0 
snd                    58372  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
serio_raw               8452  0 
floppy                 63044  0 
evdev                  11392  1 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
soundcore              11232  1 snd
i2c_viapro              9876  0 
pcspkr                  4352  0 
i2c_core               23424  2 i2c_ec,i2c_viapro
8139cp                 24832  0 
8139too                29056  0 
via_ircc               28948  0 
mii                     6912  2 8139cp,8139too
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
via_agp                11264  1 
agpgart                34888  2 drm,via_agp
irda                  214332  1 via_ircc
crc_ccitt               3200  1 irda
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  9 usb_storage,at76c505a_rfmd2958,at76c503,at76_usbdfu,libusual,usbhid,ehci_hcd,uhci_hcd
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  5 
via82cxxx              10500  0 [permanent]
generic                 5764  0 
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
chris@DESKTOP:~$[/I] 
:::::::::::::::::::::::::::::::::::::::::

Thanks for your patience!  :)

---

### Post by tturrisi on 2006-12-17
these are the atmel modules:

at76c505a_rfmd2958 5900 0
at76c503 92896 1 at76c505a_rfmd2958
at76_usbdfu 6532 1 at76c503

---

### Post by jbutler12 on 2006-12-19
I am by no means an expert at this, but having just spent literally 30 hours pouring over docs and wiki to get my Belkin USB wireless to work, i have a few thoughts.

First, can you run
```
iwlist wlan0 scan
```  
and post the results?  If this correctly scans and finds nearby networks, ive found that the problem is most likely in your internet setup as opposed to your device setup.  The reason i say this might be the case is you are getting a signal strength in your iwconfig.  I misspent a while because my device was working fine but my box's internet configuration was all screwed up.

-John

---

### Post by 2CV67 on 2006-12-19
John - you are 100% right! :D :D :D 

I did not run iwlist, but I just switched back from Ethernet (after spending some hours  getting that running) to WiFi & it all chimed in right away!

Obviously (in hindsight) the fiddling I had to do to get Internet connected under Ethernet was what was missing to get through in WiFi too, at least in the final stages.

This was stuff about "Type of Authentication" & "Password type" & "SSL Encryption" etc - none of which looks like the corresponding items in XP...

My "lessons learned" after a week of pretty full-time forum & Googling is that it is preferable to set up Internet connection & mail accounts by Ethernet first, before venturing into WiFi. 
Thanks for that suggestion tturrisi !!

The other conclusion is that the Inventel/Atmel WU221L dongle works just fine in Ubuntu.
Should be added to a list somewhere?

I also learned that there are a lot of very helpful people on these forums, thanks to you all :-D  
but that finding clear, simple, absolute-beginner-level instructions on websites is...well...lacking. :( 

If Ubuntu really wants to attract & keep non-geeks (& I think it does, and deserves to) then somehow there needs to be some effort put into beginner-level manuals, without too much control-line manipulation.

So - all's well that ends well :D  - Thanks again!

---

### Post by tturrisi on 2006-12-19
> My "lessons learned" after a week of pretty full-time forum & Googling is that it is preferable to set up Internet connection & mail accounts by Ethernet first, before venturing into WiFi.
Thanks for that suggestion tturrisi
You're welcome.  Hehe, I learned that lesson many years ago doing windows installs and network  setups.  Even now on my laptop, whenever I do a debian net install, I use ethernet to install the system and setup the wifi after I make all my other configs. (plus, ethernet is 100%+ faster than wifi)

---

### Post by 2CV67 on 2006-12-20
Spoke too soon again!

No WiFi today... (in Ubuntu, I mean - it's perfect in XP).

Went via ethernet again - OK.

Back to WiFi - still nothing!
Well, WiFi Radar looks good, with IP & Signal strength, but WLAN stays at flashing green LED & never gets to steady green, so I can tell it has not hooked the modem.
Not even with the modem within 2ft of the WLAN...

I don't think I have changed anything & all the wlan0 & account settings look OK, but no cigar!

I suppose delete all the settings & start again, but without much hope?

Are there some diagnostic checks I can run to pin down where the problem is/isn't ?

All suggestions welcome. :(

---

### Post by 2CV67 on 2006-12-20
Can anybody explain the contradictory indications between WiFi-Radar & the LEDs on my WLAN? (as of today).

Under XP, the LEDs behave as follows:
Red: 
- Starts as soon as mains power up to PC & stays on as long as power to PC, whether PC is switched on or off.
Green Flashing: 
- Starts during boot at about same time as log-in screen.
- Seems to indicate WLAN is looking for modem?
- XP "wireless network" ikon stays crossed out.
- Stays like this if modem not powered up.
Green Constant: 
- Starts spontaneously (from flashing condition) after a few seconds, even if log-in screen untouched (when modem plugged in, of course).
- Seems to indicate WLAN is talking to modem, but not indication of internet connection?
- XP wireless network ikon indicates "connected".
- Stays like this even if ADSL lead between modem & phone line is unplugged.

Corresponding pings seem to be:
All working: 127.0.0.1 & 192.168.1.9 & 192.168.1.1 & 212.129.9.68 & [www.ubuntu.com](www.ubuntu.com)
ADSL unplugged: 127.0.0.1 & 192.168.1.9 & 192.168.1.1
Modem unplugged: 127.0.0.1 & 192.168.1.9
WLAN unplugged: 127.0.0.1

Under Ubuntu (today):
Red: As above
Green Flashing: As above (except XP ikon). This is as far as I get, whatever I do. Strangely, it stays flashing even after "Quitting" the PC, until I cut the mains power...
Green Constant: Never see it (today).

On the other hand, WiFi-Radar has a signal-strength indicator (all-or-nothing? gray = no? blue = yes?) and this starts gray when I open WiFi-Radar, which soon finds IP(192.168.1.9) and then switches to blue.
If I unplug & replug the modem, the indicator in WiFi-Radar duly goes gray & then blue again, as though it was really indicating connection to the modem.
Ubuntu pings are limited to 127.0.0.1 & 192.168.1.9

So it seems to me that the LEDS & pings are telling me Ubuntu is not connected to the modem, but WiFi-Radar is telling me I am connected?

Any explanation & any suggestions please?

I also ran iwlist wlan0 scan, as suggested yesterday & the results are:
[I]chris@DESKTOP:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:90:4B:84:34:15
                    ESSID:"DW-B-200-3d555"
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Quality:0/0  Signal level:18/255  Noise level:0/0
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s[/I]

Interpretation, anybody?

---

### Post by tturrisi on 2006-12-20
I believe the problem is the modem.
Not a problem, per se, but the cause of the issue.
When you connect a modem directly to the comp, it associates with the mac address of the adapter being used, UNLESS the modem also has a built in router that uses dhcp.  Just like a modem associates itself w/ the mac address of a separate router that uses dhcp.  Try rebooting the modem when in linux and see if issue resolves.

What I would do is uninstall wifiradar completely, reboot and try to connnect using net-admin (administration>networking> and start from scratch.  The drivers you need are the correct ones and they are loading properly.  There's something else "in the way".

---

### Post by 2CV67 on 2006-12-21
Quote *" When you connect a modem directly to the comp, it associates with the mac address of the adapter being used, UNLESS the modem also has a built in router that uses dhcp. Just like a modem associates itself w/ the mac address of a separate router that uses dhcp"* .... 
...Sorry, that still goes goes over my head despite lots of browsing. I do believe my modem has a built-in router that uses DHCP, since part of it's "System Info" print out includes Start & Finish DHCP server IPs (192.168.1.9 & 200). Also the XP Wireless Connection ikon tells me Addresses are attributed by DHCP server.
But this DHCP business is maybe important - see below...

Anyway - back in Ubuntu-land, I have rebooted the modem in Linux (& vice-versa & simultaneously) dozens of times, with no effect.

I just uninstalled WiFi-Radar. So now I have no visual indication of connection or signal strength - in XP I have one by XP ikon & one by Inventel ikon... By the way, I saw that the WiFi-Radar signal indicator was NOT all-or-nothing, it was indicating usually 4/4 & sometimes 3/4.

I scrubbed my Wireless Connection in Admin > Networking.
I re-introduced SSID & Hexadecimal & WEP key & DHCP (like in XP).
At this point, looking in Admin > Network Tools, the wlan0 information has dissappeared & the "Configure" button is grayed out.
Firefox does not connect.
WLAN is desolately flashing green, as always.

In Networking > Wireless Connection, I tried shifting from DCHP to Static & entered some IPs (192.168.1.9 & 255.255.255.0 & 212.129.9.68) as before.
At this point, in Network tools, the wlan0 information is present again & the "Configure" button brings me to the same screen I filled in under Networking.
But Firefox still does not connect & WLAN still flashes.
...even after a modem re-boot, to make sure.

Next suggestion please?? 

I sure appreciate & really need the help - thanks!

---

### Post by tturrisi on 2006-12-21
disable wifi security on the router-modem & try connecting.
in Networking enter:
ssid
plain (ascii)
dhcp

---

### Post by jbutler12 on 2006-12-21
Hi,

As I asked before, can you run:

iwlist wlan0 scan

and post the results?  Dont use the GUI tools, they (believe it or not) complicate things.  We'll take this step-by-step.  If iwlist wlan0 scan gives you a list of networks, then we know your driver is properly loaded and your wifi card is basicly working on your computer.  Then we test to see if your interface is loading properly (wlan0), etc...  So, run "iwlist wlan0 scan" and we'll do this step-by-step making sure everything is working alon gthe way.

-John

---

### Post by 2CV67 on 2006-12-21
Hi John!

I posted the results of iwlist... in post #19, but here they are again (this was yesterday, with WiFi-Radar still present & WEP still enabled):

[I]chris@DESKTOP:~$ iwlist wlan0 scan
wlan0 Scan completed :
Cell 01 - Address: 00:90:4B:84:34:15
ESSID:"DW-B-200-3d555"
Mode:Master
Channel:11
Encryption key:on
Quality:0/0 Signal level:18/255 Noise level:0/0
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s[/I]

Hope this means something to you...

Thanks!

---

### Post by 2CV67 on 2006-12-21
tturrisi - I also tried your suggestions in post #22

I was not able to directly disable the WEP security, there is no obvious option for that - only by wiping out the 26-digit code, which it did not like, but accepted at 3rd attempt.

Then in Networking I set ESSID & plain (ascii) & DHCP.
After that, in Network tools > wlan0 there is no data & "config" button is grayed out...

No Firefox internet access & WLAN stays flashing.

In this condition, I was unable to hook up from XP either, as the Inventel screen which runs the connection asks for WEP code & will not accept blank answer.

My kid's laptop (XP), which normally connects OK & has standard XP connection controls, was also unable to hook up to modem, even after we switched off the WEP for that connection.

So basically I am not sure what state the modem was really in then.

I have temporarily put WEP back, but am prepared to try again...

---

### Post by tturrisi on 2006-12-21
It appears that the wifi security has not been disabled in the modem-router.  There HAS to be an option to turn off wifi security, I have never ever seen a wifi router that forces WEP or WPA.  To fix this in windows you must go to "change the order of preferred networks" & delete your wlan in the list, then rescan & connect.  If windows still asks for a key then the wifi security has not been shut off in tyhe modem-router.

---

### Post by 2CV67 on 2006-12-21
Well, I re-re-read the 145-page manual & it says nothing about switching off WEP.
It says you can change the number if really necessary...

I re-studied all the available controls in the modem & still find nothing.

There are options for the firewall, but that is something completely different, isn't it?

I attach screenshots of all the control pages with relevant-looking titles, in case I missed something...

---

### Post by 2CV67 on 2006-12-21
Last screenshot...

---

### Post by jbutler12 on 2006-12-21
OK, those results are very promising.  Your wireless card on your computer is working fine.  Now we can eliminate any problems with drivers, etc... as the cause, and move on to test your network interface settings.

First, lets look at your settings.  Issue the following command:

```
iwconfig
```

You'll see something like this:

wlan2     IEEE 802.11g  ESSID:off/not availible
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:1B:D9:90   
          Bit Rate:11 Mb/s   Tx-Power:-2147483648 dBm   Sensitivity=0/3  
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beac

(You will obviously have wlan0 and maybe 802.11b instead of 'g', but the basic idea is the same).

Now, we want to set the interface settings.  You will use command-line commands to set the settings, and then try to connect all in one go.  First, since you cannot disable encryption (?), lets try to set the encryption:

```
sudo iwconfig wlan0 key open <key>
```

where <key> is your key without <>.  This assumes you use open WEP encryption, the most popular.  Doing this is much, much easier without encryption, so if you could find out how to disable it, that would make it much better.  Now we will tell the network interface where to find your network:

```
sudo iwconfig wlan0 essid <ESSID>
```

where <ESSID> is the case-sensitive ESSID listed when you did iwlist wlan0 scan without quotes or <>s.  Now that we have that setup, we can try to bring up the network.  First, knock down any existing network connections:

Type:
```
iwconfig
```
again. Now, instead of saying "none / not availbile" it should say ESSID: your network name.  If so, we are almost there.  If not, there is most likely a problem with your encryption and we'll need to find a way to disable it before moving on.  Just post up that that is the case and we'll see about disabling encryption (there must be a way to do it).

If it does say ESSID: your network name, we want to bring up the network.  FIrst we shut down running interfaces to start clean:

```
sudo ifdown eth0
```
```
sudo ifdown wlan0
```

dont worry if these give errors, they most likely will.  Then we bring up the wireless:

```
sudo ifup wlan0
```

If you see a bunch of lines of "DHCP blah blah blah" then we are on the right track.  It probably doesnt work yet (though it might), but we are almost there, and we only need to configure the router.

---

### Post by tturrisi on 2006-12-21
I tried to grab the manual for the modem but you must register to access Inventel support site :-(

---

### Post by 2CV67 on 2006-12-22
My Inventel support access permission just gets me to a limited "Tiscali France" area where there are no manuals available - just an option to download the whole installation CD, including manual, which they suggest could be "long"...
I have the manual on my hard drive, but it is 32Mo & in French...
I have been through it several times & really don't think it mentions dissabling WEP.
I asked for help in dissabling WEP via their support site.

---

### Post by 2CV67 on 2006-12-22
Reply to John - post #29

Thanks for your detailed plan!

Back in my original post #1 my iwconfig listing was already:
:::::::::::::::::::::::::::::::::::
[I]chris@salon:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11-DS ESSID:"DW-B-200-3d555" Nickname:"DW-B-200-3d555"
Mode:Managed Frequency:2.457 GHz Access Point: Not-Associated
Bit Rate:11 Mb/s Tx-Power=15 dBm
Retry limit:8 RTS thr=1536 B Fragment thr=1536 B
Power Management:off
Link Quality=0/0 Signal level=55/255 Noise level=0/0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.[/I]
:::::::::::::::::::::::::::::::::::::::

showing the ESSID etc - as you hoped to see after your 4th instruction above.

On this basis, I skipped the first 3 instruction. (I won't be offended if you tell me to go back & do it all properly!)

I did the last 3 instructions & got to the DHCPblablabla which I attach for your perusal.

::::::::::::::::::::::::::::::::::::::
[I]chris@DESKTOP:~$ sudo ifdown eth0
Password:
There is already a pid file /var/run/dhclient.eth0.pid with pid 3357
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:5b:00:29:37
Sending on   LPF/eth0/00:11:5b:00:29:37
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

chris@DESKTOP:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 3368
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:06:f4:07:db:3c
Sending on   LPF/wlan0/00:06:f4:07:db:3c
Sending on   Socket/fallback

chris@DESKTOP:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Listening on LPF/wlan0/00:06:f4:07:db:3c
Sending on   LPF/wlan0/00:06:f4:07:db:3c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ [/I]
::::::::::::::::::::::::::::::::::::::::::::::::

No actuel difference in performance yet - still not connected & WLAN still flashing green.

Is there any good news in there doc?

Thanks!

---

### Post by 2CV67 on 2006-12-22
While waiting hopefully for some response on the above, I am laboring through
*help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide*

& this mentions Channel 11 = 2.462GHz

My modem parameters mention Channel 11 with no frequency

*iwlist wlan0 scan* says Channel 11

*iwconfig wlan0 says* Frequency:2.457 GHz

Is this significant?

Also I see variously [I]Mode Managed & Mode Master....
[/I]
All tips welcome!

Thanks!

---

### Post by 2CV67 on 2006-12-22
For information & in case it can help anybody, there is a very comprehensive (French language) site on DW-B-200 modem here:
[http://www.porciello.com/inventel/](http://www.porciello.com/inventel/)

and a (dangerously bad, mechanical) English translation here:
[http://trans.voila.fr/voila?systran_lp=fr_en&systran_id=Voila-fr&systran_url=http://www.porciello.com/inventel/&systran_f=1166805845](http://trans.voila.fr/voila?systran_lp=fr_en&systran_id=Voila-fr&systran_url=http://www.porciello.com/inventel/&systran_f=1166805845)

I see there is a command-line solution for permanently removing WEP, but with lots of big red caveats, so I don't dare to try that yet.

There is also a link to download the manual, but it is 37Mo & is still French only.

I am combing through the French version of the site to see if there is more on WEP removal...

Any comments on previous posts yet?

Thanks!

---

### Post by 2CV67 on 2006-12-23
More steps backwards here.

I found this site [http://www.moospip.moostik.net/artic...?id_article=27](http://www.moospip.moostik.net/artic...?id_article=27) (again in french)
which confirms that I can only disable WEP by getting inside my modem with Telnet & rewriting part of it's internal Linux programming. 
With my performance so far, I don't feel up to that yet...

I found a site [http://www.wirelessdefence.org/Conte...ssCommands.htm](http://www.wirelessdefence.org/Conte...ssCommands.htm) 
which suggested basic commands for connecting to WEP with DHCP:
[I]
iwconfig wlan0 mode managed key 260E****************************
iwconfig essid "DW-B-200-3d555"
dhclient wlan0
ping [www.bbc.co.uk](www.bbc.co.uk)
[/I]
So I tried that - particularly as it looked as though it would force "Managed" which I suspect is part of my problem(s).
But again - no cigar.
This is what I got.
::::::::::::::::::::::::::::::
[I]
chris@DESKTOP:~$ sudo iwconfig wlan0 mode managed key 260E****************
Password:
chris@DESKTOP:~$ sudo iwconfig wlan0 mode managed key 260E************

chris@DESKTOP:~$ sudo iwconfig essid "DW-B-200-3d555"
Error : unrecognised wireless request "DW-B-200-3d555"

chris@DESKTOP:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:06:f4:07:db:3c
Sending on   LPF/wlan0/00:06:f4:07:db:3c
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
chris@DESKTOP:~$ [/I]
:::::::::::::::::::::::::::::::::::::::

I also tried to force the frequency, to correspond with what I have seen channel 11 should be.
This seems to have worked BUT WAS IT THE RIGHT THING TO DO or have I just screwed things up more?
::::::::::::::::::::::::::::::::::::::::
[I]
chris@DESKTOP:~$ sudo iwconfig wlan0 freq 2.462G
chris@DESKTOP:~$ 

chris@DESKTOP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"DW-B-200-3d555"  Nickname:"okuwlan"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality=0/0  Signal level=127/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

chris@DESKTOP:~$ [/I]
:::::::::::::::::::::::::::::::::::::::::

I tried forcing wlan0 down & up
::::::::::::::::::::::::::::::::::::::::
[I]
chris@DESKTOP:~$ sudo ifconfig wlan0 down
chris@DESKTOP:~$ sudo ifconfig wlan0 up
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ 
chris@DESKTOP:~$ [/I]
:::::::::::::::::::::::::::::::::::::::::::

I tried forcing wireless mode from Master to Managed. This does not seem to have had any effect.
Does it matter?
What should I have there?
:::::::::::::::::::::::::::::::::::::::::
[I]
chris@DESKTOP:~$ sudo iwconfig wlan0 mode managed
Password:
chris@DESKTOP:~$ 

chris@DESKTOP:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:90:4B:84:34:15
                    ESSID:"DW-B-200-3d555"
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Quality:0/0  Signal level:38/255  Noise level:0/0
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

chris@DESKTOP:~$ [/I]
::::::::::::::::::::::::::::::::::::::::::::

I am now VERY depressed by this whole business.
I have been struggling almost full-time for a week!

Surely there must be a simple, step-by-step method to move through this process & check off, one by one, what is working & what needs fixing????

I know there are hundreds of mistakes I could have & probably really have made, all of which lead to no connection, no ping etc.
I have doubts about the IPs, Gateways, DNS, DCHP/Static, Channel, Frequency, Managed/Master etc etc etc.
The number of attempts I would need to make, to try all the possible combinations methodically is enormous. (I sure tried a lot already!!!)
This blind rambling does not seem reasonable.

I thought we were moving in the right direction with post #29 (thanks John!) but there has been no follow up on the results I posted #32....

Could some kind soul please help me?

---

### Post by 2CV67 on 2006-12-23
:D :D :D :D 

99% there now!!!

Browsed dozens of French Forum threads & found (but not understood) 2 tips which have got me onto Internet - repeatably but not automatically yet.
That's the 1% more I need from you guys ;) .

WhenUbuntu is up, I have to:

1. sudo iwconfig wlan0 key restricted 260E******** (=WEP)
This changes my WLAN from flashing to steady green, which is usually a sign (in XP) that it has hooked the modem & is ready to go.
But at this stage - still no Internet.

2. In Networking, Disable & re-enable the Wireless Connection
At this point I have full Internet service :D :D 

Funnily enough, Network manager still thinks there is "no connection" but I can live with that.

Remaining problem is that I need to go through steps 1 & 2 every time I boot Ubuntu.

I would be DELIGHTED if somebody could suggest a way round that.

And I would be interested to know what I did & why it works now & not before!

Thanks for the last 1% for perfection guys! :-D

---

### Post by 2CV67 on 2006-12-23
:D :D :D 

99.9% now!!

Again blindly following leads from French Ubuntu forum, I added "restricted" in a line of code as follows:
::::::::::::::::::::::::

[I]sudo gedit /etc/network/interfaces

iface wlan0 inet dhcp
address 192.168.1.9
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid DW-B-200-3d555
wireless-key 260E***********[/I]

Change last line to:

*wireless-key restricted 260E************
::::::::::::::::::::::::::::::::::::::::

After which Ubuntu boots with Internet connection blazing!

...but still "no connection" indicated by Network Manager ikon.
I will dump that.

Last 0.1% (which I can live with, but would still like to fix if possible) is that I need to power-down the WLAN when switching between XP & Linux (both ways) either by switching off at mains or by unplugging & reconnecting at USB.

Well - that was over 100 hours work just to find where to add one word.....

I will now go & bang my head against the installation problems of my Canon printer!

Thanks for all your help - & for the last 0.1% if anybody has a lead!

---

