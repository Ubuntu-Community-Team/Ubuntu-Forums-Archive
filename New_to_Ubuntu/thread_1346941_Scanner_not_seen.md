---
title: "Scanner not seen"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Nottawa on 2009-12-05
I can't use my scanner.  I have a Canoscan 4400F scanner.  I am using Jaunty on a Thinkpad T400.  When I load the Xsane software it tells me there is no device connected.  My scanner works well in Windows XP. When I click help, I get the following:

No devices available
Possible reasons:
1) There really is no device supported by SANE
2) Supported devices are busy
3) The permissions for the device file do not allow you to use it-try as root
4) The backend is not loaded by SANE (man sane-dll)
5) The backend is not configured correctly  (man sane-"backendname")
6) Possibly there is more than one SANE version installed


How do I try some of these suggestions?  I know reason 2 is not the problem.

---

### Post by halitech on 2009-12-05
with the device connected, what is the output of lsusb? also, dmesg may give us some info.

---

### Post by Nottawa on 2009-12-05
Here is the output of lsusb:

peter@peter-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 04a9:2228 Canon, Inc. CanoScan 4400F
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
peter@peter-laptop:~$ 


Does this help?

---

### Post by halitech on 2009-12-06
[color="red"]Bus 001 Device 007: ID 04a9:2228 Canon, Inc. CanoScan 4400F[/color]

the scanner is being seen, thats a good thing. Try pressing ALT + F2 and running ```
gksudo xsane
```
and see if the scanner is being seen that way. If it is, its just a permissions issue with the device.

---

### Post by sandyd on 2009-12-06
time for new scanner.
[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

---

### Post by halitech on 2009-12-06
the info there looks to be almost 2 years out of date so its hard to say if it is still currently unsupported. I'd say give it a go and see what happens.

---

### Post by renkinjutsu on 2009-12-06
and if it IS a permission issue, it'll be a good idea to check if you're in the right group to use the scanner..
to check what group you're in type this in terminal: ```
groups
```

that should give you a list of groups your user is in.. check if your user is in the group "lp", if not, you can add it with ```
sudo usermod -a -G lp username
```

---

