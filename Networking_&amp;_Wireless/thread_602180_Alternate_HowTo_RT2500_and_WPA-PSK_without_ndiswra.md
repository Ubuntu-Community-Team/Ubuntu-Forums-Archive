---
title: "Alternate HowTo: RT2500 and WPA-PSK without ndiswrapper -- Ubuntu 7.10 Gutsy"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by xshakakee on 2007-11-04
This is a tutorial (or HowTo, or what-have-you) for setting up a new install of Ubuntu 7.10 Gusty Gibbon using rt2500 pci flavored wireless 802.11g card.  Here is my system setup:

[B]UPDATE(2007/11/05): I should tell you that I am using the i386 version of Ubuntu 7.10: ubuntu-7.10-desktop-i386.iso
END UPDATE[/B]

AMD Sempron 2800+, socket 754
Asus K8V-VM, one of those on-board everything boards
512 MB Kingston DDR400 RAM
160 gig Maxtor HDD
RT2500 PCI card.  Belkin 7000, version 3

When Ubuntu 7.10 is first installed, it loads up the incorrect driver.  If you
```

depmod | grep rt2500
```
you should get a line that says:
```

rt2500pci              19072  0 
rt2x00pci              11520  1 rt2500pci
rt2x00lib              19584  2 rt2500pci,rt2x00pci
mac80211              171016  4 rc80211_simple,rt2500pci,rt2x00pci,rt2x00lib
eeprom_93cx6            3200  1 rt2500pci

```
You will know, then, that the default driver will not work.  Go ahead.  Go into Network Manager and bang around all you want.
The default drivers that get loaded into Gutsy when you start are broken.  They do not work with Ralink chipsets.
It's a useful exercise, regardless, because mucking about in Network Manager changes/creates the /etc/network/interfaces file and /etc/resolv.config file.  You don't need to know anything about these, right now.  You will be modifying these later.

