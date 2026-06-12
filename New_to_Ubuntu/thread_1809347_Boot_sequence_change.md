---
title: "Boot sequence change"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by WA3ERQ Jim on 2011-07-21
I'm still getting used to 11.04 but I need to change the boot sequence so that the default is Windows 7. The reason is that I use the automatic updater which usually reboots the system but this ends up restarting in 11.04. I need to change this.
 
Thanks
Jim

---

### Post by _0R10N on 2011-07-21
Well, it will depend on the version of grub your system has.

Run 

```
update-grub --version
```

What you have to do is to edit the default entry of grub's menu, so its first choice is always the one you want.

---

### Post by seawolf167 on 2011-07-21
Edit the config file

```
gedit /etc/default/grub
```Change the line that says

```
GRUB_DEFAULT=0
```to

```
GRUB_DEFAULT=**X**
```where you replace the X with the menu item number (starting with 0 for the first entry) of Windows you see in grub upon boot.

Then run 

```
sudo update-grub
```

---

### Post by seawolf167 on 2011-07-21
> **_0R10N said:**
> Well, it will depend on the version of grub your system has.

He is using 11.04, so he'll have GRUB2 by default

---

### Post by WA3ERQ Jim on 2011-07-21
Thanks guys.  Altough I do have 11.04, I did not have Grub2.  I was able to modify my Grub and everything is working fine.
 
Thanks again
 
Jim

---

### Post by seawolf167 on 2011-07-21
> **WA3ERQ Jim said:**
> Thanks guys.  Altough I do have 11.04, I did not have Grub2.  I was able to modify my Grub and everything is working fine.
 
Thanks again
 
Jim

Did you specifically install Grub legacy? Else, if will be Grub2. Grub***2*** won't be displayed, it will show as just Grub (if the commands I posted earlier worked, then you are using Grub2)

If this has been solved, please mark the thread as such under Thread Tools

---

