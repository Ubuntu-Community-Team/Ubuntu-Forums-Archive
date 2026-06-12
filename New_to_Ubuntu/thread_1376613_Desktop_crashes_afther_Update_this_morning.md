---
title: "Desktop crashes afther Update this morning"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Chris11 on 2010-01-09
I updated this morning several files and after the update there was a reboot request. 

Ubuntu is configurated to not ask password at startup. I rebooted but the Desktops crashes during some moment when the Ubuntu sound is played... I fall back to the login screen and cant get any further. 

I had the same problem after upgrading from 9.04 to 9.10 and resolved it with a fresh install.

What can I do? I'd prefer to no reinstall...

---

### Post by Darce on 2010-01-09
Hi Chris,

Are there any error messages that appear ??

---

### Post by Chris11 on 2010-01-09
no error messages, the process just interumpts and goes back to the loggin screen.. nothing more....

---

### Post by kansasnoob on 2010-01-09
> **Chris11 said:**
> I updated this morning several files and after the update there was a reboot request. 

Ubuntu is configurated to not ask password at startup. I rebooted but the Desktops crashes during some moment when the Ubuntu sound is played... I fall back to the login screen and cant get any further. 

I had the same problem after upgrading from 9.04 to 9.10 and resolved it with a fresh install.

What can I do? I'd prefer to no reinstall...

I'd guess you had a kernel update, possibly from 2.6.31-16 to 2.6.31-17. If so I'd try selecting 2.6.31-16 from the grub menu at startup.

If Ubuntu is your only OS then the grub menu is probably hidden at boot so just after the system screen passes you'll have to press the space bar to "unhide" the menu if you have grub2. If you have legacy grub then you must press the Esc key to unhide the menu.

Also as you're working on this, and you get stuck like that, see if you can reboot by pressing Alt + SysReq + b all at the same time. It's a safer way to reboot than using the power button.

You may also want to try one of the Recovery Mode options from the boot menu. Sometimes that provides helpful info.

---

### Post by Chris11 on 2010-01-09
thank you.... I did the "space bar thing" and curiously this time the desktop loaded normally - I even could no select the kernel the boot process went straight trough... I reboot later and will double check if self healing as occurred ore if it is s temporal phenomena

---

### Post by kansasnoob on 2010-01-09
Well give a shout if things go haywire!

Feel free to send a brief PM pointing me back here.

---

