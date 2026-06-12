---
title: "pidgin problems!!"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by ninjaprawn on 2007-08-27
i was having problems with gaim, so i followed a very helpful howto on here to upgrade to pidgin! that went very well! thanx!

im still having the same problem tho!

ive googled a bit, and not come up with any working answers!

the problem is that i cant talk to msn contacts!!!!

other protocols work fine. what happens is that sometimes i dont connect to msn, so i retry, and it works. then i see whos online, open a conversation, and type something. then hit send. then a few seconds later, i get -> 'Message could not be sent because a connection error occured:
hi!'

any ideas??

---

### Post by janbockaert on 2007-08-27
same problem, i can see my contacts, but when i send a message, i get an error back.

---

### Post by ninjaprawn on 2007-08-27
this is the debug window for the same problem!

(21:43:51) util: Writing file prefs.xml to directory /home/danny/.purple
(21:43:52) msn: new httpconn (0x87fff20)
(21:43:52) msn: C: NS 000: XFR 12 SB
(21:43:52) msn: Appending message to queue.
(21:43:53) msn: S: NS 000: XFR 12 SB 207.46.26.38:1863 CKI 540030630.195231203.195164228
(21:43:53) dns: DNS query for 'gateway.messenger.hotmail.com' queued
(21:43:53) msn: C: SB 004: USR 1 [email]ninjaprawn@blueyonder.co.uk[/email] 540030630.195231203.195164228
(21:43:53) dns: Created new DNS child 26439, there are now 1 children.
(21:43:53) dns: Successfully sent DNS request to child 26439
(21:43:53) dns: Got response for 'gateway.messenger.hotmail.com'
(21:43:53) dnsquery: IP resolved for gateway.messenger.hotmail.com
(21:43:53) proxy: Attempting connection to 65.54.239.211
(21:43:53) proxy: Connecting to gateway.messenger.hotmail.com:80 with no proxy
(21:43:53) proxy: Connection in progress
(21:43:53) proxy: Connected to gateway.messenger.hotmail.com:80.
(21:43:55) msn: Connection error from Switchboard server (207.46.26.38): Reading error
(21:43:55) msn: Switchboard with unassigned conversation
(21:43:55) msn: destroy httpconn (0x87fff20)

ive turned of my firewall, tried a proxy, tried without http method, cant get it to get past the switchboard?!?

ive seen loads of bugs with similiar problems on the pidgin page, but most have bin closed. wonderin if anyone has a solution??

---

### Post by kevdog on 2007-08-27
Ive posted on this problem with msn messenger.  I currently do not connect with Http, but am finding the ability to get connected very intermittent.  Today it is working, yesterday it was not.

---

### Post by ninjaprawn on 2007-08-28
is it a problem with pidgin using an old version of msn or is it the msn servers themselves?? or is it something else?

---

### Post by rui_acp on 2007-08-28
Same problem. I can connect with HTTP, but i get the switchboard error when I send an IM to a contact. Without HTTP i get an error from the notification server.
It is working with Google Talk and ICQ, but not with msn. Are they trying again to block 3rd party clients? Meebo works, but I don't like to use web based IM/chat clients.

---

### Post by kevdog on 2007-08-28
No one knows the exact cause of the problem.  People have speculated that msn has changed something with the login process and changes have not been made into libpurple.  A bug has been filed at the pidgin site but I havent seen anyone actually diagnose the real reason why it doesnt work.

---

### Post by MrGrey1 on 2007-08-31
I have the same problem with Pidgin not sending messages for msn. Both the xp & ubuntu versions of Pidgin have the same problem. XP messenger works fine. Very irritating as I hate the adds on M$uX msn.

---

### Post by ninjaprawn on 2007-10-12
ive resorted to using meebo!!!!

not ideal, but atleast it works, unlike pidgin!

does anyone know a way around the never ending bug??

---

### Post by kevdog on 2007-10-12
I compiled the latest version from source -- no more problems with msn.

---

### Post by ninjaprawn on 2007-10-12
im lost when it comes to compiling from source!
i know i need to /.configure then make then make install. but blah!
ive read loads of tutorials, and cant get my head round it at all! 

tell me if this sounds right, ive downloaded and extracted the pidgin source to a folder called downloads on my desktop.

