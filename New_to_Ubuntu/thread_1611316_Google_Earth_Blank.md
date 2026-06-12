---
title: "Google Earth Blank"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by Jamezo97 on 2010-11-01
Hi,
   I am having trouble with google earth. I have looked on the internet, and can't seem to find anything helpful.
I have installed google earth as root, then once done, I told it to quit, because running it as root is not a good idea. Then I ran google earth from the terminal without root. It opens up, and what I get is this:
[IMG]http://i51.tinypic.com/2s1aucn.png[/IMG]
Most of the options in the toolbars are greyed out.

Eventually, after it has been running for a little while. It comes up with this error, and then crashes if I click on "Learn More"
[IMG]http://i56.tinypic.com/1okv45.png[/IMG]
When It crashes it gives me this in the terminal:
============================================================================
*****@*****-ubuntu:~$ googleearth
** (process:1693): DEBUG: NP_Initialize
** (process:1693): DEBUG: NP_Initialize succeeded
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/*****/.googleearth/crashlogs/crashlog-4ccf3d8e.txt

Please include this file if you submit a bug report to Google.
============================================================================

And it records down what happened when it crashed here:
============================================================================
> Major Version 5
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
Crash Time 1288650126
Up Time 241.598

Stacktrace from glibc:
./libgoogleearth_free.so(+0xd090b)[0x42690b]
[0xce2400]
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so(NP_GetMIMEDescription+0x2da)[0x449b6ea]
./libQtWebKit.so.4(+0x747d18)[0x1f12d18]
./libQtWebKit.so.4(+0x6062ff)[0x1dd12ff]
./libQtWebKit.so.4(+0x604516)[0x1dcf516]
./libQtWebKit.so.4(+0x60476a)[0x1dcf76a]
./libQtWebKit.so.4(+0x71e398)[0x1ee9398]
./libQtWebKit.so.4(+0x4ac7c6)[0x1c777c6]
./libQtWebKit.so.4(+0x4a0298)[0x1c6b298]
./libQtWebKit.so.4(+0x3baba9)[0x1b85ba9]
./libQtWebKit.so.4(+0x38a3ce)[0x1b553ce]
./libQtWebKit.so.4(+0x4ab128)[0x1c76128]
./libQtWebKit.so.4(+0x4bba48)[0x1c86a48]
./libQtWebKit.so.4(+0x4c2101)[0x1c8d101]
./libQtWebKit.so.4(+0x4c36b8)[0x1c8e6b8]
./libQtWebKit.so.4(+0x4c6773)[0x1c91773]
./libQtWebKit.so.4(+0x501706)[0x1ccc706]
./libQtWebKit.so.4(+0x5017fb)[0x1ccc7fb]
./libQtWebKit.so.4(+0x539f0b)[0x1d04f0b]
./libQtWebKit.so.4(+0x54c290)[0x1d17290]
./libQtWebKit.so.4(+0x547cc3)[0x1d12cc3]
./libQtWebKit.so.4(+0x6fd155)[0x1ec8155]
./libQtWebKit.so.4(+0x6fd83e)[0x1ec883e]
./libQtCore.so.4(_ZN11QMetaObject8metacallEP7QObjectNS_4CallEiPPv+0x3f)[0x5bb5a7]
./libQtCore.so.4(_ZN14QMetaCallEvent13placeMetaCallEP7QObject+0x24)[0x5c35ec]
./libQtCore.so.4(_ZN7QObject5eventEP6QEvent+0x185)[0x5c403d]
./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xa0)[0x1082e20]
./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x22e)[0x108c962]
./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x70)[0x5b5d50]
./libQtCore.so.4(_ZN23QCoreApplicationPrivate16sendPostedEventsEP7QObjectiP11QThreadData+0x22d)[0x5b6989]
./libQtCore.so.4(_ZN20QEventDispatcherUNIX13processEventsE6QFlagsIN10QEventLoop17ProcessEventsFlagEE+0x37)[0x5db94b]
./libQtGui.so.4(+0x1d3ca4)[0x1117ca4]
./libQtCore.so.4(_ZN10QEventLoop13processEventsE6QFlagsINS_17ProcessEventsFlagEE+0x47)[0x5b4fbf]
./libQtCore.so.4(_ZN10QEventLoop4execE6QFlagsINS_17ProcessEventsFlagEE+0xff)[0x5b5223]
./libQtCore.so.4(_ZN16QCoreApplication4execEv+0x9d)[0x5b6c05]
./libQtGui.so.4(_ZN12QApplication4execEv+0x25)[0x10827a1]
./libgoogleearth_free.so(_ZN5earth6client11Application3runEv+0x4bc)[0x431b0c]
./libgoogleearth_free.so(earthmain+0x27d)[0x425d3d]
./googleearth-bin(_init+0x12e)[0x80486d2]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x126bd6]
./googleearth-bin(_init+0x9d)[0x8048641]
============================================================================

