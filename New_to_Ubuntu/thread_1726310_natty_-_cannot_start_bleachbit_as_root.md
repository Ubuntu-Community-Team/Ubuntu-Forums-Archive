---
title: "natty - cannot start bleachbit as root"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by fremantle on 2011-04-11
[CODE][abr@abr-mini:~$ gksudo bleachbit
info: starting BleachBit version 0.8.7
debug: chown(/root/.config/bleachbit/bleachbit.ini, uid=1000)
    from Cleaner import backends
  File "/usr/share/bleachbit/bleachbit/Cleaner.py", line 44, in <module>
    import Special
  File "/usr/share/bleachbit/bleachbit/Special.py", line 27, in <module>
    from Options import options
  File "/usr/share/bleachbit/bleachbit/Options.py", line 246, in <module>
    options = Options()
  File "/usr/share/bleachbit/bleachbit/Options.py", line 44, in __init__
    self.restore()
  File "/usr/share/bleachbit/bleachbit/Options.py", line 149, in restore
    self.set_list('shred_drives', Unix.guess_overwrite_paths())
  File "/usr/share/bleachbit/bleachbit/Options.py", line 195, in set_list
    self.__flush()
  File "/usr/share/bleachbit/bleachbit/Options.py", line 62, in __flush
    General.chownself(Common.options_file)
  File "/usr/share/bleachbit/bleachbit/General.py", line 76, in chownself
    assert(path.find('/root') != 0)
AssertionError/CODE]

what could be the issue?

---

### Post by beew on 2011-04-11
It turns out that ```
sudo bleachbit 
``` would work.

I know it doesn't make sense, logically it should be "gksudo" but I ran into the same problem as you do. A simple sudo would do.

---

### Post by madjr on 2011-04-11
might want to report the bug

---

### Post by Andrew.Z on 2011-06-09
[BleachBit 0.8.8 beta 2 supports Ubuntu 11.04 (Natty) ](http://bleachbit.sourceforge.net/news/bleachbit-088beta2) running as administrator.  Version 0.8.7 is allergic to a change in Ubuntu 11.04 (through it worked fine in 10.10).

---

### Post by Frogs Hair on 2011-06-09
I have 0.8.7  working fine in 11.04 Unity ?

---

### Post by fremantle on 2011-06-10
i fixed the sudo issue by fixing the command in alacarte

---

### Post by tim fitzgerald on 2011-06-11
I had the same problem and nothing anyone suggested worked. I discovered myself that during start up if you choose Ubuntu classic the choice to run as administrator still works.
Then it is a simple matter of placing the Bleachbit Icon on the desktop, restarting your computer and this time deselecting Ubuntu classic and chose Ubuntu. when it starts your Bleachbit Icon is still on the desktop. Right click the icon and you can choose to run as Administrator. 
   Hope this helps.

---

