---
title: "[SOLVED] Intel 4695 Wireless Problems"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by SlalomMan on 2008-07-31
I posted in a thread about this here: [http://ubuntuforums.org/showthread.php?p=5498091#post5498091](http://ubuntuforums.org/showthread.php?p=5498091#post5498091)

I have an intel 4965 Wireless card. It works in Ubuntu without any configuration, but it is really, really slow. It runs much faster in Vista and XP on the same computer. I looked at other topics and downloaded the drivers from linuxwireless.com, and then I ran "make", "make install", "make unload", and "make load"

I then unplugged my LAN cable, which I had been using because it was so much faster, and no wireless networks show up to connect to. I tried a restart, but it solved nothing. I can work with a wired connection right now, and I'm sure that if I ran "make uninstall" it would put my old drivers back, but I would really like to get the speeds up. Wireless speeds, along with my Zune, is one of the only things that is keeping Windows on my computer as a secondary OS.

Any help would be greatly appreciated.

---

### Post by pytheas22 on 2008-07-31
Does:
```

sudo modprobe iwl4695
sudo ifconfig wlan0 up
```

make the wireless come on?

---

### Post by SlalomMan on 2008-07-31
For the modprobe, it just goes to a new line; i'm assuming that means it worked.


and the ifconfig:
SIOCSIFFLAGS: No such file or directory

To all who are following this; it's 4965...not 4695. My mistake.

---

### Post by mbsullivan on 2008-07-31
> For the modprobe, I get:
FATAL: Module iwl4695 not found.


It's iwl4965, not 4695. As previous user said, try something like the following:

```
sudo modprobe -r iwl4965; sudo modprobe iwl4965
sudo ifconfig wlan0 up
```

Then connect to your wireless network as ususal. This should work for any Distro newer than Feisty.

Mike

---

### Post by SlalomMan on 2008-07-31
I don't think my device goes by wlan0...it returns no file or directory. 

my ifconfig returns

```
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:78:32:e4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:90298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97004802 (92.5 MB)  TX bytes:11951857 (11.3 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86400 (84.3 KB)  TX bytes:86400 (84.3 KB)

```

I'm assuming eth0 is the LAN/ethernet, and that means that either my device isn't working anymore or it goes by lo.

EDIT: I tried to make uninstall the drivers, and now my wireless doesn't work at all....I guess I shouldn't have tried to go for more speed and just stuck with what I had...

---

### Post by pytheas22 on 2008-08-01
> I tried to make uninstall the drivers, and now my wireless doesn't work at all....I guess I shouldn't have tried to go for more speed and just stuck with what I had...

You shouldn't have to settle for something that's not usable.

What is the output of:

uname -r
locate iwl

tell you?  That should find the module on your system somewhere; if it doesn't, then something may have gone wrong when you tried compiling the drivers.

Also, if you boot into a different kernel (at the boot menu when you first turn on your computer, you should have a few different options for Ubuntu kernels), does the wireless work better?  And have you applied all Ubuntu system updates?

---

### Post by SlalomMan on 2008-08-01
I've applied all updates; I haven't tried running a different kernel yet; the only time I did that was when something broke on my desktop. Wireless has been subpar since I installed Ubuntu; when I first installed it a year ago I had to have one of the TA's help me get wireless working at all; I'm not sure how fast it was then, though.

uname -r returns "2.6.24-19-generic" - I checked this before I installed the drivers because I think it said something about being above 2.6.2 or something like that.

locate iwl returns
```

/home/kyle/.local/share/Trash/files/iwlwifi-1.0.0-1.tgz
/home/kyle/.local/share/Trash/info/iwlwifi-1.0.0-1.tgz.trashinfo
/home/kyle/Desktop/iwlwifi-1.0.0-1
/home/kyle/Desktop/compat-wireless-2008-07-30/.tmp_versions/iwl3945.mod
/home/kyle/Desktop/compat-wireless-2008-07-30/.tmp_versions/iwl4965.mod
/home/kyle/Desktop/compat-wireless-2008-07-30/.tmp_versions/iwlcore.mod
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.built-in.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-3945-rs.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-3945.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-4965-rs.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-4965.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-calib.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-core.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-eeprom.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-hcmd.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-power.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-rx.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-scan.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-sta.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl-tx.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl3945-base.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl3945.ko.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl3945.mod.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl3945.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl4965-base.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl4965.ko.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl4965.mod.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwl4965.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwlcore.ko.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwlcore.mod.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/.iwlcore.o.cmd
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/Makefile
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/built-in.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945-commands.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945-core.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945-debug.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945-hw.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945-io.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945-led.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945-led.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945-rs.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945-rs.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945-rs.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-3945.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-4965-hw.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-4965-rs.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-4965-rs.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-4965-rs.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-4965.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-4965.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-5000-hw.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-5000.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-calib.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-calib.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-calib.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-commands.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-core.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-core.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-core.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-csr.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-debug.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-debugfs.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-dev.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-eeprom.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-eeprom.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-eeprom.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-fh.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-hcmd.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-hcmd.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-helpers.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-io.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-led.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-led.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-power.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-power.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-power.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-prph.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-rfkill.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-rfkill.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-rx.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-rx.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-scan.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-scan.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-spectrum.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-sta.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-sta.h
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-sta.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-tx.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl-tx.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl3945-base.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl3945-base.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl3945.ko
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl3945.mod.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl3945.mod.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl3945.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl4965-base.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl4965-base.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl4965.ko
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl4965.mod.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl4965.mod.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwl4965.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwlcore.ko
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwlcore.mod.c
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwlcore.mod.o
/home/kyle/Desktop/compat-wireless-2008-07-30/drivers/net/wireless/iwlwifi/iwlcore.o
/home/kyle/Desktop/iwlwifi-1.0.0-1/CHANGES
/home/kyle/Desktop/iwlwifi-1.0.0-1/FILES
/home/kyle/Desktop/iwlwifi-1.0.0-1/GIT_SHA1
/home/kyle/Desktop/iwlwifi-1.0.0-1/INSTALL
/home/kyle/Desktop/iwlwifi-1.0.0-1/ISSUES
/home/kyle/Desktop/iwlwifi-1.0.0-1/LICENSE
/home/kyle/Desktop/iwlwifi-1.0.0-1/LICENSE.BSD
/home/kyle/Desktop/iwlwifi-1.0.0-1/LICENSE.GPL
/home/kyle/Desktop/iwlwifi-1.0.0-1/Makefile
/home/kyle/Desktop/iwlwifi-1.0.0-1/README.iwlwifi
/home/kyle/Desktop/iwlwifi-1.0.0-1/dvals
/home/kyle/Desktop/iwlwifi-1.0.0-1/load
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin
/home/kyle/Desktop/iwlwifi-1.0.0-1/patches
/home/kyle/Desktop/iwlwifi-1.0.0-1/scripts
/home/kyle/Desktop/iwlwifi-1.0.0-1/unload
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/Kconfig
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/Makefile
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/base.c
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-3945-hw.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-3945-rs.c
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-3945-rs.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-3945.c
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-3945.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-4965-hw.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-4965-rs.c
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-4965-rs.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-4965.c
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-4965.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-channel.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-commands.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-debug.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-eeprom.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-helpers.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-hw.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-io.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-priv.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwl-spectrum.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/origin/iwlwifi.h
/home/kyle/Desktop/iwlwifi-1.0.0-1/patches/.keep
/home/kyle/Desktop/iwlwifi-1.0.0-1/patches/01-queue_delayed_work.sh
/home/kyle/Desktop/iwlwifi-1.0.0-1/patches/02-cancel_delayed_work.sh
/home/kyle/Desktop/iwlwifi-1.0.0-1/patches/02-kcompat_delayed_work.patch
/home/kyle/Desktop/iwlwifi-1.0.0-1/patches/03-isr.patch
/home/kyle/Desktop/iwlwifi-1.0.0-1/patches/04-rx_flag_radiotap.patch
/home/kyle/Desktop/iwlwifi-1.0.0-1/patches/05-delayed_work_define.patch
/home/kyle/Desktop/iwlwifi-1.0.0-1/patches/d80211-v1.patch
/home/kyle/Desktop/iwlwifi-1.0.0-1/patches/wlan_80211.patch
/home/kyle/Desktop/iwlwifi-1.0.0-1/scripts/check_kernel
/home/kyle/Desktop/iwlwifi-1.0.0-1/scripts/determine_compat
/home/kyle/Desktop/iwlwifi-1.0.0-1/scripts/generate_compatible
/home/kyle/Desktop/iwlwifi-1.0.0-1/scripts/make_snapshot
/home/kyle/Desktop/iwlwifi-1.0.0-1/scripts/patch_kernel
/lib/firmware/2.6.24-16-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-16-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-16-generic/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-16-generic/iwlwifi-4965.ucode
/lib/firmware/2.6.24-18-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-18-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-18-generic/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-18-generic/iwlwifi-4965.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-3945-1.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-3945.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-4965-1.ucode
/lib/firmware/2.6.24-19-generic/iwlwifi-4965.ucode
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-16-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211/compatible
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-18-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwl4965.ko
/lib/modules/2.6.24-19-generic/updates/drivers/net/wireless/iwlwifi/iwlcore.ko
/sbin/iwlist
/usr/share/man/cs/man8/iwlist.8.gz
/usr/share/man/fr/man8/iwlist.8.gz
/usr/share/man/man8/iwlist.8.gz
/usr/src/linux-headers-2.6.24-16/drivers/net/wireless/iwlwifi
/usr/src/linux-headers-2.6.24-16/drivers/net/wireless/iwlwifi/Kconfig
/usr/src/linux-headers-2.6.24-16/drivers/net/wireless/iwlwifi/Makefile
/usr/src/linux-headers-2.6.24-18/drivers/net/wireless/iwlwifi
/usr/src/linux-headers-2.6.24-18/drivers/net/wireless/iwlwifi/Kconfig
/usr/src/linux-headers-2.6.24-18/drivers/net/wireless/iwlwifi/Makefile
/usr/src/linux-headers-2.6.24-19/drivers/net/wireless/iwlwifi
/usr/src/linux-headers-2.6.24-19/drivers/net/wireless/iwlwifi/Kconfig
/usr/src/linux-headers-2.6.24-19/drivers/net/wireless/iwlwifi/Makefile

```

The ones in the trash are from when I tried to install the official drivers from the intel website; I couldn't figure it out, though.

Would downloading an XP driver and using Ndiswrapper be any easier/better? I know native support is best, but if Ndiswrapper can make it faster than before, I would take that.

---

### Post by pytheas22 on 2008-08-01
> Would downloading an XP driver and using Ndiswrapper be any easier/better? I know native support is best, but if Ndiswrapper can make it faster than before, I would take that.

Yes, that should work and might be easier, since I don't know what's going on with the iwl driver.  The module exists on your system, so I don't know why it's not working.  If you don't know how to get it working with ndiswrapper, ask.  Otherwise I'll just mention (because the tutorials you follow may not) that you need to remember to blacklist the iwl4965 module (blacklisting iwl3945 too can't hurt) first by adding the lines:
```

blacklist iwl4965
blacklist iwl3945
```

to the file /etc/modprobe.d/blacklist.

Also remember that if you're on a 64-bit kernel, you need to use 64-bit Windows drivers with ndiswrapper--many how-to's also forget to mention this.

---

### Post by SlalomMan on 2008-08-01
Alright, I'll blacklist those now. I installed Ndiswrapper and a GUI front end for it, and I downloaded the XP drivers from intel's site. However, there are a few .inf files...and there's an exe file, which I assume is for windows. I could wine it, but I don't think that would do much good; and I'm not sure which INF file to use with Ndiswrapper...
any suggestions?

---

### Post by pytheas22 on 2008-08-01
> However, there are a few .inf files...and there's an exe file, which I assume is for windows. I could wine it, but I don't think that would do much good; and I'm not sure which INF file to use with Ndiswrapper...
any suggestions?

If you open up the .exe in wine, it might first ask you to choose a location for extracting files; pick a folder on your desktop or something, let it extract the files, then kill the installer.

Alternatively, a better, but less adventurous, way to extract .exe's it is to install cabextract:
```

sudo apt-get install cabextract
```

and extract the .exe with:
```

cabextract /path/to/installer.exe
```

I'm wondering however why there's a .exe file AND .inf files--generally the .inf files would be inside the .exe, or there would be no .exe at all (unless it's to install something like a program to control the wireless on Windows).  Can you provide a link to the drivers that you downloaded?  I'll take a look and see if I can tell which .inf you should use--although it may come down to trial and error.

---

### Post by SlalomMan on 2008-08-01
I downloaded the first item from [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Windows*+XP+Home+Edition&lang=eng&strOSs=45&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Windows*+XP+Home+Edition&lang=eng&strOSs=45&submit=Go)!

It said "drivers only" so i'd assume there was no wireless app or whatever in there. And XP drivers would be okay, right?

EDIT: I think that the NETw4x32.inf worked; the NETw4k32 said invalid driver when I tried ndiswrapper with it; the NETw4x32 returned "unable to see if hardware is present"; but the w29n51 also said "unable to see if hardware is present" so I"m not sure what to do now.

On the gui, Netw4x32 says hardware present: yes

and the w29n51 says hardware present: no. I'll try to see if this worked in a little bit.

---

### Post by pytheas22 on 2008-08-01
Yes, the XP drivers should be alright--although sometimes it's hit and miss with ndiswrapper and using a different release of the drivers would make a difference.  But try to connect now with Netw4x32 and see how it goes.

---

### Post by SlalomMan on 2008-08-01
Well I don't think it worked; No networks showed up in roaming and when I tried to "join other network" it wouldn't connect. I'm not even sure if I'm using ndiswrapper right because I'm using a GUI front end i downloaded from the repository.

---

### Post by pytheas22 on 2008-08-01
The frontend is called ndisgtk and it's alright to use it.

To help figure out what could be wrong, what is the output of:
```

uname -n
ndiswrapper -l
lshw -C Network
```

---

### Post by SlalomMan on 2008-08-02
uname -n returns "kyle-laptop"

ndiswrapper -l returns:
netw4x32 : driver installed
	device (8086:4229) present (alternate driver: iwl4965)
w29n51 : driver installed

and lshw -C Network returns:
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:78:32:e4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:1b:22:c7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw4x32 driverversion=1.52+Intel,03/13/2008,11.5.1.15 ip=192.168.1.102 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

I turned on my computer this morning and found that it had connected to my wireless network all by itself; I am assuming the outputs mean that Ndiswrapper is working, and the speed is a little faster than it was before, usable at the least. Thanks for the help.

EDIT: After some browsing today, I can safely say that it is A LOT faster with the Ndiswrapper driver. Youtube videos load quickly and I don't have to wait to play them because they load faster than it plays...My only complaint is that it seems like I get lower signal strength, but I don't know how much I usually get; it's much better, nonetheless. Maybe later I will try to get the linuxwireless drivers to work, but for now, I'm happy.

---

### Post by pytheas22 on 2008-08-02
Alright, I'm glad it seems to be working better now.  I think that the whole root of the problem was a bug with the Intel driver, which seems to have been fixed in the source code; that means that pretty soon, the fix should get pushed out through Ubuntu updates as well, and you could revert back to the native Intel driver.  If you want to switch back to iwl4965, you just need to remove these lines from /etc/modprobe.d/blacklist:
```

blacklist iwl4965
blacklist iwl3495
```

and replace them with:
```

blacklist ndiswrapper
```

Then reboot.

Also, I'm not sure whether Ubuntu updates will update your wireless drivers, since you custom-compiled them.  I think you may need to run "sudo make uninstall" on the linuxwireless stuff in order for system updates to apply to the wireless again...the linuxwireless website mentioned something like that.

---

### Post by SlalomMan on 2008-08-02
Alright, thanks for all of your help; I guess this thread is solved for now, I'll mark it as that.

---

