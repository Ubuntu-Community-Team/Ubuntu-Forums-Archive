---
title: "How Do You Set Up A Netgear WG111T USB Dongle In Ubuntu?"
date: 2006-09-16
forum: Networking &amp; Wireless
---

### Post by koholint1000 on 2006-09-16
Hi, I'm a complete newbie to the Linux kernel, and the Ubuntu OS, but am eager to learn.

I dual booted with XP, and was dissapointed to realise that my Netgear Wireless USB Dongle WG111T was not recognised, so consequently I cannot access the Internet.

Does anyone know (in as simple terms as possible [thanks] ) how to get it working? :confused: 

The dongle is still working fine in XP, so I should be able to download the drivers if someone posts a URL, but I'll probably have a nervous breakdown if I need to use the command line! #-o 

Thanks in Advance :D 

An eager new member of the rapidly expanding Linux Community!

---

### Post by Blackneck on 2006-09-30
I'm a Linux novice too, and I'm not interested in the terminal and all the technical stuff - I just wanted a PC for the wife to run an office suite without having to pay any more Microsoft Tax.

I got my WG111t running without much difficulty - mainly due to blind luck, I admit.

I was exploring the 'Advanced' part of the Add & Remove menu, and saw ndisgtk, which claimed to be a graphical front end for ndiswrapper - and as I had been unable to find where ndiswrapper is hidden I thought it may help, so I selected it.  It added an icon in the system menu for Windows wireless drivers.  It opened a window which asked for the drivers (I used the drivers provided on the CD which came with the dongle), plugged in the aforementioned dongle, and the thing worked!

After a reboot, however, it didn't work.  I unplugged it and plugged it back in again (it was the only thing I could think of) and once again it worked.  It seems it will only work if it is plugged into a USB port after the machine is running and a user is logged in.

So there ya go, beginners luck.  Wife has her PC and internet connection and everyone is happy.:D

---

### Post by DraeLee on 2006-10-11
Well first off I just wanted to say I feel excited and intrigued to learn linux.  Second The gentleman who posted above me, his way worked beautifully for me.  The only difference is that I couldnt find the add/remove progams (lol i know i know) i did say i was new to this.  I looked up ndisgtk and downloaded it and installed it.  From there I tried to use the drivers that i had downloaded, but they didnt work.  Then I came across this post and went (doi).  I forgot I had the cd with the drivers for my dongle.  So i went under the windows wireless drivers under system > Administration and used the  inf on the cd.  plugged it in recognized that it was connected.  Restarted and voila I am officially on UBUNTU typing up this post.  People please use these forums they have a wealth of info.  Took a little searching but found exactly what I was looking for and I have no doubt now that I will find everything else.  

My wireless (microsoft) keyboard and mouse worked out the box, my sound, my video allof that worked out the box.  I am truly impressed with that.  and now that i got my internetworking its on to learning the rest of this wonder app.  Keep up the good work and wish me luck 8)

---

### Post by DraeLee on 2006-10-13
Well lol now i got an issue lol.  my device does not connect unless i uninstall and reinstall the drivers since i got them off the disc.  I might have to try a different method, because when I copy the files needed on the disc to the hd for some reason the nd app doesnt want to see the drivers.  I click on them but they are not inserted into the area for the .inf.  So I am really confused.](*,)   any help on this would be appreciated.  I am not sure what is the best method but I want to do it correctly.  thx in advance

---

### Post by koholint1000 on 2006-10-16
Well, I dont suffer from this problem; but apparently some PCs running ndisgtk need to have the dongle plugged in AFTER the PC is booted up. As I said, I don't need to do this, but my dongle doesn't work if I don't use the dongle within about 30secs of bootup. I think this might be because this "activates" the device, or something...

Anyway, try using the internet straight upon bootup; and if that doesn't work; just plug the dongle in AFTER the PC has booted up fully.

Hope this helps!

^_^

---

### Post by koholint1000 on 2006-12-21
I found out today that on the driver cd there is another .inf file that is called athfmwdl.inf. Install that through ndisgtk and it'll work on bootup. This is the bootloader driver.

