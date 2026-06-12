---
title: "Atheros AR9485 Wireless Network Adapter problems"
date: 2014-07-25
forum: Networking &amp; Wireless
---

### Post by medeirosat on 2014-07-25
Hello, I recently installed the latest version of kubuntu on my system and it's giving me some problems. The system is a bit unstable and I think it because of the wirless adapter. I'm kind of a begginer on Linux, so please bear with me.
I had the bug seen on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173681](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173681) so I did the workaround described there and it worked fine. But recently I noticed some instability in my system so I went to syslog and saw this there
```
2014-07-25 10:57:18    andre-X550CC    wpa_supplicant[1172]    wlan0: CTRL-EVENT-SCAN-STARTED 
2014-07-25 11:01:18    andre-X550CC    wpa_supplicant[1172]    message repeated 2 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
2014-07-25 11:01:21    andre-X550CC    wpa_supplicant[1172]    nl80211: send_and_recv->nl_recvmsgs failed: -33
2014-07-25 11:03:18    andre-X550CC    wpa_supplicant[1172]    wlan0: CTRL-EVENT-SCAN-STARTED 
2014-07-25 11:03:21    andre-X550CC    wpa_supplicant[1172]    nl80211: send_and_recv->nl_recvmsgs failed: -33
2014-07-25 11:05:18    andre-X550CC    wpa_supplicant[1172]    wlan0: CTRL-EVENT-SCAN-STARTED 
2014-07-25 11:05:21    andre-X550CC    wpa_supplicant[1172]    nl80211: send_and_recv->nl_recvmsgs failed: -33
2014-07-25 11:07:18    andre-X550CC    wpa_supplicant[1172]    wlan0: CTRL-EVENT-SCAN-STARTED 

```

it is spamming in the log like crazy.

I also found something else that it's not related to the wlan problem, don't know what is causing the freezes/instability, and I don't know were to start looking.
Here is what i found so far

