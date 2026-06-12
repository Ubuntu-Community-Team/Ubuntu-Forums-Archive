---
title: "[SOLVED] Virtualbox USB help"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by djbushido on 2008-12-18
I am trying to connect a usb hard drive to virtual box in windows. The problem is that windows auto mounts it and then won't give control to virtualbox. Is there a way around this?

EDIT: since the hard drive is left over from a previous install (ext3) windows won't recognize it with a drive letter, so i can't unmount it from explorer.

Also, sorry about posting about windows, i am trying to do this to install Linux and avoid a lot of hassle later. Thank you.

---

### Post by Hospadar on 2008-12-19
Hi,
This page:
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
gives a howto on how to set up your USB.  It doesn't mention though that after you do the setup, you need to plug in the device, go to the settings for you (powered down) virtual machine, and "add filter" and select the USB device you want to use.

That said, for a drive, I think it would be easier to just use it as a shared folder.  In this case it doesn't even matter what filesystem is on it so long as your linux installation can read it.

If you don't know how to do that, the guide I linked has instructions

---

### Post by HotShotDJ on 2008-12-19
> **djbushido said:**
> I am trying to connect a usb hard drive to virtual box in windows. The problem is that windows auto mounts it and then won't give control to virtualbox. Is there a way around this?I've never used Virtualbox on a Windows Host, however, I suspect the solution is similar to running it on a Linux host.

Plug in the usb drive. Open virtualbox, highlight the Virtual Machine that you will be using.  Click on settings and find and click on the USB section. You should see a large white box under the heading "USB Device Filters."   Right click within the box and click on "Add Filter from Device" -- in the popup menu, choose your USB drive.  It should now appear in the Device Filters box with a check mark.  Click "OK"

Now, remove the USB drive from the USB port.  Start up your virtual machine.  After it boots up, you should be able to plug in the USB drive and bypass the host OS.

Please let me know if this worked.  I don't have a windows system to test these instructions on.

---

### Post by djbushido on 2008-12-19
Turns out i had to make a device filter and _then_ plug it in. Got it working, thanks!

---

