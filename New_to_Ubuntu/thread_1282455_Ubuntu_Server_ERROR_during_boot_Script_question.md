---
title: "Ubuntu Server ERROR during boot/ Script question"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by sleepy-time-demon on 2009-10-04
Running Ubuntu Server 8.04 because I'd like to keep it constant, rather then constantly updating (which is why I'm waiting until the next LTS to upgrade).

I've got two problems.

The first one is an error message that comes up every time I boot. The error message reads:

[QUOTE=Error Message]device not accepting address 2, error -71[/QUOTE]

I was also wondering, how can I get Sockso Music Server to load on bootup, so I don't need to manually run it every time. It's a SH file.

Thanks

---

### Post by crolanx on 2009-10-04
Could you post some more lines from dmesg, so that I can see, which device cuases this error?

If you want to start the Music Server automatically, just insert the whole path to the shell-script into **/etc/rc.local**. To edit that file, use something like ```
gksudo gedit /etc/rc.local
```.

After you inserted the path to your script, the file could look like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/path/to/your/script.sh
exit 0

```

You'll also need to change the X-Bit of the file by using **sudo chmod a+x /etc/rc.local**.

---

### Post by sleepy-time-demon on 2009-10-04
Attached is the DMESG output.

I'm going to reboot the server, see if your code works.

**EDIT:** It didn't work, it's not loading on the boot.

---

### Post by crolanx on 2009-10-04
Thanks for the output from dmesg. If you take a look at the entry from 27.195924, you can see that there the device is recognized without any errors. About a half second later, it is rejected, but I don't know why.

Maybe you could tell us, which device is connected to your Computer during boot.

Concerning your music server, are you sure that the script which starts the Sockso Music Server is executable by root? And what happens, when you execute the Script for the music service manually, or do the same with **/etc/rc.local**? Does the service start?

---

### Post by sleepy-time-demon on 2009-10-04
> **crolanx said:**
> Thanks for the output from dmesg. If you take a look at the entry from 27.195924, you can see that there the device is recognized without any errors. About a half second later, it is rejected, but I don't know why.

Maybe you could tell us, which device is connected to your Computer during boot.

I've got a USB Hub, a USB mouse, and had a flash drive plugged in once, but I removed it because it wasn't getting used.

> Concerning your music server, are you sure that the script which starts the Sockso Music Server is executable by root? And what happens, when you execute the Script for the music service manually, or do the same with **/etc/rc.local**? Does the service start?

When I launch it manually, it works fine. As for executable by root, I'm not sure... how does one check?

---

### Post by crolanx on 2009-10-05
> I've got a USB Hub, a USB mouse
Do theese devices work as you expect? If they do so, then I'd say that you simply can ignore the error.

> As for executable by root, I'm not sure... how does one check?
You could open a terminal and use
```

ls -l /etc/rc.local
ls -l /path/to/the/other/script.sh

```

In the output of each command, there should be three **x** at the beginning of the line. For rc.local, the output could look like this:
**-rwxr-xr-x 1 root root <some more information> /etc/rc.local**.

You also can look at the propoerties of those files in nautilus. Then you can verify if they are executable at the "page" *Permissions*.

---