:D

---

### Post by liamjames91 on 2006-12-28
arghhhh!! i think theres enough people with the "wg111t with ndiswrapper in ubuntu" problem to start a club! ive got ndiswrapper and ndisgtk (the gui for ndiswrapper) all installed, and both the .inf files that i downloaded, no matter what i do, the athfmwdl ses device present but the ng11t ses its not there!! it worked ok, not brilliant but ok in dapper, after the upgrade to edgy (via a fresh install not online upgrade) it just makes me wanna scream! ](*,)  im now wondering if it may be easier to buy a cheap dongle on ebay that is supposed to work with linux? question is will that work?

---

### Post by suga on 2007-03-26
I too am a total newbie and to make things more interesting I installed on a system I built myself.  This is the first system that I have built since 800MHZ was fast, and my third ever.  I have had a couple issues getting the 8800 gts working but the above process got my wg111t going pretty well.  I found that it was easiest to use synaptic to install the ndiswrapper from the install disk then download the packet for the GUI ndisgtk from the site onto a USB.  that can be added simply by double clicking and the install option came up.

I am still having the same issue where I have to attach the wg111t only after the system boots.  I have not found the other inf yet.

---

### Post by koholint1000 on 2007-03-27
Right...

I am aware of the immense irony involved in the person who originally asked the question to be answering it once and for all; but nonetheless...

First; download the attachment to your home directory. Then, open a terminal: -
```
$ sudo apt-get install ndiswrapper # Install ndiswrapper Fresh from Repository
$ unzip wg111t.zip # Unzip the Archive
$ cd wg111t # Navigate to Driver Directory
$ sudo ndiswrapper -i athfmwdl.inf # Install the Boot-Loader Driver
$ sudo ndiswrapper -i netwg11t.inf # Install the Wi-Fi Driver
$ sudo ndiswrapper -m # Configure ndiswrapper so Runs on Bootup
$ cd / # Navigate to Root
$ sudo gedit /etc/modprobe.preload # Use kate for KDE
# Append "ndiswrapper" to the bottom of the file if it already isn't there
```

You might need to reboot the PC; I'm not sure; but the last thing you need to do is set up the wireless settings in the Network Settings thing (sorry if it's different on KDE; I'm an avid GNOME user ^_^ )

This *should* work; if not, post the error messages (if any), and me, or someone better equipped (in the |-|4><0r 1337 sense) will assist ASAP.

:D

---

### Post by SwaroopKunduru on 2007-03-27
Hi,

Did you check this site?

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html)

Regards,

Swaroop Kunduru.

---

### Post by koholint1000 on 2007-03-28
Yes. It seems that this site recommends the same things I do; bar the whole 
```
sudo depmod -a
sudo modprobe ndiswrapper
```
thing.

:D

---

### Post by jokeeffe on 2007-04-01
This is for **Ubuntu 6.10 ONLY** also, i recommend turning all wireless security features off on your router until you're connected! If you've setup or installed ndiswrapper before, remove all of it. Really, I recommend starting with a fresh copy of 6.10.

Most the of suggestions on the web didnt help me get my Netgear 111T working so ill post the steps i took to get it to work

Step 1. Kernel Headers
```

sudo apt-get install linux-headers-`uname -r`
sudo apt-get install build-essential

```

Step 2. Get ndiswrapper
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

Step 3. Build (for the sake of this example, im using 1.41, replace w/ whatever version u download)
```

tar xvfz ndiswrapper-1.41.tar.gz
cd ndiswrapper-1.41/
make distclean
make
sudo make install

```

To Check to see if it worked properly
```

ndiswrapper -v

```
you should see something like (if u downloaded ndiswrapper 1.41, otherwise the version will likely be different)
 
utils version: 1.9
driver version:        1.41
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1

Note: In this case, its version 41 (tar xvfz ndiswrapper-1.41.tar.gz)

