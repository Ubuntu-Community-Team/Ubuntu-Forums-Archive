---
title: "Blackberry tether sucess story"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by dna on 2007-11-19
Here's how I got my blackberry 7250 to tether with 7.10

First install software from these[ instructions]("http://wiki.colar.net/tethering_with_blackberry_pearl_on_linux").

The main [XmBlackBerry]("http://xmblackberry.sourceforge.net/") site also has software links in case these don't work.

If you've never compiled anything before:
```
sudo apt-get install libc6-dev g++ gcc make build-essential
```

Build deps:
```
sudo apt-get install libtool autoconf automake cvs libglib2.0-dev libxml2-dev libssl-dev libopensync0-dev libxt-dev x11proto-print-dev libxmu-dev libxft-dev libfreetype6-dev libXp-dev flex byacc libgd2-xpm-dev
```

I also use checkinstall to cut down on the cruft but feel free to just do make install instead...

I found if I didn't compile Xlt before openmotif it would error out when linking to the newer version so compile it first:
Link to [Xlt-13.0.13.tar.gz]("http://downloads.sourceforge.net/xlt/Xlt-13.0.13.tar.gz?modtime=1126877818&big_mirror=0")
```
tar xvzf Xlt-13.0.13.tar.gz
cd Xlt-13.0.13
./configure --prefix=/usr
make
checkinstall
```

On to OpenMotif-2.3 -- 7.10 comes with 2.2 or some such so I installed both versions.
Link to [openmotif-2.3.0.tar.gz]("ftp://ftp.ics.com/openmotif/2.3/2.3.0/openmotif-2.3.0.tar.gz")
```
tar xvzf openmotif-2.3.0.tar.gz
cd openmotif-2.3.0
./configure --prefix=/usr/local
make
checkinstall
```

[XmBlackBerry]("http://downloads.sourceforge.net/xmblackberry/xmblackberry-0.3.0.tar.gz?modtime=1189847430&big_mirror=0") <--link

```
tar xvzf xmblackberry-0.3.0.tar.gz
cd xmblackberry-0.3.0
./configure --prefix=/usr --with-motif-includes=/usr/local/include --with-motif-libraries=/usr/local/lib
make
checkinstall
```

add 'blacklist berry_charge'(without the quotes) to /etc/modprobe.d/blacklist because it just doesn't work right with that module loaded.

Plug in your blackberry and run:
```
lsusb
```
and hopefully you see something like
```
Bus 004 Device 014: ID 0fca:0001 Research In Motion, Ltd. Blackberry Handheld
```

If lsusb hangs then it's probably because berry_charge is still being loaded -- took a while to figure that out... do a 'lsmod | grep berry' to make sure.

-----------------------------------------------------------------------------------------------------------

Now on to the instructions at this [page]("http://www.blackberryforums.com/linux-users-corner/101715-how-verizon-8703e-usb-tethered-linux-ubuntu-7-10-a.html")...

run,
```
sudo XmBlackBerry
```
and look for a line that looks like;
```
XmBlackBerry.c:OptionPopupCallback(998) - GPRS modem device /dev/pts/1
```
and that's your modem, /dev/pts/1

I has lots of problems because I made a symbolic link to /dev/modem so resist the urge until you get everything up and working...

The first pppd script,
```
sudo nano /etc/chatscripts/blackberry
```
with the contents;
```
ABORT BUSY ABORT 'NO CARRIER' ABORT VOICE ABORT 'NO DIALTONE' ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT DELAYED ABORT ERROR
SAY "Initializing\n"
'' ATZ
OK-AT-OK ATDT#777
CONNECT \d\c
```

And then
```
sudo nano /etc/ppp/peers/blackberry
```
with,
```
debug debug debug
nodetach
/dev/pts/1
115200
connect "/usr/sbin/chat -f /etc/chatscripts/blackberry"
nomultilink
defaultroute
noipdefault
ipcp-restart 7
ipcp-accept-local
ipcp-accept-remote
# added this, so that it doesn't disconnect after few mn of innactivity
lcp-echo-interval 0
lcp-echo-failure 999
modem
noauth
nocrtscts
noipdefault
novj # refused anyway, no point in trying every time
usepeerdns
user Your10digitnumber@vzw3g.com
password Your10digitnumber
```

