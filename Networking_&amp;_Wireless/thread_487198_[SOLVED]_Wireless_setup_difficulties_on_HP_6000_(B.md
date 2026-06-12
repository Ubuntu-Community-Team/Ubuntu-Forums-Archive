---
title: "[SOLVED] Wireless setup difficulties on HP 6000 (BCM4311)"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by Paul_Joseph on 2007-06-28
Problem:

I am unable to get my wireless to work.  I have tried numerous methods and suggestions that I have read within the forums.  I have google'd and tried more suggestions.  I have reinstalled different versions.  I did manage at one point to get the wireless led (blue) to come on, but still never could connect.  I want to try again, asking those members of the community wiser than I what I am missing.  Maybe the process will be informative for others.

Computer:

I am on an HP Pavilion dv6000; model 6045nr; the dual processors are AMD K8 Athlon64/Opteron.  The wireless card is the infamous Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01) - bcm4311 firmware.  I currently have a wired connection for this laptop (in fact I am writing up this post from this laptop).  The wireless router that I am trying to connect to is Linksys WCG200v2.  Also connected wirelessly in my house: 1 Edubuntu (Edgy) desktop, 1 Xubuntu (Fiesty) desktop, 1 XP Home laptop, and 2 XP Media Center laptops.  I previously (2 days ago) installed XP Home on this laptop and connected to the router just fine.  The router has been set for now with no security - open to the world at large.

Me:  

Not a newbie, but not an expert either.  Computer literate, but I still have to continually refer back to the C reference manual when reading/writing code.  I buy organic veg's at Whole Foods because they spend money on carbon reduction; I buy the CF bulb at $3 more even if my electric bill doesn't go down; and if I'm right I will argue the traffic ticket even if I have to pay more to be right.  I've played with Red Hat and Fedora for years, going out of my way to avoid MS whenever possible.  Most of the time all I really need is OpenOffice, Firefox, Thunderbird and wireless internet.

Task at Hand:

I wiped the partitions, and started again from scratch.  I have installed Xubuntu 7.04 from Live Desktop 64-bit CD which starts with the 2.6.20-15-generic kernel.  I have to modify the boot params to include 'pci=noacpi'.  I have previously tried just 'noacpi' and even 'noacpi noacpi', neither work for me.  After booting up the laptop, about 5 minutes into anything that I am working on, I get the message:

Message from syslogd@adeptus at Thu Jun 28 17:33:23 2007 ...
adeptus kernel: [  307.932110] Disabling IRQ #7

I have attached log files for dmesg and lspci.

Of the methods to get the broadcom card working, is ndiswrapper or native driver the prefered method of install for bcm4311 on Feisty AMD64?

Respectfully,

Xubuntu Grasshopper

[B]
Solution:

It would appear that the central fix related to my using ndiswrapper was related to the boot options that I was using.  I had added 'pci=noacpi', but what I really needed was just 'noapic'.[/B]

My boot params are: 'ro splash noapic mem=1024M'  (The mem= refers to the 1G of RAM on my laptop).

Still, here is the code I executed right after installation, you can save it to file and run it as a script if you like:

