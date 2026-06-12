---
title: "Ubuntu USB trace - will it capture USB from VirtualBox guest?"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by anewguy on 2009-10-23
I know there at least used to be support built in for doing a USB trace, but I don't recall right now how to do it (I think it was putting a Y or N in a file - I'd have to look up my old post).  What I'd like to know is, since native devices are mapped to a virtual machine, will I be able to run a USB trace in Ubuntu and have it capture the USB traffic from my old Windows 98SE virtual machine running in VirtualBox?  I would assume yes, but don't know if there is some trick to this or not.

Why would I want to actually DO this?  Well, my old HP Scanjet 4200C USb scanner works fine in Ubuntu thanks to all of the HP support, except that I can't turn the lamp off after a scan - it stays on until I remove the power plug from the scanner.  There is (maybe I should say *was* as I haven't gone back to check yet) a HP utility to toggle the lamp in Windows, so what I'm hoping to do is trap the USB exchanges so I can write a program in C using libusb routines to toggle the lamp in Linux/Ubuntu.  Kind of the hard way around to something, but since there doesn't seem to be any such utility in Linux in general for my scanner, and since I've used the libusb development stuff before, I figure as long as I can trap the exchanges then I can build a program to do it.

Thanks in advance!

Dave :)

---

