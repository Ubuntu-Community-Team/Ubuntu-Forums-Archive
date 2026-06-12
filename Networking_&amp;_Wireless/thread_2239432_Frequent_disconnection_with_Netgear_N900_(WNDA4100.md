---
title: "Frequent disconnection with Netgear N900 (WNDA4100) Wireless Adapter"
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by oceola2 on 2014-08-13
Having the same issue with an N900 dangle to a mifi.
Prior to the HDWE update the connection was listed as ra0 but now is wlan0.

It seems to me it is a timeout of somekind.
Contents of the provided script editing out some of the extra dmesg connection detritus.


    ======== Wireless-Info START ========

```
System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

harvey2 3.13.0-33-generic i686,  Ubuntu 12.04.5 LTS, precise

CPU    : Intel(R) Core(TM) i7-3770K CPU @ 3.50GHz
Memory : 32121 MB
Uptime : 08:19:15 up 31 min,  3 users,  load average: 1.20, 1.58, 1.22


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~



lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 005 Device 004: ID 0846:9012 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 03f0:0405 Hewlett-Packard ScanJet 3400cse
Bus 002 Device 004: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 005: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 002 Device 007: ID 03f0:152a Hewlett-Packard 


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"VirginMobile MiFi2200 893 Secure"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 VirginMobile MiFi2200 893 Secure>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
2: phy2: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rt2800usb              26740  0 
rt2800lib              89156  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20161  1 rt2800usb
rt2x00lib              49529  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              564484  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              423921  2 rt2x00lib,mac80211
eeepc_wmi              12983  0 
asus_wmi               23994  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
mxm_wmi                12893  0 
video                  19330  2 asus_wmi,i915
wmi                    18827  2 asus_wmi,mxm_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
eeepc_wmi     (1): hotplug_wireless=N
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800usb     (1): nohwcrypt=N
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===========================================o======  =======o===========o===========o=========o========  ===o==============o===========
 Interface & ID                            | Type        | Driver    | State     | Default | Speed     | Support      | HW Addr   
===========================================o======  =======o===========o===========o=========o========  ===o==============o===========
 wlan0  [VirginMobile MiFi2200 893 Secure] | 802.11 WiFi | rt2800usb | connected | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    HOME-6020-2.4:   Infra, <MAC C-NA HOME-6020-2.4 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    WGSB5:           Infra, <MAC C-02 WGSB5>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    MHCRP:           Infra, <MAC C-NA MHCRP 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    HOME-6020-5:     Infra, <MAC C-NA HOME-6020-5 1>, Freq 5805 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    *VirginMobile MiFi2200 893 Secure: Infra, <MAC C-01 VirginMobile MiFi2200 893 Secure>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA
    SMBCB:           Infra, <MAC C-NA SMBCB 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2

    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
-------------------------------------------+-------------+-----------+-----------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

VirginMobile MiFi2200 893 Secure : ssid=VirginMobile | permissions=user:grumpus:; MiFi2200 893 Secure | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.0.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 3.966/4.105/4.244/0.139 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     27 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 149 (5.745 GHz)
          Channel 151 (5.755 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 159 (5.795 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)

          Current Frequency=2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 VirginMobile MiFi2200 893 Secure>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption keyn
                    ESSID:"VirginMobile MiFi2200 893 Secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000032cf6167
                    Extra: Last beacon: 188ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 WGSB5>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption keyn
                    ESSID:"WGSB5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001cca8313180
                    Extra: Last beacon: 7132ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rt2800usb]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
firmware:       rt2870.bin
version:        2.3.0
srcversion:     D6F814DAF78F2BEA3DA12CB
depends:        rt2x00lib,rt2800lib,rt2x00usb
parm:           nohwcryptisable hardware encryption. (bool)

[rt2800lib]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt

[crc_ccitt]
filename:       /lib/modules/3.13.0-33-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        

[rt2x00usb]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211

[rt2x00lib]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     CC69EE39E7D673974A21C0A
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-33-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algoefault rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-33-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)

[eeepc_wmi]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/platform/x86/eeepc-wmi.ko
srcversion:     B54CE86332FC282F9684B45
depends:        asus-wmi
parm:           hotplug_wireless:Enable hotplug for wireless device. If your laptop needs that, please report to [EMAIL="acpi4asus-user@lists.sourceforge.net"]acpi4asus-user@lists.sourceforge.net[/EMAIL]. (bool)

[asus_wmi]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     222BD5E26B3EE82CC433FF2
depends:        sparse-keymap,wmi,video

[mxm_wmi]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/platform/x86/mxm-wmi.ko
srcversion:     62CBD37DE87DF0C4CD7FBA3
depends:        wmi

[video]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int

[wmi]
filename:       /lib/modules/3.13.0-33-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdgump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# USB device 0x0846:0x9012 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
rt3573sta


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-33-generic root=UUID=702d1098-6799-490d-9d23-5d1db8e867ea ro quiet splash vt.handoff=7
```

Some how some of the code got bolexed and a too many images notice occurred, probably bbcode picking up on parenthesis, colon and semi colons

---

### Post by Toz on 2014-08-13
Hello oceola2 and welcome to the forums. 

I have moved your post to its own thread (its not exactly the same problem as the thread you posted in) and have added **[noparse]```
 
```[/noparse]** tags.

---

### Post by varunendra on 2014-08-13
Hello oceola2,

It is clear from your description (earlier it was "ra0") and the report (/etc/modules) that you were previously using the proprietary driver downloaded from Ralink's site. Manually compiled drivers, unless installed with 'dkms', need to be compiled with every kernel upgrade.

The current driver in use is the native one from the kernel, and the support for your device in the native driver has just been added to it. So let's try a few things with the native driver first. Please open a terminal, and run the following command (you may copy-paste it to avoid typo) in it -

```
sudo iwconfig wlan0 power off
```
This will disable Power Management on the wlan0 interface. Does it help stability? If yes, report back and we'll make it permanent if is reset on reboot.

If it doesn't seem to help, make sure it actually turned off by looking at the output of -
```
iwconfig
```
Among other things, it should show "Power Management" as "off". Keep watching this output from time to time and report back if it automatically turns back on.

Additionally, or if the above seems to have no effect at all (keep PM off anyway), try a driver parameter -
```
sudo modprobe -rv rt2800usb
sudo modprobe -v rt2800usb nohwcrypt=Y
```
The first command will remove the driver, thus disabling the wireless. The second one will reload it with the 'nohwcrypt=Y' parameter. Does this make the connection stable? This will be a temporary change that will be reset at next boot. If it helps, we can make it permanent.

Another thing worth trying, if required and if possible for you, try changing the encryption in the router/access-point to WPA2-PSK with AES (CCMP). Of course you need admin access to the router/access-point to change this in it. Currently it is using WPA with TKIP, which is less secure and not as optimal as AES at high speeds.

If none of these seem to help, please try the guide/post that you followed earlier to install the proprietary "rt3573sta" driver, and see if you can install it again. It would be helpful if you can give us link to the guide you followed/following to install it.

---

### Post by oceola2 on 2014-08-14
Let me thank you for the rapid response first.
**sudo iwconfig wlan0 power off** appears to function properly.
iwconfig confirms:
wlan0     IEEE 802.11abgn  ESSID:"VirginMobile MiFi2200 893 Secure"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 5C0A04:F2:88:93   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc:38   Missed beacon: 0
lo        no wireless extensions.

**sudo modprobe -rv rt2800usb** disconnects the wireless.
I did not try to re-instate the rt2800usb but did do a re-install of the rt3573sta and reboot the system to see if anything held.
Apparently not as the wlan0 managed connection returned.
I powered off the wlan0 again using the **sudo iwconfig wlan0 power off**
But it seems the rt2800usb stays in force, 
current iwconfig readout:
wlan0     IEEE 802.11abgn  ESSID:"VirginMobile MiFi2200 893 Secure"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 5C: DA: D4: F2: 88: 93
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit: 7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:57   Missed beacon:0
lo        no wireless extensions.

As to the install used it is the one provided in the wireless thread in the Ubuntu forums from a while ago for the N900.
**copied for the thread**

[quote="original thread"]Re: WNDA 4100 (NetGear N900) Wireless Dual Band USB Adapter

    You will need to download and compile rt3573sta and make a few changes. Can you get a wired ethernet connection even temporarily? If not, we can still compile, but it will be a bit difficult. If you can hook up an ethernet cable and get a connection, open a terminal and do:
    Code:

    **sudo apt-get install linux-headers-generic build-essential**

    Go here [http://www.wikidevi.com/wiki/Netgear_WNDA4100](http://www.wikidevi.com/wiki/Netgear_WNDA4100) and download the package for rt3573sta. Get it to your desktop so we can find it. Right-click it and select Extract Here. Open the folder that appears called Linux and select the DPO version. Right-click it and select Extract Here. Now we will make some changes to it. Drill down to os/linux/config.mk. Open the file with a text editor and make these changes:
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
    Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
    In other words, change the =n to =y in those two lines. Proofread very carefully, save and close the text editor.

    Open the file common/rtusb_dev_id.c with any text editor, such as gedit. Add a line as I've highlighted:
    Code:

    #endif /* RT35xx */
    #ifdef RT3573
        {USB_DEVICE(0x148F,0x3573)}, /* Ralink 3573 */
        {USB_DEVICE(0x7392,0x7733)}, /* Edimax */
        {USB_DEVICE(0x0846,0x9012)}, /* Netgear */
        {USB_DEVICE(0x0B05,0x17AD)}, /*ASUS */
    #endif /* RT3573 */
        { }/* Terminating entry */

    All other lines before and after are unchanged. Punctuation, spelling, spacing, etc. are crucial so proofread very carefully, save and close the text editor.

    Now we're ready to compile. Open a terminal and do:
    Code:

    cd Desktop/Linux/DPO

    Press Tab and the remainder will fill in automagiaclly. Press Enter. Now do:
    Code:

    sudo su
    make
    make install
    modprobe rt3573sta
    exit

    Is it working now? Are we there yet? 

AFTER KERNEL IMAGE UPDATE - Re compile
Code:
    cd Desktop/Linux/DPO

Press Tab and the remainder will fill in automagically. Press Enter. Now do:
Code:
    sudo su
    make clean
    make
    make install
    modprobe rt3573sta
    exit
Please make a note of these instructions so you'll be ready. 

**previously I never had to go farther than this point as everything was stable, **

Booted into the new kernel, please run and post:
Code:

sudo modprobe rt3573sta
dmesg | grep -e rt3 -e wlan

More info: if state
Hmmm. Let's dig deeper. Please post:
Code:
    modinfo rt3573sta | head -n5
    lsusb
    sudo modprobe rt3573sta
    dmesg | tail -n10 [/quote]

This worked all the way up to the HWE update. It worked also in Fedora, Linux Mint14 - 32 bit and Linux Mint 16 -64 bit with the files replacements suggested for the 64 bit dirver compile

---

### Post by oceola2 on 2014-08-14
Update: so far turning off the power management using **sudo iwconfig wlan0 power off** seems to stabilize the connection but has to be renewed for each system re-boot.
It would be nice to have a default with the power management off but it does turn off as indicated in the iwconfig output in the previous thread.
Tested this in another forum which had been cutting out about every so many minutes and it did not break connection once in 30 minute.

---

### Post by varunendra on 2014-08-14
> **oceola2 said:**
> But it seems the rt2800usb stays in force

Since the rt2800usb driver is tightly integrated with the kernel, it will always be preferred unless blacklisted. So if you are trying to use the sta driver now, please blacklist the native driver first -
```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
This will add "rt2800usb" to the default blacklist file "/etc/modprobe.d/blacklist.conf". Reboot after this. You already have "rt3573sta" in the /etc/modules file, so it'll get loaded, but not the native 'rt2800usb' this time due to blacklisting.

You didn't need that earlier because the older version of the native driver did not support the card, so wasn't loaded by the kernel.

Please try and report back how it goes.

---

### Post by oceola2 on 2014-08-15
Disabling (blacklisting ) did not help but the command line worked fine.
The command worked fine but the re-install of the rt3573sta did not.
It was there prior to the HWE update and may have been during the update but after blacklisting the rt2800usb and re-booting the wireless connections were gone.
 I tried to perform a re-install following the methods in my post from previous and was able to complete all the way to the **modprobe rt3573sta**
The message stated the rt3573sta module could not be inserted due to an improper format.

additional: an /etc/wireless folder was created but it was for a rt2870sta but no mention of the rt3573sta.
Best guess is the name had been changed to implement the original modules acceptance or possibly the two chips were similar.

I un-blacklisted the rt2800 and turned off the power management and was able to get back on line.
I may have to operate this way or find a simple method to disable the power management at startup.

More: I installed Linux Mint 17 64 bit this morning and will be installing Ubuntu 14.04 shortly.
The **sudo ifconfig wlan0 power off** command works fine for the Linux Mint but the 64 bit driver for the N900 seems to be unnecessary as the device was recognized and made the connection. I'm still fiddling with that system but so far so good.

---

### Post by varunendra on 2014-08-15
The ralink proprietary drivers have really weird ways of dealing with module/driver/interface names. They choose to rename the interface as "ra<a number>" instead of "wlan<a number>", choose to call their drivers "Ralink" in lshw, "rt2860sta" in other system calls and so on..

So, the /etc/wireless having no references to rt3573sta (it might have been rt2860sta there) is perfectly normal and in line with Ralink's fancy ways. But from your last post above, it seems the newly compiled driver doesn't work with the latest kernels.

Since the native one seems to be working fine, let's just make the power off thing automatic. But before that, I suggest you completely remove the sta driver that you installed. The command should be -
```
sudo make uninstall
```
..from the same directory where you earlier would have run "sudo make install" from to install it. I don't know if the /etc/wireless/<ralink stuff> needs to be deleted manually or is removed automatically, but it shouldn't matter anyway once the module is purged.

Then, to disable the power management permanently on "wlan0", try the elegant method first -
```
sudo touch /etc/pm/power.d/wireless
```
This will create a blank file named "wireless" in /etc/pm/power.d, which disables the default power management script located in /usr/lib/pm-utils/power.d directory. Then turn the PM off using the "sudo iwconfig wlan0 power off" command like before > reboot > check if it is still off. If it is, nothing else is required.

But if not, try making the "wireless" file we just created executable, putting the command in it -
```
echo "/sbin/iwconfig wlan0 power off" | sudo tee /etc/pm/power.d/wireless
sudo chmod +x /etc/pm/power.d/wireless
```

Then turn PM off with iwconfig command > reboot to make sure it remains off.

---

### Post by oceola2 on 2014-08-16
varunendra
Thanks again.  I will make changes off line and see if it holds.
So far the command continues to keep the power management from interrupting.
I'm getting the full 54MB/second transfer speed from the dangle to the mifi.

When I bring 14.04 on line I will see how it reacts to the dangle and try and apply some of the fixes I have seen, if needed, but it appears, since Mint is based on Ubuntu it may function without any issues. will keep in touch.
Oceola

---

### Post by oceola2 on 2014-08-17
varunendra

The first instructions : **sudo touch /etc/pm/power.d/wireless** had no effect, still had to manually turn off the power mangement for the wlan0.
This last bit of instructions:  
    **echo "/sbin/iwconfig wlan0 power off" | sudo tee /etc/pm/power.d/wireless**
   **sudo chmod +x /etc/pm/power.d/wireless** worked fine for turning off the power management and stayed so after reboot.

I also note the **sudo make install** in the install folder for the rt3573sta does not remove the changed name .dat file in the /etc/Wireless.
It had to be removed manually.

However the connection still seems to be breaking as the "Edit Connections" panel, when looking at the wireless account changes from **now** to some time increment.
I have however been able to post, download updates and so far there has been no logging out resulting from the indicated break.
It may very well be the network or some other unknown condition.

Thanks again

---

### Post by varunendra on 2014-08-17
Thank you for letting us know what worked and what didn't - a confirmation/feedback from the users is sometimes the only way for us to know something. :)

Regarding this -
> **oceola2 said:**
> I also note the **sudo make [COLOR="#FF0000"]install[/COLOR]** in the install folder for the rt3573sta does not remove the changed name .dat file in the /etc/Wireless.
It had to be removed manually.
Should I assume it is just a typo in the above, not really "install"? Because obviously it has to be "uninstall" in order to remove things.

> However the connection still seems to be breaking as the "Edit Connections" panel, when looking at the wireless account changes from **now** to some time increment.
I think whether the connection is breaking or not can be better confirmed by the dmesg part of the wireless_script report. Run it when you see some time instead of "now" in the NM settings for the connection in use. Of course, make sure you see this in the connection that is being used.

(Hint : The number in large bracket (e.g. [001234.5678]) in the dmesg part is time in seconds since the system started. In a full dmesg output, it starts at about '0' second, upto the time (in seconds) it is run after. It is normal to have a few connect/disconnect/reconnect attempts initially, but if you see that at significant time difference, we may have a real disconnection going on in the background. We may try a few things in that case, depending upon clues in the report.)

**PS:**
To properly mark the thread as **[SOLVED]**, use the "Thread Tools" link above the top post. You can see screenshots of it in the "see how" link in my signature below. :)

---

### Post by oceola2 on 2014-08-18
varunendra
It was a typo.
I will run the dmesg when in Ubuntu but I just ran it in Linux Mint 16 which seems to be stable but checked the "edit connections" and it changed from "now" to "4 minutes ago."
I noticed there is no power management listed in iwconfig but this is an older kernel with the 64 bit compile of the rt3573sta. It also lists the rt2870 as "nickname."
iwconfig output:
ra0       Ralink STA  ESSID:"VirginMobile MiFi2200 893 Secure"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 5C: DA: D4: F2 :88: 93
          Bit Rate=54 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=100/100  Signal level:-38 dBm  Noise level: -49 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0
lo        no wireless extensions.

dmesg output:
Start: [ 6718.991240] [UFW AUDIT] IN= OUT=ra0 SRC=192.168.1.2 DST=91.189.89.153 LEN=766 TOS=0x00 PREC=0x00 TTL=64 ID=59303 DF PROTO=TCP SPT=58481 DPT=443 WINDOW=296 RES=0x00 ACK PSH URGP=0 
[ 6719.012891] [UFW AUDIT] IN=ra0 OUT= MAC=4c:60:de:ce:7f:10:5c:da:d4:f2:88:93:08:00 SRC=91.189.94.12 DST=192.168.1.2 LEN=1500 TOS=0x00 PREC=0x00 TTL=59 ID=25210 DF PROTO=TCP SPT=80 DPT=49963 WINDOW=102 RES=0x00 ACK URGP=0 
. . . a great many lines of information.
Final few lines to end of dmesg:
[ 7053.093099] [UFW AUDIT] IN= OUT=ra0 SRC=192.168.1.2 DST=91.189.94.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=50644 DF PROTO=TCP SPT=49990 DPT=80 WINDOW=270 RES=0x00 ACK FIN URGP=0 
[ 7053.599462] [UFW AUDIT] IN=ra0 OUT= MAC=4c: 60: de: ce: 7f: 10: 5c: da: d4: f2: 88:93:08: 00 SRC=91.189.94.12 DST=192.168.1.2 LEN=52 TOS=0x00 PREC=0x00 TTL=59 ID=49756 DF PROTO=TCP SPT=80 DPT=49990 WINDOW=55 RES=0x00 ACK URGP=0 
[ 7075.678646] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 1027
[ 7195.933035] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 848

The amount in the "edit connections" continues to change.
Hope this helps in some way.

oceola2

---

### Post by varunendra on 2014-08-19
No hints of connection breaking in dmesg, which makes me believe what you see in Network Manager GUI is either some misunderstanding, or some harmless bug.

You may also try to look for hints in 'syslog' to be extra sure whether it is really breaking or not -
```
cat /var/log/syslog
```
The output will be huge, but the timings will be in human understandable form. :)

---

### Post by oceola2 on 2014-08-19
varunendra (was logged out due to break while trying to make the adjustments in the copy display, seems it just takes longer   I'm thinking it's a wireless ISP network thing.  During an update the speed of the download went to zero, there was a pause and the download began again and the speed was increased. The "edit connections" went from a "now" state to a "one minute ago." The download/update completed successfully.   Some of this may be due to my blocking 445 and 139 ports (just guessing)  Hopefully it's not related to the ports as I have been blocking them for years with no past ill effect.     This is some of the syslog output which may be relative: (Saved the entire out put)    ```
Aug 19 08:48:11 XXXXXX NetworkManager[892]:  DNS: starting dnsmasq...   Aug 19 08:48:11 XXXXXX NetworkManager[892]:  dnsmasq not available on the bus, can't update servers.    Aug 19 08:48:11 XXXXXX NetworkManager[892]:  [1408452491.623260] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name   Aug 19 08:48:11 XXXXXX NetworkManager[892]:  DNS: plugin dnsmasq update failed    Aug 19 08:48:11 XXXXXX NetworkManager[892]:  Writing DNS information to /sbin/resolvconf    Aug 19 08:48:11 XXXXXXdnsmasq[887]: started, version 2.68 cache disabled    Aug 19 08:48:11 XXXXXX dnsmasq[887]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth    Aug 19 08:48:11 XXXXXX dnsmasq[887]: DBus support enabled: connected to system bus    Aug 19 08:48:11 XXXXXX dnsmasq[887]: warning: no upstream servers configured    Aug 19 08:48:29 XXXXXX NetworkManager[892]:  (wlan0): IP6 addrconf timed out or failed.    Aug 19 08:48:29 XXXXXX NetworkManager[892]:  Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...    Aug 19 08:48:29 XXXXXX NetworkManager[892]:  Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...    Aug 19 08:48:29 XXXXXX NetworkManager[892]:  Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```       General Note: the commands to turn off the powermanagement works in Linux Mint17, 14.4.1 and 12.4.5 (should since they are same ugly baby in a new dress) Sorry for the run on atarts at AUG for each item, for some reason couldn't get the LF to work properly for a appropriate list.  Thanks again

---

### Post by varunendra on 2014-08-19
Please set "IPv6" to "Ignore" in network manager, and disable it permanently following this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

Either reboot, or do -
```
sudo sysctl -p
```
..to load the changes immediately.

Does it help anything?

**PS:**
You can always use pastebin.ubuntu.com to post large outputs. Just make sure it doesn't contain anything that you may consider sensitive info.

---

### Post by oceola2 on 2014-08-20
varunendra

If I turn off the ipv6 permanently does this impede any connections which are using or when the ipv6 becomes standard, make things more difficult.
I saw the permanently disabling ipv6 and have both the lines for the sysctl.conf file and the coded command to use and can edit them into the file.
I did set ipv6 to ignore in the network manager. I remember removing the network manager with previous distributions as it was a nuisance but wasn't using wireless at the time.
I have left it at the ignore state in the NM but is it possible to leave it set for local and accomplish the same thing?

Thanks
oceola2

---

### Post by varunendra on 2014-08-21
> **oceola2 said:**
> If I turn off the ipv6 permanently does this impede any connections which are using or when the ipv6 becomes standard, make things more difficult.

IPv4 is supported everywhere, while IPv6 relatively still very little. It becoming the 'Standard' doesn't seem to happen anytime soon, but when it does, it won't be a cause of potential problems anymore. Whatever problems currently occur are due to the fact that only a few entities seem to support it, thus causing delays, bottlenecks in establishing an end-to-end communication channel when attempting to establish a link using IPv6 protocol.

And above all, reverting the changes, if and when required, is as easy as deleting two-three lines from the sysctl.conf file and changing the setting in NM. So you really don't need to worry about it.

---

### Post by oceola2 on 2014-08-22
varunendra
Thanks again, will do this. Editing is simple enough.

Is there a reason the icon shows only 73%?

oceola2

ps: I also note changing the regdomain from the 00 to the appropriate country code caused the password for the wireless provider account to need a redo.

---

### Post by varunendra on 2014-08-22
No idea which icon and which 73% you are talking about. I am still using 12.04.1, and I don't see wifi signal strength in %. The only icon that has a number with % sign on my system here is the battery status icon.

However, if it is indeed wifi signal icon on your system, what do you expect to see, and why?

---

### Post by oceola2 on 2014-08-23
varunendra
Made the ipv6 off permanent but believe the percentage issue may be relative to turning it off or not making it available to "all users", not sure at this point.
The signal icon  for Ubuntu 12.04.5LTS takes the shape of a quadrant which encloses four arcs. As the signal strengthens or weakens the arcs brighten or fade.
This is paralleled somewhat in Linux Mint17 but a passover of the icon in Mint presents the percentage value but is different as it is vertical bars which perform in the same manner.
Have a copy of 14.4.1LTS which is still to be installed and am hoping the same icon, similar to Mint, has the same features.
Previously there would be comment in both the Network manger and in Connection information of 100% and the icon would stay on, all four arcs or quadrants.
This may be due to improvements or limitations placed on the USB connection by the new kernels. 
May also relate to upgrades which go beyond my 3G connection and represent the more liberal use of 4G and the incoming 5G. Just brainstorming on that.

---

### Post by oceola2 on 2014-08-24
varunendra
[quote="oceola2"]Just performed some more looking at the icon issue and it appears the provided driver in the later kernels for Ubuntu and Linux Mint might not be secure on these devices.
Guessing but it may be something needed in the Netgear driver for security missing in the kernel provided driver.
Using the native Netgear driver in an older version of Mint reveals a 100% secure condition but the 73-77% Secure condition of both the native drivers supplied with 14.04, 12.04 and Mint 17 may very well be compromised by some internal issue.
One thought I have had is the driver modification for the Netgear N900 for Ubuntu 14.04.1 - 64 bit may be able to be installed in both 64 bit and 32 bit systems and restore the 100% security.
Only way to know is to try it. [/quote]

Wish me luck. If it works I'll try and explain it.

**Modified driver did not succeed, same "not installing due to wrong format" Security not related to percentage shown**
Also it appears the percentage is a connection and not security.
This is due to the manner in which it is displayed as the word "Secure precedes the percentage but Secure is part of the name of the connection"

oceola2

PS: Still losing connection, logged out while viewing other pages in these forums. Something in the system is not allowing a full connection or timing things out.

---

### Post by oceola2 on 2014-08-28
varunendra
Branstorming with this.
As Ubuntu, Mint and some others install additional power management softwares for various laptops could there be something in one of those causing the confusions as well as the items fixed or changed so far?
Noticed in the file logind.conf (apparently removed in 12.04.5) under the /etc/systemd folder a change in items between the original setup and the newer setups.
Controllers item now has a string and is uncommented (blkio cpu cpuacct cpuset devices frreezer hugetlb memory perf_event net_cls net_prio
ResetControllers item also uncommented with no string.

Also the items below in the original configuration were uncommented and set to ignore while in the newer version commented out:
HandlePowerKey
HandleSuspend Key
HandleHibernateKey
HandleLidSwitch

---

### Post by varunendra on 2014-08-28
So after all, should we consider the problem still existing? Is it any better from where we started? Ignorable? Or just about the same?

Can you test the connection, without installing or tweaking anything, on a Live session running directly off a DVD or Live USB? If the output of "iwconfig" shows the Power Management to be "on", just use the regular command (sudo iwconfig wlan0 power off) to turn it off, then check its stability (probably across a download?).

If nothing else, at least it will rule out the possibility of the traces of the sta driver being the cause of the issue.

Regarding whatever you have discovered in the system files - if it were due to them, the problem would have been the same for everyone using this driver. But evidently, while the "rt2800usb" driver seems to keep the power management "on" by default on 14.04, turning it "off" by 'iwconfig' command seems to solve the problem for other users (at least two others). Unless they didn't notice the breakage as closely as you do, none of the other users of rt2800usb have so far reported any similar problem after applying the 'power off' trick.

Unfortunately, I neither have the hardware to experiment with, nor enough time to dig deeper with clues you have provided, if they have the potential to lead us to the root cause of the issue.

---

### Post by oceola2 on 2014-08-30
varunendra
At this point I would give it 90% percentage fixed. I have been trying to see if there is some other reason for the breaks to occur.
It may take more time to find the issue but the Netgear 900 driver works at 100% all the time in previous installs before the kernel and HWE updates while the kernel driver supplied under USB has been between 75% and 87% indicated signal strength but both remain steady with both showing the fluctuating changes (now, 4min ago, 2 min ago and 1 min ago) in the network manager Edit Connections area. Probably stable enough for most users except during large downloads where a secure login is required. The break in signal being long enough to essentially log one out. 
The power-off code provided works well and I have not had it fail yet once it is applied in a permanent fashion.
It would have been nice to be able to use the recompiled driver for the 64bit systems instead of the "spec" driver supplied in the newer kernel, It may be a commercial limitation or someone just didn't feel the format was good enough.

Anyway, I am in the process of re-installing some of the systems and if I come across anything I'll present it.

Thanks Again
Oceola

Additionally, with the new kernel update, there was no break in the system wireless which formerly had to be recompiled with each kernel update or change.
The power-off condition held.

---

### Post by oceola2 on 2014-09-06
@varunendra and all
Installed Ubuntu 14.04.1 LTS and over the past week found the fixes in this thread worked for the N900.
Also, still work for the 12.04.5 LTS as well.
Have not noticed any breaks or logouts as a result of the systems for over a week.
Note: also made sure Region was proper and did turn off IPV6 as suggested as default.

Thanks

---

### Post by varunendra on 2014-09-06
Glad to know the see-saw (kinda your profile pic) ended in a positive direction. :) Hope it remains stable from now on.

The correct way to mark the thread as [SOLVED] is to use the "Thread Tools" link above the top post - it marks the Thread Title itself as [SOLVED].

---

### Post by oceola2 on 2014-09-07
@varunendra
Thanks Again, will do.
Oceola2

---

