---
title: "DVD Play back problem."
date: 2009-05-05
forum: New to Ubuntu
---

### Post by jose187 on 2009-05-05
I've used Movie Player, then VLC... NOTHING.

When i play the DVD with Movie Player, the window freezes and nothing happens.

When i play it with VLC, it first said i didn't have the permission to play it, and then that it had to do something with the code.

I checked everything (codec wise) and it is all there.

I changed the DVD, and the same thing...

PLEASE HELP!!!

---

### Post by feelshift on 2009-05-05
System -> Help and Support -> Music, Video and Photos -> Movies, DVDs and videos -> Playing DVDs.
Have you read it?

---

### Post by jose187 on 2009-05-05
> **feelshift said:**
> System -> Help and Support -> Music, Video and Photos -> Movies, DVDs and videos -> Playing DVDs.
Have you read it?

Yes,

all packages are installed, including the one for encripted dvds,
On Movie Player I get a "you may not have permission" error message, and on VLC it just closes itself.

---

### Post by kpkeerthi on 2009-05-05
Open a terminal and enter **vlc** to launch from there. Post back the errors it prints out when it closes.

---

### Post by jose187 on 2009-05-05
This is what i get.

> libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: Step_Brothers
libdvdnav: DVD Serial Number: 394fbda3
libdvdnav: DVD Title (Alternative): Step_Brothers
libdvdnav: Unable to find map file '/home/jose/.dvdnav/Step_Brothers.map'
*** Zero check failed in ifo_read.c:520
    for vmgi_mat->zero_6 = 0x0000001100000000000000000000000000000000000000000000000000000000
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001c0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0002529e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x0002529e)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000252b2
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x000252b2)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00327656
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x00327656)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00332f1f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00332f4e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00332f52
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00332f78
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00332f7c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00337ad7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00337aeb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x00337b24
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00337b28
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003c8897
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003c889b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x003ce060
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003ce064
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x003cf10a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x003cf10e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003ebb41
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x003ebb45
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x003efafa
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x003efb4f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x003f09db
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003f1779
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003f5235
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_16_1.VOB at 0x003f5289
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_16_1.VOB (0x003f5289)!!
libdvdread: Elapsed time 0
libdvdread: Found 16 VTS's
libdvdread: Elapsed time 0
*** Zero check failed in ifo_read.c:1120
    for vts_ptt_srpt->zero_1 = 0xe1b7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1122 ***
*** for vts_ptt_srpt->nr_of_srpts < 100 ***

libdvdread: Can't allocate memory for file read!
libdvdread: Unable to read PTT search table.
libdvdnav: ifoRead_VTS_PTT_SRPT failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted


---

### Post by nimbus9 on 2009-05-16
I experienced the exact same problem today. This was using a legitimate DVD:

libdvdnav: DVD Title: WAKINGLIFE
libdvdnav: DVD Serial Number: 2C6E8CD5
libdvdnav: DVD Title (Alternative): WAKINGLIFE
libdvdnav: Unable to find map file '/home/nimbus/.dvdnav/WAKINGLIFE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted

---

### Post by emacbri on 2009-05-16
The libdvdcss in the repositories is outdated. Unfortunately, the new one in the medibuntu repository. Follow this link:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by doas777 on 2009-05-16
> **emacbri said:**
> The libdvdcss in the repositories is outdated. Unfortunately, the new one in the medibuntu repository. Follow this link:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

+1

I always install the ubuntu-restricted-extras package, then the medibuntu repos (with lib2dvdcss and w64 codecs) and mplayer as well (for the videos nothing else will play), and I havn't seen a file I couldn't play in years, excepting a few DRMed wmvs.

---

### Post by nimbus9 on 2009-05-16
I went through this entire tutorial:
[http://ubuntuforums.org/showthread.php?t=766683&highlight=totem+dvd](http://ubuntuforums.org/showthread.php?t=766683&highlight=totem+dvd)
Now I just get the error:
Could not open location; you might not have permission to open the file.

---

### Post by doas777 on 2009-05-16
> **nimbus9 said:**
> I went through this entire tutorial:
[http://ubuntuforums.org/showthread.php?t=766683&highlight=totem+dvd](http://ubuntuforums.org/showthread.php?t=766683&highlight=totem+dvd)
Now I just get the error:
Could not open location; you might not have permission to open the file.

ok, once you have the repos installed as shown in that tutorial, install the packages like:
```
sudo apt-get install libdvdcss2
```

---

### Post by nimbus9 on 2009-05-16
I installed libdvdcss2 and still have the same error.

---

### Post by Wangberg on 2009-05-26
> **nimbus9 said:**
> I installed libdvdcss2 and still have the same error.

i also have this same error message:

```

[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: DIE_HARD_1
libdvdnav: DVD Serial Number: 38D08B50APPLEDSP
libdvdnav: DVD Title (Alternative): DIE_HARD_1
libdvdnav: Unable to find map file '/home/wangberg/.dvdnav/DIE_HARD_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00df0000. Regions: 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001b8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000ac7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0036fe7b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0036feb4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00373d09
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00373d42
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted

```

any ideas on how to get this resolved?

---

### Post by Wangberg on 2009-05-26
very strange issue....

I installed a few of the codec devel files (libdvdcss-dev, libdvdnav-dev, libdvdread-dev) and libxine1, libxine1-all-plugins, MPlayer, Xine, in addition to VLC.  

I still had the same issues and couldn't get a DVD to play.  After about 5 hours i thought, it might be a DVD region problem since i'm using Region 6 DVD's, so i popped in a region free bootlegged DVD from the street and it worked fine.  Then i decided i would try a Region 6 DVD different from the first tested, and it also worked.  Then i tried the original one and it surprisingly worked.  

After these worked, I deleted xine player and mplayer because i prefer VLC (not a complete removal, just the players -- kept the codecs).  and VLC can now play DVDs.  

Try installing those devel packs for the codecs libdvdnav, libdvdcss, libdvdread and see what happens.  

hope this helps!

---

### Post by rainbowmagik on 2009-06-17
I had the same issue even after installing libdvdcss2 from the help pages, I then installed the repositories and codecs from here: 

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

It didn't work until after I rebooted.
And now dvds play perfectly

---

