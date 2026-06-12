---
title: "Atheros wireless drops and requires reboot"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by liuzerus87 on 2008-11-19
Hi, I'm currently running Kubuntu 8.10 on a Thinkpad T400 with an Atheros wireless card:

```
david@Whistler:~$ lspci | grep Atheros
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

I'm using the ath_5k driving from backports after having blacklisted ath_hal and ath_pci as according to the second part of [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html"). I'm having a problem where after some random time (sometimes 2 minutes, sometimes hours and hours), my wireless disconnects and won't reconnect until a full reboot. dmesg gives

```
david@Whistler:~$ dmesg | grep wlan0
[   27.374909] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   27.376102] wlan0: authenticated
[   27.376109] wlan0: associate with AP 00:0f:8f:08:f9:90
[   27.377613] wlan0: RX AssocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=66)
[   27.377618] wlan0: associated
[   27.378311] wlan0: disassociating by local choice (reason=3)
[   27.379790] wlan0: deauthenticated
[   28.376155] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   28.377298] wlan0: authenticated
[   28.377306] wlan0: associate with AP 00:0f:8f:08:f9:90
[   28.379762] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=67)
[   28.379771] wlan0: associated
[   28.382463] wlan0: disassociating by local choice (reason=3)
[   28.383921] wlan0: deauthenticated
[   29.380126] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   29.381285] wlan0: authenticated
[   29.381293] wlan0: associate with AP 00:0f:8f:08:f9:90
[   29.383156] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=68)
[   29.383162] wlan0: associated
[   29.383958] wlan0: disassociating by local choice (reason=3)
[   29.385138] wlan0: deauthenticated
[   30.384148] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   30.388324] wlan0: authenticated
[   30.388335] wlan0: associate with AP 00:0f:8f:08:f9:90
[   30.394398] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=69)
[   30.394410] wlan0: associated
[   30.395335] wlan0: disassociating by local choice (reason=3)
[   30.397901] wlan0: deauthenticated
[   31.396552] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   31.397723] wlan0: authenticated
[   31.397731] wlan0: associate with AP 00:0f:8f:08:f9:90
[   31.399453] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=70)
[   31.399460] wlan0: associated
[   31.400346] wlan0: disassociating by local choice (reason=3)
[   31.403174] wlan0: deauthenticated
[   32.400180] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   32.401407] wlan0: authenticated
[   32.401421] wlan0: associate with AP 00:0f:8f:08:f9:90
[   32.403274] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=71)
[   32.403286] wlan0: associated
[   32.405665] wlan0: disassociating by local choice (reason=3)
[   32.409603] wlan0: deauthenticated
[   33.408132] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   33.410147] wlan0: authenticated
[   33.410160] wlan0: associate with AP 00:0f:8f:08:f9:90
[   33.413475] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=72)
[   33.413486] wlan0: associated
[   33.414421] wlan0: disassociating by local choice (reason=3)
[   33.415718] wlan0: deauthenticated
[   34.412149] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   34.413317] wlan0: authenticated
[   34.413330] wlan0: associate with AP 00:0f:8f:08:f9:90
[   34.416317] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=73)
[   34.416326] wlan0: associated
[   34.416878] wlan0: disassociating by local choice (reason=3)
[   34.418532] wlan0: deauthenticated
[   35.416131] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   35.417318] wlan0: authenticated
[   35.417333] wlan0: associate with AP 00:0f:8f:08:f9:90
[   35.419074] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=74)
[   35.419085] wlan0: associated
[   35.420567] wlan0: disassociating by local choice (reason=3)
[   35.424083] wlan0: deauthenticated
[   36.424185] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   36.425792] wlan0: authenticated
[   36.425806] wlan0: associate with AP 00:0f:8f:08:f9:90
[   36.435136] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=75)
[   36.435146] wlan0: associated
[   36.435698] wlan0: disassociating by local choice (reason=3)
[   36.438013] wlan0: deauthenticated
[   37.436061] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   37.437204] wlan0: authenticated
[   37.437213] wlan0: associate with AP 00:0f:8f:08:f9:90
[   37.439534] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=76)
[   37.439546] wlan0: associated
[   37.440638] wlan0: disassociating by local choice (reason=3)
[   37.441731] wlan0: deauthenticated
[   38.444073] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   38.446375] wlan0: authenticated
[   38.446384] wlan0: associate with AP 00:0f:8f:08:f9:90
[   38.449830] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=77)
[   38.449837] wlan0: associated
[   38.450275] wlan0: disassociating by local choice (reason=3)
[   38.452125] wlan0: deauthenticated
[   39.448043] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   39.456908] wlan0: authenticated
[   39.456925] wlan0: associate with AP 00:0f:8f:08:f9:90
[   39.458676] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=78)
[   39.458685] wlan0: associated
[   39.460174] wlan0: disassociating by local choice (reason=3)
[   39.461659] wlan0: deauthenticated
[   40.460066] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   40.461227] wlan0: authenticated
[   40.461235] wlan0: associate with AP 00:0f:8f:08:f9:90
[   40.465372] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=79)
[   40.465383] wlan0: associated
[   40.466811] wlan0: disassociating by local choice (reason=3)
[   40.467931] wlan0: deauthenticated
[   41.464103] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   41.465298] wlan0: authenticated
[   41.465306] wlan0: associate with AP 00:0f:8f:08:f9:90
[   41.467122] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=80)
[   41.467127] wlan0: associated
[   41.467454] wlan0: disassociating by local choice (reason=3)
[   41.468558] wlan0: deauthenticated
[   42.468141] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   42.472056] wlan0: authenticated
[   42.472073] wlan0: associate with AP 00:0f:8f:08:f9:90
[   42.481095] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=81)
[   42.481111] wlan0: associated
[   42.482562] wlan0: disassociating by local choice (reason=3)
[   42.485353] wlan0: deauthenticated
[   43.484128] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   43.485322] wlan0: authenticated
[   43.485335] wlan0: associate with AP 00:0f:8f:08:f9:90
[   43.489250] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=82)
[   43.489262] wlan0: associated
[   43.490636] wlan0: disassociating by local choice (reason=3)
[   43.496948] wlan0: deauthenticated
[   44.496556] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   44.498454] wlan0: authenticated
[   44.498460] wlan0: associate with AP 00:0f:8f:08:f9:90
[   44.504729] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=83)
[   44.504736] wlan0: associated
[   44.505552] wlan0: disassociating by local choice (reason=3)
[   44.507369] wlan0: deauthenticated
[   45.504699] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   45.505884] wlan0: authenticated
[   45.505900] wlan0: associate with AP 00:0f:8f:08:f9:90
[   45.508034] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=84)
[   45.508048] wlan0: associated
[   45.509401] wlan0: disassociating by local choice (reason=3)
[   45.510726] wlan0: deauthenticated
[   46.508052] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   46.509264] wlan0: authenticated
[   46.509280] wlan0: associate with AP 00:0f:8f:08:f9:90
[   46.514252] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=85)
[   46.514266] wlan0: associated
[   46.514667] wlan0: disassociating by local choice (reason=3)
[   83.624246] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   83.631960] wlan0: authenticated
[   83.631976] wlan0: associate with AP 00:0f:8f:08:f9:90
[   83.635111] wlan0: deauthenticated
[   84.632077] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[   84.633238] wlan0: authenticated
[   84.633245] wlan0: associate with AP 00:0f:8f:08:f9:90
[   84.639484] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=86)
[   84.639497] wlan0: associated
[  518.458462] wlan0: authenticate with AP 00:11:92:36:41:f0
[  518.462583] wlan0: authenticated
[  518.462595] wlan0: associate with AP 00:11:92:36:41:f0
[  518.466307] wlan0: RX ReassocResp from 00:11:92:36:41:f0 (capab=0x421 status=0 aid=55)
[  518.466318] wlan0: associated
[  637.745064] wlan0: failed to restore operational channel after scan
[  637.860809] wlan0: failed to set freq to 2412 MHz for scan
[  637.920438] wlan0: Failed to config new BSSID to the low-level driver
[  638.197337] wlan0: failed to set freq to 2417 MHz for scan
[  638.534001] wlan0: failed to set freq to 2422 MHz for scan
[  638.870564] wlan0: failed to set freq to 2427 MHz for scan
[  639.207031] wlan0: failed to set freq to 2432 MHz for scan
[  639.543264] wlan0: failed to set freq to 2437 MHz for scan
[  639.879743] wlan0: failed to set freq to 2442 MHz for scan
[  640.216623] wlan0: failed to set freq to 2447 MHz for scan
[  640.553260] wlan0: failed to set freq to 2452 MHz for scan
[  640.889976] wlan0: failed to set freq to 2457 MHz for scan
[  641.226833] wlan0: failed to set freq to 2462 MHz for scan
[  641.226911] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[  641.424110] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[  641.624654] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[  641.824115] wlan0: authentication with AP 00:0f:8f:08:f9:90 timed out
[  643.292751] wlan0: failed to set freq to 2412 MHz for scan
[  643.634395] wlan0: failed to set freq to 2417 MHz for scan
[  643.975026] wlan0: failed to set freq to 2422 MHz for scan
[  644.315672] wlan0: failed to set freq to 2427 MHz for scan
[  644.657243] wlan0: failed to set freq to 2432 MHz for scan
[  644.998575] wlan0: failed to set freq to 2437 MHz for scan
[  645.340133] wlan0: failed to set freq to 2442 MHz for scan
[  645.683050] wlan0: failed to set freq to 2447 MHz for scan
[  646.025814] wlan0: failed to set freq to 2452 MHz for scan
[  646.368237] wlan0: failed to set freq to 2457 MHz for scan
[  646.709835] wlan0: failed to set freq to 2462 MHz for scan
[  646.710616] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[  646.908076] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[  647.112170] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[  647.312057] wlan0: authentication with AP 00:0f:8f:08:f9:90 timed out
[  657.080721] wlan0: failed to set freq to 2412 MHz for scan
[  657.421436] wlan0: failed to set freq to 2417 MHz for scan
[  657.762072] wlan0: failed to set freq to 2422 MHz for scan
[  658.102844] wlan0: failed to set freq to 2427 MHz for scan
[  658.443956] wlan0: failed to set freq to 2432 MHz for scan
[  658.784366] wlan0: failed to set freq to 2437 MHz for scan
[  659.124788] wlan0: failed to set freq to 2442 MHz for scan
[  659.465213] wlan0: failed to set freq to 2447 MHz for scan
[  659.805714] wlan0: failed to set freq to 2452 MHz for scan
[  660.146474] wlan0: failed to set freq to 2457 MHz for scan
[  660.486927] wlan0: failed to set freq to 2462 MHz for scan
[  661.502209] wlan0: Failed to config new SSID to the low-level driver
[  666.445996] wlan0: failed to set freq to 2412 MHz for scan
[  667.374023] wlan0: failed to set freq to 2417 MHz for scan
[  669.223710] wlan0: failed to set freq to 2422 MHz for scan
[  670.153279] wlan0: failed to set freq to 2427 MHz for scan
[  671.081165] wlan0: failed to set freq to 2432 MHz for scan
[  672.009314] wlan0: failed to set freq to 2437 MHz for scan
[  672.936684] wlan0: failed to set freq to 2442 MHz for scan
[  673.864038] wlan0: failed to set freq to 2447 MHz for scan
[  674.791407] wlan0: failed to set freq to 2452 MHz for scan
[  675.719989] wlan0: failed to set freq to 2457 MHz for scan
[  676.648637] wlan0: failed to set freq to 2462 MHz for scan
[  682.609399] wlan0: failed to set freq to 2412 MHz for scan
[  683.538149] wlan0: failed to set freq to 2417 MHz for scan
[  684.467272] wlan0: failed to set freq to 2422 MHz for scan
[  685.395367] wlan0: failed to set freq to 2427 MHz for scan
[  686.323432] wlan0: failed to set freq to 2432 MHz for scan
[  687.251063] wlan0: failed to set freq to 2437 MHz for scan
[  688.179579] wlan0: failed to set freq to 2442 MHz for scan
[  689.107261] wlan0: failed to set freq to 2447 MHz for scan
[  690.955894] wlan0: failed to set freq to 2452 MHz for scan
[  691.883444] wlan0: failed to set freq to 2457 MHz for scan
[  692.811488] wlan0: failed to set freq to 2462 MHz for scan
[  693.738936] wlan0: Failed to config new SSID to the low-level driver
[  693.738944] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[  693.936626] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[  694.136567] wlan0: authenticate with AP 00:0f:8f:08:f9:90
[  694.338369] wlan0: authentication with AP 00:0f:8f:08:f9:90 timed out
```

I also tried using ifconfig to restart wireless and got
```
david@Whistler:~$ sudo ifconfig wlan0 down
david@Whistler:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Resource temporarily unavailable
```

This is my iwconfig when the connection is working:
```
david@Whistler:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"uchicago"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:8F:08:F9:90
          Bit Rate=11 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=51/100  Signal level:-65 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

