---
title: "Computer restarts after disk check"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Blutkoete on 2011-02-28
Good morning, good day or good evening (depending on your location)!

Every time Kubuntu 10.10 performs a disk check on start up, it reboots afterwards. The next start-up shows the Grub menu (which normally doesn't show up as I'm not dual-booting) hinting that there was some kind of problem during start-up.

Two (or three) questions:

1. Is there a way to trigger the start-up disk check manually for testing?

2. Which log might be helpful?

(3. Is that a known problem with a known solution?)

Thank you very much,

Blutkoete

P.S.: The systems runs normally without problems after the reboot.

---

### Post by sikander3786 on 2011-02-28
You can try forcing a disk check on reboot by following this command.

```
sudo touch /forcefsck
```

It would check your partitions when you reboot.

Or boot from a Live CD/USB and run a check by following this command while your partitions are un-mounted.

```
sudo fsck -f /dev/sdXY
```

Where sdXY is your intended partition.

If there are any errors, fixing them should allow you to boot without any problems later.

---

### Post by Blutkoete on 2011-02-28
Thank you, I'm creating a LiveUSB stick right now to look into that.

---

### Post by Blutkoete on 2011-02-28
Great! Everything is fine now. I checked the disk (found some wrong-sized i_nodes, whatever that means, I'm googling for that at the moment), repaired it and then forced the standard check and it booted fine.

For other users coming here which might not be using the terminal daily:

**NOTE:** We'll use *SUDO* here, providing us with super user (root) privileges. Everything you do with *SUDO* can break your system, be cautious and know what you're doing. Check for typos before issuing a command.

1. Boot from a LiveCD / LiveUSB stick.** (this step is important, don't just boot from your hard disk)**

2. Open the terminal - in GNOME (Ubuntu): Press ALT-F2, type in *gnome-terminal* and hit the <Enter> key. In KDE (Kubuntu): Press ALT-F2, type in *konsole* and hit the <Enter> key.

3. Everything wrapped in the <code> tags from now on means you type it in the terminal window followed by pressing the <Enter> key. Find out the name of your partitions:

The *-l* options for *fdisk* commands* fdisk* to list all your partitions. Try* man fdisk* for more information (that calls the manual page which you can leave by pressing *q*).

```
sudo fdisk -l
```This will show you a list with all your devices. Your local hard disk is probably named *sda1*. (correct me if this is plainly wrong).

4. Run the second command stated by sikander3786. The *-f* option forces* fsck* to perform the test even if everything seems to be ok (check *man fsck* to read more).

```
sudo fsck -f /dev/sdXY
```Replace *XY* by the partition you want to check, e.g. *a1 *if it is sda1.

5. That'll perform the check. If it finds errors, it'll ask you whether it should correct them or not. The repair might break things, so if you're unsure, post the error in this forum and ask about it. Or even better: Use Google to look for it first.

6. In my case, everything was fine now.

---

