---
title: "Tether Sprint Blackberry 7130e SUCCESS!"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by bigmack83 on 2008-03-20
I have successfully tethered my Blackberry phone to my Ubuntu 7.10 box.

Carrier: Sprint
Phone: Blackberry 7130e
Windows DSL Reports Avg Download Speed: Low 700kb
Ubuntu DSL Reports Avg Download Speed: Mid 900kb

i had a decent speed increase for my speed, according to sprint my connections should be rated on average in the 600's so i think im doing well. It took me 3 days of constant searching the forums and compiling results from multiple threads. I will show you the compiled results here instead of just giving you the thread links (which was my problem, no one place to go)

On a side note before i show you, i used XmBlackberry to connect. Some people said the only supported phone was the Pearl but i think as long as you set up your connections properly, correctly spell everything, and watch you upper and lower cases you should be fine (right before i finished i couldnt get XmBlackberry to register at all for nearly 4 hours of tinkering and eventually realized that i Wrote "XmBlackberry" when it was supposed to be "XmBlackBerry" one i did that it went smoothly.)

Another thing that took me a while to figure out was my installed packets. In the beginning i wasnt able to compile, and when i was i got all kinds of errors. Finally i searched through my errors in the konsole and all the libs, or anything else it said i needed i searched for it in the packet manager and downloaded everything that related to that error/search. Eventually things started installing easier and i started narrowing down my problems.

At this point i am looking for a good way to make a good Disconnect launcher to stick on my desktop. I just started getting into Ubuntu (and linux at all for that matter) for 2 or 3 days now so i am still relativley a noob at all this. I just got tired of M$ Winblows and am going for a mostly full move to linux. I still need windows as im going to school and i use Adobe CS3 and that doesnt wine at all, and i get better performance running in windows rather than a Virtual Box. Well anyways heres what to do to get a Blackberry connected:

You MUST download this post to your hard drive to reference it later. You may also have to go somewhere that has an open connection so you can still get a net connection temporarily (even better) as you do need to download some things

(i will link to origional forums at the end of the post)

