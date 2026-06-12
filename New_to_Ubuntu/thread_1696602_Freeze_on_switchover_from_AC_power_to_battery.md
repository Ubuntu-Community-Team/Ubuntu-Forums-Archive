---
title: "Freeze on switchover from AC power to battery"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by Subhajit on 2011-02-27
Hello,

I have installed Ubuntu 10.10 in my dell-vostro laptop as single boot OS. nice experience as everything is working fine.

however, if there is a power disruption and the laptop needs to switch to battery the OS freezes. (I didnot say X freezes as I could not even switch to console mode pressing cntrl+alt+F1). I am not sure if the same would happen if it switches from battery to ac power. 

however, upon resetting the machine, it can run on battery mode. the problem occurs only while switching. 

 kindly help me as power line  fluctuations are very common here.

---

### Post by Subhajit on 2011-02-28
Adding to the previous post: I did try out some permutations. its like this lock up happens when i have Firefox running and a power fluctuation occurs (even momentarily). checked through syslog. The log entries around the time of crash are given below: 

```
Feb 28 02:55:26 tiger kernel: [   26.616062] eth0: no IPv6 routers present
Feb 28 02:55:32 tiger gdm-session-worker[1421]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Feb 28 02:55:37 tiger NetworkManager[1018]: <error> [1298841937.29526] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Feb 28 02:55:37 tiger NetworkManager[1018]: <error> [1298841937.49824] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Feb 28 02:55:37 tiger kernel: [   37.925264] Skipping EDID probe due to cached edid
Feb 28 02:55:37 tiger kernel: [   37.976093] Skipping EDID probe due to cached edid
Feb 28 02:55:37 tiger kernel: [   38.041219] Skipping EDID probe due to cached edid
Feb 28 02:55:37 tiger kernel: [   38.068070] Skipping EDID probe due to cached edid
Feb 28 02:55:38 tiger rtkit-daemon[1429]: Successfully made thread 1637 of process 1637 (n/a) owned by '1000' high priority at nice level -11.
Feb 28 02:55:38 tiger rtkit-daemon[1429]: Supervising 4 threads of 2 processes of 2 users.
Feb 28 02:55:38 tiger rtkit-daemon[1429]: Successfully made thread 1649 of process 1637 (n/a) owned by '1000' RT at priority 5.
Feb 28 02:55:38 tiger rtkit-daemon[1429]: Supervising 5 threads of 2 processes of 2 users.
Feb 28 02:55:38 tiger rtkit-daemon[1429]: Successfully made thread 1650 of process 1637 (n/a) owned by '1000' RT at priority 5.
Feb 28 02:55:38 tiger rtkit-daemon[1429]: Supervising 6 threads of 2 processes of 2 users.
Feb 28 02:55:38 tiger NetworkManager[1018]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb 28 02:55:38 tiger rtkit-daemon[1429]: Successfully made thread 1659 of process 1659 (n/a) owned by '1000' high priority at nice level -11.
Feb 28 02:55:38 tiger rtkit-daemon[1429]: Supervising 7 threads of 3 processes of 2 users.
Feb 28 02:55:38 tiger pulseaudio[1659]: pid.c: Daemon already running.
Feb 28 02:55:38 tiger kernel: [   38.949079] Skipping EDID probe due to cached edid
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 24.
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c: snd_pcm_dump():
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c: Soft volume PCM
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c: Control: PCM Playback Volume
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c: min_dB: -51
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c: max_dB: 0
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c: resolution: 256
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c: Its setup is:
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   stream       : CAPTURE
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   format       : S16_LE
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   subformat    : STD
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   channels     : 2
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   rate         : 44100
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   msbits       : 16
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   buffer_size  : 88192
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   period_size  : 44096
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   period_time  : 999909
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   tstamp_mode  : ENABLE
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   period_step  : 1
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   avail_min    : 87310
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   period_event : 0
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   start_threshold  : -1
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   stop_threshold   : 1444937728
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   silence_threshold: 0
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   silence_size : 0
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   boundary     : 1444937728
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c: Its setup is:
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   stream       : CAPTURE
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   access       : MMAP_INTERLEAVED
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   format       : S16_LE
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   subformat    : STD
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   channels     : 2
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   rate         : 44100
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   exact rate   : 44100 (44100/1)
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   msbits       : 16
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   buffer_size  : 88192
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   period_size  : 44096
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   period_time  : 999909
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   tstamp_mode  : ENABLE
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   period_step  : 1
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   avail_min    : 87310
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   period_event : 0
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   start_threshold  : -1
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   stop_threshold   : 1444937728
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   silence_threshold: 0
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   silence_size : 0
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   boundary     : 1444937728
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   appl_ptr     : 87336
Feb 28 02:55:40 tiger pulseaudio[1637]: alsa-util.c:   hw_ptr       : 87336
Feb 28 02:55:42 tiger kernel: [   43.148068] Skipping EDID probe due to cached edid
Feb 28 02:56:46 tiger NetworkManager[1018]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Feb 28 02:58:21 tiger NetworkManager[1018]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
```this might be of some help.

---

### Post by Subhajit on 2011-03-01
ping! anyone?

---

### Post by Subhajit on 2011-03-06
Can anyone please help me on this? 

let me elaborate the situation better. I have configured my network interface by editing /etc/network/interfaces and not from system->preferences->network connections

when I have a power outage the lan switch i am connected to goes off. and my system freezes if any network operation is going on at that time.

---

### Post by rez182 on 2011-04-01
i have a similar problem. except mine does not even boot in battery mode also freezes when switching from A/C to battery.

Been like this ever since Ubuntu 10.10 (first ever) installation. i have a dual boot with win7, which runs perfectly. hopefully in the next ubuntu release it wont happen. i seriously want to stick to linux.

here are the threads that i started for this problem.
[Ubuntu crashes in battery mode (EVERYTIME)]("http://ubuntuforums.org/showthread.php?t=1717584")
[Ubuntu crash when A/C plugged out suddently]("http://ubuntuforums.org/showthread.php?t=1717314")

---

