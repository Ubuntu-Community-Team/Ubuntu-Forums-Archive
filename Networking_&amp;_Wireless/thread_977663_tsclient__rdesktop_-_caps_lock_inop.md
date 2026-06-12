---
title: "tsclient / rdesktop - caps lock inop"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by toyoder on 2008-11-10
The caps lock key doesn't work or 'flow thru' to the terminal session.
(If the user holds the shift key caps will type thru to the terminal session.)

Within tsclient on the 'local resources' tab I selected the keyboard language
to "en-us" and I've tried enabling the "window manager's key bindings" 
option under the tsclient performance tab without any noticeable benefit. 

Is there a setting within tsclient, rdesktop or Gnome that will enable the 
caps lock functionality?

---

### Post by jimv on 2008-11-10
Try the gnome-rdp client instead.  It's so much faster than the one that comes with Ubuntu...and your capslock might work too.

sudo apt-get install gnome-rdp

---

### Post by toyoder on 2008-11-10
> **jimv said:**
> Try the gnome-rdp client instead.  It's so much faster than the one that comes with Ubuntu...and your capslock might work too.

sudo apt-get install gnome-rdp
Thanks for the suggestion...
:-(
Sadly I must report Gnome-RDP suffers the same trouble as tsclient(as does grdesktop too). Caps lock setting dose not pass thru to the terminal server session.

Where oh where is this hidden bit found?

---

### Post by apedraza on 2008-11-10
It is a regression since it used to work in Hardy.

---

### Post by toyoder on 2008-11-11
> **apedraza said:**
> It is a regression since it used to work in Hardy.

That being the case, with whom or where should I file the bug report?

---

### Post by dmsimms on 2008-11-11
> **apedraza said:**
> It is a regression since it used to work in Hardy.

I'm having the same problem; caps lock isn't "detected" when I remote desktop (using tsclient) into a Windows 2003 machine (haven't tried other versions of Windows). Shift seems to work fine. This was working for months in Ubuntu 8.04, and stopped working when I upgraded to 8.10.

---

### Post by paulie420 on 2008-11-12
same ISSUE thou i did find a work around, BUT IT does screw things up a bit in ubuntu, thou it does allow the caps lock to function normal in terminal services, the num pad unfortunately does not work thou. here IS what i did>

SYSTEM> preferances > keyboard > click on the LAYOUTS tab, select "OTHER OPTIONS..."

find caps lock behavior and expand the options, select CAPSLOCK TOGGLES SHIFT SO ALL KEYS ARE AFFECTED."

like i said, ALL SEEMS NORMAL in rdesktop (terminal services) but, UBUNTU, ACTS A LITTLE CRAZY SINCE IT THINKS YOUR HOLDING THE SHIFT KEY, when you attempt to move a window with capslock off in ubuntu< it moves very erratically -, but terminal services does not think the same thing,  i HOPe they come out with a fix for this one, I use rdesktop religiously since everything at work is operated by microsoft products.

PAUL

ps (this is occurring after the upgrade from 8.04 TO 8.10) and this is the message that keeps occurring in the terminal window i start rdesktop in;

"WARNING: No translation for (keysym 0xffe6, Shift_Lock)" & "WARNING: No translation for (keysym 0xfef9, Pointer_EnableKeys)" thou i think the last error has to do with numpad not working in rdesktop using the temporary fix i put in place.  i will try to keep up today with the issues and fixes i find.

---

### Post by PascalNobus on 2008-11-27
Try hitting [Ctrl][Shift][NumLock] at the same time,
or [Shift][Numeric 7]

---

### Post by kribba on 2008-12-03
I've got the same problem when I upgraded to 8.10. But after I removed the rdesktop package using synaptic and downloaded the .deb package from the Hardy release (v 1.5.0 something) and installed, I now got the caps lock to work properly in krdc since it depends on rdesktop as many other clients do.

I just hope no other issue shows up using this combination...

---

### Post by sql on 2008-12-23
while using rdesktop  try 

rdesktop -k common ...

instead of 

rdesktop -k en-us...

 may be it help.

all variants of key "-k" are names of files in folder /usr/share/rdesktop/keymaps/

at least in Fedora Core

---

### Post by mpadams on 2009-01-06
I can verify this issue for 2003 & 2000 servers. Using the -L or -K options do not help. -y will enable CAPS, but disable arrow keys: it also negates the L or K options.

There's a bug of this reported at rdesktop.org: something's not playing nice with whatever version of X.org is in use on 8.10.

---

### Post by mpadams on 2009-01-07
[https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/254968](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/254968)

Some posters in the bug-fix area have figured out some solutions. I have my own that goes to the source: I've rewritten most of the keyboard scanfile to use newer keyboard codes & recompiled the program against Jaunty's X11 & SSL libraries. For those that are brave, I've provided a bzip2ed-binary you can try that may work for you: if you want to build your own...

1. Grab the include file from the bug page & the source code from rdesktop.org
2. (sudo / as root) apt-get install build-essential libssl-dev libx11-dev libasound2-dev
3. Edit the ./configure file to change "/usr/local" to "/usr"
4. Run ./configure with --with-x --with-ipv6 --with-sound=alsa --enable-static-openssl --enable-smartcard

*EDIT: Further testing... w & t don't stay capped, regardless of which scancode I use; holding SHIFT works fine for them though. I still believe the permanent solution is to rewrite the keyboard handler.

---

### Post by Xires on 2009-01-15
--- /usr/share/rdesktop/keymaps/common.orig	2009-01-15 12:32:10.000000000 -0600
+++ /usr/share/rdesktop/keymaps/common	2009-01-15 12:00:40.000000000 -0600
@@ -225,5 +225,6 @@
 #
 # Inhibited keys
 #
-Caps_Lock 0x0 inhibit
+#Caps_Lock 0x0 inhibit
+Caps_Lock 0x3a capslock
 Multi_key 0x0 inhibit

---

### Post by mpadams on 2009-01-15
[http://www.assembla.com/wiki/show/rdesktop-xkb](http://www.assembla.com/wiki/show/rdesktop-xkb)

Another developer has started a temporary fork to pin down the keyboard issues for good.

---

### Post by mpadams on 2009-01-19
Another solution: use the Debian unstable rdesktop that doesn't have the Alt-Linux keyboard patch in it. Also supports IPv6.

[http://packages.debian.org/unstable/x11/rdesktop](http://packages.debian.org/unstable/x11/rdesktop)

---

### Post by lazman on 2009-04-15
> **mpadams said:**
> Another solution: use the Debian unstable rdesktop that doesn't have the Alt-Linux keyboard patch in it. Also supports IPv6.

[http://packages.debian.org/unstable/x11/rdesktop](http://packages.debian.org/unstable/x11/rdesktop)

This solution works for me. I'm connecting to an XP box. Everything seems to work great now. However, now there is an update because I'm using an older version of rdesktop. I do not know if there is a way to keep this from updateing. It would be nice to have the updater to not check this package at all, at least for now.

Thanks for posting the solution to this!

---

### Post by lazman on 2009-04-17
I found out how to keep it from updating. Go to Synaptic Package Manager, type in rdesktop in the search at the top, make sure rdesktop is highlighted, then in the top menu click on Package->Lock Version. This will prevent the updater from checking this file, and you will not have the update icon unless you have other updates.

---

### Post by tonywang86 on 2009-07-08
A simple method to solve the problem:

[https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/254968](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/254968)

---

### Post by ChinnoDog on 2009-10-29
> **Xires said:**
> --- /usr/share/rdesktop/keymaps/common.orig	2009-01-15 12:32:10.000000000 -0600
+++ /usr/share/rdesktop/keymaps/common	2009-01-15 12:00:40.000000000 -0600
@@ -225,5 +225,6 @@
 #
 # Inhibited keys
 #
-Caps_Lock 0x0 inhibit
+#Caps_Lock 0x0 inhibit
+Caps_Lock 0x3a capslock
 Multi_key 0x0 inhibit

Thanks! Fixed for me. I wonder why it is inhibited in the keymap....

---

### Post by AlmarS on 2010-02-05
> **Xires said:**
> --- /usr/share/rdesktop/keymaps/common.orig    2009-01-15 12:32:10.000000000 -0600
+++ /usr/share/rdesktop/keymaps/common    2009-01-15 12:00:40.000000000 -0600
@@ -225,5 +225,6 @@
 #
 # Inhibited keys
 #
-Caps_Lock 0x0 inhibit
+#Caps_Lock 0x0 inhibit
+Caps_Lock 0x3a capslock
 Multi_key 0x0 inhibit

Yes, this solution worked for me too. Thanks!

---

### Post by sstvinc2 on 2010-05-19
> **Xires said:**
> --- /usr/share/rdesktop/keymaps/common.orig    2009-01-15 12:32:10.000000000 -0600
+++ /usr/share/rdesktop/keymaps/common    2009-01-15 12:00:40.000000000 -0600
@@ -225,5 +225,6 @@
 #
 # Inhibited keys
 #
-Caps_Lock 0x0 inhibit
+#Caps_Lock 0x0 inhibit
+Caps_Lock 0x3a capslock
 Multi_key 0x0 inhibit

Fantastic!  Worked perfectly for me

---

### Post by ontwowheels on 2010-06-19
> **sstvinc2 said:**
> Fantastic!  Worked perfectly for me

ditto

---

