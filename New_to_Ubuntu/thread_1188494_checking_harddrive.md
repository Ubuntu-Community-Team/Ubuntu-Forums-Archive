---
title: "checking harddrive"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by 2blue on 2009-06-15
Is there an ubuntu tool that can check the hard drive for faults, or at least tell if it probably all right?

---

### Post by whoop on 2009-06-15
If you want to check the filesystem, ubuntu does that every 30 boots or so (fsck). If you want to check the health of your hd itself you can try smartmontools.

---

### Post by SoftwareExplorer on 2009-06-15
I'm pretty sure that the file system is check every so many reboots, if that is what you are talking about.

EDIT:looks like whoop beat me to it...

---

### Post by mgmiller on 2009-06-15
Or you can run fsck your self from a command line.  Here is a quick rundown of some of the options:

** fsck**

  Filesystem consistency check and interactive repair. Journaling file systems avoid the need to run fsck.
 Syntax
      fsck [*options*] [*filesystem*] ...

Options
  --     Pass all subsequent options to filesystem-specific checker.
         All options that fsck doesn't recognize will also be passed.

  -r     Interactive mode; prompt before making any repairs.

  -s     Serial mode.

  -t [I]fstype
[/I]         Specify the filesystem type. Do not check filesystems of any other type.

  -A     Check all filesystems listed in /etc/fstab.

  -N     Suppress normal execution; just display what would be done.

  -R     Meaningful only with -A: check all filesystems listed in /etc/fstab except the root filesystem.

  -T     Suppress printing of title.

  -V     Verbose mode.

EXIT CODES

  1    Errors were found and corrected.
  2    Reboot suggested.
  4    Errors were found but not corrected.
  8    fsck encountered an operational error.
  16   fsck was called incorrectly.
  128  A shared library error was detected. The return status is the exit status of the last command    executed in consequent-commands, or zero if none were executed. 



For more info here is a link:
[http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

---

### Post by Cheesemill on 2009-06-15
It is also possible to force a filesystem check on next boot by doing:
```
sudo touch /forcefsck
```

---

### Post by halitech on 2009-06-15
not Ubuntu related but you could also try the tools from the Ultimate boot cd to test the health of the drive with programs from the manufactorer,

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by 2blue on 2009-06-16
Thanks to all of you! 

I have lots to work with now :p

---

