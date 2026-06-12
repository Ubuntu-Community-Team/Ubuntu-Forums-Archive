---
title: "Intel 4965 GN Wireless won't work depsite all efforts"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by mattl320 on 2008-04-04
I have read all the posts on Ubuntu and other linux forums.  I am using PCLINUXOS...a sweet distro for a newbie like me....However, my attempts to get my wireless working has failed repeatedly with Ubuntu, Mandrake, Suse, Fedora and now PCLINUXOS.  I know it's because I don't know what I am doing.  Please help if you can.

Using ndiswrapper, I tried to install the netw4v32.inf driver for my 4965AGN intel wireless card. It appeared to fail with an error message that stated no device found or something of that nature.  I opened terminal and ran ndiswrapper -l which gave me the following output.

[root@localhost mattl320]# ndiswrapper -l
airplus : driver installed
bcmwl5 : driver installed
bcmwl5a : driver installed
blkwgnv7 : driver installed
lsbcmnds6 : driver installed
lstinds : driver installed
mrv8k51 : driver installed
net5211 : driver installed
net8185 : driver installed
netr33x : driver installed
netw4v32 : driver installed
        device (8086:4229) present (alternate driver: iwl4965)
prismnic : driver installed
rt2500 : driver installed
rt73 : driver installed
sis163u : driver installed
wlannic : driver installed
wlanuig : driver installed
wlipnds : driver installed
[root@localhost mattl320]# 

I'm using a Sony Vaio VGN-CR190 laptop.  I've tried turning the wireless switch off before installing the driver as well with no success. 

I also ran lspci to add more info that may be helpful.
Here's that output.

[root@localhost mattl320]# lspci
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation Mobile SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
08:07.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


Since ndiswrapper obviously didn't work, I went to Intel's website and was directed from there to another website ([http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)) for the driver which gave me instructions for installing the Intel driver for linux.  This did not work either. Here is what happened.


[root@localhost mattl320]# wget \
> [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.17.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.17.tgz)
--13:42:43--  [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.17.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.17.tgz)
           => `iwlwifi-4965-ucode-4.44.17.tgz'
Resolving intellinuxwireless.org... 204.253.143.234
Connecting to intellinuxwireless.org|204.253.143.234|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 83,700 (82K) [application/x-gzip]

100%[====================================>] 83,700       147.45K/s             

13:42:43 (146.99 KB/s) - `iwlwifi-4965-ucode-4.44.17.tgz' saved [83700/83700]

[root@localhost mattl320]# tar xvf iwlwifi-4965-ucode-4.44.17.tgz
iwlwifi-4965-ucode-4.44.17/
iwlwifi-4965-ucode-4.44.17/iwlwifi-4965.ucode
iwlwifi-4965-ucode-4.44.17/LICENSE.iwlwifi-4965-ucode
iwlwifi-4965-ucode-4.44.17/README.iwlwifi-4965-ucode
[root@localhost mattl320]# cp iwlwifi-4965-ucode-4.44.17/iwlwifi-4965.ucode /lib/firmware/
[root@localhost mattl320]# wget \
> 
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
[root@localhost mattl320]# wget \
> http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-1.2.25.tgz
--13:44:24--  http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-1.2.25.tgz
           => `iwlwifi-1.2.25.tgz'
Resolving intellinuxwireless.org... 204.253.143.234
Connecting to intellinuxwireless.org|204.253.143.234|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 368,111 (359K) [application/x-gzip]

100%[====================================>] 368,111      219.88K/s             

13:44:26 (219.60 KB/s) - `iwlwifi-1.2.25.tgz' saved [368111/368111]