```
Jul 25 00:39:52 andre-X550CC dbus[766]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 25 00:39:52 andre-X550CC dbus[766]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: snd_pcm_avail() retornou um valor excepcionalmente elevado: 5542828 bytes (31421 ms).
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Provavelmente isto é um erro no driver ALSA 'snd_hda_intel'. Por favor, reporte este problema aos programadores do ALSA.
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: snd_pcm_dump():
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Soft volume PCM
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Control: PCM Playback Volume
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: min_dB: -51
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: max_dB: 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: resolution: 256
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Its setup is:
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   stream       : PLAYBACK
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   format       : S16_LE
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   subformat    : STD
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   channels     : 2
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   rate         : 44100
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   msbits       : 16
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   buffer_size  : 16384
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_size  : 8192
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_time  : 185759
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_step  : 1
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   avail_min    : 15503
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_event : 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   start_threshold  : -1
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   silence_threshold: 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   silence_size : 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   boundary     : 4611686018427387904
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel PCH' device 0 subdevice 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Its setup is:
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   stream       : PLAYBACK
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   format       : S16_LE
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   subformat    : STD
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   channels     : 2
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   rate         : 44100
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   msbits       : 16
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   buffer_size  : 16384
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_size  : 8192
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_time  : 185759
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_step  : 1
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   avail_min    : 15503
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_event : 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   start_threshold  : -1
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   silence_threshold: 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   silence_size : 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   boundary     : 4611686018427387904
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   appl_ptr     : 638181
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   hw_ptr       : 2007504
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: snd_pcm_delay() retornou um valor excepcionalmente elevado: -5527288 bytes (-31333 ms).
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Provavelmente isto é um erro no driver ALSA 'snd_hda_intel'. Por favor, reporte este problema aos programadores do ALSA.
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: snd_pcm_dump():
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Soft volume PCM
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Control: PCM Playback Volume
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: min_dB: -51
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: max_dB: 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: resolution: 256
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Its setup is:
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   stream       : PLAYBACK
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   format       : S16_LE
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   subformat    : STD
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   channels     : 2
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   rate         : 44100
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   msbits       : 16
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   buffer_size  : 16384
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_size  : 8192
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_time  : 185759
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_step  : 1
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   avail_min    : 15503
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_event : 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   start_threshold  : -1
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   silence_threshold: 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   silence_size : 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   boundary     : 4611686018427387904
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel PCH' device 0 subdevice 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c: Its setup is:
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   stream       : PLAYBACK
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   access       : MMAP_INTERLEAVED
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   format       : S16_LE
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   subformat    : STD
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   channels     : 2
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   rate         : 44100
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   exact rate   : 44100 (44100/1)
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   msbits       : 16
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   buffer_size  : 16384
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_size  : 8192
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_time  : 185759
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   tstamp_mode  : ENABLE
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_step  : 1
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   avail_min    : 15503
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   period_event : 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   start_threshold  : -1
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   stop_threshold   : 4611686018427387904
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   silence_threshold: 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   silence_size : 0
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   boundary     : 4611686018427387904
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   appl_ptr     : 658026
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-util.c:   hw_ptr       : 2039848
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-sink.c: ALSA acordou-nos para escrever novos dados para o dispositivo, mas não havia nada para escrever!
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-sink.c: Provavelmente isto é um erro no driver ALSA 'snd_hda_intel'. Por favor, reporte este problema aos programadores do ALSA.
Jul 25 00:41:31 andre-X550CC pulseaudio[2152]: [alsa-sink-ALC270 Analog] alsa-sink.c: Fomos acordados pelo conjunto POLLOUT -- contudo uma chamada a seguir de snd_pcm_avail() retornou 0 ou outro valor < min_avail.
Jul 25 00:52:13 andre-X550CC colord: Profile removed: icc-189936c762931c9fa9e3e29007110fd8
Jul 25 00:52:13 andre-X550CC colord: device removed: xrandr-LVDS1
Jul 25 00:52:14 andre-X550CC NetworkManager[1051]: <info> (wlan0): device state change: activated -> disconnected (reason 'connection-removed') [100 30 38]
Jul 25 00:52:14 andre-X550CC NetworkManager[1051]: <info> (wlan0): deactivating device (reason 'connection-removed') [38]
Jul 25 00:52:15 andre-X550CC NetworkManager[1051]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1874
Jul 25 00:52:15 andre-X550CC avahi-daemon[910]: Withdrawing address record for fe80::a6db:30ff:fe40:10a4 on wlan0.
Jul 25 00:52:15 andre-X550CC avahi-daemon[910]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::a6db:30ff:fe40:10a4.
Jul 25 00:52:15 andre-X550CC avahi-daemon[910]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jul 25 00:52:15 andre-X550CC kernel: [10481.678829] wlan0: deauthenticating from 00:22:b0:f0:05:d7 by local choice (reason=3)
Jul 25 00:52:15 andre-X550CC kernel: [10481.689733] cfg80211: Calling CRDA to update world regulatory domain
Jul 25 00:52:07 andre-X550CC wpa_supplicant[1182]: message repeated 7 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jul 25 00:52:15 andre-X550CC wpa_supplicant[1182]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:22:b0:f0:05:d7 reason=3 locally_generated=1
Jul 25 00:52:16 andre-X550CC avahi-daemon[910]: Withdrawing address record for 192.168.1.4 on wlan0.
Jul 25 00:52:16 andre-X550CC avahi-daemon[910]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.4.
Jul 25 00:52:16 andre-X550CC avahi-daemon[910]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jul 25 00:52:16 andre-X550CC NetworkManager[1051]: <warn> DNS: plugin dnsmasq update failed
Jul 25 00:52:16 andre-X550CC NetworkManager[1051]: <info> Removing DNS information from /sbin/resolvconf
Jul 25 00:52:16 andre-X550CC avahi-daemon[910]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::a6db:30ff:fe40:10a4.
Jul 25 00:52:16 andre-X550CC avahi-daemon[910]: New relevant interface wlan0.IPv6 for mDNS.
Jul 25 00:52:16 andre-X550CC avahi-daemon[910]: Registering new address record for fe80::a6db:30ff:fe40:10a4 on wlan0.*.
Jul 25 00:52:16 andre-X550CC dnsmasq[1889]: configurando servidores upstream do DBus
Jul 25 00:52:17 andre-X550CC kernel: [10483.062499] cfg80211: World regulatory domain updated:
Jul 25 00:52:17 andre-X550CC kernel: [10483.062502] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 25 00:52:17 andre-X550CC kernel: [10483.062504] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 25 00:52:17 andre-X550CC kernel: [10483.062505] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 25 00:52:17 andre-X550CC kernel: [10483.062506] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 25 00:52:17 andre-X550CC kernel: [10483.062507] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 25 00:52:17 andre-X550CC kernel: [10483.062508] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 25 00:52:17 andre-X550CC acpid: client 1119[0:0] has disconnected
Jul 25 00:52:17 andre-X550CC acpid: client connected from 4393[0:0]
Jul 25 00:52:17 andre-X550CC acpid: 1 client rule loaded
Jul 25 00:52:17 andre-X550CC NetworkManager[1051]: <info> NetworkManager state is now DISCONNECTED
Jul 25 00:52:17 andre-X550CC NetworkManager[1051]: <warn> Connection disconnected (reason -3)
Jul 25 00:52:17 andre-X550CC NetworkManager[1051]: <info> (wlan0): supplicant interface state: completed -> disconnected
Jul 25 00:52:17 andre-X550CC NetworkManager[1051]: <warn> Connection disconnected (reason -3)
Jul 25 00:52:17 andre-X550CC wpa_supplicant[1182]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 25 00:52:17 andre-X550CC dbus[766]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 25 00:52:18 andre-X550CC dbus[766]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'

```

