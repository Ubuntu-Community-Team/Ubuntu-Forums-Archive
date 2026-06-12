---
title: "No wireless with Edgy upgrade: no ra0"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by Steve S. on 2006-12-13
Well, it looks like the upgrade worked, for the first time since Hoary (I've always had to fall back on a clean install).  I definitely have a new kernel in the grub menu, so that looks good.

But I have no wireless.

I was running a linksys wireless card with a cantenna as ra0 and it was working great in dapper.  Now I go to "Network" and I can't get it to configure.  I go to "Network Tools" and it shows that I have ra0 (along with eth0 and lo) and shows that it is active.

I don't know how to set this up via command, please advise.  Or via gui would be great also.

I can't make sure that everything is kosher with the upgrade until I have internet again...no "sudo aptitude update" without a connection!

Please help.

---

### Post by Steve S. on 2006-12-13
Nobody yet?  This seems to be a common problem with the Edgy upgrade...lots of posts with very few answers on this issue.

iwconfig shows ra0 as active, it seems.  So it seems that it recognizes the card, I just can't get a connection.  How do I start it up via command?

I found something [here. ]("http://www.ubuntuforums.org/showthread.php?t=132980&highlight=RaLink+RT61+Wireless+Solved") If I follow (f) through (h) will it get me set up?  I don't quite know enough about command line to know whether or not that will jack my system (technical terminology).

---

### Post by Steve S. on 2006-12-13
No responses?  On a forum that is brutally helpful otherwise, that's quite disconcerting and scary. :-? 

Perhaps this will help and someone that knows what I should do will help...oh, please, oh, please....

The results of iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"garageubuntu"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-206 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

The results of dmesg:
```
ra0: no Ipv6 routers present
```

---

### Post by Steve S. on 2006-12-13
Hey!  Still me answering myself and freaking out...;) 

Perhaps this further information will tell someone what is going on with my system and how I can correct it:
Ran this:
```
sudo gedit /etc/network/interfaces
```
and checked to see if ra0 was set to be automatic and if everything looked kosher.  It was and did.

Then ran this:
```
sudo ifdown ra0
```
 
then this:
```
sudo ifup ra0
```

and got this:
```
There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:12:17:68:1a:2e
Sending on   LPF/ra0/00:12:17:68:1a:2e
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

So, does that clarify anything?

---

### Post by Steve S. on 2006-12-13
Ok, I'm trying to run ndiswrapper since I haven't gotten any response on this thread thus far.

If you can give me a better answer than ndiswrapper, for goodness-sake, [B]please help me out.
[/B]
If not, I'm slowly trying to get ndiswrapper installed.

When I run “make install” to try to install ndiswrapper, I get stuck at this message:
```
make -C driver install
make[1]: Entering directory `/home/stephen/downloads/ndiswrapper-1.2/driver'
Can't find kernel sources in /lib/modules/2.6.17-10-386/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/stephen/downloads/ndiswrapper-1.2/driver'
make: *** [install] Error 2
```

even though the contents of /lib/modules/2.6.17-10-386/build is:
```
control         data.tar.gz    lib                  md5sums
control.tar.gz  debian-binary  linux-2.6.17-10-386  usr

```
Isn't that what it is looking for?  I'm following installation instructions [from here.]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

I have found the driver for my card and all that, so I should be able to take it from there once I get ndiswrapper installed.

PLEASE HELP!!

---

### Post by Steve S. on 2006-12-14
Still no responses?  Maybe I've been black-listed and don't know about it.

Although **I can still use some help with this**, I have figured out how to get a connection.

Ndiswrapper was too complicated for me to set up, and I noticed someone mentioned that wlassistant worked great.  I should have known this, since I'd used it on the livecd of PCLinuxOS before.

Since I'm running a dual boot, I was still able to get to the interent via Windows.  I [went to here]("http://archive.ubuntu.com/ubuntu/pool/main/w/wlassistant/wlassistant_0.5.5-0ubuntu3.2_i386.deb") and got the deb file.

However you can, get the downloaded deb file to your Ubuntu.  Thankfully, my Windoze and Linux drives can read each other, so I just copied it to the Linux drive.