[root@localhost mattl320]# tar xvf iwlwifi-1.2.25.tgz
iwlwifi-1.2.25/
iwlwifi-1.2.25/CHANGES
iwlwifi-1.2.25/LICENSE.BSD
iwlwifi-1.2.25/load
iwlwifi-1.2.25/scripts/
iwlwifi-1.2.25/scripts/determine_compat
iwlwifi-1.2.25/scripts/patch_kernel
iwlwifi-1.2.25/scripts/check_kernel
iwlwifi-1.2.25/scripts/make_snapshot
iwlwifi-1.2.25/scripts/generate_compatible
iwlwifi-1.2.25/FILES
iwlwifi-1.2.25/ISSUES
iwlwifi-1.2.25/Makefile
iwlwifi-1.2.25/LICENSE
iwlwifi-1.2.25/origin/
iwlwifi-1.2.25/origin/iwl4965-base.c
iwlwifi-1.2.25/origin/iwl-3945.c
iwlwifi-1.2.25/origin/iwl-3945.h
iwlwifi-1.2.25/origin/iwl-3945-hw.h
iwlwifi-1.2.25/origin/iwl-4965-hw.h
iwlwifi-1.2.25/origin/iwl-3945-debug.h
iwlwifi-1.2.25/origin/iwl-spectrum.h
iwlwifi-1.2.25/origin/iwl-4965-io.h
iwlwifi-1.2.25/origin/iwl-3945-rs.c
iwlwifi-1.2.25/origin/iwl-helpers.h
iwlwifi-1.2.25/origin/iwl-4965-rs.h
iwlwifi-1.2.25/origin/iwl-4965-rs.c
iwlwifi-1.2.25/origin/iwl3945-base.c
iwlwifi-1.2.25/origin/Makefile
iwlwifi-1.2.25/origin/iwl-3945-commands.h
iwlwifi-1.2.25/origin/iwl-3945-io.h
iwlwifi-1.2.25/origin/iwl-4965.h
iwlwifi-1.2.25/origin/iwl-4965-commands.h
iwlwifi-1.2.25/origin/iwl-4965.c
iwlwifi-1.2.25/origin/iwl-4965-debug.h
iwlwifi-1.2.25/origin/iwl-3945-rs.h
iwlwifi-1.2.25/origin/iwl-prph.h
iwlwifi-1.2.25/origin/Kconfig
iwlwifi-1.2.25/patches/
iwlwifi-1.2.25/patches/08-is_power_of_2.patch
iwlwifi-1.2.25/patches/i_private.sh
iwlwifi-1.2.25/patches/01-queue_delayed_work.sh
iwlwifi-1.2.25/patches/04-rx_flag_radiotap.patch
iwlwifi-1.2.25/patches/02-cancel_delayed_work.sh
iwlwifi-1.2.25/patches/09-cancel_work_sync.patch
iwlwifi-1.2.25/patches/03-isr.patch
iwlwifi-1.2.25/patches/06-csa.patch
iwlwifi-1.2.25/patches/wlan_80211.patch
iwlwifi-1.2.25/patches/07-hex_dump.patch
iwlwifi-1.2.25/patches/10-preferred_rate_control.patch
iwlwifi-1.2.25/patches/05-delayed_work_define.patch
iwlwifi-1.2.25/patches/02-kcompat_delayed_work.patch
iwlwifi-1.2.25/patches/.keep
iwlwifi-1.2.25/LICENSE.GPL
iwlwifi-1.2.25/dvals
iwlwifi-1.2.25/README.iwlwifi
iwlwifi-1.2.25/GIT_SHA1
iwlwifi-1.2.25/unload
iwlwifi-1.2.25/INSTALL
[root@localhost mattl320]# cd iwlwifi-1.2.25
[root@localhost iwlwifi-1.2.25]# make
Checking kernel compatibility in:
        /lib/modules/2.6.22.15.tex3/source
grep: /lib/modules/2.6.22.15.tex3/source/net/mac80211/sta_info.h: No such file or directory
grep: /lib/modules/2.6.22.15.tex3/source/lib/hexdump.c: No such file or directory
grep: /lib/modules/2.6.22.15.tex3/source/kernel/workqueue.c: No such file or directory
 * Kernel requires compatibility version:
   - Requires IEEE80211_CONF_CHANNEL_SWITCH compat.
   - Remove CONFIG_IWL4965_HT_AGG option if defined
   - Requires hex_dump compat
   - Requires cancel_work_sync avoidance
