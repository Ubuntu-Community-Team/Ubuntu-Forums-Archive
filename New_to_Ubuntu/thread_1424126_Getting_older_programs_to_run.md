---
title: "Getting older programs to run"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by RTrev on 2010-03-07
I have a little executable that dates from around 2005 or so, called pvconv -- it converts between .wav files and .qcp (Qualcomm PureVoice format) files.

In both 32- and 64-bit Karmic, it complained that it couldn't find libstdc++.so.5 -- I guess a newer version of the libs was used in Karmic.  Prior to Karmic, it had run just fine.  So I grabbed the file libstdc++.so.5.0.7 from an earlier version (might have been Jaunty), copied it to Karmic's /usr/lib directory, and then created a link to it named libstdc++.so.5 -- and it worked.  I was amazed. <g>

Now, however, I have a similar problem in moving to 64-bit Lucid.  At first pvconv wouldn't run at all.  I tried installing the 32-bit libs package libc6-i386, and now it at least complains about something specific:

```

bob@ub64:~/pv$ pvconv
pvconv: error while loading shared libraries: libgcc_s.so.1: cannot open shared object file: No such file or directory

```

I searched for this libgcc_s.so.1 file, and found it in the /lib directory.  I don't know whether my old pvconv program is choking on it because it's newer, or if it simply is telling the truth that it can't find the file for some reason.  The protections look correct (world readable.)

Anybody got any suggestions?  This program is rather important to me, so I'd be grateful for any tips.

TIA,
Bob

---

### Post by egalvan on 2010-03-07
Two sites that may be of help...

[http://www.bitpim.org/help/error-nopvconv.htm](http://www.bitpim.org/help/error-nopvconv.htm)

[http://www.qctconnect.com/downloads/purevoice/pvsdk_readme.txt](http://www.qctconnect.com/downloads/purevoice/pvsdk_readme.txt)

---

### Post by RTrev on 2010-03-07
Yeah, I downloaded the SDK earlier, looked at it, and gulped.  I'll give it a try.  Thanks.  Will be the first time compiling anything under Linux... <g>

Was sure hoping there'd be some easy fix.  Ah well.

---

### Post by RTrev on 2010-03-07
Ahah.  Installing ia32-libs did the trick!  I tried this out of desperation, before rolling up my sleeves and trying to learn c++. <g>

---

