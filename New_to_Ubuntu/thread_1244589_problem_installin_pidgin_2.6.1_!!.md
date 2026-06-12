---
title: "problem installin pidgin 2.6.1 !!"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by MBG1987 on 2009-08-19
the version of pidgin is released ), I removed the last version and downloaded the new version 2.6.1 as binary files, and i run the usually command for such a files. 
when i typed ./configure command this error message appeared:
> mbg@MBG:~/Desktop/pidgin-2.6.1$ ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
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
checking whether gcc and cc understand -c and -o together... yes
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
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
checking for a BSD-compatible install... /usr/bin/install -c
checking whether NLS is requested... yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.0
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for working alloca.h... yes
checking for alloca... yes
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
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  af am ar az be@latin bg bn bs ca ca@valencia cs da de dz el en_AU en_CA en_GB eo es et eu fa fi fr ga gl gu he hi hu hy id it ja ka km kn ko ku lo lt mk mn my_MM nb ne nl nn oc pa pl pt_BR pt ps ro ru si sk sl sq sr sr@latin sv sw ta te th tr uk ur vi xh zh_CN zh_HK zh_TW
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
checking for inet_ntop... yes
checking for socklen_t... yes
checking for struct sockaddr.sa_len... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for dlopen... no
checking for dlopen in -ldl... yes
checking for fileno()... yes
checking for the %z format string in strftime()... yes
checking for GLIB... yes
checking for X... no
checking for GTK... no
no
configure: error:

You must have GTK+ 2.4.0 or newer development headers installed to compile
Pidgin.  If you want to build only Finch then specify --disable-gtkui when
running configure.

so what's i have to do now ? tnx

---

### Post by jmszr on 2009-08-19
MBG1987.

Unless your're running 8.10, install from here: [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin) .

---

### Post by mcduck on 2009-08-19
You don't haven't installed all the development libraries required for compiling Pidgin.