Once the deb file was there, the edgy installer worked great.  I double clicked it, it went through the gui installation process (it asked if I was sure, and stuff like that...just kept saying yes).

Then ran wlassistant as root (it doesn't work if you don't do that):
```
sudo wlassistant

```
...and then it showed the available wireless in the area (there was mine and a neighbor's).  I picked mine, it connected, good to go.

So, the only problem now is that I have to run wlassistant every time I log on.

**Can this be done automatically? ** Advise on that would be appreciated and this thread could be closed as solved.

---

### Post by jmomandia on 2006-12-14
I don't know if this answers your query:

In 6.10, I clicked on Applications, then Add/Remove, then added Wifi Radar. Once installed, it shows all the networks. Just select one and click connect. Hope it works with you.

---

### Post by Steve S. on 2006-12-14
> **jmomandia said:**
> I don't know if this answers your query:

In 6.10, I clicked on Applications, then Add/Remove, then added Wifi Radar. Once installed, it shows all the networks. Just select one and click connect. Hope it works with you.

Excellent!  I added it.  Of course, to add that, you have to have a connection...glad I have one now.  Thanks!

That being said, I am still trying to find a way that the connection will automatically be running when I log on.  That is the only connection that I use, so it is a pain to have to connect it each time.

Although, not as much of a pain as not having a connection at all.8)

---

### Post by Steve S. on 2006-12-14
> **jmomandia said:**
> I don't know if this answers your query:

In 6.10, I clicked on Applications, then Add/Remove, then added Wifi Radar. Once installed, it shows all the networks. Just select one and click connect. Hope it works with you.

Thanks for the response, once again, jmomandia.

No, Wifi Radar didn't get it.  Still wlassistant is the only thing.

Anyone know how to get it to run at startup?  Or, for that matter, how to change what I have running at startup?  I can't find that manager in Edgy.

Thanks.

---

### Post by Dynapen on 2006-12-14
To get a app to startup with the machine, under Gnome it's System > Preferecnes > Sessions
There is a tab for startup programs, and you simply add the command to the list.

---

### Post by Dynapen on 2006-12-14
jmomandia-

When I run wifi-radar, it only gives me the option to disconnect, but even when it finds multiple networks available, it doesn't allow me to conenct to one. 

My problem is that I have multiple wifi networks I connect to throughout the week. What I have to do now is go into the System > Adminisration > Networking menu and manaully changes SSID of the wireless card to the one I want. (which I find using wifi-radar).

Is there a way to tell Ubuntu to automatically connect to the best wifi signal available?

I had that working at one point. Originally had installed Dapper and then upgraded. Had to rebuid it all and when I did the Dapper install (becuase I had the disks) and the did the upgrade again, that part did work anymore

---

### Post by Steve S. on 2006-12-15
> **Dynapen said:**
> To get a app to startup with the machine, under Gnome it's System > Preferecnes > Sessions
There is a tab for startup programs, and you simply add the command to the list.

Thank you much!  I couldn't remember where it was...

---

### Post by Steve S. on 2006-12-15
> **Dynapen said:**
> jmomandia-

When I run wifi-radar, it only gives me the option to disconnect, but even when it finds multiple networks available, it doesn't allow me to conenct to one. 

My problem is that I have multiple wifi networks I connect to throughout the week. What I have to do now is go into the System > Adminisration > Networking menu and manaully changes SSID of the wireless card to the one I want. (which I find using wifi-radar).

Is there a way to tell Ubuntu to automatically connect to the best wifi signal available?

I had that working at one point. Originally had installed Dapper and then upgraded. Had to rebuid it all and when I did the Dapper install (becuase I had the disks) and the did the upgrade again, that part did work anymore

Thank you!  That's my problem exactly...glad I'm not alone.;)

---

### Post by Steve S. on 2007-01-04
So, did anyone figure this out?

I can get a network with no effort if I run wlassistant.  But that is the ONLY way I can get it...I've tried KDE app's and Gnome app's...

