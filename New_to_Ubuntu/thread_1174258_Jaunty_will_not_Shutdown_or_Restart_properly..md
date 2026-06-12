---
title: "Jaunty will not Shutdown or Restart properly."
date: 2009-05-30
forum: New to Ubuntu
---

### Post by lazukars on 2009-05-30
I can no longer get Juanty to shutdown or restart properly.  When you click on the shutdown or restart option from the top panel, a dialog apprears asking you if you want to restart or shutdown.  If you click OK nothing happens after that.  

I have always used this way of shutting down or restarting in the past and all of a sudden this problem has happend.  Now the only way to shutdown or restart is to physically push the power button on the computer.  YIKES!

Any help would be greatly appreciated.

Ryan

---

### Post by blueridgedog on 2009-05-30
Perhaps if you try and shutdown in a terminal, we can get some more information.  It may tell you what is happening.

Try:

```
such /sbin/shutdown -r now
```

This will tell the system to reboot.  Look for error messages as it attempts to do so.

To shutdown, you can change the -r to a -h (for halt).

Post back any error message you get.

---

### Post by lazukars on 2009-05-31
Tried that, but it comes back "such" command not found.

---

### Post by ibutho on 2009-05-31
The command should be "sudo" and not "such". I think it was a typo.

---

### Post by blueridgedog on 2009-05-31
Right...fat finger typo on my part.

---

