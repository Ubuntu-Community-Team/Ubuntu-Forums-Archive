---
title: "Problems with Dial up modem"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by Sonyadora on 2008-08-24
I just purchased an ideapad y150 and I love it! I was hoping that someone here could help me figure out how to get the dial up modem working though. I'm new to Linux and I think I might have screwed something up fiddling around.

I followed the dial up modem instructions on ubuntu's support pages and ran scanModem. The results:

Quote:
-------------------------- System information ----------------------------
CPU=i686,
Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008
scanModem update of: 2008_08_19

There are no blacklisted modem drivers in /etc/modprobe* files
Attached USB devices are:
ID 5986:0200 Bison

USB modems not recognized

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
PCI slot PCI ID SubsystemID Name
---------- --------- --------- --------------
00:1b.0 8086:284b 17aa:3d96 Audio device: Intel Corporation 82801H

Modem interrupt assignment and sharing:
23: 348 351 IO-APIC-fasteoi HDA Intel
--- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[ 30.510152] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[ 30.510188] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics =====
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.16
The modem cards detected by "aplay -l" are:
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

The /proc/asound/pcm file reports:
-----------------------
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-02: ALC883 Analog : ALC883 Analog : capture 1
00-01: ALC883 Digital : ALC883 Digital : playback 1
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xfeaf8000 irq 23

PCI slot 00:1b.0 has a High Definition Audio Card
The drivers are in the kernel modules tree at:
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko
The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Motorola Si3054
Address: 1
Vendor Id: 0x10573055
Subsystem Id: 0x17aa3d7d
Revision Id: 0x100700
Modem Function Group: 0x1

The audio card hosts a softmodem chip: 0x10573055

The softmodem chip 0x10573055 is in principle supported by the COMM support of slmodemd
and the joint snd-hda-intel audio+modem driver, begun with ALSA version 1.0.13.
For HDA cards with ALC883 chips, an upgrade to ALSA verions 1.0.15 way be necessary. Instructions for Upgrading snd-hda-intel and its dependent driver set are at:
[http://linmodems.technion.ac.il/biga.../msg00838.html](http://linmodems.technion.ac.il/biga.../msg00838.html)

If not a Conexant modem, the driver snd-hda-intel with its dependent drivers:
snd_hda_intel 344728 3
snd_pcm 78596 2 snd_hda_intel,snd_pcm_oss
snd_page_alloc 11400 2 snd_hda_intel,snd_pcm
snd_hwdep 10500 1 snd_hda_intel
snd 56996 17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,sn d_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_ seq,snd_timer,snd_seq_device
----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips.

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:1b.0:
Modem chipset detected on
NAME="Audio device: Intel Corporation 82801H "
CLASS=0403
PCIDEV=8086:284b
SUBSYS=17aa:3d96
IRQ=23
HDA=8086:284b
SOFT=8086:284b.HDA
CHIP=0x10573055
IDENT=slmodemd
SLMODEMD_DEVICE=hw:0,6
Driver=snd-hda-intel

For candidate modem in: 00:1b.0
0403 Audio device: Intel Corporation 82801H
Primary device ID: 8086:284b
Subsystem PCI_id 17aa:3d96
Softmodem codec or chipset from diagnostics: 0x10573055
from Archives:
The HDA card softmodem chip is 0x10573055


Support type needed or chipset: slmodemd supporting the snd-hda-intel audio+modem driver

An ALSA (Advanced Linux Sound Architecture) modem driver: snd-hda-intel
provides Low Level support enabling contact with the modem hardware.
For all BUT Conexant chip soft modems (using hsfmodem software)
complementary High Level support is through a Smartlink utility: slmodemd
This was quite an overwhelming amount of information for me, but it seemed like I should be using ALSA drivers so I followed the instructions here: [https://help.ubuntu.com/community/Di...owto/AlsaModem](https://help.ubuntu.com/community/Di...owto/AlsaModem) and installed the slmodem-daemon and slmodem-source packages using synaptic. and ran sudo /etc/init.d/sl-modem-daemon restart and got this output:

Shutting down SmartLink Modem driver normally ... no slmodemd daemon running.
Unloading modem driver from kernel ... snd_atiixp_modem.
FATAL: Module ungrab_winmodem not found
FATAL: Module slamr not found.
Starting SmartLink Modem driver for: auto.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

Well, that made me think I needed to follow the instructions here: [https://help.ubuntu.com/community/Di...owto/Smartlink](https://help.ubuntu.com/community/Di...owto/Smartlink)

At the first step to compile the driver things seemed to be working out, but failed halfway through. The log file looks like this:

Quote:
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem'
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem/modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem/modem'
dh_clean
/usr/bin/make -C drivers clean
make[1]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[1]: Leaving directory `/usr/src/modules/sl-modem/drivers'
/usr/bin/make -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/sl-modem'
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem'
make[2]: *** No rule to make target `clean'. Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem'
make[1]: [clean] Error 2 (ignored)
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem/modem'
make[2]: *** No rule to make target `clean'. Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem/modem'
make[1]: [clean] Error 2 (ignored)
dh_clean
/usr/bin/make -C drivers clean
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
for templ in /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.backup /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.modules.in; do \
cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.24-19-generic/g'` ; \
done
for templ in `ls debian/*.modules.in` ; do \
test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
sed -e 's/##KVERS##/2.6.24-19-generic/g ;s/#KVERS#/2.6.24-19-generic/g ; s/_KVERS_/2.6.24-19-generic/g ; s/##KDREV##/2.6.24-19.36/g ; s/#KDREV#/2.6.24-19.36/g ; s/_KDREV_/2.6.24-19.36/g ' < $templ > ${templ%.modules.in}; \
done
dh_clean -k
dh_installdirs lib/modules/2.6.24-19-generic/misc usr/lib/sl-modem
if ! test -e drivers/Makefile ; then echo "Please update the package, extract the tarball!"; exit 1 ; fi
/usr/bin/make -C drivers KERNEL_DIR=/usr/src/linux KVERS=2.6.24-19-generic
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
gcc -I/usr/src/linux/include -o kernel-ver kernel-ver.c
kernel-ver.c: In function ‘main’:
kernel-ver.c:11: error: ‘UTS_RELEASE’ undeclared (first use in this function)
kernel-ver.c:11: error: (Each undeclared identifier is reported only once
kernel-ver.c:11: error: for each function it appears in.)
make[2]: *** [kernel-ver] Error 1
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/sl-modem'
make: *** [kdist_build] Error 2

Clearly, I'm in way over my head, since I don't understand just what all the commands were meant to do anyway, I'm not able to make sense of where they went wrong. Any guidance would be appreciated.

---

### Post by Paul S on 2008-09-09
You should be able to get some help by posting your report on the linmodems.org mailing list.  It looks like it's identified your modem as motorola and might be suggesting it can be made to work using an alsa driver with the slmodem command.

Keep trying and you should find someone with the exact help.

regards,

---

