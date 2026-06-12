---
title: "No audio please help!"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by thefirstman on 2009-01-02
I am new to ubuntu. new to linux. i first installed knoppix about 7yrs ago. i have ubuntu 8.10, gnome 2.24.1 (intrepid). i have no startup sound, no system sounds, no sound from youtube etc. when i go to system-->preferences-->sound and try to test the sound/s i can hear nothing. at one time the tests worked but i think running the oss driver changed this some how. i have tried both alsa and oss to no avail. the volume is up, my speakers work and are plugged in. i have swapped sound cards... i have tried some things in other posts with no success. thanks in advance for any help or suggestions.

---

### Post by abn91c on 2009-01-02
run in terminal **aplay -l**

---

### Post by thefirstman on 2009-01-02
aplay: device list:215: no soundcards found...

---

### Post by khelben1979 on 2009-01-02
Maybe [this]("http://ubuntuforums.org/showthread.php?t=1027809") can help you.

A future advice: try searching this Ubuntu forum. The database is starting to get "a bit" large now. :)

---

### Post by thefirstman on 2009-01-02
thanks khelben1979 i have downloaded all the packages...what is the quickest way to install them?

---

### Post by khelben1979 on 2009-01-02
Create a directory which you call ALSA. Then extract all archives in this catalog.

When you enter each catalog you do this:

./configure
make
make install

for all the [ALSA]("http://alsa.opensrc.org/index.php?page=AlsaOpensrcOrg") package files. 

Then you go off using the script which was explained above.
You may also haveto run [the alsaconf program]("http://man-wiki.net/index.php/8:alsaconf") in order to setup your sound card.

[This guide]("http://www.linux.com/base/ldp/howto/Alsa-sound.htmlt#toc5") may also be useful.

---

### Post by thefirstman on 2009-01-02
thanks so much for helping me. i made the directory alsa. i have extracted all the packages there. i am not sure how to enter each catalog. i apologize for my ignorance but am a newbie. thanks for your patience.

---

### Post by khelben1979 on 2009-01-02
Open a text terminal (for example XTERM).

Then use the cd command to navigate back and forth through the directory structure.

For example if you have chosen to place the ALSA directory in /home/thefirstman/

cd /home/thefirstman/
cd ALSA

Then use the cd command to get into each of these catalogs and going through the three steps which I mentioned for configuring up and compiling up the source code.

You don't need to excuse yourself on this b.t.w. Compiling source code is not for newbies. ):P

---

### Post by thefirstman on 2009-01-02
Did I do something wrong?

jdimaio@box:~/alsa$ cd alsa-firmware-1.0.17
jdimaio@box:~/alsa/alsa-firmware-1.0.17$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for as31... no
checking firmware installation directory... /lib/firmware
configure: creating ./config.status
config.status: creating Makefile
config.status: creating hdsploader/Makefile
config.status: creating mixartloader/Makefile
config.status: creating usx2yloader/Makefile
config.status: creating vxloader/Makefile
config.status: creating pcxhrloader/Makefile
config.status: creating echoaudio/Makefile
config.status: creating emi_26_62/Makefile
config.status: creating emu/Makefile
config.status: creating asihpi/Makefile
config.status: creating korg1212/Makefile
config.status: creating maestro3/Makefile
config.status: creating multisound/Makefile
config.status: creating sb16/Makefile
config.status: creating wavefront/Makefile
config.status: creating ymfpci/Makefile
config.status: creating aica/Makefile
config.status: executing depfiles commands
jdimaio@box:~/alsa/alsa-firmware-1.0.17$ make
Making all in hdsploader
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/hdsploader'
if gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"alsa-firmware\" -DVERSION=\"1.0.17\" -DSTDC_HEADERS=1 -I. -I.     -g -O2 -MT tobin.o -MD -MP -MF ".deps/tobin.Tpo" -c -o tobin.o tobin.c; \
	then mv -f ".deps/tobin.Tpo" ".deps/tobin.Po"; else rm -f ".deps/tobin.Tpo"; exit 1; fi
