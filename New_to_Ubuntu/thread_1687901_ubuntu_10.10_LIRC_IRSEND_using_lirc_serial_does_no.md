---
title: "ubuntu 10.10 LIRC IRSEND using lirc_serial does nothing"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by Gadgetman on 2011-02-14
I have recently built a new 10.10 and installed MythTV and LIRC.
I have correctly (?) configured LIRC for my specific IR Blaster on the serial port. Using the test send (see below), nothing happens - ie none of the pins on the serial port change state, and hence my IR Blaster hardware does nothing. No errors are produced and the log output looks good (?) - see below.
# irsend  SEND_ONCE DSTV9110 1 2 3

tail -f /var/log/syslog
Feb 15 00:56:56 MalutiPVR2 lircd-0.8.7-pre3[10127]: lircd(default) ready, using /var/run/lirc/lircd
Feb 15 00:57:04 MalutiPVR2 lircd-0.8.7-pre3[10127]: accepted new client on /var/run/lirc/lircd
Feb 15 00:57:04 MalutiPVR2 lircd-0.8.7-pre3[10127]: removed client

root@MalutiPVR2:/etc/lirc# ls -l /dev/lirc*
crw------- 1 root root 250, 0 2011-02-13 07:42 /dev/lirc0
lrwxrwxrwx 1 root root     19 2011-02-15 00:56 /dev/lircd -> /var/run/lirc/lircd

I also re-enabled /dev/ttyS0 (as it has to be disabled for LIRC) and sent data to the port (echo hello > /dev/ttyS0), and found data on TX pin & DTR pin (using scope) just to prove to myself that the com port is working!

All of this works perfectly on my 10.04 installation. I still have the 10.04 installation so have been able to compare configs etc.

I note that on 10.04 ***lirc 0.8.6-0ubuntu4.2*** is installed, whereas on 10.10 ***lirc 0.8.7~pre3-0ubuntu1*** is installed.

Some configs:-
**/etc/lirc/lircd.conf** 
#Configuration for the Home-brew (16x50 UART Hauppauge PVR-150 RC) remote:
include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"

#Configuration for the Home-brew (16x50 Serial Port UART] : DSTV Satellite Receiver transmitter:
include "/usr/share/lirc/extras/transmitters/dstv/dstv9110.conf"

[B]/etc/lirc/hardware.conf
[/B]REMOTE="Home-brew (16x50 UART Hauppauge PVR-150 RC)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="Home-brew (16x50 Serial Port UART] : DSTV Satellite Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="dstv/dstv9110.conf"
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES="true"
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

What could be wrong?
Do others have this working?

---

### Post by tiplady on 2011-02-17
I'm having a similar problem have you managed to solve this yet?

---

### Post by Stonh on 2011-05-12
Try to change order of loading modules:
from REMOTE_MODULES="lirc_dev lirc_serial"
to REMOTE_MODULES="lirc_serial lirc_dev"

After restart of lirc I had another problem. In message log file I got next message:
lirc_serial: use 'setserial /dev/ttySX uart none'

Than i did as the message said (setserial /dev/ttyS0 uart none) and all works fine.

I hope this help you.

Bye TS

---

