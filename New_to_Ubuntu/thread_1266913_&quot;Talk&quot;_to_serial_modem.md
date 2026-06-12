---
title: "&quot;Talk&quot; to serial modem"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by anewguy on 2009-09-15
Currently using Win98 on old computer to access web.  Was sent a nice serial modem for free by someone from this forum (thanks again!) but haven't been able to get to it.  I tried doing some things in pppconf but must have done them wrong.

I currently don't "see" a modem on the system, and am looking for capability of old Windows "terminal" program to talk to a serial port so you could talk to the modem, be sure it was configured correctly, etc..  The "terminal" program that comes as part of X doesn't appear to me at least to have this capability.  I've tried echoing AT to /dev/ttyS0 (with su) but get told I don't have permissions, etc..

I would really like a CLI or GUI program so I can talk to the modem.

One caveat - the only downloading I can do is through the old Windows 98 computer with dialup, so I would need a complete package so I don't have to go hunting all over for dependencies as well.

Thanks in advance!
Dave :)

---

### Post by lkraemer on 2009-09-15
Dave,
You haven't got that modem online yet?????  What is the holdup???
That has been months since I sent it..........

Don't worry about trying to communicate with the modem, just install
wvdial and let it do it's thing......easy.......

Here are the dependencies for wvdial.
debconf(>=0.5.00) | cdebconf
libc6(>=2.7-1)
libuniconf4.4
libwvstreams4.4-base
livwvstreams4.4-extras
libxplc0.3.13
ppp(>=2.3.0)

Just use Synaptic and search for each of these (minus the (>=2.7-1 etc))
to see which ones you need to download.  (The ones that are installed
will have a box beside them that is filled in with a color....
maybe green......if it is like my system.....)  

Then also install Gnome-ppp......but you need to follow my writeup
first making wvdial work properly.....then and only then setup Gnome-ppp
and use it from the desktop GUI.  Install Gnome-ppp using wvdial
and a dialup connection so you don't have to worry about dependencies.

It shouldn't take more than 30 minutes after you get started.
wvdial will work good.  (You most likely have to uncheck work offline
in Firefox everytime you go online...I have to on my system).

Go to this post:
[http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdial](http://ubuntuforums.org/showthread.php?t=1100310&highlight=wvdial)

Start at "THESE WORK WONDERFUL WITH WVDIAL............" about 
one half way down the post.....

Go step by step......making sure you don't skip any steps.
(You can try both pap and chap ......if needed, but the default
will probably work in pppcon......)

I'll check back later tonight to see how you are progressing.

lkraemer

---

### Post by anewguy on 2009-09-16
Been pretty sick so haven't really felt like doing much except checking email and here once a day or so.  Thanks again SO MUCH for the modem!

I've done some checking, and it appears that I won't be able to connect to Juno and do anything from Linux - all the posts I've read say you can get connected, but it won't let you go anywhere (I assume because it wants all the stuff for their ad servers).

Going to take a look at basicisp (?) - the one that's only $6.95 a month.

I did see via synaptic that to install wvdial I need 4 packages plus gnome-ppp - thanks for the tip as for some reason I went brain-dead and didn't think about checking there to see what dependencies it would mark even though I still have to download it all manually via the Win98 computer.

It may take me a day or two to get everything and get it going.  I have to go to the mental health center Wednesday and have to ride the bus (my first time - never lived in a big city and had to take a bus before).  Means a few switches and a lot of waiting.  Then, I hate to admit it, but my FAVORITE TV shows are on Wednesday night on SyFy, and I just don't miss them if I can avoid it.

Thanks SO MUCH again, and thanks for the pointers!

Dave :)

---

### Post by lkraemer on 2009-09-16
Dave,
I use Copper.net, and it is nation wide in the USA.  It is $99.00 a
year with unlimited connect time, and I haven't had trouble getting
online except during travels through West Texas and on into New Mexico
until after Santa Rosa.  Sparse coverage out there.......

You might want to check them out.  ($8.25 per month)
[www.Copper.net](www.Copper.net)

Keep plugging away at the modem and you'll be online in 30 to 45
minutes after the downloads.  If you have trouble post back and we
will get it going.

Oh, I may have forgotten to tell you......but, the modem was Flashed to
the latest firmware from US Robotics, so you should have the latest
and greatest in the External modem right now.

Good luck with the travels to the Dr. Visit and get well soon.