im assuming that all i do is in a terminal, cd to that folder, 
then /.configure
make
make install

and hey presto, compiled from source?!?!?!

where does it get installed to? or should i put it in a different folder first? do i need to uninstall the old pidgin?

id much appreciate it if u could help with this, shud be ok for future as well then!

thanks.

---

### Post by kevdog on 2007-10-12
Well you kind of have it.

The general rule of 
./configure --prefix=/usr
make
sudo make install

This will install it to the the /usr directory so it will accessible in your path.

Pidgin however requires a bunch of dependencies.  It took me a long time to get all of the dependencies
I dont know all of them because it was trial and error.

Run this statment before the configure statement above:
sudo apt-get install libgtk2.0-dev libxml2-dev gettext libnss-dev libnspr-dev libgtkspell-dev libnss-dev libnspr-dev build-essential libglib2.0-dev


Then try to run configure, etc

---

### Post by ninjaprawn on 2007-10-12
thanks,

i googled it, and came up with this [http://neoaddict.wordpress.com/2007/10/01/compile-pidgin-221-from-source-in-ubuntu/]("http://neoaddict.wordpress.com/2007/10/01/compile-pidgin-221-from-source-in-ubuntu/")
im just at the make stage now! its got all the dependencies listed there, except 1! i had to do sudo apt-get install gettext as well!

this will be the 1st thing ive compiled succesfully if it works! ive tried a few things b4, and wen they failed for wot ever reason, i spent a short time trying to fix em, but gave up! since about june, if i ever needed to compile, i would just do with out!

fingers crossed, i can get away from meebo after this!

thanks.

---

### Post by kevdog on 2007-10-12
Tutorial looks good, there are often many ways to skin a cat!!!  If you want to do checkinstall you can, if not sudo make install will also work.
Let me know how you make out.

---

### Post by ninjaprawn on 2007-10-12
it went ok! its all working now, including msn!!!! there was 1 dependency missing for me, 'gettext' but i just installed that and then it went all smoothly till i got to the check install bit! i copy and pasted the line from the tutorial, and it gave me an error, so i ran sudo checkinstall instead, it went the whole way thru till it was installing the deb packages, then came up with an error! so i went back to the line 'sudo checkinstall –exclude=/etc/gconf,/usr/bin,/usr/lib' but typed it myself, and it was all groovy!!!!!!!!!!!!!!!!!!!!!!

thanks for that, thats the 1st time ive compiled something succesfully! ta!

is there any cleaning up i need to do? or is it all done automaticaly?

thanks again!

---

### Post by kevdog on 2007-10-12
Its all done -- 

can you post the list of dependencies you installed here, and can you also run the
./configure statement again, and also post the summary (The one where is states, yes, no , no, yes).

I think I can add some of this info to a tutorial, but I need your help.

---

### Post by ninjaprawn on 2007-10-12
i just did the following,

1) Get the source from the pidgin home page

2) Unpack the archive with Archive Manager or equivalent.

3) Cd (change directory) into the extracted directory. Run the following command in Terminal, but replace the_directory with the directory name.

    cd the_directory

4) Type in this command into Terminal to remove previous versions pf Pidgin (will not remove your personal info):

    sudo apt-get remove –purge pidgin
or completly remove with
    sudo apt-get remove pidgin
    sudo apt-get autoremove

5) Now, we need to install the dependencies to allow us to compile:

    sudo apt-get install libxml2-dev checkinstall libgnutls-dev libgtk2.0-dev libglib2.0-dev
and
    sudo apt-get install gettext

6) Wait for the packages to install, then run this command in Terminal:

    ./configure –prefix=/usr/local –enable-gnutls=yes

7) After that is done, run this in Terminal:

    sudo make

8) When that is finally done (10 - 20 minutes later), run this in Terminal:

    sudo checkinstall –exclude=/etc/gconf,/usr/bin,/usr/lib

that was that, my ./configure log was

