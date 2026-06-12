---
title: "Atheros AR5212 Madwifi HowTo"
date: 2005-06-02
forum: Networking &amp; Wireless
---

### Post by elvis on 2005-06-02
I purchased myself a Netgear WG511T network card based on the recommendation of this page:

[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)

Which incorrectly states it works "out of the box" with Hoary.  It does no such thing.

lspci gives me:
```
0000:06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

Long story short, Hoary ships with ath_hal 0.9.12.14, which is too old.  Hopefully this mini-guide will help others upgrade and get wireless working.

If your wireless isn't working, at a console type "dmesg | less".  Scroll around and search for the string starting with "ath_hal".  If you see something like: 

ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212)  HAL status 13

The "HAL Status 13" bit means your card is not supported by the current drivers, and you need to upgrade.

The laptop I was working on was quite old, and had no onboard LAN.  So this guide assumes nothing more than the Hoary install CD, and the following files:

1) GNU sharutils - needed for uudecode for the madwifi driver install:
[ftp://ftp.gnu.org/gnu/sharutils/REL-4.3.80/sharutils-4.3.80.tar.gz](ftp://ftp.gnu.org/gnu/sharutils/REL-4.3.80/sharutils-4.3.80.tar.gz)

2) The latest madwifi snapshot:
[http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)

I downloaded these on a internet-capable PC, and copied them to my laptop via USB pendrive and "sneakernet".

To build, we need the GNU C Compiler, gcc.  At a prompt (represented by "#") I type:

```

# sudo su
# apt-get update
# apt-get install make gcc g++

```

You'll need the Hoary cdrom inserted for the above, and most of the following.

Purists will probably tell me "sudo su" is naughty, but with no web access anyway, it isn't much of a security risk. :)

You may recieve warnings here that packages cannot be verified.  It's safe to ignore these for now.

Madwifi compiles against your currently installed kernel.  For this, we also need kernel headers.  The command 
```
# uname -r
```
tells me the kernel I have installed.  For me, that's "2.6.10-5-386".  Now to grab the correct headers:

```

# apt-get install linux-headers-2.6.10-5-386

```

APT also installs linux-headers-2.6.10.  Note this, because we need to fix a problem this causes later.

So now I untar my two files I downloaded

```

# tar xvzf sharutils-4.3.80.tar.gz
# tar xvzf madwifi-cvs-current.tar.gz

```

First, I build sharutils, which installs the "uudecode" program I need for madwifi

```

# cd sharutils-4.3.80
# ./configure
# make
# make install
# cd ..

```

Once done, I build madwifi.  Madwifi incorrectly detects my kernel as "2.6.10" and not "2.6.10-5-386" and will build against the wrong headers.  To fix this, we need to export some variables.  Again, change these to match your installed kernel (found via the 'uname -r' command).

```

# cd madwifi
# export KERNELPATH=/usr/src/linux-2.6.10-5-386
# export KERNELRELEASE=2.6.10-5-386
# make
# make install

```

The new madwifi drivers should now be built and installed.  At this stage, I ejected the Haory CDROM and rebooted my machine.

After reboot, dmesg now says:

```

wlan: 0.8.4.5 (EXPERIMENTAL)
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)

```

Notice the jump to ath_hal 0.9.14.9 from the old 0.9.12.14.

Now I can click System -> Administration -> Networking and my wireless network card appears as "ath0" which I can configure as normal with all my usual ESSID, WEP and IP information.

I'm assuming the next test release of Ubuntu will include the updated Madwifi drivers, but I hope in the short term this helps a few people getting theirs up and running.  I see these forums are littered with folks failing to get their wireless working, which is frustrating especially after you've purchased hardware based on an official hardware compatability list, which is supposedly the clever thing to do.

---

### Post by jaykay on 2005-06-10
Here is a simple and easy way to get the Netgear Wg511T card up and running in easy steps. In 5 minutes you will be up and running.

1. start up a root console

2.type: **iwconfig** ( this will give you your card info and network /wireless info)

3. type: **iwconfig ath0 channel 6** ( substitute channel 6 for whichever channel your router is transmitting on)

4. Type: **iwlist scan** ( this may take a minute, this will give you your routers wireless settings.)

5. Type: **iwconfig ath0 essid xxxxxx** ( replace xxxxxx with your routers essid)

6. Type: **iwconfig ath0 ap xx xx xx xx xx xx**( this is the six double digit mac address required and is listed in your iwlist scan message as above.)

7. Type: **iwconfig ath0 key XXXXXXXXXX** ( replace XXXXXXXX with your own hex wep key )

8. type: **dhclient** ( this gets your dhcp sorted ) you should now be up and running.

All of the information you need is right on the screen, although  you will need to make a note of your wep key from your routers settings, as the output above may list it only as a ******** output .

Hope this helps some one.

I have testd this on various linux systems and it appears to work fine including live CDs.

One thing to note if you are using a knoppix system step 8 above will not work but you can replace it with the following command 

step 8: type: **pump -i ath0**

Good Luck 

Jaykay

---

### Post by IcemanV9 on 2005-06-16
UPDATED: I realized (uname -r) confused many newbies. So, I changed it to reflect a correct syntax - `uname -r`; so that you can copy and paste.

Your info does help me to resolve the problem with my new cardbus adapter, D-Link DWL-G650.

Here's what I did:

wget [http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz](http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz)
sudo apt-get install build-essential (only if you don't have it)
sudo apt-get install linux-headers-`uname -r` (again, only if you don't have it)
sudo apt-get install sharutils

tar xvzf madwifi-cvs-current.tar.gz
cd madwifi
KERNELPATH=/usr/src/linux-headers-`uname -r`; export KERNELPATH
KERNELRELEASE=`uname -r`; export KERNELRELEASE
sudo make
sudo make install

sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko.orig
sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko.orig
sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko.orig

sudo cp /lib/modules/2.6.10-5-686/net/ath_rate_onoe.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko
sudo cp /lib/modules/2.6.10-5-686/net/ath_hal.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko
sudo cp /lib/modules/2.6.10-5-686/net/ath_pci.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko

reboot (leave your cardbus in the slot)

when boot up, it will recongize the cardbus adapter (without an error message)!

To TEST ath0, I just used some commands from jaykay's instruction. AND, it works great.

---

### Post by rlklee on 2005-06-18
When following the instructions given by Elvis, I get this repeated error on the  "make" command for madwifi:


#make
Checking if all requirements are met,,, ok.
mkdir -p ./symbols
for i in ./ath_hal ath_rate/onoe ./net80211 ./ath; do \
     (cd $i; make) | | exit 1; \
done
make[1]: Entering directory '/home/rlklee/Desktop/madwifi/ath_hal'
make -C /usr/src/linux-headers-2.6.10-5-386 SUBDIRS=/home/rlklee/Desktop/madwifi/ath_hal MODVERDIR=/home/rlklee/Desktop/madwifi/ath_hal../symbols modules
make[2]: Entering directory '/usr/src/linux-headers-2.6.10-5-386'
  Building modules, stage 2
  MODPOST
Warning: could not find /home/rlklee/Desktop/madwifi/ath_hal/.hal.o.cmd for /home/rlklee/Desktop/madwifi/ath_hal/hal.o


It then continues to reiterate in this same warning pattern till the end...  I'm new to the game, any help would be greatly appreciated.

---

### Post by elvis on 2005-06-18
[QUOTE=rlklee]When following the instructions given by Elvis, I get this repeated error on the  "make" command for madwifi[/QUOTE]

It looks like the build part is OK, but the scripts inside the madwifi source is giving you issues.

Perhaps try getting either a newer or older CVS snapshot and trying again.  Maybe the snapshot you have has something broken in it?

---

### Post by rlklee on 2005-06-21
Fixed the problem: 

Everyone following Elvis' instructions (which are tip-top) should make sure to uninstall the linux-restricted madwifi package (using synaptic; just seach for linux-restricted, it should be the only one to pop up).  All should be well. 

Cheers,

---

### Post by DagaZ on 2005-06-21
Using the guide of IcemanV9 I got my Netgear WG311T up and running in no-time. My bridged firewall works great!

---

### Post by doans on 2005-06-21
[QUOTE=DagaZ]Using the guide of IcemanV9 I got my Netgear WG311T up and running in no-time. My bridged firewall works great![/QUOTE]

Yes, I also got my WG311T up and running using IcemanV9 post in no time.  FYI The first post did not work for me.

---

### Post by elvis on 2005-06-24
[QUOTE=doans]Yes, I also got my WG311T up and running using IcemanV9 post in no time.  FYI The first post did not work for me.[/QUOTE]

It looks like my post is specific to people using the "-386" kernels.  People using "-686" kernels need to follow IcemanV9's instructions instead.

Again, "uname -r" will tell you which kernel you have installed.

---

### Post by doans on 2005-06-24
[QUOTE=elvis]It looks like my post is specific to people using the "-386" kernels. People using "-686" kernels need to follow IcemanV9's instructions instead.

Again, "uname -r" will tell you which kernel you have installed.[/QUOTE]

FYI I am using the k7 kernel version. Just had to change all entries from -686 to -k7. Other than that no problems.

---

### Post by elvis on 2005-06-24
[QUOTE=doans]FYI I am using the k7 kernel version. Just had to change all entries from -686 to -k7. Other than that no problems.[/QUOTE]

That makes sense, as there is little difference in "k7" and "686" asides from some "3dnow!" stuff that is far less prevalent than MMX and SSE anyway.  386 and 686 share far less in common.

It's interesting how for 686 users (and up), the installer incorrectly installs things to /lib/modules/<version>/net rather than /lib/modules/<version>/kernel/drivers/net/wireless.  I wonder if this is Ubuntu specific or Madwifi specific?  Perhaps I should point the Madwifi kids to this thread and see what they say?

---

### Post by ximkolo on 2005-06-24
i tried the shorter version cuz it was shorter anad i have an amd 64 cpu, i am still geting trouble with it.  once i type in step 3 (iwconfig ath0 channel 6) i get an error message - Error for wireless requests "set frequency" (8B04) :    SET failed on device ath0 ;  No such device-    i am not sure at all what that means or really have to do, i will greatly appreciate any help.

---

### Post by elvis on 2005-06-24
"No such device" means your driver isn't being loaded properly.  When you followed the guide, did you make sure to substitute your correct kernel location in?

---

### Post by Dmjit on 2005-06-28
I just got my Dlink DWL-G520 Rev. B working using Elvis' method with a few extra steps. Here's what I did:

First before you start, follow rlklee's suggestion to use synaptic to uninstall the linux-restricted madwifi package

I then followed Elvis' steps except I had to replace the following line:
```
# export KERNELPATH=/usr/src/linux-2.6.10-5-386
```
with this:
```
# export KERNELPATH=/usr/src/linux-headers-2.6.10-5-386
```

I then modified my /etc/network/interfaces file to configure the wireless card instead of the original ethernet card. (See interfaces file below.)

The card now showed up in system > administration > networking and I could get it to work with out encryption. Eventually I figured out that no matter how I entered the WEP key in the GUI network configuation tool, even if it seemed to accept it and the computer didn't freeze up, iwconfig didn't see it or didn't like the format of it. I also noticed the Access Point MAC address was FF:FF:FF:FF:FF:FF

If I entered the MAC address for the Access Point and WEP key manually I could get it to work until I rebooted the computer. I then deleted my WEP key from the GUI network configuation tool (I left the essid in there) and added the configuration data to the /etc/network/interfaces file. Here's what the file looks like:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep

	# I commented out the map line for the ethernet card 
	#map eth0

	# I added this line to map the wireless card	
        map ath0

# The primary network interface

# The next line was for the ethernet card again I commented it out
#iface eth0 inet dhcp

# I added the next line for the wireless card
iface ath0 inet dhcp

# The next three lines install the settings that would normally go in system > administration > networking

# Enter your essid here
wireless-essid XXXXXXXXXXXX

# Enter your WEP key using colons for 128bit WEP
wireless-key XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XX

# Enter your MAC address for your Wireless Access Point using colons
wireless-ap XX:XX:XX:XX:XX:XX

# I think I changed this next line from auto eth0
auto ath0
```


