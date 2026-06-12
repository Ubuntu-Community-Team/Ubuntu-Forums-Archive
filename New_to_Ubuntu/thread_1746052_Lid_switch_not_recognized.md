---
title: "Lid switch not recognized"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by DGINSD on 2011-05-01
****K I've been dealin' with this issue for a while and for the life of me I cant find an answer. I want my laptop to hibernate when I close the lid. I can Hibernate without a hitch by clicking Shut Down then Hibernate. But when I set the power manager settings to hibernate with the lid nothing happens I've tried changing all the settings, I've set it to shut down, and sleep with the lid with the same results; nothing happening. I know the lid switch is working fine because when I'm on my Windows XP partition it works perfectly. Which leads me to think that the lid switch is not being recognized by Ubuntu. So my question is how do I go about troubleshooting and fixing this?

As a side not I do have a few other issues with power management. The power indicator is very inaccurate for example I'm running on battery power but the indicator icon shows me as charging. 

To be complete, I should mention that I have tried changing the lid switch setting for both battery and AC power, same result.

---

### Post by matt_symes on 2011-05-01
Hi

When you close the lib what is the value of 

```
cat /proc/acpi/button/lid/*/state
```

You will have to do this from an external keyboard, via ssh or a script to write to a file. These are the ways to check this that comes to mind quickly.

This will show if Ubuntu recognises if the lid is closed.

Kind regards

---

### Post by DGINSD on 2011-05-01
I'm a super noob  so I need a bit more help. When I run, cat /proc/acpi/button/lid/*/state  the state is open but I dont have a usb keyboard to print the output with the lid closed. Any iedas on a script like a delayed enter or something?

Thanks for the help this is farther than I've gotten before.

---

### Post by matt_symes on 2011-05-02
Hi

Open a terminal (Applications->Accessories->Terminal) .

Type

```
cd
nano lid_button.sh
```and copy and paste this code into it

```

#!/bin/bash
sleep 60
cat /proc/acpi/button/lid/*/state > button_state
```Press ctrl + o to save and ctrl + x to exit.

Make script executable

```
chmod 755 lid_button.sh
```start the script by typing

