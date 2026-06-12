---
title: "Problem on boot --- 8.10"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by nitr0smash on 2009-01-17
I installed ubuntu on my machine and set it up as a dual boot with Windows XP.  Ubuntu installed just fine, and I was able to use it normally for a while.  Then I decided to reboot the computer.  I selected to boot to Ubuntu, and instead of booting to the desktop GUI, it says Kinit: No resume image, doing normal boot...    And then gives me a command line interface instead of going to ubuntu's GUI.  How do I access the GUI from here, and, even better, how can I get ubuntu to boot directly to the GUI instead of to the command line interface?   Thanks for all help.

---

### Post by utnubuuser on 2009-01-17
Don't suppose it's just a matter of "sudo startx"?

---

### Post by nitr0smash on 2009-01-18
Entering   sudo startx   gives me another series of error messages:


Module Loader present
markers: (--) probed, (**) from config file, (==) default setting,
         (++) from command line, (!!) notice, (II) informational,
         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 18 16:17:07 2009
(==) Using config file : "/etc/x11/xorg.conf"
(WW) fglrx: No matching Device section for instance (Bus ID PCI:0@1:0:0) found
(WW) fglrx: No matching Device section for instance (Bus ID PCI:0@1:0:1) found
(WW) fglrx: No matching Device section for instance (Bus ID PCI:0@2:0:0) found
(WW) fglrx: No matching Device section for instance (Bus ID PCI:0@2:0:1) found
(EE) No devices detected

Fatal server error:
no screens found
giving up.

xinit: Connection refused (errno 111) unable to connect to X server
xinit: No such process (errno3): Server error.

Again, thanks for all help.

---

### Post by diablo75 on 2009-01-18
It seems like there is a misconfiguration for your video card.  Try typing this into the terminal window:

(you might be at a root prompt so you may not need to type sudo... but if you aren't at a root prompt type):

**sudo dpkg-reconfigure xorg-xserver**

Answer all the questions.  When you get to the one about using the kernel buffer, say no.

Once that's all done, you can type **sudo init 6** at the prompt to restart the PC.

---

### Post by nitr0smash on 2009-01-18
This gives me:

Package 'xorg-xserver' is not installed and no info is available.
Use dpg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (=dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xorg-xserver is not installed

---

### Post by diablo75 on 2009-01-18
> **nitr0smash said:**
> This gives me:

Package 'xorg-xserver' is not installed and no info is available.
Use dpg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (=dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xorg-xserver is not installed

Not installed?  That's crazy talk...

Well... If you have an internet connection you could try:

**sudo apt-get install xorg-xserver**

No promises that will work; it's just a guess.

---

### Post by nitr0smash on 2009-01-18
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package xorg-server


The system does have a solid internet connection.

---

### Post by diablo75 on 2009-01-18
Another shot in the dark:

sudo aptitude install xorg

Correction:

After looking at [this thread]("http://ubuntuforums.org/archive/index.php/t-498313.html") I think the command you should try is:

sudo apt-get install xserver-xorg

---

### Post by nitr0smash on 2009-01-18
Reading package lists... Done
Building dependency tree
Reading state information... Done
xserver-xorg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 216 not upgraded.

---

### Post by diablo75 on 2009-01-18
Well you've stumped me.  Something you might try is to go into your grub menu by pressing ESC when it says "Loading grub menu" and select an older kernel from the list if there's one available to see if that works.  You might also try recovery mode and see if the repair utility works.  I've never used it so I can't say what it does or doesn't do...

---

### Post by MenZa on 2009-01-18
> **diablo75 said:**
> Well you've stumped me.  Something you might try is to go into your grub menu by pressing ESC when it says "Loading grub menu" and select an older kernel from the list if there's one available to see if that works.  You might also try recovery mode and see if the repair utility works.  I've never used it so I can't say what it does or doesn't do...

You really had it the first time; you just tried to reconfigure the wrong package. :)

Try doing the following, nitr0smash:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by nitr0smash on 2009-01-18
Okay, after going through that reconfiguration, and trying sudo startx, I'm given this:

Module Loader present
markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 18 20:08:20 2009
(==) Using config file : "/etc/x11/xorg.conf"
Primary device is not PCI
(EE) No devices detected

Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno3): Server error.
xauth: error in locking authority file /home/[username]/.Xauthority

---

### Post by MenZa on 2009-01-18
> **nitr0smash said:**
> Okay, after going through that reconfiguration, and trying sudo startx, I'm given this:

Module Loader present
markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 18 20:08:20 2009
(==) Using config file : "/etc/x11/xorg.conf"
Primary device is not PCI
(EE) No devices detected

Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno3): Server error.
xauth: error in locking authority file /home/[username]/.Xauthority

You're just supposed to type 'startx'. You don't need sudo.

---

### Post by nitr0smash on 2009-01-18
Same thing happens either way.

---

### Post by MenZa on 2009-01-18
Which graphics card do you have? Please paste the output of `lspci`.

---

### Post by nitr0smash on 2009-01-18
Well, I can't really copy paste from the terminal, because for one, it's running on a different computer than the one I'm using here on the forum.  The other reason is due to the nature of my problem:  I'm not accessing the terminal from withing Ubuntu's GUI, this is at boot.  When I enter in   lspci   it seems that it reports back so much text that it more than one screen can hold, so something is being lost up top.

What I can tell you is that I have two Radeon HD 4850s in Crossfire configuration.

---

### Post by metallicamike on 2009-01-18
> **nitr0smash said:**
> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package xorg-server


The system does have a solid internet connection.

try doing that again with "xserver" not "server";) a simple typo goes a long way :lolflag:

---