Building compatibility version in 'compatible/' directory:
Copying compatible/ from origin/...done
 + Applying: patches/06-csa.patch
        diff -urp old/iwl-helpers.h origin/iwl-helpers.h
 + Applying: patches/07-hex_dump.patch
        diff -urp origin/iwl3945-base.c new/iwl3945-base.c
 + Applying: patches/09-cancel_work_sync.patch
        diff -urp origin/iwl3945-base.c new/iwl3945-base.c

Makefile has been modified by generate_compatible, please run `make' again

make: *** [compatible/kversion] Error 1
[root@localhost iwlwifi-1.2.25]# make
make -C /lib/modules/2.6.22.15.tex3/source O=/lib/modules/2.6.22.15.tex3/build M=/home/mattl320/iwlwifi-1.2.25/compatible/ EXTRA_CFLAGS="-DCONFIG_IWL3945_DEBUG=y -DCONFIG_IWL4965_DEBUG=y -DCONFIG_IWL3945_SPECTRUM_MEASUREMENT=y -DCONFIG_IWL4965_SPECTRUM_MEASUREMENT=y -DCONFIG_IWL4965_HT=y -DCONFIG_IWL4965_SENSITIVITY=y -DCONFIG_IWL3945_QOS=y -DCONFIG_IWL4965_QOS=y" modules
make[1]: Entering directory `/usr/src/linux-2.6.22.15.tex3'
  CC [M]  /home/mattl320/iwlwifi-1.2.25/compatible/iwl3945-base.o