```
./lid_button.sh
```The script will wait 60 second before dumping /proc/acpi/button/lid/*/state into the file button_state in the same directory.

This will give you enough time to close the lid and wait. It the timeout is not long enough adjust the value 60.

Wait for a couple of minutes, open the lid and look at the contents of the file button_state. 

```
cat button_state
```Post the results back here.

Kind regards

---

### Post by DGINSD on 2011-05-03
Your instructions worked out great and the result was closed so it is working. So where do I go from here? :confused:

This is just a though I had and it may be totally out of wack but with the other issue I'm having with the power indicator is it possable that the system isn't polling acpi often enough to check for new status on  stuff like lid open or closed, ac power plug or battery, or does it not work that way?

---

### Post by matt_symes on 2011-05-04
Hi

> **DGINSD said:**
> Your instructions worked out great and the result was closed so it is working. So where do I go from here? :confused: 

That's good. Ubuntu knows the lid is closed so we can eliminate that.

> 
This is just a though I had and it may be totally out of wack but with the other issue I'm having with the power indicator is it possable that the system isn't polling acpi often enough to check for new status on  stuff like lid open or closed, ac power plug or battery, or does it not work that way?

Don't know yet. It could very well be an ACPI issue. Lets work though the problem though. Please post the output of

```
cat /etc/acpi/events/lidbtn
```

```
ps aux | grep [g]nome-power-manager
```

Then lets try to hibernate your PC using pm-utils.

```
sudo pm-hibernate
```

Enter your password. It will not be echoed to the screen. This is normal. Then post the output of

```
cat /var/log/pm-suspend.log
```

Did the above command hibernate your machine ?

Kind regards

---

### Post by DGINSD on 2011-05-04
Heres the output of the first two 

```
david@DGINSD:~$ cat /etc/acpi/events/lidbtn
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
david@DGINSD:~$ ps aux | grep [g]nome-power-manager
david     1587  0.0  1.1 156648  8852 ?        Sl   May03   0:00 gnome-power-manager
david@DGINSD:~$ 

```

As far as 
```
sudo pm-hibernate 
```
the system hibernated just fine, and now the output of 
```
cat /var/log/pm-suspend.log
``` 
its a very long one, but you asked for it :mrgreen:
```
david@DGINSD:~$ cat /var/log/pm-suspend.log
Initial commandline parameters: 
Sun May  1 23:27:45 PDT 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux DGINSD 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
aes_i586                7280  120 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
xt_limit                1394  7 
xt_tcpudp               1927  7 
ipt_addrtype            1611  4 
xt_state                1014  7 
joydev                  8767  0 
ip6table_filter         1275  1 
ip6_tables             11764  1 ip6table_filter
snd_intel8x0           25664  2 
nf_nat_irc              1168  0 
nf_conntrack_irc        3348  1 nf_nat_irc
snd_ac97_codec         99227  1 snd_intel8x0
nf_nat_ftp              1398  0 
ac97_bus                1014  1 snd_ac97_codec
arc4                    1165  2 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
nf_conntrack_ftp        5361  1 nf_nat_ftp
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_midi            4588  0 
b43                   168681  0 
iptable_filter          1302  1 
snd_rawmidi            17783  1 snd_seq_midi
mac80211              231959  1 b43
pcmcia                 35973  0 
ip_tables              10460  1 iptable_filter
snd_seq_midi_event      6047  1 snd_seq_midi
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
cfg80211              144694  2 b43,mac80211
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           21518  0 
snd                    49038  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            10566  1 yenta_socket
psmouse                59033  0 
dcdbas                  5402  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw               4022  0 
led_class               2633  1 b43
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
i915                  295435  4 
drm_kms_helper         30200  1 i915
drm                   168060  4 i915,drm_kms_helper
b44                    26253  0 
ssb                    39320  2 b43,b44
intel_agp              26566  2 i915
i2c_algo_bit            5168  1 i915
mii                     4425  1 b44
video                  18712  1 i915
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
             total       used       free     shared    buffers     cached
Mem:        765712     731744      33968          0      59100     362452
-/+ buffers/cache:     310192     455520
Swap:      1598432       4688    1593744

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...method return sender=:1.2 -> dest=:1.81 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Sun May  1 23:27:50 PDT 2011: performing hibernate
Sun May  1 23:35:31 PDT 2011: Awake.
Sun May  1 23:35:32 PDT 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.2 -> dest=:1.83 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Sun May  1 23:35:51 PDT 2011: Finished.
Initial commandline parameters: 
Mon May  2 03:36:56 PDT 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux DGINSD 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
aes_i586                7280  100 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
xt_limit                1394  7 
xt_tcpudp               1927  7 
ipt_addrtype            1611  4 
xt_state                1014  7 
joydev                  8767  0 
ip6table_filter         1275  1 
ip6_tables             11764  1 ip6table_filter
snd_intel8x0           25664  2 
nf_nat_irc              1168  0 
nf_conntrack_irc        3348  1 nf_nat_irc
snd_ac97_codec         99227  1 snd_intel8x0
nf_nat_ftp              1398  0 
ac97_bus                1014  1 snd_ac97_codec
arc4                    1165  2 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
nf_conntrack_ftp        5361  1 nf_nat_ftp
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_midi            4588  0 
b43                   168681  0 
iptable_filter          1302  1 
snd_rawmidi            17783  1 snd_seq_midi
mac80211              231959  1 b43
pcmcia                 35973  0 
ip_tables              10460  1 iptable_filter
snd_seq_midi_event      6047  1 snd_seq_midi
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
cfg80211              144694  2 b43,mac80211
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           21518  0 
snd                    49038  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            10566  1 yenta_socket
psmouse                59033  0 
dcdbas                  5402  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw               4022  0 
led_class               2633  1 b43
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
i915                  295435  4 
drm_kms_helper         30200  1 i915
drm                   168060  4 i915,drm_kms_helper
b44                    26253  0 
ssb                    39320  2 b43,b44
intel_agp              26566  2 i915
i2c_algo_bit            5168  1 i915
mii                     4425  1 b44
video                  18712  1 i915
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
             total       used       free     shared    buffers     cached
Mem:        765712     601044     164668          0      22684     295440
-/+ buffers/cache:     282920     482792
Swap:      1598432      85904    1512528

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...method return sender=:1.2 -> dest=:1.106 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Mon May  2 03:36:59 PDT 2011: performing hibernate
Mon May  2 05:17:51 PDT 2011: Awake.
Mon May  2 05:17:51 PDT 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.2 -> dest=:1.108 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Mon May  2 05:18:01 PDT 2011: Finished.
Initial commandline parameters: 
Mon May  2 07:38:12 PDT 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux DGINSD 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
nls_utf8                1069  1 
udf                    79366  1 
crc_itu_t               1383  1 udf
aes_i586                7280  171 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
xt_limit                1394  7 
xt_tcpudp               1927  7 
ipt_addrtype            1611  4 
xt_state                1014  7 
ip6table_filter         1275  1 
snd_intel8x0           25664  3 
ip6_tables             11764  1 ip6table_filter
joydev                  8767  0 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
nf_nat_irc              1168  0 
snd_pcm                71475  3 snd_intel8x0,snd_ac97_codec
nf_conntrack_irc        3348  1 nf_nat_irc
nf_nat_ftp              1398  0 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
snd_seq_midi            4588  0 
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
snd_rawmidi            17783  1 snd_seq_midi
arc4                    1165  2 
nf_conntrack_ftp        5361  1 nf_nat_ftp
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_midi_event      6047  1 snd_seq_midi
pcmcia                 35973  0 
iptable_filter          1302  1 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ip_tables              10460  1 iptable_filter
b43                   168681  0 
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_timer              19067  2 snd_pcm,snd_seq
mac80211              231959  1 b43
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144694  2 b43,mac80211
yenta_socket           21518  0 
snd                    49038  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5402  0 
pcmcia_rsrc            10566  1 yenta_socket
psmouse                59033  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore                880  1 snd
led_class               2633  1 b43
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
i915                  295435  4 
drm_kms_helper         30200  1 i915
drm                   168060  4 i915,drm_kms_helper
b44                    26253  0 
intel_agp              26566  2 i915
ssb                    39320  2 b43,b44
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
mii                     4425  1 b44
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
             total       used       free     shared    buffers     cached
Mem:        765712     535728     229984          0      53744     333708
-/+ buffers/cache:     148276     617436
Swap:      1598432      43704    1554728

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...method return sender=:1.2 -> dest=:1.57 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Mon May  2 07:38:20 PDT 2011: performing hibernate
Mon May  2 19:07:32 PDT 2011: Awake.
Mon May  2 19:07:32 PDT 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.2 -> dest=:1.59 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Mon May  2 19:07:38 PDT 2011: Finished.
Initial commandline parameters: 
Tue May  3 07:42:03 PDT 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux DGINSD 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
nls_utf8                1069  1 
udf                    79366  1 
crc_itu_t               1383  1 udf
aes_i586                7280  88 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
xt_limit                1394  7 
xt_tcpudp               1927  7 
ipt_addrtype            1611  4 
xt_state                1014  7 
ip6table_filter         1275  1 
snd_intel8x0           25664  3 
ip6_tables             11764  1 ip6table_filter
joydev                  8767  0 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
nf_nat_irc              1168  0 
snd_pcm                71475  3 snd_intel8x0,snd_ac97_codec
nf_conntrack_irc        3348  1 nf_nat_irc
nf_nat_ftp              1398  0 
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10783  9 nf_nat
snd_seq_midi            4588  0 
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
snd_rawmidi            17783  1 snd_seq_midi
arc4                    1165  2 
nf_conntrack_ftp        5361  1 nf_nat_ftp
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_midi_event      6047  1 snd_seq_midi
pcmcia                 35973  0 
iptable_filter          1302  1 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ip_tables              10460  1 iptable_filter
b43                   168681  0 
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_timer              19067  2 snd_pcm,snd_seq
mac80211              231959  1 b43
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144694  2 b43,mac80211
yenta_socket           21518  0 
snd                    49038  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5402  0 
pcmcia_rsrc            10566  1 yenta_socket
psmouse                59033  0 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore                880  1 snd
led_class               2633  1 b43
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
i915                  295435  5 
drm_kms_helper         30200  1 i915
drm                   168060  5 i915,drm_kms_helper
b44                    26253  0 
intel_agp              26566  2 i915
ssb                    39320  2 b43,b44
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
mii                     4425  1 b44
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
             total       used       free     shared    buffers     cached
Mem:        765712     706544      59168          0     103056     268432
-/+ buffers/cache:     335056     430656
Swap:      1598432     104792    1493640

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...method return sender=:1.2 -> dest=:1.87 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Tue May  3 07:42:12 PDT 2011: performing hibernate
Tue May  3 17:06:17 PDT 2011: Awake.
Tue May  3 17:06:18 PDT 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.2 -> dest=:1.89 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Tue May  3 17:06:51 PDT 2011: Finished.
Initial commandline parameters: 
Tue May  3 21:14:45 PDT 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux DGINSD 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
nls_utf8                1069  1 
udf                    79366  1 
crc_itu_t               1383  1 udf
aes_i586                7280  173 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
dm_crypt               11385  0 
xt_limit                1394  7 
xt_tcpudp               1927  7 
ipt_addrtype            1611  4 
xt_state                1014  7 
joydev                  8767  0 
ip6table_filter         1275  1 
ip6_tables             11764  1 ip6table_filter
nf_nat_irc              1168  0 
snd_intel8x0           25664  3 
nf_conntrack_irc        3348  1 nf_nat_irc
nf_nat_ftp              1398  0 
snd_ac97_codec         99227  1 snd_intel8x0
arc4                    1165  2 
ac97_bus                1014  1 snd_ac97_codec
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
snd_pcm                71475  3 snd_intel8x0,snd_ac97_codec
nf_conntrack_ipv4      10783  9 nf_nat
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
nf_conntrack_ftp        5361  1 nf_nat_ftp
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_midi            4588  0 
b43                   168681  0 
snd_rawmidi            17783  1 snd_seq_midi
iptable_filter          1302  1 
pcmcia                 35973  0 
ip_tables              10460  1 iptable_filter
snd_seq_midi_event      6047  1 snd_seq_midi
mac80211              231959  1 b43
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144694  2 b43,mac80211
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
snd                    49038  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5402  0 
psmouse                59033  0 
led_class               2633  1 b43
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore                880  1 snd
shpchp                 29886  0 
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
i915                  295435  5 
drm_kms_helper         30200  1 i915
drm                   168060  5 i915,drm_kms_helper
b44                    26253  0 
ssb                    39320  2 b43,b44
intel_agp              26566  2 i915
mii                     4425  1 b44
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
             total       used       free     shared    buffers     cached
Mem:        765712     751656      14056          0      30552     455768
-/+ buffers/cache:     265336     500376
Swap:      1598432          0    1598432

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...method return sender=:1.2 -> dest=:1.57 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Tue May  3 21:14:50 PDT 2011: performing hibernate
Wed May  4 06:00:59 PDT 2011: Awake.
Wed May  4 06:00:59 PDT 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.2 -> dest=:1.59 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Wed May  4 06:01:13 PDT 2011: Finished.
Initial commandline parameters: 
Wed May  4 06:17:21 PDT 2011: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux DGINSD 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux
Module                  Size  Used by
nls_utf8                1069  1 
udf                    79366  1 
crc_itu_t               1383  1 udf
aes_i586                7280  101 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
ipt_REJECT              2004  1 
ipt_LOG                 4490  5 
dm_crypt               11385  0 
xt_limit                1394  7 
xt_tcpudp               1927  7 
ipt_addrtype            1611  4 
xt_state                1014  7 
joydev                  8767  0 
ip6table_filter         1275  1 
ip6_tables             11764  1 ip6table_filter
nf_nat_irc              1168  0 
snd_intel8x0           25664  2 
nf_conntrack_irc        3348  1 nf_nat_irc
nf_nat_ftp              1398  0 
snd_ac97_codec         99227  1 snd_intel8x0
arc4                    1165  2 
ac97_bus                1014  1 snd_ac97_codec
nf_nat                 16289  2 nf_nat_irc,nf_nat_ftp
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
nf_conntrack_ipv4      10783  9 nf_nat
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
nf_conntrack_ftp        5361  1 nf_nat_ftp
nf_conntrack           63258  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_midi            4588  0 
b43                   168681  0 
snd_rawmidi            17783  1 snd_seq_midi
iptable_filter          1302  1 
pcmcia                 35973  0 
ip_tables              10460  1 iptable_filter
snd_seq_midi_event      6047  1 snd_seq_midi
mac80211              231959  1 b43
x_tables               15921  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144694  2 b43,mac80211
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
snd                    49038  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5402  0 
psmouse                59033  0 
led_class               2633  1 b43
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore                880  1 snd
shpchp                 29886  0 
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
i915                  295435  4 
drm_kms_helper         30200  1 i915
drm                   168060  4 i915,drm_kms_helper
b44                    26253  0 
ssb                    39320  2 b43,b44
intel_agp              26566  2 i915
mii                     4425  1 b44
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
             total       used       free     shared    buffers     cached
Mem:        765712     709436      56276          0      23840     349824
-/+ buffers/cache:     335772     429940
Swap:      1598432      49540    1548892

/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:

/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Sessions still open, not unmounting
Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:

/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...method return sender=:1.2 -> dest=:1.81 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:

/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:

/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:

/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:

/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Wed May  4 06:17:25 PDT 2011: performing hibernate
Wed May  4 06:20:46 PDT 2011: Awake.
Wed May  4 06:20:46 PDT 2011: Running hooks for thaw
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:

/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:

/usr/lib/pm-utils/sleep.d/95led thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:

/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:

/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:

/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate:

/usr/lib/pm-utils/sleep.d/70action_wpa thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...method return sender=:1.2 -> dest=:1.83 reply_serial=2
Done.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:

/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate:

/usr/lib/pm-utils/sleep.d/45bluetooth-service thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate:

/usr/lib/pm-utils/sleep.d/44bluetooth-known-quirk thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:

/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Sessions still open, not unmounting

/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:

/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:

/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:

/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Wed May  4 06:20:58 PDT 2011: Finished.
david@DGINSD:~$ 

```

---

### Post by matt_symes on 2011-05-04
Hi

That's all looking good so far. Lets make sure the kernel is emitting events.

Open a terminal and type

```
acpi_listen
```

Close the laptop and reopen. Press ctrl + c to exit acpi_listen. Copy and paste the results back here.

If that does not work, reboot your PC and select recovery menu from grub. When you get the menu hit the down arrow until you get to root console option. Boot into the root console and then type

```
cat /proc/acpi/event
```

Open and close the lid as before. Is anything displayed on the screen and if so what ? Press ctrl + c as to exit this.

Type ```
exit
``` to restart. It will boot to the command line if you choose resume from the menu. Enter your user name and password.

Type

```
sudo service gdm start
```

to start and X session via gdm. You can then start your browser and reply :)

Kind regards

---

### Post by DGINSD on 2011-05-05
This one didn't work out so well, I entered <acpi_listen> and hit enter, but nothing happened, no prompt or anything. So I continued on with your instructions; closed the lid waited about 10 seconds or so and re-opened it, but still nothing, So I hit <control x> but all I got was this 
```
david@DGINSD:~$ acpi_listen
^X

```
it seems the <control x> isn't exiting and the <acpi_listen> isn't seeming to do anything either.

So I moved on to the recovery mode, booting into the root console and followed your instructions, which had much the same results. Typing in 
```
cat /proc/acpi/event
```
 output nothing, not even a prompt, and after cycling the lid, same thing.  So I went to exit  with <control x> but just got the same ```
^X 
``` but nothing else. So with no prompt I couldn't "exit" so I had to <control alt delete> to restart.

Just for good measure, I tried both operations twice with the exact same results.  Both times when I was done and closed my terminal window a prompt came up asking if I wanted to close the terminal and that doing so would also kill the process currently  running
 ```
There is still a process running in this terminal. Closing the terminal will kill it.
```

So I seem to of hit a snag, is this possibly the issue thats causing my system  to not respond?

---

### Post by matt_symes on 2011-05-05
Hi

> **DGINSD said:**
> This one didn't work out so well, I entered <acpi_listen> and hit enter, but nothing happened, no prompt or anything. So I continued on with your instructions; closed the lid waited about 10 seconds or so and re-opened it, but still nothing, So I hit <control x> but all I got was this 
```
david@DGINSD:~$ acpi_listen
^X

```
it seems the <control x> isn't exiting and the <acpi_listen> isn't seeming to do anything either.

So I moved on to the recovery mode, booting into the root console and followed your instructions, which had much the same results. Typing in 
```
cat /proc/acpi/event
```
 output nothing, not even a prompt, and after cycling the lid, same thing.  So I went to exit  with <control x> but just got the same ```
^X 
``` but nothing else. So with no prompt I couldn't "exit" so I had to <control alt delete> to restart.

Just for good measure, I tried both operations twice with the exact same results.  Both times when I was done and closed my terminal window a prompt came up asking if I wanted to close the terminal and that doing so would also kill the process currently  running
 ```
There is still a process running in this terminal. Closing the terminal will kill it.
```

So I seem to of hit a snag, is this possibly the issue thats causing my system  to not respond?

First things first. 

It should have been ctrl + c to exit and not ctrl + x. They are next to each other on my keyboard, so a typo :( . You have my apologies. I have amended by post above.

Second. That looks like what may be your problem as when you closed the laptop case you should have had a message about a lid event. 

Both commands will not give any feedback, not even a flashing cursor. What will happen though is any acpi event received will be logged to the terminal or console. That is why you have to press ctrl + c to exit.

I will have to look into this tomorrow though.

Bump this thread when you read this so i will see it in my subscriptions area.

Kind regards

---

### Post by DGINSD on 2011-05-06
Just out of curiosity a power cord being plugged in or pulled out would be an acpi event as well so I could give it another test?

 I just re-read your post where you say
> Both commands will not give any feedback[COLOR="Red"], not even a flashing cursor.[/COLOR] What will happen though is any acpi event received will be logged to the terminal or console. That is why you have to press ctrl + c to exit.

well I do have a flashing cursor, and for what it's worth neither unplugging or plugging back in were listed.

---

### Post by matt_symes on 2011-05-06
Hi

> **DGINSD said:**
> Just out of curiosity a power cord being plugged in or pulled out would be an acpi event as well so I could give it another test?

 I just re-read your post where you say


well I do have a flashing cursor, and for what it's worth neither unplugging or plugging back in were listed.

Actually i do get a flashing cursor from the terminal (just tried it).
 I think it may have been from the console i got no output but i will have to double check.

This is what is get on my laptop when i run acpi_listen with the screen set to blank in power management when the lid is closed  and the lid is closed then opened again and also when i remove and reinsert the power cord. <poorly worded sentence>  

```
matthew@matthew-laptop:~/my_documents/collaborative_scripts$ acpi_listen
button/lid LID0 00000080 00000001
button/lid LID0 00000080 00000002
ac_adapter ADP1 00000080 00000000
battery BAT0 00000080 00000001
ac_adapter ADP1 00000080 00000001
battery BAT0 00000080 00000001
```

You get no output like this at all ?

Kind regards

---

### Post by DGINSD on 2011-05-06
Nothing of the kind, only a flashing cursor.

Do I need to move to a differant directory to run acpi_listen?

---

### Post by matt_symes on 2011-05-06
Hi

> **DGINSD said:**
> Nothing of the kind, only a flashing cursor.

Do I need to move to a differant directory to run acpi_listen?

No. Any directory will do.

When you remove the power supply does Ubuntu recognise that it has been removed ?

I.e. on the desktop ?

Kind regards

---

### Post by DGINSD on 2011-05-06
It will recognize it but it seems to take quite a while sometimes. For example if I unplug the cord the charging icon will remain for 3 or 4 minutes before it changes to just the battery indicator but it's rather irregular.  Sometimes I will get a "battery is discharging" notification but that is also very hit or miss.

---

### Post by matt_symes on 2011-05-07
Hi

Well i think that is the problem. I am no expert in this, however it seems the acpi daemon (acpid) is not emitting events correctly for some reason.

This will require some research to find out what the problem could be. I will get back to you if i make progress.

Kind regards

---

### Post by DGINSD on 2011-05-07
Thank you much I appreciate your time, and I will be doing my own searching as well (though it seems much over my head)

---

### Post by DGINSD on 2011-05-07
Just some things I've tried and things I've noticed. I've booted using the other two kernels loaded in grub and ran acpi_listen, both had the same results; no events logging. I also tried with a Maverick 10.10 live CD and  Natty 11.04 live CD same result; no events logging. 

Something I've noticed with the live CD's when using the Maverick 10.10 I get an error message I'll post back with it later when I have more time. With the Natty 11.04 I don't get the error, I don't know if this has anything to do with this issue just thought I'd bring it up. Primarily because my system was installed using the Maverick 10.10 CD and was concerned that any such errors could of screwed up the install perhaps causing such issues.

Here is the error : (process: 280) Glib Warning ** : getpwuid_r( ): failed due to unknown user id (0)

I always get one of these using the Maverick 10.10 live CD thought the (process 280) part will often contain a different number. As i sait this may be totally unrelated but just thought I'd bring it up. The 10.10 disc was  downloaded using my browser and the Natty 11.04 (that produces no errors) was  downloaded using Transmission Bit Torrent  Client, I also had to burn the 10.10 twice as the first one wouldn't install.

---

### Post by matt_symes on 2011-05-07
Hi

Your not booting with any special acpi kernel options are you ? Just to make sure, please post the output of 

```
cat /proc/cmdline
```

Kind regards

---

### Post by DGINSD on 2011-05-07
Not as far as I know, and if I am it's completely by accident (I'm no where near advanced enough to mess with the kernel)

Here"s the output:


david@DGINSD:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=25952c4e-39d7-4aea-8dfe-77de8596ce76 ro vga=792 splash quiet splash
david@DGINSD:~$

---

