---
title: "how to undo chmod commands?"
date: 2010-02-15
forum: New to Ubuntu
---

### Post by ownx0rz on 2010-02-15
Hello, everyone, I am running Ubuntu Netbook Edition 9.1. In the terminal, I accidentally changed permissions recursively to I think /, as when I try to become su remotely, I receive "setgid: Operation not permitted". You see, I was attempting to add this script to an MMO macro that I use [it would not save the gedit file in the location I desired], but I believe to have mistakenly chmod 667 -R / or chmod 667 home instead of /home/user/home, where the SVN for the autoers is located...I was not paying attention very much. At any rate, I cannot access Synaptic, but can initialize Software Center, not confident if it will work, because I know not what the password for super user is. Sooo, yeah, /etc/passwd is readable, but I do not see an /etc/group? Someone please help or refer me to a resolved thread, as I could not find one as specific as this, only explanations of chmod and whatnot.

Thanks.

---

### Post by audiomick on 2010-02-15
If you have just done this, the cursor up arrow will scroll back through the last commands that you typed in the terminal. It wont help you fix it, but you might be able at least to see exactly what you did.
edit: this also works if you have already closed the terminal. Open one again and try it.

---

### Post by ownx0rz on 2010-02-15
I have already restarted the computer since then? Sudo does not even work, as I am returned with "sudo: must be setuid root"

---

### Post by mikewhatever on 2010-02-15
Since you don't know exactly what you did, and since there is no undo for chmod, I guess it's time to reinstall, or restore from backup.

---

### Post by ownx0rz on 2010-02-15
I am pretty sure I did chmod 667 -R home, as I was actually trying to recursively set all the files in /home/user/home to be able to be accessed by whomever, for my macro. That or I performed chmod 667 -R /, but I do not think I would be that stupid. I was ignorantly paying attention to my XBOX.

---

### Post by audiomick on 2010-02-15
I think mikewhatever might be right: cut your losses and re-install. If you need to save anything out of the install, your best bet is probably to boot into the live CD and transfer the files you need to back up onto an external drive.

---

### Post by ownx0rz on 2010-02-15
Why is there no way to set the su and resolve my query with the conflicts I presented? Everything works fine and does not have a lock on the icon, except for /dev, /sys, and other miscellaneous files, but I cannot open Synaptic [at all] nor become super user/utilize the sudo command. Here are the contents of my /etc/passwd text file, if it helps:

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:102::/home/syslog:/bin/false
messagebus:x:102:106::/var/run/dbus:/bin/false
hplip:x:103:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:105:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:106:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
haldaemon:x:107:114:Hardware abstraction layer,,,:/var/run/hald:/bin/false
speech-dispatcher:x:108:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
saned:x:110:116::/home/saned:/bin/false
pulse:x:111:117:PulseAudio daemon,,,:/var/run/pulse:/bin/false
gdm:x:112:119:Gnome Display Manager:/var/lib/gdm:/bin/false
plato:x:1000:1000:Plato,,,:/home/plato:/bin/bash

Sorry, I am not exactly pro with UNIX-like systems, but I willfully removed Windows in favor of Ubuntu the day I purchased my Netbook. I know there must be a solution to this, as their always is. I figured I would ask the community before I bothered Evan D, my friend and shell programmer for Canonical, as I perpetually trouble him with my noobishness.

Thanks.

---

### Post by bcbc on 2010-02-15
Boot in recovery mode and drop to the root shell. Then you'll be root. Don't know if it will help you fix it, but at least you'll have the authority to try and recover.

---

### Post by ownx0rz on 2010-02-15
> **bcbc said:**
> Boot in recovery mode and drop to the root shell. Then you'll be root. Don't know if it will help you fix it, but at least you'll have the authority to try and recover.

bcbc, I am not quite sure what you mean. like, right before logging in, I select x-term instead of GNOME as the session manager? that is how I fixed the /home/user permissions to be able to access it, as only the user, root, was able to; even then, I could not become root [I think??], but was able to reverse the damage I wrought on this whole mess of permissions. Is there not a way to be able to become root though something like, uh, chroot or one of those frail attempts of "hacking" Linux computers nocive programmers claim to have the capacity to attack UNIX-based systems? Except, legitimately, through GRUB or whatnot? 

When I turn on my computer, I can enable D12 recovery mode or something, but that only works with the original Windows Recovery Disc, and, being this is a Netbook, was not included. Would you be more specific, please?

---

### Post by cariboo on 2010-02-15
You didn't say what version you were using, but during startup press esc when you see the grub menu in versions before Karmic (9.10), hold down the shift key to see the grub menu in Karmic. Once you have the grub menu up use the arrow keys to select recovery mode, and once at the menu choose drop to root prompt.

---

