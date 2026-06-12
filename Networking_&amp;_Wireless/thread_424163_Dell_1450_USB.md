---
title: "Dell 1450 USB"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by arfink on 2007-04-26
Here is how I got my Dell 1450 USB wireless device working: I had to download a file from Dell called R112743.exe. This file was a self-extracting EXE, so I extracted it with WinZip in Windoze, and then saw another self-extracting EXE, which I also extracted the contents of. This yielded a installer program named dotnetinstaller.exe, which made a directory called "drivers" which contained the .INF and .SYS files needed for ndiswrapper. I installed the drivers with no difficulty in Ubuntu 7.04 Fiesty using the graphical utility. Hope this helps some people out there using this device!

---