I ripped most of my instructions off from [[COLOR="SandyBrown"]_this post_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3595458&postcount=6").

Also, check [[COLOR="SandyBrown"]_this_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500") out.
Instruction #1 from the first guide was to pull down ra2500-source.  I could not do that.  Edit your sources list.
```

sudo gedit /etc/apt/sources.list
```
Make it look something like this:
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free license. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy universe multiverse

# WICD repository

deb http://apt.wicd.net gutsy extras

#	If you get an error about missing keys
#	run the following commands, replacing KEY with
#	the actual number of the key.

#	gpg &#8211;keyserver subkeys.pgp.net &#8211;recv KEY
# 	gpg &#8211;export &#8211;armor KEY | sudo apt-key add - 

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu gutsy universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse


## Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

## Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
#deb ftp://cipherfunk.org/pub/packages/ubuntu/ gutsy main

## Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
#deb-src ftp://cipherfunk.org/pub/packages/ubuntu gutsy main

## Penguin Liberation Front (packages)
#deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ gutsy free non-free

## Penguin Liberation Front (sources)
#deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ gutsy free non-free

```

You might want to comment out the first line, or you'll be asked to put the cd-rom in the drive when you can't find a package from the main-line repositories (happened when I tried to download the kernel headers, an unnecessary step).
If you want to include the Cipherfunk and Penguin Liberation Front packages, be my guest.  They aren't necessary for this tutorial, but they come in useful once you start expanding your Ubuntu use.
OK, once you've made your changes to sources.lst, you need to update:```

sudo apt-get update
```
Oh, and for those of you who hate to type sudo all the time, just go into terminal and type:
```

sudo su

```
Enter your password at the prompt, and leave that terminal open.
Any time you need to code anything, just copy the part after "sudo".  It really saves time.

Start on your wired network.  If you have dhcp enabled, this should be a cinch.  You probably don't even need to go into Network Manager.  I did so anyway, just to look at my defaults.

Besides, I had some messed up network settings, to begin with.
First, I ran: 
```

sudo cp /etc/network/interfaces /etc/network/interfaces.bak
sudo gedit /etc/network/interfaces

```
and making it look like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.4
netmask 255.255.255.0
gateway 192.168.2.1

```

I'm not going to go over what to do if networking fails once you plug in the wire.  If you need a tutorial on that, go back to /etc/network/interfaces and change it back to your original settings.
[B]Update(2007/11/05): Suggestion by kevdog.
Before I start downloading new sources, I need to bring in the build-essentials package.[/B]
```
sudo apt-get install build-essential
```
**End Update**

OK, from here you can either type:
```
 sudo apt-get install rt2500-source
```
** UPDATE: Some users have experienced problems with this method, for safety's sake, do the SerialMonkey method, below.**
or:

Go to the [[COLOR="SandyBrown"]_Serial Monkey_[/COLOR]]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") website.

I went to the Serial Monkey Website, went to Downloads, and pulled down the legacy rt2500 driver, which in my case was
 
rt2500-cvs-2007102623

**Do Not Download the Beta!**
The beta driver will not compile, on a default install of the OS.  You get all these dependency errors.  The CVS compiled nicely.
```

tar -xvzf rt2500-cvs-daily.tar.gz
cd rt2500-cvs-2007102623/Module
make
sudo make install

```
OK, once you have either apt-get installed or compiled your own module, you can do the following:
```

echo "blacklist rt2500pci" >> /etc/modprobe.d/blacklist
echo rt2500 >> /etc/modules

```
Also, for some reason, I like to copy the module into the same folder as the other rt2500 module:** UPDATE: Sorry, this will not work until the module has been added into the modules directory, or turned on somehow.**
```
sudo cp /lib/modules/2.6.22-14-generic/extra/rt2500.ko /lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/

```
**Update: do the following instead:**
```

sudo modprobe -r rt2500pci
sudo modprobe rt2500
lsmod | grep rt2500

```
Don't think the following is necessary.
> I honestly do no know if this makes any difference.  I like to cover my bases.

**UPDATE(2007/11/05): suggestion by kevdog.  Get WICD first, then remove Network Manager. END UPDATE**
I added WICD through the Synaptic package manager, following the instructions [[COLOR="SandyBrown"]_here_[/COLOR]]("http://wicd.sourceforge.net/download.php").

Turns out, I didn't actually use it to set up my network, but it is a handy network monitor; a good Network Manager surrogate.

What seems to have worked, from this point onward, was going back to:
```

sudo gedit /etc/network/interfaces

```
and adding the following lines, in red:
```

auto lo
iface lo inet loopback

#auto eth0[COLOR="Red"]
iface eth0 inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.2.2
gateway 192.168.2.1
dns-nameservers <ip address of nameserver1>, <ip address of nameserver2>
netmask 255.255.255.0

pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "My SSID"
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="my preshared key"
pre-up ifconfig wlan0 up
[/COLOR]
```
As you can see, I destroyed the eth0 portion, as well as adding
an entirely new portion, the wlan0.
**UPDATE(2007/11/05) suggestion by kevdog.  Remove Network Manager only after WICD installed and people are able to get out on the net, wired connection**
Next, Uninstalled networking manager
```

sudo apt-get remove network-manager-gnome

```
I restarted at this point, not knowing how to remove modules and add them on the fly.

Once I did that, I had a network conflict, since I was still plugged into the wired.

A better method would have been to use the following code:
```

sudo ifconfig wlan0 down
sudo modprobe -r rt2500pci
sudo modprobe rt2500

```
Then, in order to make my wired ethernet disappear:
```

sudo gedit /etc/network/interfaces

```
and edit the file so that it looks like this:
```

auto lo
iface lo inet loopback

[COLOR="Red"]#[/COLOR]auto eth0
iface eth0 inet static
address 192.168.2.4
netmask 255.255.255.0
gateway 192.168.2.1

```
Last step, at this phase, is to restart the network:
```

sudo /etc/init.d/networking restart

```

OK -- but still no network!  What gives?  Let's be patient, shall we?
You probably need to just run this:
```
sudo ifconfig wlan0 down
sudo modprobe -r rt2500pci
sudo modprobe rt2500
sudo depmod
sudo ifconfig wlan0 up
```

**END UPDATE**

Once I ran: ```
sudo /etc/init.d/networking restart
```

it all came up.  I rebooted a couple of times, and the changes seemed to have taken.

[B]UPDATE(2007/11/05) The following is perhaps unnecessary banter:> One caveat: I have a card with little blinking lights in the back, so I know when it is active.  (I actually have the USB version of this adapter, and love it because it blinks at me when active.  It's on the Mac, though.)  At some point, the lights are going to go off.  I got frustrated with this several times, and thought, what am I doing wrong?  I solved it (I think) by using various iterations of the following code:
```

sudo ifconfig wlan0 down
sudo modprobe -r rt2500pci
sudo depmod
sudo modprobe rt2500
sudo depmod

```
I ran this, and ran the restart script, and the adapter seems to have kicked in.  It takes a minute for that last depmod to kick in.  Just be patient.

**UPDATE(2007/11/05) Suggestion by kevdog.  You will only need to do this if you do not have dhcp enabled, and you are unable to get out on the net.  I had this problem when I first came up on the net.  I could type in numerical requests, but couldn't resolve names.  This should be a pretty rare situation.END UPDATE**
Also, you *may* need to modify your resolv.conf.  I did because I got rid of network manager before I could even create this file.  Therefore, my machine did not know where to go for DNS resolution.  Here's how you do it.
```

sudo gedit /etc/resolv.conf

```
Make sure the following lines are in there:
```

nameserver 208.67.220.220
nameserver 208.67.220.222

```
That's all.  The OpenDNS servers are all you need.  You can also pull the nameservers from your cable/dsl provider, but I find it easier just to stick with these two.

That's it!  Fire up WICD, restart your network:
```

sudo /etc/init.d/networking restart

```
and you should be on the way!

I will attempt to post a version of this using the USB adapter and RutilT.  I don't think I'll be doing much more, because I lack the hardware to test every case.

---

### Post by MrHyde on 2007-11-04
I tried following your instructions and hit a wall.

I installed rt2500-source using apt-get.  The next step says to copy extra/rt2500.ko to the other folder.  However, the extra folder does not exist and I have searched the whole filesystem for rt2500.ko and it does not exist anywhere.

Also, when I ran depmod, it returns nothing at all.

I have a fresh install of Gutsy on a AMD64 motherboard and have a rt2500 PCI wireless card that I am trying to get working.

---

### Post by xshakakee on 2007-11-05
Hmm...it looks like the rt2500-source install doesn't install anything, in particular.

I would stick to the serialmonkey install.  You should be able to see a rt2500.ko when you make and make install the serialmonkey cvs.

It's weird, because [[COLOR="SandyBrown"]_this guy_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3595458&postcount=6") said using the rt2500-source would be a cinch.

Well, you need to ```

sudo modprobe -r rt2500pci
sudo modprobe rt2500
depmod
```

anyway.  Might be a good idea to also do this:```

sudo su
echo rt2500 >> /etc/modules
```

This ought to place the rt2500.ko in the correct spot.

Well, sorry about the confusion.  I'll check my sources next time, and hopefully, you won't be left in the lurch.

---

### Post by xshakakee on 2007-11-05
One last request, Mr. Hyde.  Can you post the results of your locate rt2500 command?

Try doing this:```

locate rt2500 > list.txt
```

Open up your home folder, and look for a file called list.txt.  Open that, Select All, and Paste into the Reply to Thread window.  I know it will be huge, but I'd like to know just what
apt-get install rt2500-source does.

Here's mine for comparison:```

/usr/share/app-install/desktop/rt2500.desktop
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.22-14-generic/extra/rt2500.ko
/home/user1/rt2500
/home/user1/rt2500/THANKS
/home/user1/rt2500/Utilitys
/home/user1/rt2500/Utilitys/ico
/home/user1/rt2500/Utilitys/ico/CVS
/home/user1/rt2500/Utilitys/ico/CVS/Repository
/home/user1/rt2500/Utilitys/ico/CVS/Entries
/home/user1/rt2500/Utilitys/ico/CVS/Root
/home/user1/rt2500/Utilitys/CVS
/home/user1/rt2500/Utilitys/CVS/Repository
/home/user1/rt2500/Utilitys/CVS/Entries.Log
/home/user1/rt2500/Utilitys/CVS/Entries
/home/user1/rt2500/Utilitys/CVS/Root
/home/user1/rt2500/FAQ
/home/user1/rt2500/CVS
/home/user1/rt2500/CVS/Repository
/home/user1/rt2500/CVS/Entries.Log
/home/user1/rt2500/CVS/Entries
/home/user1/rt2500/CVS/Root
/home/user1/rt2500/Module
/home/user1/rt2500/Module/wpa.o
/home/user1/rt2500/Module/docs
/home/user1/rt2500/Module/docs/CVS
/home/user1/rt2500/Module/docs/CVS/Repository
/home/user1/rt2500/Module/docs/CVS/Entries
/home/user1/rt2500/Module/docs/CVS/Root
/home/user1/rt2500/Module/rt2500.o
/home/user1/rt2500/Module/.rtmp_wep.o.cmd
/home/user1/rt2500/Module/eeprom.c
/home/user1/rt2500/Module/auth.o
/home/user1/rt2500/Module/.sanity.o.cmd
/home/user1/rt2500/Module/README
/home/user1/rt2500/Module/.wpa.o.cmd
/home/user1/rt2500/Module/.tmp_versions
/home/user1/rt2500/Module/.tmp_versions/rt2500.mod
/home/user1/rt2500/Module/rtmp_init.c
/home/user1/rt2500/Module/rtmp_info.c
/home/user1/rt2500/Module/sanity.c
/home/user1/rt2500/Module/rt2x00debug.c
/home/user1/rt2500/Module/rt2x00debug.o
/home/user1/rt2500/Module/rtmp_main.c
/home/user1/rt2500/Module/.auth.o.cmd
/home/user1/rt2500/Module/mlme.h
/home/user1/rt2500/Module/md5.h
/home/user1/rt2500/Module/rtmp_data.c
/home/user1/rt2500/Module/rt2x00debug.h
/home/user1/rt2500/Module/.md5.o.cmd
/home/user1/rt2500/Module/.rtmp_main.o.cmd
/home/user1/rt2500/Module/rtmp_tkip.c
/home/user1/rt2500/Module/mlme.c
/home/user1/rt2500/Module/TESTING
/home/user1/rt2500/Module/.rtmp_init.o.cmd
/home/user1/rt2500/Module/.assoc.o.cmd
/home/user1/rt2500/Module/rt2500.mod.c
/home/user1/rt2500/Module/rtmp_main.o
/home/user1/rt2500/Module/RT2500STA.dat
/home/user1/rt2500/Module/.rt2500.ko.cmd
/home/user1/rt2500/Module/.sync.o.cmd
/home/user1/rt2500/Module/.rtmp_info.o.cmd
/home/user1/rt2500/Module/2.6.x
/home/user1/rt2500/Module/2.6.x/CVS
/home/user1/rt2500/Module/2.6.x/CVS/Repository
/home/user1/rt2500/Module/2.6.x/CVS/Entries
/home/user1/rt2500/Module/2.6.x/CVS/Root
/home/user1/rt2500/Module/rtmp_wep.c
/home/user1/rt2500/Module/.rtmp_data.o.cmd
/home/user1/rt2500/Module/md5.o
/home/user1/rt2500/Module/rtmp_type.h
/home/user1/rt2500/Module/auth_rsp.c
/home/user1/rt2500/Module/.rt2500.mod.o.cmd
/home/user1/rt2500/Module/.eeprom.o.cmd
/home/user1/rt2500/Module/CVS
/home/user1/rt2500/Module/CVS/Repository
/home/user1/rt2500/Module/CVS/Entries.Log
/home/user1/rt2500/Module/CVS/Entries
/home/user1/rt2500/Module/CVS/Root
/home/user1/rt2500/Module/rtmp_data.o
/home/user1/rt2500/Module/ifcfg-ra0
/home/user1/rt2500/Module/rt2560.h
/home/user1/rt2500/Module/oid.h
/home/user1/rt2500/Module/sanity.o
/home/user1/rt2500/Module/rt_config.h
/home/user1/rt2500/Module/wpa.c
/home/user1/rt2500/Module/sync.o
/home/user1/rt2500/Module/iwpriv_usage.txt
/home/user1/rt2500/Module/auth_rsp.o
/home/user1/rt2500/Module/.mlme.o.cmd
/home/user1/rt2500/Module/eeprom.o
/home/user1/rt2500/Module/rtmp_info.o
/home/user1/rt2500/Module/connect.c
/home/user1/rt2500/Module/auth.c
/home/user1/rt2500/Module/sync.c
/home/user1/rt2500/Module/.connect.o.cmd
/home/user1/rt2500/Module/.rt2x00debug.o.cmd
/home/user1/rt2500/Module/rtmp_def.h
/home/user1/rt2500/Module/.auth_rsp.o.cmd
/home/user1/rt2500/Module/rtmp.h
/home/user1/rt2500/Module/rtmp_init.o
/home/user1/rt2500/Module/connect.o
/home/user1/rt2500/Module/md5.c
/home/user1/rt2500/Module/Makefile
/home/user1/rt2500/Module/rt2500.mod.o
/home/user1/rt2500/Module/assoc.c
/home/user1/rt2500/Module/.rt2500.o.cmd
/home/user1/rt2500/Module/rt2500.ko
/home/user1/rt2500/Module/2.4.x
/home/user1/rt2500/Module/2.4.x/CVS
/home/user1/rt2500/Module/2.4.x/CVS/Repository
/home/user1/rt2500/Module/2.4.x/CVS/Entries
/home/user1/rt2500/Module/2.4.x/CVS/Root
/home/user1/rt2500/Module/assoc.o
/home/user1/rt2500/Module/mlme.o
/home/user1/rt2500/Module/rtmp_wep.o
/home/user1/rt2500/Module/.rtmp_tkip.o.cmd
/home/user1/rt2500/Module/rtmp_tkip.o
/home/user1/rt2500/Module/Module.symvers
/home/user1/rt2500/Module/wpa.h
/home/user1/rt2500/LICENSE
/home/user1/rt2500/CHANGELOG

```

Thanks.

---

### Post by kevdog on 2007-11-05
Nice instructions, but basically you are telling everyone to download and install the serial monkey rt2500 driver in leiu of the built in driver and use OpenDNS for the dhcp server (this part is unnecessary for many).

You need to include in your instructions that for people to do this they need the :
#1 - Build-essential package installed
#2- Linux header package - linux-headers-`uname -r`

With these commands:
> sudo ifconfig wlan0 down
sudo modprobe -r rt2500pci
sudo depmod
sudo modprobe rt2500
sudo depmod


The last module dependency statement is unnecessary.

Kudos for uninstalling network manager.   Once you uninstall this however there might be a problem with people connecting to the internet to download the wicd package.  You might want to mention this.  Also if in a jam, I believe people can connect manually from the command line to gain internet access if its necessary.

Other than that I would mention the OpenDNS server step is optional 

Very good tutorial.

---

### Post by xshakakee on 2007-11-05
Thanks, kevdog.  Notice taken.  Also, I didn't have to separately download essential-packages, for some reason.  I used Synaptic to pull down WICD, and at some point, and the dependencies all got rolled in.

I'm still trying to figure out what apt-get install rt2500-source does.
I know it asks me to pop in the cd, so maybe the kernel headers get installed in that step.

As far as I can tell, this step creates a rt2500.tar.bz2 file in /usr/src, but doesn't unpack it.

Then again, I had serialmonkey drivers already installed, so unpacking the .tar.bz2 file would probably not be a good thing.  At any rate, I'll post a cleaned up version of this tute (unless you all want me to shut up until I've learned more about this).

I plan on re-installing from scratch on a Socket A machine (sorry, AMD fanboi here).

Oh, and the only reason I suggest that people download drivers, as opposed to using native drivers, is that the native drivers don't work.  I checked out posts by wieman01 and odiseo77 and basically synthesized on top of those.  I just wanted to incorporate everything I learned into one tute, so that people didn't have to go bouncing around the forums looking for the answer.  Of course, I solve only one, very specific problem.

How to get 2500 pci network card working on an AMD Sempron, i386 version of Ubuntu 7.10.  It doesn't address usb adapter (I have one, I just have to pry it from the Mac user in the house), or AMD64 version of Ubuntu (I am not a "power user" so 32-bit is adequate).  I also don't address Intel or Multi-Core cpu's.  I don't think the cpu type makes that big a difference, for this issue.  Certainly, there seem to be issues with the 64-bit versions of Linux, generally, and I don't feel comfortable making that leap, since I am still in the relatively low-tech game (now where did I put that socket 7 board?)  Anyway, enough chat.

Thanks for the help everyone.  I'll definitely clean up my act before my next post.

---

### Post by Sebxoii on 2007-11-10
Hi everyone,

First of all, thanks a lot xshakakee, I finally managed to get a working connection.

I still have a tiny problem : when I reboot, I have to type these 3 lines to have my wifi back :

	sudo iwconfig wlan0 essid xxxx key xxxxxxxxxxxxxxxxx
	sudo /etc/init.d/networking restart
	sudo dhclient

I don't know what the problem is precisely, but it seems to me that the drivers are loaded, but when I type "ifconfig", the wlan0 interface doesn't show up.

How do you think I should do to make it work without having to do that every time ? I thought about doing a little script and launching it at startup, but I guess there must be a better way to do that ?

Thanks in advance.

Sébastien.

---

### Post by Sebxoii on 2007-11-10
The solution was in the driver's README :

```
If you want for rt2500 driver to auto-load at boot time:
A) choose ra0 for first RT2500 WLAN card, ra1 for second RT2500 WLAN
   card, etc.

B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2500

C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0
   DEVICE='ra0'
   ONBOOT='yes'


NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'
```

edit : Well, it does work on startup, but the connection is down after 5-10mn. After that time, I have to type 
```
sudo ifup wlan0
sudo ifdown wlan0
sudo iwconfig wlan0 essid xxxx key xxxxxxxxxx
sudo /etc/init.d/networking restart
```
Anyone got an idea why it does that ?

---

### Post by WernerBrandt on 2007-11-11
YES!

Got it working, thanks alot man!

Note:
I use an Rt2500 USb device, but I replaced all rt2500 by rt2570 more or less
(The 2500 usb is an 2570 @ serial monkey

---

### Post by Jehu on 2007-12-09
In my case the solution was to follow these instructions in the README-file (directory "Module" of the cvs-Package):
-8<---------------------------------------------------------------------
Configuration File : RT2500STA.dat

# Copy this file to /etc/Wireless/RT2500STA/RT2500STA.dat
# This file is a binary file and will be read on loading rt2500.o
# module.
-8<---------------------------------------------------------------------
and so on....

After setting up this file my card works fine.

---

