---
title: "I really need some help installing HP Scanjet 4200"
date: 2009-02-06
forum: New to Ubuntu
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

### Post by taseedorf on 2009-02-06
Before every command you type when installing this printer use sudo

so...

sudo sane-find-scanner

that will probably work for you.  I have a very similar machine as you, and mine installed right after I plugged it in.

---

### Post by ivanvajar on 2009-02-09
I've been asking for help with installing HP ScanJet 2400. People here were very helpfull, but there was still some things to workout on myown. If You have the same problem, this is the solution that worked in Ubuntu 8.04. First of all, download drivers from [http://www.elcot.in/linuxdrivers_download.php](http://www.elcot.in/linuxdrivers_download.php) and follow the procedure included, but, there may be some problems with extracting files to target dirs.

There are archives hp2400.tgz and libsane.tgz in the downloaded file.
-Extract them manualy by right-clicking them and 'extract here'.
-Use 'sudo' or open Root(Superuser)Terminal to copy files from those dirs manualy using 'cp' command. It's not hard to work it out.

Here are the examples for those who do not feel comfortable using terminal:

root@ivan-desktop:/home/ivan# cd Desktop/scanner/2400rv/hp2400/usr/lib/sane
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/hp2400/usr/lib/sane# ls
libsane-hp2400.la  libsane-hp2400.so.1
libsane-hp2400.so  libsane-hp2400.so.1.0.18
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/hp2400/usr/lib/sane# cp libsane-hp2400.la /usr/lib/sane/libsane-hp2400.la
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/hp2400/usr/lib/sane# cp libsane-hp2400.la /usr/lib/sane/libsane-hp2400.so
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/hp2400/usr/lib/sane# cp libsane-hp2400.la /usr/lib/sane/libsane-hp2400.so.1
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/hp2400/usr/lib/sane# cp libsane-hp2400.la /usr/lib/sane/libsane-hp2400.so.1.0.18

AND for the other directory:

root@ivan-desktop:/home/ivan# cd Desktop/scanner/2400rv/usr/lib#
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/usr/lib# ls
libsane.la  libsane.so  libsane.so.1  libsane.so.1.0.14
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/usr/lib# copy libsane.la /usr/lib/libsane.la
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/usr/lib# copy libsane.la /usr/lib/libsane.so
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/usr/lib# copy libsane.la /usr/lib/libsane.so.1
root@ivan-desktop:/home/ivan/Desktop/scanner/2400rv/usr/lib# copy libsane.la /usr/lib/libsane.so.1.0.18


Scanner will work when you load settings for it in XSane => Preferences/load device settings, but some features will not work, such as scanning in grayscale, which is not much of a problem :-)

---

