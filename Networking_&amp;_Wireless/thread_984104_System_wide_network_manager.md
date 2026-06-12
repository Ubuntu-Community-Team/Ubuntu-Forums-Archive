---
title: "System wide network manager"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by hanspb on 2008-11-16
I installed Intrepid a while ago, and I was really looking forward to not having to unlock the keyring every time i booted to connect to the wireless network. The short story is that for me this does not work. I can go into Edit Connections and check the "system setting" checkbox, but the setting is not kept. If I click "OK" to go out of the dialog and then go back in, the checkbox is unchecked again. Also if I reboot I have to unlock the keyring. Does anybody have a solution to this?

I have a Broadcom bcm4318 wireless card using b43 driver.

---

### Post by maddentim on 2008-11-30
Hi, not sure if I can help or not, but here are my thoughts.  First, is this a fresh install or did you perform a distribution upgrade from 8.04?  If you upgraded, the problem may be tied to settings from the prior release that did not get changed or something in the new release.  The developer's goal is for this all to go smoothly for one to the other, but I have found that there are things that are missed.  Either something was forgotten, not tested, or most likely I had made changes in the course of using the software, that caused trouble in the new version.  

Anyhow, it is easy to test for this as the cause.  Unless you have been installing lots of software from source it is highly unlikely that you have changed much outside of the home directory that is of consequence.  I suggest that you set up rename your current home directory and make a new one of the same name. Close all open programs and open a terminal.

```
$ sudo mv /home/<username> /home/<username>_old
$ sudo mkdir <username>
```

Then logout (or even better reboot to be extra thorough) and log back in again.  Ubuntu will find your home directory empty and will set up everything from scratch. Test to see if your problem exists with this fresh home directory.  

If the new directory solves the problem, then this would indicate that the problem lies in one of those hidden configuration files or directories in your original user.  In this case, you should probably copy over your documents, music, etc. from the <username>_old directory and leave the settings files behind.  Otherwise, you would have to isolate the problem file / directory.  Good luck!

---

### Post by hanspb on 2008-12-02
Thanks for the reply, but the problem is already solved. It seems that the two checkboxes "Automatic connection" and "System setting" need to be checked in the right order, ans "System setting" must be checked first.

Thanks to [Link at Linux1.no]("http://linux1.no/forum/viewtopic.php?p=1920916#p1920916") for the tip.

---

