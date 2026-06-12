---
title: "replace iwl3945 with ipw3945"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by rogergantner on 2014-03-17
Ubuntu 12.04, 32 bit.
Intel Wireless 3945ABG.

I've been looking far and wide to revert to the intel proprietary driver ipw3945. iwl3945 is giving me very very slow wireless rates which makes it practically useless and I'm getting really tired of it.
Every search I've done to try and find a guide to replace the iwl driver shows threads that are old and link no longer work, etc. Others go no where.

Can anyone help me out with this?

I've also tried to use ndisgtk and have a driver running on it currently, however I'm not sure whether or not this driver is currently in use or not by the system. Under the wireless 'Connection Information' it shows driver to be iwl3945.

---

### Post by chili555 on 2014-03-17
It is a mistake to attempt to install an older, less developed driver for your wireless. It will either not work at all or worsen your issues. In case you doubt my opinion, here is the device I'm currently using:```
*-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: xx:19:d2:c2:1b:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes[COLOR="#FF0000"] driver=iwl3945[/COLOR] 
```I suggest we troubleshoot and tweak your device and perhaps your router settings. Only if all that fails to resolve your issue, we'll install a *newer* driver version. Let's get started. Please run and post:```
lsmod | grep -e ndis -e iwl
ls /etc/modprobe.d
uname -r
modinfo iwl3945 | grep parm
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by rogergantner on 2014-03-17
Thanks for your reply.

Before I post outputs of those commands, please note that in my attempt to get ndiswrapper to work I broke the automatic loading of the iwl3945 driver.
In order to make it work I have to open a terminal and run 'sudo modprobe iwl3945', otherwise the wireless remains as 'unclaimed'.
Any chance you can help me get that back to automatically run up?

ok, so after loading iwl3945 here goes lsmod | grep -e ndis -e iwl

> iwl3945                64640  0 
iwlegacy               88342  1 iwl3945
mac80211              534922  2 iwl3945,iwlegacy
cfg80211              416271  3 iwl3945,iwlegacy,mac80211
ndiswrapper           192977  0

> roger@a100:~$ ls /etc/modprobe.d
alsa-base.conf              blacklist-modem.conf         ndiswrapper.conf
blacklist-ath_pci.conf      blacklist-oss.conf           ndiswrapper.conf~
blacklist.conf              blacklist-rare-network.conf  oss-compat.conf
blacklist.conf~             blacklist-watchdog.conf      sl-modem.conf
blacklist-firewire.conf     dkms.conf                    vmwgfx-fbdev.conf
blacklist-framebuffer.conf  iwl3945


> roger@a100:~$ uname -r
3.11.0-18-generic


> roger@a100:~$ modinfo iwl3945 | grep parm
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

---

### Post by rogergantner on 2014-03-17
Please disregard my comment regarding the wireless driver not starting at boot. I ran the command 'echo 'iwl3945' | sudo tee -a /etc/modules' in terminal and its now loading at boot properly.

---

