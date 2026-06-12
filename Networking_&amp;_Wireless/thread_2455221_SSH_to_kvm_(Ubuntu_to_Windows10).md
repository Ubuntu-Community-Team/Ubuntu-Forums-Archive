---
title: "SSH to kvm (Ubuntu to Windows10)"
date: 2020-12-15
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2020-12-15
My scenario is to be able to have remote access from either a windows 10 machine or ubutnu machine to the other to do Remote Desktop.  I'm looking at using x2go (from ubuntu to windows 10) and so initially setting up a shh connection between both machines.  If we are going from ubuntu to windows does it matter what machine generates to two ssh keys (public and private) providing the private and public keys are on ubuntu and the same public key on the win machine?  Ubuntu stores the keys in ~/.ssh and windows in c:\ProgramData\ssh - is the physical generation of the keys independent of the machines they are used on?   I have tried the above on my ubuntu host and windows kvm and it does not want to play.  Before using key authentication I could ssh user@xxxxxxx both ways (ubuntu to win or win to ubuntu) just using normal password authentication and it all worked as prescribed.

---

### Post by TheFu on 2020-12-15
There isn't any x2go server for Windows, therefore you cannot do X --> Windows via x2go.
However, if you run Win10 in a VM, under SPICE/QXL, then you can use virt-viewer to connect to Windows, at least over the LAN and performance will be excellent.

From Windows ---> Linux, you have Spice, x2go, and a few other options.

Win10 ssh works just like Linux. A few months ago, I helped someone setup their ssh-keys on Win10 to connect into Linux.  The Win10 ssh directories are in the same relative location for each userid on Win10 at they are for Linux and use the same filenames  ~/.ssh/ .  BTW, you do know that Windows has always allowed using / for directory separators and it works fine in both the shell and inside programs.  Windows has ssh-keygen and it works the same.  However, there isn't any ssh-copy-id on Windows, so you get to do it the manual way.

ssh has some very specific file and directory permissions that are required.  Basically,  600 for everything except the .pub files which are 644.

---