I just CAN'T get it to be automatic.  Has anyone figured out how to do this yet?  I had Dapper would automatically find it, but I have yet to get this "new" gnome-network-manager to like ra0 and automatically have it be my primary option and to get it to run in Edgy.

I'll try any suggestions on this...assume I haven't tried anything.  Any hints?  Things to try?

---

### Post by Riyonuk on 2007-01-04
Your trying to automate your wireless connection? Have you tried GTKWi-fi or maybe network-manager-gnome?

Cantenna? What kind, how much distance? Mines crap T_T

---

### Post by Steve S. on 2007-01-04
> **Riyonuk said:**
> Your trying to automate your wireless connection? Have you tried GTKWi-fi or maybe network-manager-gnome?

Cantenna? What kind, how much distance? Mines crap T_T

Cantenna: it's an actual, brand name Cantenna rather than home made...price was pretty close.  I am going from the garage, through the living room and to the router in the master bedroom, so pretty good range I think.  Using a Linksys wireless card, if I hadn't mentioned that before.

I've tried network-manager-gnome and hate how it is set up compared to Dapper.  Just subtle differences are killing me.  Advice on how specifically to set it up?  Maybe I missed something in my fiddling.

I'll try the GTKWi-fi tonight.  Odds are I tried it, but can't remember off the top of my head.  Thanks for trying, either way!

---

### Post by Riyonuk on 2007-01-04
Ahh the cantenna from [www.cantenna.com](www.cantenna.com), I thought you were using some massiv parabolic dish or something.

Setting up network-manager-gnome is pretty much adding it to the panel and thats it :p

And GTK Wi-Fi isnt in the respositiores if I remmber correctly, if you look in the 3rd Party Projects of this forum, you will find it. Hope you get it working, my internet isnt right now.

---

### Post by Steve S. on 2007-01-04
> **Riyonuk said:**
> Ahh the cantenna from [www.cantenna.com](www.cantenna.com), I thought you were using some massiv parabolic dish or something.

Setting up network-manager-gnome is pretty much adding it to the panel and thats it :p

And GTK Wi-Fi isnt in the respositiores if I remmber correctly, if you look in the 3rd Party Projects of this forum, you will find it. Hope you get it working, my internet isnt right now.

Thanks, Riyonuk!

LOL No parabolic dish....

I can get wireless great, but network-manager doesn't find it and use it.  It finds it, just won't use it.

Wlassistant is the only thing, so I hook up with it every time.

Just wish it were automated....I'll try that GTK thing tonight...thanks again.

If you get any other ideas, keep 'em coming...surely something will get this thing as good as it was in Dapper...that's one of the few things I miss BAD.  Oh, well...

---

### Post by sy1911 on 2007-01-04
I have a ralink based wireless adapter that i got working just the other day, so maybe i can help.  Here's a couple questions: 
1) were the drivers installed from a package or did you install them yourself? does it use a config file (/etc/Wireless/RT*STA/ or something similar)
2) what is the output of 
# iwlist ra0 scanning
?

---

### Post by haiku99 on 2007-01-04
> **Riyonuk said:**
> Ahh the cantenna from [www.cantenna.com](www.cantenna.com), I thought you were using some massiv parabolic dish or something.

Setting up network-manager-gnome is pretty much adding it to the panel and thats it :p

And GTK Wi-Fi isnt in the respositiores if I remmber correctly, if you look in the 3rd Party Projects of this forum, you will find it. Hope you get it working, my internet isnt right now.

The parabolic setup can work great FWIW, I built one from a small Weber BBQ lid and a USB wifi adapter, and it will a make a  weak, unusable wifi signal strong.  Woks work great too, there is a good website on all this at [http://www.usbwifi.orcon.net.nz/](http://www.usbwifi.orcon.net.nz/)

---

### Post by scottylans on 2007-01-04
Steve,

Sorry to hear about your problems, I can't help too well unfortunately as I too don't know too much.
That being said it seems to me that 6.10 broke a hell of a lot of wireless things that 6.06 had fine.

---

### Post by Steve S. on 2007-01-04
> **sy1911 said:**
> I have a ralink based wireless adapter that i got working just the other day, so maybe i can help.  Here's a couple questions: 
1) were the drivers installed from a package or did you install them yourself? does it use a config file (/etc/Wireless/RT*STA/ or something similar)
2) what is the output of 
# iwlist ra0 scanning
?