```
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  af am ar az be@latin bg bn bs ca ca@valencia cs da de dz el en_AU en_CA en_GB eo es et eu fa fi fr gl gu he hi hu id it ja ka kn ko ku lo lt mk my_MM nb ne nl nn pa pl pt_BR pt ps ro ru sk sl sq sr sr@latin sv ta te th tr uk vi xh zh_CN zh_HK zh_TW
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking arpa/nameser_compat.h usability... yes
checking arpa/nameser_compat.h presence... yes
checking for arpa/nameser_compat.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for locale.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for stdint.h... (cached) yes
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking for an ANSI C-conforming const... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for time_t... yes
checking size of time_t... 4
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
checking for strftime... yes
checking for strdup... yes
checking for strstr... yes
checking for atexit... yes
checking for setlocale... yes
checking for getopt_long... yes
checking for inet_aton... yes
checking for __res_query in -lresolv... yes
checking for gethostent in -lnsl... yes
checking for socket... yes
checking for getaddrinfo... yes
checking for socklen_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for the %z format string in strftime()... yes
checking for GLIB... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for GTK... yes
checking for pango... yes
checking for X11... yes
checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... no
checking for SmcSaveYourselfDone in -lSM... yes
checking X11/SM/SMlib.h usability... yes
checking X11/SM/SMlib.h presence... yes
checking for X11/SM/SMlib.h... yes
checking for STARTUP_NOTIFICATION... no
no
checking for GTKSPELL... no
no
checking for EVOLUTION_ADDRESSBOOK... no
yes
checking for EVOLUTION_ADDRESSBOOK... no
yes
checking for SQLITE3... no
no
checking for initscr in -lncursesw... no
checking for update_panels in -lpanelw... no
checking for initscr in -lncurses... no
checking for update_panels in -lpanel... no
checking for LIBXML... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for GSTREAMER... no
no
checking for MEANWHILE... no
no
checking for AVAHI... no
no
checking avahi-client/client.h usability... no
checking avahi-client/client.h presence... no
checking for avahi-client/client.h... no
checking avahi-glib/glib-malloc.h usability... no
checking avahi-glib/glib-malloc.h presence... no
checking for avahi-glib/glib-malloc.h... no
checking for avahi_client_new in -lavahi-client... no
checking for HOWL... no
no
checking for HOWL... no
no
checking howl.h usability... no
checking howl.h presence... no
checking for howl.h... no
checking for sw_discovery_init in -lhowl... no
checking for SILC... no
no
checking for SILC... no
no
checking for SILC... no
no
checking for GADU... no
no
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking for uname... yes
checking for -Waggregate-return option to gcc... yes
checking for -Wcast-align option to gcc... yes
checking for -Wdeclaration-after-statement option to gcc... yes
checking for -Wendif-labels option to gcc... yes
checking for -Werror-implicit-function-declaration option to gcc... yes
checking for -Wextra -Wno-sign-compare -Wno-unused-parameter option to gcc... yes
checking for -Winit-self option to gcc... yes
checking for -Wmissing-declarations option to gcc... yes
checking for -Wmissing-noreturn option to gcc... yes
checking for -Wmissing-prototypes option to gcc... yes
checking for -Wnested-externs option to gcc... yes
checking for -Wpointer-arith option to gcc... yes
checking for -Wundef option to gcc... yes
checking for FORTIFY_SOURCE support... yes
checking for pidgin... /usr/local/bin/pidgin
checking for dbus-binding-tool... yes
checking for DBUS... no
no
Building without D-Bus support
checking for perl... /usr/bin/perl
checking for Perl compile flags... ok
checking for libperl... checking for perl_run... no
checking EXTERN.h usability... yes
checking EXTERN.h presence... yes
checking for EXTERN.h... yes
checking for perl.h... yes
checking for GnuTLS includes... ""
checking gnutls/gnutls.h usability... yes
checking gnutls/gnutls.h presence... yes
checking for gnutls/gnutls.h... yes
checking for GnuTLS libraries... yes
checking for Mozilla nspr4 includes in ... ""
checking nspr.h usability... no
checking nspr.h presence... no
checking for nspr.h... no
checking prio.h usability... no
checking prio.h presence... no
checking for prio.h... no
checking for Mozilla nspr4 libraries... no
checking for Mozilla nss3 includes... no
checking for Mozilla nss libraries... no
checking for tclConfig.sh... no
checking for snprintf... yes
checking for connect... (cached) yes
checking for me pot o' gold... no
checking for gethostid... yes
checking for lrand48... yes
checking for memcpy... yes
checking for memmove... yes
checking for random... yes
checking for strchr... yes
checking for strerror... yes
checking for vprintf... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking sgtty.h usability... yes
checking sgtty.h presence... yes
checking for sgtty.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking sys/cdefs.h usability... yes
checking sys/cdefs.h presence... yes
checking for sys/cdefs.h... yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/msgbuf.h usability... no
checking sys/msgbuf.h presence... no
checking for sys/msgbuf.h... no
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking for sys/utsname.h... (cached) yes
checking for sys/wait.h... (cached) yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking sys/sysctl.h usability... yes
checking sys/sysctl.h presence... yes
checking for sys/sysctl.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking for struct tm.tm_zone... yes
checking for timezone external... yes
checking for altzone external... no
checking for daylight external... yes
checking for tm_gmtoff in struct tm... yes
checking for CHECK... no
checking for check - version >= 0.8.2... no
*** Could not run check test program, checking why...
*** The test program failed to compile or link. See the file config.log for
*** the exact error that occured.
checking for doxygen... false
configure: WARNING: *** Doxygen not found, docs will not be available
configure: creating ./config.status
config.status: creating Makefile
config.status: creating Doxyfile
config.status: creating doc/Makefile
config.status: creating doc/pidgin.1
config.status: creating doc/finch.1
config.status: creating m4macros/Makefile
config.status: creating pidgin.apspec
config.status: creating pidgin/Makefile
config.status: creating pidgin/pidgin.pc
config.status: WARNING:  pidgin/pidgin.pc.in seems to ignore the --datarootdir setting
config.status: creating pidgin/pidgin-uninstalled.pc
config.status: WARNING:  pidgin/pidgin-uninstalled.pc.in seems to ignore the --datarootdir setting
config.status: creating pidgin/pixmaps/Makefile
config.status: creating pidgin/pixmaps/animations/Makefile
config.status: creating pidgin/pixmaps/animations/16/Makefile
config.status: creating pidgin/pixmaps/buddy_icons/Makefile
config.status: creating pidgin/pixmaps/buddy_icons/qq/Makefile
config.status: creating pidgin/pixmaps/dialogs/Makefile
config.status: creating pidgin/pixmaps/dialogs/16/Makefile
config.status: creating pidgin/pixmaps/dialogs/16/scalable/Makefile
config.status: creating pidgin/pixmaps/dialogs/64/Makefile
config.status: creating pidgin/pixmaps/dialogs/64/scalable/Makefile
config.status: creating pidgin/pixmaps/emblems/Makefile
config.status: creating pidgin/pixmaps/emblems/16/Makefile
config.status: creating pidgin/pixmaps/emblems/16/scalable/Makefile
config.status: creating pidgin/pixmaps/emotes/Makefile
config.status: creating pidgin/pixmaps/emotes/default/Makefile
config.status: creating pidgin/pixmaps/emotes/default/24/Makefile
config.status: creating pidgin/pixmaps/emotes/default/24/scalable/Makefile
config.status: creating pidgin/pixmaps/emotes/none/Makefile
config.status: creating pidgin/pixmaps/icons/Makefile
config.status: creating pidgin/pixmaps/icons/16/Makefile
config.status: creating pidgin/pixmaps/icons/16/scalable/Makefile
config.status: creating pidgin/pixmaps/icons/22/Makefile
config.status: creating pidgin/pixmaps/icons/22/scalable/Makefile
config.status: creating pidgin/pixmaps/icons/24/Makefile
config.status: creating pidgin/pixmaps/icons/24/scalable/Makefile
config.status: creating pidgin/pixmaps/icons/32/Makefile
config.status: creating pidgin/pixmaps/icons/32/scalable/Makefile
config.status: creating pidgin/pixmaps/icons/48/Makefile
config.status: creating pidgin/pixmaps/icons/48/scalable/Makefile
config.status: creating pidgin/pixmaps/protocols/Makefile
config.status: creating pidgin/pixmaps/protocols/16/Makefile
config.status: creating pidgin/pixmaps/protocols/16/scalable/Makefile
config.status: creating pidgin/pixmaps/protocols/22/Makefile
config.status: creating pidgin/pixmaps/protocols/22/scalable/Makefile
config.status: creating pidgin/pixmaps/protocols/48/Makefile
config.status: creating pidgin/pixmaps/protocols/48/scalable/Makefile
config.status: creating pidgin/pixmaps/status/Makefile
config.status: creating pidgin/pixmaps/status/11/Makefile
config.status: creating pidgin/pixmaps/status/11/scalable/Makefile
config.status: creating pidgin/pixmaps/status/11/rtl/Makefile
config.status: creating pidgin/pixmaps/status/16/Makefile
config.status: creating pidgin/pixmaps/status/16/rtl/Makefile
config.status: creating pidgin/pixmaps/status/16/scalable/Makefile
config.status: creating pidgin/pixmaps/status/22/Makefile
config.status: creating pidgin/pixmaps/status/22/rtl/Makefile
config.status: creating pidgin/pixmaps/status/22/scalable/Makefile
config.status: creating pidgin/pixmaps/status/32/Makefile
config.status: creating pidgin/pixmaps/status/32/rtl/Makefile
config.status: creating pidgin/pixmaps/status/32/scalable/Makefile
config.status: creating pidgin/pixmaps/status/48/Makefile
config.status: creating pidgin/pixmaps/status/48/rtl/Makefile
config.status: creating pidgin/pixmaps/toolbar/Makefile
config.status: creating pidgin/pixmaps/toolbar/16/Makefile
config.status: creating pidgin/pixmaps/toolbar/16/scalable/Makefile
config.status: creating pidgin/pixmaps/toolbar/22/Makefile
config.status: creating pidgin/pixmaps/toolbar/22/scalable/Makefile
config.status: creating pidgin/pixmaps/tray/Makefile
config.status: creating pidgin/pixmaps/tray/16/Makefile
config.status: creating pidgin/pixmaps/tray/16/scalable/Makefile
config.status: creating pidgin/pixmaps/tray/22/Makefile
config.status: creating pidgin/pixmaps/tray/22/scalable/Makefile
config.status: creating pidgin/pixmaps/tray/32/Makefile
config.status: creating pidgin/pixmaps/tray/48/Makefile
config.status: creating pidgin/plugins/Makefile
config.status: creating pidgin/plugins/cap/Makefile
config.status: creating pidgin/plugins/gestures/Makefile
config.status: creating pidgin/plugins/gevolution/Makefile
config.status: creating pidgin/plugins/musicmessaging/Makefile
config.status: creating pidgin/plugins/perl/Makefile
config.status: creating pidgin/plugins/perl/common/Makefile.PL
config.status: creating pidgin/plugins/ticker/Makefile
config.status: creating libpurple/example/Makefile
config.status: creating libpurple/gconf/Makefile
config.status: creating libpurple/purple.pc
config.status: WARNING:  libpurple/purple.pc.in seems to ignore the --datarootdir setting
config.status: creating libpurple/purple-uninstalled.pc
config.status: WARNING:  libpurple/purple-uninstalled.pc.in seems to ignore the --datarootdir setting
config.status: creating libpurple/plugins/Makefile
config.status: creating libpurple/plugins/mono/Makefile
config.status: creating libpurple/plugins/mono/api/Makefile
config.status: creating libpurple/plugins/mono/loader/Makefile
config.status: creating libpurple/plugins/perl/Makefile
config.status: creating libpurple/plugins/perl/common/Makefile.PL
config.status: creating libpurple/plugins/ssl/Makefile
config.status: creating libpurple/plugins/tcl/Makefile
config.status: creating libpurple/Makefile
config.status: creating libpurple/protocols/Makefile
config.status: creating libpurple/protocols/bonjour/Makefile
config.status: creating libpurple/protocols/gg/Makefile
config.status: creating libpurple/protocols/irc/Makefile
config.status: creating libpurple/protocols/jabber/Makefile
config.status: creating libpurple/protocols/msn/Makefile
config.status: creating libpurple/protocols/myspace/Makefile
config.status: creating libpurple/protocols/novell/Makefile
config.status: creating libpurple/protocols/null/Makefile
config.status: creating libpurple/protocols/oscar/Makefile
config.status: creating libpurple/protocols/qq/Makefile
config.status: creating libpurple/protocols/sametime/Makefile
config.status: creating libpurple/protocols/silc/Makefile
config.status: creating libpurple/protocols/silc10/Makefile
config.status: creating libpurple/protocols/simple/Makefile
config.status: creating libpurple/protocols/toc/Makefile
config.status: creating libpurple/protocols/yahoo/Makefile
config.status: creating libpurple/protocols/zephyr/Makefile
config.status: creating libpurple/tests/Makefile
config.status: creating libpurple/version.h
config.status: creating share/Makefile
config.status: creating share/sounds/Makefile
config.status: creating share/ca-certs/Makefile
config.status: creating finch/Makefile
config.status: creating finch/libgnt/Makefile
config.status: creating finch/libgnt/gnt.pc
config.status: creating finch/libgnt/wms/Makefile
config.status: creating finch/plugins/Makefile
config.status: creating po/Makefile.in
config.status: creating pidgin.spec
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

pidgin 2.2.1

Build GTK+ 2.x UI............. : yes
Build console UI.............. : no
Build for X11................. : yes

Enable Gestures............... : yes
Protocols to build dynamically : gg irc jabber msn myspace novell oscar qq simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : no
Build with D-Bus support...... : no
Build with NetworkManager..... : no
SSL Library/Libraries......... : GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Has you....................... : yes

Use XScreenSaver Extension.... : no
Use X Session Management...... : yes
Use startup notification...... : no
Build with GtkSpell support... : no

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : no
Build with Tcl support........ : no
Build with Tk support......... : no

Print debugging messages...... : no

Pidgin will be installed in /usr/local/bin.
Warning: You have an old copy of Pidgin at /usr/local/bin/pidgin.

configure complete, now type 'make'

```