Here is the results of wireless_script:


```
########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux andre-X550CC 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6627]
    Kernel driver in use: ath9k


04:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169


##### lsusb #####


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b40a Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211


##### iw reg get #####


country PT:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"INFORMATICA_TA"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:406   Missed beacon:0


##### route #####


Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 wlan0
192.168.100.0   0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [INFORMATICA_TA] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    LALMEIDAWL_AP:   Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 37 WEP
    *INFORMATICA_TA: Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 69 WEP


  IPv4 Settings:
    Address:         192.168.100.127
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.1


    DNS:             192.168.100.1


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"INFORMATICA_TA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ae7e6eff9
                    Extra: Last beacon: 136ms ago
                    IE: Unknown: 000E494E464F524D41544943415F5441
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706505400010D10
          Cell 02 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"LALMEIDAWL_AP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000064399b6aacf
                    Extra: Last beacon: 84ms ago
                    IE: Unknown: 000D4C414C4D45494441574C5F4150
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B0001031047001000000000000010000000B0487ABBB5221021000754502D4C494E4B10230009544C2D57413930314E10240003322E3010420003312E301054000800060050F204000110110017576972656C657373204E20415020544C2D57413930314E100800020086103C000101
                    IE: Unknown: DD050050F20500


##### iwlist channel #####


wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.472 GHz (Channel 13)


##### modinfo #####


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     7EAAD420ADF6B9354F0C8C1
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512


##### modules #####


lp
rtc


##### blacklist #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/bumblebee.conf]
blacklist nouveau
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
blacklist nvidia-304
blacklist nvidia-304-updates
blacklist nvidia-experimental-304
blacklist nvidia-310
blacklist nvidia-310-updates
blacklist nvidia-experimental-310
blacklist nvidia-313
blacklist nvidia-313-updates
blacklist nvidia-experimental-313
blacklist nvidia-319
blacklist nvidia-319-updates
blacklist nvidia-experimental-319
blacklist nvidia-325
blacklist nvidia-325-updates
blacklist nvidia-experimental-325
blacklist nvidia-331
blacklist nvidia-331-updates
blacklist nvidia-experimental-331


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    2.706333] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f03)
[   17.708511] ath: phy0: Disable PLL PowerSave
[   17.715498] ath: phy0: Enable LNA combining
[   17.717106] ath: EEPROM regdomain: 0x60
[   17.717109] ath: EEPROM indicates we should expect a direct regpair map
[   17.717111] ath: Country alpha2 being used: 00
[   17.717113] ath: Regpair used: 0x60
[   22.429760] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.432874] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.689802] wlan0: authenticate with <MAC address removed>
[   43.707512] wlan0: send auth to <MAC address removed> (try 1/3)
[   43.709410] wlan0: authenticated
[   43.709527] ath9k 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   43.712876] wlan0: associate with <MAC address removed> (try 1/3)
[   43.716165] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=6)
[   43.716317] wlan0: associated
[   43.716338] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   43.719041] ath: EEPROM regdomain: 0x826c
[   43.719044] ath: EEPROM indicates we should expect a country code
[   43.719046] ath: doing EEPROM country->regdmn map search
[   43.719047] ath: country maps to regdmn code: 0x37
[   43.719048] ath: Country alpha2 being used: PT
[   43.719049] ath: Regpair used: 0x37
[   43.719051] ath: regdomain 0x826c dynamically updated by country IE


########## wireless info END ############

```


