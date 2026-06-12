---
title: "should i reinstall or upgrade or neither"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by lunaz on 2007-02-13
i tried installing belkin driver from its cd by following the guide at
[http://ubuntuforums.org/showthread.php?t=210035&highlight=newbie+needs+help+with+wireless+belkin+f](http://ubuntuforums.org/showthread.php?t=210035&highlight=newbie+needs+help+with+wireless+belkin+f)

it's not working since my network settings box freezes all the time & when it does come up wireless isnt in there. (step7)

should i start in on this next one or just upgrade to edgy & see if that makes a difference? or did i do something to screw up the 1st one?

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29%20?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29%20?highlight=%28WifiDocs%2FDevice%29)

i'm hooked up to dsl modem right now til i figure all this out...or buy a router & 50 feet of ethernet cable..or move furniture around

---

### Post by NeoFax on 2007-02-13
Try removing the driver using the ndiswrapper utility.  Then download a newer driver from the belkin website and load it.

---

### Post by lunaz on 2007-02-14
thanks, i found one at
[http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=0&fid=2599&fn=F5D7050v4000_V1.0.0.9_FCC.exe](http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=0&fid=2599&fn=F5D7050v4000_V1.0.0.9_FCC.exe)
but how do u use .exe files here?

---

### Post by gradedcheese on 2007-02-14
you don't :(  Go to some Windows box, open the .exe installer to get it to extract the driver (.inf or .INF) and then copy that.  Install the whole driver on that Windows box if you have to.  The .exe is just a self-extracting archive+installer in this case.

---