### Post by chili555 on 2014-03-17
You have been busy under the hood, I see. Let's clean some things up first and then troubleshoot. I suggest you remove ndiswrapper. It is loaded and undoubtedly conflicts:> iwl3945 64640 0
iwlegacy 88342 1 iwl3945
mac80211 534922 2 iwl3945,iwlegacy
cfg80211 416271 3 iwl3945,iwlegacy,mac80211
ndiswrapper 192977 0 Please open a terminal and do:```
sudo apt-get purge ndiswrapper*
sudo rm -rf /etc/modprobe.d/ndiswrapper.conf
```Now let's see what is in these two files and tweak as needed:```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modprobe.d/iwl3945
```Thanks.

---

### Post by rogergantner on 2014-03-17
> You have been busy under the hood, I see.
Time flew by quicker then you'd think lol

> roger@a100:~$ sudo apt-get purge ndiswrapper*
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ndiswrapper-common' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-utils' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-source' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-dkms' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-modules-1.9' for regex 'ndiswrapper*'
Note, selecting 'ndiswrapper-utils-1.9' for regex 'ndiswrapper*'
Package ndiswrapper-common is not installed, so not removed
Package ndiswrapper-utils-1.9 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  module-assistant dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ndiswrapper-dkms* ndiswrapper-source*
0 upgraded, 0 newly installed, 2 to remove and 7 not upgraded.
After this operation, 972 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 178617 files and directories currently installed.)
Removing ndiswrapper-dkms ...

------------------------------
Deleting module version: 1.57
completely from the DKMS tree.
------------------------------
Done.
Removing ndiswrapper-source ...
roger@a100:~$ sudo rm -rf /etc/modprobe.d/ndiswrapper.conf
roger@a100:~$ 



> roger@a100:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


> roger@a100:~$ cat /etc/modprobe.d/iwl3945
&#8220;alias wlan0 iwl3945 noptions iwl3945 disable_hw_scan=1&#8243;



---

### Post by chili555 on 2014-03-17
> roger@a100:~$ cat /etc/modprobe.d/iwl3945
“alias wlan0 iwl3945 noptions iwl3945 disable_hw_scan=1&#8243;This is not quite the correct way to do what you appear to be trying to do in a couple of respects. Rather than patch it up, I suggest we remove it for now and see if we need a driver parameter at all; if so, we'll write it a bit differently. ```
sudo rm /etc/modprobe.d/iwl3945
```Now reboot and let me have your report. In addition to any comments about how the wireless works, I'd like to see:```
sudo iwlist wlan0 scan
```Just show your network; we needn't see the neighbors. Please obscure the MAC address like this:> wlan0     Scan completed :
          Cell 01 - Address: [COLOR="#FF0000"]***********[/COLOR]
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006819ea3ac4
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000447425231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
Is your router 802.11N capable? Thanks.

---

### Post by rogergantner on 2014-03-17
I did "sudo rm /etc/modprobe.d/iwl3945" and rebooted, then initiated a file transfer from my xbmc media center runnin win7 and connected to a gigabit network to this laptop. See screen shot. Slowwwww...

[ATTACH=CONFIG]251239[/ATTACH]

Output of "sudo iwlist wlan0 scan" is way long, this is the first line I can begin to copy:

> 
**Edit.. just realized what this does.. trying to find my network amongst the mess.


The router is not wireless N capable.

---

### Post by rogergantner on 2014-03-17
Here it is:

> wlan0     Scan completed :
          Cell 01 - Address: xxxxxxxxxxxxxx
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"pretty fly for a WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014370ca2c7
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 001570726574747920666C7920666F7220612057694669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00



---

### Post by chili555 on 2014-03-17
> Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=53/70 Signal level=-57 dBm
Encryption keyn
ESSID:"A Tryhuba2"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
18 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
Mode:Master
<snip>
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
<snip>Is this your network? It seems to be the highest signal strength of what you posted. If not, may we see your networks' details? You can scroll the result with the arrow keys with:```
sudo iwlist wlan0 scan | less
```Get out of *less* with q.

---

### Post by rogergantner on 2014-03-17
No, sorry. See post #9 for my network.
[http://ubuntuforums.org/showthread.php?t=2211708&p=12959893#post12959893](http://ubuntuforums.org/showthread.php?t=2211708&p=12959893#post12959893)

---

### Post by chili555 on 2014-03-17
> ESSID:"pretty fly for a WiFi"LOLOL!

I notice the encryption method is TKIP. You will probably have better luck and more security if you reset the encryption to AES. Please do so and reboot the router. I suspect your performance will be greatly improved. I will be very interested in your report.

I am very glad to see that you aren't using WPA and WPA2 mixed mode.

---

### Post by rogergantner on 2014-03-17
> **chili555 said:**
> LOLOL!

I notice the encryption method is TKIP. You will probably have better luck and more security if you reset the encryption to AES. Please do so and reboot the router. I suspect your performance will be greatly improved. I will be very interested in your report.

I am very glad to see that you aren't using WPA and WPA2 mixed mode.

Thanks for all your help, I will try that as well... I need a break.

---

### Post by rogergantner on 2014-03-17
Ok, well.. I changed security to AES. Results are that transfer speeds have increased to 2MB/sec. Better then 150kb/sec for sure. See pic.

[ATTACH=CONFIG]251240[/ATTACH]

---

### Post by chili555 on 2014-03-17
> **rogergantner said:**
> Ok, well.. I changed security to AES. Results are that transfer speeds have increased to 2MB/sec. Better then 150kb/sec for sure. See pic.

[ATTACH=CONFIG]251240[/ATTACH]So is that what you are shooting for? Is that a reasonable speed given what speed you are paying your ISP for minus the expected overhead or do we have more work to do?

---

### Post by rogergantner on 2014-03-17
Well, I wont be doing a lot of huge data transfers on this laptop, so I can live with it. Of course if there is a way to increase the speed even more then I'm game to try. Realistically speaking I dont think I could get much more out of it.

---

### Post by chili555 on 2014-03-17
Let's see if there are any informative clues:```
cat /var/log/syslog | grep -e wlan -e iwl | tail -n20
```

---

### Post by rogergantner on 2014-03-17
> roger@a100:~$ cat /var/log/syslog | grep -e wlan -e iwl | tail -n20
Mar 17 19:25:33 a100 NetworkManager[874]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 17 19:25:33 a100 NetworkManager[874]: <info> Activation (wlan0) Beginning IP6 addrconf.
Mar 17 19:25:33 a100 NetworkManager[874]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Mar 17 19:25:33 a100 NetworkManager[874]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Mar 17 19:25:33 a100 dhclient: Listening on LPF/wlan0/00:18:de:5a:8e:b0
Mar 17 19:25:33 a100 dhclient: Sending on   LPF/wlan0/00:18:de:5a:8e:b0
Mar 17 19:25:33 a100 dhclient: DHCPREQUEST of 10.0.0.122 on wlan0 to 255.255.255.255 port 67
Mar 17 19:25:33 a100 NetworkManager[874]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Mar 17 19:25:33 a100 NetworkManager[874]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Mar 17 19:25:33 a100 NetworkManager[874]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Mar 17 19:25:34 a100 NetworkManager[874]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Mar 17 19:25:36 a100 NetworkManager[874]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Mar 17 19:25:36 a100 NetworkManager[874]: <info> Policy set 'pretty fly for a wifi' (wlan0) as default for IPv4 routing and DNS.
Mar 17 19:25:36 a100 NetworkManager[874]: <info> Activation (wlan0) successful, device activated.
Mar 17 19:25:36 a100 NetworkManager[874]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Mar 17 19:25:54 a100 NetworkManager[874]: <info> (wlan0): IP6 addrconf timed out or failed.
Mar 17 19:25:54 a100 NetworkManager[874]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 17 19:25:54 a100 NetworkManager[874]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 17 19:25:54 a100 NetworkManager[874]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 17 19:26:09 a100 kernel: [12961.116239] Modules linked in: snd_hda_codec_si3054 snd_hda_codec_realtek joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi pcmcia snd_rawmidi snd_seq_midi_event i915 snd_seq yenta_socket drm_kms_helper tifm_7xx1 drm psmouse tifm_core serio_raw i2c_algo_bit snd_timer pcmcia_rsrc pcmcia_core toshiba_acpi sparse_keymap snd_seq_device video wmi snd bnep rfcomm mac_hid bluetooth parport_pc lpc_ich ppdev arc4 iwl3945 soundcore iwlegacy mac80211 snd_page_alloc cfg80211 ndiswrapper(OF) lp parport firewire_ohci e100 firewire_core sdhci_pci mii sdhci crc_itu_t [last unloaded: ac97_bus]

Thanks

---

### Post by chili555 on 2014-03-17
This all looks pretty normal until:> Mar 17 19:26:09 a100 kernel: [12961.116239] Modules linked in: snd_hda_codec_si3054 <snip>That usually happens just after some process choked and threatened to crash. All the modules that were loaded and working, including your wireless, are listed as an aid to troubleshooting. It is not necessarily related to wireless, but may be. I suggest you do:```
less /var/log/syslog
```See what the last two or three lines were before this scary message by looking at the timestamp. See what went wrong at 19:29:09 or just a moment before.

I doubt it has much to do with your speed problem, but it's worth finding and fixing.

Let's dig deeper:```
dmesg | grep 80211
sudo iw reg get
```

---

### Post by rogergantner on 2014-03-17
I dont have any data past 19:26:09

> Mar 17 19:25:36 a100 NetworkManager[874]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Mar 17 19:25:36 a100 NetworkManager[874]: <info> Policy set 'pretty fly for a wifi' (wlan0) as default for IPv4 routing and DNS.
Mar 17 19:25:36 a100 NetworkManager[874]: <info> Activation (wlan0) successful, device activated.
Mar 17 19:25:36 a100 dbus[549]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 17 19:25:36 a100 NetworkManager[874]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Mar 17 19:25:36 a100 dbus[549]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 17 19:25:51 a100 ntpdate[7768]: step time server 91.189.94.4 offset 0.524840 sec
Mar 17 19:25:54 a100 NetworkManager[874]: <info> (wlan0): IP6 addrconf timed out or failed.
Mar 17 19:25:54 a100 NetworkManager[874]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 17 19:25:54 a100 NetworkManager[874]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 17 19:25:54 a100 NetworkManager[874]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 17 19:26:09 a100 kernel: [12961.116134] Corrupted low memory at c0007be8 (7be8 phys) = 53770000
Mar 17 19:26:09 a100 kernel: [12961.116147] Corrupted low memory at c0007bec (7bec phys) = 00000157
Mar 17 19:26:09 a100 kernel: [12961.116153] Corrupted low memory at c0007bf0 (7bf0 phys) = 00020700
Mar 17 19:26:09 a100 kernel: [12961.116160] Corrupted low memory at c0007bf4 (7bf4 phys) = 3f0e0000
Mar 17 19:26:09 a100 kernel: [12961.116166] Corrupted low memory at c0007bf8 (7bf8 phys) = 07e60033
Mar 17 19:26:09 a100 kernel: [12961.116173] Corrupted low memory at c0007bfc (7bfc phys) = 08e8e64d
Mar 17 19:26:09 a100 kernel: [12961.116209] ------------[ cut here ]------------
Mar 17 19:26:09 a100 kernel: [12961.116227] WARNING: CPU: 0 PID: 5981 at /build/buildd/linux-lts-saucy-3.11.0/arch/x86/kernel/check.c:140 check_for_bios_corruption+0xbe/0xd0()
Mar 17 19:26:09 a100 kernel: [12961.116233] Memory corruption detected in low memory
Mar 17 19:26:09 a100 kernel: [12961.116239] Modules linked in: snd_hda_codec_si3054 snd_hda_codec_realtek joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi pcmcia snd_rawmidi snd_seq_midi_event i915 snd_seq yenta_socket drm_kms_helper tifm_7xx1 drm psmouse tifm_core serio_raw i2c_algo_bit snd_timer pcmcia_rsrc pcmcia_core toshiba_acpi sparse_keymap snd_seq_device video wmi snd bnep rfcomm mac_hid bluetooth parport_pc lpc_ich ppdev arc4 iwl3945 soundcore iwlegacy mac80211 snd_page_alloc cfg80211 ndiswrapper(OF) lp parport firewire_ohci e100 firewire_core sdhci_pci mii sdhci crc_itu_t [last unloaded: ac97_bus]
Mar 17 19:26:09 a100 kernel: [12961.116374] CPU: 0 PID: 5981 Comm: kworker/0:3 Tainted: PF       W  O 3.11.0-18-generic #32~precise1-Ubuntu
Mar 17 19:26:09 a100 kernel: [12961.116380] Hardware name: TOSHIBA Satellite A100/CAPELL VALLEY(NAPA) CRB, BIOS 6.00    07/12/2007
Mar 17 19:26:09 a100 kernel: [12961.116390] Workqueue: events check_corruption
Mar 17 19:26:09 a100 kernel: [12961.116397]  00000000 00000000 cd2f5e84 c1673454 c18f60e0 cd2f5eb4 c10559c4 c18f60b4
Mar 17 19:26:09 a100 kernel: [12961.116417]  cd2f5ee0 0000175d c18f60e0 0000008c c104872e c104872e 00000000 c0010000
Mar 17 19:26:09 a100 kernel: [12961.116436]  c1b783b0 cd2f5ecc c1055a83 00000009 cd2f5ec4 c18f60b4 cd2f5ee0 cd2f5ef4
Mar 17 19:26:09 a100 kernel: [12961.116455] Call Trace:
Mar 17 19:26:09 a100 kernel: [12961.116472]  [<c1673454>] dump_stack+0x41/0x52
Mar 17 19:26:09 a100 kernel: [12961.116482]  [<c10559c4>] warn_slowpath_common+0x84/0xa0
Mar 17 19:26:09 a100 kernel: [12961.116493]  [<c104872e>] ? check_for_bios_corruption+0xbe/0xd0
Mar 17 19:26:09 a100 kernel: [12961.116504]  [<c104872e>] ? check_for_bios_corruption+0xbe/0xd0
Mar 17 19:26:09 a100 kernel: [12961.116514]  [<c1055a83>] warn_slowpath_fmt+0x33/0x40
Mar 17 19:26:09 a100 kernel: [12961.116524]  [<c104872e>] check_for_bios_corruption+0xbe/0xd0
Mar 17 19:26:09 a100 kernel: [12961.116535]  [<c1048750>] check_corruption+0x10/0x40
Mar 17 19:26:09 a100 kernel: [12961.116547]  [<c106dad6>] process_one_work+0x116/0x390
Mar 17 19:26:09 a100 kernel: [12961.116558]  [<c106e95a>] worker_thread+0xfa/0x320
Mar 17 19:26:09 a100 kernel: [12961.116569]  [<c106e860>] ? manage_workers.isra.24+0x140/0x140
Mar 17 19:26:09 a100 kernel: [12961.116579]  [<c1074374>] kthread+0x94/0xa0
Mar 17 19:26:09 a100 kernel: [12961.116592]  [<c1080000>] ? perf_trace_sched_kthread_stop_ret+0xb0/0xc0
Mar 17 19:26:09 a100 kernel: [12961.116603]  [<c1685177>] ret_from_kernel_thread+0x1b/0x28
Mar 17 19:26:09 a100 kernel: [12961.116613]  [<c10742e0>] ? flush_kthread_worker+0x90/0x90
Mar 17 19:26:09 a100 kernel: [12961.116621] ---[ end trace 532c35728d92e05f ]---
END



> roger@a100:~$ dmesg | grep 80211
[    2.323595] cfg80211: Calling CRDA to update world regulatory domain
[    2.576853] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[  134.868080] ieee80211 phy0: wlan0: No probe response from AP 00:22:6b:63:9a:85 after 500ms, disconnecting.
[  134.900285] cfg80211: Calling CRDA to update world regulatory domain
[ 2834.308089] ieee80211 phy0: wlan0: No probe response from AP 00:22:6b:63:9a:85 after 500ms, disconnecting.
[ 2834.356278] cfg80211: Calling CRDA to update world regulatory domain
[ 4263.500082] ieee80211 phy0: wlan0: No probe response from AP 00:22:6b:63:9a:85 after 500ms, disconnecting.
[ 4263.521108] cfg80211: Calling CRDA to update world regulatory domain
[ 4465.496098] ieee80211 phy0: wlan0: No probe response from AP 00:22:6b:63:9a:85 after 500ms, disconnecting.
[ 4465.514970] cfg80211: Calling CRDA to update world regulatory domain
[ 4654.274891] cfg80211: Calling CRDA to update world regulatory domain
[ 4812.500118] ieee80211 phy0: wlan0: No probe response from AP 00:22:6b:63:9a:85 after 500ms, disconnecting.
[ 4812.529129] cfg80211: Calling CRDA to update world regulatory domain
[ 5148.244327] cfg80211: Calling CRDA to update world regulatory domain
[ 7610.244080] ieee80211 phy0: wlan0: No probe response from AP 00:22:6b:63:9a:85 after 500ms, disconnecting.
[ 7610.292310] cfg80211: Calling CRDA to update world regulatory domain
[ 7622.739325] cfg80211: Calling CRDA to update world regulatory domain
[12915.961657] cfg80211: Calling CRDA to update world regulatory domain
[12920.176326] Modules linked in: snd_hda_codec_si3054 snd_hda_codec_realtek joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi pcmcia snd_rawmidi snd_seq_midi_event i915 snd_seq yenta_socket drm_kms_helper tifm_7xx1 drm psmouse tifm_core serio_raw i2c_algo_bit snd_timer pcmcia_rsrc pcmcia_core toshiba_acpi sparse_keymap snd_seq_device video wmi snd bnep rfcomm mac_hid bluetooth parport_pc lpc_ich ppdev arc4 iwl3945 soundcore iwlegacy mac80211 snd_page_alloc cfg80211 ndiswrapper(OF) lp parport firewire_ohci e100 firewire_core sdhci_pci mii sdhci crc_itu_t [last unloaded: ac97_bus]
[12961.116239] Modules linked in: snd_hda_codec_si3054 snd_hda_codec_realtek joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi pcmcia snd_rawmidi snd_seq_midi_event i915 snd_seq yenta_socket drm_kms_helper tifm_7xx1 drm psmouse tifm_core serio_raw i2c_algo_bit snd_timer pcmcia_rsrc pcmcia_core toshiba_acpi sparse_keymap snd_seq_device video wmi snd bnep rfcomm mac_hid bluetooth parport_pc lpc_ich ppdev arc4 iwl3945 soundcore iwlegacy mac80211 snd_page_alloc cfg80211 ndiswrapper(OF) lp parport firewire_ohci e100 firewire_core sdhci_pci mii sdhci crc_itu_t [last unloaded: ac97_bus]


sudo: iw: command not found

[/QUOTE]

---

### Post by chili555 on 2014-03-17
> 19:26:09 a100 kernel: [12961.116134] [COLOR="#FF0000"]Corrupted low memory[/COLOR] at c0007be8 (7be8 phys) = 53770000That doesn't sound good. I'd ask about that here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)> sudo: iw: command not found
Please try:```
sudo apt-get install iw
sudo iw reg get
```Off for the evening; I'll check in tomorrow.

---

### Post by rogergantner on 2014-03-17
> country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 80), (6, 20), PASSIVE-SCAN, NO-IBSS
    (57240 - 63720 @ 2160), (N/A, 0)



Yea that corrupt memory I'm curious about. It wouldnt surprise me if something is breaking down. This thing I bought in the fall of 2006.
Thanks for your help so far. Pretty interesting.

---

### Post by rogergantner on 2014-03-17
BIOS memory possibly corrupting;

[http://ubuntuforums.org/showthread.php?t=1106037](http://ubuntuforums.org/showthread.php?t=1106037)

---

### Post by chili555 on 2014-03-18
In some but not all cases, setting your regulatory domain explicitly may help. Yours is currently 00, meaning one-size-maybe-fits-all, just like my old orange jumpsuit! Let's set it and see if it helps. Please look up yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it with:```
sudo iw reg set IS
```Of course, substitute yours here, if you aren't in Iceland. If it helps, make it permanent:```
gksudo gedit /etc/rc.local
```Right above the line 'exit 0' add this new line:```
iw reg set IS
```I don't know if this memory issue is hardware or software related, but I suggest you step up your backup strategy.

---

### Post by rogergantner on 2014-03-20
Now set to Canada:
> roger@a100:~$ sudo iw reg set CA
[sudo] password for roger: 
roger@a100:~$ sudo iw reg get
country CA:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)



I've also read that the memory issue can be when the computer resumes from standby (sleep mode). I notice that this laptop specifically doesnt do well after recovering from standby. The cooling fan will run continuously.
That said, I checked the log again after a reboot this morning, and its still reporting corrupt memory. It's ok though, I dont keep important stuff on this laptop. If the BIOS eventually craps out in the next few years I still would of got lots of life out of it.
I really believe the memory issue is related to this:
> > From: "H. Peter Anvin" <hpa@xxxxxxxxx>
> Date: Fri, 10 Jul 2009 07:59:01 -0700
> Re: Intel BIOS - Corrupted low memory at ffff880000004200
>
> Ingo Molnar wrote:
>
>
>> So I'd really like to know what is happening there,
>> instead of just zapping support for 64K of RAM on the
>> majority of Linux systems.
>>
>> We might end up doing the same thing in the end
>> (i.e. disable that 64k of RAM) - but it should be an
>> informed decision, not a wild stab in the dark.
>
>
> Speaking as a boot loader author, I can let you know that
> these kinds of problems are in no [ways] limited to
> suspend/resume.
>
> Pretty much any time you're executing BIOS code you're
> going to have *some* platform which has severe memory
> corruption somewhere. This is particularly painful for boot
> loaders, obviously, because the BIOS corrupts the boot
> loader as it is running. In most cases, there simply isn't
> any way to prevent the corruption, and it's simply dumb
> luck that you will boot most of the time.
>
> And no, I don't think EFI is going to magically solve
> anything. EFI will just spread the same class of corruption
> problems over the entire memory map. It will reduce the
> density of such bugs -- in particular it will eliminate
> the "right offset, wrong segment" as well as "idiot coding
> assembly" class of problems -- but it will not confine the
> ones that can and will happen; it's still fundamentally a
> super-privileged flat memory space.
>
> The root cause seems to be a lack of verification practices
> in the BIOS industry in the post-DOS era. Back when DOS was
> still a commercially significant system, the BIOS didn't
> just support the running OS, it also directly supported
> running applications. That put a relatively high bar on how
> broken your BIOS could be and still have a viable platform.
> These days, it doesn't look like neither the BIOS vendors
> nor the OEMs necessarily even know how to QA, and since the
> BIOS industry is relatively small and highly consolidated,
> if there isn't sufficient OEM pressure it simply won't
> happen since there is no money in it.
>
> The HDMI case is a good example -- that probably involved
> SMI being triggered and the SMI code then clobbering a wild
> pointer.
>
> -hpa
>
> --
> H. Peter Anvin, Intel Open Source Technology Center
> I work for Intel. I don't speak on their behalf.

---

### Post by chili555 on 2014-03-20
I'm not a memory corruption/BIOS/EFI student, but I might wonder if you have a corrupted BIOS that might benefit from an upgrade flash. I might also wonder if I might end up bricking a laptop that is at least mostly working. Please proceed with care and I disclaim all responsibility!

---

### Post by rogergantner on 2014-03-20
There are no more bios updates for this machine. I suppose if it came right down to it I could reflash the current most firmware, if it lets me, but it isnt giving me any problems so I will leave it be as it is.

---