Step 4. Grab windows drivers
[ftp://downloads.netgear.com/files/wg111t_1_2.zip](ftp://downloads.netgear.com/files/wg111t_1_2.zip)

unzip the file, sure you grab netwg11t.inf, wg11tnd5.sys, ar5523.bin, athfwdl.inf, athfwdl.sys in the WG111T_re1.2_rc1

Step 5. Load drivers
Note: make sure you're in the directory of where u placed the windows drivers (else, u need to do something like sudo ndiswrapper -i /location/to/file)
```

sudo ndiswrapper -i athfmwdl.inf
sudo ndiswrapepr -i netwg11t.inf

```

Check it
```

ndiswrapper -l

```


You should see
athfmwdl : driver installed
netwg11t : driver installed

If you made a typo (like i did earlier) and see something like this, 
athfwdl : invalid driver

remove the bad driver like so
```

sudo ndiswrapper -e athfwdl

```

Step 6. Plug in NetGear WG111T
after plugging it in, check it
```

ndiswrapper -l

```

You should see like this
athfmwdl : driver installed
        device (1385:4251) present
netwg11t : driver installed


OR

athfmwdl : driver installed
netwg11t : driver installed
    device (1385:4250) present





Step 7.
```

sudo modprobe ndiswrapper
sudo nano /etc/modules

```
add this text to the end of modules file
ndiswrapper

RESTART AND PRAY
on restart, you should see the blue light blink on your wireless USB (i think after logging in as your user name)

check to make sure linux recognizes your wireless
```
ifconfig
```

You see something like 
eth0      Link encap:Ethernet  HWaddr 00:E0:4C:F0:70:7A  
          inet addr:192.168.1.54  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fef0:707a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4479 errors:1 dropped:0 overruns:0 frame:1
          TX packets:1792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2084286 (1.9 MiB)  TX bytes:231867 (226.4 KiB)
          Interrupt:217 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1160 (1.1 KiB)  TX bytes:1160 (1.1 KiB)

wlan1     Link encap:Ethernet  HWaddr 00:18:4D:33:D3:BB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

As long as u have wlan, you should be good
Now search for wireless networks
```
iwlist scan
```

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:17:9A:48:7C:6F
                    ESSID:"BookIt2ndFloor"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : PSK  

sit0      Interface doesn't support scanning.

Now just go to System->Administration->Networking
you should see wireless connection, select it and click properties
and the rest is yours. I'll add some screenshots in a bit.

---

### Post by flx00 on 2007-04-12
Hi, im a complete linux newb


```

sudo ndiswrapper -i athfwdl.inf
sudo ndiswrapepr -i netwg11t.inf

```

followed this and got:


athfwdl : invalid driver
netwg11t : driver installed


realised there was a typo perhaps, so did this

```

sudo ndiswrapper -i athfmwdl.inf


```

got this:

athfmwdl: driver installed
athfwdl : invalid driver
netwg11t : driver installed

After step6, got same message as above, no device found.

how do i remove athfwdl? if that is causing the problem.

also i continued onto the next step, where it told me it that no /etc/modules directory existed, where should i perfom this step- in which directory?

---

### Post by The Thinman on 2007-04-16
Hi,

after many frustrating attempts at setting up the drivers, I find I should have ndiswrapper v1.23 or later. The one supplied with ubuntu was 1.22. How can I get this if my ubuntu Linux system won't connect to the internet. Can I download it from somewhere using Windows and then copy it on?

Thanks

---

### Post by uberplum on 2007-04-19
Hi, I have this exact same problem. I have followed all the steps here, used ndiswrapper to install the .inf driver files, but still, Linux doesn't even pick up the device. I can't think of what to do.

---

### Post by jokeeffe on 2007-04-20
> **flx00 said:**
> Hi, im a complete linux newb


```

sudo ndiswrapper -i athfwdl.inf
sudo ndiswrapepr -i netwg11t.inf

```

followed this and got:


athfwdl : invalid driver
netwg11t : driver installed


realised there was a typo perhaps, so did this

```

sudo ndiswrapper -i athfmwdl.inf


```

got this:

athfmwdl: driver installed
athfwdl : invalid driver
netwg11t : driver installed

After step6, got same message as above, no device found.

how do i remove athfwdl? if that is causing the problem.

also i continued onto the next step, where it told me it that no /etc/modules directory existed, where should i perfom this step- in which directory?

what version of ndiswrapper do u have installed?
```
ndiswrapper -v
```

Remove the bad drivers like this
```

sudo ndiswrapper -e athfwdl

```

Argh. Sorry guys, i made a typo earlier, i corrected my typo in the original post, so, the steps should be correct now. Make sure to remove any driver that failed to install properly or misspelled.

---

### Post by jokeeffe on 2007-04-20
> **The Thinman said:**
> Hi,

after many frustrating attempts at setting up the drivers, I find I should have ndiswrapper v1.23 or later. The one supplied with ubuntu was 1.22. How can I get this if my ubuntu Linux system won't connect to the internet. Can I download it from somewhere using Windows and then copy it on?

Thanks

yes, that will work too

---

### Post by The Thinman on 2007-04-21
Right, got the latest version of ndiswrapper, followed the instructions. ndiswrapper -l shows drivers installed and hardware present; still nothing. wlan0 does not appear in the list of connections in network tools. Is there something else I need to do?

---

### Post by jokeeffe on 2007-04-21
> **The Thinman said:**
> Right, got the latest version of ndiswrapper, followed the instructions. ndiswrapper -l shows drivers installed and hardware present; still nothing. wlan0 does not appear in the list of connections in network tools. Is there something else I need to do?

can u show me what this command displays for you
```
ndiswrapper -l
```

Also, what version of ndiswrapper are you using
```
ndiswrapper -v
```

I'm assuming u did step 7 and then restarted, double check and make sure the file (/etc/modules) has the line
ndiswrapper in it.

an example of my /etc/modules file looks like this
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper

```

---

### Post by The Thinman on 2007-04-22
> **jokeeffe said:**
> can u show me what this command displays for you
```
ndiswrapper -l
```

Also, what version of ndiswrapper are you using
```
ndiswrapper -v
```

I'm assuming u did step 7 and then restarted, double check and make sure the file (/etc/modules) has the line
ndiswrapper in it.

an example of my /etc/modules file looks like this
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper

```

Hi,

ndiswrapper -v shows version 1.42

ndiswrapper -l:

athfmwdl driver installed, hardware present
netwg11t driver installed

ndiswrapper is in /etc/modules

wlan0 still stubbornly refuses to appear.

Is there a file which contains the network devices? eth0 etc. which is editable. I don't know if that will help.

---

### Post by dbld on 2007-04-22
Fraking frustrating. This damn netgear peace of **** dongle just refuses point blank to come on.
Device is listed in system devices but she dot wek on Feisty baaas

```
dbld@dbld-desktop:~$ ndiswrapper -v
utils version: 1.9
driver version:        1.38
vermagic:       2.6.20-15-generic SMP mod_unload 586 
dbld@dbld-desktop:~$ ndiswrapper -l
athfmwdl : driver installed
        device (1385:4251) present
netwg11t : driver installed
dbld@dbld-desktop:~$
```

---

### Post by Nellephant on 2007-04-24
I have similar problems with a WG111T dongle. I finally managed to get Ubuntu to recognise the dongle (using previous posts in this thread). Although its got its flashing blue light, when I query 'iwlist' I get "wlan0 no scan results".  It appears that whilst the drivers are loaded and recognised, the dongle doesn't seem to be transmitting (strange...). Can't get it to work at all.  On verge of giving up and buying a PCI adaptor instead

Anyone any suggestions?

---

### Post by dbld on 2007-04-26
> **Nellephant said:**
> I have similar problems with a WG111T dongle. I finally managed to get Ubuntu to recognise the dongle (using previous posts in this thread). Although its got its flashing blue light, when I query 'iwlist' I get "wlan0 no scan results".  It appears that whilst the drivers are loaded and recognised, the dongle doesn't seem to be transmitting (strange...). Can't get it to work at all.  On verge of giving up and buying a PCI adaptor instead

Anyone any suggestions?

YES DON'T BUY A PEACE OF SH1T NETGEAR,
USB WILL WORK FINE THOUGH CHOOSE ONE FORM SUPPORTED HARDWARE LIST

---

### Post by jokeeffe on 2007-04-26
Sigh! I used Synaptic Package Manager to upgrade 6.10 (working netgear wg111t) to 7.04. The upgrade went through flawlessly. I used my netgear card the entire time, no problems. I restarted today and now the device isn't showing up. Also, I started over with a fresh install of ubuntu 7.04 and try to get it to work. It doesn't and even though I download and compile 1.42 of ndiswrapper, it shows as 1.38. So, until somebody finds out the best way to get it to work on 7.04. Your best bet is 6.10.

---

### Post by fireant on 2007-04-28
Hi All,

I have managed to get my WG111T working in Feisty.
Before I explain how I did it, let me say I am a complete and utter ubuntu noob, so the way I have got it working may not be the best, but it seems to work for me.

1. Started with fresh install of feisty.

2, Compiled ndiswrapper 1.42.

3. Installed the athfmwdl.inf and netwg11t.inf files from the 1.2 version of the netgear drivers 

4. Modprobe ndiswrapper, blue light starts flashing.

athfmwdl : driver installed
netwg11t : driver installed
device (1385:4250) present

5. It did not automatically detect any wireless networks at all with iwlist scan, and I know there are at least 5 I can pick up from my neighbours, so...

6. Manually entered my network details in /etc/network/interfaces file

auto wlan0
iface wlan0 inet dhcp
wireless-essid NETGEAR
wireless-key ***********

I also commented out all the other entries to speed up the network discovery process.

7. Entered the following into rc.local as adding ndiswrapper to the /etc/modules file didn't seem to work on boot up.

modprobe ndiswrapper
/etc/init.d/networking restart

All works fine.

Hope this helps someone

---

### Post by koholint1000 on 2007-05-04
> **dbld said:**
> YES DON'T BUY A PEACE OF SH1T NETGEAR,
USB WILL WORK FINE THOUGH CHOOSE ONE FORM SUPPORTED HARDWARE LIST

Please don't use capital letters throughout your entire post, and please don't diss a brand in a thread specifically dedicated to halping out users who wish to connect a device made by that brand. The ranting helps no-one.

*exhales*

The steps above, and in quite a few other places on t'internet (on the forums and otherwise) work for most people. I have noticed that the steps tend to work better for the PCI version of this dongle (i.e. the WG311v3). Belkin Dongles have a tendency to work "out of the box" with Ubuntu and Debian (due to the natively supported Ralink chipsets), so that might be a possibility, however in my opinion Belkin wireless devices aren't as good as Netgear's (I think it's a signat integrity thing, though it might have something to do with the shape and size of my house).

