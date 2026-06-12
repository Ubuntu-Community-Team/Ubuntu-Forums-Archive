---
title: "No internet while playing a song!!"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by vagrant87 on 2008-12-04
Hello everyone, I'm running Ubuntu 8.04 - Hardy Heron
and I have a very unusual problem:
If a listen to music (mp3 in any player, amarok, rhythmbox) my internet connections fails and I don't have internet at all, but when I stop listening to music (press stop) It works again...
It's like that: 
play music, no internet at all
Stop playing, internet again
I just can't figure out what the problem is :S
Can anyone help me?
Or at least is there a way to know what is going on?
thank you

Hola gente, tengo Ubuntu 8.04 - Hardy Heron
y me pasa una cosa muy rara: 
cuando escucho musica (mp3) en cualquier reproductor (he probado amarok, rhythmbox, totem) mi conexion a internet deja de funcionar, se cae siempre que una cancion este sonando. cuando pulso stop en el reproductor vuelvo a tener internet. O sea, le doy Play y se me cae internet, le doy stop y vuelve a andar.
realmente no se como encarar la situacion y me esta volviendo loco.. si alguien me puede ayudar a saber que es lo que podria llegar a pasar le agradeceria un monton. Desde ya muchas gracias

---

### Post by Michael.Godawski on 2008-12-05
Interesting...
Try to open one of the music applications via terminal
just type in the name, for instance
```
rhythmbox
```

open a new terminal tab and run firefox
```
firefox
```

Launch some music... do you see any messages in the terminal which might be helpful?

While you are doing this open a third terminal tab and run
```
top
```
and post the output here.

---

### Post by billgoldberg on 2008-12-05
Never heard that problem.

Do as the poster suggests above me.

--

It might be a long shot (could this be pulseaudio related?) but try switching to Alsa or OSS in "system -> preferences -> sound" and see if that helps.

--

Be sure to post the outcome of those commands.

*(the terminal is located in "applications -> accessories -> terminal".)*

---

### Post by 3rdalbum on 2008-12-05
Are you using wireless? If so, try moving your wireless aerial away from your computer. Your sound card might be generating some electrical noise that is causing the wireless to drop the connection.

---

### Post by vagrant87 on 2008-12-05
Hi, thanks for the answers..

-I'm not using wireless
-Switching Alsa or OSS didn't work :(

rhythmbox showed this messages in the terminal when I closed it:

(rhythmbox:6402): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(rhythmbox:6402): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(rhythmbox:6402): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(rhythmbox:6402): Gtk-WARNING **: ShowWindowTray: missing action TrayShowWindow

(rhythmbox:6402): Gtk-WARNING **: ShowNotifications: missing action TrayShowNotifications


And here is the top info (when listening to music):

top - 17:02:33 up 13 min,  1 user,  load average: 0.73, 0.95, 0.69
Tasks: 128 total,   2 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.9%us,  2.0%sy,  0.0%ni, 78.8%id,  0.0%wa,  0.0%hi,  3.3%si,  0.0%st
Mem:    515572k total,   481336k used,    34236k free,    10172k buffers
Swap:        0k total,        0k used,        0k free,   196360k cached

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6118 pc        20   0  196m  74m  24m S  6.0 14.8   1:07.07 firefox
 6014 pc        20   0 80172  27m 7180 S  5.3  5.4   0:57.82 compiz.real
 5550 root      20   0 79316  33m 8220 S  3.0  6.6   1:04.98 Xorg
 6163 pc        20   0 33340  17m  14m R  1.3  3.5   0:05.24 konsole
 5946 pc        20   0 56236  27m  15m S  0.7  5.4   0:09.76 gnome-panel
 5948 pc        20   0 15532 2672 1780 S  0.7  0.5   0:02.42 gnome-screensav
 6178 pc        20   0 26688 8328 6600 S  0.7  1.6   0:00.24 kded
 6121 pc        20   0 67448  30m 7116 S  0.3  6.0   0:24.64 wish
    1 root      20   0  2844 1688  544 S  0.0  0.3   0:02.26 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.12 kblockd/0
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
  120 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
  158 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  159 root      20   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
  160 root      15  -5     0    0    0 S  0.0  0.0   0:00.14 kswapd0
  203 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1418 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 ata/0
 1421 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux
 1435 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd
 1443 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1446 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 1455 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 scsi_eh_1

---

### Post by philinux on 2008-12-05
Open a terminal.

Make sure internet is working play a song then issue this command. Use copy and paste it into the terminal.

```
cat /var/log/messages | tail -30
```

---

### Post by vagrant87 on 2008-12-05
Ok, it shows this:

Dec  5 16:50:10 LeaMonde kernel: [   61.562676] powernow: ACPI and legacy methods failed
Dec  5 16:50:10 LeaMonde kernel: [   61.562680] powernow: See [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.html)
Dec  5 16:50:13 LeaMonde kernel: [   65.455672] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Dec  5 16:50:13 LeaMonde kernel: [   65.455683] apm: overridden by ACPI.
Dec  5 16:50:14 LeaMonde kernel: [   65.773393] ppdev: user-space parallel port driver
Dec  5 16:50:14 LeaMonde kernel: [   66.239182] audit(1228503014.602:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5140 profile="/usr/sbin/cupsd" namespace="default"
Dec  5 16:50:17 LeaMonde kernel: [   68.849853] NET: Registered protocol family 10
Dec  5 16:50:17 LeaMonde kernel: [   68.850892] lo: Disabled Privacy Extensions
Dec  5 16:50:17 LeaMonde dhcdbd: Started up.
Dec  5 16:50:20 LeaMonde kernel: [   72.029318] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Dec  5 16:50:20 LeaMonde dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec  5 16:50:20 LeaMonde kernel: [   72.254851] Bluetooth: Core ver 2.11
Dec  5 16:50:20 LeaMonde kernel: [   72.256285] NET: Registered protocol family 31
Dec  5 16:50:20 LeaMonde kernel: [   72.256293] Bluetooth: HCI device and connection manager initialized
Dec  5 16:50:20 LeaMonde kernel: [   72.256301] Bluetooth: HCI socket layer initialized
Dec  5 16:50:20 LeaMonde kernel: [   72.361801] Bluetooth: L2CAP ver 2.9
Dec  5 16:50:20 LeaMonde kernel: [   72.361810] Bluetooth: L2CAP socket layer initialized
Dec  5 16:50:20 LeaMonde kernel: [   72.516711] Bluetooth: RFCOMM socket layer initialized
Dec  5 16:50:20 LeaMonde kernel: [   72.516747] Bluetooth: RFCOMM TTY layer initialized
Dec  5 16:50:20 LeaMonde kernel: [   72.516751] Bluetooth: RFCOMM ver 1.8
Dec  5 16:50:22 LeaMonde kernel: [   74.544194] NET: Registered protocol family 17
Dec  5 16:50:23 LeaMonde dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Dec  5 16:50:23 LeaMonde dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec  5 16:50:23 LeaMonde dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Dec  5 16:50:23 LeaMonde dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Dec  5 16:50:23 LeaMonde kernel: [   75.097861] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Dec  5 16:50:23 LeaMonde kernel: [   75.098632] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Dec  5 16:50:23 LeaMonde kernel: [   75.099554] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Dec  5 16:50:34 LeaMonde pulseaudio[5927]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Dec  5 17:09:14 LeaMonde syslogd 1.5.0#1ubuntu1: restart.

---

### Post by vagrant87 on 2008-12-09
can someone help me please?

---