### Post by lunaz on 2007-02-14
hm, well, i have no idea which of these to try using. :(

```

gail@gail-oldpos:/media/usbdisk/ndis$ ls -a
.                     caroot.pem                     preflib.dll
..                    CrashRpt.dll                   Region.INI
BelkinHWStatus.dll    dot1x_dll.dll                  ssleay32.dll
BelkinwcuiDLL.dll     F5D7050v4000_V1.0.0.9_FCC.exe  UNICOWS.DLL
Belkinwcui.exe        install.dll                    UploadDLL.dll
BelkinwcuiJAPDLL.dll  KCopy.exe                      W32N55.dll
BelkinwcuiKORDLL.dll  lang                           W32N55.INI
BelkinwcuiSCHDLL.dll  libeay32.dll                   ZDWlan.dll
BelkinwcuiTCHDLL.dll  msvcr71.dll                    zlib.dll
BlkwcapiZU.DLL        openssl.exe
brdcm2k.dll           order.txt
gail@gail-oldpos:/media/usbdisk/ndis$ cd lang
gail@gail-oldpos:/media/usbdisk/ndis/lang$ ls -a
.   dut.ini  fre.ini  ita.ini  kor.ini  spa.ini
..  en.ini   ger.ini  jap.ini  sch.ini  tch.ini
gail@gail-oldpos:/media/usbdisk/ndis/lang$

```

i got the file F5D7050v4000_V1.0.0.9_FCC.exe from the belkin site, took it to the windows comp & installed it to desktop/ndis & brought all of it back here.

---

### Post by gradedcheese on 2007-02-15
this is a total guess, but I would try "W32N55.INI"

---

### Post by lunaz on 2007-02-16
here's what i got so far. i didn't think i was successful uninstalling the other one i tried but...

```

gail@gail-oldpos:/etc/ndiswrapper$ ndiswrapper -l
No drivers installed
gail@gail-oldpos:/media/usbdisk/ndis$ sudo ndiswrapper -i W32N55.INI
Password:
Installing w32n55.ini
gail@gail-oldpos:/media/usbdisk/ndis$ sudo modprobe ndiswrapper
gail@gail-oldpos:/media/usbdisk/ndis$ sudo ndiswrapper -m
modprobe config already contains alias directive

gail@gail-oldpos:/media/usbdisk/ndis$

```

got to go shoppin now but will try out rest of the guide when i get home & post back. step 7 again.

edit for dumb question: when they say to blacklist drivers how do u know for sure which ones? and where do u see a list of drivers installed?

---

### Post by gradedcheese on 2007-02-16
here's one way: you can run "lsmod" to see what kernel modules are loaded.  Want to know which ones get loaded when you insert the network card?  Remove the network card and wait a few seconds.  Now do this:

```

lsmod > modules_without

```

This saves lsmod's output to a text file.  Now put the card in and wait 30 seconds or so and:

```

lsmod > modules_with

```

This saves the lsmod output to another file (this time with the card installed).  Now we'll compare them:

```

diff modules_without modules_with

```

...and that should tell you what (if any) modules were loaded when you put the card in.  Now you know what to add to the backlist, if you need to.

---

### Post by lunaz on 2007-02-17
well i started over on that guide. not real sure what i did, but here's all my output. it even includes me navigating. :P

```

gail@gail-oldpos:~$ cd /media/usbdisk
gail@gail-oldpos:/media/usbdisk$ ls
Documents  LaunchU3.exe  ndis  System
gail@gail-oldpos:/media/usbdisk$ cd ndis
gail@gail-oldpos:/media/usbdisk/ndis$ ls
BelkinHWStatus.dll    CrashRpt.dll                   preflib.dll
BelkinwcuiDLL.dll     dot1x_dll.dll                  Region.INI
Belkinwcui.exe        F5D7050v4000_V1.0.0.9_FCC.exe  ssleay32.dll
BelkinwcuiJAPDLL.dll  install.dll                    UNICOWS.DLL
BelkinwcuiKORDLL.dll  KCopy.exe                      UploadDLL.dll
BelkinwcuiSCHDLL.dll  lang                           W32N55.dll
BelkinwcuiTCHDLL.dll  libeay32.dll                   W32N55.INI
BlkwcapiZU.DLL        msvcr71.dll                    ZDWlan.dll
brdcm2k.dll           openssl.exe                    zlib.dll
caroot.pem            order.txt
gail@gail-oldpos:/media/usbdisk/ndis$ sudo ndiswrapper -i W32N55.INI
Password:
w32n55.ini is already installed. Use -e to remove it
gail@gail-oldpos:/media/usbdisk/ndis$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-28-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
gail@gail-oldpos:/media/usbdisk/ndis$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-28-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
gail@gail-oldpos:/media/usbdisk/ndis$ cd desktop
bash: cd: desktop: No such file or directory
gail@gail-oldpos:/media/usbdisk/ndis$ cd /
gail@gail-oldpos:/$ ls
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old
gail@gail-oldpos:/$ cd desktop
bash: cd: desktop: No such file or directory
gail@gail-oldpos:/$ cd usr
gail@gail-oldpos:/usr$ ls
bin  games  include  lib  local  sbin  share  src  X11R6
gail@gail-oldpos:/usr$ cd /home
gail@gail-oldpos:/home$ ls
gail
gail@gail-oldpos:/home$ cd gail
gail@gail-oldpos:~$ ls
Battle.mid           Desktop   Firefox_wallpaper.png  update1
contactlist2007.xls  Examples  ****
gail@gail-oldpos:~$ cd Desktop
gail@gail-oldpos:~/Desktop$ ls
F5D7050v4000_V1.0.0.9_FCC.exe
gail@gail-oldpos:~/Desktop$ lsmod > modules_without
gail@gail-oldpos:~/Desktop$ lsmod > modules_with
gail@gail-oldpos:~/Desktop$ diff modules_without modules_with
gail@gail-oldpos:~/Desktop$ ls
F5D7050v4000_V1.0.0.9_FCC.exe  modules_with  modules_without
gail@gail-oldpos:~/Desktop$ diff modules_without modules_with
gail@gail-oldpos:~/Desktop$

```

i did follow that last post having to do w module_with & _without, but the diff... command didn't do anything. should i post the contents of module_with & module_without?

also, every time i make it to stop 7 my network settings box freezes up alot.

---

### Post by gradedcheese on 2007-02-17
> 
i did follow that last post having to do w module_with & _without, but the diff... command didn't do anything. should i post the contents of module_with & module_without?


That means that no modules (drivers) were loaded when you inserted the card :(  The way diff works is that it compares two files and shows the difference -- if the files were identical, then there's nothing to output.

---

### Post by lunaz on 2007-02-17
hmm... i reinstalled ubuntu again lol. i'm convinced i messed something up somewhere. i'll fully update dapper then....i dunno. these guides seem to get me stuck somewhere. :( what info am i msssing? right now i'm still hooked up to my dsl modem & the wireless thing is on the winxp computer right now...working. :P

---

### Post by gradedcheese on 2007-02-17
you don't need to reinstall the OS.  Unlike in Windows, there's almost nothing that you can screw up in Linux to make a reinstall required, it's just a matter of figuring out what's wrong.

Anyhow, I am curious about what chipset your card has and if you really need to suffer through this ndiswrapper stuff.  Can you please run "lspci" in the terminal and post the output?  Specifically, any lines mentioning "Ethernet Controller".

---

### Post by lunaz on 2007-02-18
```

gail@gail-oldpos:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
0000:02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:02:0b.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:02:0c.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem
0000:02:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
0000:02:0d.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
gail@gail-oldpos:~$

```

i don't have the belkin adapter plugged in right now, it's on the windows computer. should i bring it in here & do lsusb?

---

### Post by gradedcheese on 2007-02-18
> 
should i bring it in here & do lsusb?


oh yes, sorry that's what I meant to ask you to do.

---

### Post by lunaz on 2007-02-18
it's plugged in, light is on but i'm still connected to dsl modem, its wireless option is on with wep right now but i can change that if needed. here's lsusb:

```

gail@gail-oldpos:~$ lsusb
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 050d:705c Belkin Components
Bus 002 Device 001: ID 0000:0000
gail@gail-oldpos:~$

```

---

### Post by gradedcheese on 2007-02-18
Ok, so the mystery device is plugged in, but it (I assume) doesn't show up when you run "iwconfig" (ie: anything with wireless extensions there?).  As I recall, you installed ndiswrapper to support this device, is ndiswrapper loaded? "lsmod | grep ndis" should return something.  If not, try "sudo modprobe ndiswrapper"

---

### Post by lunaz on 2007-02-18
```

gail@gail-oldpos:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

gail@gail-oldpos:~$ lsmod | grep ndis
gail@gail-oldpos:~$ sudo modprobe ndiswrapper
Password:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-28-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
gail@gail-oldpos:~$

```

before i did this, i installed ndiswrapper-utils from synaptic.

---

### Post by gradedcheese on 2007-02-18
hmm, do you actually have this file?  Run:

```

ls /lib/modules/2.6.15-28-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

```

does that say "no such file or directory"?

---

### Post by lunaz on 2007-02-18
nope, it repeats the path back to me.

---

### Post by lunaz on 2007-02-19
i heard network-manager-gnome is suppose to help configure this stuff so i installed it. it only shows wired stuff though. can'ts eem to find any guide how to use it.

i guess i'll try to use the version 3 drivers, then if that dont work upgrade to edgy. i heard both those might help.

edit: ok, tried somebodys version 3 driver link but it came out corrupted when i tried to extract it in windows so i went to belkin.com & now cant find any drivers just stuff about vista. i guess i'll try to upgrade to edgy now.

---

### Post by lunaz on 2007-02-19
i upgraded to edgy but wireless dont work out of the box there either. i tried to disable my ethernet but it dont save settings, network-manager-gnome dont show anything either. what now?

edit: i even tried to turn off wireless security in the router. no go. i'm doing things from the windows comp after the edgy upgrade got all done with.

edit2: i found this bit of info:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

Card: Belkin Wireless G USB Network Adapter
    * Chipset: Unsure
    * usbid: 050d:705c
    * Driver: On the CD at /files/Driver/blkwgu.inf
    * Other: run ndiswrapper -i blkwgu.inf on CD, copy blkwgu.sys to same directory as ndiswrapper puts the inf file. bring up device. Had problem not being able to use restricted mode and had to switch to open WEP. Works once i made the switch, pretty straightforward.

where does ndis keep the inf files? have i been doing this wrong hte whole time? should i have been copying the blkwgu.sys from cd to ...i dont know where?

---

### Post by lunaz on 2007-02-22
i got it working on edgy following this guide:

[http://ubuntuforums.org/showpost.php?p=1223311&postcount=2](http://ubuntuforums.org/showpost.php?p=1223311&postcount=2)

by using BLKWGU.sys and .inf. i was only using .inf last time so not sure if u just need .sys or both the .inf & .sys, but i hope it helps someone & ty all for the replies. :D

---

