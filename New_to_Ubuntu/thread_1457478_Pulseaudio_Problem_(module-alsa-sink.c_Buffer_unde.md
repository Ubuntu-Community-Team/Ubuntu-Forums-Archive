---
title: "Pulseaudio Problem (module-alsa-sink.c: Buffer underrun)"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2010-04-18
Hi All,

Please anyone help me on this issue. I'm using Ubuntu 8.04 LTS , Pulseaudio 0.9.10 and kernel 2.6.24-27-generic. When I try to run any movies in my system, after sometime it will give me an error 

pulseaudio[6665]: module-alsa-sink.c: Buffer underrun!. 

After this error pulseaudio throw below error.

[HTML]
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: main.c: Daemon shutdown initiated.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-alsa-sink" (index: #0).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-rescue-streams.c: No evacuation sink found.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: Buffer underrun!
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: EAGAIN
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: Buffer underrun!
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: EAGAIN
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: Buffer underrun!
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: EAGAIN
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-suspend-on-idle.c: Sink alsa_output.surround40_0 becomes idle.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-suspend-on-idle.c: Sink alsa_output.surround40_0 becomes idle.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: sink-input.c: Freeing output 0 "audio stream"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: Buffer underrun!
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: EAGAIN
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-rescue-streams.c: No source outputs to move away.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-sink.c: Thread shutting down
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: sink.c: Freeing sink 0 "alsa_output.surround40_0"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: source.c: Freeing source 0 "alsa_output.surround40_0.monitor"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-alsa-sink" (index: #0).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-alsa-source" (index: #1).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-rescue-streams.c: No source outputs to move away.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-source.c: Thread shutting down
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: source.c: Freeing source 1 "alsa_input.pci_1102_7_sound_card_0_alsa_capture_0"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-alsa-source" (index: #1).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-alsa-source" (index: #2).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-rescue-streams.c: No source outputs to move away.
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-alsa-source.c: Thread shutting down
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: source.c: Freeing source 2 "alsa_input.pci_1131_7134_sound_card_0_alsa_capture_0"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-alsa-source" (index: #2).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-hal-detect" (index: #3).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module-hal-detect.c: dbus: interface=org.freedesktop.DBus.Local, path=/org/freedesktop/DBus/Local, member=Disconnected
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-hal-detect" (index: #3).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-esound-protocol-unix" (index: #4).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: client.c: Freed 0 "EsounD client (UNIX socket client)"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: client.c: Freed 1 "EsounD client (UNIX socket client)"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: client.c: Freed 4 "EsounD client (UNIX socket client)"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: client.c: Freed 7 "EsounD client (UNIX socket client)"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-esound-protocol-unix" (index: #4).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-native-protocol-unix" (index: #5).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: client.c: Freed 2 "VLC media player"
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-native-protocol-unix" (index: #5).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-volume-restore" (index: #6).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-volume-restore" (index: #6).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-default-device-restore" (index: #7).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-default-device-restore" (index: #7).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-rescue-streams" (index: #8).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-rescue-streams" (index: #8).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-suspend-on-idle" (index: #9).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-suspend-on-idle" (index: #9).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-gconf" (index: #10).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-gconf" (index: #10).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloading "module-x11-publish" (index: #11).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: module.c: Unloaded "module-x11-publish" (index: #11).
Apr 19 01:42:32 vipinb-desktop pulseaudio[6665]: main.c: Daemon terminated.

[/HTML]There will not be any sound after this. As soon as when I check in my system monitor pulseaudio service will not be running. Please help me.

---

### Post by lidex on 2010-04-18
So this is with VLC then? Have you tried MPlayer to see if anything else causes the same behavior? What are your audio settings in VLC preferences?

---

### Post by vipin.balakrishnan on 2010-04-18
Hi lidex,

 It is happening with all players not only VLC. Can you please help me on this problem..

---

### Post by vipin.balakrishnan on 2010-04-24
Hi All,

 Can anyone reply to my question. Here I'm only replying answering .

---

