---
title: "Playing a DVD crashes VLC"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by Famicommander on 2009-11-08
I tried to watch a DVD in VLC and it crashed. I also tried Totem and I get the same problem.

I ran it in terminal and this is what I came up with:
```

jason@ubuntu:~$ vlc
VLC media player 1.0.2 Goldeneye
[0x81c5538] main interface error: no interface module matched "globalhotkeys,none"
[0x81c5538] main interface error: no suitable interface module
[0x811c140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x811c140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: FINAL_FANTASY_VII
libdvdnav: DVD Serial Number: 4411F8FC___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jason/.dvdnav/FINAL_FANTASY_VII.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f20000. Regions: 1 3 4
*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0x81
*** Zero check failed in ifo_read.c:854
    for pgc->still_time = 0x30
*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0x06
*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0x01

*** libdvdread: CHECK_VALUE failed in ifo_read.c:856 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:858 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:842 ***
*** for pgc->nr_of_programs <= pgc->nr_of_cells ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:860 ***
*** for pgc->program_map_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:861 ***
*** for pgc->cell_playback_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:862 ***
*** for pgc->cell_position_offset != 0 ***

*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0x81

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_VOBU_ADMAP vtsi failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted
jason@ubuntu:~$ 

```

---

### Post by stoogiebuncho on 2009-11-09
Do you have Medibuntu installed?  

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Famicommander on 2009-11-09
Yes. It still crashes.

---

### Post by jmszr on 2009-11-09
Famicommander,

You didn't indicate which release of Ubuntu you are using, but if it is 9.10 then this might be of help:[http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html](http://www.ubuntugeek.com/fix-for-vlc-doesnt-play-video-after-ubuntu-9-10-karmic-upgrade.html)

---

### Post by Famicommander on 2009-11-09
I am using Ubuntu Karmic.

And none of the above work. And it isn't just VLC that crashes, but every media player. They crash immediately after I start to play a DVD.

Thanks for the reply, though.

---

### Post by naxtek on 2009-11-11
I have this exact issue too...

Just bought a new DVD drive as I thought it was broken, but it turns out it's Ubuntu...


Anyone any ideas?

---

### Post by PGScooter on 2009-11-11
Try looking for a similar bug here:
[https://launchpad.net/bugs/bugtrackers/vlc-trac-bugs](https://launchpad.net/bugs/bugtrackers/vlc-trac-bugs)
If you don't find one, post a new one so that the developers are aware.

You could also post on the VLC forums:
[http://forum.videolan.org/](http://forum.videolan.org/)

---

### Post by sandyd on 2009-11-11
> **Famicommander said:**
> I tried to watch a DVD in VLC and it crashed. I also tried Totem and I get the same problem.

I ran it in terminal and this is what I came up with:
```

jason@ubuntu:~$ vlc
VLC media player 1.0.2 Goldeneye
[0x81c5538] main interface error: no interface module matched "globalhotkeys,none"
[0x81c5538] main interface error: no suitable interface module
[0x811c140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x811c140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: FINAL_FANTASY_VII
libdvdnav: DVD Serial Number: 4411F8FC___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/jason/.dvdnav/FINAL_FANTASY_VII.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f20000. Regions: 1 3 4
*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0x81
*** Zero check failed in ifo_read.c:854
    for pgc->still_time = 0x30
*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0x06
*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0x01

*** libdvdread: CHECK_VALUE failed in ifo_read.c:856 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:858 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:842 ***
*** for pgc->nr_of_programs <= pgc->nr_of_cells ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:860 ***
*** for pgc->program_map_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:861 ***
*** for pgc->cell_playback_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:862 ***
*** for pgc->cell_position_offset != 0 ***

*** Zero check failed in ifo_read.c:855
    for pgc->pg_playback_mode = 0x81

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_VOBU_ADMAP vtsi failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted
jason@ubuntu:~$ 

```
looks like its missing the dvdcss libraries.
sure you installed libdvdcss2?

---

### Post by PRC09 on 2009-11-11
Is this any help....

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by arnoutvos on 2009-12-31
i had the exact same problem, and i fixed it

searching the forums, i tried a lot.
- i installed medibuntu,
- followed the vlc fix link
- re-installed most of the packages that are involved with dvd playback
- did a regionset
- the last thing i did was an libdvdcss2 update (strangly, it took a while before the update became available after i installed the medibuntu repo)

the problem is, it didn't work untill i rebooted my pc so now i don't really know what made the difference. i only know one thing:
_it only worked after a reboot_

so my advice is to reboot everytime you try something new and report afterwards

btw: i have an amd64 laptop with ubuntu 64, is this a 64bit problem?

---

### Post by Devour on 2010-01-16
I just installed libdvdread4 and did the install-css.sh script and it didn't work at first, but after a reboot it works now. I find this strange but there might be a kernel module that needs to be inserted or loaded and this would be done on startup or could be done manually in the terminal.

---