I am running Ubuntu 10.04. I have a working graphics card. Google Earth used to run fine on Windows XP, before I got Ubuntu.
So any help is VERY appreciated, I really want to know how to fix this. 
Thanks
James - (New to all this)
P.S.(Please write in an easy way to understand, not programming talk, because I can't understand all of that... yet...)

---

### Post by wojox on 2010-11-01
Try running it as root again and see if it works.

```
gksudo googleearth
```

---

### Post by Jamezo97 on 2010-11-01
Nup, still doesn't work. Just get the blank space...

---

### Post by jcolyn on 2010-11-01
Did you install Googleearth from Medibuntu or the .bin file from Googleearth??

---

### Post by Jamezo97 on 2010-11-01
I installed it from Google's .bin file.

---

### Post by jcolyn on 2010-11-02
> **Jamezo97 said:**
> I installed it from Google's .bin file.

Easiest way is to uninstall what you have then go to this page for instructions on enabling Medibuntu. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you don't want to do that go here [http://packages.medibuntu.org/lucid/googleearth.html](http://packages.medibuntu.org/lucid/googleearth.html) and scroll down and click the i386 or amd64 .deb file and save to a folder.

Click the .deb file and it will install a working version.

The .bin file from googleearth is not fully compatible with Ubuntu..

---

### Post by I'mGeorge on 2010-11-02
> **Jamezo97 said:**
> Hi,
   I am having trouble with google earth. I have looked on the internet, and can't seem to find anything helpful.
I have installed google earth as root, then once done, I told it to quit, because running it as root is not a good idea. Then I ran google earth from the terminal without root. It opens up, and what I get is this:

 
The solution might be actually very simple. First go to your googleerath folder and if there you have an uninstall file in your terminal as root do sh uninstall if you don't find an uninstall file just delete the googleearth folder. After that install googleearth without root privilegies 'cause some software aren't ment to be installed and executed as root I believe Googleearth it's one of them, and see what happens.

---

### Post by TopEnder on 2010-11-03
Jamezo97, until you get googleearth up and operational you could use [http://vpike.com](http://vpike.com) to view an address, just tyoe in the address like you address a letter.

---

### Post by oldos2er on 2010-11-03
> **jcolyn said:**
> The .bin file from googleearth is not fully compatible with Ubuntu..

The *bin file is perfectly compatible with Ubuntu in my experience.

To the OP: See if the suggestions in this thread help you: [http://www.google.com/support/forum/p/earth/thread?tid=522e9e6586ef2cc2&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=522e9e6586ef2cc2&hl=en)

---

### Post by jcolyn on 2010-11-03
> **oldos2er said:**
> The *bin file is perfectly compatible with Ubuntu in my experience.[]("http://www.google.com/support/forum/p/earth/thread?tid=522e9e6586ef2cc2&hl=en")

It may work fine for you and others but in my experience and seeing posts here and other Linux forums it is buggy and seldom works right.

I have tried to install it on 8 different machines over the last several months and everyone crashed.

Medibuntu has in my opinion the best option available and will install with just a couple of clicks..

---

### Post by wojox on 2010-11-04
> **jcolyn said:**
> 
Medibuntu has in my opinion the best option available and will install with just a couple of clicks..

+1, it is a lot more simple.

---

### Post by oldos2er on 2010-11-04
> **jcolyn said:**
> It may work fine for you and others but in my experience and seeing posts here and other Linux forums it is buggy and seldom works right.


Beta software certainly has the potential to be buggy; that doesn't mean a *bin file itself is incompatible with Ubuntu. And of course you're only going to see problems posted on the forums, that's the nature of the beast.

---

### Post by oldos2er on 2010-11-04
> **wojox said:**
> +1, it is a lot more simple.

I find running a *bin to be more simple. To each her own.

---