And when its broken
```
david@Whistler:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"uchicago"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

I've seen some suggestions based on the SIOCSIFFLAGS that I need to disable plug-n-play in my bios, but I can't find such an option, only an option to manually set PCI IRQ numbers. Should I try to do that, or should I install ndiswrappers, or is there something else I should try? Thanks.

---

### Post by dmv on 2008-11-20
i get the same problem, network card (lspci)
Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]

it is interesting that it sometimes connects when i am already connected to the router via ethernet, and the connection drops as soon as i when i disconnect ethernet, unless i bring down eth0 before removing the cable, in which case i stay connected

---

### Post by iponeverything on 2008-11-20
Things seem to going swimmingly up until here:

```
[   84.633245] wlan0: associate with AP 00:0f:8f:08:f9:90
[   84.639484] wlan0: RX ReassocResp from 00:0f:8f:08:f9:90 (capab=0x421 status=0 aid=86)
[   84.639497] wlan0: associated
[  518.458462] wlan0: authenticate with AP 00:11:92:36:41:f0
[  518.462583] wlan0: authenticated
[  518.462595] wlan0: associate with AP 00:11:92:36:41:f0
[  518.466307] wlan0: RX ReassocResp from 00:11:92:36:41:f0 (capab=0x421 status=0 aid=55)
[  518.466318] wlan0: associated

```

You associate with the cisco product (00:11:92:36:41:f0) and your driver has a fit. Seems like a a bug in your driver. You should not need to reboot though.. if you take down the interface and remove and reinsert the module -- it should start working again.

---

### Post by liuzerus87 on 2008-11-23
Could you explain what it means to take down the interface? I've tried

```
sudo modprobe -r ath5k
sudo modprobe ath5k
```

to no effect. Is there another step I need?

---

### Post by rospogrigio on 2009-02-17
> **dmv said:**
> i get the same problem, network card (lspci)
Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]

it is interesting that it sometimes connects when i am already connected to the router via ethernet, and the connection drops as soon as i when i disconnect ethernet, unless i bring down eth0 before removing the cable, in which case i stay connected

I have the same exact wireless device (did not try the ethernet thing though). Waiting for some workaround 'cause there's really no other way than rebooting and it's quite annoying... :(
Regards

---

### Post by seamustry on 2009-02-17
yep this happens on my intel 2915abg also but only when i'm using my college's wifi...at home it works fine.

also, sometimes when i wake the laptop from sleep, the wireless is disabled by itself and i have to reboot to make it work.

---

