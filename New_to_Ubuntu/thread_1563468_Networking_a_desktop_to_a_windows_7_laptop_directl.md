---
title: "Networking a desktop to a windows 7 laptop directly, and some novice questions"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by cchaos on 2010-08-29
Hi there

I currently share the WIFI connection thats on my laptop to my desktop by LAN (RJ45). Ubuntu is finding [using] this ok, but I would like to know the following:

Is it possible to share the drives on both my laptop and my desktop? I know this is possible (even under windows XP) but so far havent found an option to do this with Ubuntu. To be honest I will probably just share the NTFS partitions that is on a second hard drive.

The reason why I am asking is my laptop has a load of stuff on it that I need on my desktop. I am going to put Windows XP and Windows 7 on my desktop but if I could also do this through Ubuntu, it would be brilliant.

Also, whilst my profile says I have Ubuntu 8.10, I also have the ISO for Ubuntu 10.04 and Ubuntu on my desktop has been updated to Ubuntu 9.10. Would it be worth me installing 10.04 straight away or would it be better to install 8.10 and then upgrade it? I will more than likely totally wipe my booting hard drive as Im not sure how to recover the GRUB and have updated it to the latest GRUB loader (v 1.99?)

Admittedly my experience of Ubuntu is not that great, but I do have a "knack" for sorting out issues with my monitor (which so far has meant editing the monitors.xml) after installing the required driver.

Hoping I havent made this topic too complicated

---

### Post by MattBD on 2010-08-29
Shouldn't be a problem. You might want to check out [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) for details, particularly the part about using Windows XP as a server. It doesn't cover Windows 7, however, but I don't imagine it will be that different,

You might be better off using Ubuntu 10.04 as I believe Windows 7 introduced a new version of NTFS, and so that may well offer better support for the newest version.

---

### Post by skatinjj on 2010-08-29
> **cchaos said:**
> Hi there

I currently share the WIFI connection thats on my laptop to my desktop by LAN (RJ45). Ubuntu is finding [using] this ok, but I would like to know the following:

Is it possible to share the drives on both my laptop and my desktop? I know this is possible (even under windows XP) but so far havent found an option to do this with Ubuntu. To be honest I will probably just share the NTFS partitions that is on a second hard drive.

The reason why I am asking is my laptop has a load of stuff on it that I need on my desktop. I am going to put Windows XP and Windows 7 on my desktop but if I could also do this through Ubuntu, it would be brilliant.

Also, whilst my profile says I have Ubuntu 8.10, I also have the ISO for Ubuntu 10.04 and Ubuntu on my desktop has been updated to Ubuntu 9.10. Would it be worth me installing 10.04 straight away or would it be better to install 8.10 and then upgrade it? I will more than likely totally wipe my booting hard drive as Im not sure how to recover the GRUB and have updated it to the latest GRUB loader (v 1.99?)

Admittedly my experience of Ubuntu is not that great, but I do have a "knack" for sorting out issues with my monitor (which so far has meant editing the monitors.xml) after installing the required driver.

Hoping I havent made this topic too complicated

Also, a fresh install would be better than an upgrade from 8.10

---

### Post by cchaos on 2010-08-29
> **MattBD said:**
> Shouldn't be a problem. You might want to check out [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) for details, particularly the part about using Windows XP as a server. It doesn't cover Windows 7, however, but I don't imagine it will be that different,
Ok, thanks for the link.

Installed samba then lost my internet connection after the reboot :lol: (probably my fault for installing something I didnt need) Uninstalled it and now the connection is back. So far all I have managed to achieve is read access from the desktop to the laptop. The laptop is not finding the desktop. However I will try to see what I need to do and be more careful.

EDIT: Update: scratch the above: its allowing me to read and write now (like it was when I was under XP which is fine :))

Windows 7: turn on file sharing with passwords, and find out the IP address of it on the connection you are connected to (in my case, it is the wired/LAN connection)

Ubuntu: Places, connect to server,  type in the IP address of the above, enter login details, and you should be fine

> **MattBD said:**
> You might be better off using Ubuntu 10.04 as I believe Windows 7 introduced a new version of NTFS, and so that may well offer better support for the newest version.
> **skatinjj said:**
> Also, a fresh install would be better than an upgrade from 8.10
Ok, thought that might be the case :)

---

