---
title: "broadcom wifi driver: so clueless how to do this!"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by vegas-steven on 2009-03-24
ok so here is the deal:

last nite I ran the live cd and saw that my hp ze4900 broadcom driver was found.
all other hardware appears to work well so I went ahead and installed the full os.

after it started, I went to the hardware portion of the system and the broadcom card was not found 

I am really great in windows (I repair them for ppl as a side job) and I am trying now to learn Linux by way of ubuntu...
but I am LOST.
I've read that the os may see the device but has no firmware for it because of legal reasons. 
I can get the zip file with the driver from hp however I have no idea where to go from there.

is there some straight forward place with a guide for this?
where do I start?

thanks so much for any nudge in the right direction.

---

### Post by Teamgeist on 2009-03-24
Hi.

Have you looked under System--> Administration--> Hardware Drivers ?

The driver might just have to be downloaded and activated. You will need to have a wired connection to the internet to do so.

And you're right, Ubuntu does not ship this driver because it is closed source.

---

### Post by jordilin on 2009-03-24
I have a broadcom as well, and drivers (Intrepid Ibex 64bit) were successfully installed using System->Administration->Hardware Drivers.
Type:
```
lspci | grep Broadcom
```
and tell what do you get.

---

### Post by vegas-steven on 2009-03-24
ok well when I get a chance I'll run it...



the live cd showed the adapter from the connection menu (I think) and the full install showed nothing.
I'm on my iphone ATM so when I get to it I'll take a run at the method you guys described.

I can't even get the hardware switch to light up when I press the button... hope this ends up beind straightforward.

---

### Post by achase79 on 2009-03-24
I have to extract my firmware (using fwcutter) for my broadcom card.

---

### Post by Teamgeist on 2009-03-24
> **vegas-steven said:**
> .. hope this ends up beind straightforward.

We'll see. Just try System--> Administration--> Hardware Drivers and post back.

---

### Post by vegas-steven on 2009-03-24
ok so going system - administration - hardware drivers shows:

no properiatary drivers are installed on this system

where to now?

---

### Post by lkraemer on 2009-03-25
First check to see what Broadcom card you have.
```

lshw -C network
ndiswrapper -l 


```

Post the output of the above.

Then, If it is a Broadcom card...............

