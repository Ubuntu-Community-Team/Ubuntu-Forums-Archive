---
title: "syslog - hibernation issue"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by tomster2300 on 2011-08-13
Hey guys, 

I've always had issues with resuming my computer from suspend / hibernation.  I have the syslog contents from putting my computer into hibernation, hard rebooting it (power button) and then logging back in.  Could someone decipher this for me and maybe point me in the right direction for what I should troubleshoot? 

Here is the log:  


Aug 13 12:47:16 user-EX58-UD3R NetworkManager[951]: <info> sleep requested (sleeping: no  enabled: yes)
Aug 13 12:47:16 user-EX58-UD3R NetworkManager[951]: <info> sleeping or disabling...
Aug 13 12:47:16 user-EX58-UD3R NetworkManager[951]: <info> (eth0): now unmanaged
Aug 13 12:47:16 user-EX58-UD3R NetworkManager[951]: <info> (eth0): device state change: 8 -> 1 (reason 37)
Aug 13 12:47:16 user-EX58-UD3R NetworkManager[951]: <info> (eth0): deactivating device (reason: 37).
Aug 13 12:47:16 user-EX58-UD3R NetworkManager[951]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1483
Aug 13 12:47:16 user-EX58-UD3R NetworkManager[951]: <info> (eth0): cleaning up...
Aug 13 12:47:16 user-EX58-UD3R NetworkManager[951]: <info> (eth0): taking down device.
Aug 13 12:47:16 user-EX58-UD3R NetworkManager[951]: <info> (eth0): carrier now OFF (device state 1)
Aug 13 12:47:17 user-EX58-UD3R anacron[2933]: Anacron 2.3 started on 2011-08-13
Aug 13 12:47:17 user-EX58-UD3R anacron[2933]: Normal exit (0 jobs run)
Aug 13 12:47:17 user-EX58-UD3R kernel: [ 1635.741802] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Aug 13 12:47:19 user-EX58-UD3R kernel: [ 1637.339925] PM: Marking nosave pages: 000000000009e000 - 0000000000100000
Aug 13 12:47:19 user-EX58-UD3R kernel: [ 1637.339928] PM: Basic memory bitmaps created
Aug 13 12:59:07 user-EX58-UD3R kernel: imklog 4.6.4, log source = /proc/kmsg started.
Aug 13 12:59:07 user-EX58-UD3R rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="913" x-info="http://www.rsyslog.com"] (re)start
Aug 13 12:59:07 user-EX58-UD3R rsyslogd: rsyslogd's groupid changed to 103
Aug 13 12:59:07 user-EX58-UD3R rsyslogd: rsyslogd's userid changed to 101
Aug 13 12:59:07 user-EX58-UD3R rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Aug 13 12:59:07 user-EX58-UD3R avahi-daemon[933]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Aug 13 12:59:07 user-EX58-UD3R avahi-daemon[933]: Successfully dropped root privileges.
Aug 13 12:59:07 user-EX58-UD3R avahi-daemon[933]: avahi-daemon 0.6.30 starting up.
Aug 13 12:59:07 user-EX58-UD3R avahi-daemon[933]: Successfully called chroot().
Aug 13 12:59:07 user-EX58-UD3R avahi-daemon[933]: Successfully dropped remaining capabilities.
Aug 13 12:59:07 user-EX58-UD3R gdm-binary[929]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 13 12:59:07 user-EX58-UD3R NetworkManager[936]: <info> NetworkManager (version 0.8.3.998) is starting...
Aug 13 12:59:07 user-EX58-UD3R NetworkManager[936]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 13 12:59:07 user-EX58-UD3R NetworkManager[936]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 13 12:59:07 user-EX58-UD3R NetworkManager[936]: <info> trying to start the modem manager...
Aug 13 12:59:07 user-EX58-UD3R modem-manager[940]: <info>  ModemManager (version 0.4) starting...
Aug 13 12:59:07 user-EX58-UD3R modem-manager[940]: <info>  Loaded plugin Linktop
Aug 13 12:59:07 user-EX58-UD3R avahi-daemon[933]: Loading service file /services/udisks.service.
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000] Linux version 2.6.38-10-generic-pae (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #46-Ubuntu SMP Tue Jun 28 16:54:49 UTC 2011 (Ubuntu 2.6.38-10.46-generic-pae 2.6.38.7)
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee2000 (ACPI NVS)
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000]  BIOS-e820: 00000000cfee2000 - 00000000cfef0000 (ACPI data)
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 00000001b0000000 (usable)
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000] NX (Execute Disable) protection: active
Aug 13 12:59:07 user-EX58-UD3R kernel: [    0.000000] DMI 2.4 present.

---

### Post by Uzi304 on 2011-08-13
I don't think I see anything jumping out on the logs but could you post the Hooks you're using from your /etc/mkinitcpio.conf? Also I'm assuming you're using pm-utils to suspend?

---

### Post by tomster2300 on 2011-08-13
I don't seem to have a mkiknitcpio.conf file in /etc/.  I'm not sure about pm-utils for suspending. I've been suspending through the options menu in the top right corner. Is there a way that I could check?

Update: I tried installing pm-utils, but it said that I was already running the most recent version.  How do I test that I'm using it to suspend?

---

### Post by tomster2300 on 2011-08-13
This is what pm-suspend.log says:

Initial commandline parameters: 
Sat Aug 13 23:34:58 EDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux tmcgahee-EX58-UD3R 2.6.38-10-generic-pae #46-Ubuntu SMP Tue Jun 28 16:54:49 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
binfmt_misc            13213  1 
pci_stub               12550  1 
vboxpci                22892  0 
vboxnetadp             13348  0 
vboxnetflt             27225  0 
vboxdrv               251892  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
radeon                925094  3 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
lp                     13349  0 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_timer              28659  2 snd_seq,snd_pcm
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184133  5 radeon,ttm,drm_kms_helper
i7core_edac            23249  0 
edac_core              42881  1 i7core_edac
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_rawmidi,snd_seq,snd_hwdep,snd_pcm,snd_timer,snd_seq_device
soundcore              12600  1 snd
parport                36746  3 parport_pc,ppdev,lp
psmouse                59039  0 
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
firewire_ohci          31504  0 
hid_apple              13124  0 
usbhid                 41704  0 
hid                    77084  2 hid_apple,usbhid
ahci                   21591  3 
firewire_core          56138  1 firewire_ohci
r8169                  46630  0 
libahci                25548  1 ahci
crc_itu_t              12627  1 firewire_core
pata_jmicron           12651  0 
floppy                 60032  0 
             total       used       free     shared    buffers     cached
Mem:       6189784    1007924    5181860          0      63404     408432
-/+ buffers/cache:     536088    5653696
Swap:     17940476          0   17940476

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Sat Aug 13 23:34:59 EDT 2011: performing suspend




It looks like it's failing here:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

---

### Post by tomster2300 on 2011-08-14
Update: It looks like virtualbox was the culprit, as I found out in this thread: [http://ubuntuforums.org/showthread.php?p=11138759](http://ubuntuforums.org/showthread.php?p=11138759)

The terminal commands in that thread's final post didn't work for me, but completely uninstalling virtualbox did.  

Suspend now works for me (although I have to push the power button to bring the computer back as opposed to a keyboard / mouse button).  Trying out hibernate now...

---

### Post by tomster2300 on 2011-08-14
Tested hibernation: one of my hard drives threw a temporary error, but the computer successfully hibernated and came back to life after pushing the power button.  I'm going to mark this thread as solved.

---