```
#!/bin/sh

# get rid of ndiswrapper - if this is a clean install, then won't exist
sudo rmmod ndiswrapper
sudo ndiswdrapper -e bcmwl5
sudo apt-get -y remove ndiswrapper ndiswrapper-utils
sudo rmmod ndiswrapper

sudo apt-get -y update
sudo apt-get -y install build-essential cabextract
sudo apt-get -y install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo modprobe -r bcm43xx

# get the latest ndiswrapper
cd ~; wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz
tar -xzvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
sudo make uninstall
sudo make uninstall
make distclean
make
sudo make install
cd ~; rm ndiswrapper-1.47.tar.gz

# get the latest HP driver for this card
wget ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe -O${HOME}/sp34152.exe
cd ~; mkdir bcm4311; mv sp34152.exe bcm4311; cd bcm4311
cabextract sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo cp /etc/ndiswrapper/bcmwl5/14E4:4311.5.conf /etc/ndiswrapper/bcmwl5/.conf
cd ~; cat /etc/ndiswrapper/bcmwl5/.conf | egrep -B 100 'Afterburner' > bcmwl.1
cat /etc/ndiswrapper/bcmwl5/.conf | egrep -A 100 'Afterburner' > bcmwl.2
cat ~/bcmwl.1 | egrep -v 'Afterburner' > bcmwl.conf
echo 'Afterburner|0' | tee -a bcmwl.conf
cat ~/bcmwl.2 | egrep -v 'Afterburner' | tee -a bcmwl.conf
sudo cp ~/bcmwl.conf /etc/ndiswrapper/bcmwl5/.conf
cd ~; rm bcmwl.*

sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig

cd ~; cat /etc/network/interfaces | egrep -v 'eth1' > interface.1
cat ./interface.1 | egrep -v 'wlan0' > interface.2
cat ./interface.2 | egrep -v 'wireless' | sudo tee /etc/network/interfaces
cd ~; rm interface.*

echo 'iface wlan0 inet dhcp' | sudo tee -a /etc/network/interfaces
echo 'wireless-essid any' | sudo tee -a /etc/network/interfaces
echo 'auto wlan0' | sudo tee -a /etc/network/interfaces

sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

# get rid of eth1
cd ~; sudo cp /etc/iftab /etc/iftab.old
cat /etc/iftab.old | sudo egrep -v 'eth1' > iftab
sudo cp iftab /etc/iftab
cd ~; rm iftab

sudo apt-get -y install network-manager wlassistant

iwconfig
sudo ifdown wlan0
sudo ifup wlan0
sudo iwlist scanning
sudo dhclient wlan0

# add automatix cuz you are going to use it later
echo "deb http://www.getautomatix.com/apt feisty main" | sudo tee -a /etc/apt/sources.list
wget http://www.getautomatix.com/keys/automatix2.key
gpg --import automatix2.key
gpg --export --armor E23C5FC3 | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install automatix2
cd ~

sudo shutdown -r now
```

After you are up, you are going to want to use Automatix2 and update NVidia drivers.

Happy trails.

---

### Post by Paul_Joseph on 2007-06-28
Alright,

I am going to try the ndiswrapper, following the advice of [http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

paperdiesel suggest that I remove already installed ndiswrapper via:

```
sudo rmmod ndiswrapper
sudo ndiswrapper -e bcmwl5
sudo apt-get remove ndiswrapper-utils
```

Of course, since this was a fresh install, the above just says 'does not exist' and 'not known'.  Now get build utils.

```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
```

The latest network driver provided by HP is Broadcom 4.100.15.5 Driver, Release Date: 2006-11-10, Version: 6.10 A.

```
wget ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe
```

And then the lastest ndiswrapper:

```
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz
tar -xzvf ndiswrapper-1.47.tar.gz

```

Blacklisting native driver:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

Time to reboot.

---

### Post by Old *ix Geek on 2007-06-28
I went through HELL trying to get wireless working on my dv6000--but I finally did do it. :)  I'm using NDISwrapper and am SO HAPPY with its connection speed, I can't even tell you!

Here's [my thread](http://ubuntuforums.org/showthread.php?t=442816) about the problems I had.  If you follow the links found in replies in that thread, you'll be doing what I did--and it worked.

Specifically, follow [these instructions](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%284311%29) to the letter.  If you run into problems, look at [the NDISwrapper page](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33) for troubleshooting suggestions.

---

### Post by Paul_Joseph on 2007-06-28
Now to compile ndiswrapper.  Docs say to re-rerun 'sudo make uninstall' numerous times until it stops saying 'removing ...'.  I only had to run it twice.

```
cd ndiswrapper-1.47
sudo make uninstall
sudo make uninstall
```

Installing ndiswrapper:

```
sudo make
sudo make install
```

Installing driver:

