---
title: "AWLH6075 wireless PCI adapter doesn't work."
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Thocrun on 2010-07-09
I have tried ndis wrapper using a different driver and tried installing the ralink driver but failed at about step 6 on the guide I just want to be able to use the adapter to all it's ability (wireless N), I plan on making a hotspot out of it using coovachilli and the other wired adapter already installed. please help me get this working.

This is the ralink driver guide I tried to follow [http://ubuntuforums.org/showthread.php?t=296281](http://ubuntuforums.org/showthread.php?t=296281)
This is the ndis wifi guide I attempted to follow also [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by bkratz on 2010-07-09
> **Thocrun said:**
> I have tried ndis wrapper using a different driver and tried installing the ralink driver but failed at about step 6 on the guide I just want to be able to use the adapter to all it's ability (wireless N), I plan on making a hotspot out of it using coovachilli and the other wired adapter already installed. please help me get this working.

This is the ralink driver guide I tried to follow [http://ubuntuforums.org/showthread.php?t=296281](http://ubuntuforums.org/showthread.php?t=296281)
This is the ndis wifi guide I attempted to follow also [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Post 8 gives you the driver that the OP says worked.

[http://swiss.ubuntuforums.org/showthread.php?p=9443556](http://swiss.ubuntuforums.org/showthread.php?p=9443556)

---

### Post by anewguy on 2010-07-09
Also, so far I don't think Windows 7 drivers work - only Windows XP - when using ndiswrapper (use ndisgtk as the gui'd front-end to ndiswrapper and make your life *much* easier).

I prefer to get a native or restricted driver working whenever possible.  Sometimes it isn't possible, at which time loading ndiswrapper and ndisgtk, then using the Windows XP drivers usually works as the alternative.

Dave ;)

---

### Post by Thocrun on 2010-07-09
> **anewguy said:**
> Also, so far I don't think Windows 7 drivers work - only Windows XP - when using ndiswrapper (use ndisgtk as the gui'd front-end to ndiswrapper and make your life *much* easier).

I prefer to get a native or restricted driver working whenever possible.  Sometimes it isn't possible, at which time loading ndiswrapper and ndisgtk, then using the Windows XP drivers usually works as the alternative.

Dave ;)
Thanks for the quick response I guess I am just confused on what exact driver to use since the windows drivers are .exe? and I am looking for one already extracted .inf?

---

### Post by anewguy on 2010-07-10
PM me with a link to download your driver .exe file, and I'll extract the files for you and post back step-by-step how to install it using ndiswrapper with ndisgtk as the gui'd front end.

Dave

---

### Post by casperlingus on 2010-07-21
I'm pretty sure that card uses an RaLink chipset, *which has native linux drivers available from the ralink website*:

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

I just installed an older ralink card with the driver from this site and the installation was flawless.  I followed this guide, *just remember replace the **rt2860** with the correct driver for this card*:

[http://ubuntuforums.org/showthread.php?p=9268017](http://ubuntuforums.org/showthread.php?p=9268017)

It's quite a few steps, but I succeeded on the very first try without any errors or confusion.  The general process is easier to understand than the specific steps:

```

1)  Download correct driver file. 
2)  Unpack 
3)  Modify a couple lines of source code to enable WPA
4)  Install linux headers and build-essential
5)  Compile the driver
6)  Replace the existing system driver with the one you just compiled
7)  Set the driver to load on boot
8)  Reboot
```

After I rebooted, network manager knew what to do and I was connected immediately.  NOTE: in my case, the file I downloaded was named incorrectly, I had to rename from .bz2 to .tgz for the archive manager to be able to unpack it.

Hope that helps!
-Casper

---

