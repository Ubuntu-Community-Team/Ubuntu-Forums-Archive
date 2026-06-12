---
title: "VLC STILL not working (probably region issue)"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by runningjake on 2010-07-18
I've been trying forever to get VLC to play a DVD in another region and it just refuses.  

I've gone through this thread: [http://ohioloco.ubuntuforums.org/showthread.php?p=8586957](http://ohioloco.ubuntuforums.org/showthread.php?p=8586957) and tried everything and it STILL crashes.  AHHH!  ](*,)


I've instaled the libdvd stuff, install-css.sh, I've tried uninstalling everything and reinstalling it again and then rebooting the laptop like crazy.  And all the other commands listed in that thread.  I'm at a total loss here.  All other media players just crash the second I try and open the DVD.  

FWIW, I have a Dell XPS M1530 and am running Ubuntu 9.10.

Here's the error I get if I run it in the terminal:

> VLC media player 1.0.2 Goldeneye
[0x8cb5180] main demux warning: no access_demux module matching "file" could be loaded
[0x8cc69b8] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: (lists title etc. here)
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000203
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000690
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00000690)
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000190a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000190a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000690
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x00000690)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000190a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x0000190a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00000690
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x00000690)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x0000190a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x0000190a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00000690
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_0.VOB (0x00000690)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0000190a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x0000190a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00000690
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_0.VOB (0x00000690)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0000190a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x0000190a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00000690
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_0.VOB (0x00000690)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0000190a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_06_1.VOB (0x0000190a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x00000690
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_0.VOB (0x00000690)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0000190a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x0000190a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x00000690
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_0.VOB (0x00000690)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0000190a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x0000190a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x00000690
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_0.VOB (0x00000690)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0000190a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x0000190a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x00000690
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_0.VOB (0x00000690)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0000190a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_10_1.VOB (0x0000190a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00000690
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_0.VOB (0x00000690)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0000190a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_11_1.VOB (0x0000190a)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x0026ebbd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x0026ec70
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_12_1.VOB (0x0026ec70)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x0026f27d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x0026f330
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_13_1.VOB (0x0026f330)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x0026fa23
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x0026fb0f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_0.VOB at 0x0026fbe3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x0026fc96
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_15_1.VOB (0x0026fc96)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_0.VOB at 0x00273a1b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x00273ace
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_16_1.VOB (0x00273ace)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_0.VOB at 0x0027516e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_17_0.VOB (0x0027516e)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_17_1.VOB at 0x00275221
libdvdread: Elapsed time 0
libdvdread: Found 17 VTS's
libdvdread: Elapsed time 6

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_VOBU_ADMAP vtsi failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted


---

### Post by k3lt01 on 2010-07-18
What region are you in? I always thought region settings were a hardware issue not a software issue. You can get region free drives, that may be your only answer.

---

### Post by runningjake on 2010-07-18
The Drive is set to region 1 and I want to play a region 2 DVD.  I've always been able to do this with older computers of mine using VLC (although other programs wouldn't do it) but again, I'm far from an expert on these things.

---

### Post by runningjake on 2010-07-18
> **k3lt01 said:**
> What region are you in? I always thought region settings were a hardware issue not a software issue. You can get region free drives, that may be your only answer.


You know what, I think you're right. I just found this thread: [http://ubuntuforums.org/showthread.php?t=814564](http://ubuntuforums.org/showthread.php?t=814564)

and that's my exact DVD driver so I guess I'm doomed.  Really stinks because we have a ton of DVDs from both region 1 and 2.  I wish I knew before I got this laptop grr... I guess we'll pick up an external DVD drive tomorrow.

---

### Post by jtarin on 2010-07-18
No...follow the instructions on that link to install regionset.

---

### Post by runningjake on 2010-07-18
Sure, but then I'd have to just change it back and there's a limited number of changes.  We switch back and forth DVD regions all the time (we travel a lot) so it doesn't have any use to me if I can only change the region 5 times...

It's already working just fine for region 1.

---

### Post by jtarin on 2010-07-18
Check to see if you have the [libdvdread4]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") package(more than likely have)
There is also info for regionset on that page. if you don't want to change your DVD firmware with a flash, then you will either have to use the software solution or buy a new player, but then you will have the same problems. I flashed my player in Windows and it is set to play any region DVD. I can't guarantee there is a flash available for yours.

---

### Post by AlfyBoy on 2010-07-18
I'm sorry, for asking this, but:
Do you have installed libdvdcss2? it's form the [[COLOR="DarkRed"]medibuntu[/COLOR]]("http://medibuntu.org/") repository. ;)

---

### Post by k3lt01 on 2010-07-18
> **AlfyBoy said:**
> I'm sorry, for asking this, but:
Do you have installed libdvdcss2? it's form the [[COLOR="DarkRed"]medibuntu[/COLOR]]("http://medibuntu.org/") repository. ;)It stands to reason that if he can play Region 1 DVDs then YES he has installed it.

---

