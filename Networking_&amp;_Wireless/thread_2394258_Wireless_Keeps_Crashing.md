---
title: "Wireless Keeps Crashing"
date: 2018-06-14
forum: Networking &amp; Wireless
---

### Post by satluri on 2018-06-14
[COLOR=#000000]Did a fresh install of Ubuntu 18.04 LTS, but my computer now periodically crashes. Seems to have to do with my WiFi? It's integrated with my motherboard ([/COLOR][https://www.asrock.com/mb/Intel/Z370%20Taichi/](https://www.asrock.com/mb/Intel/Z370%20Taichi/)[COLOR=#000000])[/COLOR]

[COLOR=#000000]Never had this issue on 16.04 LTS. Below is what I see in /var/log/kern.log[/COLOR]

[COLOR=#000000]Jun 10 20:45:57 Fractal kernel: [ 6993.277247] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd[/COLOR]
[COLOR=#000000]Jun 10 20:45:57 Fractal kernel: [ 6993.277254] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5[/COLOR]
[COLOR=#000000]Jun 10 20:45:57 Fractal kernel: [ 6993.277255] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)[/COLOR]
[COLOR=#000000]Jun 10 20:45:59 Fractal kernel: [ 6995.306718] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd[/COLOR]
[COLOR=#000000]Jun 10 20:45:59 Fractal kernel: [ 6995.306727] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5[/COLOR]
[COLOR=#000000]Jun 10 20:45:59 Fractal kernel: [ 6995.306728] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)[/COLOR]
[COLOR=#000000]Jun 10 20:46:01 Fractal kernel: [ 6997.335792] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd[/COLOR]
[COLOR=#000000]Jun 10 20:46:01 Fractal kernel: [ 6997.335799] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5[/COLOR]
[COLOR=#000000]Jun 10 20:46:01 Fractal kernel: [ 6997.335800] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)[/COLOR]
[COLOR=#000000]Jun 10 20:46:03 Fractal kernel: [ 6999.365298] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd[/COLOR]
[COLOR=#000000]Jun 10 20:46:03 Fractal kernel: [ 6999.365307] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5[/COLOR]
[COLOR=#000000]Jun 10 20:46:03 Fractal kernel: [ 6999.365308] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)[/COLOR]
[COLOR=#000000]Jun 10 20:46:05 Fractal kernel: [ 7001.394717] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd[/COLOR]
[COLOR=#000000]Jun 10 20:46:05 Fractal kernel: [ 7001.394725] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5[/COLOR]
[COLOR=#000000]Jun 10 20:46:05 Fractal kernel: [ 7001.394726] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)[/COLOR]
[COLOR=#000000]Jun 10 20:46:07 Fractal kernel: [ 7003.423809] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd[/COLOR]
[COLOR=#000000]Jun 10 20:46:07 Fractal kernel: [ 7003.423817] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5[/COLOR]
[COLOR=#000000]Jun 10 20:46:07 Fractal kernel: [ 7003.423819] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)[/COLOR]
[COLOR=#000000]Jun 10 20:46:09 Fractal kernel: [ 7005.453260] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd[/COLOR]
[COLOR=#000000]Jun 10 20:46:09 Fractal kernel: [ 7005.453267] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5[/COLOR]
[COLOR=#000000]Jun 10 20:46:09 Fractal kernel: [ 7005.453268] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)[/COLOR]
[COLOR=#000000]Jun 10 20:46:11 Fractal kernel: [ 7007.482595] iwlwifi 0000:05:00.0: Failed to wake NIC for hcmd[/COLOR]
[COLOR=#000000]Jun 10 20:46:11 Fractal kernel: [ 7007.482603] iwlwifi 0000:05:00.0: Error sending CMD_DTS_MEASUREMENT_TRIGGER_WIDE: enqueue_hcmd failed: -5[/COLOR]
[COLOR=#000000]Jun 10 20:46:11 Fractal kernel: [ 7007.482606] iwlwifi 0000:05:00.0: Failed to get the temperature (err=-5)[/COLOR]

[COLOR=#000000]...[/COLOR]

[COLOR=#000000](repeats forever until I hit the reset button on my computer)[/COLOR]

[COLOR=#000000]Any help on how to resolve this would be much appreciated![/COLOR]

---

### Post by Steve White on 2018-09-09
I have had frequent WIFI crashes and apparently WIFI-related system crashes on two generations of Acer laptops; now I'm seeing log messages just like those.

This machine is a TravelMate 1B.  I have updated to the most recent BIOS -- I thought for a while it helped, but now the problem has returned.
The problem happens erratically -- sometimes it goes days without problems, some days I can hardly get WIFI -- it looks like it has no WIFI device -- even after re-booting.
I have noted that the machine often gets very warm.  Often just as the problem starts, the trackpad response begins dropping out.

A hard reset (holding the power button down to cycle throught the splash screen) seems to help when it really gets stuck.

/proc/cpuinfo shows Intel(R) Pentium(R) CPU  N3710  @ 1.60GHz
lspci shows Network controller: Intel Corporation Wireless 7265 (rev 59)
lsmod shows net and wifi related drivers:
nf_conntrack_netbios_ns    16384  0
nf_conntrack_broadcast    16384  1 nf_conntrack_netbios_ns
nf_conntrack          131072  8 nf_conntrack_ipv6,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_broadcast,nf_nat_ftp,nf_conntrack_netbios_ns,xt_conntrack,nf_nat
iwlwifi               282624  1 iwlmvm
cfg80211              622592  3 iwlmvm,iwlwifi,mac80211


It has occured to me it might be temperature-related, and in fact I have seen the CPU temperature get up to 65°C when problems started happening (and top sometimes showed Firefox at 100% CPU -- don't know if it's related).  I looked into the possibility of throttling the CPU -- everything seems in place to implement that, but as near as I can' tell, nothing is actually performing throttling at this time.

I too would like a solution!

---