sorry, the begining got lost, terminal ran out of room!

thats everything! do i need to do anything to clean out the ./configure i just did?

---

### Post by kevdog on 2007-10-12
Configure just checks for dependencies and then produces make files.  To clean out the object files you can run

sudo make distclean

Just a learning point for you:

See all the options with the yes, no, no, yes, at the end of the configure statement -- you can compile pidgin with some extra libraries if you want to enable some of these options.

The line you used 
./configure –prefix=/usr/local –enable-gnutls=yes

Told the compiler to make pidgin with tls support.  Notice that you had installed the libgnutls-dev package prior to issuing this statement, so that you had the required dependency to support this statement.
Everything was successful as you can see in the summary:
SSL Library/Libraries......... : GnuTLS

Ive basically been able to compile my version with pidgin, with every single option changed to yes, however I installed so many libraries, Im not sure which ones I needed and which ones I didnt.  I at least have an idea of the basic packages needed to do a basic install such as yours.

Note some packages by default attempt to be included, some try to be excluded.  You can find which ones are included/excluded by ./configure --help

Just as an example - gtkspell support is included by default if the library is included.  You can install this library:
sudo apt-get install libgtkspell-dev

And then rerun ./configure again and see that in the summary support for gtkspell is included.  Of course to make use of this feature you would have to compile (make) and then install the package.

