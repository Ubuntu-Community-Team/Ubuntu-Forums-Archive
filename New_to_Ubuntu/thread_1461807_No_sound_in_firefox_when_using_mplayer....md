---
title: "No sound in firefox when using mplayer...?"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-04-24
When playing radio streams in mplayer I'm not getting any sound from say flash videos in firefox:(

has this got something to do with pulse audio?

how can solve this?

using Linux Mint KDE CE (kubuntu 9.10 'karmic koala')

---

### Post by lovinglinux on 2010-04-25
Try to change you sound settings to ALSA in "System >> Preferences >> Sound". That always did the trick for me when using Gnome.

---

### Post by kamitsukai on 2010-04-25
> **lovinglinux said:**
> Try to change you sound settings to ALSA in "System >> Preferences >> Sound". That always did the trick for me when using Gnome.

didn't help

---

### Post by kamitsukai on 2010-04-25
Okay I have some mild success with getting this working =]

Using the information I found in the RestrictedFormats/Flash section of the Ubuntu Documentation ([https://help.ubuntu.com/community/RestrictedFormats/Flash/#Troubleshooting](https://help.ubuntu.com/community/RestrictedFormats/Flash/#Troubleshooting)) I've installed the alsa-oss package and have edited the Firefox rc script to include:

```
FIREFOX_DSP="aoss"
```

and success! I can now watch flash videos with sound while listeing to online radio stations, however... I don't use Firefox as my main browser anymore I use Swiftfox so I followed the instructions to make the patch however I get this error when applying it...

```
carl@carl-laptop ~ $ sudo patch -p0 <swiftfox_oss_patch.diff
[sudo] password for carl:
patching file /usr/lib/swiftfox/run-mozilla.sh
patch unexpectedly ends in middle of line
Hunk #1 FAILED at 163.
1 out of 1 hunk FAILED -- saving rejects to file /usr/lib/swiftfox/run-mozilla.sh.rej

```

---