Oh, and please don't swear...

---

### Post by bixio on 2007-05-16
> **fireant said:**
> Hi All,

I have managed to get my WG111T working in Feisty.
Before I explain how I did it, let me say I am a complete and utter ubuntu noob, so the way I have got it working may not be the best, but it seems to work for me.

1. Started with fresh install of feisty.

2, Compiled ndiswrapper 1.42.

3. Installed the athfmwdl.inf and netwg11t.inf files from the 1.2 version of the netgear drivers 

4. Modprobe ndiswrapper, blue light starts flashing.

athfmwdl : driver installed
netwg11t : driver installed
device (1385:4250) present

5. It did not automatically detect any wireless networks at all with iwlist scan, and I know there are at least 5 I can pick up from my neighbours, so...

6. Manually entered my network details in /etc/network/interfaces file

auto wlan0
iface wlan0 inet dhcp
wireless-essid NETGEAR
wireless-key ***********

I also commented out all the other entries to speed up the network discovery process.

7. Entered the following into rc.local as adding ndiswrapper to the /etc/modules file didn't seem to work on boot up.

modprobe ndiswrapper
/etc/init.d/networking restart

All works fine.

Hope this helps someone
I tried your instructions but when I type "modprobe ndiswrapper" the blue light doesn't start flashing and the dongle isn't detected. I only have eth0 and lo, and if I try with "sudo ifup wlan0" nothing happens (no such device). What can I do? Please help me cos nobody, in the forums where I wrote answered me!

