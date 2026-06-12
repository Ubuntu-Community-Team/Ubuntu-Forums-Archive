---
title: "karmic live cd graphics fail"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by pranayama on 2009-10-31
I was hoping to reinstall this time instead of update, because I’d like to switch up to 64-bit from 32, and reformat my Linux partition to ext4 from ext3.

I am having a strange problem with the Karmic live CDs. The md5sums check out, I think they’ve been burnt properly. After selecting the option to “Try Ubuntu without any change to my computer” I get a pulsating white Ubuntu logo, and then everything changes to brilliant and dark vertical magenta stripes. The logon bongo drums play fine.

I can switch to a virtual terminal with Ctrl/alt F2, but even in the virtual terminal there seems to be some graphics display problem, because text isn’t flowing normally. The cursor stays flashing at the top left corner but what I type appears at the bottom of the screen. I can’t even navigate man pages properly.

The situation is exactly the same with both the ubuntu-9.10-desktop-amd64.iso and ubuntu-9.10-desktop-i386.iso

I haven’t had these problems with Hardy, Intrepid or Jaunty.

I have tried running ubuntu-9.10-desktop-i386.iso within VirtualBox on 450MB of RAM and it works perfectly!

My system includes:

HP Pavilion t3729.uk Desktop PC
Intel Pentium D
1001 MiB
Nvidia GeForce 7500 LE PCI-E 16x

Totally lost with this one.

---

### Post by Liolikas on 2009-10-31
Maybe try 32bit 9.10?
Sounds like kernel bug, you can report it you will get more info with dmesg command.

---

### Post by cariboo on 2009-10-31
Try starting in safe graphics mode, that's what I had to do to install Xubuntu Karmic. At the menu screen press F4 and highlight **safe graphics mode** and press enter, then select either try before installing or install. 

I personally prefer the try before installing method, as after selecting installation from the desktop I open Firefox and have something to do during the installation.

---

### Post by pranayama on 2009-11-02
Thanks, safe graphics mode works.

I did try the 32-bit version I think, isn’t that ubuntu-9.10-desktop-i386.iso ?

I’d like to report a bug but not smart enough to understand the output of dmesg. I wouldn’t know how to print or save it in a virtual terminal in a live session, and as I said the text is getting garbled inside the virtual terminal.

---