is it a pulseaudio bug? a wireless bug? maybe both?
any insight on this would be greatly apreciated, if any more information needed please tell how to get it, as I said I'm kind of a begginer on Linux.
Ty for the answers in advance :)

---

### Post by jeremy31 on 2014-07-25
Start by changing your router to use WPA2-AES and see if it works
And run this newer wireless script
```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
```

---

### Post by varunendra on 2014-07-25
First off, Welcome to the forums medeirosat! :)

Secondly, please do what jeremy31 suggested above - It doesn't seem that changing the encryption setting is going to help in this case (but is recommended as he mentioned anyway), but post the wireless_script report (this is a different one, not the one you used in your first post) while Network Manager is running.

I don't usually suggest this anymore, but seeing some weird unexplainable problems with particularly 14.04 lately, and a hint from [here]("http://askubuntu.com/a/457687") that this may be some bug in Network Manager included in 14.04, may I suggest to try WICD instead of Network Manager for a test?

Remove Network Manager and install WICD as mentioned here : [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)
(it is important to download Network Manager packages first, in case we need to revert to it)

..and see if you can get rid of those wpa_supplicant error messages in syslog (reboot the system after changing to WICD). If not run the new wireless_script (that jeremy31 linked to) again while WICD is running, and post back its report too.

---

### Post by medeirosat on 2014-07-27
Hey all, thank you for your answers. I waited a couple of days to make some testing.
Did what varunendra suggested and installed Wicd, the messages stopped but the system kept crashing. Found out the problem was with pulse audio and those messages. A quick pulse audio unistall and a kmix reinstall did the trick. Ubuntu is sucessufly running for the last 2 days without crashing. Ty all for the tips :D

Here's what I found so far to install kubuntu on a Asus 550CC Laptop if anyone is reading this:

- Use nvidia 331.89 driver with bumblebee to get rid of horizontal lines on fullscreen video
- Unistall pulseaudio and reinstall kmix
- For your wireless card, remove Network Manager and install Wicd as suggested in the post above, and read this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173681](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1173681) to a workaround.
They are not bug fixes but will make your system more stable.

---

### Post by WinEunuchs2Unix on 2014-08-10
> **varunendra said:**
> First off, Welcome to the forums medeirosat! :)

I don't usually suggest this anymore, but seeing some weird unexplainable problems with particularly 14.04 lately, and a hint from [here]("http://askubuntu.com/a/457687") that this may be some bug in Network Manager included in 14.04, may I suggest to try WICD instead of Network Manager for a test?


I have those nasty syslog spam messages every minute as well after installing the new RT3072 chipset Premiertek "Speedy2" USB Wifi Adapter with two cool antenna's and 1000 mW amplifier... my fifth wifi adapter in 3 months :D

Anyway WiCD sounds like a great "network manager lite" for the mainstream however I'm concerned that it's not getting the community attention and volunteer development support it needs / deserves.

The first day I installed the new adapter after an hour it would disconnect and try to find the infamous regulator domain every few minutes.  It was attached to the USB2.0 non-powered hub.  The next day I attached it to the USB 3.0 ac-powered 2amp hub and the connection was FLAWLESS.  However I still have these nasty spam messages to deal with.

That world famous Varun is always one step ahead with the problems I research.... With so many following in his footsteps might have to change his last name to Ghandi :D

