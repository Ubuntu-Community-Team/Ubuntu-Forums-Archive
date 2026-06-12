---
title: "Need help with Bluetooth headset and Skype on Hardy"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Horomancer on 2009-08-19
Hi. I just got a bluetooth headset and dongle to make using Skype easier and it is not going well. Currently I can get my headset to pair with Ubuntu, have Skype recognize my headset, play sound from skype through my headset.
I can not use my headset to record sound
Skype breaks after I make a test call with my headset, it will not close down pick up incoming calls, make new calls or test sounds. You can still open and close windows, and play with the options and settings however so it can't be said to freeze up.
I am trying to compile the latest Bluez files, but am having not luck.

```
jackmo@Time Control:~/bluez-4.48$ ./configure --prefix=/usr --mandir=/usr/share/man \
> 
acinclude.m4   config.guess   cups/          ltmain.sh      sbc/
aclocal.m4     config.h       depcomp        Makefile       scripts/
audio/         config.h.in    doc/           Makefile.am    serial/
AUTHORS        config.log     gdbus/         Makefile.in    src/
bluez.pc       config.status  include/       missing        stamp-h1
bluez.pc.in    config.sub     input/         network/       test/
ChangeLog      configure      INSTALL        NEWS           tools/
client/        configure.ac   install-sh     plugins/       ylwrap
common/        COPYING        lib/           README         
compat/        COPYING.LIB    libtool        rfcomm/        
> --sysconfdir=/etc --localstatedir=/var --libexecdir=/lib
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
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
checking whether gcc accepts -fPIE... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for bison... bison -y
checking for flex... flex
checking lex output file root... lex.yy
checking lex library... -lfl
checking whether yytext is a pointer... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 98304
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether to build gtk-doc documentation... no
checking for gtkdoc-check... /usr/bin/gtkdoc-check
checking for ppoll... yes
checking for dlopen in -ldl... yes
checking for DBUS... yes
checking for dbus_watch_get_unix_fd in -ldbus-1... yes
checking for GLIB... yes
checking for ALSA... yes
checking for clock_gettime in -lrt... yes
checking for GSTREAMER... yes
checking for USB... yes
checking for usb_get_busses in -lusb... yes
checking for usb_interrupt_read in -lusb... yes
checking for NETLINK... yes
checking for SNDFILE... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating lib/Makefile
config.status: creating gdbus/Makefile
config.status: creating common/Makefile
config.status: creating sbc/Makefile
config.status: creating src/Makefile
config.status: creating test/Makefile
config.status: creating cups/Makefile
config.status: creating tools/Makefile
config.status: creating client/Makefile
config.status: creating rfcomm/Makefile
config.status: creating compat/Makefile
config.status: creating plugins/Makefile
config.status: creating network/Makefile
config.status: creating serial/Makefile
config.status: creating input/Makefile
config.status: creating audio/Makefile
config.status: creating scripts/Makefile
config.status: creating scripts/bluetooth.rules
config.status: creating doc/Makefile
config.status: creating doc/version.xml
config.status: creating src/bluetoothd.8
config.status: creating src/hcid.conf.5
config.status: creating bluez.pc
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

jackmo@Time Control:~/bluez-4.48$ make && make install
make --no-print-directory all-recursive
Making all in include
Making all in lib
make[2]: Nothing to be done for `all'.
Making all in sbc
make[2]: Nothing to be done for `all'.
Making all in gdbus
make[2]: Nothing to be done for `all'.
Making all in common
make[2]: Nothing to be done for `all'.
Making all in plugins
make[2]: Nothing to be done for `all'.
Making all in network
make[2]: Nothing to be done for `all'.
Making all in serial
make[2]: Nothing to be done for `all'.
Making all in input
make[2]: Nothing to be done for `all'.
Making all in audio
make  all-am
make[3]: Nothing to be done for `all-am'.
Making all in src
make  all-am
make[3]: Nothing to be done for `all-am'.
Making all in client
make[2]: Nothing to be done for `all'.
Making all in tools
make[2]: Nothing to be done for `all'.
Making all in rfcomm
make  all-am
make[3]: Nothing to be done for `all-am'.
Making all in compat
make[2]: Nothing to be done for `all'.
Making all in cups
make[2]: Nothing to be done for `all'.
Making all in test
make[2]: Nothing to be done for `all'.
Making all in scripts
cp bluetooth.rules 97-bluetooth.rules
Making all in doc
make[2]: Nothing to be done for `all'.
Making install in include
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/include/bluetooth" || /bin/mkdir -p "/usr/include/bluetooth"
 /usr/bin/install -c -m 644 bluetooth.h hci.h hci_lib.h sco.h l2cap.h sdp.h sdp_lib.h rfcomm.h bnep.h cmtp.h hidp.h '/usr/include/bluetooth'
