---
title: "HOWTO: boot maverick on a Toshiba NB series laptop"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by conor on 2010-10-10
Hello, 

A lot of us Toshiba users (and some lenovo users have been having trouble getting ubuntu online due to a powersaving bug. This bug still exists in the final release, and thus I'm writing this HOWTO for anyone who is having trouble getting started.


After a fresh install of maverick: 

1 - When booting, hold left shift to access the grub menu. (If you have a dual-boot setup, then the menu might show up automatically)

2 - Highlight the ubuntu entry and press e to edit the options.

3 - Add 'intel_idle.max_cstate=0' after the words 'quiet splash'

4 - Hit ctrl-x to boot the computer.

5 - Once you've booted into ubuntu, press alt-F2 to open a run dialog and enter
```
gksu gedit /etc/default/grub

```

6 - look for the line that reads
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

this should be the 9th line. Modify it to read:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=0"


7 - Save the file and exit.

8 - Open a terminal and type the following:
```
sudo update-grub
```

This is all the steps. Now everytime you boot the computer, this option will be active.

---

### Post by pwebster25 on 2010-11-02
This did just the trick.  My boot times on a Toshiba NB205 were at about 10 minutes.  I couldn't figure it out.  This simple changed fixed me up.  We are back to 30ish seconds.

Thanks
paul

---

### Post by psychok7 on 2010-12-10
not working for me..followed all the steps (and everything is right) and its still slow when booting
using nb200

> **conor said:**
> Hello, 

A lot of us Toshiba users (and some lenovo users have been having trouble getting ubuntu online due to a powersaving bug. This bug still exists in the final release, and thus I'm writing this HOWTO for anyone who is having trouble getting started.


After a fresh install of maverick: 

1 - When booting, hold left shift to access the grub menu. (If you have a dual-boot setup, then the menu might show up automatically)

2 - Highlight the ubuntu entry and press e to edit the options.

3 - Add 'intel_idle.max_cstate=0' after the words 'quiet splash'

4 - Hit ctrl-x to boot the computer.

5 - Once you've booted into ubuntu, press alt-F2 to open a run dialog and enter
```
gksu gedit /etc/default/grub

```

6 - look for the line that reads

this should be the 9th line. Modify it to read:


7 - Save the file and exit.

8 - Open a terminal and type the following:
```
sudo update-grub
```

This is all the steps. Now everytime you boot the computer, this option will be active.

---