gcc  -g -O2   -o tobin  tobin.o  
./tobin
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/hdsploader'
Making all in mixartloader
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/mixartloader'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/mixartloader'
Making all in pcxhrloader
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/pcxhrloader'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/pcxhrloader'
Making all in usx2yloader
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/usx2yloader'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/usx2yloader'
Making all in vxloader
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/vxloader'
if gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"alsa-firmware\" -DVERSION=\"1.0.17\" -DSTDC_HEADERS=1 -I. -I.     -g -O2 -MT toxlx.o -MD -MP -MF ".deps/toxlx.Tpo" -c -o toxlx.o toxlx.c; \
	then mv -f ".deps/toxlx.Tpo" ".deps/toxlx.Po"; else rm -f ".deps/toxlx.Tpo"; exit 1; fi
gcc  -g -O2   -o toxlx  toxlx.o  
./toxlx < x1_2_v22.rbt > x1_2_v22.xlx
./toxlx < x1_1_vx2.rbt > x1_1_vx2.xlx
./toxlx < x1_1_vxp.rbt > x1_1_vxp.xlx
./toxlx < x1_1_vp4.rbt > x1_1_vp4.xlx
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/vxloader'
Making all in echoaudio
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/echoaudio'
if gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"alsa-firmware\" -DVERSION=\"1.0.17\" -DSTDC_HEADERS=1 -I. -I.     -g -O2 -MT fw_writer.o -MD -MP -MF ".deps/fw_writer.Tpo" -c -o fw_writer.o fw_writer.c; \
	then mv -f ".deps/fw_writer.Tpo" ".deps/fw_writer.Po"; else rm -f ".deps/fw_writer.Tpo"; exit 1; fi
gcc  -g -O2   -o fw_writer  fw_writer.o  
./fw_writer DSP/LoaderDSP.c loader_dsp.fw
./fw_writer DSP/Darla20DSP.c darla20_dsp.fw
./fw_writer DSP/Gina20DSP.c gina20_dsp.fw
./fw_writer DSP/Layla20DSP.c layla20_dsp.fw
./fw_writer ASIC/LaylaASIC.c layla20_asic.fw
./fw_writer DSP/Darla24DSP.c darla24_dsp.fw
./fw_writer DSP/Gina24DSP.c gina24_301_dsp.fw
./fw_writer ASIC/Gina24ASIC.c gina24_301_asic.fw
./fw_writer DSP/Gina24_361DSP.c gina24_361_dsp.fw
./fw_writer ASIC/Gina24ASIC_361.c gina24_361_asic.fw
./fw_writer DSP/Layla24DSP.c layla24_dsp.fw
./fw_writer ASIC/Layla24_1ASIC.c layla24_1_asic.fw
./fw_writer ASIC/Layla24_2A_ASIC.c layla24_2A_asic.fw
./fw_writer ASIC/Layla24_2S_ASIC.c layla24_2S_asic.fw
./fw_writer DSP/MonaDSP.c mona_301_dsp.fw
./fw_writer ASIC/Mona1ASIC48.c mona_301_1_asic_48.fw
./fw_writer ASIC/Mona1ASIC96.c mona_301_1_asic_96.fw
./fw_writer DSP/Mona361DSP.c mona_361_dsp.fw
./fw_writer ASIC/Mona1ASIC48_361.c mona_361_1_asic_48.fw
./fw_writer ASIC/Mona1ASIC96_361.c mona_361_1_asic_96.fw
./fw_writer ASIC/Mona2ASIC.c mona_2_asic.fw
./fw_writer DSP/MiaDSP.c mia_dsp.fw
./fw_writer DSP/Echo3gDSP.c echo3g_dsp.fw
./fw_writer ASIC/3G_ASIC.c 3g_asic.fw
./fw_writer DSP/IndigoDSP.c indigo_dsp.fw
./fw_writer DSP/IndigoIODSP.c indigo_io_dsp.fw
./fw_writer DSP/IndigoDJDSP.c indigo_dj_dsp.fw
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/echoaudio'
Making all in asihpi
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/asihpi'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/asihpi'
Making all in emi_26_62
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/emi_26_62'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/emi_26_62'
Making all in emu
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/emu'
if gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"alsa-firmware\" -DVERSION=\"1.0.17\" -DSTDC_HEADERS=1 -I. -I.     -g -O2 -MT fw_writer.o -MD -MP -MF ".deps/fw_writer.Tpo" -c -o fw_writer.o fw_writer.c; \
	then mv -f ".deps/fw_writer.Tpo" ".deps/fw_writer.Po"; else rm -f ".deps/fw_writer.Tpo"; exit 1; fi
