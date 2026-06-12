---
title: "Yet another can't play DVD thread"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Dark_Emerald on 2009-09-16
Hello.  I currently run Kubuntu 9.04 on my computer, but I am having an issue playing DVDs.  I have libdvdread4 and libdvdnav4 installed and all, but when I attempt to play a DVD in vlc or mplayer, I'm getting this message:

```
libdvdnav: Using dvdnav version 4.1.3                                           
libdvdread: Encrypted DVD support unavailable.                                  
************************************************                                
**                                            **                                
**  No css library available. See             **                                
**  /usr/share/doc/libdvdread4/README.Debian  **                                
**  for more information.                     **                                
**                                            **                                
************************************************                                
libdvdnav: DVD Title: DeathNote_Volume1                                         
libdvdnav: DVD Serial Number: ca950849
libdvdnav: DVD Title (Alternative): DeathNote_Volume1
libdvdnav: Unable to find map file '/home/p1/.dvdnav/DeathNote_Volume1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_VOBU_ADMAP vtsi failed

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1704 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_VOBU_ADMAP vtsi failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:397: vm_new_copy: Assertion `0' failed.
Aborted
```

I'm not sure why it is saying this if I already have libdvdread4 installed.  Can anyone help?  I'm still pretty new to this (KDE and Kubuntu), so please forgive me.

---

### Post by Dark_Emerald on 2009-09-16
I'm assuming it's because I'm using libdvdread4 instead of 3, isn't it?

---

### Post by dearingj on 2009-09-16
You'll need to install libdvdcss2 if you're trying to play commercial DVDs. You can download it from this page: [http://packages.medibuntu.org/jaunty/libdvdcss2.html](http://packages.medibuntu.org/jaunty/libdvdcss2.html)

---

### Post by Dark_Emerald on 2009-09-16
Wow!!!  That did the trick!  Thank you very much!  Is all this info in the beginner's guide as well?  I apologize if I wasted your time!

---

### Post by nothingspecial on 2009-09-16
you mean [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by theozzlives on 2009-09-16
> **Dark_Emerald said:**
> Wow!!!  That did the trick!  Thank you very much!  Is all this info in the beginner's guide as well?  I apologize if I wasted your time!

It's not a waste of time, at least for me, I get a sense of satisfaction out of helping people. I'm sure most people here feel the same way.

---

### Post by Dark_Emerald on 2009-09-16
> **nothingspecial said:**
> you mean [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

Thanks for the link!

---

### Post by Dark_Emerald on 2009-09-16
> **theozzlives said:**
> It's not a waste of time, at least for me, I get a sense of satisfaction out of helping people. I'm sure most people here feel the same way.

Well, thanks once again!  This was the final piece of the puzzle to make my new computer fully operational!

---

