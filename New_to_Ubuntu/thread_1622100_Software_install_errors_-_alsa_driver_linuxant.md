---
title: "Software install errors - alsa driver linuxant?"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Garrote2010r on 2010-11-15
Hello all,

It seems everytime I download a program from the Software Center, it doesn't seem to install correctly.  Here I tried to install Alsamixer.  Any help would be greatly appreciated:

installArchives() failed: Selecting previously deselected package gnome-alsamixer.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 203584 files and directories currently installed.)
Unpacking gnome-alsamixer (from .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for python-support ...
Setting up alsa-driver-linuxant (1.0.18.0) ...
Building modules for the 2.6.32-25-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.4334.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up gnome-alsamixer (0.9.7~cvs.20060916.ds.1-2) ...

Errors were encountered while processing:
 alsa-driver-linuxant
Setting up alsa-driver-linuxant (1.0.18.0) ...
Building modules for the 2.6.32-25-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.8623.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2

Please help!

---

### Post by anewguy on 2010-11-15
What does it say in:

/tmp/alsa-driver-linuxant.4334.log

and

/tmp/alsa-driver-linuxant.8623.log


You may also want to be sure the build-essential package is installed:

- in Synaptic Package Manager (System/Administration/Synaptic Package Manager):

search for build-essential and be sure it is installed

There may also be other packages that prerequisites.

Dave ;)

---

### Post by Garrote2010r on 2010-11-15
> **anewguy said:**
> What does it say in:

/tmp/alsa-driver-linuxant.4334.log

and

/tmp/alsa-driver-linuxant.8623.log


You may also want to be sure the build-essential package is installed:

- in Synaptic Package Manager (System/Administration/Synaptic Package Manager):

search for build-essential and be sure it is installed

There may also be other packages that prerequisites.

Dave ;)

Hi Dave,

Thanks for offering your input.  I was unable to successfully install the Build-essential pack as I got this message:

E: alsa-driver-linuxant: subprocess installed post-installation script returned error exit status 2

As for the log files, mine are slightly different:

alsa-driver-linuxant.6633.log:

rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/acore'
make -C ioctl32 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
make -C oss mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/oss'
make -C seq mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq'
make -C oss mrproper
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c'
make -C l3 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
make -C other mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers'
make -C mpu401 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
make -C opl3 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
make -C opl4 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
make -C pcsp mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
make -C vx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/isa'
make -C ad1816a mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
make -C ad1848 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
make -C cs423x mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
make -C es1688 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
make -C gus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/gus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/gus'
make -C msnd mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
make -C opti9xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
make -C sb mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/sb'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/sb'
make -C wavefront mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
make -C wss mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/synth'
make -C emux mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/pci'
make -C ac97 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
make -C ali5451 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
make -C asihpi mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
make -C au88x0 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
make -C aw2 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
make -C ca0106 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
make -C cs46xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
make -C cs5535audio mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
make -C echoaudio mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
make -C emu10k1 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
make -C hda mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/hda'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/hda'
make -C ice1712 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
make -C korg1212 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
make -C mixart mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
make -C nm256 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
make -C oxygen mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
make -C pcxhr mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
make -C pdplus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
make -C riptide mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
make -C rme9652 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
make -C trident mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/trident'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/trident'
make -C vx222 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
make -C ymfpci mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa'
make -C codecs mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
make -C core mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/core'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/core'
make -C fabrics mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
make -C soundbus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
make -C i2sbus mrproper
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/soc'
make -C at32 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/at32'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/at32'
make -C at91 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/at91'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/at91'
make -C au1x mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
make -C blackfin mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
make -C codecs mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
make -C davinci mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
make -C fsl mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
make -C omap mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/omap'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/omap'
make -C pxa mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
make -C s3c24xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
make -C sh mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/sh'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/sh'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/usb'
make -C caiaq mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
make -C usx2y mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make -C pdaudiocf mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
make -C vx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/misc'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/misc'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/include'
rm -f .depend core *.o sndversions.h modules/*.ver modules/*.stamp
rm -f *.orig *.rej *~ .#*
rm -f linux/* asm/* media/*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/include'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/test'
rm -f *.o mmap_test osspcm osspcm1 ossdelay
rm -f *~ *.orig *.rej .#*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/test'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/utils'
rm -f *.orig *.rej *~ .#*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/utils'
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -rf autom4te.cache
rm -f alsa-kernel/include/version.h
rm -f include/sound
rm -fr .tmp_versions
rm -f Module.symvers
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/lib/alsa-driver-linuxant
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.32-25-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.32-25-generic
checking for GCC version... ./configure: eval: line 5117: syntax error near unexpected token `)'
./configure: eval: line 5117: `my_compiler_version=4.4.3-4ubuntu5)'
./configure: line 5117: warning: syntax errors in . or eval will cause future versions of the shell to abort as Posix requires
Kernel compiler:  Used compiler: gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... no
Creating a dummy <asm/hw_irq.h>...
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/io.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos_params.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... no
Creating a dummy <asm/irq_regs.h>...
checking for kernel linux/seq_file.h... yes
checking for kernel linux/debugfs.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker input subsystem in kernel... module
checking for directory to store kernel modules... /lib/modules/2.6.32-25-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... yes
checking for video_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kstrndup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for pci_ioremap_bar... yes
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.18
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... no
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... all
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
cp -pvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant'
#@for d in acore i2c drivers isa synth pci aoa soc usb pcmcia misc; do if ! make -C $d prepare; then exit 1; fi; done
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant'
make -C /lib/modules/2.6.32-25-generic/build SUBDIRS=/usr/lib/alsa-driver-linuxant  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/hwdep.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memory_wrapper.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memalloc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sgbuf.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_native.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_misc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_memory.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/rawmidi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/wrappers.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/misc_driver.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sound.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/init.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memory.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/info.o
/usr/lib/alsa-driver-linuxant/acore/info.c: In function ‘snd_info_entry_prepare’:
/usr/lib/alsa-driver-linuxant/acore/info.c:161: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/lib/alsa-driver-linuxant/acore/info.c: In function ‘snd_info_register’:
/usr/lib/alsa-driver-linuxant/acore/info.c:1003: error: ‘struct proc_dir_entry’ has no member named ‘owner’
make[3]: *** [/usr/lib/alsa-driver-linuxant/acore/info.o] Error 1
make[2]: *** [/usr/lib/alsa-driver-linuxant/acore] Error 2
make[1]: *** [_module_/usr/lib/alsa-driver-linuxant] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [compile] Error 2

alsa-driver-linuxant.10858.log:

rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/acore'
make -C ioctl32 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
make -C oss mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/oss'
make -C seq mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq'
make -C oss mrproper
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c'
make -C l3 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
make -C other mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers'
make -C mpu401 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
make -C opl3 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
make -C opl4 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
make -C pcsp mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
make -C vx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/isa'
make -C ad1816a mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
make -C ad1848 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
make -C cs423x mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
make -C es1688 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
make -C gus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/gus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/gus'
make -C msnd mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
make -C opti9xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
make -C sb mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/sb'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/sb'
make -C wavefront mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
make -C wss mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/synth'
make -C emux mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/pci'
make -C ac97 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
make -C ali5451 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
make -C asihpi mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
make -C au88x0 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
make -C aw2 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
make -C ca0106 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
make -C cs46xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
make -C cs5535audio mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
make -C echoaudio mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
make -C emu10k1 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
make -C hda mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/hda'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/hda'
make -C ice1712 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
make -C korg1212 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
make -C mixart mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
make -C nm256 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
make -C oxygen mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
make -C pcxhr mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
make -C pdplus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
make -C riptide mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
make -C rme9652 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
make -C trident mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/trident'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/trident'
make -C vx222 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
make -C ymfpci mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa'
make -C codecs mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
make -C core mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/core'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/core'
make -C fabrics mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
make -C soundbus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
make -C i2sbus mrproper
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/soc'
make -C at32 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/at32'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/at32'
make -C at91 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/at91'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/at91'
make -C au1x mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
make -C blackfin mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
make -C codecs mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
make -C davinci mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
make -C fsl mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
make -C omap mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/omap'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/omap'
make -C pxa mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
make -C s3c24xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
make -C sh mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/sh'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/sh'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/usb'
make -C caiaq mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
make -C usx2y mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make -C pdaudiocf mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
make -C vx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/misc'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/misc'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/include'
rm -f .depend core *.o sndversions.h modules/*.ver modules/*.stamp
rm -f *.orig *.rej *~ .#*
rm -f linux/* asm/* media/*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/include'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/test'
rm -f *.o mmap_test osspcm osspcm1 ossdelay
rm -f *~ *.orig *.rej .#*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/test'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/utils'
rm -f *.orig *.rej *~ .#*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/utils'
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -rf autom4te.cache
rm -f alsa-kernel/include/version.h
rm -f include/sound
rm -fr .tmp_versions
rm -f Module.symvers
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/lib/alsa-driver-linuxant
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.32-25-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.32-25-generic
checking for GCC version... ./configure: eval: line 5117: syntax error near unexpected token `)'
./configure: eval: line 5117: `my_compiler_version=4.4.3-4ubuntu5)'
./configure: line 5117: warning: syntax errors in . or eval will cause future versions of the shell to abort as Posix requires
Kernel compiler:  Used compiler: gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... no
Creating a dummy <asm/hw_irq.h>...
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/io.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos_params.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... no
Creating a dummy <asm/irq_regs.h>...
checking for kernel linux/seq_file.h... yes
checking for kernel linux/debugfs.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker input subsystem in kernel... module
checking for directory to store kernel modules... /lib/modules/2.6.32-25-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... yes
checking for video_drvdata... yes
checking for V4L1 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kstrndup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for pci_ioremap_bar... yes
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.18
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... yes
checking for x86-compatible PC... no
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... all
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
if [ ! -d include/sound -a ! -L include/sound ]; then \
	  ln -sf ../alsa-kernel/include include/sound ; \
	fi
cp -pvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant'
#@for d in acore i2c drivers isa synth pci aoa soc usb pcmcia misc; do if ! make -C $d prepare; then exit 1; fi; done
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant'
make -C /lib/modules/2.6.32-25-generic/build SUBDIRS=/usr/lib/alsa-driver-linuxant  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/hwdep.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memory_wrapper.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memalloc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sgbuf.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_native.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_lib.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_misc.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_memory.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/rawmidi.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/timer.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/wrappers.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/misc_driver.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sound.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/init.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memory.o
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/info.o
/usr/lib/alsa-driver-linuxant/acore/info.c: In function ‘snd_info_entry_prepare’:
/usr/lib/alsa-driver-linuxant/acore/info.c:161: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/usr/lib/alsa-driver-linuxant/acore/info.c: In function ‘snd_info_register’:
/usr/lib/alsa-driver-linuxant/acore/info.c:1003: error: ‘struct proc_dir_entry’ has no member named ‘owner’
make[3]: *** [/usr/lib/alsa-driver-linuxant/acore/info.o] Error 1
make[2]: *** [/usr/lib/alsa-driver-linuxant/acore] Error 2
make[1]: *** [_module_/usr/lib/alsa-driver-linuxant] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [compile] Error 2

Any recommendations?

---

### Post by anewguy on 2010-11-16
From both, we can see there is an error in the source code for the info.c file itself - look for this: 

```
CC [M] /usr/lib/alsa-driver-linuxant/acore/info.o
/usr/lib/alsa-driver-linuxant/acore/info.c: In function &#8216;snd_info_entry_prepare&#8217;:
/usr/lib/alsa-driver-linuxant/acore/info.c:161: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
/usr/lib/alsa-driver-linuxant/acore/info.c: In function &#8216;snd_info_register&#8217;:
/usr/lib/alsa-driver-linuxant/acore/info.c:1003: error: &#8216;struct proc_dir_entry&#8217; has no member named &#8216;owner&#8217;
```


I also note there is an error apparently in configure:

```
checking for GCC version... ./configure: eval: line 5117: syntax error near unexpected token `)'
./configure: eval: line 5117: `my_compiler_version=4.4.3-4ubuntu5)'
./configure: line 5117: warning: syntax errors in . or eval will cause future versions of the shell to abort as Posix requires

```

As far a build-essential goes, before you try the configure, be sure it is installed if you haven't already done so (not sure if it will fix the problem unless the"owner" structure is actually defined in the linux headers):

sudo apt-get install build-essential <press enter>  If prompted for a password, use your default password.

It's possible that if you get build-essential installed FIRST, then run the script, that it will compile ok.  If there is an error anywhere along the way, stop, copy the screen and post it back here.

Dave ;)

---

### Post by Garrote2010r on 2010-11-16
Ran this command in terminal, sudo apt-get install build-essential, then got this:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up alsa-driver-linuxant (1.0.18.0) ...
Building modules for the 2.6.32-25-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.6214.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 alsa-driver-linuxant
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Garrote2010r on 2010-11-16
Bump.. Can anyone please advise on how to repair this issue?

---

### Post by anewguy on 2010-11-20
Maybe we should ask another question at this point - why do you need this?  Can't you install the alsa stuff via synaptic package manager?  Doing so would be sure to get all dependencies and hopefully a package that works.  What you have now has errors in the source - I would suggest contacting whoever is in charge of the package, perhaps where you downloaded it from?

Dave ;)

---

### Post by sonicborg on 2010-12-10
I am actually having the same issue. This came about because I was following another guide on this forum for Asus K52F laptops, where I wanted to make my laptop speaks mute when I plugin my headphones.

Since I did the step that advises downloading and coping across the snd-hda-codec-conexant.ko to the /lib/modules/[KERNEL VERS HERE]/kernel/sound/pci/hda 

I have now been getting errors in relation to this, exactly the same as above, and during boot time it says that the module is invalid type. 
I have actually removed the file from that directory but still get the same errors so I'm assuming I must have loaded it into the kernel at somepoint (lost track of all the things I've done over hte last few days sorry)

I have install kernel 2.6.36, and can only think that part of the issue might be that the file I copied across was part of patched-conexant-driver-kernel-2.6.35-23.tar.gz which is a kernel before hand?

Maybe I need to download 2.6.36 again, find the .ko file in there and recompile my kernel with this correct version ?

I apologise for my niavity, fairly new to linux after not using it for 10 years, alot has changed. :)

---