Just an FYI

---

### Post by ninjaprawn on 2007-10-12
cheers for that explanation. ive wanted to understand and learn to compile for ages! i still wouldnt no what option and bits to use for anything else i compile from source in future tho! atleast i understand what im looking at now anyway! the '-prefix=/usr/local' will be useful, ill always use that! it puts the program wer it shud be!

1 year using linux, and finaly managed to compile something! yay!

hopefully anther year and ill be able to understand it all enuf to modify programs and compile without a tutorial!

thanks again!

---

### Post by kevdog on 2007-10-12
All programs that you compile and install by default are put in the /usr/local directory.  Just make a note that these days many of the preinstalled programs are installed in /usr rather than /usr/local.  Because of this you could potentially have two copies of a program installed in both /usr and /usr/local.  Either make note of this and remember, or when compiling in the future just install everything into /usr with --prefix=/usr   If you supply no --prefix statement, the installation will go into /usr/local by default.

---

### Post by ninjaprawn on 2007-10-13
ive just had a quick look at ur plugins tutorial!

im going to have a go at it 2morow probably! if not then sunday!

cheers for all this advice!

---

### Post by Flanamana on 2008-06-28
When my buddy is typing pidgin isn't diplaying the "buddy is talking" thing in the corner of the window... it's only with this 1 buddy, with everyone else it works. Can someone help me?

---

