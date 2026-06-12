---
title: "Streaming media in Mplayer"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by Leberyo on 2009-12-14
Hi, I installed the latest mplayer via source using these directions; [http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)
The only problem is that I'd like to play streaming wmvs' via mms.  Is there a way I can make this happen?

---

### Post by Tamlynmac on 2009-12-14
If your using it for wmv's, might I suggest you try SMPlayer. Works great with mpegs and wmv's.

smplayer is in the package manager and should load the appropriate codecs when installing. If it doesn't, it will ask you when you start a wmv.

Been using it for 3 years and have had zero problems with smplayer. Just works...

Good Luck - Hope this helps.

---

### Post by Leberyo on 2009-12-14
> **Tamlynmac said:**
> If your using it for wmv's, might I suggest you try SMPlayer. Works great with mpegs and wmv's.

smplayer is in the package manager and should load the appropriate codecs when installing. If it doesn't, it will ask you when you start a wmv.

Been using it for 3 years and have had zero problems with smplayer. Just works...

Good Luck - Hope this helps.


Installed SMPlayer already as an Mplayer frontend as per the instructions in building Mplayer.

---

### Post by Synoc on 2009-12-14
> **Tamlynmac said:**
> If your using it for wmv's, might I suggest you try SMPlayer. Works great with mpegs and wmv's.

smplayer is in the package manager and should load the appropriate codecs when installing. If it doesn't, it will ask you when you start a wmv.

Been using it for 3 years and have had zero problems with smplayer. Just works...

Good Luck - Hope this helps.
how does it work with DVDs? I have been having issues with Mplayer. I D/Ld the restricted package and got it PLAYING them, but they are choppy and not as sharp as they were under my laptop's Windows "dictatorship"

---

### Post by Tamlynmac on 2009-12-15
I've never used SMPlayer to watch DVD's. I use MPlayer for that purpose. 

I only use SMPlayer for Internet streaming of AVI's, WMV's, etc. One does need to make sure the selected files are assigned to SMPlayer in Firefox:
Firefox/edit/preferences/applications
Select "use other" under "action" and I believe the executable for SMPlayer can be found here:
file system/usr/bin/smplayer

This assures that the streaming files are linked directly to the opening of SMPlayer and not MPlayer or some other application.

Good Luck

---

