---
title: "Thunar autodetection doesn't work"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by Buce on 2009-07-13
I installed ubuntu with the Minimal CD, and Thunar autodetection isn't working. I have both thunar and thunar-volman installed, and the checkbox under Thunar -> Edit -> Prefs -> Advanced -> Volume Management is ticked, but CDs, etc still won't show up. If I were doing this under Arch, my previous distro, I know the thing to check next would be hal or dbus, but I'm not sure how I would do this in Ubuntu.

---

### Post by tarps87 on 2009-07-14
You could try starting them, they are in /etc/init.d/
If they are already running it will tell you rather than report that it has failed. If it is not on my set up it is linked as K16hal in /etc/rc1.d/ and S24hal in /etc/rc2.d/ rc3.d rc4.d and rc5.d
Rather than in rc.conf under daemons ;)
Although I think the minimal cd sets up hal and all the polices and permissions needed to work.

Have you check dmesg when you put the cd in?

---

### Post by Buce on 2009-07-14
I don't see anything that looks relevant in dmesg.

```
$ dmesg | tail
[   65.680849] wlan0: RX authentication from 00:14:51:6f:b8:3d (alg=0 transaction=2 status=0)
[   65.680853] wlan0: authenticated
[   65.680856] wlan0: associate with AP 00:14:51:6f:b8:3d
[   65.682465] wlan0: RX AssocResp from 00:14:51:6f:b8:3d (capab=0x411 status=0 aid=5)
[   65.682470] wlan0: associated
[   68.652753] [drm] Initialized drm 1.1.0 20060810
[  105.225542] NET: Registered protocol family 10
[  105.225818] lo: Disabled Privacy Extensions
[  106.259347] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  115.951595] wlan0: no IPv6 routers present
```

dbus is running fine, but it looks like hal isn't even installed. There's no hal file in /etc/init.d/, and nothing with 'hal' in the filename in /etc/rcX.d/. And apt-get seems to agree:

```
$ sudo apt-get install hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  acl hal-info libpolkit-dbus2 libpolkit-grant2 libpolkit2 libsmbios1 pm-utils
  policykit powermgmt-base
Suggested packages:
  gnome-device-manager libsmbios-doc
Recommended packages:
  libsmbios-bin radeontool uswsusp vbetool policykit-gnome
The following NEW packages will be installed:
  acl hal hal-info libpolkit-dbus2 libpolkit-grant2 libpolkit2 libsmbios1
  pm-utils policykit powermgmt-base
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 871kB of archives.
After this operation, 4170kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

Should I go ahead and install hal, or does ubuntu use something else that I need to configure?

---

### Post by Buce on 2009-07-14
I installed hal, and it looks like it worked. Doesn't seem to detect my mic, though.

---

### Post by Buce on 2009-07-14
Okay, fixed that by installing esd.

Thanks a bunch!

---

### Post by tarps87 on 2009-07-15
Looks like you have solved it, I didn't realise the minimal cd doesn't install hal by default.
Just looked and cds don't appear to be reported in dmesg so nothing odd there.

---

### Post by Buce on 2009-07-15
> **tarps87 said:**
> Looks like you have solved it, I didn't realise the minimal cd doesn't install hal by default.

Yeah, I thought that odd too. *shrug*

---

