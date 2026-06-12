---
title: "Wubi downloads i386 .iso for an AMD64"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Keiran230 on 2010-04-18
If I attempt to download Ubuntu, wubi grabs the 64-bit .iso. However, on the same computer that wubi determined was 64-bit, if I attempt to install Kubuntu, it grabs kubuntu-9.10-desktop-i386-.iso.torrent.

I have an AMD Athlon 64 3500+ in a 939-socket. I am currently running Windows XP Professional with SP3 (32-bit OS).

Exact steps to get there:
[LIST=1]
[*]download wubi installer from wubi-installer.org
[*]run wubi.exe
[*]Select drive, select size, select Kubuntu desktop environment, English, and place in a username and password
[*]select install
[/LIST]
Therefore, I don't think this was the result of PEBKAC.

Things I've tried:
[LIST]
[*]starting wubi with the "--64bit" command-line argument (it has a "--32bit" option, so I tried it on the off-chance it'll recognize this one too.)
[*]manually downloading kubuntu-9.10-desktop-amd64.iso and placing it in the same folder, then running wubi.
[/LIST]

I've noticed that for some reason, it lists my installation drives twice, but I don't know if this is related to the issue.

Possibly related to the bug: if I attempt to download Kubuntu Netbook Remix, I get this error: "Cannot download the metalink and therefore the ISO."

I split the log into two parts because of the filesize limit.

---

### Post by WinterRain on 2010-04-18
To use wubi, which I don't recommend, simply insert any ubuntu live cd while running windows, and it will prompt you to install. Easy.

---

### Post by Keiran230 on 2010-04-18
I just tried that. It read the disk, then abandoned it, then started downloading kubuntu-9.10-desktop-i386.iso.torrent again.

---

### Post by Keiran230 on 2010-04-18
The Launchpad website had a fix. The Wubi installer has a bug in it.

[https://bugs.launchpad.net/wubi/+bug/465936?comments=all](https://bugs.launchpad.net/wubi/+bug/465936?comments=all)

**SOLUTION!**
Use this executable instead: [http://people.canonical.com/~evand/wubi/karmic/wubi-r168.exe](http://people.canonical.com/~evand/wubi/karmic/wubi-r168.exe)

---