```
cd ~
mkdir bcm4311
mv sp34152.exe bcm4311
cd bcm4311
sudo apt-get install cabextract
cabextract sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

Time to reboot again.

---

### Post by Paul_Joseph on 2007-06-28
This is the part where I start to have problems.

```
sudo iwlist scanning
```

produces -> 

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

Doesn't look like it sees a eth1 or a wlan0.  And as expected, I see no blue wireless light.

---

### Post by Paul_Joseph on 2007-06-28
> **Old *ix Geek said:**
> I went through HELL trying to get wireless working on my dv6000--but I finally did do it. :)  I'm using NDISwrapper and am SO HAPPY with its connection speed, I can't even tell you!

Here's [my thread](http://ubuntuforums.org/showthread.php?t=442816) about the problems I had.  If you follow the links found in replies in that thread, you'll be doing what I did--and it worked.

Specifically, follow [these instructions](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%284311%29) to the letter.  If you run into problems, look at [the NDISwrapper page](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33) for troubleshooting suggestions.

Thanks.  Following the first link that I had listed, I end with another failure.

So, now I will start again following the link that you suggested.  [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%284311%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%284311%29")

So, as to start absolutely fresh, I will wipe the partition and install from cd again.   I will let you know how it goes.

---

### Post by Paul_Joseph on 2007-06-28
Starting similarly with

```
sudo apt-get update
sudo apt-get install build-essential

```

This one wasn't necessary, but just to follow the steps.

```
sudo apt-get install linux-headers-`uname -r`
```

Get the recommended driver:

```
wget ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe -O${HOME}/sp33008.exe
```

Again, download ndiswrapper.

```
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz
tar -xzvf ndiswrapper-1.47.tar.gz
```

Blacklisting the native driver:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

And rebooting.

---

### Post by Paul_Joseph on 2007-06-28
Compiling ndiswrapper

```
cd ndiswrapper-1.47
sudo make uninstall
sudo make uninstall
```

Installing ndiswrapper

```
sudo make
sudo make install
```

Get utils:

```
sudo apt-get install ndiswrapper-utils-1.9 cabextract
```

Install driver:

```
cd ~; mkdir bcm4311; mv sp33008.exe bcm4311; cd bcm4311
cabextract sp33008.exe
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
```

Continue installing driver.  Use the 14E4:4311 address from the line above in the next step.

```
sudo cp /etc/ndiswrapper/bcmwl5/14E4:4311.5.conf /etc/ndiswrapper/bcmwl5/.conf
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

