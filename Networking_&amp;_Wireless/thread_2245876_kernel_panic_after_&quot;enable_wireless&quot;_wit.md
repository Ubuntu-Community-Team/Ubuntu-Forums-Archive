---
title: "kernel panic after &quot;enable wireless&quot; with Realtek 8723be on Lenovo G50-45"
date: 2014-09-26
forum: Networking &amp; Wireless
---

### Post by EarlsFurniture on 2014-09-26
After a clean install of 12.04.5, wireless was non-functional. (lshw and lspci reported the hardware, but driver failed to load - 'enable wireless' was absent in the nm indicator menu) Neither ifconfig nor iwconfig could see wlan0.

I was in a rush and did not test it in the live environment prior to installing, but I have rebooted with a liveUSB and it was also not working there.

After reading several threads across various forums, I found [bug #1240940]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1240940") at launchpad.

I followed the last fix recommended in [comment #55]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1240940/comments/55") there. Namely, to:

```
git clone [http://github.com/lwfinger/rtlwifi_new.git](http://github.com/lwfinger/rtlwifi_new.git)
cd rtlwifi_new
make
sudo make install
```

Which as explained in the thread, would download the latest driver scheduled for inclusion in the 3.18 kernel. (but not yet backported to 3.13 or other)

The build went fine save for some compile errors on various modules that seem to be minor, but I didn't save the output and would have to rebuild to get them again.(unless there is a build log generated somewhere?)

After build and install, I was able to see and select "enable wireless" in the nm-indicator menu. The kernel promptly panicked (flashing caps-lock LED with frozen system that even sysRq couldn't resolve). And I've been stuck at this state ever since. (a few days now)

I've tried setting various options for the rtl8723be driver as suggested in that launchpad bug discussion, to no avail.

I've tried removing the ideapad-lenovo module suggested elsewhere, which also results in instant kernel panic.

I'm looking here for any clues, wild guesses, or help troubleshooting the panic itself if not something perhaps more mundane that was the root cause from the get-go.

My last resorts will be to attempt to try a newer kernel (is that possible on an HWE stack?) as 3.16 has been reported to work with this driver and hardware (other HW mileage may vary though)

OR

To change the hardware - either the card itself, or the entire laptop.

Unfortunately, this is not my machine with the problem, and the owner is not keen to update past the 12.04.5 release at present unless necessary. The owner is even contemplating trading in the laptop for another model with the retailer, but he has to make a decision by Monday.  9/29/14. (not trying to rush anyone - just advising what my time-table for solving this is before I get to try again with a different set of hardware)

I'm also having issue that the integrated graphics are not recognized and Ubuntu is operating in Unity2d mode right now.

I'm not sure if there is a relation, perhaps an interrupt issue, but thought I'd mention it. (since from what I've read, might be the source of the kernel panic, but I don't know how to track this down and fix)

Thanks in advance for any assitance anyone can provide.

Here's the wireless-info.txt:


```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Lenovo-G50-45 3.13.0-36-generic x86_64,  Ubuntu 12.04.5 LTS, precise

CPU    : AMD A6-6310 APU with AMD Radeon R4 Graphics
Memory : 3413 MB
Uptime : 15:41:16 up 5 min,  2 users,  load average: 0.37, 0.37, 0.19


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3812]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 13d3:5727 IMC Networks 
Bus 002 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                  Soft blocked  Hard blocked
0: hci0: Bluetooth                   no            no
1: ideapad_wlan: Wireless LAN        yes           no
2: ideapad_bluetooth: Bluetooth      no            no
3: phy0: Wireless LAN                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8723be             143475  0 
rtl_pci                39766  1 rtl8723be
btcoexist             183403  1 rtl8723be
rtlwifi               120761  3 rtl8723be,rtl_pci,btcoexist
mac80211              658125  3 rtl8723be,rtl_pci,rtlwifi
cfg80211              502970  2 rtlwifi,mac80211


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8723be     (6): debug=0 | disable_watchdog=N | fwlps=N | ips=N | swenc=N | swlps=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
============================o=============o===========o=============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | r8169     | connected   | yes     | 1000 Mb/s |              | <MAC eth0>

    Address:         192.168.0.56
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             68.105.28.12
    DNS:             68.105.29.11
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | rtl8723be | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.0.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.112/1.682/2.252/0.570 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rtl8723be]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
srcversion:     759541BD671E62ABDFC9E2A
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
parm:           ips:using no link power save (default 1 is open)
parm:           fwlps:using linked fw control power save (default 1 is open)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)

[rtl_pci]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     107BE1FCDB0F4E45B90BD3C
depends:        mac80211,rtlwifi

[btcoexist]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko
srcversion:     97A952CB16550F2BF298DD8
depends:        rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     1B11A49D7945F44320C512B
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~
Binary file /etc/udev/rules.d/70-persistent-net.rules matches


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
rtl8723be.conf    : options rtl8723be fwlps=0 swlps=0 ips=0
                    options MSI=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=14513bb3-b61b-4e7d-baa4-843a2ad8c4a5 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.974790] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.975283] audit: initializing netlink socket (disabled)
[    1.318876] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    8.083379] rtlwifi: module verification failed: signature and/or  required key missing - tainting kernel
[    8.395026] Using firmware rtlwifi/rtl8723befw.bin
[    8.554911] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.555287] rtlwifi: wireless switch is on
[   21.040013] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.174917] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.229441] r8169 0000:02:00.0: Direct firmware load failed with error -2
[   23.249763] r8169 0000:02:00.0 eth0: unable to load firmware patch rtl_nic/rtl8168g-3.fw (-2)

    ======== Done ========
```

---

### Post by praseodym on 2014-09-26
Try this one:

```
sudo apt-get install git unzip build-essential linux-headers-$(uname -r) linux-headers-generic
cd ~/Downloads/
wget https://github.com/lwfinger/rtl8723be/archive/a21b5b0228fe462df4301bd32a20dc4b8863ead9.zip
unzip ~/Downloads/rtl8723be-a21b5b0228fe462df4301bd32a20dc4b8863ead9.zip
git clone https://github.com/lwfinger/rtl8723be
cp -r /rtl8723be/firmware/ rtl8723be-a21b5b0228fe462df4301bd32a20dc4b8863ead9
cd rtl8723be-a21b5b0228fe462df4301bd32a20dc4b8863ead9
make 
sudo make install
sudo depmod -a
sudo update-initramfs -u 
```
From here (for kernel 3.2-3.13, for kernel 3.14 only [!!!] below):
[http://forum.ubuntuusers.de/topic/kein-internet-seit-ubuntu-13-10-auf-lenovo-b54/#post-6266182](http://forum.ubuntuusers.de/topic/kein-internet-seit-ubuntu-13-10-auf-lenovo-b54/#post-6266182)

---

### Post by EarlsFurniture on 2014-09-27
First, thank you very much for finding something specific to the 3.13 kernel, in German no less!

However, these instructions (not yours I see) are full of errors. Good thing I comprehend directory trees. A cursory overview would make obvious that these commands will not work and will generate errors that unless understood, one could not proceed past.

For starters, though minor, "cd ~-/Downloads/" should be "cd ~/Downloads"

Second, the wget command in line 3 fetches "really long hex string.zip" yet the next command attempts to unzip "rtl8723be-really long hex string.zip", since there is no such file, this command would fail. (so of course, I uncompressed what I really got)

The 5th line is a bit mystifying. Am I supposed to be copying everything from ~/rtl8723be/firmware to "rtl8723be-really long hex string" directory?

That could pose a problem since no command up to this point created ~/rtl8723be/firmware or put any files there. So I'm not sure what's supposed to happen here.

Then I see an attempt to CD into "rtl8723be-really absurdly long hexstring that I'm tired of even typing about much less copy and pasting the real thing" which doesn't exist

And then doing a make and make install.

So I simply cd'd into the "really long hexstring" directory (minus the rtl8723be- prefix)where all the source files were and skipped the CP step and did make and make install.

Of course, errors abound.

Notably, the one I mentioned earlier which goes something like this:

warning: passing argument 1 of 'ieee80211_is_robust_mgmt_frame' from incompatible pointer type [enabled by default]
include/linux/ieee80211.h:2224:20: note: expected "struct sk_buff *' but argument is of type "struct ieee80211_hdr *'

this was while compiling trx.c at 617:3

Proceeding anyway with the make install got me this:

cp: cannot stat "firmware/rtlwifi/': no such file or directory
make: *** [install] Error 1

So apparently, somewhere there should be a tree containing "firmware/rtlwifi" but it never got created.

Unfortunately, I have no clue as to where it should exist or when it should have been created or what it should contain.

If someone knows off hand, 1000 thanks. Otherwise, I'll be digging into the makefile and then the source in the morning and trying to sort this out.

Much thanks to praseodym for the assistance.

---

### Post by praseodym on 2014-09-28
Sorry, my keyboard has some problems with the "-" key. Create that folder
```

sudo mkdir -p /lib/firmware/rtlwifi
```
and try it again

---

### Post by EarlsFurniture on 2014-09-28
[FONT=lucida console]Thanks again, but it's still failing at this step:

[FONT=courier new]```
cp -r /rtl8723be/firmware/ rtl8723be-a21b5b0228fe462df4301bd32a20dc4b8863ead9
cp: cannot stat `/rtl8723be/firmware/': No such file or directory

```[/FONT]

[/FONT][FONT=lucida console]Presumably because the clone command prior to that did not create or put anything in a directory called /rtl8723be/firmware/

There did appear a directory (inside my ~/Downloads folder) called "rtl8723b2e" but there is no '/firmware/" directory within. There are however two hidden directories called ".git" and ".gitignore" respectively.

Yes. I did create /lib/firmware/rtlwifi which now appears to have files in it.

So the cp command didn't work and the compile still errors out with:

[FONT=courier new]```
cp: cannot stat `firmware/rtlwifi/': No such file or directory
find /lib/modules/3.13.0-36-generic -name "btcoexist_*.ko" -exec rm {} \;
find /lib/modules/3.13.0-36-generic -name "r8723be_*.ko" -exec rm {} \;
cp: cannot stat `firmware/rtlwifi/': No such file or directory
make: *** [install] Error 1
```[/FONT][/FONT]

---

### Post by EarlsFurniture on 2014-09-28
So I decided to proceed with the depmod and update-initramfs commands anyway.

Same result - still kernel panic.

Rebooted, tried to enable wireless again - kernel panic.

Rebooted, tried to enable wireless again, this time via function key for "airplane mode" (essentially the same as using the nm-indicator menu) - kernel panic.

Decided to check for updates. (using eth0) - there was 3.13.0-37. Installed it.

Rebooted.

It WORKS!

I'm not sure if it was the procedure advised in this thread, or if a proper driver was finally backported to 3.13.0-37. But so far, all is good, am I'm writing this reply via wifi right now!

Thanks for the help! (now, off to solve Unity running in 2d mode!)

---

### Post by praseodym on 2014-10-03
Check the VGA card:
```

lspci -nnk | grep -iA2 VGA
lsmod
```

---

### Post by www.rzr.online.fr on 2015-05-03
what about bluetooth status too ? I am investigating at [http://rzr.online.fr/q/ideapad](http://rzr.online.fr/q/ideapad)

---

