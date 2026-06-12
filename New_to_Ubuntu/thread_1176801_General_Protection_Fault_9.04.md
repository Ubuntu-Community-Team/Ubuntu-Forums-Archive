---
title: "General Protection Fault 9.04"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by CylnZ on 2009-06-02
So, Im cruising along reading the forums here just 1 instance of firefox open with 1 extra tab open, no xtra apps running etc and <SLAP> this happens:

```
kernel: [23624.652219] general protection fault: 0000 [#1] SMP 
Jun  2 16:59:49 john-laptop1 kernel: [23624.652228] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/statistics/collisions
Jun  2 16:59:49 john-laptop1 kernel: [23624.652233] Dumping ftrace buffer:
Jun  2 16:59:49 john-laptop1 kernel: [23624.652238]    (ftrace buffer empty)
Jun  2 16:59:49 john-laptop1 kernel: [23624.652241] CPU 1 
Jun  2 16:59:49 john-laptop1 kernel: [23624.652244] Modules linked in: aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs input_polldev ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_state ipt_addrtype ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables joydev coretemp lp parport snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss arc4 ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwlagn iwlcore snd_seq lmpcm_usb snd_timer snd_seq_device led_class mac80211 snd soundcore uvcvideo snd_page_alloc cfg80211 compat_ioctl32 videodev v4l1_compat iTCO_wdt iTCO_vendor_support usbhid psmouse serio_rawJun  2 17:01:31 john-laptop1 syslogd 1.5.0#5ubuntu3: restart.
Jun  2 17:01:31 john-laptop1 kernel: Inspecting /boot/System.map-2.6.28-12-generic

```Thoughts??

---

### Post by randallecook on 2009-06-02
Does this happen consistently, or was it just a one-time event?

Randall

---

### Post by CylnZ on 2009-06-02
1st time I've had a hardware lock up since release of 9.04 that wasnt readily apparent due to something I was doing (drivers/config etc) and the second overall crash since last Friday when I tried out firefox 3.5, but ff3.5 has been totally removed right after crash.

64bit ubuntu 9.04, 2.6.28.12 generic, with custom dsdt, ext4 on a 6860fx

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800M GTS (rev a2)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

```syslog from 1 hour before up to GPF

```
Jun  2 16:00:02 john-laptop1 /USR/SBIN/CRON[11811]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Jun  2 16:00:02 john-laptop1 /USR/SBIN/CRON[11812]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  2 16:10:01 john-laptop1 /USR/SBIN/CRON[12053]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  2 16:17:01 john-laptop1 /USR/SBIN/CRON[12260]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  2 16:20:01 john-laptop1 /USR/SBIN/CRON[12321]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  2 16:26:24 john-laptop1 sensord: Chip: acpitz-virtual-0
Jun  2 16:26:24 john-laptop1 sensord: Adapter: Virtual device
Jun  2 16:26:24 john-laptop1 sensord:   temp1: 41.0 C
Jun  2 16:26:24 john-laptop1 sensord:   temp2: 48.0 C
Jun  2 16:26:24 john-laptop1 sensord: Chip: coretemp-isa-0000
Jun  2 16:26:24 john-laptop1 sensord: Adapter: ISA adapter
Jun  2 16:26:24 john-laptop1 sensord:   Core 0: 41.0 C
Jun  2 16:26:24 john-laptop1 sensord: Chip: coretemp-isa-0001
Jun  2 16:26:24 john-laptop1 sensord: Adapter: ISA adapter
Jun  2 16:26:24 john-laptop1 sensord:   Core 1: 44.0 C
Jun  2 16:30:02 john-laptop1 /USR/SBIN/CRON[12528]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  2 16:40:01 john-laptop1 /USR/SBIN/CRON[12755]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  2 16:40:51 john-laptop1 NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake 
Jun  2 16:40:51 john-laptop1 NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Jun  2 16:50:01 john-laptop1 /USR/SBIN/CRON[12993]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jun  2 16:56:24 john-laptop1 sensord: Chip: acpitz-virtual-0
Jun  2 16:56:24 john-laptop1 sensord: Adapter: Virtual device
Jun  2 16:56:24 john-laptop1 sensord:   temp1: 27.0 C
Jun  2 16:56:24 john-laptop1 sensord:   temp2: 32.0 C
Jun  2 16:56:24 john-laptop1 sensord: Chip: coretemp-isa-0000
Jun  2 16:56:24 john-laptop1 sensord: Adapter: ISA adapter
Jun  2 16:56:24 john-laptop1 sensord:   Core 0: 21.0 C
Jun  2 16:56:24 john-laptop1 sensord: Chip: coretemp-isa-0001
Jun  2 16:56:24 john-laptop1 sensord: Adapter: ISA adapter
Jun  2 16:56:24 john-laptop1 sensord:   Core 1: 25.0 C
Jun  2 16:59:49 john-laptop1 kernel: [23624.652219] general protection fault: 0000 [#1] SMP 
Jun  2 16:59:49 john-laptop1 kernel: [23624.652228] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0/statistics/collisions
Jun  2 16:59:49 john-laptop1 kernel: [23624.652233] Dumping ftrace buffer:
Jun  2 16:59:49 john-laptop1 kernel: [23624.652238]    (ftrace buffer empty)
Jun  2 16:59:49 john-laptop1 kernel: [23624.652241] CPU 1 
Jun  2 16:59:49 john-laptop1 kernel: [23624.652244] Modules linked in: aes_x86_64 aes_generic binfmt_misc ppdev bridge stp bnep nfsd lockd nfs_acl auth_rpcgss sunrpc exportfs input_polldev ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_state ipt_addrtype ip6table_filter ip6_tables nf_nat_irc nf_conntrack_irc nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables joydev coretemp lp parport snd_hda_codec_idt snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss arc4 ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iwlagn iwlcore snd_seq lmpcm_usb snd_timer snd_seq_device led_class mac80211 snd soundcore uvcvideo snd_page_alloc cfg80211 compat_ioctl32 videodev v4l1_compat iTCO_wdt iTCO_vendor_support usbhid psmouse serio_rawJun  2 17:01:31 john-laptop1 syslogd 1.5.0#5ubuntu3: restart.
Jun  2 17:01:31 john-laptop1 kernel: Inspecting /boot/System.map-2.6.28-12-generic

```let me know anything that could be helpful

---

### Post by seaq on 2009-06-22
maybe is this same bug

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/364441](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/364441)

---