/usr/bin/install: cannot remove `/usr/include/bluetooth/bluetooth.h': Permission denied
/usr/bin/install: cannot remove `/usr/include/bluetooth/hci.h': Permission denied
/usr/bin/install: cannot remove `/usr/include/bluetooth/hci_lib.h': Permission denied
/usr/bin/install: cannot remove `/usr/include/bluetooth/sco.h': Permission denied
/usr/bin/install: cannot remove `/usr/include/bluetooth/l2cap.h': Permission denied
/usr/bin/install: cannot remove `/usr/include/bluetooth/sdp.h': Permission denied
/usr/bin/install: cannot remove `/usr/include/bluetooth/sdp_lib.h': Permission denied
/usr/bin/install: cannot remove `/usr/include/bluetooth/rfcomm.h': Permission denied
/usr/bin/install: cannot remove `/usr/include/bluetooth/bnep.h': Permission denied
/usr/bin/install: cannot remove `/usr/include/bluetooth/cmtp.h': Permission denied
/usr/bin/install: cannot remove `/usr/include/bluetooth/hidp.h': Permission denied
make[2]: *** [install-includeHEADERS] Error 1
make[1]: *** [install-am] Error 2
make: *** [install-recursive] Error 1
jackmo@Time Control:~/bluez-4.48$ 

```
I have also made a .asoundrc file for my headset-

```
pcm.bluetoothraw {
   type bluetooth
   device 00:07:B0:11:81:24
}
pcm.bluetooth {
    type plug
    slave {
        pcm bluetoothraw
    }
}

```

The format based of the Skype workaround listed in the Bluez wiki
I'm pretty much lost now on what to do. Does anyone have any ideas?

---

### Post by rajeev1204 on 2009-08-20
bump.

---

### Post by Horomancer on 2009-08-20
Really?
No one?
Why does this have to be so difficult? Why is this not simply plug an play?

---

### Post by Horomancer on 2009-08-21
bump

---

### Post by Arla on 2009-08-21
Unfortunately bluetooth doesn't seem to be "there" in Ubuntu yet, I had massive problems getting mine to work in 9.04 (so massive that I gave up), I'm trying again in 9.10 since I gather bluetooth is much improved, but haven't yet really played with it, still waiting on my brother in the UK to have time to play with Ekiga to see if I can switch to that rather than keep using Skype.

---

### Post by Horomancer on 2009-08-24
Well that breaks my heart. I'm looking at getting an eeePC soon. Is the problem with getting bluetooth to work a linux thing or an Ubuntu thing? i would have to get the ebuntu distro up only to hit the same wall.
Un related topic- why would you want to use Ekiga rather than skype? I've never delt with Ekiga though i see it comes default in Ubuntu.

---

### Post by Arla on 2009-08-24
Ekiga is open-source, Skype, not so much.

Also Skype for Linux seems to be an "after-throught" to say the least, I'd rather use software that is actually intented to be used, or not at all.

---

### Post by Horomancer on 2009-08-26
I can understand that. Does Ekiga do somethign simular to Skype where you can have a regular phone number and a flat annual rate? I looked a little at it and all I saw was a per minute pay scheme.

---

