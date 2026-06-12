---
title: "No gdm anymore"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by Mazza558 on 2009-01-27
I don't know what I've done, but I no longer have gdm at startup. I have to login at command line and type "startx" to do anything.

How can I solve this problem?

---

### Post by blueridgedog on 2009-01-27
What are your options under System -> Administration -> Login Window?

Is GDM set to run?

System -> Administration -> Services and look for GDM.

---

### Post by Mazza558 on 2009-01-29
On the services applet, the unlock button and the options are greyed out, even when run as root. 

Is there a config file which does the same thing?

---

### Post by jualin on 2009-01-29
Try this command > sudo dpkg-reconfigure gdm before typing the "startx" command. This should reconfigure the GDM login. Hope this helps!

---

### Post by jualin on 2009-01-29
Also you can look at [this suggestion]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/232059") which may work for you.

---

### Post by Mazza558 on 2009-01-29
> **jualin said:**
> Also you can look at [this suggestion]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/232059") which may work for you.

Looks like I just need to start gdm to get access to the services applet, and then turn off kdm, which is ticked as well as gdm - and is probably the root of the problem. I'll do that once updates are finished.

---

### Post by jualin on 2009-01-29
Keep us updated! :lol:

---

### Post by blueridgedog on 2009-01-29
I would like to see the output of:

```
ls -al /etc/rc2.d
```

Prior to any editing.  I am curious what has turned gdm off.

---

### Post by Mazza558 on 2009-01-30
I've disabled kdm but suffer the same problem - no gdm at startup.

Here's the output of ls -al:

> total 20
drwxr-xr-x   2 root root  4096 2009-01-29 19:29 .
drwxr-xr-x 149 root root 12288 2009-01-30 18:35 ..
-rw-r--r--   1 root root   556 2009-01-20 15:22 README
lrwxrwxrwx   1 root root    19 2008-11-21 16:24 S01policykit -> ../init.d/policykit
lrwxrwxrwx   1 root root    17 2008-11-21 16:24 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx   1 root root    15 2008-11-21 16:24 S10acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root    25 2008-11-21 16:24 S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx   1 root root    18 2008-11-21 16:24 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root    34 2008-11-21 16:24 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx   1 root root    15 2008-11-21 16:24 S11klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root    14 2008-11-21 16:24 S12dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root    22 2008-11-21 16:24 S14avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx   1 root root    23 2009-01-15 18:38 S17mysql-ndb-mgm -> ../init.d/mysql-ndb-mgm
lrwxrwxrwx   1 root root    19 2009-01-15 18:38 S18mysql-ndb -> ../init.d/mysql-ndb
lrwxrwxrwx   1 root root    15 2009-01-15 18:38 S19mysql -> ../init.d/mysql
lrwxrwxrwx   1 root root    14 2008-11-21 16:24 S20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root    14 2008-11-21 16:24 S20cups -> ../init.d/cups
lrwxrwxrwx   1 root root    22 2008-11-21 16:24 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root    19 2008-11-21 16:24 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx   1 root root    15 2008-11-21 16:24 S20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root    15 2008-12-03 18:37 S20samba -> ../init.d/samba
lrwxrwxrwx   1 root root    15 2009-01-15 17:11 S20saned -> ../init.d/saned
lrwxrwxrwx   1 root root    17 2008-12-06 20:07 S20winbind -> ../init.d/winbind
lrwxrwxrwx   1 root root    13 2008-11-21 16:24 S24hal -> ../init.d/hal
lrwxrwxrwx   1 root root    20 2008-11-21 16:24 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx   1 root root    24 2008-11-21 16:24 S28NetworkManager -> ../init.d/NetworkManager
lrwxrwxrwx   1 root root    13 2008-11-21 16:24 S30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    31 2008-11-21 16:24 S30system-tools-backends -> ../init.d/system-tools-backends
lrwxrwxrwx   1 root root    28 2008-11-22 20:28 S31usplash-smooth-get -> ../init.d/usplash-smooth-get
lrwxrwxrwx   1 root root    20 2009-01-29 19:29 S50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx   1 root root    16 2009-01-29 19:29 S50apport -> ../init.d/apport
lrwxrwxrwx   1 root root    17 2008-11-21 16:24 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root    13 2008-11-21 16:24 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root    14 2008-11-21 16:24 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root    24 2008-11-21 16:24 S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx   1 root root    17 2008-11-21 16:24 S98usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root    22 2008-11-21 16:24 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root    21 2008-11-21 16:24 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root    18 2008-11-21 16:24 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root    19 2008-11-21 16:24 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx   1 root root    24 2009-01-17 20:44 S99stop-bootchart -> ../init.d/stop-bootchart
lrwxrwxrwx   1 root root    24 2008-11-21 16:24 S99stop-readahead -> ../init.d/stop-readahead


---

### Post by blueridgedog on 2009-01-30
Well, it is set to load:

> lrwxrwxrwx 1 root root 13 2008-11-21 16:24 S30gdm -> ../init.d/gdm

Can you verify that you are at run level to with the command:

```
runlevel
```

And can you see if there is an error regarding gdm during boot with:

```

dmesg
```

If you tell it to start, I assume it starts fine:

```
sudo /etc/init.d/gdm &
```

---

### Post by Mazza558 on 2009-01-31
I've added a script to init.d to autostart it and that works fine.

---

### Post by Adarzh on 2009-01-31
Whats the use of this command
> ls -al /etc/rc2.d

Adz

---