Also, I read a post somewhere in this forum that Linux worked good with
Juno, but I can't seem to find it right now.  I'd recommend you try it
first with Linux and Firefox before getting another Dialup ISP.
I'll continue  my searches tonight when I have more time.  I know it is
there and I thought I had responed to it but searches for Juno didn't
find anything which contained my username.  I'll try again tonight.

lkraemer

---

### Post by Bartender on 2009-09-16
+1 n Copper.  Their U.S. based tech support is pretty darn friendly and helpful.  You will of course get the usual "we don't support Linux" answer but that doesn't mean it doesn't work.  Just means they're not going to get bogged down trying to help you. 

pppconfig is the most reliable tool for getting online.  It's a little inscrutable at first because you have to use an odd mixture of tab, enter and space buttons to work thru the settings.

If you want to take another run at it, plug the serial modem into the first serial port on the PC (if you can tell) and have it on when the computer starts.  I've configured pppconfig a dozen times on several different computers.  Although it never found the modem, it was always on /dev/ttys0.  That's a zero, not an oh.

---

### Post by Whiffle on 2009-09-16
I've found wvdial to be pretty pain free as well.

---

### Post by anewguy on 2009-09-16
CopperNet and BasicISP both use the exact same 4 numbers here, so I'll be trying BasicISP since it is $6.95/month.  Will be doing all that later - need to download all the pieces for wvdial to work for now.

Thanks again!

Dave :)

---

### Post by anewguy on 2009-09-17
Downloaded the packages I needed to flash and moved to my Ubuntu box and installed them.  Didn't need any instructions - this stuff, including just wvdial, was easy compared to trying to do this in 1995 and 1996 with Slackware.  Just another way that things have changed for the better.  I'll be signing up for BasicISP and trying it out within a day.

Wvdial talked to the modem fine, as did gnome-ppp, so everything should be set to go once I have a username and password.

Thanks again!

Dave :)

---

### Post by lkraemer on 2009-09-17
Dave,
Make sure you start by configuring pppconfig so those files
properly reference pap or chap.  The guide will lead you through
the proper steps.

And once wvdial dials, connects, and you are online you MUST KEEP
THE TERMINAL WINDOW OPEN for your session you are ONLINE.  TO EXIT
YOUR SESSION USE "CNTL C" in the Terminal Window where you executed
wvdial.  Then you can close that Terminal Window.

Once wvdial works properly, then setup Gnome-ppp, and use it from the
Desktop GUI.

I'd suggest trying Juno, because I know I found a post where it works
fine.  I'll do some more searching.  I know it will work.

How about trying this:
[http://ubuntuforums.org/showthread.php?t=111570](http://ubuntuforums.org/showthread.php?t=111570)

NetZero/Juno does work on Ubuntu, but you have to use apt-get or
Synaptic Package Manager to download and install the
Java 2 Runtime Environment (j2re). The NetZero/Juno dialer depends
on j2re. Without j2re, the NetZero/Juno dialer will NOT work.

lkraemer

---

### Post by Bartender on 2009-09-17
I dumped Juno 2 years ago specifically because they were not compatible with Linux.  They rely on proprietary dialer software.  I could get connected, but they'd dump me in about 30 seconds.  From then on, any ISP that used any sort of proprietary software was on the blacklist.
  
Maybe Juno has changed.  When I quit, they wanted to know why and I told them.

---

### Post by anewguy on 2009-09-18
Everything working via pon-poff.  Now I'll try moving over to gnome-ppp, but I have always seemed to have problems with wvdial (which gnome-ppp uses).  Let you know how it goes.

EDIT:  gnome-ppp working okay now - had some additional files I had to change permissions on, plus it helps not to have another network connection up (goes to nowhere anyway!).

Thanks again, 

dave :)

---

### Post by anewguy on 2009-10-01
Only re-opened this so I could add this, which I forgot to put in my original post when I got things working:

For those of you who have to manually tell Firefox to work online, there is a solution:

- there is a bug in networkmanager where it does not report the status of a dialup network, and since Firefox gets its online/offline signal from network manager, Firefox will start in offline mode for dialup.

To fix this:

- via synaptic package manager, simply install wicd and use it in place of networkmanager (installing it will remove networkmanager).  


dave :)

---

### Post by colorpurple21859 on 2009-10-10
netzero will work with just about any distro contrary to what some believe. here is a link to  get netzero working . it works best if you use the java -jre program from sunjava and install according to the howto. [http://www.linuxquestions.org/questions/slackware-14/netzero-628659/](http://www.linuxquestions.org/questions/slackware-14/netzero-628659/)

---

