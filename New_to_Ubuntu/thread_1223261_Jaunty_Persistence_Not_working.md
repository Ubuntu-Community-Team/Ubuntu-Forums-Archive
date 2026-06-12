---
title: "Jaunty Persistence Not working"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by pspsampsp on 2009-07-25
Ok , so i created a live usb with 2gb of persistence , however everything is forgotten on shutdown - persistence is not working , i have done it with the fedora live usb creator , the Ubuntu Startup disk creator and following this tutorial: [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/) , but with all of them the persistence has never worked , could someone help me get it working.

---

### Post by C.S.Cameron on 2009-07-26
Strange that you are not getting persistence with any of those three methods.
When booting you can check for the persistent flag when you get to the second screen, (the one after languages).
Press F6 for boot options and you should see the following line:
"append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --"
If persistent does not appear in that line type it after "splash -- ".
continue the boot to see if the session is persistent.
If so type "gksu nautilus" click "file system", double click "cdrom" then "syslinux" then "text.cfg" find the line above and add "persistent" as shown or after "splash -- "

---

### Post by squashpup on 2009-08-23
[http://ubuntuforums.org/showthread.php?t=1247384&highlight=usb+persistence](http://ubuntuforums.org/showthread.php?t=1247384&highlight=usb+persistence)

---

