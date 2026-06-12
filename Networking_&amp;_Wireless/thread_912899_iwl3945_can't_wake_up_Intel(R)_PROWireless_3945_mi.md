---
title: "iwl3945 can't wake up Intel(R) PRO/Wireless 3945 mini card"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by dvlong on 2008-09-07
I'm curious to know how many of you are having unresolved problems with Pro/wireless 3945 on Hardy.  I've been following and trying every possible solution I can find, (in many cases several times) but to no avail. I'm a bit afraid of missing the answer as well.  It seems that others are doing likewise, but not necessarily posting.

Can we consolidate things here but directing one another to other threads that might hold that answer?

I'm using a Compaq v3000 with Hardy.  The center of the problem seems to lie with the power management see below:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ESSID_IN_QUOTES"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:E5:61:36:13   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Does anyone have anything new on this???  I would hate to reinstall Windows!

---

### Post by chili555 on 2008-09-07
My 3945ABG works perfectly. My power management is 'off' as well. Power management, among other things, permits the card to go into a sleep mode and wake up and get back to work after a period of time. The objective is to save battery power. I don't think we want power management quite yet.

Have you installed *linux-backports-modules-hardy-generic*?

Can you scan and see networks?```
sudo iwlist wlan0 scan
```

Is your switch on or off?```
sudo cat /var/log/messages | grep switch
```

Have you rechecked your encryption; WPA, WEP, etc.?

---

### Post by dvlong on 2008-09-07
Thanks, Chili555.  I've tried everything shown in the JasonKirk thread 'dell 1525 laptop & iwl3945 nightmare.  Before that I tried the ndiswrapper fix but that didn't work.  I don't know how to analyze all the outputs but after installing linux-backports-modules-hardy-generic things worked for a couple of days but then started getting 'strange'.  One of the threads was pointing to updates as being the possible cause of this strange behaviour.  I don't know.

Below are the outputs:

$ sudo iwlist wlan0 scan
sudo: unable to resolve host longslap2
[sudo] password for dvlong: 
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:61:36:13
                    ESSID:"linksys"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=80/100  Signal level=-52 dBm  Noise level=-84 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000bb8dcf57b

And...

