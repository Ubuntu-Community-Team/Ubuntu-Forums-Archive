---
title: "Is there anything you can do when your system freezes, or how to avoid this?"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by jlbr21 on 2009-05-19
I recently upgraded to Jaunty, and it's too bad I did because it's full of bugs. But the one thing that is annoying the heck out of me is the way the system is freezing constantly, pretty much in every session!!

Is there a tool to try to control this, try to snap the system back on, a set of keys, like the ctrl-alt-del of Windoze?

Help would be much appreciated.

Thanks!

---

### Post by raymondh on 2009-05-19
we used to have the ctr + alt + backspace but that combo key is now  disabled by default.  To enable, you'll need to install dontzap.  See the official release notes.

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Of course, you can also enable it by editing the xorg.conf file.

Hope this helps.  Regards.

---

### Post by jlbr21 on 2009-05-19
Done! I hope it helps next time it freezes. 

Thanks a lot!

---

### Post by raymondh on 2009-05-19
Let me add, if you wish to disable dontzap.

in a terminal, enter per line

```
sudo apt-get install dontzap
sudo dontzap --disable
```

Or, if you choose to edit your xorg.conf file, add this:

Section "ServerFlags"
Option "DontZap" "False"
EndSection

Reboot.

Regards.

---

### Post by raymondh on 2009-05-19
Am glad. 

After re-reading  my posts, I may have been confusing as to the term "enable".  Enable meaning enabling the combo key again.... which requires us to DISABLE dontzap.

Also, there's a new combo key which I think is RT CTR + ALT + SYSREQ though I've never used it.

Glad you got it going.  Happy Ubuntuing.

---

### Post by WRDN on 2009-05-19
You have to disable it, because, it is "Dontzap", not "zap". It's inverting the meaning of "dont" i.e. dozap. Do-Don't = Don't, Don't-Don't=Do

---