[Before you do anything update EVERYTHING. it is vital. Download any and all C# compiling utilities/packets that you need to compile all of this. If you miss something look for the missing packet (or app) and search for them and download them either through the packet manager or the add remove apps.

Also some of the apt-get's and what not didnt work ( i will note them when they come up). When you download them from the alternate link remember that location as when i tell you to use the command "cd' to go to that directory it will say "no directory exists" (ex:  cd XmBlackBerry). instead it might be "cd /home/<your username here>/Desktop/XmBlackBerry" so keep in mind that location. The same goes when i give the command to extract the .gz file, which might be on your desktop

Update again if needed, Restart if necessary. 

OK here we go

```
sudo apt-get install libc6-dev g++ gcc make build-essential
```
```
sudo apt-get install libmotif-dev
```


To compile/install all those things i had to install the following packages first (not sure if i really needed ALL of those though)

```
sudo apt-get install libtool autoconf automake cvs libglib2.0-dev libxml2-dev libssl-dev libopensync0-dev libxt-dev x11proto-print-dev libxmu-dev libxft-dev libfreetype6-dev libXp-dev flex byacc libgd2-xpm-dev
```

not sure if that is a safe thing to do(probably OK), so you might want to revert this after (move back) after compiling openmotif.

```
cd /usr/include/
```
```
sudo mv freetype freetype-back
```
```
sudo mv freetype2/freetype/ .
```

*NOTE: in the other post, the above was in one code window. i put them in seperate ones to help out the new guys as you can only put one in at a time. DO NOT copy all the lines at once. Only one at a time

To help XmBlackBerry to run later on:

```
sudo ln -s /usr/X11R6/lib/libXm.so.4 /usr/X11R6/lib/libXm.so.3
```

For those who want all the downloads at once here they are ( i will compile and extract them as we get to them). When i did this i had to download everything at once then compile later. So here they are:

[SIZE="2"]
Openmotif[/SIZE]
// not sure about this one, Some people may already have ver. 3, but in the posts i read that you may have to have this version and uninstall ver 3 to set this up. (can anyone clarify this?)

Out with the old:
```
sudo apt-get remove libmotif3 libmotif-dev motif-clients
```

In with the new:
```
cd ~
```
```
wget ftp://ftp.ics.com/openmotif/2.3/2.3.0/openmotif-2.3.0.tar.gz
```

[SIZE="2"]libXlt[/SIZE]
```
cvs -d :pserver:anonymous@xlt.cvs.sourceforge.net:/cvsroot/xlt co Xlt
```

// I actually had problems downloading this one like this. I had to find the file on the net.
[ftp://ftp.ics.com/openmotif/2.3/2.3.0/openmotif-2.3.0.tar.gz](ftp://ftp.ics.com/openmotif/2.3/2.3.0/openmotif-2.3.0.tar.gz)

//this page may also be helpful to other Linux distros: :)
[http://www.motifzone.net/index.php](http://www.motifzone.net/index.php) 

[SIZE="2"]XmBlackberry[/SIZE]
```
cvs -d:pserver:anonymous@xmblackberry.cvs.sourceforge.net:/cvsroot/xmblackberry co XmBlackBerry
```

// had probs downloading this one to. go here:
[http://downloads.sourceforge.net/xmblackberry/xmblackberry-0.3.0.tar.gz?modtime=1189847430&big_mirror=0](http://downloads.sourceforge.net/xmblackberry/xmblackberry-0.3.0.tar.gz?modtime=1189847430&big_mirror=0)
[SIZE="2"]
Barry[/SIZE]
```
cvs -d:pserver:anonymous@barry.cvs.sourceforge.net:/cvsroot/barry login 
```

// again didnt work for me. i didnt have a login. so heres the download link
[http://downloads.sourceforge.net/barry/barry-0.11.tar.gz?modtime=1197042100&big_mirror=0](http://downloads.sourceforge.net/barry/barry-0.11.tar.gz?modtime=1197042100&big_mirror=0)

// that is downloaded from this page which may be usefull to some as it has many more barry related files:
[http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564](http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564)

Now do this
```
cvs -z3 -d:pserver:anonymous@barry.cvs.sourceforge.net:/cvsroot/barry co -P barry
```


[SIZE="4"]
INSTALLATION and COMPILING:[/SIZE]

First do these:
```
cd /usr/include/
```
```
sudo mv freetype freetype-back
```
```
sudo mv freetype2/freetype/ .
```
// Note the period on the last one. copy and paste the whole line. it didnt work for me the first time

[SIZE="2"]Installing OpenMotif 2.3[/SIZE]

```
cd ~
```
```
tar xzvf openmotif-2.3.0.tar.gz
```
```
cd openmotif-2.3.0/
```
```
./configure
```
```
make
```
```
sudo make install 
```

// if this didnt go well you need to make sure you have al the correct compilers and llibraries.

[SIZE="2"]Installing libXlt[/SIZE]

// Also know as just "Xlt". A few had some problems with this. but if your up to date you should be fine

```
cd ~
```
```
cd Xlt
```
```
./CVSMake
```
```
./configure --prefix=/usr
```
```
make
```
```
sudo make install
```


[SIZE="2"]Installing XmBlackBerry[/SIZE]

// Note this is where i had problems and also a few others did to. make sure your caps and spelling are correct. Note these commands are inside the XmBlackberry folder

```
cd XmBlackBerry/
```

Compile and install:
```
./CVSMake
```
[HTML]./configure --enable-maintainer-mode --disable-shared[/HTML]
```
make
```
```
sudo make install
```

Install libusb (for Barry)

// Still in the XmBlackberry folder

```
cd libusb
```
```
sudo make install
```

Now install opensync (came with XmBlackberry)

```
cd ..
```
```
cd opensync
```
```
make
```
```
sudo make install
```

// a lot of people had problems here. Some were due to they werent up to date on their packages. if if any errors are thrown be sure to look at the error instead of giving up and search for those packets and install them. Dont give up. If your phone really wont sync with linux this isnt where you will have problems at so keep at it and it will install. If you download the new packets just start over on installing this one. It will install.

// ALMOST DONE !!

[SIZE="2"]Install Barry[/SIZE]

```
cd ~
```
```
cd barry
```
```
sh buildgen.sh
```
```
./configure --prefix=/usr
```
```
make
```
```
sudo make install
```

// Now for the fun part...

**[SIZE="3"]PLUG YOUR BLACKBERRY NOW WITH THE USB CABLE.[/SIZE]**

//when you first plug it in it will hang for a sec (the phone) because the os is looking funny at it. it only took maybe 10 - 15 seconds. we will fix this later.

There is an issue whereas the module usb_storage takes over the Blacberry device as soon as it is plugged in and thus XmBB can't use/see it.

We are gonna run Barry's bcharge, this has two uses here:
1) It will regrab the device from usb_storage
2) It will set the BB charging current to 500ma instead of 100ma, this will make the BB happy (no more warning) and allow it to dialog correctly with XmBB.

Because of a driver issue on the pearl we have to run bcharge twice, sounds odd, but is needed, as you will see on the second call the device will be found.

```
sudo bcharge
```
// will think for a second. if your blackberry doesnt pop up the do this:

```
sudo bcharge -o
```

Now, the device should be found. Example:

```
sudo btool -l
```

// good luck. if all goes well you should get this thown back at you:

```
Blackberry devices found:
Device ID: 0x80xxxx. PIN: 241xxxx, Description: RIM #### Series Colour GPRS Handheld
```

// #### will be your model number

Let Barry set it up whenever you plug your phone in:

```
cp /home/<your user name here>/barry/udev/*b* /etc/udev/rules.d/
```

// OK and now its down to the line. This we be the line that will make you be happy (but its not done yet)
 
```
sudo XmBlackberry
```
// check spelling and caps. this is where it tried to thwart me astray

// a small window will pop up. **dont click any buttons in the menu**. When i did it stopped coming up and had to re install XmBlackBerry for it to work.

the terminal should dump something similar to this:

```
XmBlackBerry.c:OptionPopupCallback(995) - GPRS modem device /dev/pts/0
```

// If you found this, CONGRATS, linux can see your modem. but were not done yet.
// DO NOT SHUT IT DOWN YET! if need be open another console because that one will be busy monitoring XmBlackBerry.

Note “/dev/pts/0”, this is going to be your modem device.
If you have other device it might be another number rather than 0, note this for it is important. Mine was "/dev/pts/3" which was only there if i ran XmBlackBerry. So remember this

[SIZE="2"]Tethering & connecting to GPRS / EDGE/CDMA[/SIZE]

// you will need to make a few ppp scripts to go any further.

```
sudo gedit /etc/chatscripts/blackberry
```

// Copy and paste this into your editor:

```
ABORT BUSY ABORT 'NO CARRIER' ABORT VOICE ABORT 'NO DIALTONE' ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT DELAYED ABORT ERROR
SAY "Initializing\n"
'' ATZ
OK-AT-OK ATDT#777
CONNECT \d\c
```

// Save as 'blackberry' in the folders '/etc/chatscripts/'

//-----Verizon users may have to put this into the file instead:

ABORT BUSY ABORT ’NO CARRIER’ ABORT VOICE ABORT ’NO DIALTONE’ ABORT ’NO DIAL TONE’ ABORT ’NO ANSWER’ ABORT DELAYED ABORT ERROR
SAY “Initializing\n”
’’ATZ
SAY “ATE\n”
OK ’AT+CGDCONT=1,“IP","12.168.70.74”’
OK ’AT’
OK ’ATDT*99***1#’
SAY “Dialing\n”
CONNECT “\d\c”

//-----



```
sudo gedit /etc/ppp/peers/blackberry
```

// Copy and paste this into your editor:

debug debug debug
nodetach
/dev/pts/3                                                 // this will be what your modem was. did you remember it??
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
user <your phone number with no dashes>@<your provider>.com / .net 
password <your phone number with no dashes>

// Save as 'blackberry' in the folders '/etc/ppp/peers/'

//-----verizon user may look something more like this:

debug debug debug
nodetach
/dev/pts/2       // your modem number. remember?
115200
connect “/usr/sbin/chat -f /etc/chatscripts/blackberry”
nomultilink
defaultroute
noipdefault
ipcp-restart 7
ipcp-accept-local
ipcp-accept-remote
#need lcp-echo turned off, at least for tmobile, otherwise c0onnectin
# disconnects after few mn of inactivity.
# thanks to ?loon? for this info
lcp-echo-interval 0
lcp-echo-failure 999
modem
noauth
nocrtscts
noipdefault
novj # refused anyway, no point in trying every time
usepeerdns
user <your phone number>@vzw3g.com
password vzw

//-----


// OK now were ready to try and get connected. REMEMBER not to close the XmBlackBerry Window or console. If you do start it back up. this is where you jump for joy and go to your browser and type 'www.google.com' to see if it loads. then you will jump for joy again.

// Before you do this make sure any other connections to the net are disabled

```
sudo pppd call blackberry
```

if all goes well the console will throw this:

```
Initializing
Dialing
Serial connection established.
using channel 15
Using interface ppp0
Connect: ppp0 <--> /dev/pts/0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x682edbe8> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x10 <asyncmap 0x0> <auth chap MD5>]
.....
sent [PAP AuthReq id=0x1 user=“thibautc-laptop” password=<hidden>]
.....
PAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
......
local  IP address 10.169.13.231
remote IP address 169.254.1.1
primary   DNS address 66.94.9.120
secondary DNS address 66.94.25.120
Script /etc/ppp/ip-up started (pid 20529)
Script /etc/ppp/ip-up finished (pid 20529), status = 0x0
```
........

// It will take a second to load but if you get that you are connected to the internet. Congrats! The display wont be exact, mine was slightly different (and a heck of a lot longer). so pat yourself on the back for getting yourself through this. 

// And for those who have asked before this DID connect to my EVDO high speed connection

//--------------------------------------------------
// Here were some helpful, specific posts:

//--------------------------------------------------
Post time:02/09/2008 16:56 By:Guest (Guest@127.0.0.1)
Title: Got it working!!
Thank you so much for this article.

I have a bb 8830 and Sprint is the carrier.

I got it working by installing barry, opensync, and deps from source first, then followed your guide. I fought with ppp, then switched to wvdial and voila! Here’s my wvdial.conf:

[Modem0]
Modem = /dev/pts/5
Baud = 115200
SetVolume = 0
Dial Command = ATDT
Init1 = ATZ
FlowControl = Hardware (CRTSCTS)
[Dialer blackberry]
Username = <cell_phone_number>
Password = <cell_phone_number>
Phone = #777
Stupid Mode = 1
Inherits = Modem0

I noticed that sometimes the /dev/pts/5 changes and had to reflect the change in the conf.

This is so sweet!

HippiePete


//--------------------------------------------------

kd7swh's Avatar  	
kd7swh kd7swh is offline
Way Too Much Ubuntu
	  	
Join Date: Jul 2006
Location: Montana, USA
Beans: 298
Fedora User
Thanks: 0
Thanked 1 Times in 1 Posts
Send a message via AIM to kd7swh Send a message via MSN to kd7swh Send a message via Skype™ to kd7swh
Re: Blackberry tether sucess story
I was missing the X11 Xaw developmental library.

Code:

sudo apt-get install libxaw7-dev

should do it.

//--------------------------------------------------

 ps6000  ps6000 is offline
Spilled the Beans
	  	
Join Date: Apr 2007
Beans: 14
Thanks: 0
Thanked 0 Times in 0 Posts
Re: Blackberry tether sucess story
Looks like my 8830 isn't supported yet. Too bad. This was one of the few things keeping me from "not looking back".
__________________


// this isnt necessarily true, my phone technically wasnt supported either. My phone isnt even a GPRS, its an EVDO / CDMA phone.

//--------------------------------------------------


On a side note, i cant stress enough how important it was tocheck spelling and caps, and more importantly to make sure you had ALL your compiler/library/c#/etc.. packets downladed and updated. Thats what made me be able to install and use this

//--------------------------------------------------

Here are the forums that i looked at:

[http://ubuntuforums.org/showthread.php?t=617811](http://ubuntuforums.org/showthread.php?t=617811)

//this is the page that i owe the most credit towards. be sure to leave some comments here to.

[http://wiki.colar.net/tethering_with_blackberry_pearl_on_linux](http://wiki.colar.net/tethering_with_blackberry_pearl_on_linux)

[http://www.blackberryforums.com/linux-users-corner/90882-tethering-8830-sprint-sled.html](http://www.blackberryforums.com/linux-users-corner/90882-tethering-8830-sprint-sled.html)

[http://www.blackberryforums.com/linux-users-corner/92085-how-tether-use-modem-your-bb-linux.html](http://www.blackberryforums.com/linux-users-corner/92085-how-tether-use-modem-your-bb-linux.html)

// Information on making a bluetoothe connection can be found here:
[http://www.thinkwiki.org/wiki/How_to_setup_Bluetooth](http://www.thinkwiki.org/wiki/How_to_setup_Bluetooth)

//-----------------------------------

I will continue to update this first post for corrections and when new or vital info is given. 
I did not come up with all of this my self, its more of a compilation of my experiences trying to get it to work. I take no credit in making this connection guide myself. it is cut and pasted from different forums

Please give as much feedback as you can. if you know alternatives to specific things or suolutions to problems let me know and i will fix it in this post. 

I couldnt have done this with out the Ubuntu forums, thanks for your help to...

:guitar:

I have linked a gzip of all the files i downloaded.I also put the 2 launchers that i created for convenience. Remember to use the XmBlackBerry launcher first. it is an 8.3 Mb file

[http://www.4shared.com/file/41352248/fe892b36/Blackberry_Tethering_FIles.html](http://www.4shared.com/file/41352248/fe892b36/Blackberry_Tethering_FIles.html)


// If anyone knows if theres a way I can get this to work through the network manager please let me know. I also want to know if theres a way i can set this up so when i plug my phone is it automatically starts the xmblackberry then connects with the pppd call. I would like this to be something that i can put up as a app suite of somesort so it can be posted in a 3rd party repository or something. when you download it, it gets all the files necessary to get it to work.

---

### Post by BDNiner on 2008-03-20
Nice post, I am going to give this a try when I get home.

---

### Post by sangamc on 2008-03-20
wonderful stuff!!!

il probably give it a shot over the course of next week. i have several different blackberry models in my office, from the 7250 to the 8830, ill try them all and post the results as well as any new stuff that might come up

---

### Post by bigmack83 on 2008-03-20
thanks for the comments. Its amazing how much one can learn when one actually looks through the forum and asks for help and researches it. iv only been woking with linux for 3 days now. and before i only knew basic concepts of how programming works. like if/fi/else statements and really simple things like that. so its not hard if your willing to learn

First off in order to be able to do this "Legally" you have to have a data plan from your provider. or you might get charged for using the data.

Ok after having the connection up for a bit , updating and restarting my computer heres some more info:

For some reasn my phone randomly shut off (does this once in a while in windose also, its an 7130e thing i think). So one the phone restarted i had to take the battery out again and let it restart again (those of you who have a 7130 know how much of a pain it is waiting for the phone to start up, worse than windows). during that time i had to shut down my terminals, and xmblackberry. when the phone came back on i re did the 'sudo XmBlackberry' command and the 'sudo pppd call blackberry' command and all was good.

if i didnt do it like this the computer couldnt read my phone for some reason. seems like its an inevitable prob with the 7130.

Ok now, the launchers i made dont work like i wanted them to, i still have to use the console because they have to be ran under 'su' or 'sudo' commands then i have to put in my password. anyone know how to get around this????

Also does anyone have an idea on how to make a disconnect command/launcher that is a friendly disconnection?

---

### Post by bigmack83 on 2008-03-21
ok ive also noticed something odd, im not sure if its just me or if it means something. but when i open the console to enter in 'XmBlackBerry' my phone just goes into 'connected to desktop' mode and wont use the port that supposed to be the internet connection (/dev/pts/3) except it uses (/dev/pts/2) so it doesnt connect. no matter how many times i try. BUT, when i double click the space next to the tab where it says 'shell' and open another shell that is called 'Shell no. 2' it connects to /dev/pts/3 first try  ans then i can do 'pppd call blackberry' and it connects right away. is this some weird coincidence or could that mean anything?

also i am creating a google group to try and bring everyone together on this. i am leaving messages here at ubuntu forums, blackberry forums, and other linux forums. I have seen a lot of people try to do this on many different sites. i think if we worked together we could get this working as im connected now and others can to and some cannot. id like to get this thing solved for more people. so please join the group.

[http://groups.google.com/group/blackberryonlinux](http://groups.google.com/group/blackberryonlinux)

---

### Post by swimmerbody on 2008-04-11
my machine has success with wvdial, dns resolution, ping to [www.google.com](www.google.com) works but browser wont resolve.  Is there a proxy setting to change? other problem?

---

### Post by fireman71 on 2008-04-11
I tried this with the 8130 on the sprint network and ran into a few problems.

First when I plug the blackberry in on ubuntu 7.10  with the usb cale the file browser opens up automagically. I then run the sudo bcharge and sudo bcharge -o in a terminal and get a window that pops up complaining about unsafe device removal and then in the terminal 

Scanning for Blackberry devices...
Found device #015...adjusting charge setting...adjusting Pearl mode to dualDetecting possible kernel driver conflict, trying to resolve...

usb_reset failed: could not reset: No such device
...done

and then I get another file browser window that opens up.

I then go on to run the XmBlackBerry and get the following in the terminal:

fireman71@fireman71-laptop:~$ sudo XmBlackBerry
sync.c:sync_init(296) - rim-sync plugin not available. Unable to find plugin "rim-sync". This can be caused by unresolved symbols Sync disabled.
bb_usb.c:scan_device(1809) - bcdDevice 0107, 1 configurations bcdDevice 0x0107
bb_usb.c:say_hello(510) - Read 0 bytes of 7 from ep 85. Didn't hear hello. Resource temporarily unavailable No error
bb_usb.c:check_endpoint_pair(1506) - Couldn't say hello on endpoint pair 5 5
bb_usb.c:check_endpoint_pair(1478) - found one 3 3
ip_modem.c:NewIpModem(280) - pty name. "/dev/pts/1"

I set the dev to pts/1 in the chat script and call it with sudo pppd call blackberry and it just hangs with:
Initializing
ATE

and I have to control-c to get out of it.

My initial thoughts are that the file browser keeps grabbing the device and keeps everything else fom talking to it.

Does anyone have any experience with the 8130 or can anyone offer any suggestions?

TIA

---

### Post by vn1 on 2008-06-18
I am currently trying to setup my curve 8310 to work with my laptop when ever I open XmBlackberry I receive the error below anyone have any idea?
I know this device has tether capabilities ( [http://www.wireless.att.com/answer-center/main.jsp?t=solutionTab&solutionId=KB84956](http://www.wireless.att.com/answer-center/main.jsp?t=solutionTab&solutionId=KB84956) ) but for some reason I can't get it to work.

here is the output I have.


xxx@vn1-lptp:~/barry$ sudo XmBlackBerry
sudo: unable to resolve host vn1-lptp
sync.c:sync_init(296) - rim-sync plugin not available. Unable to find plugin "rim-sync". This can be caused by unresolved symbols Sync disabled.
bb_usb.c:scan_device(1809) - bcdDevice 0106, 1 configurations bcdDevice 0x0106
bb_usb.c:say_hello(510) - Read 0 bytes of 7 from ep 81. Didn't hear hello. Resource temporarily unavailable No error
bb_usb.c:check_endpoint_pair(1506) - Couldn't say hello on endpoint pair 1 2
bb_usb.c:check_endpoint_pair(1478) - found one 3 4
**bb_usb.c:process(1003) - 242db4ce set mode "RIM_UsbSerData" failed.**


Any one with any idea on how to solve this problem with my device? I've been looking and there's only one post with someone who has a similar problem see([http://www.blackberryforums.com/linux-users-corner/92085-how-tether-use-modem-your-bb-linux-2.html](http://www.blackberryforums.com/linux-users-corner/92085-how-tether-use-modem-your-bb-linux-2.html)) but no answer.

Thanks

---