/home/mattl320/iwlwifi-1.2.25/compatible/iwl3945-base.c:8516: warning: initialization from incompatible pointer type
  CC [M]  /home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945.o
  CC [M]  /home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.o
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:43:44: error: ../net/mac80211/ieee80211_rate.h: No such file or directory
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:334: warning: &#8216;struct sta_info&#8217; declared inside parameter list
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:334: warning: its scope is only this definition or declaration, which is probably not what you want
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:334: warning: &#8216;struct ieee80211_local&#8217; declared inside parameter list
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: In function &#8216;rs_rate_init&#8217;:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:346: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:347: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:352: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:352: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:355: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:356: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: At top level:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:361: warning: &#8216;struct ieee80211_local&#8217; declared inside parameter list
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: In function &#8216;rs_alloc&#8217;:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:363: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: In function &#8216;rs_tx_status&#8217;:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:483: warning: implicit declaration of function &#8216;sta_info_get&#8217;
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:483: warning: assignment makes pointer from integer without a cast
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:484: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:486: warning: implicit declaration of function &#8216;sta_info_put&#8217;
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:491: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: At top level:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:567: warning: &#8216;struct ieee80211_local&#8217; declared inside parameter list
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: In function &#8216;iwl3945_get_lowest_rate&#8217;:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:569: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: At top level:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:663: warning: &#8216;struct rate_control_extra&#8217; declared inside parameter list
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: In function &#8216;rs_get_rate&#8217;:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:685: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:685: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:685: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:685: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:685: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:685: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:696: warning: passing argument 1 of &#8216;iwl3945_get_lowest_rate&#8217; from incompatible pointer type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:699: warning: assignment makes pointer from integer without a cast
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:700: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:707: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:708: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:708: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_x&#8217;
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:708: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:713: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:761: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:839: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:841: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:841: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:843: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:843: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: At top level:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:852: error: variable &#8216;rs_ops&#8217; has initializer but incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:853: error: unknown field &#8216;module&#8217; specified in initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:853: warning: excess elements in struct initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:853: warning: (near initialization for &#8216;rs_ops&#8217;)
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:854: error: unknown field &#8216;name&#8217; specified in initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:854: warning: excess elements in struct initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:854: warning: (near initialization for &#8216;rs_ops&#8217;)
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:855: error: unknown field &#8216;tx_status&#8217; specified in initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:855: warning: excess elements in struct initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:855: warning: (near initialization for &#8216;rs_ops&#8217;)
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:856: error: unknown field &#8216;get_rate&#8217; specified in initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:856: warning: excess elements in struct initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:856: warning: (near initialization for &#8216;rs_ops&#8217;)
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:857: error: unknown field &#8216;rate_init&#8217; specified in initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:857: warning: excess elements in struct initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:857: warning: (near initialization for &#8216;rs_ops&#8217;)
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:858: error: unknown field &#8216;clear&#8217; specified in initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:858: warning: excess elements in struct initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:858: warning: (near initialization for &#8216;rs_ops&#8217;)
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:859: error: unknown field &#8216;alloc&#8217; specified in initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:859: warning: excess elements in struct initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:859: warning: (near initialization for &#8216;rs_ops&#8217;)
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:860: error: unknown field &#8216;free&#8217; specified in initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:860: warning: excess elements in struct initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:860: warning: (near initialization for &#8216;rs_ops&#8217;)
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:861: error: unknown field &#8216;alloc_sta&#8217; specified in initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:861: warning: excess elements in struct initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:861: warning: (near initialization for &#8216;rs_ops&#8217;)
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:862: error: unknown field &#8216;free_sta&#8217; specified in initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:862: warning: excess elements in struct initializer
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:862: warning: (near initialization for &#8216;rs_ops&#8217;)
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: In function &#8216;iwl3945_fill_rs_info&#8217;:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:867: warning: implicit declaration of function &#8216;hw_to_local&#8217;
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:867: warning: initialization makes pointer from integer without a cast
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:877: warning: assignment makes pointer from integer without a cast
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:878: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:887: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: In function &#8216;iwl3945_rate_scale_init&#8217;:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:948: warning: initialization makes pointer from integer without a cast
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:954: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:955: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:961: warning: assignment makes pointer from integer without a cast
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:962: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:969: error: dereferencing pointer to incomplete type
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: In function &#8216;iwl3945_rate_control_register&#8217;:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:1013: warning: implicit declaration of function &#8216;ieee80211_rate_control_register&#8217;
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c: In function &#8216;iwl3945_rate_control_unregister&#8217;:
/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.c:1018: warning: implicit declaration of function &#8216;ieee80211_rate_control_unregister&#8217;
make[3]: *** [/home/mattl320/iwlwifi-1.2.25/compatible/iwl-3945-rs.o] Error 1
make[2]: *** [_module_/home/mattl320/iwlwifi-1.2.25/compatible] Error 2
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.22.15.tex3'
make: *** [modules] Error 2
[root@localhost iwlwifi-1.2.25]# make install
make: *** No rule to make target `compatible/iwl4965.ko', needed by `install'.  Stop.
[root@localhost iwlwifi-1.2.25]# make install
make: *** No rule to make target `compatible/iwl4965.ko', needed by `install'.  Stop.
[root@localhost iwlwifi-1.2.25]# dmesg -c > /dev/null
[root@localhost iwlwifi-1.2.25]# ./load debug=0x43fff
./unload: line 23: lsmod: command not found
./unload: line 23: lsmod: command not found
./unload: line 23: lsmod: command not found
./unload: line 23: lsmod: command not found
No modules unloaded.
./load: line 28: lsmod: command not found
./load: line 28: lsmod: command not found
./load: line 28: lsmod: command not found
No modules loaded.
[root@localhost iwlwifi-1.2.25]# ifconfig wlan0 up
bash: ifconfig: command not found
[root@localhost iwlwifi-1.2.25]# 


Thanks in advance for any help!  Please respond in newbie fashion so that I can comprehend any suggestions or tips.  Thank you very much in advance!

---