gcc  -g -O2   -o fw_writer  fw_writer.o  
./fw_writer
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/emu'
Making all in korg1212
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/korg1212'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/korg1212'
Making all in maestro3
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/maestro3'
if gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"alsa-firmware\" -DVERSION=\"1.0.17\" -DSTDC_HEADERS=1 -I. -I.     -g -O2 -MT fw_writer.o -MD -MP -MF ".deps/fw_writer.Tpo" -c -o fw_writer.o fw_writer.c; \
	then mv -f ".deps/fw_writer.Tpo" ".deps/fw_writer.Po"; else rm -f ".deps/fw_writer.Tpo"; exit 1; fi
gcc  -g -O2   -o fw_writer  fw_writer.o  
./fw_writer
writing maestro3_assp_kernel.fw ...
writing maestro3_assp_minisrc.fw ...
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/maestro3'
Making all in multisound
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/multisound'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/multisound'
Making all in sb16
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/sb16'
if gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"alsa-firmware\" -DVERSION=\"1.0.17\" -DSTDC_HEADERS=1 -I. -I.     -g -O2 -MT fw_writer.o -MD -MP -MF ".deps/fw_writer.Tpo" -c -o fw_writer.o fw_writer.c; \
	then mv -f ".deps/fw_writer.Tpo" ".deps/fw_writer.Po"; else rm -f ".deps/fw_writer.Tpo"; exit 1; fi
gcc  -g -O2   -o fw_writer  fw_writer.o  
./fw_writer
writing mulaw_main.csp ...
writing alaw_main.csp ...
writing ima_adpcm_init.csp ...
writing ima_adpcm_playback.csp ...
writing ima_adpcm_capture.csp ...
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/sb16'
Making all in wavefront
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/wavefront'
if gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"alsa-firmware\" -DVERSION=\"1.0.17\" -DSTDC_HEADERS=1 -I. -I.     -g -O2 -MT fw_writer.o -MD -MP -MF ".deps/fw_writer.Tpo" -c -o fw_writer.o fw_writer.c; \
	then mv -f ".deps/fw_writer.Tpo" ".deps/fw_writer.Po"; else rm -f ".deps/fw_writer.Tpo"; exit 1; fi
gcc  -g -O2   -o fw_writer  fw_writer.o  
./fw_writer
writing yss225_registers.bin ...
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/wavefront'
Making all in ymfpci
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/ymfpci'
if gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"alsa-firmware\" -DVERSION=\"1.0.17\" -DSTDC_HEADERS=1 -I. -I.     -g -O2 -MT fw_writer.o -MD -MP -MF ".deps/fw_writer.Tpo" -c -o fw_writer.o fw_writer.c; \
	then mv -f ".deps/fw_writer.Tpo" ".deps/fw_writer.Po"; else rm -f ".deps/fw_writer.Tpo"; exit 1; fi
gcc  -g -O2   -o fw_writer  fw_writer.o  
./fw_writer
writing ds1_dsp.fw ...
writing ds1_ctrl.fw ...
writing ds1e_ctrl.fw ...
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/ymfpci'
Making all in aica
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/aica'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/aica'
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17'
jdimaio@box:~/alsa/alsa-firmware-1.0.17$ make install
Making install in hdsploader
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/hdsploader'
make[2]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/hdsploader'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/alsa/firmware/hdsploader" || mkdir -p -- "/usr/local/share/alsa/firmware/hdsploader"
mkdir: cannot create directory `/usr/local/share/alsa': Permission denied
make[2]: *** [install-firmwareDATA] Error 1
make[2]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/hdsploader'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/hdsploader'
make: *** [install-recursive] Error 1
jdimaio@box:~/alsa/alsa-firmware-1.0.17$ make install
Making install in hdsploader
make[1]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/hdsploader'
make[2]: Entering directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/hdsploader'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/alsa/firmware/hdsploader" || mkdir -p -- "/usr/local/share/alsa/firmware/hdsploader"
mkdir: cannot create directory `/usr/local/share/alsa': Permission denied
make[2]: *** [install-firmwareDATA] Error 1
make[2]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/hdsploader'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-firmware-1.0.17/hdsploader'
make: *** [install-recursive] Error 1
jdimaio@box:~/alsa/alsa-firmware-1.0.17$