Anyway, I recommend that you forget about compiling it yourself, and instead just download the .deb packages from getdeb.net: [http://www.getdeb.net/release/4697]("http://www.getdeb.net/release/4697")

---

### Post by markitoxs on 2009-08-19
> **mcduck said:**
> You don't haven't installed all the development libraries required for compiling Pidgin.

Anyway, I recommend that you forget about compiling it yourself, and instead just download the .deb packages from getdeb.net: [http://www.getdeb.net/release/4697]("http://www.getdeb.net/release/4697")


Probably he is trying to compile because the /deb comes without the video support.

---

### Post by korin43 on 2009-08-19
EDIT: Pidgin 2.6.1 is in the [Pidgin Developers PPA](Pidgin Developers PPA), so you can install it from there. All you need to do this add this PPA: [https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa). The instructions are on that page.

Once it's added to your sources.list, just do:
```
sudo aptitude update
sudo aptitude upgrade
```

If you had [my PPA](https://launchpad.net/~korin43/+archive/ppa) (korin43) set up, remove it and the [Nicolas DERIVE PPA](https://launchpad.net/~kalon33/+archive/ppa) (kalon33), and do:
```
sudo aptitude remove pidgin libpurple0 libpurple-bin pidgin-data
sudo aptitude update
sudo aptitude install pidgin
```

---

If you want to compile it yourself, add the PPA's listed above, with their source lines (starting with deb-src), then:
```
sudo aptitude update
sudo aptitude install build-essential
sudo apt-get build-deb pidgin
apt-get source pidgin
cd pidgin-2.6.1
debuild binary-arch
```

---

If you're really hardcore and want to compile the dependencies yourself, you need the newest versions of farsight2 (0.0.14), libnice and gstreamer. I really don't advise this though. It'll take all day.

---

Once it's installed, just restart pidgin and open a conversation. Click on Conversation (at the top) -> Media and you'll see a list of voice/video related things. Note that it'll only work with Google Talk/XMPP and only with other people with Pidgin 2.6.1 (with voice and video) or the Google Talk web client. Also it might work with new versions of Empathy.. Who knows though.

---

### Post by korin43 on 2009-08-19
Oops didn't mean to post this as a seperate reply.

---

### Post by cooldudei06 on 2009-08-20
Great post Korin43.

One library you forgot to mention is libgstreamer-plugins-base0.10-dev
(mentioned at [http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo]("http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo"))

Also, after running configure, make sure at the end it says
'Build with voice and video.... yes'.

The links to start Voice and Video are in the conversation window > Conversation > Media

---

### Post by korin43 on 2009-08-20
Thanks a lot. I was just trying to compile this on my roommate's computer and I couldn't figure out what I was missing and causing:
"checking for GSTINTERFACES... no"

Installing that library did it :)

---

### Post by korin43 on 2009-08-21
Hey so I got this compiled in a PPA for anyone who needs it. You'll still need Nicolas DERIVE for dependencies:
[https://launchpad.net/~kalon33/+archive/ppa/+index?start=0&batch=75](https://launchpad.net/~kalon33/+archive/ppa/+index?start=0&batch=75)

And here's mine:
[https://launchpad.net/~korin43/+archive/ppa](https://launchpad.net/~korin43/+archive/ppa)

Right now it has pidgin-2.6.1 with voice/video enabled. I'm planning to add up to date versions of pidgin-facebookchat and skype4pidgin :)

Oh, and I think I got the dependencies right, but let me know.

If anyone else wants to package it the debian way, I just grabbed the source for pidgin 2.6.1 from getdeb (since they added the code to seperate the packages into pidgin pidgin-dev libpurple0 libpurple-bin finch and pidgin-data).

---

### Post by kagashe on 2009-08-21
> **korin43 said:**
> Hey so I got this compiled in a PPA for anyone who needs it. You'll still need Nicolas DERIVE for dependencies:
[https://launchpad.net/~kalon33/+archive/ppa/+index?start=0&batch=75](https://launchpad.net/~kalon33/+archive/ppa/+index?start=0&batch=75)

And here's mine:
[https://launchpad.net/~korin43/+archive/ppa](https://launchpad.net/~korin43/+archive/ppa)

Right now it has pidgin-2.6.1 with voice/video enabled. I'm planning to add up to date versions of pidgin-facebookchat and skype4pidgin :)

Oh, and I think I got the dependencies right, but let me know.In view of your pre-compiled packages on PPA could you please post here how to install Pidgin 2.6.1 On Ubuntu Jaunty using these two PPAs including all dependencies.

kagashe

---

### Post by korin43 on 2009-08-21
> **kagashe said:**
> In view of your pre-compiled packages on PPA could you please post here how to install Pidgin 2.6.1 On Ubuntu Jaunty using these two PPAs including all dependencies.

kagashe

To add the sources, go to the main menu, click System, then Administration, then Software Sources. Click on the Third-Party Software tab, then click the Add button.

Paste:
```
deb http://ppa.launchpad.net/kalon33/ppa/ubuntu jaunty main
```

Click Add Source, then click the Add button again and add my PPA:
```
deb http://ppa.launchpad.net/korin43/ppa/ubuntu jaunty main
```

Close that window then open up a terminal and put this in:
```
sudo aptitude update
sudo aptitude install pidgin
```

That should be it. Let me know if anything doesn't work.

---

### Post by kagashe on 2009-08-21
> **korin43 said:**
> To add the sources, go to the main menu, click System, then Administration, then Software Sources. Click on the Third-Party Software tab, then click the Add button.

Paste:
```
deb http://ppa.launchpad.net/kalon33/ppa/ubuntu jaunty main
```

Click Add Source, then click the Add button again and add my PPA:
```
deb http://ppa.launchpad.net/korin43/ppa/ubuntu jaunty main
```

Close that window then open up a terminal and put this in:
```
sudo aptitude update
sudo aptitude install pidgin
```

That should be it. Let me know if anything doesn't work.
I followed your instructions but I don't see any option to use Voice &/or Video.

Here is relevant information from Help/About:
> Pidgin 2.6.1
(libpurple 2.6.1)
76c08f9df332fb22059ada8287a5da4b7a1d37fa

Pidgin is a graphical modular messaging client based on libpurple which is capable of connecting to AIM, MSN, Yahoo!, XMPP, ICQ, IRC, SILC, SIP/SIMPLE, Novell GroupWise, Lotus Sametime, Bonjour, Zephyr, MySpaceIM, Gadu-Gadu, and QQ all at once.  It is written using GTK+.

You may modify and redistribute the program under the terms of the GPL (version 2 or later).  A copy of the GPL is contained in the 'COPYING' file distributed with Pidgin.  Pidgin is copyrighted by its contributors.  See the 'COPYRIGHT' file for the complete list of contributors.  We provide no warranty for this program.

URL: [http://pidgin.im/](http://pidgin.im/)

FAQ: [http://developer.pidgin.im/wiki/FAQ](http://developer.pidgin.im/wiki/FAQ)

Help via e-mail: [email]support@pidgin.im[/email]

IRC Channel: #pidgin on irc.freenode.net

XMPP MUC: [email]devel@conference.pidgin.im[/email]

Debugging Information
  Arguments to ./configure:   '--build=i486-linux-gnu' '--prefix=/usr' '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--libexecdir=${prefix}/lib/pidgin' '--disable-maintainer-mode' '--disable-dependency-tracking' '--enable-gevolution' '--enable-cap' '--with-system-ssl-certs=/etc/ssl/certs' '--enable-perl' '--with-zephyr=/usr' '--enable-dbus' '--enable-gnutls=no' '--enable-nss=yes' '--enable-cyrus-sasl' 'build_alias=i486-linux-gnu' 'CC=cc' 'CFLAGS=-g -O2 -g -Wall -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS='
  Print debugging messages: No
  Plugins: Enabled
  SSL: SSL support is present.

  Library Support
    Cyrus SASL: Enabled
    D-Bus: Enabled
    Evolution Addressbook: Enabled
    Gadu-Gadu library (libgadu): Enabled
    GtkSpell: Enabled
    GnuTLS: Disabled
    GStreamer: Enabled
    Mono: Disabled
    NetworkManager: Enabled
    Network Security Services (NSS): Enabled
    Perl: Enabled
    Startup Notification: Enabled
    Tcl: Disabled
    Tk: Disabled
    Voice and Video: Enabled
    X Session Management: Enabled
    XScreenSaver: Enabled
    Zephyr library (libzephyr): External
    Zephyr uses Kerberos: No


kagashe

---

### Post by kagashe on 2009-08-21
> **cooldudei06 said:**
> The links to start Voice and Video are in the conversation window > Conversation > Media
found it and it works!

kagashe

---

### Post by Cope57 on 2009-08-21
What issues were you having with pidgin 2.5.8?

If it was not broken, why was there a need to *fix* it...

---

### Post by korin43 on 2009-08-21
There's nothing wrong with 2.5.8. The reason to update is for new functionality in 2.6.1.

Kagashe: What arch are you using (32 bit, 64 bit, arm)? I'm gonna look through the compile logs and try to figure out what's missing. You might also be missing a required library (I'm not sure I got the depends right).
EDIT: According to the [build logs](http://launchpadlibrarian.net/30608280/buildlog_ubuntu-jaunty-amd64.pidgin_1%3A2.6.1-1~ppa1_FULLYBUILT.txt.gz), voice/video should be enabled, so I must be missing a dependency somewhere :(

EDIT2: Checked the dependencies.. I don't think anything is missing. Anyone else have ideas? I'd say post your debug log but I don't really feel like going through the billion pages of debug info Pidgin gives.. (start pidgin with "pidgin -d" and you'll understand what I mean).

EDIT3: One last idea. Is your Ubuntu completely up to date? I might have accidentally updated something you didn't, so try updating everything that's available..

Oh and.. in your conversation window, click the "Conversation" menu item to get a menu. In that menu should be "media" with options like "audio call", but it will be greyed out for anyone except certain jabber/google talk users.

---

### Post by kagashe on 2009-08-22
> **korin43 said:**
> 
Oh and.. in your conversation window, click the "Conversation" menu item to get a menu. In that menu should be "media" with options like "audio call", but it will be greyed out for anyone except certain jabber/google talk users.
found it and tested it. Audio call working!

kagashe

---

### Post by mac-duff on 2009-08-22
Morning,

can anybody help me out with this:

> 
I ve compiled now Pidgin and have a option video audio but which is also by gmail users greyed out. Do the gmail user also has to run Linux and Pidgin so it does not work with the gmail client on windows?

Another point is, I had to update gstreamer and gst plugin base and now I cant play mp3s with Totem any more, VLC works.

Error is:
Code:

Totem could not startup.
Could not find the audio output. You may need to install addiotional GStreamer plugins...

I ve already reinstalled the packages over the package manager

Thx


---

### Post by sikku on 2009-08-22
> **korin43 said:**
> To add the sources, go to the main menu, click System, then Administration, then Software Sources. Click on the Third-Party Software tab, then click the Add button.

Paste:
```
deb http://ppa.launchpad.net/kalon33/ppa/ubuntu jaunty main
```Click Add Source, then click the Add button again and add my PPA:
```
deb http://ppa.launchpad.net/korin43/ppa/ubuntu jaunty main
```Close that window then open up a terminal and put this in:
```
sudo aptitude update
sudo aptitude install pidgin
```That should be it. Let me know if anything doesn't work.

@Korin

Hi,

I did exactly as the instruction given by you... But the media part is grayed... I cannot make a call... not can others make a call... I know the call can be made only to those who have call enabled... I am able to make the call to the same user from fedora 11 but not from Ubuntu Jaunty...

If I do ./configure I am not getting the required output...
i.e I am getting this at the end...

```
Build with voice and video.... : no
```

Did I miss anything???

---

### Post by kagashe on 2009-08-22
@ Korin43
Can somebody compile Pidgin 2.6.1 on Hardy after installing dependencies from:
> deb [http://ppa.launchpad.net/kalon33/ppa/ubuntu](http://ppa.launchpad.net/kalon33/ppa/ubuntu) hardy main 
deb-src [http://ppa.launchpad.net/kalon33/ppa/ubuntu](http://ppa.launchpad.net/kalon33/ppa/ubuntu) hardy main

kagashe

---

### Post by kagashe on 2009-08-22
korin43

After installing Pidgin 2.6.1 I contacted a Windows user. Initially he called me and I accepted the call but we could not hear each other. Then I called him he accepted and we could hear each other.

Later on in the evening I could contact Ubuntu jaunty user who had installed as per these instructions. When either of us initiated the call we could not hear each other similar to the first case when Windows person had called me.

Please tell me how to debug further and where/how to submit the bug report.

kagashe

---

### Post by korin43 on 2009-08-22
There are some things anyone using this needs to know:
- It will only work with XMMP/Google Talk
- It will only work with Google Talk on Pidgin (this version) or the web version of Google Talk (desktop Google Talk will NOT work)
- This will only work on Ubuntu Jaunty (and probably Karmic)

Here's the build-depends (I'll put this on the front page too):
intltool, libgtk2.0-dev, libxss-dev, libmeanwhile-dev, libgadu-dev (>= 1:1.6+20060215), libnss3-dev (>= 3.11.7), tcl8.4-dev, tk8.4-dev, libgstreamer0.10-dev, libgtkspell-dev, libltdl3-dev, libperl-dev,
 libstartup-notification0-dev, libzephyr-dev, libxml2-dev, libebook1.2-dev, libedata-book1.2-dev, libcamel1.2-dev, libdbus-glib-1-dev, dbus, python (>= 2.4), libavahi-client-dev, libavahi-glib-dev, libxml-parser-perl, libncursesw5-dev, libsasl2-dev, xsltproc, doxygen, libsilc-1.1-2-dev | libsilc-dev (>= 1.1.1), libsqlite3-dev (>= 3.3), ca-certificates, network-manager-dev, libidn11-dev, libgstfarsight0.10-dev (>= 0.0.14), libgstreamer0.10-dev (>= 0.10.23), libgstreamer-plugins-base0.10-dev (>= 0.10.23)

so try running:
```
sudo apt-get install intltool libgtk2.0-dev libxss-dev libmeanwhile-dev libgadu-dev libnss3-dev tcl8.4-dev, tk8.4-dev libgstreamer0.10-dev libgtkspell-dev libltdl3-dev libperl-dev libstartup-notification0-dev libzephyr-dev libxml2-dev libebook1.2-dev libedata-book1.2-dev libcamel1.2-dev libdbus-glib-1-dev dbus python libavahi-client-dev libavahi-glib-dev libxml-parser-perl libncursesw5-dev libsasl2-dev xsltproc doxygen libsilc-1.1-2-dev libsqlite3-dev ca-certificates network-manager-dev libidn11-dev libgstfarsight0.10-dev  libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
```

Let me know if it's not compiling for you using the build-depends I'm using (and you're on Ubuntu).

You can submit bug reports on their website: [http://developer.pidgin.im/wiki/TipsForBugReports](http://developer.pidgin.im/wiki/TipsForBugReports)
If you submit a bug report using my build, let them know that that you're using Pidgin 2.6.1 for Ubuntu (from getdeb) recompiled with support for Voice/Video. The build logs (showing Build with voice and video.... : yes) are here: [i386](http://launchpadlibrarian.net/30608346/buildlog_ubuntu-jaunty-i386.pidgin_1%3A2.6.1-1~ppa1_FULLYBUILT.txt.gz), [amd64](http://launchpadlibrarian.net/30608280/buildlog_ubuntu-jaunty-amd64.pidgin_1%3A2.6.1-1~ppa1_FULLYBUILT.txt.gz).

---

### Post by kevdog on 2009-08-23
Are you recommending compiling gstreamer and nice from source as well as farsight2 or taking them from repository?

---

### Post by iheartubuntu on 2009-08-23
Thanks for all your hard work everyone. Is there any development in the future for ICQ video? My wife only uses ICQ! She is in Europe right now and because I dont use Microsoft products at home, I have to wait to get into work and use a company computer to do video. 

Even though I am a 3+ years Ubuntu user now the lack of video support is a major problem that needs to be solved. My wife uses her little netbook with built in cam on ICQ to chat with her family all day long on video. She shows them our veggie garden, front yard fence I just built, clothes she just bought, etc. We dont ever use a phone anymore when my wife calls home. Its all done by ICQ with both parties having high speed internet service.

Now my wife is visiting her family in Europe and I cant show my wife the pets or anything. It pains me to say this but I may have to install XP and do a dual boot, which would be a major hassle and a dent in my Ubuntu armor (sort of speak :) ).

ICQ doesnt work in Wine (older versions do, but video doesnt work). ICQ works fine in my XP Virtual Box, but the video doesnt work. Any suggestions I could try so I dont have to do a dual boot setup?

---

### Post by korin43 on 2009-08-23
> **kevdog said:**
> Are you recommending compiling gstreamer and nice from source as well as farsight2 or taking them from repository?

I'd recommend just installing from my PPA (add my PPA and the Nicolas DERIVE, then apt-get update).

If you want to compile, add the Nicolase DERIVE PPA and then install the dependencies I listed.

If you really want to you can compile it all yourself, but that's a lot of effort and it won't make a difference in the end.

And I'm not a Pidgin developer, I'm just learning how to package things so I figured I'd give it a try with this version of Pidgin.

As for ICQ, Pidgin is using the [Farsight2](http://farsight.freedesktop.org/wiki/) libraries, and they don't support ICQ, so it's unlikely that Pidgin ever will. Is there any way you can convince your relatives to use Skype? Also, VMWare supports USB webcams, so you could use ICQ in Windows XP running in VMWare. I don't really know how to do that or how much effort it takes though.

---

### Post by kevdog on 2009-08-23
korin43

How did you make your packages?  Im installing the dependencies from source on Intrepid.  Yes the hard way.  farsight2 and nice were from the git tree, and gstreamer, gstreamer-plugins were from latest release.  Yes it took my crappy computer over 3 hourse to compile all that.  I'm currently grabbing pidgin from mtn.  Away to make all this hard work distributable?

---

### Post by abhiroopb on 2009-08-23
Just to let you guys know. I installed Pidgin 2.6.1 (through the pidgin dev PPA) and all the required libraries were updated/installed. 

The Audio/Video chat worked great with a friend using a Mac. Not as clear as skype but definitely a good alternative for me.

---

### Post by ian_hawdon on 2009-08-23
> **abhiroopb said:**
> Just to let you guys know. I installed Pidgin 2.6.1 (through the pidgin dev PPA) and all the required libraries were updated/installed. 

The Audio/Video chat worked great with a friend using a Mac. Not as clear as skype but definitely a good alternative for me.

I also installed through the Pidgin-Developers PPA, but the Media options are still grayed out for all Gtalk users... my webcam (built-in iSight) works fine for cheese and Skype, and I installed gnome-media (Kubuntu user here), anyone got any suggestions?

---

### Post by abhiroopb on 2009-08-23
> **ian_hawdon said:**
> I also installed through the Pidgin-Developers PPA, but the Media options are still grayed out for all Gtalk users... my webcam (built-in iSight) works fine for cheese and Skype, and I installed gnome-media (Kubuntu user here), anyone got any suggestions?

Its sometimes greyed out for me too. Best thing to do is close down all programs that are using voice (e.g. skype, ekiga, pidgin, etc.) and then just restart pidgin. This worked for me.

---

### Post by ian_hawdon on 2009-08-23
> **abhiroopb said:**
> Its sometimes greyed out for me too. Best thing to do is close down all programs that are using voice (e.g. skype, ekiga, pidgin, etc.) and then just restart pidgin. This worked for me.

Still nothing :-(

---

### Post by abhiroopb on 2009-08-23
> **ian_hawdon said:**
> Still nothing :-(

Does the person you want to communicate with have Voice/Video Chat enabled?

How did you install it?

---

### Post by ian_hawdon on 2009-08-23
> **abhiroopb said:**
> Does the person you want to communicate with have Voice/Video Chat enabled?

How did you install it?

I've just installed it on their system (the use camera withing gmail tool)

EDIT: and I upgraded pidgin from the developers ppa using:

```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```

---

### Post by korin43 on 2009-08-23
Since the packages and build-deps are on the [Pidgin Developers PPA](https://launchpad.net/~pidgin-developers/+archive/ppa), all you need to do now is add that one and apt-get update, apt-get upgrade.
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

---

### Post by jarwadi on 2009-08-23
Pidgin is successfully installed on my ubuntu 9.04 by following this method. I can connect and chat with my gmail and facebook chat but I can not connect to my yahoo chat account.

The error message is : Received invalid data

Can anyone please help me?

---

### Post by kevdog on 2009-08-23
The ppa only is active for the xmpp protocol which is Jabber/Gmail.  Yahoo,MSN,AIM, or any other protocol you can think of is not supported.

---

### Post by ian_hawdon on 2009-08-24
> **korin43 said:**
> Since the packages and build-deps are on the [Pidgin Developers PPA](https://launchpad.net/~pidgin-developers/+archive/ppa), all you need to do now is add that one and apt-get update, apt-get upgrade.
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

That is the ppa I am using, but the options are still grayed out for Gtalk users, my webcam works in gstreamer-properties, so I really don't know what's wrong!

---

### Post by abhiroopb on 2009-08-24
The implementation still seems a bit shoddy. It sometimes works and sometimes doesn't.

Is pulse at fault again? It always seems to be at the root of all audio related problems (I wonder why?? :P)!

---

### Post by ian_hawdon on 2009-08-24
> **abhiroopb said:**
> The implementation still seems a bit shoddy. It sometimes works and sometimes doesn't.

Is pulse at fault again? It always seems to be at the root of all audio related problems (I wonder why?? :P)!

haha, I got rid of pulse ages ago, and never looked back!

I'm guessing this is one of those mysteries that'll probably get randomly solved in Ubuntu 9.10, I just can't see what's causing this problem!

---

### Post by MBG1987 on 2009-08-24
tnx for all replies ! I think my ubuntu needs some dependencies in order to run the new version of pidgin ...

---