OK, go here and download the b43-all-fw.tar.gz file:
[http://www.omattos.com/broadcom/](http://www.omattos.com/broadcom/)

You are getting all of the Broadcom Firmware.

I assume you will be saving the file to your Desktop.
In your GUI copy the downloaded file to a folder under
/home/yourloginname/Downloads/Broadcom_Firmware

Make sure you substitute your login name everywhere yourloginname
is located below.

Let's assume it's Broadcom_Firmware.

In a Terminal window do:
```

cd /
cd /home/yourloginname/Downloads/Broadcom_Firmware
tar zxvf b43-all-fw.tar.gz

```
Copy the folder b43 to /lib/firmware/b43

You should be able to get your wireless functional right from the terminal window.
```

sudo modprobe b43xx
dmesg
iwconfig

```
This will tell you the Wifi's identification....wlan0, ath0, wifi0, etc.

Assume your ID is wlan0...so substitute wlan0 everywhere there is a
<interface> in the code below. Turn on your Wifi switch if there is one,
or use CNTL F2 or whatever keystrokes enable your Wifi. Insert your
essid (UPPERCASE or lowercase specific)
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>

```
You should be able to surf, even though your LED for Wifi isn't "ON".
It may never work, but that is OK!

ref URL:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

If you are using WEP or WPA or WPA2 see URL above.

another ref URL:
[http://ubuntuforums.org/showthread.php?t=607410](http://ubuntuforums.org/showthread.php?t=607410)


lkraemer

---

### Post by vegas-steven on 2009-03-25
well how dumb do i feel.

i am so lost in terminal commands.
i am a product of a windows 95 and up generation.

so i run the first command and i get:

> stevenj@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:51:07:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.140 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:97:6b:12
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c6:84:9f:d2:c1:c5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



THEN... i run the second command and get:

> 
stevenj@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found


seeing as i am a neophyte i am a little worried about running the command by typing as suggested... anyhow, thats what i get.

---

### Post by vegas-steven on 2009-03-25
something went wrong.
i went ahead and entered from terminal as posted, and when i got to this point:

> cd /B43
ls -alt
cp *.fw /lib/firmware
cd /
pwd

i enter the next command and get:

> total 176
drwxr-xr-x 4 stevenj stevenj  4096 2009-03-24 22:50 ..
drwxr-xr-x 2 stevenj stevenj  4096 2008-04-19 04:36 .
-rw-r--r-- 1 stevenj stevenj    18 2008-04-18 11:27 a0g0bsinitvals4.fw
-rw-r--r-- 1 stevenj stevenj   158 2008-04-18 11:27 a0g0bsinitvals5.fw
-rw-r--r-- 1 stevenj stevenj  2680 2008-04-18 11:27 a0g0initvals4.fw
-rw-r--r-- 1 stevenj stevenj  1858 2008-04-18 11:27 a0g0initvals5.fw
-rw-r--r-- 1 stevenj stevenj   158 2008-04-18 11:27 a0g1bsinitvals13.fw
-rw-r--r-- 1 stevenj stevenj   158 2008-04-18 11:27 a0g1bsinitvals5.fw
-rw-r--r-- 1 stevenj stevenj  2056 2008-04-18 11:27 a0g1initvals13.fw
-rw-r--r-- 1 stevenj stevenj  1858 2008-04-18 11:27 a0g1initvals5.fw
-rw-r--r-- 1 stevenj stevenj   158 2008-04-18 11:27 b0g0bsinitvals13.fw
-rw-r--r-- 1 stevenj stevenj    18 2008-04-18 11:27 b0g0bsinitvals4.fw
-rw-r--r-- 1 stevenj stevenj   158 2008-04-18 11:27 b0g0bsinitvals5.fw
-rw-r--r-- 1 stevenj stevenj  2056 2008-04-18 11:27 b0g0initvals13.fw
-rw-r--r-- 1 stevenj stevenj  2680 2008-04-18 11:27 b0g0initvals4.fw
-rw-r--r-- 1 stevenj stevenj  1858 2008-04-18 11:27 b0g0initvals5.fw
-rw-r--r-- 1 stevenj stevenj   158 2008-04-18 11:27 lp0bsinitvals13.fw
-rw-r--r-- 1 stevenj stevenj  2052 2008-04-18 11:27 lp0initvals13.fw
-rw-r--r-- 1 stevenj stevenj  1320 2008-04-18 11:27 pcm4.fw
-rw-r--r-- 1 stevenj stevenj  1320 2008-04-18 11:27 pcm5.fw
-rw-r--r-- 1 stevenj stevenj 26600 2008-04-18 11:27 ucode11.fw
-rw-r--r-- 1 stevenj stevenj 24424 2008-04-18 11:27 ucode13.fw
-rw-r--r-- 1 stevenj stevenj 20080 2008-04-18 11:27 ucode4.fw
-rw-r--r-- 1 stevenj stevenj 22088 2008-04-18 11:27 ucode5.fw
stevenj@ubuntu:~/Downloads/Broadcom_Firmware/b43$ cp *.fw /lib/firmware
cp: cannot create regular file `/lib/firmware/a0g0bsinitvals4.fw': Permission denied
cp: cannot create regular file `/lib/firmware/a0g0bsinitvals5.fw': Permission denied
cp: cannot create regular file `/lib/firmware/a0g0initvals4.fw': Permission denied
cp: cannot create regular file `/lib/firmware/a0g0initvals5.fw': Permission denied
cp: cannot create regular file `/lib/firmware/a0g1bsinitvals13.fw': Permission denied
cp: cannot create regular file `/lib/firmware/a0g1bsinitvals5.fw': Permission denied
cp: cannot create regular file `/lib/firmware/a0g1initvals13.fw': Permission denied
cp: cannot create regular file `/lib/firmware/a0g1initvals5.fw': Permission denied
cp: cannot create regular file `/lib/firmware/b0g0bsinitvals13.fw': Permission denied
cp: cannot create regular file `/lib/firmware/b0g0bsinitvals4.fw': Permission denied
cp: cannot create regular file `/lib/firmware/b0g0bsinitvals5.fw': Permission denied
cp: cannot create regular file `/lib/firmware/b0g0initvals13.fw': Permission denied
cp: cannot create regular file `/lib/firmware/b0g0initvals4.fw': Permission denied
cp: cannot create regular file `/lib/firmware/b0g0initvals5.fw': Permission denied
cp: cannot create regular file `/lib/firmware/lp0bsinitvals13.fw': Permission denied
cp: cannot create regular file `/lib/firmware/lp0initvals13.fw': Permission denied
cp: cannot create regular file `/lib/firmware/pcm4.fw': Permission denied
cp: cannot create regular file `/lib/firmware/pcm5.fw': Permission denied
cp: cannot create regular file `/lib/firmware/ucode11.fw': Permission denied
cp: cannot create regular file `/lib/firmware/ucode13.fw': Permission denied
cp: cannot create regular file `/lib/firmware/ucode4.fw': Permission denied
cp: cannot create regular file `/lib/firmware/ucode5.fw': Permission denied
stevenj@ubuntu:~/Downloads/Broadcom_Firmware/b43$ cd /
stevenj@ubuntu:/$ pwd


And then after i get:

> stevenj@ubuntu:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


so i cant see where it identifies my lan at all. seems it doesnt see it whatsoever and i cannot continue on.

---

### Post by vegas-steven on 2009-03-25
UPDATE...

somehow after i went back into system - admin - hardware drivers it FOUND the broadcom hardware and installed a driver for it.

now i have my wifi light on and the hardware working.
i can even use the network icon at the top to enable/disable the hardware, however i cannot scan for networks...

i am using the command "iwlist scan" and it comes up with "no scan results" which is false because there are at least 5-10 networks near me at any given time here in my home.

so any ideas?

i tried adding manually selecting edit connections with right click, then wireless tab, then adding my ssid and ifastructure mode, under wireless security wpa and wpa2 personal and then putting in the key that it needs.

SOMEHOW i had it requesting and trying to join even and then i got a prompt asking me for the CORRECT password, which makes no sense as its the same password (checked it on my iphone, all is working fine)

thanks again for any suggestions!

---

### Post by lkraemer on 2009-03-25
OK,
The ndiswrapper -l command told us it isn't installed so we know
that no drivers are loaded with ndiswrapper that might have been
a conflict.  This is GOOD.

SLOW DOWN!  You're not in Wonders, and in a terminal window you
are configuring the Wifi just as you would in DOS from a Command prompt.

The iwconfig command did find your Wifi as noted below.
```

wlan0 IEEE 802.11bg ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=0 dBm 
................................................

```
but you haven't told it what the ESSID is just yet...........
Now you're getting it.......aren't you????????


Now, back to where we were before you jumped the gun.......

The copy command (cp) didn't work for some reason.  Maybe the subdirectory
(folder) /lib/firmware doesn't exist.  You can check that with the following:
Open a terminal window:
```

cd /
cd /lib
pwd
ls -alt
cd /firmware
pwd
ls -alt


```

and post the output.

These commands were just to get it working manually the first time from
the terminal.
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>

```
From now on you will be in the GUI using what you have manually tested.

I am referencing 8.04 LTS as I haven't used 8.10 or later versions.
Once you have it working you will need to use the wireless icon on the top
right of the display to select your network to attach to.  Move the mouse
cursor over the network icon and left click.  Your wireless AP's that are
local and seen should be there for you to select.  (You won't need the terminal commands any more.)

My iwconfig produces:
```

larry@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Airlink"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:A5:81:D0:D2   
          Bit Rate:24 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-49 dBm  Noise level=-96 dBm
          Rx invalid nwid:350  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
in which Airlink is one of my choices from the top icon display.

lkraemer

---

### Post by vegas-steven on 2009-03-25
thanks for the reply. i wont be able to check into it until later on today.

---

### Post by sanemanmad on 2009-03-25
Hi, Please take a look at my post before you start installing software on your GNU OS. :)

[http://ubuntuforums.org/showpost.php?p=6948594&postcount=1426](http://ubuntuforums.org/showpost.php?p=6948594&postcount=1426)

---

### Post by lkraemer on 2009-03-25
sanemanmad,
What software are you referencing when you say do not install software
on a new system?

Are you saying that copying the *.fw files to /lib/firmware is installing
software?  I'd think it is more like moving data files for Ubuntu to use,
versus installing software.

Ndiswrapper wasn't referenced as to being installed.

There must be Windows drivers used by ndiswrapper, OR firmware used
to allow the hardware to work, OR the madwifi driver software installed
to get the Wifi working.  I happened to pick the *.fw method.

Maybe I am confused?  Explain in more detail.....Please.

lkraemer

---

### Post by abn91c on 2009-03-25
> **Teamgeist said:**
> We'll see. Just try System--> Administration--> Hardware Drivers and post back.
do the above however to "activate" the drivers you need to connect by wire in order for the drivers to be downloaded to the computer, then you can activate the card and use it.

---

### Post by MrWES on 2009-03-25
Part of the problem is you must enable the multiverse repositories ,etc. and run an update to get the third party drivers for the card. I've actually seen this many many times, and most go for the ndiswrapper right away when it really isn't necessary. The development team needs to make that easier that it current is.

Bill

---

### Post by anewguy on 2009-03-25
Here's the reason some of us end up recommending ndiswrapper:

You don't have access to connecting hard-wired, only by wireless (I've seen this several times for whatever reasons).  Now you CAN'T connect to do the update and upgrade, you can't connect to download anything.  Not always, by any means, by usually the Windows driver is available on a CD, etc..  Without any internet access at all, ndiswrapper can be installed, the windows driver can be installed and the wireless adaptor works.  Doesn't mean it's the only way, doesn't mean it's the best way, just that it works.

My contention with the newer tools (fwcutter, etc.) is that more needs to be included on the install so that these tools can be used, and the wireless activated, without having net access.  I suspect it is a combination of a large number of drivers/firmware and the idea that a lot of it may be closed source, but I don't know.

I think we would all agree that the easiest way may be different from user to user, from whether the net is available by hard wire, etc..  Depending on the user, sometimes ndiswrapper may be the quickest/least amount of hassle way to get them up.  It just all depends.  The firmware cutter, the b43 driver, ndiswrapper - they all have their place.  No one of those tools is better than the other.

As for the user having the copies fail - you did notice it said permissions denied?  Re-run the copy with sudo in front.

Dave :)

---

### Post by vegas-steven on 2009-03-26
pessimistic...

this sounds ultra complicated.
i wont fault the os as it isnt as mainstream as windows is... so i dont expect it to work out of the box as well as windows does.
i am actually impressed with how complete it WAS from the get go on my older hardware, but this is an integral part of getting my laptop usable and it is getting a little complex.

so at that, here is what happened when i ran the command as recommended before the little debate there:

this command:
cd /
cd /lib
pwd
ls -alt
cd /firmware
pwd
ls -al

produced this in terminal:
> stevenj@ubuntu:~$ cd /
stevenj@ubuntu:/$ cd /lib
stevenj@ubuntu:/lib$ pwd
/lib
stevenj@ubuntu:/lib$ ls -alt
total 9232
drwxr-xr-x 21 root root    4096 2009-03-25 00:38 ..
drwxr-xr-x  2 root root    4096 2009-03-25 00:32 security
drwxr-xr-x  3 root root    4096 2009-03-25 00:30 udev
drwxr-xr-x  4 root root    4096 2009-03-25 00:25 linux-restricted-modules
drwxr-xr-x  8 root root    4096 2009-03-25 00:25 firmware
drwxr-xr-x  4 root root    4096 2009-03-25 00:24 modules
drwxr-xr-x 16 root root   12288 2009-03-25 00:24 .
lrwxrwxrwx  1 root root      22 2009-03-25 00:24 libvolume_id.so.0 -> libvolume_id.so.0.85.0
lrwxrwxrwx  1 root root      17 2009-03-25 00:24 libpamc.so.0 -> libpamc.so.0.81.0
lrwxrwxrwx  1 root root      21 2009-03-25 00:24 libpam_misc.so.0 -> libpam_misc.so.0.81.3
lrwxrwxrwx  1 root root      17 2009-03-25 00:24 libpam.so.0 -> libpam.so.0.81.12
lrwxrwxrwx  1 root root      12 2009-03-25 00:23 ld-linux.so.2 -> ld-2.8.90.so
lrwxrwxrwx  1 root root      16 2009-03-25 00:23 libanl.so.1 -> libanl-2.8.90.so
lrwxrwxrwx  1 root root      25 2009-03-25 00:23 libBrokenLocale.so.1 -> libBrokenLocale-2.8.90.so
lrwxrwxrwx  1 root root      17 2009-03-25 00:23 libcidn.so.1 -> libcidn-2.8.90.so
lrwxrwxrwx  1 root root      18 2009-03-25 00:23 libcrypt.so.1 -> libcrypt-2.8.90.so
lrwxrwxrwx  1 root root      14 2009-03-25 00:23 libc.so.6 -> libc-2.8.90.so
lrwxrwxrwx  1 root root      15 2009-03-25 00:23 libdl.so.2 -> libdl-2.8.90.so
lrwxrwxrwx  1 root root      14 2009-03-25 00:23 libm.so.6 -> libm-2.8.90.so
lrwxrwxrwx  1 root root      16 2009-03-25 00:23 libnsl.so.1 -> libnsl-2.8.90.so
lrwxrwxrwx  1 root root      23 2009-03-25 00:23 libnss_compat.so.2 -> libnss_compat-2.8.90.so
lrwxrwxrwx  1 root root      20 2009-03-25 00:23 libnss_dns.so.2 -> libnss_dns-2.8.90.so
lrwxrwxrwx  1 root root      22 2009-03-25 00:23 libnss_files.so.2 -> libnss_files-2.8.90.so
lrwxrwxrwx  1 root root      23 2009-03-25 00:23 libnss_hesiod.so.2 -> libnss_hesiod-2.8.90.so
lrwxrwxrwx  1 root root      24 2009-03-25 00:23 libnss_nisplus.so.2 -> libnss_nisplus-2.8.90.so
lrwxrwxrwx  1 root root      20 2009-03-25 00:23 libnss_nis.so.2 -> libnss_nis-2.8.90.so
lrwxrwxrwx  1 root root      20 2009-03-25 00:23 libpthread.so.0 -> libpthread-2.8.90.so
lrwxrwxrwx  1 root root      19 2009-03-25 00:23 libresolv.so.2 -> libresolv-2.8.90.so
lrwxrwxrwx  1 root root      15 2009-03-25 00:23 librt.so.1 -> librt-2.8.90.so
lrwxrwxrwx  1 root root      19 2009-03-25 00:23 libthread_db.so.1 -> libthread_db-1.0.so
lrwxrwxrwx  1 root root      17 2009-03-25 00:23 libutil.so.1 -> libutil-2.8.90.so
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libslang.so.2 -> libslang.so.2.1.3
lrwxrwxrwx  1 root root      12 2009-03-23 17:44 libss.so.2 -> libss.so.2.0
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libsysfs.so.2 -> libsysfs.so.2.0.1
lrwxrwxrwx  1 root root      13 2009-03-23 17:44 libtic.so.5 -> libtic.so.5.6
lrwxrwxrwx  1 root root      14 2009-03-23 17:44 libticw.so.5 -> libticw.so.5.6
lrwxrwxrwx  1 root root      20 2009-03-23 17:44 libulockmgr.so.1 -> libulockmgr.so.1.0.1
lrwxrwxrwx  1 root root      19 2009-03-23 17:44 libusb-0.1.so.4 -> libusb-0.1.so.4.4.4
lrwxrwxrwx  1 root root      14 2009-03-23 17:44 libuuid.so.1 -> libuuid.so.1.2
lrwxrwxrwx  1 root root      16 2009-03-23 17:44 libwrap.so.0 -> libwrap.so.0.7.6
lrwxrwxrwx  1 root root      21 2009-03-23 17:44 cpp -> /etc/alternatives/cpp
lrwxrwxrwx  1 root root      15 2009-03-23 17:44 libacl.so.1 -> libacl.so.1.1.0
lrwxrwxrwx  1 root root      15 2009-03-23 17:44 libatm.so.1 -> libatm.so.1.0.0
lrwxrwxrwx  1 root root      16 2009-03-23 17:44 libattr.so.1 -> libattr.so.1.1.0
lrwxrwxrwx  1 root root      15 2009-03-23 17:44 libblkid.so.1 -> libblkid.so.1.0
lrwxrwxrwx  1 root root      18 2009-03-23 17:44 libbrlapi.so.0.5 -> libbrlapi.so.0.5.2
lrwxrwxrwx  1 root root      15 2009-03-23 17:44 libbz2.so.1 -> libbz2.so.1.0.4
lrwxrwxrwx  1 root root      15 2009-03-23 17:44 libbz2.so.1.0 -> libbz2.so.1.0.4
lrwxrwxrwx  1 root root      14 2009-03-23 17:44 libcap.so.1 -> libcap.so.1.10
lrwxrwxrwx  1 root root      14 2009-03-23 17:44 libcap.so.2 -> libcap.so.2.10
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libcom_err.so.2 -> libcom_err.so.2.1
lrwxrwxrwx  1 root root      18 2009-03-23 17:44 libdbus-1.so.3 -> libdbus-1.so.3.4.0
lrwxrwxrwx  1 root root      13 2009-03-23 17:44 libe2p.so.2 -> libe2p.so.2.3
lrwxrwxrwx  1 root root      16 2009-03-23 17:44 libext2fs.so.2 -> libext2fs.so.2.4
lrwxrwxrwx  1 root root      16 2009-03-23 17:44 libfuse.so.2 -> libfuse.so.2.7.3
lrwxrwxrwx  1 root root      19 2009-03-23 17:44 libgcrypt.so.11 -> libgcrypt.so.11.4.4
lrwxrwxrwx  1 root root      21 2009-03-23 17:44 libgpg-error.so.0 -> libgpg-error.so.0.3.0
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libhistory.so.5 -> libhistory.so.5.2
lrwxrwxrwx  1 root root      18 2009-03-23 17:44 libkeyutils.so.1 -> libkeyutils-1.2.so
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libncurses.so.5 -> libncurses.so.5.6
lrwxrwxrwx  1 root root      18 2009-03-23 17:44 libncursesw.so.5 -> libncursesw.so.5.6
lrwxrwxrwx  1 root root      20 2009-03-23 17:44 libntfs-3g.so.28 -> libntfs-3g.so.28.0.0
lrwxrwxrwx  1 root root      22 2009-03-23 17:44 libparted-1.8.so.9 -> libparted-1.8.so.9.0.0
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libpcre.so.3 -> libpcre.so.3.12.1
lrwxrwxrwx  1 root root      16 2009-03-23 17:44 libpopt.so.0 -> libpopt.so.0.0.0
lrwxrwxrwx  1 root root      18 2009-03-23 17:44 libreadline.so.5 -> libreadline.so.5.2
-rwxr-xr-x  1 root root  112055 2009-01-29 02:23 libpthread-2.8.90.so
-rwxr-xr-x  1 root root  113252 2009-01-29 02:23 ld-2.8.90.so
-rw-r--r--  1 root root    9804 2009-01-29 02:23 libanl-2.8.90.so
-rw-r--r--  1 root root    5440 2009-01-29 02:23 libBrokenLocale-2.8.90.so
-rwxr-xr-x  1 root root 1315024 2009-01-29 02:23 libc-2.8.90.so
-rw-r--r--  1 root root  185820 2009-01-29 02:23 libcidn-2.8.90.so
-rw-r--r--  1 root root   38300 2009-01-29 02:23 libcrypt-2.8.90.so
-rw-r--r--  1 root root    9676 2009-01-29 02:23 libdl-2.8.90.so
-rw-r--r--  1 root root  149332 2009-01-29 02:23 libm-2.8.90.so
-rw-r--r--  1 root root   13692 2009-01-29 02:23 libmemusage.so
-rw-r--r--  1 root root   79612 2009-01-29 02:23 libnsl-2.8.90.so
-rw-r--r--  1 root root   30436 2009-01-29 02:23 libnss_compat-2.8.90.so
-rw-r--r--  1 root root   17884 2009-01-29 02:23 libnss_dns-2.8.90.so
-rw-r--r--  1 root root   38412 2009-01-29 02:23 libnss_files-2.8.90.so
-rw-r--r--  1 root root   17896 2009-01-29 02:23 libnss_hesiod-2.8.90.so
-rw-r--r--  1 root root   34352 2009-01-29 02:23 libnss_nis-2.8.90.so
-rw-r--r--  1 root root   46604 2009-01-29 02:23 libnss_nisplus-2.8.90.so
-rw-r--r--  1 root root    5440 2009-01-29 02:23 libpcprofile.so
-rw-r--r--  1 root root   63312 2009-01-29 02:23 libresolv-2.8.90.so
-rw-r--r--  1 root root   30624 2009-01-29 02:23 librt-2.8.90.so
-rw-r--r--  1 root root   13692 2009-01-29 02:23 libSegFault.so
-rw-r--r--  1 root root   30384 2009-01-29 02:23 libthread_db-1.0.so
-rw-r--r--  1 root root    9688 2009-01-29 02:23 libutil-2.8.90.so
-rw-r--r--  1 root root   54740 2009-01-23 12:14 libgcc_s.so.1
-rw-r--r--  1 root root   21884 2009-01-05 06:53 libnss_winbind.so.2
-rw-r--r--  1 root root 1841636 2009-01-05 06:53 libnss_wins.so.2
-rw-r--r--  1 root root    9576 2008-11-11 06:48 libpamc.so.0.81.0
-rw-r--r--  1 root root    9588 2008-11-11 06:48 libpam_misc.so.0.81.3
-rw-r--r--  1 root root   42476 2008-11-11 06:48 libpam.so.0.81.12
-rw-r--r--  1 root root   30024 2008-11-03 10:12 libvolume_id.so.0.85.0
-rw-r--r--  1 root root   59080 2008-10-29 21:11 libproc-3.2.7.so
drwxr-xr-x  3 root root    4096 2008-10-29 16:02 brltty
drwxr-xr-x  3 root root    4096 2008-10-29 16:02 init
drwxr-xr-x  2 root root    4096 2008-10-29 16:00 linux-sound-base
drwxr-xr-x  2 root root    4096 2008-10-29 16:00 iptables
drwxr-xr-x  2 root root    4096 2008-10-29 15:58 dbus-1.0
drwxr-xr-x  3 root root    4096 2008-10-29 15:54 tls
drwxr-xr-x  2 root root    4096 2008-10-29 15:53 lsb
-rw-r--r--  1 root root   91792 2008-10-20 14:14 libdevmapper.so.1.02.1
-rw-r--r--  1 root root  447108 2008-10-16 15:10 libusplash.so.0
-rw-r--r--  1 root root   22624 2008-10-13 06:10 libe2p.so.2.3
-rw-r--r--  1 root root   40612 2008-10-13 06:09 libblkid.so.1.0
-rw-r--r--  1 root root    9576 2008-10-13 06:09 libcom_err.so.2.1
-rw-r--r--  1 root root  166236 2008-10-13 06:09 libext2fs.so.2.4
-rw-r--r--  1 root root   21976 2008-10-13 06:09 libss.so.2.0
-rw-r--r--  1 root root   13872 2008-10-13 06:09 libuuid.so.1.2
-rw-r--r--  1 root root  222816 2008-10-07 07:23 libdbus-1.so.3.4.0
drwxr-xr-x  2 root root    4096 2008-09-29 03:32 i486-linux-gnu
-rw-r--r--  1 root root  108992 2008-09-25 09:06 libfuse.so.2.7.3
-rw-r--r--  1 root root    9540 2008-09-25 09:06 libulockmgr.so.1.0.1
-rw-r--r--  1 root root  396300 2008-09-12 07:31 libparted-1.8.so.9.0.0
-rw-r--r--  1 root root   38648 2008-08-06 02:09 libbrlapi.so.0.5.2
-rwxr-xr-x  1 root root   64704 2008-08-03 19:19 klibc-zUXi_KjK5ZQAIyc8jlwme9T6a4U.so
-rw-r--r--  1 root root  165124 2008-08-01 15:48 libpcre.so.3.12.1
-rw-r--r--  1 root root  697288 2008-07-21 15:43 libslang.so.2.1.3
-rw-r--r--  1 root root   99972 2008-07-15 08:59 libselinux.so.1
-rw-r--r--  1 root root  214716 2008-07-15 06:03 libsepol.so.1
-rw-r--r--  1 root root  186516 2008-07-10 02:12 libntfs-3g.so.28.0.0
-rw-r--r--  1 root root  423876 2008-07-02 01:43 libgcrypt.so.11.4.4
-rw-r--r--  1 root root    9440 2008-06-30 12:13 libx86.so.1
-rw-r--r--  1 root root   34640 2008-06-26 01:24 libpopt.so.0.0.0
-rw-r--r--  1 root root   70020 2008-06-23 01:02 libbz2.so.1.0.4
-rw-r--r--  1 root root   13792 2008-06-12 06:39 libcap.so.2.10
-rw-r--r--  1 root root   31072 2008-06-12 05:50 libusb-0.1.so.4.4.4
-rw-r--r--  1 root root   30960 2008-05-03 00:14 libwrap.so.0.7.6
-rw-r--r--  1 root root   34464 2008-05-02 23:44 libatm.so.1.0.0
-rw-r--r--  1 root root    9436 2008-05-02 18:19 libkeyutils-1.2.so
-rw-r--r--  1 root root   17760 2008-05-02 17:27 libattr.so.1.1.0
-rw-r--r--  1 root root   26156 2008-05-02 17:01 libacl.so.1.1.0
-rw-r--r--  1 root root    7552 2008-04-18 14:28 libnss_mdns4_minimal.so.2
-rw-r--r--  1 root root    8148 2008-04-18 14:28 libnss_mdns4.so.2
-rw-r--r--  1 root root    7616 2008-04-18 14:28 libnss_mdns6_minimal.so.2
-rw-r--r--  1 root root    8196 2008-04-18 14:28 libnss_mdns6.so.2
-rw-r--r--  1 root root    8172 2008-04-18 14:28 libnss_mdns_minimal.so.2
-rw-r--r--  1 root root    8580 2008-04-18 14:28 libnss_mdns.so.2
-rw-r--r--  1 root root   37784 2008-04-01 10:03 libsysfs.so.2.0.1
-rw-r--r--  1 root root  190584 2008-02-23 15:38 libncurses.so.5.6
-rw-r--r--  1 root root  236568 2008-02-23 15:38 libncursesw.so.5.6
-rw-r--r--  1 root root   69952 2008-02-23 15:38 libtic.so.5.6
-rw-r--r--  1 root root   69952 2008-02-23 15:38 libticw.so.5.6
drwxr-xr-x 15 root root    4096 2008-02-23 15:38 terminfo
-rw-r--r--  1 root root   27444 2007-12-21 06:36 libiw.so.29
-rw-r--r--  1 root root   11468 2007-11-15 16:56 libgpg-error.so.0.3.0
-rw-r--r--  1 root root   27188 2007-10-02 07:35 libhistory.so.5.2
-rw-r--r--  1 root root  196560 2007-10-02 07:35 libreadline.so.5.2
-rw-r--r--  1 root root   10316 2007-07-31 12:20 libcap.so.1.10
stevenj@ubuntu:/lib$ cd /firmware
bash: cd: /firmware: No such file or directory
stevenj@ubuntu:/lib$ pwd
/lib
stevenj@ubuntu:/lib$ ls -alt
total 9232
drwxr-xr-x 21 root root    4096 2009-03-25 00:38 ..
drwxr-xr-x  2 root root    4096 2009-03-25 00:32 security
drwxr-xr-x  3 root root    4096 2009-03-25 00:30 udev
drwxr-xr-x  4 root root    4096 2009-03-25 00:25 linux-restricted-modules
drwxr-xr-x  8 root root    4096 2009-03-25 00:25 firmware
drwxr-xr-x  4 root root    4096 2009-03-25 00:24 modules
drwxr-xr-x 16 root root   12288 2009-03-25 00:24 .
lrwxrwxrwx  1 root root      22 2009-03-25 00:24 libvolume_id.so.0 -> libvolume_id.so.0.85.0
lrwxrwxrwx  1 root root      17 2009-03-25 00:24 libpamc.so.0 -> libpamc.so.0.81.0
lrwxrwxrwx  1 root root      21 2009-03-25 00:24 libpam_misc.so.0 -> libpam_misc.so.0.81.3
lrwxrwxrwx  1 root root      17 2009-03-25 00:24 libpam.so.0 -> libpam.so.0.81.12
lrwxrwxrwx  1 root root      12 2009-03-25 00:23 ld-linux.so.2 -> ld-2.8.90.so
lrwxrwxrwx  1 root root      16 2009-03-25 00:23 libanl.so.1 -> libanl-2.8.90.so
lrwxrwxrwx  1 root root      25 2009-03-25 00:23 libBrokenLocale.so.1 -> libBrokenLocale-2.8.90.so
lrwxrwxrwx  1 root root      17 2009-03-25 00:23 libcidn.so.1 -> libcidn-2.8.90.so
lrwxrwxrwx  1 root root      18 2009-03-25 00:23 libcrypt.so.1 -> libcrypt-2.8.90.so
lrwxrwxrwx  1 root root      14 2009-03-25 00:23 libc.so.6 -> libc-2.8.90.so
lrwxrwxrwx  1 root root      15 2009-03-25 00:23 libdl.so.2 -> libdl-2.8.90.so
lrwxrwxrwx  1 root root      14 2009-03-25 00:23 libm.so.6 -> libm-2.8.90.so
lrwxrwxrwx  1 root root      16 2009-03-25 00:23 libnsl.so.1 -> libnsl-2.8.90.so
lrwxrwxrwx  1 root root      23 2009-03-25 00:23 libnss_compat.so.2 -> libnss_compat-2.8.90.so
lrwxrwxrwx  1 root root      20 2009-03-25 00:23 libnss_dns.so.2 -> libnss_dns-2.8.90.so
lrwxrwxrwx  1 root root      22 2009-03-25 00:23 libnss_files.so.2 -> libnss_files-2.8.90.so
lrwxrwxrwx  1 root root      23 2009-03-25 00:23 libnss_hesiod.so.2 -> libnss_hesiod-2.8.90.so
lrwxrwxrwx  1 root root      24 2009-03-25 00:23 libnss_nisplus.so.2 -> libnss_nisplus-2.8.90.so
lrwxrwxrwx  1 root root      20 2009-03-25 00:23 libnss_nis.so.2 -> libnss_nis-2.8.90.so
lrwxrwxrwx  1 root root      20 2009-03-25 00:23 libpthread.so.0 -> libpthread-2.8.90.so
lrwxrwxrwx  1 root root      19 2009-03-25 00:23 libresolv.so.2 -> libresolv-2.8.90.so
lrwxrwxrwx  1 root root      15 2009-03-25 00:23 librt.so.1 -> librt-2.8.90.so
lrwxrwxrwx  1 root root      19 2009-03-25 00:23 libthread_db.so.1 -> libthread_db-1.0.so
lrwxrwxrwx  1 root root      17 2009-03-25 00:23 libutil.so.1 -> libutil-2.8.90.so
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libslang.so.2 -> libslang.so.2.1.3
lrwxrwxrwx  1 root root      12 2009-03-23 17:44 libss.so.2 -> libss.so.2.0
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libsysfs.so.2 -> libsysfs.so.2.0.1
lrwxrwxrwx  1 root root      13 2009-03-23 17:44 libtic.so.5 -> libtic.so.5.6
lrwxrwxrwx  1 root root      14 2009-03-23 17:44 libticw.so.5 -> libticw.so.5.6
lrwxrwxrwx  1 root root      20 2009-03-23 17:44 libulockmgr.so.1 -> libulockmgr.so.1.0.1
lrwxrwxrwx  1 root root      19 2009-03-23 17:44 libusb-0.1.so.4 -> libusb-0.1.so.4.4.4
lrwxrwxrwx  1 root root      14 2009-03-23 17:44 libuuid.so.1 -> libuuid.so.1.2
lrwxrwxrwx  1 root root      16 2009-03-23 17:44 libwrap.so.0 -> libwrap.so.0.7.6
lrwxrwxrwx  1 root root      21 2009-03-23 17:44 cpp -> /etc/alternatives/cpp
lrwxrwxrwx  1 root root      15 2009-03-23 17:44 libacl.so.1 -> libacl.so.1.1.0
lrwxrwxrwx  1 root root      15 2009-03-23 17:44 libatm.so.1 -> libatm.so.1.0.0
lrwxrwxrwx  1 root root      16 2009-03-23 17:44 libattr.so.1 -> libattr.so.1.1.0
lrwxrwxrwx  1 root root      15 2009-03-23 17:44 libblkid.so.1 -> libblkid.so.1.0
lrwxrwxrwx  1 root root      18 2009-03-23 17:44 libbrlapi.so.0.5 -> libbrlapi.so.0.5.2
lrwxrwxrwx  1 root root      15 2009-03-23 17:44 libbz2.so.1 -> libbz2.so.1.0.4
lrwxrwxrwx  1 root root      15 2009-03-23 17:44 libbz2.so.1.0 -> libbz2.so.1.0.4
lrwxrwxrwx  1 root root      14 2009-03-23 17:44 libcap.so.1 -> libcap.so.1.10
lrwxrwxrwx  1 root root      14 2009-03-23 17:44 libcap.so.2 -> libcap.so.2.10
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libcom_err.so.2 -> libcom_err.so.2.1
lrwxrwxrwx  1 root root      18 2009-03-23 17:44 libdbus-1.so.3 -> libdbus-1.so.3.4.0
lrwxrwxrwx  1 root root      13 2009-03-23 17:44 libe2p.so.2 -> libe2p.so.2.3
lrwxrwxrwx  1 root root      16 2009-03-23 17:44 libext2fs.so.2 -> libext2fs.so.2.4
lrwxrwxrwx  1 root root      16 2009-03-23 17:44 libfuse.so.2 -> libfuse.so.2.7.3
lrwxrwxrwx  1 root root      19 2009-03-23 17:44 libgcrypt.so.11 -> libgcrypt.so.11.4.4
lrwxrwxrwx  1 root root      21 2009-03-23 17:44 libgpg-error.so.0 -> libgpg-error.so.0.3.0
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libhistory.so.5 -> libhistory.so.5.2
lrwxrwxrwx  1 root root      18 2009-03-23 17:44 libkeyutils.so.1 -> libkeyutils-1.2.so
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libncurses.so.5 -> libncurses.so.5.6
lrwxrwxrwx  1 root root      18 2009-03-23 17:44 libncursesw.so.5 -> libncursesw.so.5.6
lrwxrwxrwx  1 root root      20 2009-03-23 17:44 libntfs-3g.so.28 -> libntfs-3g.so.28.0.0
lrwxrwxrwx  1 root root      22 2009-03-23 17:44 libparted-1.8.so.9 -> libparted-1.8.so.9.0.0
lrwxrwxrwx  1 root root      17 2009-03-23 17:44 libpcre.so.3 -> libpcre.so.3.12.1
lrwxrwxrwx  1 root root      16 2009-03-23 17:44 libpopt.so.0 -> libpopt.so.0.0.0
lrwxrwxrwx  1 root root      18 2009-03-23 17:44 libreadline.so.5 -> libreadline.so.5.2
-rwxr-xr-x  1 root root  112055 2009-01-29 02:23 libpthread-2.8.90.so
-rwxr-xr-x  1 root root  113252 2009-01-29 02:23 ld-2.8.90.so
-rw-r--r--  1 root root    9804 2009-01-29 02:23 libanl-2.8.90.so
-rw-r--r--  1 root root    5440 2009-01-29 02:23 libBrokenLocale-2.8.90.so
-rwxr-xr-x  1 root root 1315024 2009-01-29 02:23 libc-2.8.90.so
-rw-r--r--  1 root root  185820 2009-01-29 02:23 libcidn-2.8.90.so
-rw-r--r--  1 root root   38300 2009-01-29 02:23 libcrypt-2.8.90.so
-rw-r--r--  1 root root    9676 2009-01-29 02:23 libdl-2.8.90.so
-rw-r--r--  1 root root  149332 2009-01-29 02:23 libm-2.8.90.so
-rw-r--r--  1 root root   13692 2009-01-29 02:23 libmemusage.so
-rw-r--r--  1 root root   79612 2009-01-29 02:23 libnsl-2.8.90.so
-rw-r--r--  1 root root   30436 2009-01-29 02:23 libnss_compat-2.8.90.so
-rw-r--r--  1 root root   17884 2009-01-29 02:23 libnss_dns-2.8.90.so
-rw-r--r--  1 root root   38412 2009-01-29 02:23 libnss_files-2.8.90.so
-rw-r--r--  1 root root   17896 2009-01-29 02:23 libnss_hesiod-2.8.90.so
-rw-r--r--  1 root root   34352 2009-01-29 02:23 libnss_nis-2.8.90.so
-rw-r--r--  1 root root   46604 2009-01-29 02:23 libnss_nisplus-2.8.90.so
-rw-r--r--  1 root root    5440 2009-01-29 02:23 libpcprofile.so
-rw-r--r--  1 root root   63312 2009-01-29 02:23 libresolv-2.8.90.so
-rw-r--r--  1 root root   30624 2009-01-29 02:23 librt-2.8.90.so
-rw-r--r--  1 root root   13692 2009-01-29 02:23 libSegFault.so
-rw-r--r--  1 root root   30384 2009-01-29 02:23 libthread_db-1.0.so
-rw-r--r--  1 root root    9688 2009-01-29 02:23 libutil-2.8.90.so
-rw-r--r--  1 root root   54740 2009-01-23 12:14 libgcc_s.so.1
-rw-r--r--  1 root root   21884 2009-01-05 06:53 libnss_winbind.so.2
-rw-r--r--  1 root root 1841636 2009-01-05 06:53 libnss_wins.so.2
-rw-r--r--  1 root root    9576 2008-11-11 06:48 libpamc.so.0.81.0
-rw-r--r--  1 root root    9588 2008-11-11 06:48 libpam_misc.so.0.81.3
-rw-r--r--  1 root root   42476 2008-11-11 06:48 libpam.so.0.81.12
-rw-r--r--  1 root root   30024 2008-11-03 10:12 libvolume_id.so.0.85.0
-rw-r--r--  1 root root   59080 2008-10-29 21:11 libproc-3.2.7.so
drwxr-xr-x  3 root root    4096 2008-10-29 16:02 brltty
drwxr-xr-x  3 root root    4096 2008-10-29 16:02 init
drwxr-xr-x  2 root root    4096 2008-10-29 16:00 linux-sound-base
drwxr-xr-x  2 root root    4096 2008-10-29 16:00 iptables
drwxr-xr-x  2 root root    4096 2008-10-29 15:58 dbus-1.0
drwxr-xr-x  3 root root    4096 2008-10-29 15:54 tls
drwxr-xr-x  2 root root    4096 2008-10-29 15:53 lsb
-rw-r--r--  1 root root   91792 2008-10-20 14:14 libdevmapper.so.1.02.1
-rw-r--r--  1 root root  447108 2008-10-16 15:10 libusplash.so.0
-rw-r--r--  1 root root   22624 2008-10-13 06:10 libe2p.so.2.3
-rw-r--r--  1 root root   40612 2008-10-13 06:09 libblkid.so.1.0
-rw-r--r--  1 root root    9576 2008-10-13 06:09 libcom_err.so.2.1
-rw-r--r--  1 root root  166236 2008-10-13 06:09 libext2fs.so.2.4
-rw-r--r--  1 root root   21976 2008-10-13 06:09 libss.so.2.0
-rw-r--r--  1 root root   13872 2008-10-13 06:09 libuuid.so.1.2
-rw-r--r--  1 root root  222816 2008-10-07 07:23 libdbus-1.so.3.4.0
drwxr-xr-x  2 root root    4096 2008-09-29 03:32 i486-linux-gnu
-rw-r--r--  1 root root  108992 2008-09-25 09:06 libfuse.so.2.7.3
-rw-r--r--  1 root root    9540 2008-09-25 09:06 libulockmgr.so.1.0.1
-rw-r--r--  1 root root  396300 2008-09-12 07:31 libparted-1.8.so.9.0.0
-rw-r--r--  1 root root   38648 2008-08-06 02:09 libbrlapi.so.0.5.2
-rwxr-xr-x  1 root root   64704 2008-08-03 19:19 klibc-zUXi_KjK5ZQAIyc8jlwme9T6a4U.so
-rw-r--r--  1 root root  165124 2008-08-01 15:48 libpcre.so.3.12.1
-rw-r--r--  1 root root  697288 2008-07-21 15:43 libslang.so.2.1.3
-rw-r--r--  1 root root   99972 2008-07-15 08:59 libselinux.so.1
-rw-r--r--  1 root root  214716 2008-07-15 06:03 libsepol.so.1
-rw-r--r--  1 root root  186516 2008-07-10 02:12 libntfs-3g.so.28.0.0
-rw-r--r--  1 root root  423876 2008-07-02 01:43 libgcrypt.so.11.4.4
-rw-r--r--  1 root root    9440 2008-06-30 12:13 libx86.so.1
-rw-r--r--  1 root root   34640 2008-06-26 01:24 libpopt.so.0.0.0
-rw-r--r--  1 root root   70020 2008-06-23 01:02 libbz2.so.1.0.4
-rw-r--r--  1 root root   13792 2008-06-12 06:39 libcap.so.2.10
-rw-r--r--  1 root root   31072 2008-06-12 05:50 libusb-0.1.so.4.4.4
-rw-r--r--  1 root root   30960 2008-05-03 00:14 libwrap.so.0.7.6
-rw-r--r--  1 root root   34464 2008-05-02 23:44 libatm.so.1.0.0
-rw-r--r--  1 root root    9436 2008-05-02 18:19 libkeyutils-1.2.so
-rw-r--r--  1 root root   17760 2008-05-02 17:27 libattr.so.1.1.0
-rw-r--r--  1 root root   26156 2008-05-02 17:01 libacl.so.1.1.0
-rw-r--r--  1 root root    7552 2008-04-18 14:28 libnss_mdns4_minimal.so.2
-rw-r--r--  1 root root    8148 2008-04-18 14:28 libnss_mdns4.so.2
-rw-r--r--  1 root root    7616 2008-04-18 14:28 libnss_mdns6_minimal.so.2
-rw-r--r--  1 root root    8196 2008-04-18 14:28 libnss_mdns6.so.2
-rw-r--r--  1 root root    8172 2008-04-18 14:28 libnss_mdns_minimal.so.2
-rw-r--r--  1 root root    8580 2008-04-18 14:28 libnss_mdns.so.2
-rw-r--r--  1 root root   37784 2008-04-01 10:03 libsysfs.so.2.0.1
-rw-r--r--  1 root root  190584 2008-02-23 15:38 libncurses.so.5.6
-rw-r--r--  1 root root  236568 2008-02-23 15:38 libncursesw.so.5.6
-rw-r--r--  1 root root   69952 2008-02-23 15:38 libtic.so.5.6
-rw-r--r--  1 root root   69952 2008-02-23 15:38 libticw.so.5.6
drwxr-xr-x 15 root root    4096 2008-02-23 15:38 terminfo
-rw-r--r--  1 root root   27444 2007-12-21 06:36 libiw.so.29
-rw-r--r--  1 root root   11468 2007-11-15 16:56 libgpg-error.so.0.3.0
-rw-r--r--  1 root root   27188 2007-10-02 07:35 libhistory.so.5.2
-rw-r--r--  1 root root  196560 2007-10-02 07:35 libreadline.so.5.2
-rw-r--r--  1 root root   10316 2007-07-31 12:20 libcap.so.1.10
stevenj@ubuntu:/lib$ 


So i cannot get past that.
aaaaaand im spent!

so i sit, broken hearted (for now)

and the ESSID i am trying to get to is "steven"

i just want to add that fwiw i feel stupid posting that much of a rambling rant worth of terminal stuff.
obviously i am in over my head and frustrated. ready to go back to windows at this point if i cant get this working.
worst case i can reclaim 6 gigs of HDD space but i am smarter than this.

---

### Post by vegas-steven on 2009-03-26
> **sanemanmad said:**
> Hi, Please take a look at my post before you start installing software on your GNU OS. :)

[http://ubuntuforums.org/showpost.php?p=6948594&postcount=1426](http://ubuntuforums.org/showpost.php?p=6948594&postcount=1426)

thanks, i did what was in the post and it seems to have worked as far as installing all the needed software from the server, however there is no wireless icon for me to connect to i am afraid.

> 
do the above however to "activate" the drivers you need to connect by wire in order for the drivers to be downloaded to the computer, then you can activate the card and use it.

hrm. intriguing as i am posting this on the os. i am wired.
all this ive been doing has been while using the os and being online (via network cable)

here is where i am NOW when i run that same screen:
[IMG]http://i198.photobucket.com/albums/aa167/stevenj-89145/Screenshot.png[/IMG]

---

### Post by vegas-steven on 2009-03-27
one last thing:

ive tried the method listed here:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

i managed to get the firmware file AND fwcutter.
installed fwcutter and ran it. i managed to get the files it extracted into \~lib\firmware

the network manager is already installed from something else i was trying, and so that SHOULD be working

i can also see that under system-preferences-sessions

i then reboot and cannot get anything started however i can still see the power for the hardware active.

so i get a gold star for effort!

and it shows wlan0 under the network tools tab:
[IMG]http://i198.photobucket.com/albums/aa167/stevenj-89145/WIFISCREEN.png[/IMG]

---