---

### Post by khelben1979 on 2009-01-02
You have to be logged on as root to be able to go through the make install process.

Type: [sudo]("http://en.wikipedia.org/wiki/Sudo") root
(enter password)

Then: make install
(do this step again for all your alsa catalogs)

---

### Post by thefirstman on 2009-01-02
ok i got firmware, lib, oss, plugins done. now i am on tools...here is what i got.

jdimaio@box:~$ cd /home/jdimaio/alsa
jdimaio@box:~/alsa$ cd alsa-tools-1.0.18
jdimaio@box:~/alsa/alsa-tools-1.0.18$ ./configure
bash: ./configure: No such file or directory
jdimaio@box:~/alsa/alsa-tools-1.0.18$ make
./ac3dec
./gitcompile: 3: aclocal: not found
make: *** [all] Error 1
jdimaio@box:~/alsa/alsa-tools-1.0.18$ su
Password: 
root@box:/home/jdimaio/alsa/alsa-tools-1.0.18# ./configure
bash: ./configure: No such file or directory
root@box:/home/jdimaio/alsa/alsa-tools-1.0.18# make
./ac3dec
./gitcompile: 3: aclocal: not found
make: *** [all] Error 1
root@box:/home/jdimaio/alsa/alsa-tools-1.0.18#

---

### Post by khelben1979 on 2009-01-02
You can skip tools.

---

### Post by thefirstman on 2009-01-02
i skipped tools and went on to utils and this is what i got...