---

### Post by mileswilliams on 2007-05-28
I managed to get mine going using the how to guide posted above this message, worth noting though that the connection dropps and restarts if the dongle gets warm.

I have a compaq machine and the exhaust fan blows over the dongle, warming it up.

I since added a length of USB extension cable and it works ! 

What gave this away for me was that it ran fine for about 10 minutes, then the connection was up and down more often than a kangaroo on a pogo stick.:roll:

---

### Post by nomisholman on 2007-06-15
> **fireant said:**
> Hi All,

I have managed to get my WG111T working in Feisty.
Before I explain how I did it, let me say I am a complete and utter ubuntu noob, so the way I have got it working may not be the best, but it seems to work for me.

1. Started with fresh install of feisty.

2, Compiled ndiswrapper 1.42.

3. Installed the athfmwdl.inf and netwg11t.inf files from the 1.2 version of the netgear drivers 

4. Modprobe ndiswrapper, blue light starts flashing.

athfmwdl : driver installed
netwg11t : driver installed
device (1385:4250) present

5. It did not automatically detect any wireless networks at all with iwlist scan, and I know there are at least 5 I can pick up from my neighbours, so...

6. Manually entered my network details in /etc/network/interfaces file

auto wlan0
iface wlan0 inet dhcp
wireless-essid NETGEAR
wireless-key ***********

