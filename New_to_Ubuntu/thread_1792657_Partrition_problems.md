---
title: "Partrition problems"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by jiggajoe506 on 2011-06-28
Hey guys I have ran into a problem booting Ubuntu. I tried firing up winidows and get a partition error message and it then said grub recovery. I then followed these steps to fix it so that windows would boot.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

&

[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

Windows seven boots up fine now but I had tried going into the windows boot-loader and Ubuntu is not an option. So I made a boot-able installer for Ubuntu but it just shows a black screen and stays there till I power off the laptop. Are there any suggestions on how to make this work. If not I have attached a picture with my partitions and would like to delete the Ubuntu partition if possible. Thanks in advance for all the help guys, I am sure you guys will be super helpful as  you always have been.

---

### Post by dFlyer on 2011-06-28
I don't see any linux partition. Are you running wubi?

---

### Post by jiggajoe506 on 2011-06-28
no i created a whole partition for it when doing the set up, if you see windows its only showing 152 gigs of hdd but My laptop has a 320 gig hdd....

---

### Post by oldfred on 2011-06-28
Windows does not 'see' Linux partitions, so it may be in the unallocated.

From Ubuntu liveCD run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by srs5694 on 2011-06-28
> **oldfred said:**
> Windows does not 'see' Linux partitions, so it may be in the unallocated.

Windows doesn't show Linux partitions as active drives, but they should *not* show up as "unallocated" in the Windows partitioning tool!

> From Ubuntu liveCD run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Running this script is certainly advisable.

My suspicion is that Windows deleted the Ubuntu partition. The Windows Vista and 7 installers are known to do this under certain circumstances, and it's entirely possible that the recovery disc did the same thing. If so, it will be necessary to recover the partition in one way or another, [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) being the most common tool for this task.

---