```

Time to reboot again.

---

### Post by Paul_Joseph on 2007-06-28
And familiarity sets in again.  After rebooting, I not only don't have wireless, but now I don't even have ethernet.  (I'm am now using my desktop to post - laptop is now without any internet access).

So looking over instructions. Did I miss something?

Check .conf file to change Afterburner since I do have a Linksys router.  Though, this won't make any difference if the wireless is not even trying to work.  I'll go ahead and change Afterburner 1 to 0.

```
sudo mousepad /etc/ndiswrapper/bcmwl5/.conf
```

How about checking iwconfig.

```
iwconfig
```

And it only lists lo and eth0.  wlan0 is missing.  

I guess I was supposed to add wlan0 to interfaces first before rebooting.  So, first I'll prove it isn't there already.

```
cat /etc/network/interfaces | grep wlan0
```

Well, then I'll add it now.

```
echo 'iface wlan0 inet dhcp' | sudo tee -a /etc/network/interfaces
echo 'wireless-essid linksys' | sudo tee -a /etc/network/interfaces
echo 'auto wlan0' | sudo tee -a /etc/network/interfaces
```

Now I'll reboot again.

---

### Post by Paul_Joseph on 2007-06-28
Still no wireless.  Still no ethernet.

Hmmm... Why did the instructions have me wipe out interfaces and leave only lo earlier?

I'll add back in eth0 and regain atleast ethernet.

```
echo 'iface eth0 inet dhcp' | sudo tee -a /etc/network/interfaces
echo 'auto eth0' | sudo tee -a /etc/network/interfaces
```

Reboot again.

---

### Post by Paul_Joseph on 2007-06-28
Back with ethernet, but iwconfig show no wlan0.

There are more steps, but if iwconfig isn't showing any wlan0, then I've obviously strayed.  I see I need to reconcile the differences in [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%284311%29]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%284311%29") and [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

Suggestions, or shall I try again from scratch?

---

### Post by kevdog on 2007-06-28
Congrats on working with ndiswrapper -- your steps are excellent.

Lets just check a few things before going with reinstall.  

Please post the following

lspci
lshw -C network
ndiswrapper -v
ndiswrapper -l
/etc/network/interfaces
/etc/iftab

Id add more stuff, but frankly that would make it totally ridiculous :)

---

### Post by Paul_Joseph on 2007-06-29
Glad someone was reading.

I just ran the following:

```
lspci > lspci.txt
sudo lshw -C network > lshw.txt
ndiswrapper -v > ndisv.txt
ndiswrapper -l > ndisl.txt
cat /etc/network/interfaces > interfaces.txt
cat /etc/iftab > iftab.txt
```

And they are attached.

---

### Post by Paul_Joseph on 2007-06-29
I guess I could have just dumped in as a post, but that gets a bit long.

---

### Post by Paul_Joseph on 2007-06-29
And in generating these files....I see an eth1 in iftab.  Should that be changed to wlan0 or just commented out?

---

### Post by kevdog on 2007-06-29
Wow -- someone who actually reads what he posts!!

Yea I would change that from eth1 to wlan0.  I should have asked for ifconfig -- that would have given me the MAC address of the wireless card.  

Make the change then reboot

Check lshw -C network

Your card shouldnt be listed as unclaimed if everything is setup properly.

Also just check that in /etc/modprobe.d/blacklist that the bcm43xx driver is blacklisted!

---

### Post by Old *ix Geek on 2007-06-29
I believe I commented out the eth1 line in iftab.

From your posts I see that you've used a different driver than I did; here's the one I used: [ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe) (it's supposed to fix various issues in dv6000 computers).

Do you have "Wireless Assistant" installed?  I had forgotten all about that until I reread my thread about my problems getting wireless to work.  You can use Synaptic to install it if it isn't already.  I remember it being critical in FINALLY getting my wireless working correctly. I also used "Manual network configuration" to plug in various values, but I can no longer recall whether that actually made a difference or not.

I know it's REALLY frustrating to jump through all these hoops and still not have it working right, but don't despair!  I did it, and you can too.

---

### Post by Paul_Joseph on 2007-06-29
Ok.  First I tried changing eth1 to wlan0 in iftab.  Rebooted.  iwconfig does not have wlan0.

Attached files.

Now, I will try with wlan0 just commented out of iftab.

---

### Post by kevdog on 2007-06-29
Not that this is probably going to do anything but get rid of the WEP on the router for now, and modify your /etc/network/interfaces file and remove the essid line (or comment it out).

2 ideas
If you do a lsmod | grep ndiswrapper -- does it show the ndiswrapper as being loaded??
If you do a modprobe -l | grep ndisrapper - it confirms the the module as loaded in the kernel??

Might be a driver related issue -- I think previous poster might have been on to this.  I helped someone get this up and running once I used the driver from the ndiswrapper website rather than the ones supplied by the manufacturer:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/) 
Look for #48.  The ftp site links to dell, so I dont know what to tell you

If it were a driver problem see if anything shows up in the boot log:
dmesg

---

### Post by Paul_Joseph on 2007-06-29
Commenting out ap in /etc/network/interfaces.

They appear to show me that ndiswrapper is loaded.  (Your modprobe threw me for a minute - your post was missing a 'w' and I just cut and pasted).

```
cat /etc/network/interfaces > interfaces.txt
lsmod | grep ndiswrapper > lsmod.txt
modprobe -l | grep ndiswrapper > modprobe.txt
dmesg | grep ndiswrapper > dmesg.txt

