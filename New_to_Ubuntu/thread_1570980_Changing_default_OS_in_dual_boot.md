---
title: "Changing default OS in dual boot"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by jbarntt on 2010-09-09
Hi,

I'm dual booting Ubuntu 10.04 and Windows XP.

After upgrading to Ubuntu 10.04, my preference for default boot up was changed from XP to Ubuntu. How can I make XP the default ? In the past I used Webmin to do this, but I guess the Webmin Grub module hasn't been updated to Grub 2.

TIA

jbarntt

---

### Post by Windows Nerd on 2010-09-09
> **jbarntt said:**
> Hi,

I'm dual booting Ubuntu 10.04 and Windows XP.

After upgrading to Ubuntu 10.04, my preference for default boot up was changed from XP to Ubuntu. How can I make XP the default ? In the past I used Webmin to do this, but I guess the Webmin Grub module hasn't been updated to Grub 2.

TIA

jbarntt
So just to be clear, are you using GRUB or GRUB2? 

If you are running Grub, could you run in the terminal:

```
cat /boot/grub/menu.lst
```

Or, if you are running Grub2, could you run:

```
cat /boot/grub/grub.cfg
```

Scott

---

### Post by jbarntt on 2010-09-09
Running Grub2

File you recommended looking at says do not edit

---

### Post by Windows Nerd on 2010-09-09
> **jbarntt said:**
> Running Grub2

File you recommended looking at says do not edit
I know, I am not going to ask you to edit it. I just need to see it's content to help you out.
Could you post the output of ```
cat /boot/grub/grub.cfg
```. And now that I know you are using Grub2, could you also post the output of:
```
cat /etc/default/grub
```
For me please.

Scott

---

