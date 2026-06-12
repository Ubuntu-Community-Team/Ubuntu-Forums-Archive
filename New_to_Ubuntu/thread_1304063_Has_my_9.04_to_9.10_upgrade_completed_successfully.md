---
title: "Has my 9.04 to 9.10 upgrade completed successfully?"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-10-28
Hi everyone,

I recently typed this into terminal:
```
update-manager -d
```

To force an early upgrade to 9.10. About halfway through, the  wireless internet was cut off. 

Now that I've got internet back again, I typed this into terminal:
```
root@girdy-laptop:/home/girdy# sudo dpkg --configure -a
root@girdy-laptop:/home/girdy# 

```

I also launched update-manager -d as root, but update manager seems blank (no updates available). This is good!! :D , right? Doesn't that mean my system is up to date? 

Have I successfully upgraded to Ubuntu 9.10? 
BTW, that new boot splash and login screen look bada**. Good job developers! :popcorn:
Is there any other sure-fire command that can be issued from terminal to tell if this upgrade has completed successfully?

:wink:Thanks in advance, linux community! :guitar:

---

### Post by Gazneth on 2009-10-28
Open your system monitor application, under the menu: system administration the first tab will tell you your release version.

---

### Post by asuastrophysics on 2009-10-28
[[img=http://img687.imageshack.us/img687/8664/screenshot.th.png]](http://img687.imageshack.us/i/screenshot.png/)
I also notice that "Add/Remove" in the Gnome-Main-Menu is now called "Ubuntu Software Center".

But I still don't have the option to "disable the touchpad while typing"
in System -> Preferences -> Mouse 

From what I understand, this was supposed to be included in 9.10.
Here is the output of uname -a:
```
girdy@girdy-laptop:~$ uname -a
Linux girdy-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
girdy@girdy-laptop:~$

```

Are you sure it upgraded successfully? Is that output in terminal terminal normal?

---

### Post by Gazneth on 2009-10-28
The terminal output is correct for version 9.10. I would assume your upgrade was successful the thing to do now is use it to check for stability.  I don't know about the touchpad issue.

---

### Post by lavinog on 2009-10-28
> **asuastrophysics said:**
> 
To force an early upgrade to 9.10. About halfway through, the  wireless internet was cut off. 


The update manager will download all packages prior to installing the update.  If the network was disconnected you would get a warning that not all packages could be downloaded.  Once downloaded, you shouldn't need the network anymore.

---

### Post by MrWES on 2009-10-28
> **asuastrophysics said:**
> [[img=http://img687.imageshack.us/img687/8664/screenshot.th.png]](http://img687.imageshack.us/i/screenshot.png/)
I also notice that "Add/Remove" in the Gnome-Main-Menu is now called "Ubuntu Software Center".

But I still don't have the option to "disable the touchpad while typing"
in System -> Preferences -> Mouse 

From what I understand, this was supposed to be included in 9.10.
Here is the output of uname -a:
```
girdy@girdy-laptop:~$ uname -a
Linux girdy-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
girdy@girdy-laptop:~$

```

Are you sure it upgraded successfully? Is that output in terminal terminal normal?

```
lsb_release -a
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

```

---

### Post by asuastrophysics on 2009-10-28
Thanks! :popcorn:

I guess the upgrade did complete successfully after all.

Thanks for all your help! :guitar:

---

