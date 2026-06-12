---
title: "ibex, winndows bootloader, i don't want windows, gparted, or what?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by adamogardner on 2008-12-29
I got an hp mini 2133 w/ vista.  I tried to install from flashdrive, and did but it didn't go as well as planned.  vista is still on my machine and GRUB  did not steal the show and install as i've seen it done in the past.  Is there a way ?

---

### Post by malathion on 2008-12-29
> **adamogardner said:**
> I got an hp mini 2133 w/ vista.  I tried to install from flashdrive, and did but it didn't go as well as planned.  vista is still on my machine and GRUB  did not steal the show and install as i've seen it done in the past.  Is there a way ?

I'm going to need more details about what you are trying to accomplish. Do you want to wipe out Vista and have only ubuntu on the system? If so, the "guided" option is not what you want, since that may default to dual-boot configuration. Instead, to get rid of Vista:

1. If you have any sensitive data on the laptop back it up since it will all be gone

2. Boot off the livecd or flash drive

3. Open up gparted
```
$ gksudo gparted
```

4. Delete every partition on the disk and click apply changes

5. Run the Installer as normal

That should get you a fresh Ubuntu install with nothing else on the disk.

---

### Post by oldos2er on 2008-12-30
> **adamogardner said:**
> I got an hp mini 2133 w/ vista.  I tried to install from flashdrive, and did but it didn't go as well as planned.  vista is still on my machine and GRUB  did not steal the show and install as i've seen it done in the past.  Is there a way ?

 Use the 'Guided - Use entire disk' option.

---

### Post by adamogardner on 2009-01-03
> **oldos2er said:**
> Use the 'Guided - Use entire disk' option.

well that's what I mean.  There was no 'guided anything' no options to choose.  I had to start it initially in safe graphics mode after several failed attepts.  I did this off of a usb stick if that means anything.

---

### Post by -kg- on 2009-01-03
I noticed from [a review]("http://www.notebookreview.com/default.asp?newsID=4352") that your netbook comes in various configurations:

> ...(from a) 1.0GHz VIA processor, 512MB of RAM and a 4GB PATA Flash module with Linux, to (a) 1.6GHz VIA processor, 2GB of RAM and a 120GB 5400 rpm hard drive running Windows Vista Business.

From the "4GB PATA Flash module with Linux" statement, I assume this to mean that particular model doesn't have a hard drive but runs totally on a Flash module.  It might also help if we knew the configuration of your computer.

With all the specs I've seen, I can't understand why it would be necessary to use "Safe Graphics Mode" for the install.  512 MB of RAM should be more than enough, even using some of it as VID RAM.

I'm still trying to learn Linux just as you are, so I'm interested in threads like this.

---

