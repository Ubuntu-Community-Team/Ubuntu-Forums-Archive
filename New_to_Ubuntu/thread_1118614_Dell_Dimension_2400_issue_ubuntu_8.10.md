---
title: "Dell Dimension 2400 issue ubuntu 8.10"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Cxtroen on 2009-04-07
Hi All,

complete ubuntu newbie here so excuse me if I am not quite up to speed. Basic problem of failure to boot I've solved by removing the quiet splash text from the boot kernel as per posts on the forum.

The new problem is after login;
Basically I get an orange screen a mouse pointer but no other interface icons or otherwise to click on....

The mouse moves about but no menus on right or left click and I can't get the console to open.

Keyboard and Mouse seem to work fine as I can key in username password and so on

All ideas welcome

---

### Post by Penguin Guy on 2009-04-07
Try booting into recovery mode, once you are in type [COLOR="DimGray"]startx[/COLOR] to enter the graphical interface.

---

### Post by Cxtroen on 2009-04-07
ok well I tried the boot in recovery mode option  and it gave me a menu to fix things like broken packages as in up down and enter to make them work and finally a boot normally option. There did not seem to be a boot in recovery mode on the menu.

once again into orange screen and nowhere to type startx

---

### Post by presence1960 on 2009-04-07
> **Cxtroen said:**
> ok well I tried the boot in recovery mode option  and it gave me a menu to fix things like broken packages as in up down and enter to make them work and finally a boot normally option. There did not seem to be a boot in recovery mode on the menu.

once again into orange screen and nowhere to type startx


when you choose recovery mode from the GRUB menu that interface that comes up is recovery mode! Boot into recovery mode and choose xfix -  try to fix xserver. If that doesn't work in recovery mode again choose root - drop to shell prompt 
then enter startx

---

### Post by Cxtroen on 2009-04-07
No won't login now just goes to a black screen and hangs
went back to check the kernel cmd line and xfix had restored the quiet splash words so removed them again and login was allowed but no GUI Is it worth my while trying a newer version?? Or can I provide any other info that may help??

---

### Post by presence1960 on 2009-04-07
> **Cxtroen said:**
> No won't login now just goes to a black screen and hangs
went back to check the kernel cmd line and xfix had restored the quiet splash words so removed them again and login was allowed but no GUI Is it worth my while trying a newer version?? Or can I provide any other info that may help??

why don't you let us know your machine's specs: processor, RAM, video card etc. Also which version of Ubuntu are you running? I have to get ready for work but someone here will gladly help you along.

---

### Post by Cxtroen on 2009-04-07
Ok Machine Spec as follows:
Intel Celeron 2.60GHz 1.50GB RAM ACPI Uniprocessor computer Video Card Intel82845G/GL/GE/PV Graphics Controller
Network Adapters Broadcom440 10/100 built in ethernet and D-Link GDWL G520 wireless adapter the DLink being the one in use Ubuntu Feisty from what I remember from the install I did a while back

---

### Post by dmillerw on 2009-04-07
> **Cxtroen said:**
> Ok Machine Spec as follows:
Intel Celeron 2.60GHz 1.50GB RAM ACPI Uniprocessor computer Video Card Intel82845G/GL/GE/PV Graphics Controller
Network Adapters Broadcom440 10/100 built in ethernet and D-Link GDWL G520 wireless adapter the DLink being the one in use Ubuntu Feisty from what I remember from the install I did a while back


Yeah, this is pretty much the same specs that I have, the problem is with Compiz, for some reason it doesn't work with the Intel 82845G graphics, you'll have to wait until 9.04, or use 8.04, which is what I use, the 82845G works fine with Compiz on it

---

### Post by Penguin Guy on 2009-04-07
```
Restart your computer, scroll down to the option that says:
[COLOR="DimGray"]Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)[/COLOR]
Press enter.

Scroll down to the option that says:
[COLOR="DimGray"]root[/COLOR]
Press enter.

It will ask you for a password, type your password in.
Now type [COLOR="DimGray"]startx[/COLOR] into the prompt.
```

[B]If it opens Ubuntu as normal, post that back here.
If it does not open Ubuntu as normal, try this:[/B]

```
Restart your computer, scroll down to the option that says:
[COLOR="DimGray"]Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)[/COLOR]
Press enter.

Scroll down to the option that says:
[COLOR="DimGray"]root[/COLOR]
Press enter.

It will ask you for a password, type your password in.
Now type [COLOR="DimGray"]metacity --replace[/COLOR] into the prompt.
Now type [COLOR="DimGray"]startx[/COLOR] into the prompt.
```

**Post results back here.**

---

### Post by Cxtroen on 2009-04-14
Ok tried all the options you have given guys and still no joy so I'm going to try to install the 9.04 beta and see if that works any better.

Thanks for the help and advice greatly appreciated

---

### Post by Jakey_TheSnake on 2009-04-14
> **Cxtroen said:**
> No won't login now just goes to a black screen and hangs
went back to check the kernel cmd line and xfix had restored the quiet splash words so removed them again and login was allowed but no GUI Is it worth my while trying a newer version?? Or can I provide any other info that may help??

Does Alt+F2 bring up the Run Apps box?

---

