---
title: "Problems with Nautilus"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by Buleste on 2011-05-21
I'm trying to use Nautilus to change permissions for a folder (something I need to do to fully install some software) but whenever I open Nautilus I get the following message

> ** (nautilus:1553): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '1553'

(nautilus:1553): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
Can someone help me  solve this please.

---

### Post by Gone fishing on 2011-05-21
This is when you open nautilus from the the terminal with gksudo nautilus? The error is in the terminal but nautilus opens? Ignore it.

have a look at:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/499288](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/499288)
[http://ubuntuforums.org/showthread.php?t=566572](http://ubuntuforums.org/showthread.php?t=566572)

I'd suggest you change permissions with chown or chmod depending what you wish to do.

[http://wiki.mybb.com/index.php/HOWTO_Chmod](http://wiki.mybb.com/index.php/HOWTO_Chmod)
[http://www.tuxfiles.org/linuxhelp/fileowner.html](http://www.tuxfiles.org/linuxhelp/fileowner.html)

---

### Post by Buleste on 2011-05-21
Can't install Samba as it looks like it's vanished (404 error) and I'm pretty much a full on noob with Linux. I was using "sudo nautilus /" as per the install instructions for the software. What is the difference between sudo and gksudo?

---

### Post by Gone fishing on 2011-05-21
Samba can't have vanished - what repositories are you using?

You should gksu or gksudo when using graphical applications as you could potentially mess up some file permissions.

---

### Post by Buleste on 2011-05-23
I tried under Ubuntu Vista ooops I mean 11.04 using the proper software thingy (can't remember now as I got rid of 11.04 as it is useless) and also tried ```
sudo apt-get install samba smbfs
```. Both yielding the 404 error. I have since installed 10.04 and it works under that. Just wish I'd known at the time 11.04 = bad. 10.04 = good.

---

