---
title: "Ubuntu won't install =/"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by Valrayne on 2010-07-13
Usually I have no problems with installing this distro but for some reason it just isn't working on this laptop (asus g73).

Attempt 1: I tried the windows installer and instaltion went fine except when it came to actually boot into it and it spewed out some random error message and died in DOS before the UI could even load. 

Attempt 2: Then I tried my usual method, configuring the partitions myself and installing it from DOS straight to disk. Again installation seemd to complete succesfully only when I rebooted to load ubuntu - there was no entry in the MBR and thus no option to select and boot. Only my previous win7 installtion was available to select.

So in summary, attempt 1 would properly setup the system so that it was aware of the ubuntu install but died in DOS and attempt 2 would install but not place an entry for ubuntu to select and boot into it in the first place.

The only other possible complication is that for the first time i'm attempting to install ubuntu to a SSD instead of a traditional platter based HD.

Any ideas?

---

### Post by Valrayne on 2010-07-13
Got a little further after trying attempt 1's method again. This time ubuntu loaded its post-intsall procedures after reboot from first installation. However it then had to reboot for the 2nd time and dumped back to the same error message in DOS:

init: plymouth main process (503) killed by kill signal
init: unreadahead main process (502) killed by kill signal
exec: 5: mountall: Input/output error
init: mountall main process (523) terminated with status 2
init: Failed to spawn console-setup main process: unable to execute: Input/output error
init: plymouth-stop pre-start process (527) terminated with status 2
Filesystem check or mount failed
A maintenance shell will now be started
CONTROL-D will terminate this shell and continue booting after re-trying filesystems. Any further errors will be ignored
/proc/self/fd/8: 20: /sbin/sulogin: Input/output error
init:mountall-shell main process (528) terminated with status 2
[    12567921] kernal panic - not syncing: Attempted to kill init!
start: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired or the network connection was broken.

EDIT: the smiley face is meant to be the # 8 but this board keeps inserting that stupid graphic

---

### Post by Valrayne on 2010-07-13
ugh, turns out it was due to the order in which my drives booted up. Windows seems to be able to work around this automatically however, might be worth looking into putting that functionality into grub, devs.

Problem solved

EDIT: quick side question: Does anyone know of a linux driver for operating the luminosity on keyboards? Y'know, as most better equipped laptops have them and it's kinda lame that atm such drivers haven't been put in the kernel. Although it could be impossible due to hardware configurations. Alas I have more hope that the blackhats will put it into the kernel than the manufacturer of my hardware providing legitimate linux drivers. That's right Asus/Dell/Canon - i'm looking at you.

---

