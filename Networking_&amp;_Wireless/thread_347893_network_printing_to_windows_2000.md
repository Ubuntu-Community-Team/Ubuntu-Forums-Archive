---
title: "network printing to windows 2000"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by maclenin on 2007-01-27
This is a re-post of a [thread]("http://ubuntuforums.org/showthread.php?t=346355") re: network printing - thanks for whatever help you can  provide....

---

### Post by maclenin on 2007-01-29
I think I've figured it out: CUPS seems to be the (short) answer, along with a few simple mods to /etc/samba/smb.conf. I still have to re-test to confirm my result - however, in a nutshell and very crudely:

1. /etc/samba/smb.conf

Make certain the (linux) worgroup name matches the windows workgroup name.

2. CUPS

Follow the instructions at [http://localhost:631](http://localhost:631) and enter the printer address as smb://guest@192.168.xxx.xxx/shared_printer_name (with "guest" being one of the activated user accounts (no password) on the windows machine and 192.168.xxx.xxx being the ip address of the host computer - to which the shared printer is attached).

Any observations?

---