You have to substitute your /dev/pts/* for whatever XmBlackBerry tells you and the user name and password will be different. Google is your friend on that one...

---------------------------------------------------------------------------------------------------------

Now make sure XmBlackBerry is running and your phone looks happy (mine shows 'connected to desktop') then run;
```
sudo pppd call blackberry 
```

...and if you're really, really lucky you should see a configured ppp* when you do an ifconfig and be able to surf the interwebs on your phone.

After you get everything working i believe you can take out the debug and nodetach from  /etc/ppp/peers/blackberry but I haven't gotten that far yet, just wanted to write all this down before I forget some steps. There's probably a way to get it to run from Network Manager also but I haven't looked into it yet.

---

### Post by DoctorMO on 2007-11-20
So explain to me, is this for connecting a blackberry phone to the internet via a computer or is this to connect a computer to the internet via a blackberry phone?

---

### Post by kd7swh on 2007-11-25
yes, this allows you to use the internet connection from your blackberry on your linux box. (or notebook)

Note: some carriers (like Verizon) charge extra (tethering) fees you have to pay before this will work.

thanks for the post, i was having some dependency problems.

---

### Post by kd7swh on 2007-11-25
I am still having problems compiling Xlt attached are logs. I hope they can help.

The problem seems to be in the checkinstall stage. 

the checkinstall log is too large to attach so here it is:

Edit: "log removed"

Edit: I noted that the X11 Xaw library was missing. 
Thanks, its working on my 8703e now.

---

### Post by ps6000 on 2007-11-28
What did you do to get it working, I cannot get xlt to install either.

---

### Post by kd7swh on 2007-11-28
I was missing the X11 Xaw developmental library.

```
sudo apt-get install libxaw7-dev 
```

should do it.

---

### Post by radioactivez0r on 2007-11-29
Forgive me for my ignorance, but I'm still learning Ubuntu.  If I can get this one last application working, I won't have to resort to a dual boot on my laptop.  I am able to get to the point of the system apparently recognizing my BB (from the lsusb command), but I am a  little confused at the next step.  I can't find a simple XmBlackBerry command to issue - my directory contains stuff like .h and .1, but I am unsure what those mean.  

I did get the X11 library (as far as I know), but the xmblackberry install seems to think I don't have Xlt loaded.  It's a little confusing.

---

### Post by ps6000 on 2007-11-30
Looks like my 8830 isn't supported yet. Too bad. This was one of the few things keeping me from "not looking back".

---

### Post by DoctorMO on 2007-12-03
> Looks like my 8830 isn't supported yet. Too bad. This was one of the few things keeping me from "not looking back".

It depends what you want to do, syncing for the 8830 is supported in the Barry project but not phone tethering. Oh and could you send me debug output for your phone? it will be most helpful in developing and research with these phones. 

[http://ubuntuforums.org/showthread.php?p=3884719](http://ubuntuforums.org/showthread.php?p=3884719)

---

### Post by ps6000 on 2007-12-06
I would be happy to send you a log, do you have instructions on how to get the log?

---

### Post by DoctorMO on 2007-12-07
please go here for all instructions:

[http://ubuntuforums.org/showthread.php?p=3907221](http://ubuntuforums.org/showthread.php?p=3907221)

---

### Post by rabbito on 2008-01-23
I am a little confused about how you posted the tutorial as your instructions say to follow the other sites instructions first while yours match them to a degree. Are all of the steps posted here or are they all posted on the other site? Also what is the difference in terms of installing to just:

1. extract file to desktop
2. cd <file>
3. ./configure

i just got done trying to follow the instructions and i can not get Xlt to compile correctly without throwing out a ton of errors (numentry error for everything)

---

### Post by noregrets688 on 2008-01-24
Rabbito- I'm in the same boat. I'm trying to tether a pearl to my laptop running ubuntu 7.1 to make use of the data connection. I'm getting stuck at the part where you compile XLT too. I keep getting numentry blah blah blah. I'm also confused as to the 2 sets of instructions in the beginning as well, although I do note that the ones on ubuntu forums are specific to a different device. 

So I just started using Linux a few days ago, but here's my understanding of it. Configuring  edits the config file to make it specific to your system. Compiling it uses that config file to actually create the binaries. If you only configure and compile, it is the windows equivalent of only downloading the installation files.

---

### Post by noregrets688 on 2008-01-24
.

---

### Post by motion parallax on 2008-01-29
For some reason I'm not able to compile Xlt or XmBlackBerry.  Can someone describe the steps to this?  

I have this tether working on Vista, but I really want it work on Ubuntu so I can use the internet at my university.

Xlt configure leaves errors, then make says there isn't a makefile present.

---

### Post by motion parallax on 2008-01-29
bump anyone?

---

### Post by noregrets688 on 2008-02-01
I'm having that same problem too, and thats what made me finally give up. :guitar:

---

### Post by prizrak on 2008-02-09
I'm confused, is this over USB or Bluetooth DUN?

---

### Post by Derrelicte on 2008-03-05
cvs -d:pserver:anonymous@barry.cvs.sourceforge.net:/cvsroot/barry login 

In this step for installing Barry...

It asks for a password.  I press enter and leave it blank, and it looks like it finishes, but I'm not so sure it grabs all the files because when I try the sh buildgen.sh command, I get the following

```
derrick@derrick-laptop:~/barry$ sh buildgen.sh 
Putting files in AC_CONFIG_AUX_DIR, `../..'.
configure.ac:15: installing `./config.sub'
configure.ac:9: installing `./missing'
configure.ac:9: installing `./install-sh'
configure.ac:15: installing `./config.guess'
src/Makefile.am: installing `./depcomp'
Makefile.am: installing `./INSTALL'
configure.ac:15: required file `./ltmain.sh' not found
autoreconf: automake failed with exit status: 1

```

---

### Post by bigmack83 on 2008-03-20
I have connected my Sprint Blackberry 7130e by tethering it to my ubuntu laptop (7.1 Gutsy). Here is my post

[http://ubuntuforums.org/showthread.php?p=4550979#post4550979](http://ubuntuforums.org/showthread.php?p=4550979#post4550979)

---

### Post by jeffhollon on 2008-03-20
i can't get XmBlackBerry to install, when i run the checkinstall command, i get the below.  is there a deian package that will install on my ubuntu......same thing with the CVS lines.  Xlt and motif installed and said fine.


Installing with make install...

========================= Installation results ===========================
Making install in gprs_protocol_fix
make[1]: Entering directory `/home/jhollon/Desktop/xmblackberry-0.3.0/gprs_protocol_fix'
make[2]: Entering directory `/home/jhollon/Desktop/xmblackberry-0.3.0/gprs_protocol_fix'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'gprs_protocol_fix' '/usr/sbin/gprs_protocol_fix'
/usr/bin/install -c gprs_protocol_fix /usr/sbin/gprs_protocol_fix
/usr/bin/install: setting permissions for `/usr/sbin/gprs_protocol_fix': No such file or directory
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jhollon/Desktop/xmblackberry-0.3.0/gprs_protocol_fix'
make[1]: Leaving directory `/home/jhollon/Desktop/xmblackberry-0.3.0/gprs_protocol_fix'
make[1]: Entering directory `/home/jhollon/Desktop/xmblackberry-0.3.0'
if gcc -DHAVE_CONFIG_H -I. -I. -I. -I./libusb  -I/usr/local/include  -I/usr/include/opensync-1.0   -I/usr/include/libxml2      -g -O2 -Wall -MT XmBlackBerry.o -MD -MP -MF ".deps/XmBlackBerry.Tpo" -c -o XmBlackBerry.o XmBlackBerry.c; \
        then mv -f ".deps/XmBlackBerry.Tpo" ".deps/XmBlackBerry.Po"; else rm -f ".deps/XmBlackBerry.Tpo"; exit 1; fi
XmBlackBerry.c:55:21: error: Xlt/Xlt.h: No such file or directory
XmBlackBerry.c:56:24: error: Xlt/Stroke.h: No such file or directory
XmBlackBerry.c:57:23: error: Xlt/Sound.h: No such file or directory
XmBlackBerry.c:58:30: error: Xlt/SelectionBox.h: No such file or directory
XmBlackBerry.c:329: error: expected &#8216;}&#8217; before &#8216;DEFAULT_STROKE_TRANSLATION&#8217;
XmBlackBerry.c: In function &#8216;Raw&#8217;:
XmBlackBerry.c:682: warning: implicit declaration of function &#8216;XmCreatePromptDialog&#8217;
XmBlackBerry.c:682: warning: assignment makes pointer from integer without a cast
XmBlackBerry.c: In function &#8216;SaveToggle&#8217;:
XmBlackBerry.c:1281: warning: implicit declaration of function &#8216;XltRdbPutString&#8217;
XmBlackBerry.c: In function &#8216;get_password&#8217;:
XmBlackBerry.c:2426: warning: assignment makes pointer from integer without a cast
XmBlackBerry.c: In function &#8216;AddDevice&#8217;:
XmBlackBerry.c:2551: warning: implicit declaration of function &#8216;XltCreateSelectionBox&#8217;
XmBlackBerry.c:2551: warning: assignment makes pointer from integer without a cast
XmBlackBerry.c: In function &#8216;main&#8217;:
XmBlackBerry.c:2931: warning: implicit declaration of function &#8216;XltDisplayFallbackResources&#8217;
XmBlackBerry.c:2936: warning: implicit declaration of function &#8216;XltDisplayOptions&#8217;
XmBlackBerry.c:2960: warning: implicit declaration of function &#8216;XltSetClientIcon&#8217;
XmBlackBerry.c:2961: warning: implicit declaration of function &#8216;StrokeInitialize&#8217;
XmBlackBerry.c:2963: warning: implicit declaration of function &#8216;XltSoundInitialize&#8217;
XmBlackBerry.c:3027: warning: assignment makes pointer from integer without a cast
XmBlackBerry.c:3076: warning: implicit declaration of function &#8216;XltWaitTillMapped&#8217;
XmBlackBerry.c:3079: warning: implicit declaration of function &#8216;XltRedirectStdErr&#8217;
make[1]: *** [XmBlackBerry.o] Error 1
make[1]: Leaving directory `/home/jhollon/Desktop/xmblackberry-0.3.0'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by bigmack83 on 2008-03-20
im still new to this but it looks like your problem is with Xlt. it thowing errors when XmBlackBerry is trying to use is. look at my thread on the previous post and look at the Xlt section and try to re install xlt and continue with the rest of the post and re install the other stuff after it. i had a real similar problem to this to. maybe that will help

if xlt didnt install directly find out if you are missing any packages for it. search for 'Xlt' in the package manager (System --> Admin --> Synaptic Packet manager ). look for ones that come up dealing with C# or compiling libraries. thats what i had to keep doing and eventually it worked. if you are having to use windows to post here you may have to find a different net connection to use for the time being

---

### Post by jeffhollon on 2008-03-20
there is not one listing for Xlt'anything' in my synaptics package manager.



my blackberry for some reason will now finally take a charge from my computer, i just want to be able to use my verizon account to login to my network vpn from the road.....  errrrrrrrr......

---

### Post by bigmack83 on 2008-03-20
sorry my bad, wasnt thingking straight. i meant search for C# entries that relate to libraries and compiling as they may affect the installation. thats what i did and it eventually installed.

Search for 'C#', i heve these istalled:
libzeroc-ice-3.3-cil

search for these and install them:
belocs-locales-bin
cpp
cpp-4.2
g++
g++-4.1
gcc
gcc-3.3-base
gcc-4.1
gcc-4.1-base
gcc-4.2
gcc-4.2-base
libc6-dev
make
libvala0
libvala-dev

those arent all i have installed but from my search of 'compile" i have those installed (plus some other non related stuff also. compare them to what you have and let me know if that helped. update and such if necessary

also when you ran XmBlc=ackBerry it was looking for '/usr/sbin/gprs_protocol_fix' so see if you can figure out when that was supposed to be made and try fixing that app that might not have installed or been made right. just an idea. keep in mind im still pretty new at this so im just throwing out some ideas that i used when i did mine

---

### Post by bigmack83 on 2008-03-21
jeffhollon have you had any success? I wish i could figure out what packages or resources im using when im tethered and when im setting it up so i could post them here. but im not sure how to do that. when you installed Xlt do you remember if it throw any errors? maybe thats where the problem is as it seems a lot of people had a problem there

---

### Post by bigmack83 on 2008-03-21
i am creating a google group to try and bring everyone together on this. i am leaving messages here at ubuntu forums, blackberry forums, and other linux forums. I have seen a lot of people try to do this on many different sites. i think if we worked together we could get this working as im connected now and others can to and some cannot. id like to get this thing solved for more people. so please join the group.

[http://groups.google.com/group/blackberryonlinux](http://groups.google.com/group/blackberryonlinux)

---

