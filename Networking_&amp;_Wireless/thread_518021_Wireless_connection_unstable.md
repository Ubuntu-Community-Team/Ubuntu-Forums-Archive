---
title: "Wireless connection unstable"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by Trash_Gordon on 2007-08-05
Hi,
I am sort of new in Ubuntu and it took me a long time to get my Fritz! USB WLAN Stick with ndiswrapper running and connection to the AP with WPA encryption. I tried on many Howtos, wikis, and so on, but [your description]("http://ubuntuforums.org/showthread.php?t=318539") was the only one that worked. So I was pretty happy the first time.
But here's the problem: After a random amount of time (sometimes it's 5 minutes, sometimes 2 hours, but sooner or later it always happens), I just get disconnected from the network. Reconnection doesn't work most of the time, but when it does, it doesn't last long. I usually have to restart, but sometimes that it's working either. When I get kicked off the network, dmesg shows the following:
```
[ 7072.352000] ndiswrapper (NdisWriteErrorLogEntry:231): log: C000138A, count: 0, return_address: f8f82c2f
[ 7075.528000] ndiswrapper (iw_get_network_type:306): getting network type failed: C0010011
[ 7075.528000] ndiswrapper (iw_get_network_type:306): getting network type failed: C0010011
[same thing for 20 lines]
[ 7079.476000] ndiswrapper (NdisWriteErrorLogEntry:231): log: C000138A, count: 0, return_address: f8f82c2f
[ 7082.584000] ndiswrapper (iw_get_network_type:306): getting network type failed: C0010011
```
This stuff repeats about 5 times then. Everything I found on the web was [this]("http://kanotix.com/PNphpBB2-viewtopic-t-20612.html") in a German forum, but the solution (change the channel) shouldn't work because it works fine on Windows. Can you help me?
Thanks in advance.

---

### Post by kevdog on 2007-08-05
What version of ndiswrapper are you using?? Since you have an internet connection its possible to upgrade to the svn version -- not sure if it will work, but worth a shot!

---

### Post by Trash_Gordon on 2007-08-05
```
root@adrian:/home/adrian# ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 
```

OK, I guess I'm going to update. Are there binaries out there or do I have to compile it myself? If I compile it myself, do I remove the old ndiswrapper first?

---

### Post by Snipersnest on 2007-08-05
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

The version your using sounds like the packaged version. NDISwrapper is currently upto version 1.48

You may try removing your old packaged one and compiling a new NDISwrapper from scratch.  Its not a painful procedure.

---

### Post by kevdog on 2007-08-05
If you have an internet connection, I would upgrade to svn (since you can download it)

Here are some instructions to get you started

[SIZE="4"]**SVN INSTALLATION -- Part I -- requires an internet connection**[/SIZE]
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install subversion build-essential linux-headers-`uname -r`

```
Subversion is the utility that we can use to download the svn version of ndiswrapper.  The other two packages are so we can compile from source.

Ok lets grab the ndiswrapper svn sources and compile (but not install them):
```