$ sudo cat /var/log/messages | grep switch
sudo: unable to resolve host longslap2
Sep  7 08:07:22 longslap2 kernel: [   14.132730] SMP alternatives: switching to UP code
Sep  7 08:07:22 longslap2 kernel: [   14.569333] SMP alternatives: switching to SMP code
Sep  7 08:07:22 longslap2 kernel: [   14.785880] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  7 08:07:22 longslap2 kernel: [   33.711686] Kill switch must be turned off for wireless networking to work.
Sep  7 08:22:29 longslap2 kernel: [   12.240797] SMP alternatives: switching to UP code
Sep  7 08:22:29 longslap2 kernel: [   12.672461] SMP alternatives: switching to SMP code
Sep  7 08:22:29 longslap2 kernel: [   12.888947] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  7 08:25:11 longslap2 kernel: [   12.923886] SMP alternatives: switching to UP code
Sep  7 08:25:11 longslap2 kernel: [   13.350087] SMP alternatives: switching to SMP code
Sep  7 08:25:11 longslap2 kernel: [   13.595134] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  7 09:58:50 longslap2 kernel: [   14.997860] SMP alternatives: switching to UP code
Sep  7 09:58:50 longslap2 kernel: [   15.428398] SMP alternatives: switching to SMP code
Sep  7 09:58:50 longslap2 kernel: [   15.645382] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  7 10:05:11 longslap2 kernel: [   38.642390] SMP alternatives: switching to UP code
Sep  7 10:05:11 longslap2 kernel: [   39.070261] SMP alternatives: switching to SMP code
Sep  7 10:05:11 longslap2 kernel: [   39.339416] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  7 10:15:59 longslap2 kernel: [   19.988088] SMP alternatives: switching to UP code
Sep  7 10:15:59 longslap2 kernel: [   20.414625] SMP alternatives: switching to SMP code
Sep  7 10:15:59 longslap2 kernel: [   20.631259] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  7 10:21:10 longslap2 kernel: [   17.040455] SMP alternatives: switching to UP code
Sep  7 10:21:10 longslap2 kernel: [   17.466711] SMP alternatives: switching to SMP code
Sep  7 10:21:10 longslap2 kernel: [   17.702834] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  7 10:21:22 longslap2 kernel: [   49.721079]  [switched_from_rt+0x17/0x20]  [acpi_ex_access_region+0x203/0x217] switched_from_rt+0x17/0x20
Sep  7 16:28:25 longslap2 kernel: [   20.150608] SMP alternatives: switching to UP code
Sep  7 16:28:25 longslap2 kernel: [   20.585741] SMP alternatives: switching to SMP code
Sep  7 16:28:25 longslap2 kernel: [   20.830611] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  7 17:00:55 longslap2 kernel: [   27.649210] SMP alternatives: switching to UP code
Sep  7 17:00:55 longslap2 kernel: [   28.084531] SMP alternatives: switching to SMP code
Sep  7 17:00:55 longslap2 kernel: [   28.300499] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  7 17:07:32 longslap2 kernel: [  288.030432] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x011f000a
Sep  7 18:56:40 longslap2 kernel: [   19.330435] SMP alternatives: switching to UP code
Sep  7 18:56:40 longslap2 kernel: [   19.763658] SMP alternatives: switching to SMP code
Sep  7 18:56:40 longslap2 kernel: [   20.009764] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  7 19:04:49 longslap2 kernel: [   18.783406] SMP alternatives: switching to UP code
Sep  7 19:04:49 longslap2 kernel: [   19.214714] SMP alternatives: switching to SMP code
Sep  7 19:04:49 longslap2 kernel: [   19.458293] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  7 19:07:21 longslap2 kernel: [   16.980333] SMP alternatives: switching to UP code
Sep  7 19:07:21 longslap2 kernel: [   17.417867] SMP alternatives: switching to SMP code
Sep  7 19:07:21 longslap2 kernel: [   17.661233] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  8 07:48:06 longslap2 kernel: [   17.729377] SMP alternatives: switching to UP code
Sep  8 07:48:06 longslap2 kernel: [   18.167087] SMP alternatives: switching to SMP code
Sep  8 07:48:06 longslap2 kernel: [   18.411476] ACPI: EC: non-query interrupt received, switching to interrupt mode
Sep  8 07:55:27 longslap2 kernel: [  328.872400] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x011f000a

I've tried setting encryption off and to WAP and to this specific machine but as far as I can see nothing has helped me there.

Again, I really appreciate any help you might offer and believe from reading related threads there's more than just a few of us with problems like this.  :)

---

### Post by danbob on 2008-11-13
Help!!! Please!!!

I'm having the same problems as dvlong. However, this is on a Dell Inspiron 1525 that shipped with Ubuntu Hardy 8.04.1 from the factory, and a built-in Intel PRO/Wireless 3945ABG. Wireless worked FINE upon first booting up the machine -- list of wireless networks, connected just fine, browsed the web.
After that, used the machine with no wireless in the area. Since then, it's been a nightmare and will not even sense wifi networks in the area.

I get exactly the same outputs as dvlong describes in this thread, for everything. The network has no encryption. I've completely disabled the wifi switch in the BIOS. I've updated the kernal, and tried booting 2.6.24-16 that came with the machine, upgraded, and tried booting both 2.6.24-19 and 2.6.24-21, hardy backports is installed, and so on.

I'm at the end of my rope on this machine, and I'm only 24-48 hours away from boxing this machine up and returning it to Dell as defective. I'm not afraid of the Linux command line, all my computers are Ubuntu, but nothing has worked so far on this shiny silver laptop.

Any suggestions? Other than returning the machine as defective, and scolding Dell for selling an Ubuntu laptop that does not work out of the box as promised?

DAN

---