root@box:/home/jdimaio/alsa/alsa-utils-1.0.18# make
Making all in include
make[1]: Entering directory `/home/jdimaio/alsa/alsa-utils-1.0.18/include'
make  all-am
make[2]: Entering directory `/home/jdimaio/alsa/alsa-utils-1.0.18/include'
make[2]: Leaving directory `/home/jdimaio/alsa/alsa-utils-1.0.18/include'
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-utils-1.0.18/include'
Making all in alsactl
make[1]: Entering directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl'
Making all in init
make[2]: Entering directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl/init'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl/init'
make[2]: Entering directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
	then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
	then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT utils.o -MD -MP -MF ".deps/utils.Tpo" -c -o utils.o utils.c; \
	then mv -f ".deps/utils.Tpo" ".deps/utils.Po"; else rm -f ".deps/utils.Tpo"; exit 1; fi
utils.c: In function ‘initfailed’:
utils.c:92: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:93: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:94: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:95: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT init_parse.o -MD -MP -MF ".deps/init_parse.Tpo" -c -o init_parse.o init_parse.c; \
	then mv -f ".deps/init_parse.Tpo" ".deps/init_parse.Po"; else rm -f ".deps/init_parse.Tpo"; exit 1; fi
init_parse.c: In function ‘parse_line’:
init_parse.c:1550: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
init_parse.c:1560: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
gcc  -g -O2   -o alsactl  alsactl.o state.o utils.o init_parse.o  -lasound -lm -ldl -lpthread
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl'
make: *** [all-recursive] Error 1
root@box:/home/jdimaio/alsa/alsa-utils-1.0.18# make install
Making install in include
make[1]: Entering directory `/home/jdimaio/alsa/alsa-utils-1.0.18/include'
make[2]: Entering directory `/home/jdimaio/alsa/alsa-utils-1.0.18/include'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jdimaio/alsa/alsa-utils-1.0.18/include'
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-utils-1.0.18/include'
Making install in alsactl
make[1]: Entering directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl'
Making install in init
make[2]: Entering directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl/init'
make[3]: Entering directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl/init'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: Leaving directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl/init'
make[2]: Leaving directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl/init'
make[2]: Entering directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl'
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/jdimaio/alsa/alsa-utils-1.0.18/alsactl'
make: *** [install-recursive] Error 1
root@box:/home/jdimaio/alsa/alsa-utils-1.0.18# 

ill go on to pyalsa and try that.

P.S. Like your new pic better.

---

### Post by thefirstman on 2009-01-02
seems like pyalsa is not working. can i skip that step?

---

### Post by khelben1979 on 2009-01-03
I think you can skip that one too.

After all of these packages are installed, don't forget to run that Ubuntu script afterwards.

For me, doing like this has always worked for me, so I'll hope you will be getting some sound over there soon.

I think that you need to run the [AlsaMixer]("http://en.wikipedia.org/wiki/Alsamixer") program to adjust the volume after this also. It is set to give no output on sound at default.

---

### Post by thefirstman on 2009-01-08
where exactly is the script. Am I to just copy the text into a text file and open terminal then...

exec <filename>

???

Sorry I just want to do things properly.


THANKS!

---

### Post by khelben1979 on 2009-01-08
In the first post in this thread you can see some attached files. Look [here]("http://ubuntuforums.org/showthread.php?t=962695").

Download the AlsaUpgrade script and run it with root priviligies and then use the sh command on the script after it is unpacked.

---

### Post by thefirstman on 2009-01-08
I am not positive that the script ran. My terminal window just closed. I then tried the alsamixer and this is what I got.

jdimaio@box:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
jdimaio@box:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
jdimaio@box:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
jdimaio@box:~$ 
jdimaio@box:~$

---

### Post by thefirstman on 2009-01-10
How can I tell if the script ran properly? Also how do I use the sh command on the script? Sorry if this is getting old...

---

### Post by khelben1979 on 2009-01-11
You type:

sh AlsaUpgrade-1.0.x-rev-1.15.sh (and don't forget to be in the correct file path)

Also, make sure to configure your soundcard/soundchip correctly with [alsaconf]("http://man-wiki.net/index.php/8:alsaconf").
type: alsaconf from a terminal somewhere.

---

### Post by thefirstman on 2009-01-11
Type it where? What path am I supposed to be in? I am confused.

---

### Post by thefirstman on 2009-01-11
I am confused. Where do I type it? What path am I supposed to be in?

---

### Post by thefirstman on 2009-01-11
> **khelben1979 said:**
> You type:

sh AlsaUpgrade-1.0.x-rev-1.15.sh (and don't forget to be in the correct file path)

Also, make sure to configure your soundcard/soundchip correctly with [alsaconf]("http://man-wiki.net/index.php/8:alsaconf").
type: alsaconf from a terminal somewhere.




Where do I type this? What path am I supposed to be in?

---

### Post by khelben1979 on 2009-01-12
You need to be in a shell enviroment. You can use Xterm or another program for this.

When the archive is extracted the file will be in the path where the file has been extracted.

You then need to execute this file, and since the file is a script you need to run it as a script and for that you use the sh command on the script in the path where you have extracted this file.

You can also try to locate this file in graphical mode and then just doubleclicking on the script, but in that case you need to have root permissions for this to work.

---

### Post by thefirstman on 2009-01-12
> **khelben1979 said:**
> You need to be in a shell enviroment. You can use Xterm or another program for this.

When the archive is extracted the file will be in the path where the file has been extracted.

You then need to execute this file, and since the file is a script you need to run it as a script and for that you use the sh command on the script in the path where you have extracted this file.

You can also try to locate this file in graphical mode and then just doubleclicking on the script, but in that case you need to have root permissions for this to work.

I tried the following in Xterm. Not sure if this is correct.

jdimaio@box:~$ su
Password: 
root@box:/home/jdimaio# sh /home/jdimaio/Desktop/alsa.sh
[: 99: Illegal number: 

Usage: /home/jdimaio/Desktop/alsa.sh [OPTION]...

Available options:
   -di    Download (to /usr/src), compile and install the packages
          This option will compeletely upgrade your ALSA in one step
   -d     Download the packages only
          In case you want to tweak/patch them before installation   
   -c     Compilation only 
          Kind of dry-run option to see if the configuration and compilation 
          works
   -i     Compilation and installation of packages
          Sources must exist under /usr/src. Run script with -d or -di options f
irst.
          The option is useful to speed up your installation in case Ubuntu upgr
ades 
          have overwritten your ALSA installation. It is also useful if you want
 to 
          keep your patched version or snapshot version, when reinstalling the p
ackages
   -r     Restore ALSA 
          Kernel and all ALSA relevant Ubuntu packages will be restored
          (done by re-installation of relevant packages)
   -snap  Install latest ALSA driver-sources-snapshot (from source tree)
          Script should've been run using -d option once before. 
          Recommended for troubleshooting.
          (The snapshot is not an offical ALSA release or even pre-release,
           it is a snapshot from the design-tree!) 
   -h     Help - this page 

Please visit [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695) 
to report any issues you might encounter by using this script.

root@box:/home/jdimaio#

---

### Post by khelben1979 on 2009-01-12
This is what you should type:

sh AlsaUpgrade-1.0.x-rev-1.15.sh -di

---

### Post by thefirstman on 2009-01-12
> **khelben1979 said:**
> This is what you should type:

sh AlsaUpgrade-1.0.x-rev-1.15.sh -di

Thanks for helping me. I am sorry if this is taking a lot of effort. I really appreciate your help. Anyway here is what I got...

jdimaio@box:~$ sh AlsaUpgrade-1.0.x-rev-1.15.sh -di
sh: Can't open AlsaUpgrade-1.0.x-rev-1.15.sh
jdimaio@box:~$ su
Password: 
root@box:/home/jdimaio# sh AlsaUpgrade-1.0.x-rev-1.15.sh -di
sh: Can't open AlsaUpgrade-1.0.x-rev-1.15.sh
root@box:/home/jdimaio#

---

### Post by khelben1979 on 2009-01-12
Okay. Make sure that the file is actually there by pressing the tab button two times in that text console.

Then you type chmod 777 on that script file to change it's file attributes. I think it might work.

From what I read earlier in your post you typed sh alsa.sh, and for me this feels a bit confusing, because the filename of that script should not have that name, but maybe you chose to name it alsa when you unpacked the file? In that case you should just type:

alsa.sh -di

---

### Post by thefirstman on 2009-01-12
Well I did name the script alsa.sh Sorry I named it incorrectly. I tried this...

root@box:/home/jdimaio# sh alsa.sh -di
sh: Can't open alsa.sh
root@box:/home/jdimaio# 


Should I rename the script? Right now the script is on my desktop. Is that ok? Sorry for making it hard to help but I am grateful.

---

### Post by khelben1979 on 2009-01-12
Show me what file attributes that the script has. I believe that something might have gone wrong here.

ls -l

or by choosing to take file attributes on it in graphical mode and giving me a screen dump on it.

---

### Post by thefirstman on 2009-01-12
> **khelben1979 said:**
> Show me what file attributes that the script has. I believe that something might have gone wrong here.

ls -l

or by choosing to take file attributes on it in graphical mode and giving me a screen dump on it.

jdimaio@box:~$ ls -l
total 52
drwxr-xr-x 9 jdimaio jdimaio  4096 2009-01-02 14:38 alsa
-rwxr-xr-x 1 jdimaio jdimaio 12048 2009-01-02 18:22 alsascript
-rw-r--r-- 1 jdimaio jdimaio     0 2009-01-02 18:22 alsascript~
drwxr-xr-x 5 jdimaio jdimaio  4096 2009-01-10 20:41 Desktop
drwxr-xr-x 3 jdimaio jdimaio  4096 2008-12-30 19:36 Documents
lrwxrwxrwx 1 jdimaio jdimaio    26 2008-12-22 22:12 Examples -> /usr/share/example-content
drwxr-xr-x 2 jdimaio jdimaio  4096 2008-12-22 22:22 Music
drwxr-xr-x 3 jdimaio jdimaio  4096 2008-12-31 17:08 Photos
drwxr-xr-x 2 jdimaio jdimaio  4096 2008-12-22 22:22 Pictures
drwxr-xr-x 2 jdimaio jdimaio  4096 2008-12-22 22:22 Public
drwxr-xr-x 2 jdimaio jdimaio  4096 2008-12-22 22:22 Templates
drwxr-xr-x 2 jdimaio jdimaio  4096 2008-12-22 22:22 Videos
drwxr-xr-x 3 jdimaio jdimaio  4096 2008-12-30 21:48 vuze
jdimaio@box:~$

---

### Post by khelben1979 on 2009-01-12
Take the attached file from this message and place it in your home catalog: /home/jdimaio/

Then do this again:
sh AlsaUpgrade-1.0.x-rev-1.15.sh -di (and without rename'ing this file this time)

Remember that you need root permissions. Also make sure that this script is in the same catalog as where you unpacked all the alsa packages from the Alsa base homepage.

Let me know how it goes.

---

### Post by thefirstman on 2009-01-12
root@box:/home/jdimaio# su
root@box:/home/jdimaio# sh AlsaUpgrade-1.10.x-rev-1.15.sh -di
sh: Can't open AlsaUpgrade-1.10.x-rev-1.15.sh
root@box:/home/jdimaio#

---

### Post by khelben1979 on 2009-01-12
chmod 777 on that attached file as root. Then try again.

---

### Post by thefirstman on 2009-01-12
> **khelben1979 said:**
> chmod 777 on that attached file as root. Then try again.

Not sure what I am supposed to be doing...

root@box:/home/jdimaio# chmod 777 sh AlsaUpgrade-1.10.x-rev-1.15.sh -di
chmod: invalid option -- 'd'
Try `chmod --help' for more information.
root@box:/home/jdimaio# chmod 777 sh AlsaUpgrade-1.10.x-rev-1.15.sh 
chmod: cannot access `sh': No such file or directory
chmod: cannot access `AlsaUpgrade-1.10.x-rev-1.15.sh': No such file or directory
root@box:/home/jdimaio# chmod 777 AlsaUpgrade-1.10.x-rev-1.15.sh 
chmod: cannot access `AlsaUpgrade-1.10.x-rev-1.15.sh': No such file or directory
root@box:/home/jdimaio# chmod 777 /home/jdimaio/AlsaUpgrade-1.10.x-rev-1.15.sh 
chmod: cannot access `/home/jdimaio/AlsaUpgrade-1.10.x-rev-1.15.sh': No such file or directory
root@box:/home/jdimaio#

