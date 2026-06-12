---
title: "NVIDIA stopped working"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by Cambo15 on 2011-03-09
I am new to linux and have been dual booting ubuntu 10.10with win 7 for a little over a week now. Last night when I tried to boot I could only boot in consol mode, and then after i used recovery mode and turned my video card off I could boot in low graphics mode. I am using a new sony vaio with an nvidia card and everything was working great with ubuntu until last night. PLEASE HELP!!!

---

### Post by PunkLV on 2011-03-09
1: When you boot in a normal way what **exactly** happens?
2: Which nvidia drivers are you using?
3: Did you by any chance performed an update/upgrade (are there new entries for Ubuntu in GRUB boot menu?)
4: If you are able to login to shell, please post **cat /etc/X11/xorg.conf**

---

### Post by Cambo15 on 2011-03-10
When i boot normally, it does a lot of failing and brings up a window that says it is running in low-graphics mode. i press okay and it brings me to the menu where i can reconfigure graphics, restartx, or un in low graphics mode for one session. when i restartx or run in low graphics it takes me to the shell and the last line is:
 
/etc/rc2.d/S99acpi-support: line 7: /usr?share/acpi-support/power-funcs: No such file or directory
and there is a little flashing underscore that i can't do anything with.
 
when i cancel out of that menu i can get to shell log in though.
 
when i boot in recovery, it just takes me to the shell as **root@cameron-VPCF136FM****:~#.** but when i use **startx **it takes me to a default desktop.
 
i don't know the drivers i was using, but i did update with the synaptic package manager.
 
When i post **cat /etc/X11/xorg.conf** it comes up with "no such file or directory"

---

### Post by Hippytaff on 2011-03-10
I think it's looking for the acpi device, so it's likley to be a driver thing. try booting into low graphics mode and installing the driver from System -> Administration -> additional drivers
```

[B]cat /etc/X11/xorg.conf

```

Does the same with me too...can't find not there. I think something to do with dbus xorg.conf isn't needed, but I'll need to double check that
[/B]

---

### Post by Cambo15 on 2011-03-11
that's one of my problems though. it won't open up the additional drivers. then i tried to remove and re-install it, and now i cannot access the internet with wifi or a cable.

---

### Post by Hippytaff on 2011-03-11
try highlighting ubuntu on the grub menu (where you choose which OS to load - assuming your dual booting). Press e, then change 'quiet splah' to 'nomodeset'. press CTRL+x to boot. You should be able to log into ubuntu now. Then try the driver from addition drivers again. (you should get ethernet connection)

---

### Post by Cambo15 on 2011-03-11
That didn't change anything

---

### Post by Hippytaff on 2011-03-11
ok go to the grub menu again. at the end of the quiet splash bit try acpi=off, or noacpi and CTRL+X to boot.

---

### Post by Cambo15 on 2011-03-11
still not working

---

### Post by Hippytaff on 2011-03-11
Then i'm Right Out of suggestions...Lets hope someone can Lend a hand ;-)

---

### Post by Cambo15 on 2011-03-11
Alright, so I just re-installed ubuntu. Now what should I do to make sure my drivers work properly and stay that way.

BTW: thanks for the effort

---

