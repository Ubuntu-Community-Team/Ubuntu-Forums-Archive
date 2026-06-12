---
title: "Centrino Advanced-N 6205"
date: 2014-07-21
forum: Networking &amp; Wireless
---

### Post by sandyd on 2014-07-21
I currently have a Centrino Advanced-N 6205 Half-Mini PCI-E card in a laptop.

For some reason, the card appears to work for the first ~5min. After the ~5m, the wifi light turns off, and the wifi no longer works.
Running iwlist scan gives an IO Error.

This somehow only happens in Ubuntu/Linux, but not in Windows, so I do not believe it is a hardware error.

---

### Post by tgalati4 on 2014-07-21
Perhaps it is running too hot.  Put your finger on it while in Linux.  Do the same in Windows.  Take note of any differences.  Reseat the card and antenna connection, regardless.

It's possible that you have a different transmit power setting, or using (or not using) hardware encryption, which could change the chip's temperature.  Open a terminal and post:

```
lspci | grep Network
```

Then determine what module you are running:

```
lsmod
```

Make a list of all of the advanced settings that you are using in Windows and check them one-by-one with the settings used in linux.

---

### Post by sandyd on 2014-07-23
I believe ive found the problem.

I used to have a broadcom card in this computer with the wl drivers.
I used lsmod earlier, and for some reason, the wl drivers were loaded (why?).

I removed the wl drivers, and the wifi has not crashed in the past few hours.

We will see, but I believe this has been fixed.

---