The drivers were already in Ubuntu...in Hoary/Dapper this settup worked OUT OF THE BOX as it were.  i just said, I want ra0 rather than eth0 and it worked.  Seriously that simple...in fact, that ease is why I moved to Ubuntu from Gentoo.

So, it doesn't seem to be the drivers, or any of that, only the recognition of ra0 as the primary.  Sorry, don't know the terms, but I hope you understand my meaning.  I also have an eth0, of course, but I don't ever use it.

Here is the output...hope it tells you more than it did me. ;-)
r```
a0       Scan completed :
          Cell 01 - Address: 00:12:17:44:8B:85
                    Mode:Managed
                    ESSID:"------"
                    Encryption key:off
                    Channel:6
                    Quality:84/100  Signal level:-52 dBm  Noise level:-196 dBm

```

obviously I modified the ESSID.

---

### Post by Steve S. on 2007-01-04
> **scottylans said:**
> Steve,

Sorry to hear about your problems, I can't help too well unfortunately as I too don't know too much.
That being said it seems to me that 6.10 broke a hell of a lot of wireless things that 6.06 had fine.

Amen.

---

### Post by Steve S. on 2007-01-04
> **haiku99 said:**
> The parabolic setup can work great FWIW, I built one from a small Weber BBQ lid and a USB wifi adapter, and it will a make a  weak, unusable wifi signal strong.  Woks work great too, there is a good website on all this at [http://www.usbwifi.orcon.net.nz/](http://www.usbwifi.orcon.net.nz/)

...awesome.  I love it... I have to check it out!

---

### Post by sy1911 on 2007-01-04
Ok, cool.  It looks like the wireless card can see that the network is there, its just not set to connect to it.  I guess then the next questions are: what does /etc/network/interfaces look like, and have you tried using something like iwpriv to manually set parameters?  If not, can you please give the output of `iwpriv ra0`?

---

### Post by sy1911 on 2007-01-05
So I was looking over your earlier posts and I notice that you are getting from dmesg:
ra0: no IPv6 routers or some such.  In your /etc/network/interfaces it should include in the iface block 'inet'.  That   is supposed to tell the device to only look for IPv4 routers.  make the header read 'iface ra0 inet dhcp', and see if you still get the same dmesg error upon rebooting.
If it already does have inet in there, then something weird is going on.  Try
#ifdown
#ifconfig ra0 inet up
#dhclient

and post what that results in.

Please still go ahead and post /etc/network/interfaces if you can.

---

### Post by Steve S. on 2007-01-05
Ok, GTKWifi looks great and seems to work great, but it doesn't connect me to a network.  It shows my card, what percentage it's ouputting, etc. and works automatically.  It just doesn't show any networks to connect to and certainly doesn't connect to them.  If I could get it to work, then that may be a great solution as it runs right away from start up.  Any advice, anyone?

**sy1911**: I'll try to show what I think you are looking for, and thanks in advance for trying to help me with this.  Here is iwpriv ra0:
```
ra0       Available private ioctls :
          set              (8BE2) : set 1024 char  & get   0      
          bbp              (8BE3) : set 1024 char  & get 1024 char 
          mac              (8BE5) : set 1024 char  & get 1024 char 
          e2p              (8BE7) : set 1024 char  & get 1024 char 
          rfmontx          (8BED) : set   2 int   & get   1 char 

```

And here is /etc/network/interfaces.  Notice: I was told by another thread to comment out everything but the lo interface so that network manager could do it's job, which it didn't do.  Since then it appears that /etc/network/interfaces adds and uncomments items as I gain connections.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#iface ra0 inet dhcp
#wireless-essid ---------------





#auto ra0

#iface eth0 inet dhcp



#auto eth0

#iface ra0 inet dhcp
#wireless-essid -----------

#auto ra0

#iface eth0 inet dhcp



#iface ppp0 inet ppp
#provider ppp0



iface ra0 inet dhcp
wireless-essid -------


iface eth0 inet dhcp





auto ra0

```

I included all the spaces that it leaves, 'cause I don't know if it is significant or not.  I changed the ESSID's by the way, as you can see.

---

### Post by Steve S. on 2007-01-05
Oh, and I'm using 1.06 on the GTKWifi, if that matters.

---

### Post by sy1911 on 2007-01-05
Ok.  Regarding GTKwifi:

I tried network-manager which wouldnt work on my machine.  I installed gtkwifi though, and after having the same problem it sounds like you are(device recognized, but no networks show up), I think I figured out why. 

For me at least, it was that I was missing an icon that it wants to use to build the list of available networks.  Sounds wierd, but once I put an icon in the right place, the two networks in my vicinity showed up.  I'm not sure if its a quirk of python or a code issue, but that will actually prevent the networks from showing up and being selectable.

To check, run it from a terminal, click the window to bring up the network list, and watch the terminal window.  you get anything that tells you that an icon is missing(or any other errors for that matter) that might be your problem.  

For me it was /usr/share/icons/hicolor/16x16/stock/data/stock_lock.png.  
If this is in fact a problem, copy any other appropriately sized icon to where the missing one is and rename it appropriately.  

I'm pretty sure though that its seeing your network; it calls iwlist, which does see your network.

thanks for being patient, and i hope this works.

---

### Post by Steve S. on 2007-01-05
> **sy1911 said:**
> Ok.  Regarding GTKwifi:

I tried network-manager which wouldnt work on my machine.  I installed gtkwifi though, and after having the same problem it sounds like you are(device recognized, but no networks show up), I think I figured out why. 

For me at least, it was that I was missing an icon that it wants to use to build the list of available networks.  Sounds wierd, but once I put an icon in the right place, the two networks in my vicinity showed up.  I'm not sure if its a quirk of python or a code issue, but that will actually prevent the networks from showing up and being selectable.

To check, run it from a terminal, click the window to bring up the network list, and watch the terminal window.  you get anything that tells you that an icon is missing(or any other errors for that matter) that might be your problem.  

For me it was /usr/share/icons/hicolor/16x16/stock/data/stock_lock.png.  
If this is in fact a problem, copy any other appropriately sized icon to where the missing one is and rename it appropriately.  

I'm pretty sure though that its seeing your network; it calls iwlist, which does see your network.

thanks for being patient, and i hope this works.

Oh, man, keeps the suggestions coming...this wireless thing is the only thing left giving me grief on the edgy upgrade, and you're keeping me trying things.  Soooo close!  I'll try those suggestions tonight, sy1911.  Expect a response soon!

---

### Post by Steve S. on 2007-01-05
Well, crap.

I've got good news and bad news.

Bad news: I tried what was suggested for gtkwifi, didn't go.  It would even show, of the two conections in the area, which one it noted as strongest ("linksys 64%") in the applet but it wouldn't show anything in the gui, so now go.

I tried every KDE app I could find, after I tried every gnome thing in the world.  The only one that worked every time was wlassistant, but you had to reset that each time.

Then I did something, but I don't know what.

Good news: now I have a connection at boot up, every time.  Don't know what I did.  CRAP!!

That's almost as bad as not figuring it out.

The last two things I did was I ran kwirelessmonitor.  I went through the settings, it looked good, but it showed that there was no connection in the little applet.  BUT I DIDN'T CHECK THE BROWSER, SO I DON'T KNOW FOR SURE.

Then I ran wlassistant, 'cause I wanted to post on this thread how bad I was doing.  Then it said I already had a connection and that I would be disconnecting it.

Had I run wlassistant before I ran kwirelessmonitor?  I don't think so, but I'm not sure.

Now it works automatically at boot.  ???  kwirelessmonitor kicked something over even though it said it didn't?  That's the best I can guess.

Anyone want to try and figure out what happened?  Wish I could help with a deffinite "this worked great for me!" but I can't.  sy1911, any ideas?:-k

---

### Post by sy1911 on 2007-01-06
That's great that it's working, even if mysterious.  I have had that happen before and spent longer trying to replicate it than it took to fix.

In any case, not sure how much more effort your willing to put into figuring this out, but if you are willing to answer a few questions about what happened that would be great.

1) What program are you using now that works?  GTKwifi or network-manager (or something else)?
2) have you uninstalled everything you tried that didnt work, or did you leave them on your system?
3) What was the version on kwirelessmonitor?
4) When you tried gtkwifi in the terminal the first time, did it return errors or were there no problems?

I'd like to spend a bit more time on it; it would be nice to have the solution for others.

Thanks again

---

### Post by Steve S. on 2007-01-06
> **sy1911 said:**
> That's great that it's working, even if mysterious.  I have had that happen before and spent longer trying to replicate it than it took to fix.

In any case, not sure how much more effort your willing to put into figuring this out, but if you are willing to answer a few questions about what happened that would be great.

1) What program are you using now that works?  GTKwifi or network-manager (or something else)?
2) have you uninstalled everything you tried that didnt work, or did you leave them on your system?
3) What was the version on kwirelessmonitor?
4) When you tried gtkwifi in the terminal the first time, did it return errors or were there no problems?

I'd like to spend a bit more time on it; it would be nice to have the solution for others.

Thanks again

Oh, I'm right there with you.  I would love to be definitive about what happened, but I don't know if my answers will help...
```
1) Nothing.  Neither GTKwifi or network-manager or anything else (that I know of) is running.  
2) I left them on my system.  They are not visibly running, though.
3) 0.5.91, KWirelessMonitor
4) No errors, really, and definitely not the icon thing.  I added an icon anyway to see if it made 
a difference (would have loved for something so random to have worked!) but no effect, so I 
got rid of gtkwifi and the icon (just shut it down).
```

Yeah, I don't know either.:-k

---

### Post by sy1911 on 2007-01-06
Given that you aren't running anything in the way of graphical utilities, maybe something you did setup all your config files up, removing an error we weren't catching, and now it uses a traditional ifup method to get everything running.  Some things to try:
  
#ifdown ra0
#ifup ra0

and see if its successful.  Also, its sort of a long shot, see it there is now a "/etc/sysconfig/network" folder on your machine.  One of the kde apps you tried may have tried to setup your wireless using that method.  It looks like kwirelessmonitor looks for that setup, but I'm not sure it could actually create those files.

---

### Post by Steve S. on 2007-01-07
> **sy1911 said:**
> Given that you aren't running anything in the way of graphical utilities, maybe something you did setup all your config files up, removing an error we weren't catching, and now it uses a traditional ifup method to get everything running.  Some things to try:
  
#ifdown ra0
#ifup ra0

and see if its successful.  Also, its sort of a long shot, see it there is now a "/etc/sysconfig/network" folder on your machine.  One of the kde apps you tried may have tried to setup your wireless using that method.  It looks like kwirelessmonitor looks for that setup, but I'm not sure it could actually create those files.

Nope, no /etc/sysconfig/network file.  The closest is an /etc/swscanner directory.

And I'm scared to run ifdown or ifup, 'cause as much as I'd like to figure out what I did, I want to make sure it works first and foremost, know what I mean.;)   Is there a way to check ti without shutting it on or off?

---

### Post by sy1911 on 2007-01-08
Completely understandable.  Given my level of knowledge, the only way I can think to figure this one out is to basically break it and try and fix it again.  For now though it sounds like your pretty happy to have wireless working, so it's probably best to just leave it until/if you hit another problem. 

I hope I managed to be somehow helpful. Best of luck, Steve.

---

### Post by Steve S. on 2007-01-08
> **sy1911 said:**
> Completely understandable.  Given my level of knowledge, the only way I can think to figure this one out is to basically break it and try and fix it again.  For now though it sounds like your pretty happy to have wireless working, so it's probably best to just leave it until/if you hit another problem. 

I hope I managed to be somehow helpful. Best of luck, Steve.

Oh, clearly you helped, my friend!  The fact that we couldn't figure out how doesn't matter quite so much as that we got it fixed!  Thanks again, and best to you as well!:-D

---