cd ~
svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper ~/ndiswrapper_svn
cd ndiswrapper_svn
svn up
make distclean
make
```

**[SIZE="4"]Ndiswrapper Uinstall Instructions[/SIZE]**
Ok before installing the new ndiswrapper packages we need to uninstall the old version completely. Dont worry if some of these commands dont do anything or seem not to work -- some may be repetitive.

```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo rmmod ndiswrapper
sudo rm -rf /etc/ndiswrapper/*
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```

[SIZE="4"]**SVN INSTALLATION -- Part II -- internet connection is down**[/SIZE]
Ok that should have about killed the old ndiswrapper version.  Now lets install the new version:
```
cd ~/ndiswrapper_svn
sudo make install
```

Timeout:
Check if everything went OK
```
ndiswrapper -v
```
This should return version 1.48rc1 or something similar. 
[SIZE="4"][B]
Ndiswrapper Instructions -- You may follow a different procedure based on your setup[/B][/SIZE]
Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running.

---

### Post by Trash_Gordon on 2007-08-05
WOW!!
First of all, a BIT thanks for the huge walkthrough. Unfortunately, I'm hanging at one point, and that is SVN installation Part I. I installed SVN and checked out  ndiswrapper, but if I do make distclean or make I get:
```
adrian@adrian:~/ndiswrapper_svn$ make distclean
make: *** Keine Regel, um »distclean« zu erstellen.  Schluss.

```("No rule to create "distclean"). The same for "make". Is this OK:```
adrian@adrian:~/ndiswrapper_svn$ svn up
Revision 2433.

```

---

### Post by kevdog on 2007-08-06
Hmm, thats weird -- looks like you might not be in the right directory (or possible my directions just suck)

Hmm maybe I should have done this first since:

```
cd ~
**mkdir ndiswrapper_svn**
svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper ~/ndiswrapper_svn
cd ndiswrapper_svn
svn up
make distclean
make
```

My ndiswrapper_svn directory contains:
AUTHORS, ChangeLog, driver, INSTALL, loadndisdriver.8, Makefile, ndiswrapper.8, ndiswrapper.spec, README, utils

Im currently on revision 2433

Check your directory structure, since I think I forgot one line!

---

### Post by Trash_Gordon on 2007-08-06
> **kevdog said:**
> 
My ndiswrapper_svn directory contains:
AUTHORS, ChangeLog, driver, INSTALL, loadndisdriver.8, Makefile, ndiswrapper.8, ndiswrapper.spec, README, utils


Nope,

```
adrian@adrian:~/ndiswrapper_svn$ ls
branches  tags  trunk

```

Edit: It works with```
adrian@adrian:~$ svn co https://ndiswrapper.svn.sourceforge.net/svnroot/ndiswrapper/trunk/ndiswrapper ~/ndiswrapper_svn/

```

Now I've got the same files as you. According to the changelog, it is version 1.48

---

### Post by Trash_Gordon on 2007-08-06
OK, I just followed your instructions with the files I got from svn.
Everything went well, until modprobe ndiswrapper: [http://pastebin.com/f4790a775]("http://pastebin.com/f4790a775"). dmesg gives  [this]("http://pastebin.com/m1cd9128")
depmod -a still doesn't give error messages, but there is no wlan0 configured, even after ndiswrapper -m. After the restart, when I insert the stick, the computer just beeps.  [tail -f /var/log/messages]("http://pastebin.com/f4790a775"). 
That doesn't seem right...

---

### Post by Snipersnest on 2007-08-06
Does anything come up in your iwconfig?

---

### Post by Trash_Gordon on 2007-08-06
Only lo and eth0

---

### Post by kevdog on 2007-08-06
When I see the words:
```
#
Segmentation fault
```

In the output you gave me -- that cant mean anything good.  Its weird because I downloaded, compiled, and installed the svn version just last night.  Worked out for me. 

Want I would do in this case is to uninstall the svn version.
Go into the directory where you issued the make command and type
sudo make uninstall

I would then just download the 1.48rc1.tar.gz file (its precompiled) from here and try this version:
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

Your the first person I know of thats tried the svn version and failed.

---

### Post by Trash_Gordon on 2007-08-06
OK, I installed the version from sourceforge, but I get the same problems, ndiswrapper -m just gives me "configuration file already contains alias directive". If I plug the stick in, it beeps and gives out the same problems as before. Why can't the Ubuntu repository contain current ndiswrapper binaries? It would be soooo much easier.

---

### Post by kevdog on 2007-08-06
I had to review your post to fill in some details.

Are the errors you are getting the same as you posted in #2??

Also you mentioned you were using a usb stick, but never told us what type of USB stick, or the chipset of the device.  I guess I should have asked this a long time ago.

---

### Post by Trash_Gordon on 2007-08-06
Well, I wrote it in the first message...
> **Trash_Gordon said:**
> 
I am sort of new in Ubuntu and it took me a long time to get my **Fritz! USB WLAN Stick** with ndiswrapper running and connection to the AP with WPA encryption.
There are drivers from the manufacturer for this one, but I didn't use them because I already got it running with ndiswrapper. The Error messages are the same as in the svn version.
[Here ]("http://www.avm.de/de/Produkte/FRITZBox/FRITZ_WLAN_USB_Stick/index.html##")are some description to the stick. It's German but it's understandable.

---

### Post by kevdog on 2007-08-06
Dont happen to know the chipset of this device??  If its an ra chipset, you probably shouldnt be using ndiswrapper anyway.

---

### Post by Trash_Gordon on 2007-08-07
I don't think it has a ra chipset because a lot of people have it running with ndiswrapper and there are many howtos for the stick out there recommending the use of ndiswrapper. The Stick is very popular here, as many ISPs give it away as free hardware and the company is known for good quality. I'll probably try to install the official drivers from avm, although they are very new. Hopefully it works.

---

