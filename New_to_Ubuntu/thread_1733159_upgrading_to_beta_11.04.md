---
title: "upgrading to beta 11.04"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by stalkier on 2011-04-18
I have been using Ubuntu off and on since version 5.04. I am wanting to checkout the beta for 11.04. right now I have 10.10 installed. The OS is installed on a Compaq V2000 laptop. It is a capable machine for the OS. I need to know how to force a distro upgrade.Thank you all for your support. The forum is an awesome tool.

---

### Post by beew on 2011-04-18
11.04 is not stable and apparently is still having problems with Nvidia graphic cards. Why would you want to upgrade from something that is working to a pre-release? If you want ton test  you can get a live usb or install into an external drive.

---

### Post by sammiev on 2011-04-18
Upgrade from 10.10 to 11.04 didn't go well with my system. A fresh install went great. Be in no hurry to upgrade until after it's been released and tested for a bit. GL :)

---

### Post by stalkier on 2011-04-18
> **beew said:**
> 11.04 is not stable yet. Why would you want to upgrade from something that is working to a pre-release? If you want ton test  you can get a live usb or install into an external drive.

honestly I am just curious about the release.

---

### Post by beew on 2011-04-18
> **stalkier said:**
> honestly I am just curious about the release.

Then don't do it. :)

---

### Post by kaldor on 2011-04-18
Why not just create a live USB drive? If you have a spare 4+ GB drive you can use, I recommend it; it's how I report bugs and test out new stuff on my hardware with prereleases.

It sounds difficult, but it's quite easy. Ubuntu has a preinstalled Tool that makes it quite simple. 

_Step 1_
Wipe your USB drive. Use Disk Utility (System > Administration) to Unmount then Format your USB drive (straightforward UI)

_Step 2_
Open Startup Disk Creator (also in Administration) and select the Natty Daily .iso file that you downloaded ([click here]("http://cdimage.ubuntu.com/daily-live/current/")). Select the USB drive, click "Erase" then choose the bottom option in the devices list. Then all should be fine.

[img]http://www.ubuntu.com/sites/default/files/active/maverick/usb_ubuntu_04_medium.jpg[/img]

You can then Reboot and use the USB drive as if it were a Live CD. The best thing about it, is that it saves your session unlike a CD does so that you can basically use it as an external Ubuntu install.

---

### Post by Mark Phelps on 2011-04-19
> **stalkier said:**
> honestly I am just curious about the release.

Understand -- but are you aware that, if you encounter problems after the upgrade (and you WILL, given that it's only a Beta release), there is no way to go back to the working version you have now?

That's right -- there is no System Restore capability built into Ubuntu.

So basically, unless you do some kind of backup from which you can then restore your current setup, upgrading is a one-way trip.

That's one of the main reasons folks are telling you to NOT do it.

---

### Post by andrew.46 on 2011-04-20
Have a look at this:

[http://www.ubuntu.com/testing/natty/beta#Known%20issues](http://www.ubuntu.com/testing/natty/beta#Known%20issues)

A couple of show stoppers there?

---