I also commented out all the other entries to speed up the network discovery process.

7. Entered the following into rc.local as adding ndiswrapper to the /etc/modules file didn't seem to work on boot up.

modprobe ndiswrapper
/etc/init.d/networking restart

All works fine.

Hope this helps someone

I just tried this method and it worked fine for me:D

---

### Post by dbld on 2007-08-25
> **koholint1000 said:**
> Please don't use capitalar...

Look pal, freedom of expression is fundamental. The capital letters and swear words are the only thing i have left for Netgear falks.

And any poor soul that is trying to get this product working should take advantage of return back policy if there is one as soon as possible. Rather then spend countless hours on hacking this equipment.

Just so by the way, I have eventually got it working reason being I had to use EXACTLY same version of drivers that where packed in the box with the dongle.

And if u asking your self why i'm back here, well updated my system today and guess what ..... have to redo all the installation steps. Whilst getting the instructions I checked ur post and decided to explain my self.

Now if u got some powers to strike my post off the board do so, or else pee off. Capish!?

---

### Post by Super Kaioken on 2007-09-27
This gave me the invalid driver error.

I got a set of drivers working where it says hardware present, but it wouldn't show up in the sys->admin->networking


Update:  Ok I installed some drivers and now the computer is giving me a kernel panic- not syncing fatal exception error after I rebooted, recovery mode doesn't work either.

HELP! :(

Update again:  I unplugged the dongle and replugged it in and continued on with ifconfig, etc.  So it's detected now.  It says it's active.  but for some reason firefox isn't showing up pages..
When I do 

ndiswrapper -l

I get the athfmwdl - driver's present
               netwg11t - driver's present, hardware present

It doesn't show the driver id though.

---

### Post by BigEagle21 on 2007-10-01
wg111t works with the new Gusty. 

Place all the drivers files on the desktop, in one folder. Then install using ndisgtk with ndiswrapper. :guitar:

---

### Post by Super Kaioken on 2007-10-01
Update:  I was having problems with the WEP Encryption drivers for the WG111T.  I used MAC Filters instead.  Is using MAC Filters instead of a WEP key safer and more secure?

---

### Post by Multivitamin on 2008-03-30
Please delete, i post in the wrong thread :(

---

