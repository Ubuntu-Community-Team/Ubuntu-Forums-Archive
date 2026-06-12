---
title: "ubuntu 9.10 fails to prompt for password"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by brianxc on 2010-03-04
Hi all,

Am very new to all this, but have installed ubuntu 9.10 on a thumb drive 8Gb, and boot up from the thumb drive.

All seems to work fine, and I have created a username and password for myself.

However, initially the system auto-logged in without a password prompt with username "ubuntu".

I cannot seem to change this and have it prompt the user to select a user and then request a password.
.
I have gone to the " System->administration->login screen " option and selected "show the screen for chosing who to log in". andselected "close".

I looked at the /etc/gdm/custom.conf file, and this seems to have changed as expected to :

AutomaticLoginEnable=false
AutomaticLogin=
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=10

However, once I restart the lapop, then the system persists in logging is as ubuntu, without a password. The /etc/gdm/custom.conf file has reverted back to :

AutomaticLoginEnable=true
AutomaticLogin=ubuntu
TimedLoginEnable=true
TimedLogin=ubuntu
TimedLoginDelay=10

For some reason, the auto login settings seem to revert back to the original settings, no matter what I do.


Could any of you guys point me in the right direction as to what I would need to do to resolve this?

Best regards,

Briant

---

### Post by laidback on 2010-03-04
Try System>Admin>Log in>Security then deselect Automatic login against your user id.

---

### Post by brianxc on 2010-03-09
Hi,
 Way beyond that point....

I use the System->Admin->login screen facility, it seems to work fine, I have checked the relevant config files and these have changed in accordance with the changes made with "Login screen"

However, once I restart ubuntu, the configuration has reverted back to it's original state, i.e. user "ubuntu" is logged in, with no prompt for password.

I tinnk its something to do with persistence of configuration settings when running unbuntu from a pen drive/flash drive.

At my wits end on this one!!

Cheers,

Brian

---

### Post by undecim on 2010-03-09
How did you install Ubuntu to the thumb drive? The USB startup disk creator? If so, then did you select the option to reserve room for settings and documents?

Also, if you want this password as a means of protecting your files on the thumb drive, forget it, because anyone with the thumb drive can just plug it into an Ubuntu computer and mount the persistent space to get your files.

If you want to protect the files on it, you need to install ecryptfs.

---