I then rebooted the machine several times to make sure it worked and I haven't had any problems. By the way, I forgot to mention I am using DHCP if that helps anyone.

Dmjit

---

### Post by benplaut on 2005-06-29
odd... i have a 5212 based card (IBM A/B/G Mini-PCI II) that worked out of the box (half worked).

unfortunately, the "stable" version of wireless-tools included with Hoary is too outdated to let the card scan (search through the madwifi mailing list, you'll see the problem mentioned everywhere), so we'll have to wait for whatever comes after breezy to have scanning. (do NOT try to compile wireless-tools from source. it WILL mess up wireless support, forcing you to reinstall).

good grounds to switch to Fedora  :roll:

---

### Post by gdcondor on 2005-07-07
with the madwifi drivers contained in hoary i had the following error when inserting my netgear WG511T :
ath%d: unable to attach hardware; HAL status 13

so I compiled the newest madwifi as explained in this howto but after the reboot i've this error (in dmesg) :
ath_pci: Unknown symbol ieee80211_getrssi

how to solve this ? :((

finally i read in the FAQ (madwifi) that you have to recompile your kernel with CONFIG_MODVERSIONS=no :((((
i don't want to recompile my kernel all the time a new version is coming out ! ...

i tried to install the sources of my kernel as i read somewhere (my kernel-headers were already installed) to try but it doesn't help (of course...)

---

### Post by gat on 2005-07-15
I'm sadly new to linux and trying to get a newish Windows laptop migrated fully to linux, and Kubuntu has, so far, been well up to the task.  My D-Link DWL-G650 was one of the last holdouts and this forum helped very much.  Thanks everybody for the good advice.

I followed IcemanV9's and jaykay's instructions, with just a few modifications:

While following Iceman's instructions, wherever the (uname -r) (in parens) was referenced, I had to use `uname -r` instead (between apostrophes (unicode hex value 0060)).

After reboot my dmesg looked good (as in elvis' post), but I couldn't get online at all.

None of jaykay's instructions would work.  Finally, I stumbled on the command:
sudo ifconfig ath0 up

Probably everybody knew that already -- but that seemed to wake up the lights on my wireless card.

Then I followed all jaykay's instructions and they were working fine with the following notes:
I had to fumble around trying different channels until I discovered that I was, like jaykay, on channel 6.  
I had to click K->Utilities->KCharSelect in order to figure out my WEP key hex (in Windows, I used a string).  
(I just clicked each character in turn, and copied down the rightmost two hexidigits for each.)
instead of dhclient I did:
sudo dhclient ath0

All the terminal readout looked perfect, but I still couldn't get online.

Finally I had the old revelation again and did:
sudo ifconfig eth0 down 

Then firefox (and konquerer) could finally hit the internet.  That was really a great feeling!

Later, I discovered I could probably have used the kubuntu graphic config utility (it does most of what jaykay's instructions mentioned).  I had tried it often during this struggle, but it failed every time:
(I clicked K->Control Center->Internet&Network->Wireless Network ... but it dumped me out every time I answered the password prompt)
Finally, I realized I could launch it from the command line with:
sudo kcmshell kcmwifi &

Thanks everyone for the great help.

---

### Post by beansbbq on 2005-07-16
[QUOTE=elvis]I purchased myself a Netgear WG511T network card based on the recommendation of this page:

[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)

Which incorrectly states it works "out of the box" with Hoary.  It does no such thing.

lspci gives me:
```
0000:06:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

Long story short, Hoary ships with ath_hal 0.9.12.14, which is too old.  Hopefully this mini-guide will help others upgrade and get wireless working.

If your wireless isn't working, at a console type "dmesg | less".  Scroll around and search for the string starting with "ath_hal".  If you see something like: 

ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212)  HAL status 13

The "HAL Status 13" bit means your card is not supported by the current drivers, and you need to upgrade.

The laptop I was working on was quite old, and had no onboard LAN.  So this guide assumes nothing more than the Hoary install CD, and the following files:

1) GNU sharutils - needed for uudecode for the madwifi driver install:
[ftp://ftp.gnu.org/gnu/sharutils/REL-4.3.80/sharutils-4.3.80.tar.gz](ftp://ftp.gnu.org/gnu/sharutils/REL-4.3.80/sharutils-4.3.80.tar.gz)

2) The latest madwifi snapshot:
[http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)

I downloaded these on a internet-capable PC, and copied them to my laptop via USB pendrive and "sneakernet".

To build, we need the GNU C Compiler, gcc.  At a prompt (represented by "#") I type:

```

# sudo su
# apt-get update
# apt-get install make gcc g++

```

You'll need the Hoary cdrom inserted for the above, and most of the following.

Purists will probably tell me "sudo su" is naughty, but with no web access anyway, it isn't much of a security risk. :)

You may recieve warnings here that packages cannot be verified.  It's safe to ignore these for now.

Madwifi compiles against your currently installed kernel.  For this, we also need kernel headers.  The command 
```
# uname -r
```
tells me the kernel I have installed.  For me, that's "2.6.10-5-386".  Now to grab the correct headers:

```

# apt-get install linux-headers-2.6.10-5-386

```

APT also installs linux-headers-2.6.10.  Note this, because we need to fix a problem this causes later.

So now I untar my two files I downloaded

```

# tar xvzf sharutils-4.3.80.tar.gz
# tar xvzf madwifi-cvs-current.tar.gz

```

First, I build sharutils, which installs the "uudecode" program I need for madwifi

```

# cd sharutils-4.3.80
# ./configure
# make
# make install
# cd ..

```

Once done, I build madwifi.  Madwifi incorrectly detects my kernel as "2.6.10" and not "2.6.10-5-386" and will build against the wrong headers.  To fix this, we need to export some variables.  Again, change these to match your installed kernel (found via the 'uname -r' command).

```

# cd madwifi
# export KERNELPATH=/usr/src/linux-2.6.10-5-386
# export KERNELRELEASE=2.6.10-5-386
# make
# make install

```

The new madwifi drivers should now be built and installed.  At this stage, I ejected the Haory CDROM and rebooted my machine.

After reboot, dmesg now says:

```

wlan: 0.8.4.5 (EXPERIMENTAL)
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)

```

Notice the jump to ath_hal 0.9.14.9 from the old 0.9.12.14.

Now I can click System -> Administration -> Networking and my wireless network card appears as "ath0" which I can configure as normal with all my usual ESSID, WEP and IP information.

I'm assuming the next test release of Ubuntu will include the updated Madwifi drivers, but I hope in the short term this helps a few people getting theirs up and running.  I see these forums are littered with folks failing to get their wireless working, which is frustrating especially after you've purchased hardware based on an official hardware compatability list, which is supposedly the clever thing to do.[/QUOTE]


Hi Elvis,


   I have the proxim card which is suppose to "just work".  It too has the Atheros chipset.  I attempted to follow your instructions to no avail.  A key difference is:

1. ath_hal:  did not appear when I ran the dmesg | less command.  
 
I have a question, do I still need to install the driver after following your instructions?  If so, where do I perform this task at?   My driver file is called nt11ag.ifi or something like that.  

Also, do I need the .sys file too?  In what directory should they reside?

Thanks,

Jonto

---

### Post by steffen on 2005-07-19
Anyone know whether this card works better with Breezy? I.e. if Hal is updated?

Have a Thinkpad X40 with the Atheros a/b/g thing.

---

### Post by davy014 on 2005-07-21
i try what iceman said, but i have this when i do "sudo make"

make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-686'
make[2]: *** No rule to make target `linux/drivers'.  Stop.
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/davy/logiciels linux/drivers linux/madwifi/madwifi/ath_hal'
make: *** [all] Erreur 1

what can i do?

thanks

davy

---

### Post by Drufuss on 2005-07-30
[QUOTE=Dmjit]I just got my Dlink DWL-G520 Rev. B working using Elvis' method with a few extra steps. Here's what I did:

First before you start, follow rlklee's suggestion to use synaptic to uninstall the linux-restricted madwifi package

I then followed Elvis' steps except I had to replace the following line:
```
# export KERNELPATH=/usr/src/linux-2.6.10-5-386
```
with this:
```
# export KERNELPATH=/usr/src/linux-headers-2.6.10-5-386
```

I then modified my /etc/network/interfaces file to configure the wireless card instead of the original ethernet card. (See interfaces file below.)

The card now showed up in system > administration > networking and I could get it to work with out encryption. Eventually I figured out that no matter how I entered the WEP key in the GUI network configuation tool, even if it seemed to accept it and the computer didn't freeze up, iwconfig didn't see it or didn't like the format of it. I also noticed the Access Point MAC address was FF:FF:FF:FF:FF:FF

If I entered the MAC address for the Access Point and WEP key manually I could get it to work until I rebooted the computer. I then deleted my WEP key from the GUI network configuation tool (I left the essid in there) and added the configuration data to the /etc/network/interfaces file. Here's what the file looks like:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep

	# I commented out the map line for the ethernet card 
	#map eth0

	# I added this line to map the wireless card	
        map ath0

# The primary network interface

# The next line was for the ethernet card again I commented it out
#iface eth0 inet dhcp

# I added the next line for the wireless card
iface ath0 inet dhcp

# The next three lines install the settings that would normally go in system > administration > networking

# Enter your essid here
wireless-essid XXXXXXXXXXXX

# Enter your WEP key using colons for 128bit WEP
wireless-key XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XX

# Enter your MAC address for your Wireless Access Point using colons
wireless-ap XX:XX:XX:XX:XX:XX

# I think I changed this next line from auto eth0
auto ath0
```


I then rebooted the machine several times to make sure it worked and I haven't had any problems. By the way, I forgot to mention I am using DHCP if that helps anyone.

Dmjit[/QUOTE]

So you can use WEP with the DLink DWL-G520 and the MadWifi drivers?

I had no luck installing the madwifi´s back in Suse (until i found out my card was supported out of the box), and it never worked with WEP enabled.

The DWL-G520 is working right now (without madwifi, but also without WEP) so i´ll try what you did.

Greetings

Dru

---

### Post by Drufuss on 2005-07-31
[QUOTE=rlklee]Fixed the problem: 

Everyone following Elvis' instructions (which are tip-top) should make sure to uninstall the linux-restricted madwifi package (using synaptic; just seach for linux-restricted, it should be the only one to pop up).  All should be well. 

Cheers,[/QUOTE]

Uninstall the linux-restricted madwifi package using synaptic? How do i uninstall only the madwifi part of it?

I can only select the whole package to be un-/installed, which consists of madwifi and fglrx and some other drivers according to its description. But i think i need the fglrx part for my X800Pro card. (Installing the ATi drivers, enabling 3d hardware acceleration is another issue i still have to solve).

Greetings

Dru

---

### Post by btsdev on 2005-08-01
I've tried to follow IcemanV9's steps on page one of this thread but unfortunately after backing up the .ko's to .ko.orig, when it comes time to cp the new .ko's in place, I get the following error:  I don't have ath_rate_onoe.ko in /lib/modules/`uname -r`/net.

Any ideas of what I may have done wrong, or any ideas of what I can do to get my wifi card working?

Thanks in advance.

---

### Post by Dmjit on 2005-08-02
[QUOTE=Drufuss]Uninstall the linux-restricted madwifi package using synaptic? How do i uninstall only the madwifi part of it?

I can only select the whole package to be un-/installed, which consists of madwifi and fglrx and some other drivers according to its description. But i think i need the fglrx part for my X800Pro card. (Installing the ATi drivers, enabling 3d hardware acceleration is another issue i still have to solve).

Greetings

Dru[/QUOTE]
 Drufuss,

I uninstalled the whole linux-restricted package. I am running an ATI 9250SE video card and I have not had any problems after doing this.

Dmjit

---

### Post by npaladin2000 on 2005-08-19
[QUOTE=benplaut]odd... i have a 5212 based card (IBM A/B/G Mini-PCI II) that worked out of the box (half worked).

unfortunately, the "stable" version of wireless-tools included with Hoary is too outdated to let the card scan (search through the madwifi mailing list, you'll see the problem mentioned everywhere), so we'll have to wait for whatever comes after breezy to have scanning. (do NOT try to compile wireless-tools from source. it WILL mess up wireless support, forcing you to reinstall).

good grounds to switch to Fedora  :roll:[/QUOTE]

My 5212 card works out of the box "sort of"  too.  Turns out that (on the wireless at work at least) the card keeps enabling and disabling itself.  Can't even see it in ifconfig or iwconfig, only on the network monitor icon in GNOME.  (For a while I thought it was needing a newer version of madwifi, then maybe some compilation problems).

Incidentally, it would be a GOOD idea for the Ubuntu developers to reduce restricted-modules to a metapackage and split the components out individually, so they can be removed/installed piece by piece.

Incidentally, I HAVE to get this working.  Stinking IBM THinkpads only accept IBM MiniPCI cards.  And I won't be buying my HP NC widescreen for a few months (probably not until breezy comes out at least).

---

### Post by epedersen on 2005-08-23
> **IcemanV9]UPDATED: I realized (uname -r) confused many newbies. So, I changed it to reflect a correct syntax - `uname -r` said:**
> http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz[/url]
sudo apt-get install build-essential (only if you don't have it)
sudo apt-get install linux-headers-`uname -r` (again, only if you don't have it)
sudo apt-get install sharutils

tar xvzf madwifi-cvs-current.tar.gz
cd madwifi
KERNELPATH=/usr/src/linux-headers-`uname -r`; export KERNELPATH
KERNELRELEASE=`uname -r`; export KERNELRELEASE
sudo make
sudo make install

sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko.orig
sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko.orig
sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko.orig

sudo cp /lib/modules/2.6.10-5-686/net/ath_rate_onoe.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko
sudo cp /lib/modules/2.6.10-5-686/net/ath_hal.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko
sudo cp /lib/modules/2.6.10-5-686/net/ath_pci.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko

reboot (leave your cardbus in the slot)

when boot up, it will recongize the cardbus adapter (without an error message)!

To TEST ath0, I just used some commands from jaykay's instruction. AND, it works great.
 Iceman V9's instructions worked great for me, even though I didn't uninstall the linux-restricted package.  (DLink DWL-G520 H/W ver B3, F/W ver 4.20)

Now to test it after disabling my onboard wired ethernet, and rebooting...!

---

### Post by joffa on 2005-08-24
Just so others know, and maybe for someone to correct me if I'm wrong, but I've tried every suggestion in this post and each time it fails at the make stage - I have amd64 and the Rev. B version of the DWL-G520 card.
On the hardware support page, it gives a link to a new restricted-modules package, but it's for 386 machines.
I then found another post (that I can't locate just now) that stated that madwifi doesn't (yet) support amd64.  Darn me buying amd64!
Does anyone know if breezy will have madwifi amd64 support?

---

### Post by joffa on 2005-08-24
Okay, should have tried this first before posting above but at least others who read this will now know - I changed my sources.list to include breezy and installed the new linux-restricted-modules-2.6.12-7amd64-generic package and hey presto my card now works.  I'm going to change my sources.list back to hoary and keep things sane.  Thanks to all who posted anything re amd64 and atheros ar5212 - it all helped.

---

### Post by escuchamezz on 2005-08-26
how exactly do I get madwifi to compile on amd64? It's giving me an error about a problem linking to an i386 file or something along those lines when i try to compile it.
How did you guys compile this?  :???:

---

### Post by unimark on 2005-08-27
i bought a netgear 511t today and followed the first set of instructions. all the makes did their thing but ath_hal: is still coming back with 0.9.12.14 and giving a status 13. 

i'm completely new at this and dont really know what is going on. what kind of output am i supposed to expect form make when i compile madwifi?

---

### Post by numberexhaust on 2005-08-28
About my netgear wg511T... i just use ndiswrapper at this point but want to switch to madwifi sometime.  Whenever I try to compile madwifi (even when ndiswrapper isn't up and running), I get the message "please enable all wireless interfaces".  I have absolutely no idea what that means, but it might be trivial for you guys.  I guess madwifi is worth a good shot.

EDIT -- btw, the netgear WG511T is a great card!

---

### Post by jkorotkin on 2005-08-29
i was following elvis's instructions to enable a wireless card with the ar5212 chipset. I have a dwl-g520 card. i'm running the 2.6.10-5-386 kernel. i'm fine until i try 

 # cd madwifi
 # export KERNELPATH=/usr/src/linux-2.6.10-5-386
 # export KERNELRELEASE=2.6.10-5-386
 # make
Makefile.inc:101: *** KERNELPATH: /usr/src/linux-2.6.10-5-386 does not exist.  Stop.

when i checked /usr/src/ there isn't anything called linux-2.6.10-5-386. there is a folder called linux-headers-2.6.10-5-386, a folder called linux-headers-2.6.10-5, and a folder called rpm. any help would be appreciated. I'm a complete newbie. thanks

---

### Post by tofudrifter on 2005-08-30
[QUOTE=btsdev]I've tried to follow IcemanV9's steps on page one of this thread but unfortunately after backing up the .ko's to .ko.orig, when it comes time to cp the new .ko's in place, I get the following error:  I don't have ath_rate_onoe.ko in /lib/modules/`uname -r`/net.

Any ideas of what I may have done wrong, or any ideas of what I can do to get my wifi card working?

Thanks in advance.[/QUOTE]

i had the same problem as you, there should be a ath_rate_sample.ko in /lib/modules/`uname -r`/net

i just copied that to ath_rate_onoe.ko and after a reboot it has detected the wireless card but i haven't had a chance to setup the wireless network yet.

---

### Post by Septor on 2005-08-30
[QUOTE=jkorotkin]i was following elvis's instructions to enable a wireless card with the ar5212 chipset. I have a dwl-g520 card. i'm running the 2.6.10-5-386 kernel. i'm fine until i try 

 # cd madwifi
 # export KERNELPATH=/usr/src/linux-2.6.10-5-386
 # export KERNELRELEASE=2.6.10-5-386
 # make
Makefile.inc:101: *** KERNELPATH: /usr/src/linux-2.6.10-5-386 does not exist.  Stop.

when i checked /usr/src/ there isn't anything called linux-2.6.10-5-386. there is a folder called linux-headers-2.6.10-5-386, a folder called linux-headers-2.6.10-5, and a folder called rpm. any help would be appreciated. I'm a complete newbie. thanks[/QUOTE]

Using:
  
  export KERNELPATH=/usr/src/linux-headers-2.6.10-5-386

should work fine.

---

### Post by unimark on 2005-08-30
this card is great, when it works right. Now, on my home wifi network, connections are constantly dropping whenever i try to do anything useful, like FTP or browse a web page. IM and ping work fine, oddly enough. Anything else nixes the connection. 

also, the system takes a while to think about "starting hotplug subsystem" at startup, usually about a minute or so. is this possibly signifying  problem?

---

### Post by blainegarrett on 2005-09-01
My Netgear card finally worked using IcemanV9's 06-16-2005 post.  THANK YOU SO MUCH.

A quick note. I did a clean install a few times while trying to get my wireless to work. Before trying the method in the main topic, I didn't do a full update and when i ran make on madwifi, I was getting errors about "please enable sysctl support". I had the bright idea to update using the extra repositories ala http://ubuntuguide.org/#extrarepositories

After I did this and updated, I no longer recieved the sysctl error. I may have done a few other updates, but I don't think they were significant. 

The original method still did not end up working, and then i tried IcemanV9's method (without doing a clean install) and it worked slick. Hurrah.

I am running a Dell Inspiron 1150 with a broadcom wireless card. This did not work, and even after following some tutorials online. I ended up buying the netgear card  since my buddy's exact same card did indeed work right out of the box in my laptop. The one i bought did not. 

Anyway, thanks for the tutorial. This was the last thing preventing me from switching to Linux. Wooooo hooooo. windows free at last. I feel like I just finally got the balls to dump an ex-girlfriend.

---

### Post by lmcthbe on 2005-09-01
I got also an DWL-G520 (H/W:B3,F/W:4.10) using AR5212 working with madwifi snapshot from today using IcemanV9's 06-16-2005 post but I had to DISABLE WEP!! 

wlan: 0.8.6.0 (EXPERIMENTAL)
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
ath_rate_sample: 1.2
ath_pci: 0.9.6.0 (EXPERIMENTAL)
ACPI: PCI interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 16
Build date: Sep  1 2005

THANKS for this great forum.

---

### Post by heatvent on 2005-09-02
Here's what I did.  I used a combo of methods because I saw some errors in the previous posts (I have a DLink DWLG520 - works now).  I am going to try to run this as a script in my home directory using the root terminal with the sharutils and madwifi tars also in my home directory.  If it works, you won't have to worry as much about changing kernel versions and can automate the process somewhat.  If this works, not bad for a noobie!

UBUNTU.. PLEASE FIX THIS IN FURTHER RELEASES SO WE DON'T HAVE TO GO THROUGH ALL OF THIS EACH TIME WE UPGRADE THE KERNEL.  THX.


> 

# Madwifi script assumes you are running in your home directory and execute in the root terminal.
# Sharutils and madwifi tar files should be copied to the home directory to be untarred and installed by this script.

# Untar files
tar xvzf sharutils-4.3.80.tar.gz
tar xvzf madwifi-cvs-current.tar.gz

# install sharutils
cd sharutils-4.3.80
./configure
make
make install

# install madwifi
cd ..
cd madwifi
KERNELPATH=/usr/src/linux-headers-`uname -r`; export KERNELPATH
KERNELRELEASE=`uname -r`; export KERNELRELEASE
make
make install

# rename old and copy new drivers
sudo mv /lib/modules/`uname -r`/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko.orig
sudo mv /lib/modules/`uname -r`/kernel/drivers/net/wireless/ath_hal/ath_hal.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/ath_hal/ath_hal.ko.orig
sudo mv /lib/modules/`uname -r`/kernel/drivers/net/wireless/ath/ath_pci.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/ath/ath_pci.ko.orig
sudo cp /lib/modules/`uname -r`/net/ath_rate_sample.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko
sudo cp /lib/modules/`uname -r`/net/ath_hal.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/ath_hal/ath_hal.ko
sudo cp /lib/modules/`uname -r`/net/ath_pci.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/ath/ath_pci.ko



---

### Post by surbiff on 2005-09-08
THANKS!!!  for the help Iceman!!!!

it worked great for me.. and it was not hard even if im a noob....

a big big thanks to you!!!

---

### Post by Magneto on 2005-09-13
[QUOTE=heatvent]Here's what I did.  I used a combo of methods because I saw some errors in the previous posts (I have a DLink DWLG520 - works now).  I am going to try to run this as a script in my home directory using the root terminal with the sharutils and madwifi tars also in my home directory.  If it works, you won't have to worry as much about changing kernel versions and can automate the process somewhat.  If this works, not bad for a noobie!

UBUNTU.. PLEASE FIX THIS IN FURTHER RELEASES SO WE DON'T HAVE TO GO THROUGH ALL OF THIS EACH TIME WE UPGRADE THE KERNEL.  THX.[/QUOTE]
 thank you - ive been through 6 installs of different distros trying to get this to work with wpa_supplicant and the frustration and back and forth between distros had me missing steps - your script helped immensely

---

### Post by zugvogel on 2005-09-19
[QUOTE=rlklee]Fixed the problem: 

Everyone following Elvis' instructions (which are tip-top) should make sure to uninstall the linux-restricted madwifi package (using synaptic; just seach for linux-restricted, it should be the only one to pop up).  All should be well. 

Cheers,[/QUOTE]

I followed Elvis' instructions which were fine up to the "make" command for madwifi. It gives the error that was mentioned earlier of

```

  MODPOST
Warning: could not find /home/james/Downloads/Wireless/madwifi/ath_hal/.hal.o.cmd for /home/james/Downloads/Wireless/madwifi/ath_hal/hal.o

```

So I tried to follow the advice from rlklee of uninstalling 

linux-restricted-modules-2.6.10-5-386

but to do that it also wants to remove

linux-386
linux-restricted-modules-386

Firstly, am I uninstalling the right package? Rlklee suggested that only one package would come up when searching for "linux-restricted", but I have two.
And secondly, is it safe to remove linux-386? It sounds quite fundamentle to me...

Thanks!

---

### Post by DagaZ on 2005-09-24
I reinstalled Ubuntu the other day and now nothing wireless works anymore. I am typing this from windoze where it do work. 
I have a Netgear WG311T rev. C according to Windoze XP the same goes for Ubuntu. 
The card gets listed in the DeviceManager in Ubuntu but it doesn't work no matter what I try. I have reinstalled the machine numerous times now and it still isn't working. The modules are there so I don't understand where the problem is really.
I have tried following both Elvis version and IceMan with no luck whatsoever. Icemans version worked for me when I first got the card.

Any clues anyone? Is there something new in Hoary? This might be HAL-related but it  drives me crazy. It _should_ work!

I use k7 and below is my output from dmesg

homer@linux:~$ dmesg
t version of symbol ieee80211_beacon_update
ath_pci: Unknown symbol ieee80211_beacon_update
ath_pci: disagrees about version of symbol ieee80211_ioctl_setmlme
ath_pci: Unknown symbol ieee80211_ioctl_setmlme
ath_pci: disagrees about version of symbol ieee80211_ioctl_setoptie
ath_pci: Unknown symbol ieee80211_ioctl_setoptie
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwmode
ath_pci: Unknown symbol ieee80211_ioctl_giwmode
ath_pci: Unknown symbol ieee80211_find_rxnode
ath_pci: disagrees about version of symbol ath_rate_attach
ath_pci: Unknown symbol ath_rate_attach
ath_pci: disagrees about version of symbol ieee80211_ifdetach
ath_pci: Unknown symbol ieee80211_ifdetach
ath_pci: disagrees about version of symbol ieee80211_free_node
ath_pci: Unknown symbol ieee80211_free_node
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwsens
ath_pci: Unknown symbol ieee80211_ioctl_siwsens
ath_pci: disagrees about version of symbol ath_rate_newassoc
ath_pci: Unknown symbol ath_rate_newassoc
ath_pci: disagrees about version of symbol ieee80211_notify_michael_failure
ath_pci: Unknown symbol ieee80211_notify_michael_failure
ath_pci: disagrees about version of symbol ieee80211_ioctl_chanlist
ath_pci: Unknown symbol ieee80211_ioctl_chanlist
ath_pci: disagrees about version of symbol ieee80211_ioctl_getparam
ath_pci: Unknown symbol ieee80211_ioctl_getparam
ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrate
ath_pci: Unknown symbol ieee80211_ioctl_giwrate
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwrts
ath_pci: Unknown symbol ieee80211_ioctl_siwrts
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwname
ath_pci: Unknown symbol ieee80211_ioctl_giwname
ath_pci: disagrees about version of symbol ieee80211_cipher_none
ath_pci: Unknown symbol ieee80211_cipher_none
ath_pci: disagrees about version of symbol ieee80211_ioctl_setparam
ath_pci: Unknown symbol ieee80211_ioctl_setparam
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwpower
ath_pci: Unknown symbol ieee80211_ioctl_siwpower
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwsens
ath_pci: Unknown symbol ieee80211_ioctl_giwsens
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwfreq
ath_pci: Unknown symbol ieee80211_ioctl_giwfreq
ath_pci: disagrees about version of symbol ieee80211_beacon_alloc
ath_pci: Unknown symbol ieee80211_beacon_alloc
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwfrag
ath_pci: Unknown symbol ieee80211_ioctl_siwfrag
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwap
ath_pci: Unknown symbol ieee80211_ioctl_giwap
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwfreq
ath_pci: Unknown symbol ieee80211_ioctl_siwfreq
ath_pci: Unknown symbol ieee80211_ibss_merge
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwpower
ath_pci: Unknown symbol ieee80211_ioctl_giwpower
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrange
ath_pci: Unknown symbol ieee80211_ioctl_giwrange
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwretry
ath_pci: Unknown symbol ieee80211_ioctl_giwretry
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwnickn
ath_pci: Unknown symbol ieee80211_ioctl_giwnickn
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrts
ath_pci: Unknown symbol ieee80211_ioctl_giwrts
ath_pci: disagrees about version of symbol ieee80211_iw_getstats
ath_pci: Unknown symbol ieee80211_iw_getstats
ath_pci: disagrees about version of symbol ieee80211_ioctl_addmac
ath_pci: Unknown symbol ieee80211_ioctl_addmac
ath_pci: disagrees about version of symbol ath_rate_node_cleanup
ath_pci: Unknown symbol ath_rate_node_cleanup
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwfrag
ath_pci: Unknown symbol ieee80211_ioctl_giwfrag
ath_pci: Unknown symbol ieee80211_wme_acnames
ath_pci: disagrees about version of symbol ieee80211_vlan_kill_vid
ath_pci: Unknown symbol ieee80211_vlan_kill_vid
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwencode
ath_pci: Unknown symbol ieee80211_ioctl_giwencode
ath_pci: disagrees about version of symbol ieee80211_next_scan
ath_pci: Unknown symbol ieee80211_next_scan
ath_pci: disagrees about version of symbol ieee80211_media_init
ath_pci: Unknown symbol ieee80211_media_init
ath_pci: disagrees about version of symbol ieee80211_ioctl
ath_pci: Unknown symbol ieee80211_ioctl
ath_pci: disagrees about version of symbol ieee80211_ioctl_delmac
ath_pci: Unknown symbol ieee80211_ioctl_delmac
ath_pci: Unknown symbol ieee80211_classify
ath_pci: disagrees about version of symbol ieee80211_announce
ath_pci: Unknown symbol ieee80211_announce
ath_pci: disagrees about version of symbol ieee80211_ioctl_setkey
ath_pci: Unknown symbol ieee80211_ioctl_setkey
ath_pci: disagrees about version of symbol ieee80211_ioctl_iwaplist
ath_pci: Unknown symbol ieee80211_ioctl_iwaplist
ath_pci: disagrees about version of symbol ieee80211_ioctl_delkey
ath_pci: Unknown symbol ieee80211_ioctl_delkey
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwtxpow
ath_pci: Unknown symbol ieee80211_ioctl_siwtxpow
ath_pci: disagrees about version of symbol ieee80211_chan2ieee
ath_pci: Unknown symbol ieee80211_chan2ieee
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwretry
ath_pci: Unknown symbol ieee80211_ioctl_siwretry
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwnickn
ath_pci: Unknown symbol ieee80211_ioctl_siwnickn
ath_pci: disagrees about version of symbol ath_rate_node_init
ath_pci: Unknown symbol ath_rate_node_init
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwscan
ath_pci: Unknown symbol ieee80211_ioctl_siwscan
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwmode
ath_pci: Unknown symbol ieee80211_ioctl_siwmode
ath_pci: disagrees about version of symbol ieee80211_ioctl_getoptie
ath_pci: Unknown symbol ieee80211_ioctl_getoptie
ath_pci: disagrees about version of symbol ath_rate_findrate
ath_pci: Unknown symbol ath_rate_findrate
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwessid
ath_pci: Unknown symbol ieee80211_ioctl_giwessid
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwscan
ath_pci: Unknown symbol ieee80211_ioctl_giwscan
ath_pci: disagrees about version of symbol ieee80211_crypto_encap
ath_pci: Unknown symbol ieee80211_crypto_encap
ath_pci: disagrees about version of symbol ieee80211_vlan_register
ath_pci: Unknown symbol ieee80211_vlan_register
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwessid
ath_pci: Unknown symbol ieee80211_ioctl_siwessid
ath_pci: disagrees about version of symbol ieee80211_chan2mode
ath_pci: Unknown symbol ieee80211_chan2mode
ath_pci: Unknown symbol ieee80211_getrssi
ath_pci: Unknown symbol ieee80211_pwrsave
ath_pci: Unknown symbol ieee80211_find_txnode
ath_pci: disagrees about version of symbol ath_rate_newstate
ath_pci: Unknown symbol ath_rate_newstate
ath_pci: disagrees about version of symbol ath_rate_setupxtxdesc
ath_pci: Unknown symbol ath_rate_setupxtxdesc
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwtxpow
ath_pci: Unknown symbol ieee80211_ioctl_giwtxpow
ath_rate_sample: disagrees about version of symbol ieee80211_iterate_nodes
ath_rate_sample: Unknown symbol ieee80211_iterate_nodes
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwrate
ath_pci: Unknown symbol ieee80211_ioctl_siwrate
ath_pci: disagrees about version of symbol ath_rate_tx_complete
ath_pci: Unknown symbol ath_rate_tx_complete
ath_pci: disagrees about version of symbol ieee80211_encap
ath_pci: Unknown symbol ieee80211_encap
ath_pci: disagrees about version of symbol ieee80211_input
ath_pci: Unknown symbol ieee80211_input
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwap
ath_pci: Unknown symbol ieee80211_ioctl_siwap
ath_pci: disagrees about version of symbol ieee80211_ifattach
ath_pci: Unknown symbol ieee80211_ifattach
ath_pci: Unknown symbol if_printf
ath_pci: disagrees about version of symbol ieee80211_sysctl_register
ath_pci: Unknown symbol ieee80211_sysctl_register
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwencode
ath_pci: Unknown symbol ieee80211_ioctl_siwencode
ath_pci: disagrees about version of symbol ieee80211_beacon_update
ath_pci: Unknown symbol ieee80211_beacon_update
ath_pci: disagrees about version of symbol ieee80211_ioctl_setmlme
ath_pci: Unknown symbol ieee80211_ioctl_setmlme
ath_pci: disagrees about version of symbol ieee80211_ioctl_setoptie
ath_pci: Unknown symbol ieee80211_ioctl_setoptie
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwmode
ath_pci: Unknown symbol ieee80211_ioctl_giwmode
ath_pci: Unknown symbol ieee80211_find_rxnode
ath_pci: disagrees about version of symbol ath_rate_attach
ath_pci: Unknown symbol ath_rate_attach
ath_pci: disagrees about version of symbol ieee80211_ifdetach
ath_pci: Unknown symbol ieee80211_ifdetach
ath_pci: disagrees about version of symbol ieee80211_free_node
ath_pci: Unknown symbol ieee80211_free_node
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwsens
ath_pci: Unknown symbol ieee80211_ioctl_siwsens
ath_pci: disagrees about version of symbol ath_rate_newassoc
ath_pci: Unknown symbol ath_rate_newassoc
ath_pci: disagrees about version of symbol ieee80211_notify_michael_failure
ath_pci: Unknown symbol ieee80211_notify_michael_failure
ath_pci: disagrees about version of symbol ieee80211_ioctl_chanlist
ath_pci: Unknown symbol ieee80211_ioctl_chanlist
ath_pci: disagrees about version of symbol ieee80211_ioctl_getparam
ath_pci: Unknown symbol ieee80211_ioctl_getparam
ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrate
ath_pci: Unknown symbol ieee80211_ioctl_giwrate
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwrts
ath_pci: Unknown symbol ieee80211_ioctl_siwrts
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwname
ath_pci: Unknown symbol ieee80211_ioctl_giwname
ath_pci: disagrees about version of symbol ieee80211_cipher_none
ath_pci: Unknown symbol ieee80211_cipher_none
ath_pci: disagrees about version of symbol ieee80211_ioctl_setparam
ath_pci: Unknown symbol ieee80211_ioctl_setparam
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwpower
ath_pci: Unknown symbol ieee80211_ioctl_siwpower
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwsens
ath_pci: Unknown symbol ieee80211_ioctl_giwsens
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwfreq
ath_pci: Unknown symbol ieee80211_ioctl_giwfreq
ath_pci: disagrees about version of symbol ieee80211_beacon_alloc
ath_pci: Unknown symbol ieee80211_beacon_alloc
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwfrag
ath_pci: Unknown symbol ieee80211_ioctl_siwfrag
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwap
ath_pci: Unknown symbol ieee80211_ioctl_giwap
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwfreq
ath_pci: Unknown symbol ieee80211_ioctl_siwfreq
ath_pci: Unknown symbol ieee80211_ibss_merge
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwpower
ath_pci: Unknown symbol ieee80211_ioctl_giwpower
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrange
ath_pci: Unknown symbol ieee80211_ioctl_giwrange
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwretry
ath_pci: Unknown symbol ieee80211_ioctl_giwretry
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwnickn
ath_pci: Unknown symbol ieee80211_ioctl_giwnickn
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrts
ath_pci: Unknown symbol ieee80211_ioctl_giwrts
ath_pci: disagrees about version of symbol ieee80211_iw_getstats
ath_pci: Unknown symbol ieee80211_iw_getstats
ath_pci: disagrees about version of symbol ieee80211_ioctl_addmac
ath_pci: Unknown symbol ieee80211_ioctl_addmac
ath_pci: disagrees about version of symbol ath_rate_node_cleanup
ath_pci: Unknown symbol ath_rate_node_cleanup
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwfrag
ath_pci: Unknown symbol ieee80211_ioctl_giwfrag
ath_pci: Unknown symbol ieee80211_wme_acnames
ath_pci: disagrees about version of symbol ieee80211_vlan_kill_vid
ath_pci: Unknown symbol ieee80211_vlan_kill_vid
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwencode
ath_pci: Unknown symbol ieee80211_ioctl_giwencode
ath_pci: disagrees about version of symbol ieee80211_next_scan
ath_pci: Unknown symbol ieee80211_next_scan
ath_pci: disagrees about version of symbol ieee80211_media_init
ath_pci: Unknown symbol ieee80211_media_init
ath_pci: disagrees about version of symbol ieee80211_ioctl
ath_pci: Unknown symbol ieee80211_ioctl
ath_pci: disagrees about version of symbol ieee80211_ioctl_delmac
ath_pci: Unknown symbol ieee80211_ioctl_delmac
ath_pci: Unknown symbol ieee80211_classify
ath_pci: disagrees about version of symbol ieee80211_announce
ath_pci: Unknown symbol ieee80211_announce
ath_pci: disagrees about version of symbol ieee80211_ioctl_setkey
ath_pci: Unknown symbol ieee80211_ioctl_setkey
ath_pci: disagrees about version of symbol ieee80211_ioctl_iwaplist
ath_pci: Unknown symbol ieee80211_ioctl_iwaplist
ath_pci: disagrees about version of symbol ieee80211_ioctl_delkey
ath_pci: Unknown symbol ieee80211_ioctl_delkey
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwtxpow
ath_pci: Unknown symbol ieee80211_ioctl_siwtxpow
ath_pci: disagrees about version of symbol ieee80211_chan2ieee
ath_pci: Unknown symbol ieee80211_chan2ieee
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwretry
ath_pci: Unknown symbol ieee80211_ioctl_siwretry
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwnickn
ath_pci: Unknown symbol ieee80211_ioctl_siwnickn
ath_pci: disagrees about version of symbol ath_rate_node_init
ath_pci: Unknown symbol ath_rate_node_init
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwscan
ath_pci: Unknown symbol ieee80211_ioctl_siwscan
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwmode
ath_pci: Unknown symbol ieee80211_ioctl_siwmode
ath_pci: disagrees about version of symbol ieee80211_ioctl_getoptie
ath_pci: Unknown symbol ieee80211_ioctl_getoptie
ath_pci: disagrees about version of symbol ath_rate_findrate
ath_pci: Unknown symbol ath_rate_findrate
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwessid
ath_pci: Unknown symbol ieee80211_ioctl_giwessid
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwscan
ath_pci: Unknown symbol ieee80211_ioctl_giwscan
ath_pci: disagrees about version of symbol ieee80211_crypto_encap
ath_pci: Unknown symbol ieee80211_crypto_encap
ath_pci: disagrees about version of symbol ieee80211_vlan_register
ath_pci: Unknown symbol ieee80211_vlan_register
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwessid
ath_pci: Unknown symbol ieee80211_ioctl_siwessid
ath_pci: disagrees about version of symbol ieee80211_chan2mode
ath_pci: Unknown symbol ieee80211_chan2mode
ath_pci: Unknown symbol ieee80211_getrssi
ath_pci: Unknown symbol ieee80211_pwrsave
ath_pci: Unknown symbol ieee80211_find_txnode
ath_pci: disagrees about version of symbol ath_rate_newstate
ath_pci: Unknown symbol ath_rate_newstate
ath_pci: disagrees about version of symbol ath_rate_setupxtxdesc
ath_pci: Unknown symbol ath_rate_setupxtxdesc
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwtxpow
ath_pci: Unknown symbol ieee80211_ioctl_giwtxpow

---

### Post by hebrew on 2005-09-28
hi there
being relatively new to linux and having switched to ubuntu from suse 9.3 (i am loving it by the way), i decided to go wireless
i have the netgear WG311T pci card and have followed the instructions in this thread but catn seem to get anything working :confused:
i am running an 386 machine and i tried to uninstall the linux-restricted modules but that left me without the xserver and i had to reinstall the nvidia drivers which are bundled into the linux-restricted modules....
BTW i am running hoary hedgehog.....
i seem to have installed the driver i just cant get it to work?????
not sure what to post here but i will put up what a few commands show
if i type lspci i get the card showing
> 0000:00:0f.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
if i type modprobe ath_pci i get
> WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.10-5-386/net/ath_rate_sample.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath_pci (/lib/modules/2.6.10-5-386/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

so i type dmesg i get (be prepared it is long :D)

> mbol ath_hal_computetxtime
ath_pci: disagrees about version of symbol ieee80211_notify_michael_failure
ath_pci: Unknown symbol ieee80211_notify_michael_failure
ath_pci: disagrees about version of symbol ieee80211_ioctl_chanlist
ath_pci: Unknown symbol ieee80211_ioctl_chanlist
ath_pci: disagrees about version of symbol ieee80211_ioctl_getparam
ath_pci: Unknown symbol ieee80211_ioctl_getparam
ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrate
ath_pci: Unknown symbol ieee80211_ioctl_giwrate
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwrts
ath_pci: Unknown symbol ieee80211_ioctl_siwrts
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwname
ath_pci: Unknown symbol ieee80211_ioctl_giwname
ath_pci: disagrees about version of symbol ath_hal_detach
ath_pci: Unknown symbol ath_hal_detach
ath_pci: disagrees about version of symbol ieee80211_cipher_none
ath_pci: Unknown symbol ieee80211_cipher_none
ath_pci: disagrees about version of symbol ieee80211_ioctl_setparam
ath_pci: Unknown symbol ieee80211_ioctl_setparam
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwpower
ath_pci: Unknown symbol ieee80211_ioctl_siwpower
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwsens
ath_pci: Unknown symbol ieee80211_ioctl_giwsens
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwfreq
ath_pci: Unknown symbol ieee80211_ioctl_giwfreq
ath_pci: disagrees about version of symbol ieee80211_beacon_alloc
ath_pci: Unknown symbol ieee80211_beacon_alloc
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwfrag
ath_pci: Unknown symbol ieee80211_ioctl_siwfrag
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwap
ath_pci: Unknown symbol ieee80211_ioctl_giwap
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwfreq
ath_pci: Unknown symbol ieee80211_ioctl_siwfreq
ath_pci: Unknown symbol ieee80211_ibss_merge
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwpower
ath_pci: Unknown symbol ieee80211_ioctl_giwpower
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrange
ath_pci: Unknown symbol ieee80211_ioctl_giwrange
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwretry
ath_pci: Unknown symbol ieee80211_ioctl_giwretry
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwnickn
ath_pci: Unknown symbol ieee80211_ioctl_giwnickn
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrts
ath_pci: Unknown symbol ieee80211_ioctl_giwrts
ath_pci: disagrees about version of symbol ieee80211_iw_getstats
ath_pci: Unknown symbol ieee80211_iw_getstats
ath_pci: disagrees about version of symbol ieee80211_ioctl_addmac
ath_pci: Unknown symbol ieee80211_ioctl_addmac
ath_pci: disagrees about version of symbol ath_rate_node_cleanup
ath_pci: Unknown symbol ath_rate_node_cleanup
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwfrag
ath_pci: Unknown symbol ieee80211_ioctl_giwfrag
ath_pci: Unknown symbol ieee80211_wme_acnames
ath_pci: disagrees about version of symbol ieee80211_vlan_kill_vid
ath_pci: Unknown symbol ieee80211_vlan_kill_vid
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwencode
ath_pci: Unknown symbol ieee80211_ioctl_giwencode
ath_pci: disagrees about version of symbol ieee80211_next_scan
ath_pci: Unknown symbol ieee80211_next_scan
ath_pci: disagrees about version of symbol ieee80211_media_init
ath_pci: Unknown symbol ieee80211_media_init
ath_pci: disagrees about version of symbol ieee80211_ioctl
ath_pci: Unknown symbol ieee80211_ioctl
ath_pci: disagrees about version of symbol ieee80211_ioctl_delmac
ath_pci: Unknown symbol ieee80211_ioctl_delmac
ath_pci: Unknown symbol ieee80211_classify
ath_pci: disagrees about version of symbol ieee80211_announce
ath_pci: Unknown symbol ieee80211_announce
ath_pci: disagrees about version of symbol ieee80211_ioctl_setkey
ath_pci: Unknown symbol ieee80211_ioctl_setkey
ath_pci: disagrees about version of symbol ieee80211_ioctl_iwaplist
ath_pci: Unknown symbol ieee80211_ioctl_iwaplist
ath_pci: disagrees about version of symbol ieee80211_ioctl_delkey
ath_pci: Unknown symbol ieee80211_ioctl_delkey
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwtxpow
ath_pci: Unknown symbol ieee80211_ioctl_siwtxpow
ath_pci: disagrees about version of symbol ieee80211_chan2ieee
ath_pci: Unknown symbol ieee80211_chan2ieee
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwretry
ath_pci: Unknown symbol ieee80211_ioctl_siwretry
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwnickn
ath_pci: Unknown symbol ieee80211_ioctl_siwnickn
ath_pci: disagrees about version of symbol ath_rate_node_init
ath_pci: Unknown symbol ath_rate_node_init
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwscan
ath_pci: Unknown symbol ieee80211_ioctl_siwscan
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwmode
ath_pci: Unknown symbol ieee80211_ioctl_siwmode
ath_pci: disagrees about version of symbol ieee80211_ioctl_getoptie
ath_pci: Unknown symbol ieee80211_ioctl_getoptie
ath_pci: disagrees about version of symbol ath_rate_findrate
ath_pci: Unknown symbol ath_rate_findrate
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwessid
ath_pci: Unknown symbol ieee80211_ioctl_giwessid
ath_pci: disagrees about version of symbol ath_hal_init_channels
ath_pci: Unknown symbol ath_hal_init_channels
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwscan
ath_pci: Unknown symbol ieee80211_ioctl_giwscan
ath_pci: disagrees about version of symbol ieee80211_crypto_encap
ath_pci: Unknown symbol ieee80211_crypto_encap
ath_pci: disagrees about version of symbol ieee80211_vlan_register
ath_pci: Unknown symbol ieee80211_vlan_register
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwessid
ath_pci: Unknown symbol ieee80211_ioctl_siwessid
ath_pci: disagrees about version of symbol ieee80211_chan2mode
ath_pci: Unknown symbol ieee80211_chan2mode
ath_pci: Unknown symbol ieee80211_getrssi
ath_pci: Unknown symbol ieee80211_pwrsave
ath_pci: Unknown symbol ieee80211_find_txnode
ath_pci: disagrees about version of symbol ath_rate_newstate
ath_pci: Unknown symbol ath_rate_newstate
ath_pci: disagrees about version of symbol ath_rate_setupxtxdesc
ath_pci: Unknown symbol ath_rate_setupxtxdesc
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwtxpow
ath_pci: Unknown symbol ieee80211_ioctl_giwtxpow
ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
ath_pci: Unknown symbol ath_hal_getwirelessmodes
ath_rate_sample: disagrees about version of symbol ath_hal_computetxtime
ath_rate_sample: Unknown symbol ath_hal_computetxtime
ath_rate_sample: disagrees about version of symbol ieee80211_iterate_nodes
ath_rate_sample: Unknown symbol ieee80211_iterate_nodes
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwrate
ath_pci: Unknown symbol ieee80211_ioctl_siwrate
ath_pci: disagrees about version of symbol ath_rate_tx_complete
ath_pci: Unknown symbol ath_rate_tx_complete
ath_pci: disagrees about version of symbol ieee80211_encap
ath_pci: Unknown symbol ieee80211_encap
ath_pci: disagrees about version of symbol ieee80211_input
ath_pci: Unknown symbol ieee80211_input
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwap
ath_pci: Unknown symbol ieee80211_ioctl_siwap
ath_pci: disagrees about version of symbol ieee80211_ifattach
ath_pci: Unknown symbol ieee80211_ifattach
ath_pci: disagrees about version of symbol _ath_hal_attach
ath_pci: Unknown symbol _ath_hal_attach
ath_pci: Unknown symbol if_printf
ath_pci: disagrees about version of symbol ieee80211_sysctl_register
ath_pci: Unknown symbol ieee80211_sysctl_register
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwencode
ath_pci: Unknown symbol ieee80211_ioctl_siwencode
ath_pci: disagrees about version of symbol ieee80211_beacon_update
ath_pci: Unknown symbol ieee80211_beacon_update
ath_pci: disagrees about version of symbol ieee80211_ioctl_setmlme
ath_pci: Unknown symbol ieee80211_ioctl_setmlme
ath_pci: disagrees about version of symbol ieee80211_ioctl_setoptie
ath_pci: Unknown symbol ieee80211_ioctl_setoptie
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwmode
ath_pci: Unknown symbol ieee80211_ioctl_giwmode
ath_pci: Unknown symbol ieee80211_find_rxnode
ath_pci: disagrees about version of symbol ath_rate_attach
ath_pci: Unknown symbol ath_rate_attach
ath_pci: disagrees about version of symbol ieee80211_ifdetach
ath_pci: Unknown symbol ieee80211_ifdetach
ath_pci: disagrees about version of symbol ieee80211_free_node
ath_pci: Unknown symbol ieee80211_free_node
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwsens
ath_pci: Unknown symbol ieee80211_ioctl_siwsens
ath_pci: disagrees about version of symbol ath_rate_newassoc
ath_pci: Unknown symbol ath_rate_newassoc
ath_pci: disagrees about version of symbol ath_hal_computetxtime
ath_pci: Unknown symbol ath_hal_computetxtime
ath_pci: disagrees about version of symbol ieee80211_notify_michael_failure
ath_pci: Unknown symbol ieee80211_notify_michael_failure
ath_pci: disagrees about version of symbol ieee80211_ioctl_chanlist
ath_pci: Unknown symbol ieee80211_ioctl_chanlist
ath_pci: disagrees about version of symbol ieee80211_ioctl_getparam
ath_pci: Unknown symbol ieee80211_ioctl_getparam
ath_pci: Unknown symbol ath_rate_dynamic_sysctl_register
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrate
ath_pci: Unknown symbol ieee80211_ioctl_giwrate
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwrts
ath_pci: Unknown symbol ieee80211_ioctl_siwrts
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwname
ath_pci: Unknown symbol ieee80211_ioctl_giwname
ath_pci: disagrees about version of symbol ath_hal_detach
ath_pci: Unknown symbol ath_hal_detach
ath_pci: disagrees about version of symbol ieee80211_cipher_none
ath_pci: Unknown symbol ieee80211_cipher_none
ath_pci: disagrees about version of symbol ieee80211_ioctl_setparam
ath_pci: Unknown symbol ieee80211_ioctl_setparam
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwpower
ath_pci: Unknown symbol ieee80211_ioctl_siwpower
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwsens
ath_pci: Unknown symbol ieee80211_ioctl_giwsens
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwfreq
ath_pci: Unknown symbol ieee80211_ioctl_giwfreq
ath_pci: disagrees about version of symbol ieee80211_beacon_alloc
ath_pci: Unknown symbol ieee80211_beacon_alloc
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwfrag
ath_pci: Unknown symbol ieee80211_ioctl_siwfrag
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwap
ath_pci: Unknown symbol ieee80211_ioctl_giwap
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwfreq
ath_pci: Unknown symbol ieee80211_ioctl_siwfreq
ath_pci: Unknown symbol ieee80211_ibss_merge
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwpower
ath_pci: Unknown symbol ieee80211_ioctl_giwpower
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrange
ath_pci: Unknown symbol ieee80211_ioctl_giwrange
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwretry
ath_pci: Unknown symbol ieee80211_ioctl_giwretry
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwnickn
ath_pci: Unknown symbol ieee80211_ioctl_giwnickn
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwrts
ath_pci: Unknown symbol ieee80211_ioctl_giwrts
ath_pci: disagrees about version of symbol ieee80211_iw_getstats
ath_pci: Unknown symbol ieee80211_iw_getstats
ath_pci: disagrees about version of symbol ieee80211_ioctl_addmac
ath_pci: Unknown symbol ieee80211_ioctl_addmac
ath_pci: disagrees about version of symbol ath_rate_node_cleanup
ath_pci: Unknown symbol ath_rate_node_cleanup
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwfrag
ath_pci: Unknown symbol ieee80211_ioctl_giwfrag
ath_pci: Unknown symbol ieee80211_wme_acnames
ath_pci: disagrees about version of symbol ieee80211_vlan_kill_vid
ath_pci: Unknown symbol ieee80211_vlan_kill_vid
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwencode
ath_pci: Unknown symbol ieee80211_ioctl_giwencode
ath_pci: disagrees about version of symbol ieee80211_next_scan
ath_pci: Unknown symbol ieee80211_next_scan
ath_pci: disagrees about version of symbol ieee80211_media_init
ath_pci: Unknown symbol ieee80211_media_init
ath_pci: disagrees about version of symbol ieee80211_ioctl
ath_pci: Unknown symbol ieee80211_ioctl
ath_pci: disagrees about version of symbol ieee80211_ioctl_delmac
ath_pci: Unknown symbol ieee80211_ioctl_delmac
ath_pci: Unknown symbol ieee80211_classify
ath_pci: disagrees about version of symbol ieee80211_announce
ath_pci: Unknown symbol ieee80211_announce
ath_pci: disagrees about version of symbol ieee80211_ioctl_setkey
ath_pci: Unknown symbol ieee80211_ioctl_setkey
ath_pci: disagrees about version of symbol ieee80211_ioctl_iwaplist
ath_pci: Unknown symbol ieee80211_ioctl_iwaplist
ath_pci: disagrees about version of symbol ieee80211_ioctl_delkey
ath_pci: Unknown symbol ieee80211_ioctl_delkey
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwtxpow
ath_pci: Unknown symbol ieee80211_ioctl_siwtxpow
ath_pci: disagrees about version of symbol ieee80211_chan2ieee
ath_pci: Unknown symbol ieee80211_chan2ieee
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwretry
ath_pci: Unknown symbol ieee80211_ioctl_siwretry
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwnickn
ath_pci: Unknown symbol ieee80211_ioctl_siwnickn
ath_pci: disagrees about version of symbol ath_rate_node_init
ath_pci: Unknown symbol ath_rate_node_init
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwscan
ath_pci: Unknown symbol ieee80211_ioctl_siwscan
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwmode
ath_pci: Unknown symbol ieee80211_ioctl_siwmode
ath_pci: disagrees about version of symbol ieee80211_ioctl_getoptie
ath_pci: Unknown symbol ieee80211_ioctl_getoptie
ath_pci: disagrees about version of symbol ath_rate_findrate
ath_pci: Unknown symbol ath_rate_findrate
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwessid
ath_pci: Unknown symbol ieee80211_ioctl_giwessid
ath_pci: disagrees about version of symbol ath_hal_init_channels
ath_pci: Unknown symbol ath_hal_init_channels
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwscan
ath_pci: Unknown symbol ieee80211_ioctl_giwscan
ath_pci: disagrees about version of symbol ieee80211_crypto_encap
ath_pci: Unknown symbol ieee80211_crypto_encap
ath_pci: disagrees about version of symbol ieee80211_vlan_register
ath_pci: Unknown symbol ieee80211_vlan_register
ath_pci: disagrees about version of symbol ieee80211_ioctl_siwessid
ath_pci: Unknown symbol ieee80211_ioctl_siwessid
ath_pci: disagrees about version of symbol ieee80211_chan2mode
ath_pci: Unknown symbol ieee80211_chan2mode
ath_pci: Unknown symbol ieee80211_getrssi
ath_pci: Unknown symbol ieee80211_pwrsave
ath_pci: Unknown symbol ieee80211_find_txnode
ath_pci: disagrees about version of symbol ath_rate_newstate
ath_pci: Unknown symbol ath_rate_newstate
ath_pci: disagrees about version of symbol ath_rate_setupxtxdesc
ath_pci: Unknown symbol ath_rate_setupxtxdesc
ath_pci: disagrees about version of symbol ieee80211_ioctl_giwtxpow
ath_pci: Unknown symbol ieee80211_ioctl_giwtxpow
ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes
ath_pci: Unknown symbol ath_hal_getwirelessmodes


ahhhh i haev totally ocnfused my self so if anyone can offer any suggestions as to what i can do please fire away
thanks

hebrew

---

### Post by goupil on 2005-10-12
hi there.
I'm having the exact same problem with "recent" madwifi versions (starting from 08-2005). When I switch back to an older version, everything is fine, and the ath_* modules load perfectly. I've been looking for a solution for a few hours now, and didn't find anything. It might be a problem with the kernel version, (I'm using hoary as well), I'll give breezy a try tomorrow and post my results here.

---

### Post by goupil on 2005-10-13
got it to work with breezy !
I don't know exactly what did the trick, but I noticed that breezy default setup uses ath_rate_sample instead of ath_rate_onoe. I compiled this module manually, copied all the modules in the madwifi subdir in the kernel sources and it worked like a charm (with madwifi-cvs-20051008 ).
Maybe the error was just due to this missing ath_rate_sample, but I won't switch back to hoary to tell you guys :)

hmm...
Actually it seemed to work...
I rebooted and have the same error, I think I was still using the old ath_pci module, not the new one.
 
OK I think I found the problem : it appears to be a pb with modules dependencies : if I simply try a "modprobe ath_pci" I've got the error. If I try :

modprobe wlan
modprobe ath_hal
modprobe ath_rate_sample
modprobe ath_pci

everything's fine

---

### Post by hebrew on 2005-10-15
cool so i will try installing an older version of the madwifi drivers and see how i go
thanks

---

### Post by CaptainMorgan on 2005-10-16
Great thread..

I seem to have some progress. I followed jaykays post and after running dhclient I get "No DHCPOFFER received. No working leases in persisten database - sleeping." 

I have no idea what that means, any suggestions? 

I haven't tried the madwifi route, but I think I will next if this doesn't work.

---

### Post by mcasanovas on 2005-10-19
Hei people!

With the first two posts I manage to configure my AR5212. Now my linux recongnizes it. Great.

But I come to another problem. My card detect the wifi-net but i can't get in. Our domestic network uses WPA and when I try to configure the password, it just give me  option for WEP.

Any idea?

Thanks!

Marc Casanovas

---

### Post by 8086 on 2005-10-21
[QUOTE=mcasanovas]
Our domestic network uses WPA and when I try to configure the password, it just give me  option for WEP.

Any idea?

[/QUOTE]

How is this for an idea?
```

root# apt-cache search wpa
hostapd - user space IEEE 802.11 AP and IEEE 802.1X/WPA/WPA2/EAP Authenticator
mcp-plugins - LADSPA plugins designed for Alsa Modular Synth
python2.3-gadfly - SQL database and parser generator for Python 2.3
wpasupplicant - Client support for WPA and WPA2 (IEEE 802.11i)
python-gadfly - SQL database and parser generator for Python [dummy package]
python2.4-gadfly - SQL database and parser generator for Python 2.4
```

"Oh, it seems I should consider installing a few of those. Perhaps that will do the trick? Hmm..."  :confused: 

```

sudo apt-get install wpasupplicant hostapd
```
:p

---

### Post by Magneto on 2005-10-23
[QUOTE=mcasanovas]Hei people!

With the first two posts I manage to configure my AR5212. Now my linux recongnizes it. Great.

But I come to another problem. My card detect the wifi-net but i can't get in. Our domestic network uses WPA and when I try to configure the password, it just give me  option for WEP.

Any idea?

Thanks!

Marc Casanovas[/QUOTE]
[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

---

### Post by darth_geekus on 2005-10-26
[QUOTE=Septor]Using:
  
  export KERNELPATH=/usr/src/linux-headers-2.6.10-5-386

should work fine.[/QUOTE]

I am getting the same issue. Whether or not I use the 'headers' part it says that it does not exist. Any clues?

Chris

---

### Post by basscad on 2005-11-13
heyah

newbie with a couple of week's experience having troubles with ar5212

i followed elvis instructions, but i get the same error as rklee on make for madwifi...

...so following rlklee i uninstalled restricted packages (all of them) but i sitll get the same error:

Checking if all requirements are met... ok.
mkdir -p ./symbols
for i in ./ath_hal ath_rate/sample ./net80211 ./ath; do \
        make -C $i || exit 1; \
done
make[1]: Entering directory `/home/basscad/apps/atheros_drivers/madwifi/ath_hal'
make -C /usr/src/linux-headers-2.6.10-5-386 SUBDIRS=/home/basscad/apps/atheros_drivers/madwifi/ath_hal MODVERDIR=/home/basscad/apps/atheros_drivers/madwifi/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/basscad/apps/atheros_drivers/madwifi/ath_hal/.hal.o.cmd for /home/basscad/apps/atheros_drivers/madwifi/ath_hal/hal.o
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: Leaving directory `/home/basscad/apps/atheros_drivers/madwifi/ath_hal'

etc

anybody have any ideas??
please?

---

### Post by basscad on 2005-11-13
hmmmm...

i just rebooted and opened my network settings and... there it is. my wireless network card... workiing fine (so far)... without madwifi (whatever it is anyway)...

---

### Post by calvinpriest on 2005-11-16
I just wanted to drop a note to say that I just bought a Netgear 511T today fully expecting to have to get intimate with this tutorial, but it actually worked right out of the box!  Just plugged her in and set her up in System->Administration->Networking and away it went.

I don't see any revision number on the card, or I'd include it...

---

### Post by McSnuffy on 2005-12-02
Heh. I'm rather new to this whole wifi thing. I'm following Elvis' instructions, because I have 386 too. However, I am unable to get the kernel header through apt-get. Is anybody else having this problem? Thanks.

---

### Post by ckm on 2005-12-06
Just a word of caution to everyone:

DO NOT USE THE MADWIFI-NG DRIVERS

Use the Madwifi-old drivers.  The new NG drivers break most or all of the userspace utilities by requiring cards to be setup using wlanconfig BEFORE iwconfig or anything else can even see them.

I'm sure that in due time NG will be integrated with the Ubuntu setup scripts, but right now it's just a little nightmare that only took me 4 hours to figure out....

Chris.

---

### Post by hil on 2005-12-26
Chris, can you post your experience with the madwifi-ng driver? I read about the driver. It could do access point and station mode simultaneously. It is amazing in the features. If you can tell the madwifi-ng developer team about the problems you encountered in using their driver, it would be great. Atheros chip has the old driver built into the ubuntu kernel. My atheros card worked right after I plugged it in. I only had to do ifconfig first before iwlist ath0 scan. Does anyone know why ifconfig ath0 IP_ADDR should be done first; otherwise it complains "Resource temporarily unavailable"?

---

### Post by steffen on 2005-12-27
Should this card be working with Breezy?

Just tried installing Breezy from scratch on a Thinkpad X41, and although I can find a network ESSID (using WEP) and even connect to it and get an IP address from DHCP. However, I'm not able to connect to the network or the internet.

I know it should work, as I just installed and connected Breezy on another laptop to the same router, and had no trouble. Just seems to be a problem with the Atheros driver (which should have been fixed for Breezy).

---

### Post by hil on 2005-12-27
steffen:
please give more details about your situation. What's the result of iwconfig? Does lsmod show the madwifi driver loaded? What's the dmesg kernel output right after you insert the card? You might do ifconfig ath0 10.0.0.77 for the card to search the closest access point and connect to it first. I have to do that before I can do iwlist ath0 scan.

---

### Post by MrJavalava on 2006-02-06
[QUOTE=ckm]Just a word of caution to everyone:

DO NOT USE THE MADWIFI-NG DRIVERS

Use the Madwifi-old drivers.  The new NG drivers break most or all of the userspace utilities by requiring cards to be setup using wlanconfig BEFORE iwconfig or anything else can even see them.

I'm sure that in due time NG will be integrated with the Ubuntu setup scripts, but right now it's just a little nightmare that only took me 4 hours to figure out....

Chris.[/QUOTE]

Listen to Chris.
I have a Thinkpad T41p which uses a intel bg wlan card. Breezy doesn't have the right type of driver for this card, so one must install madwifi manually.

Don't use the ng drivers of madwifi, use the madwifi-old-.. driver, and follow the instructions listed. Then the likelyhood for the WLAN to work is more present...

---

### Post by hil on 2006-02-13
The madwifi-ng driver works for me from the subversion repository. I had to edit the 
```

Makefile.inc
Open Makefile.inc
sudo gedit Makefile.inc look for 
COPTS+= -Werror
Change this line and remove the -Werror part so line now looks like this. 
COPTS+=

```
to make it work and change gcc to 3.4 by removing the old symbolic links.
for information can be found at [http://torrez.us/myubuntu/]("http://torrez.us/myubuntu/")

---

### Post by jimufa on 2006-03-17
Iám using a DWL-AG530 wireless pci card everything works fine but i cant conect with this card iwlist scan said that ath0      Failed to read scan data : Resource temporarily unavailable
 ¿What can i do? thanks

---

### Post by everett3rd on 2006-05-06
After reading this thread I purchased a NETGEAR WG511T to replace a Linksys ver 4 card that I couln't get working.

The new card worked out of the box with Breezy on my IBM Thinkpad A22m.:D

---

### Post by tombs on 2006-06-05
piece of cake!!
If works very easy!
Netgear WG511T

Thanx

---

### Post by gm__ on 2006-06-23
Jaykay is the king! :)

Netgear WG511T didnt want to work out of the box...

With Jaykay's guide , made it work in a minute...

Thanks Jaykay! ;)

---

### Post by Bruhthakuga on 2006-08-03
I have a Compaq Presario V2570NR (V2000 Series) notebook, it has a Broadcom BCM 4318 pci wireless card which I "am" haveing a time getting up but the guy in the next room has the Netgear WG511T network card which I borrowd for experimentation purposes and it worked soon as I inserted it.  I thought I should reply just so anyone interested will know my experienc with this card, Sincerely Bruh.

---

### Post by tombs on 2006-08-20
Well, it was working perfect, and after a apt-get upgrade is not working anymore.](*,) ](*,) 

tombs@ubook:~$ sudo ifconfig ath0 up
ath0: ERROR when getting markers of the interface : No such device

And when I try cliking on the network icon on desktop the error is:
Error SIOCGIFFLAGS: No such device

lscpi shows the device:
0000:03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

dmesg:
[http://paste.ubuntubrasil.org/576]("http://paste.ubuntubrasil.org/576")

Running Ubuntu Dapper 2.6.15.26-386
Could anyone help me please?
Thanx

---

### Post by tombs on 2006-08-22
OK....it's working now!:-D

---

### Post by gruffy-06 on 2006-09-17
How come the drivers from madwifi.org don't work on my AR5212?

I got a new kernel, got the drivers, compiled and installed, but I get an "unrecognized request" error when switching to ad-hoc. And why does Ubuntu report it as an AR5005?

Madwifi is version 0.92. The kernel is 2.6.17.3 (at time of download). ](*,)

---

### Post by hil on 2006-09-17
You said switching to ad-doc. Can the driver work under managed mode? I downloaded the driver for my ubuntu in a kernel patch. The driver could work, but I haven't tested it on ad-hoc mode. How does the driver function in the managed mode?

---

### Post by PRMan on 2007-04-26
In Feisty, jaykay's guide worked to get this card up.

---

### Post by scales on 2007-06-13
my card was recognized automatically in feisty, but i am having trouble connecting to hidden networks, and the signal strength is way weaker than in windows.  i think i am using madwifi, but i thought about switching to ndiswrapper. tips?

---

### Post by zumbrujm on 2007-06-13
I have tried to follow JayKay's guide, but I have had some difficulty.

When I try the step iwconfig ath0 channel 1, I get the following message:
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device ath0 ; operation not permitted.

I am very unfamiliar with linux, and I am not sure what the problem is.

---

### Post by ukripper on 2007-07-16
> **PRMan said:**
> In Feisty, jaykay's guide worked to get this card up.

I ignored Jaykay's guide which is outdated and used wlassistant to configure my essid and key worked like charm  on my sony vaio

---

### Post by Paris Heng on 2007-07-26
HOW-TO] Master Mode + Madwifi + Bridging
Dear all,

I have installed Madwifi + Atheroes Wifi in the **laptop A**, and it work well.

I have made the Wifi card into Master Mode (access Point)**(laptop A**).
My another **laptop B** use to connect to it, but cannot!! It just able to scan and detect the availability of the access point where i created in **laptop A**.

Problems:

How I to enable **laptop B** to connect to **laptop A**? What i miss?

(1) Routing ?
(2) NAT ?
(3) DHCP ?
(4) Port Fowarding ?
(5) WPA ?


Please assist.

---

### Post by mfbernstein on 2007-07-29
Trying to get a PCI-Express Atheros 5212-based abg card working on my ThinkPad X61 with 64bit Gusty (alpha 3). I'm using the madwifi drivers.

NetworkManager sees the card and see the wireless networks, but I never successfully connect to any of them. The issue isn't signal strength, as it doesn't work even if I stand next to the access point.

Updating to the latest madwifi snapshot makes no difference.

The only hints I see in the logs are:
Jul 29 13:04:30 sparrowhawk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
Jul 29 13:04:30 sparrowhawk kernel: [  115.459504] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready

Any ideas or suggestions what might be wrong here?

Thanks.

---

### Post by Dngrsone on 2007-12-18
Okay, I've been banging my head against this problem for close to a week.  I am running an Atheros mini-pci card on a Dell Latitude C610.

Now, Win XP Pro calls this wireless card an Atheros AR5005GS, however, Ubuntu thinks its an AR5212.

At any rate, the *Gutsy Gibbon* release (7.10), installed the appropriate madwifi drivers and I could see my wireless routers using [COLOR="SeaGreen"]sudo iwlist ath0 scan[/COLOR].  I added my preferred ssid, its hardware address, my WEP key, but could not get an IP address assigned via [COLOR="SeaGreen"]sudo dhclient ath0[/COLOR].

Finally, after reviewing a good number of pages here in the forums, I made it to the [madwifi wiki](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) page, where I discovered this little tidbit-- when operating in a shared-key environment, try issuing [COLOR="SeaGreen"]sudo ath0 authmode 2[/COLOR].

Now I am up and typing this through the wireless.  We shall see later if this sticks after a reboot or if I have to do some scripting or something.

---

### Post by rnaidu on 2008-02-12
Has anyone tried to access Management Information Base(MIB) on the atheros network card. It saves all the information of stuff going on the network card. I want to know what exactly is there in MIB and how to extract it. Anyone knows anything?? PLEASE REPLY

---

### Post by norbert79 on 2008-03-03
> **scales said:**
> my card was recognized automatically in feisty, but i am having trouble connecting to hidden networks, and the signal strength is way weaker than in windows.  i think i am using madwifi, but i thought about switching to ndiswrapper. tips?

I know this is an older post, but I still have the same problems with this Atheros driver. Way weaker, than in Windows, have problems accessing hidden WIFI networks.
I am using Gutsy 7.10, out of the box install, nothing has been changed. 
HAL info: 0.9.18.0
Driver: Kernel based Madwifi. Out-of the box.
Vendor: pci 0x168c "Atheros Communications, Inc."
Device: pci 0x1014 "AR5212 802.11abg NIC"

I am unable to make it work better, and I am desperate. Ideas anyone? ](*,)

---

### Post by hakujin1 on 2008-05-04
> **Dngrsone said:**
> Okay, I've been banging my head against this problem for close to a week.  I am running an Atheros mini-pci card on a Dell Latitude C610.

Now, Win XP Pro calls this wireless card an Atheros AR5005GS, however, Ubuntu thinks its an AR5212.

At any rate, the *Gutsy Gibbon* release (7.10), installed the appropriate madwifi drivers and I could see my wireless routers using [COLOR="SeaGreen"]sudo iwlist ath0 scan[/COLOR].  I added my preferred ssid, its hardware address, my WEP key, but could not get an IP address assigned via [COLOR="SeaGreen"]sudo dhclient ath0[/COLOR].

Finally, after reviewing a good number of pages here in the forums, I made it to the [madwifi wiki](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) page, where I discovered this little tidbit-- when operating in a shared-key environment, try issuing [COLOR="SeaGreen"]sudo ath0 authmode 2[/COLOR].

Now I am up and typing this through the wireless.  We shall see later if this sticks after a reboot or if I have to do some scripting or something.

That's not working for me and I have the exact same notebook with the same atheros mini pci

Same thing... an Atheros AR5005GS, however, Ubuntu thinks its an AR5212. I can see through the console that it can see other SSIDs but it's just not working after entering SSID, DHCP, WPA pass etd... Can anyone advise... slowly as I'm a recent XP to Ubuntu convert, running Gutsy Gibbon and struck out in the 1st inning getting the wifi to work. 

It's always the wifi with Linux I swear. Years past when I tried to convert it was compatibility... I always heard :get atheros-get atheros. Now I have atheros and still no go...
:confused:

Oh yeah, the signal looks weaker when scanning SSIDs too but I don't care so long as I can connect... just wondering why all the fuss when the drivers are already installed.

---

### Post by hakujin1 on 2008-05-07
I'm going to posit a guess and say this Atheros Wifi card 'bug' is still alive and well in Hardy Heron...

So much for the 'great linux support' I've been hearing so much about... ironically XP has zero problems with this Atheros AR5005GS and has never labeled it a PCI wireless card that it is not (i.e. AR5212). Come to think of it, I've never had a wireless card that didn't function correctly in xp while on the other hand, I've never owned a PCI WiFi card that worked in *nix either unsupported or w/o jumping through hoops to get going.

---