---

### Post by khelben1979 on 2009-01-12
From what I can see: that script does not seem to be copied into /home/jdimaio/

You must first place the file in that path. Doing it graphically might be the easiest thing for you.

When you were here:
I tried the following in Xterm. Not sure if this is correct.

jdimaio@box:~$ su
Password:
root@box:/home/jdimaio# sh /home/jdimaio/Desktop/alsa.sh
[: 99: Illegal number:

Usage: /home/jdimaio/Desktop/alsa.sh [OPTION]...

You were almost there. The only thing you needed was to include that parameter which we have discussed in this thread. The -di parameter.

---

### Post by thefirstman on 2009-01-12
The script is in the correct path. (/home/jdimaio/)
What am I suppose to do?

---

### Post by khelben1979 on 2009-01-12
At the present: I don't know.

What you can do is to run the alsaconf program to see if it detects your soundcard/soundchip and then choose the correct one. 

Boot the machine and adjust the volume with Alsamixer and see if anything has changed.

---

### Post by thefirstman on 2009-01-12
> **khelben1979 said:**
> At the present: I don't know.

What you can do is to run the alsaconf program to see if it detects your soundcard/soundchip and then choose the correct one. 

Boot the machine and adjust the volume with Alsamixer and see if anything has changed.

jdimaio@box:~$ alsaconf
bash: alsaconf: command not found

---

### Post by MrFocus on 2009-01-12
i, I'm having the same problem
AlsaMixer works but still have no sound
I have a nVidia Sound card on an IBM Z61m
When I op nVidia X Server Settings I get this messange:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
I am really starting from scratch with Linux and Kubuntu.
thnx in advance

---

