---
title: "additional drivers fails to launch"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by roger_reject on 2010-12-19
Hi All.

I am new to Ubuntu and I just installed 10.10.  It was working well until I installed the latest ION driver for nvidia (260.19.06).  I *think* it may have broken my system.  Since then things have been very unstable (everything crashes, system does not shut down well, programs fail to launch) and I'd just like to roll back to nouveau until I can sort out what is going on.  Unfortunately, going to System->Administration->Additional Drivers fails to launch anything.  Diving into the terminal and running "jockey-gtk" yields an exception:

dbus.exceptions.DBusException: org.freedesktop.Dbus.Error.NoReply: Message did not recieve a reply (timeout by message bus)

Any idea how to purge nvidia and get nouveau back up?

---

### Post by sandyd on 2010-12-19
> **roger_reject said:**
> Hi All.

I am new to Ubuntu and I just installed 10.10.  It was working well until I installed the latest ION driver for nvidia (260.19.06).  I *think* it may have broken my system.  Since then things have been very unstable (everything crashes, system does not shut down well, programs fail to launch) and I'd just like to roll back to nouveau until I can sort out what is going on.  Unfortunately, going to System->Administration->Additional Drivers fails to launch anything.  Diving into the terminal and running "jockey-gtk" yields an exception:

dbus.exceptions.DBusException: org.freedesktop.Dbus.Error.NoReply: Message did not recieve a reply (timeout by message bus)

Any idea how to purge nvidia and get nouveau back up?
how did you install it?

---

### Post by roger_reject on 2010-12-19
I installed through the additional drivers utility.  After install and reboot the additional drivers utility stopped working.

---

### Post by sandyd on 2010-12-19
> **roger_reject said:**
> I installed through the additional drivers utility.  After install and reboot the additional drivers utility stopped working.
```

sudo apt-get --purge remove nvidia-*
```

---

### Post by roger_reject on 2010-12-19
I tried to do what you mentioned but apt-get gave me a segmentation faulty tree error.  

I followed the advice in this thread:
[http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563)

and deleted the corrput bin files.  Then I ran apt-get update, then purged nvidia as you suggested.  Then rebooted.

On reboot, ubuntu doesn't load.  It stays on the purple load screen with ubuntu and the five dots.

---

### Post by PhantmKllr on 2010-12-19
> **roger_reject said:**
> I tried to do what you mentioned but apt-get gave me a segmentation faulty tree error.  

I followed the advice in this thread:
[http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563)

and deleted the corrput bin files.  Then I ran apt-get update, then purged nvidia as you suggested.  Then rebooted.

On reboot, ubuntu doesn't load.  It stays on the purple load screen with ubuntu and the five dots.
Look's like you'll have to re-install.

---

### Post by sandyd on 2010-12-19
> **roger_reject said:**
> I tried to do what you mentioned but apt-get gave me a segmentation faulty tree error.  

I followed the advice in this thread:
[http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563)

and deleted the corrput bin files.  Then I ran apt-get update, then purged nvidia as you suggested.  Then rebooted.

On reboot, ubuntu doesn't load.  It stays on the purple load screen with ubuntu and the five dots.

oops. I forgot this step

```

sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```just run it in recovery mode.

---

### Post by roger_reject on 2010-12-19
okay...how do i access recovery mode.  tried booting while holding down shift, and while holding down esc.  neither works.  thanks!

---

### Post by sandyd on 2010-12-19
> **roger_reject said:**
> I tried to do what you mentioned but apt-get gave me a segmentation faulty tree error.  

I followed the advice in this thread:
[http://ubuntuforums.org/showthread.php?t=19563](http://ubuntuforums.org/showthread.php?t=19563)

and deleted the corrput bin files.  Then I ran apt-get update, then purged nvidia as you suggested.  Then rebooted.

On reboot, ubuntu doesn't load.  It stays on the purple load screen with ubuntu and the five dots.

oops. I forgot this step

```

sudo rm /etc/X11/xorg.conf
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```
just run it in recovery mode.

---

### Post by roger_reject on 2010-12-19
Okay I think I am just going to save myself a headache and reinstall Ubuntu fresh.

---

### Post by PhantmKllr on 2010-12-19
> **roger_reject said:**
> Okay I think I am just going to save myself a headache and reinstall Ubuntu fresh.
That's the way to go. ;)

---