EDIT: This is the third day with the new "Speedy 2" adapter and inexplicably this afternoon the spam has disappeared from /var/log/syslog.  By accident (should I say foolish manoeuvre?) unity-desktop was reinstalled yesterday and subsequent broken libreoffice over apache openoffice dependencies were fixed this afternoon.  Could reinstalling unity-desktop have made the spam disappear?  Who knows...  But I must say this fifth adapter is the best so far :)

---

### Post by varunendra on 2014-08-11
> **WinEunuchs2Unix said:**
> ....
*[FALSE ALLEGATIONS BEGIN]*
That world famous Varun is always one step ahead with the problems I research.... With so many following in his footsteps might have to change his last name to Ghandi :D
*[/FALSE ALLEGATIONS END]*
....

Thank you so much for the kind comments WinEunuchs2Unix (again), but.... wait.... what? Whoa, "Gandhi"? Hmm.... smells like a conspiracy to drown me in the flood of expectations.... heh, not falling victim to it :p

Seriously though, I myself mostly follow the footsteps of chili555 (in wireless troubleshooting; many others in other things), whose every post is still backed up by lots of fresh research and experiments. Whereas my posts (at least when I'm short of time like nowadays) tend to be based on old, sometimes even outdated knowledge and assumptions and so can be very misleading sometimes.

The recipe to a good post, as taught by chili555, is - look for clues > use error-messages as keywords to 'search' for clues if required > follow the clues > do research and experiments as necessary > use your existing knowledge and make assumptions where necessary to derive a conclusion > try to post in an easy-to-follow way whatever you concluded, with explanations if required.... and,.... above all... be ALWAYS prepared to be proven wrong and learn something new ;)

I think the above formula is what is worth following, not any person in particular. [COLOR="#696969"](I always *<cough>*.... 'try' to follow it :p)[/COLOR]

**PS:**
I find it very unfortunate when threads I post in go unanswered (after replies of the OP) for days when I'm not around. It seems even my seniors/old-colleagues trust me more than I deserve. I believe a forum thread is supposed to be a sharing point of ideas, and everyone should feel free to post if they have any ideas that could be possibly helpful.

---

### Post by WinEunuchs2Unix on 2014-08-11
> **varunendra said:**
> Thank you so much for the kind comments WinEunuchs2Unix (again), but.... wait.... what? Whoa, "Gandhi"? Hmm.... smells like a conspiracy to drown me in the flood of expectations.... heh, not falling victim to it :p

Seriously though, I myself mostly follow the footsteps of chili555 (in wireless troubleshooting; many others in other things), whose every post is still backed up by lots of fresh research and experiments. Whereas my posts (at least when I'm short of time like nowadays) tend to be based on old, sometimes even outdated knowledge and assumptions and so can be very misleading sometimes.

The recipe to a good post, as taught by chili555, is - look for clues > use error-messages as keywords to 'search' for clues if required > follow the clues > do research and experiments as necessary > use your existing knowledge and make assumptions where necessary to derive a conclusion > try to post in an easy-to-follow way whatever you concluded, with explanations if required.... and,.... above all... be ALWAYS prepared to be proven wrong and learn something new ;)

I think the above formula is what is worth following, not any person in particular. [COLOR=#696969](I always *<cough>*.... 'try' to follow it :p)[/COLOR]

**PS:**
I find it very unfortunate when threads I post in go unanswered (after replies of the OP) for days when I'm not around. It seems even my seniors/old-colleagues trust me more than I deserve. I believe a forum thread is supposed to be a sharing point of ideas, and everyone should feel free to post if they have any ideas that could be possibly helpful.

Yes Chili555 is truly a trail blazer in wifiland.  As for being wrong; a lot of times we just go by past experience and the current problem has a new twist... more than one way to skin a cat as the old saying goes *ducks flying dishes thrown by cat lovers*.

Oh yeah another reason the 1 minute CONTROL-EVENT dmesg spam might have gone away is I installed kernel 3.15.9 in addition to unity-desktop on Sunday.  I guess I'll never know what fixed it exactly *shrugs*.

---