```

Keep the ideas flowing.

---

### Post by Paul_Joseph on 2007-06-29
> **Old *ix Geek said:**
> Do you have "Wireless Assistant" installed?  I had forgotten all about that until I reread my thread about my problems getting wireless to work. 

Now after having commented out wlan0, and rebooting.  iwconfig still does
not show wlan0.  lshw still shows unclaimed.

I have tried Old *ix Geek's suggestion to install Wireless Assistant.

```
sudo apt-get install wlassistant
```

and to reboot

```
shutdown -r now
```

lshw still shows unclaimed.

dmesg shows failures because of irq 0?  And as I originally mentioned.  About 5 minutes after each reboot, I get a Disabling IRQ #7 message.

---

### Post by kevdog on 2007-06-29
Can you post the portion of the log that you think is relevant?? (This could be dangerous!!)
 
If you remove ndiswrapper --
sudo modprobe -r ndiswrapper

do you still get the same error in the logs??

What if you reinstall ndiswrapper
sudo modprobe -i ndiswrapper

What do the logs say specifically then?? (No need to reboot after loading module).

---

### Post by kevdog on 2007-06-29
Going over your instructions again, I think I found something that is redundant

Can you cut and paste your /etc/modules file??

---

### Post by Paul_Joseph on 2007-06-29
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
ndiswrapper

---

### Post by Paul_Joseph on 2007-06-29
> **kevdog said:**
> Can you post the portion of the log that you think is relevant?? (This could be dangerous!!)

I did

```
dmesg | grep ndiswrapper > dmesg.txt
```

---

### Post by kevdog on 2007-06-29
No problem with that file ---

What about /etc/modprobe.d/ndiswrapper ??

---

### Post by Paul_Joseph on 2007-06-29
> **kevdog said:**
> 
sudo modprobe -r ndiswrapper

do you still get the same error in the logs??

What if you reinstall ndiswrapper
sudo modprobe -i ndiswrapper

What do the logs say specifically then??

See dmesg.txt above.

Any idea what 'ndiswrapper: request for IRQ 0 failed' means?

---

### Post by Paul_Joseph on 2007-06-29
> **kevdog said:**
> What about /etc/modprobe.d/ndiswrapper ??

alias wlan0 ndiswrapper

---

### Post by kevdog on 2007-06-29
Thank dmizer (another user) for this solution:

okay ... let's add a couple of kernel options to try to avoid that irq conflict.

first backup your grub like so:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup

```

now, if your computer won't boot after the changes, just use the live cd and move the menu.list-backup to menu.lst

find your most recent kernel line. it should look something like this:

```


kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash


```
add "irqpoll" and "noapic" options to your kernel like so it looks something like this:

```

kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash irqpoll noapic

```

make sure that the kernel line doesn't wrap to a second line. this will prevent your machine from booting. everything should appear on the same line.

save ... reboot. if you still have problems, please post the output of dmesg again.

More specific
when you look toward the bottom of menu.lst, you'll see a number of lines that will look similar to this:

```


## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-28-686
root            (hd0,0)
[COLOR="Red"]kernel          /boot/vmlinuz-2.6.15-28-686 root=/dev/hda1 ro quiet splash[/COLOR]
initrd          /boot/initrd.img-2.6.15-28-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-686 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-686 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-28-686
boot

```

__________________

---

### Post by Paul_Joseph on 2007-06-29
Well ain't that slicker than a hairdo on a John Travolta twenty-something look-a-like contest!

I am wireless.

I'll go back and do this over again and summarize for all who want the skinny.

Thanks Old *ix Geek, kevdog, and dmizer.

---

### Post by Old *ix Geek on 2007-06-29
YAY!  I'm so glad you got it working. :D

---

### Post by Paul_Joseph on 2007-06-29
Well it worked this morning, but started locking up during boot this afternoon.  I have been reading different threads, but I don't have the solution yet.

I wanted to make sure that I had all of the steps recorded, but for others, as well as my ability to do it again on another HP Laptop.

So, I deleted the partitions, reformated and installed new from Xubuntu 7.04 Live CD.  Then ran the following (a summary of what we did before).  Like previously, I had to add pci=noacpi to boot.

