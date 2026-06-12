---
title: "How to install HP ScanJet 4200 in Ubuntu"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by ivanvajar on 2009-02-06
How to install HP ScanJet 4200 in Ubuntu? I made sane-find-scanner find scanner on usb port, but it is still as good as dead. Does anyone know what should I do?

---

### Post by mjheagle8 on 2009-02-06
[http://ubuntuforums.org/showthread.php?t=734361](http://ubuntuforums.org/showthread.php?t=734361)
should help.
:)

---

### Post by ivanvajar on 2009-02-06
Thanks!

---

### Post by mjheagle8 on 2009-02-06
no problem. glad i could help!

---

### Post by ivanvajar on 2009-02-06
I have some problems installing HP ScanJet 2400
my /etc/sane.d/dll.conf looks like this and I have no idea what it means and what to do


# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# On Debian systems, the dll backend will also look for pieces of configuration
# in the /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory.
#

# enable the next line if you want to allow access through the network:
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
#canon_pp
cardscan
coolscan
coolscan2
#dc25
#dc210
#dc240
dell1600n_net
dmc
epjitsu
epson
#epson2
fujitsu
#gphoto2
genesys
gt68xx
hp
hp3900
hpsj5s
hp3500
hp4200
hp5400
hp5590
hpljm1005
hs2p
ibm
leo
lexmark
ma1509
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
mustek_usb2
nec
niash
pie
pixma
plustek
#plustek_pp
#pnm
qcam
ricoh
s9036
sceptre
sharp
sm3600
sm3840
snapscan
sp15c
#st400
#stv680
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
v4l

hpaio

HPLIP, libsane-extras and libsane-dev are installed, but Xane doesn't see scanner

when I run sane-find-scanner it comes up with this:
 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0, product=0x0a01, chip=GL646_HP?) at libusb:002:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

but scanner does not work. When I plug scanner, Xane loads, but it still can't scan.

---

