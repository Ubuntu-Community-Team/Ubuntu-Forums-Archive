---
title: "Almost got seamlessRDP working."
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by MoLE on 2007-09-06
I'm having trouble with seamless rdp under ubuntu - I've followed the instructions on [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization), but the application can't find it's .ini file.  How can I pass a working directory and a commandline parameter to the windows application?

The Windows shortcut commandline is:
```

Target: C:\zedmed\Patients.exe c:\zedmed\
Start in: "c:\Documents and Settings\%username%"

```

---

### Post by AnRa on 2007-09-06
Just use VirtualBox 1.5, it's easier. ;)

---

### Post by MoLE on 2007-09-06
I should probably clarify that I'm stuck using Win2003 x64 Terminal Services, and I have no control over the server configuration - but am able to install seamlessrdp files in my server userspace.

---

