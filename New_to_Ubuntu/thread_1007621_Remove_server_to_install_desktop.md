---
title: "Remove server to install desktop?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by PA-J3Cub on 2008-12-10
Hello. I have a laptop that I've installed Ubuntu 8.10 server but I want to remove server and install desktop. I know that I can add desktop gui with the following: 
```
sudo apt-get install ubuntu-desktop
```
however, my laptop is not connected to the internet to get the files.

I figured that I could simply install the live cd and reinstall, or at least get to a live desktop to reformat and/or repartition, however, the live cd crashes and will not load.

Any suggestions how I can install desktop from a CD or blow everything away and start from scratch?

Thanks.

---

### Post by Coreigh on 2008-12-10
How does the LiveCD fail? Boot problems or later? Is it a *really* old laptop? Sometimes booting with 'safe graphics' or 'VGA mode' and disabling ACPI (power management) will solve LiveCD problems.

---

### Post by Michael.Godawski on 2008-12-10
You can also download the alternate installer, which is text-based, and might work although the Live CD crashes.

---

### Post by Coreigh on 2008-12-10
here's the link to the alternate installation methods:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by PA-J3Cub on 2008-12-10
The Live CD boots and the starts to load with the splash screen and progress bar, however, a minute or so into the load the progress bar slows and then stops, the screen blanks, boot process turns to text mode, several I/O and write failures are displayed, then several ```
-bash /dev/null: Permission denied
```are displayed.

This happens if I try to install Ubuntu from the Live CD or test drive it.

---

### Post by Coreigh on 2008-12-10
Its possible you have a bad CD. Does it work on other computers? Did you run the integrity check?

---

### Post by PA-J3Cub on 2008-12-10
> **Coreigh said:**
> Its possible you have a bad CD. Does it work on other computers? Did you run the integrity check?

I did install the desktop edition from the CD on the laptop I'm currently using, however, who knows if the CD is still 100%. The laptop with the issue is at my office. I will check the data integrity tomorrow. Could it actually be that simple?:p

---

