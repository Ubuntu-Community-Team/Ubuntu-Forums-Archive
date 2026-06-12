---
title: "Google Earth problems"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by cozski on 2010-09-07
Hello

When I start Google Earth a message pops up informing me that my screen resolution is not set above 1024x768 but when I go to my monitor settings the highest resolution available is 1024x600... then the splash screen starts for GE but never actually starts. Any help appreciated.

Thanks

---

### Post by Zanderist on 2010-09-07
When I had Google Earth on my Ubuntu it would crash.

Only after I deleted the bin file that it left on the desktop did it work.

I don't know if I had the same problem(or if it even applies to you) as you, but that might work.

---

### Post by tahitiwibble on 2010-09-07
I was having all kinds of problems with Google Earth ........ until I bought a better video card and it works perfectly ever since.

---

### Post by karlm on 2010-09-07
This is what I've read, followed and remain stumped with:

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

I followed the instructions to a 't' and got GE installed. However, it would only load the splash screen then die. So I checked the help page and read this:

[http://n01getsout.com/blog/2006/11/26/google-earth-for-linux-freezing-with-ati](http://n01getsout.com/blog/2006/11/26/google-earth-for-linux-freezing-with-ati)
> 
Ever since I upgraded to my desktop to Debian Linux I have not been able to run Google Earth. It would freeze on the splash screen and never open the main interface. I used Google Earth on Debian before, so I knew it was just a problem with my machine. As it turns out, it was the new ATI fglrx drivers that were preventing it from running properly.

 

Apparently, all versions of ATI’s proprietary Linux (fglrx) drivers version 2.28 and newer will not work for Google Earth (at least on some systems). So here is how to get Google Earth working again:

   1. Get a copy of libGL.so.1.2
   2. Put the file in the Google Earth directory (usually /usr/local/google-earth)
   3. Rename the file to libGL.so.1
   4. Start Google Earth and enjoy!



So, despite my not having a clue how to copy a file in Ubuntu, I managed it... except it popped up an error screen saying permission denied. So I thought, being the clever chap I am, I would instead use the command line to move it, or the terminal as it's known here.

I tried everything but couldn't get it moved, it just kept saying permission denied - until I figured to use the 'sudo' command in front. So eventually, I typed in:

>  sudo mv libGL.so.1 /opt/google-earth which seemed to copy it across without the permission denied screen/error. 

Then I decided while I was in the terminal I would also run GE from it using the command "googleearth" (remember, I've now completed the file issue with ATI gfx cards stuff).

I was promptly met with the following error:

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
** (process:9789): DEBUG: NP_Initialize
** (process:9789): DEBUG: NP_Initialize succeeded
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/karl/.googleearth/crashlogs/crashlog-4c869fdf.txt

Please include this file if you submit a bug report to Google.
Which means absolutely nothing to me.

I've looked everywhere for the above *.txt file, but cannot locate it (using GUI or grep).

Any help always appreciated :)

---

### Post by wojox on 2010-09-07
Which set of instructions did you follow? The medibuntu repo's or did you download the .bin from Google?

---

### Post by karlm on 2010-09-07
> **wojox said:**
> Which set of instructions did you follow? The medibuntu repo's or did you download the .bin from Google?

I followed the instructions for installing via the terminal command line and it worked ok, aside it crashed. 

Looking at the FAQ section, I saw it could be my ATI card that was causing the crash - so I followed the instructions on how to work around for ATI card users (such as myself)....

However, I can't figure out how to read the file ./googleearth/etc./etc/

I'm assuming the ./ means it is a hidden directory or suchlike?

---

### Post by wojox on 2010-09-07
Try this [How to Install Google Earth in Ubuntu 10.04]("http://ubuntuforums.org/showpost.php?p=9339846&postcount=5")

---

### Post by karlm on 2010-09-07
> **wojox said:**
> Try this [How to Install Google Earth in Ubuntu 10.04]("http://ubuntuforums.org/showpost.php?p=9339846&postcount=5")

I'ts already installed :) It just stops working at the splash screen.

Could you perhaps advise on how I find the *.txt file in the ./googleearth directory though?

---

### Post by alphacrucis2 on 2010-09-07
> **karlm said:**
> I'ts already installed :) It just stops working at the splash screen.

Could you perhaps advise on how I find the *.txt file in the ./googleearth directory though?

Yes but your method of installing hasn't worked so far. I would try the using the medibuntu package and see if that works better. It worked out of the box for me and I'm using the proprietary ATI driver.

---

### Post by wojox on 2010-09-07
> **karlm said:**
> I'ts already installed :) It just stops working at the splash screen.

Could you perhaps advise on how I find the *.txt file in the ./googleearth directory though?

Open your Home Folder

Press Ctrl+H (to show hidden files and folders).

Navigate to .googleearth

---

### Post by karlm on 2010-09-08
> **wojox said:**
> Press Ctrl+H (to show hidden files and folders).

Super stuff... I love to learn stuff! 

Righty, so here is the contents of my last crash report.. .It means nothing to me, but perhaps someone here might have a clue what it's telling me.

[HTML]Major Version 5
Minor Version 2
Build Number 0001
Build Date Sep  1 2010
Build Time 11:25:42
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 32
OS Patch Version 0
Crash Signal 11
Crash Time 1283889474
Up Time 3.29778

Stacktrace from glibc:
./libgoogleearth_free.so(+0xd090b)[0x20090b]
[0xe5a400]
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so(NP_GetMIMEDescription+0x2da)[0x1a986ea]
./libQtWebKit.so.4(+0x747d18)[0x6066d18]
./libQtWebKit.so.4(+0x6062ff)[0x5f252ff]
./libQtWebKit.so.4(+0x604516)[0x5f23516]
./libQtWebKit.so.4(+0x60476a)[0x5f2376a]
./libQtWebKit.so.4(+0x712beb)[0x6031beb]
./libQtWebKit.so.4(+0x5b1595)[0x5ed0595]
./libQtWebKit.so.4(+0x5a185c)[0x5ec085c]
./libQtWebKit.so.4(+0x5b1981)[0x5ed0981]
./libQtWebKit.so.4(+0x5b199a)[0x5ed099a]
./libQtWebKit.so.4(+0xaa2c4b)[0x63c1c4b]
./libQtWebKit.so.4(+0x16ad57)[0x5a89d57]
./libQtWebKit.so.4(+0x1749d5)[0x5a939d5]
./libQtWebKit.so.4(+0x183282)[0x5aa2282]
./libQtWebKit.so.4(+0x1bc22d)[0x5adb22d]
./libQtWebKit.so.4(+0x29ac5d)[0x5bb9c5d]
./libQtWebKit.so.4(+0x2a9410)[0x5bc8410]
./libQtWebKit.so.4(+0x2a9f72)[0x5bc8f72]
./libQtWebKit.so.4(+0x2b7fea)[0x5bd6fea]
./libQtWebKit.so.4(+0x4be45a)[0x5ddd45a]
./libQtWebKit.so.4(+0x4bf243)[0x5dde243]
./libQtWebKit.so.4(+0x4c0449)[0x5ddf449]
./libQtWebKit.so.4(+0x4c2a75)[0x5de1a75]
./libQtWebKit.so.4(+0x4c36b8)[0x5de26b8]
./libQtWebKit.so.4(+0x4c6773)[0x5de5773]
./libQtWebKit.so.4(+0x501706)[0x5e20706]
./libQtWebKit.so.4(+0x5017fb)[0x5e207fb]
./libQtWebKit.so.4(+0x539f0b)[0x5e58f0b]
./libQtWebKit.so.4(+0x54c290)[0x5e6b290]
./libQtWebKit.so.4(+0x547cc3)[0x5e66cc3]
./libQtWebKit.so.4(+0x6fd155)[0x601c155]
./libQtWebKit.so.4(+0x6fd83e)[0x601c83e]
./libQtCore.so.4(_ZN11QMetaObject8metacallEP7QObjectNS_4CallEiPPv+0x3f)[0x3ea5a7]
./libQtCore.so.4(_ZN14QMetaCallEvent13placeMetaCallEP7QObject+0x24)[0x3f25ec]
./libQtCore.so.4(_ZN7QObject5eventEP6QEvent+0x185)[0x3f303d]
./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xa0)[0xf99e20]
./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x22e)[0xfa3962]
./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x70)[0x3e4d50]
./libQtCore.so.4(_ZN23QCoreApplicationPrivate16sendPostedEventsEP7QObjectiP11QThreadData+0x22d)[0x3e5989]
./libQtCore.so.4(_ZN20QEventDispatcherUNIX13processEventsE6QFlagsIN10QEventLoop17ProcessEventsFlagEE+0x37)[0x40a94b]
./libQtGui.so.4(+0x1d3ca4)[0x102eca4]
./libQtCore.so.4(_ZN10QEventLoop13processEventsE6QFlagsINS_17ProcessEventsFlagEE+0x47)[0x3e3fbf]
./libQtCore.so.4(_ZN10QEventLoop4execE6QFlagsINS_17ProcessEventsFlagEE+0xff)[0x3e4223]
./libQtCore.so.4(_ZN16QCoreApplication4execEv+0x9d)[0x3e5c05]
./libQtGui.so.4(_ZN12QApplication4execEv+0x25)[0xf997a1]
./libgoogleearth_free.so(_ZN5earth6client11Application3runEv+0x4bc)[0x20bb0c]
./libgoogleearth_free.so(earthmain+0x27d)[0x1ffd3d]
./googleearth-bin(_init+0x12e)[0x80486d2]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x9a5bd6]
./googleearth-bin(_init+0x9d)[0x8048641][/HTML]

---

### Post by cozski on 2010-09-19
Well I've unistalled, re-installed, uninstalled and re-installed and it never gets beyond the splash screen... did work, don't anymore, cant be arsed trying to resolve it anymore... a bit like trying to get Skype to work :confused: fecking nightmare

---

