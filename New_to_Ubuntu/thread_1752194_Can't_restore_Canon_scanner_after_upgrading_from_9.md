---
title: "Can't restore Canon scanner after upgrading from 9 to 10"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by ffrr on 2011-05-07
Hi,

After upgrading from 9.something to 10.04 my Canon Pixma MP 640 no longer responded. I got the latest version of libsane backend (1.0.22). I then uninstalled the older version that had been working and reinstalled the new one. (shell command "make install"). Everything seemed to work. The compile finished. The applications menu shows the "XSane Image Scanner" in the Graphics section. If I click it a tab appears on the open-windows bar at the bottom. It says "Starting XSane Image Scanner" After ten seconds it disappears and that's it.

The shell command "sane-find-scanner" succeeds like so:

found USB scanner (vendor=0x04a9 [Canon], product=0x173f [MP640 series]) at libusb:002:004

The command "scanimage -L" fails:

scanimage: error while loading shared libraries: libsane.so.1: cannot open shared object file: No such file or directory.

"find / -name libsane.so.1* -ls" turns up:

262998  304 -rwxr-xr-x  1 root  root  310795 May  7 17:05 /usr/local/lib/libsane.so.1.0.22
263079    0 lrwxrwxrwx  1 root  root         17 May  7 17:05 /usr/local/lib/libsane.so.1 -> libsane.so.1.0.22

'libsane.so.1' is there all right in the shape of a link to 'libsane.so.1.0.22'. I have no clue what to do next. Unfortunately the error message doesn't offer any actionable hints.

Suggestions most welcome

Frederic

---

### Post by ffrr on 2011-05-10
The OP says:

Zero responses in three days! Guess I misposted to the wrong user segment and will check for other options. If anyone could offer suggestions in this respect I'd be most grateful.

Frederic

---