```
sudo rmmod ndiswrapper
sudo ndiswdrapper -e bcmwl5
sudo apt-get -y remove ndiswrapper ndiswrapper-utils
sudo rmmod ndiswrapper

sudo apt-get -y update
sudo apt-get -y install build-essential cabextract
sudo apt-get -y install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo modprobe -r bcm43xx

cd ~
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz
tar -xzvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
sudo make uninstall
sudo make uninstall
make distclean
make
sudo make install

wget ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe -O${HOME}/sp34152.exe
cd ~; mkdir bcm4311; mv sp34152.exe bcm4311; cd bcm4311
cabextract sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo cp /etc/ndiswrapper/bcmwl5/14E4:4311.5.conf /etc/ndiswrapper/bcmwl5/.conf
cd ~

sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig

cd ~
cat /etc/network/interfaces | egrep -v 'eth1' > interface.1
cat ./interface.1 | egrep -v 'wlan0' > interface.2
cat ./interface.2 | egrep -v 'wireless' | sudo tee /etc/network/interfaces
rm interface.1
rm interface.2

echo 'iface wlan0 inet dhcp' | sudo tee -a /etc/network/interfaces
echo 'wireless-essid any' | sudo tee -a /etc/network/interfaces
echo 'auto wlan0' | sudo tee -a /etc/network/interfaces

sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

cd ~
sudo cp /etc/iftab /etc/iftab.old
cat /etc/iftab.old | sudo egrep -v 'eth1' > iftab
sudo cp iftab /etc/iftab

sudo apt-get -y install network-manager wlassistant

iwconfig
sudo ifdown wlan0
sudo ifup wlan0
sudo iwlist scanning
sudo dhclient wlan0

sudo fdisk -l | grep swap
echo -n 'RESUME=UUID=' | sudo tee /etc/initramfs-tools/conf.d/resume
sudo vol_id -u /dev/sda5 | sudo tee -a /etc/initramfs-tools/conf.d/resume
sudo update-initramfs -u

sudo apt-get -y install console-setup
sudo setupcon --save-only

sudo shutdown -r now
```

Afterward it came back up, I edited

```
sudo mousepad /boot/grub/menu.lst
```

and changed 'pci=noacpi' to 'irqpoll noacpi' as this was the final fix last round.

I also edited

```
sudo mousepad /etc/ndiswrapper/bcmwl5/.conf
```

and changed Afterburner to 0.

After rebooting, wireless led comes on and then boot locks up.

I am attaching stats built by

```
dmesg | grep -B 199 'PNP: PS/2 Controller' > dmesg1.txt
dmesg | grep -A 199 'PNP: PS/2 Controller' > dmesg2.txt
lspci > lspci.txt
sudo lshw -C network > lshw.txt
ndiswrapper -v > ndisv.txt
ndiswrapper -l > ndisl.txt
cat /etc/network/interfaces > interfaces.txt
cat /etc/iftab > iftab.txt
uname -r > uname.txt
```

Any suggestions?

---

### Post by Paul_Joseph on 2007-06-29
And the rest.

---

### Post by Paul_Joseph on 2007-06-29
Might as well add

```
lsmod | grep ndiswrapper > lsmod.txt
modprobe -l | grep ndiswrapper > modprobe.txt
```

---

### Post by Ayuthia on 2007-06-29
I have an HP dv6338se and have been running it with noapic nolapic and it connects wirelessly via ndiswrapper on a 4311.  The problem with this is the disabling IRQ#7 issue.  It doesn't seem to hurt anything, but I would like to find a way to fix it.

---

### Post by Paul_Joseph on 2007-06-29
I assumed that you meant 'noacpi noacpi', but I went ahead and tried both ways.

'noacpi nolacpi' - locks up at about 10% of boot process

'noacpi noacpi' - locks up at about 60%

'irqpoll noacpi' - locks up at about 60%

So, far only 'pci=noacpi' lets me boot all the way, but then wireless doesn't work.

---

### Post by Ayuthia on 2007-06-29
No, I meant noapic nolapic.  Here is a snip from my menu.lst:

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=624abd75-e2cd-4015-bf54-3c66c3fcb31e ro noapic nolapic splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

---

### Post by Paul_Joseph on 2007-06-29
I stand corrected.  And you are right.

```
noapic nolapic
```

did the trick.

Thanks a bunch.:D

---

### Post by Paul_Joseph on 2007-06-29
Further testing reveals that noapic is enough to solve the problem.

---

### Post by kevdog on 2007-06-29
Dang kernel module settings -- these things are a nuisance and really tick me off!

---

### Post by r3ptilicus on 2007-07-09
Just wanted to say thanks. I used the script you put up in the very first post and it fixed my wireless issues on my dv6208. Combined with the noapic and Broadcom driver issues this has been the biggest pain of an Ubuntu install yet. :)

---

