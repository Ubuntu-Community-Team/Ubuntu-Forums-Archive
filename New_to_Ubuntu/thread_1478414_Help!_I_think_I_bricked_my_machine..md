---
title: "Help! I think I bricked my machine."
date: 2010-05-09
forum: New to Ubuntu
---

### Post by selittl on 2010-05-09
I installed Lucid Lynx on my ASUS supposedly to dual boot with win 7.  after reboot this is all I get

error: no such device: 70ff467b-e242-43e7-97a3-ac431f823737.
grub rescue>



It does not allow me to input anything.  hitting return has no effect, if I turn off the machine and try to reboot the livecd nothing happens...just goes into this screen and nothing.

I cannot boot win 7, and cannot get to my bios setup.

Asus Eeebox PC EB1501
Intel® Atom™ N330 Dual Core
NVIDIA® ION

---

### Post by kmsalex on 2010-05-09
From the live cd go to system-administrator-software sores. 
Check anything that isn't checked except the cd.
Then go to applications-accessors-terminal.
In the terminal type the following.

```
sudo apt-get install testdisk
```

It will then prompt you for your password nothing will appearer. 
This is normal just type it in and hit enter.
after it installs go ahead and enter

```
sudo testdisk
```

If prompted enter your pass word again, now you should be in testdisk.
You don't have to recored a log so select don't recored anything.
Then copy every thing in the terminal and post it in your next post.

---

### Post by utnubuuser on 2010-05-09
There is another thread, almost identical to what you're describing...> [http://ubuntuforums.org/showthread.php?t=1477020](http://ubuntuforums.org/showthread.php?t=1477020)

---

### Post by selittl on 2010-05-10
Thank guys, got it up an running.

---

### Post by narendraD on 2010-05-11
If your issue is solved pl mark the thread as SOLVED

---

