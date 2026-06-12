---
title: "Unable to upgrade to 10.04"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by jamil_1 on 2010-05-02
Hi,
 I am currently using Ubuntu 9.10 and can't see/use any option to upgrade to 10.04. Update manager doesn't show an option to upgrade to a newer version neither do I get an option to upgrade when I mount the iso image of the alternate CD. Also running the gksu "sh /cdrom/cdromupgrade" command has no effect. Any help will be much appreciated

Regards
Jamil Haider

---

### Post by WiReIs on 2010-05-02
did you download 10.04LTS iso from the ubuntu website and burn as iso image onto CD, boot from CD

---

### Post by whoop on 2010-05-02
You should be able to see that when you start update manager.

---

### Post by Peter09 on 2010-05-02
Check in the settings for update manager as to what type of notifications that you want. You may have something like 'security' only rather than 'normal'.

---

### Post by WiReIs on 2010-05-02
if you want a fresh install go to ubuntu official website and download ISO image file to suit your system.
once download has finished, insert blank 700mbCD, right click 10.04 ISO image > copy to CD

ubuntu will burn onto CD as an ISO image file..

once finished insert CD again. do not autorun.

restart computer and boot from Live CD

this should allow you to install or play live 10.04 without any system changes

hope this helps

---

### Post by RizSilverthorn on 2010-05-02
If you follow the instructions under "Upgrading Using the Alternate CD/DVD" at [Ubuntu Help - Lucid Upgrades]("https://help.ubuntu.com/community/LucidUpgrades") it will be a much smaller download. My internet based upgrade was going to be a 1.3GB download - this was a 600MB ISO.

---

### Post by jamil_1 on 2010-05-03
Thanks for the reply. I don't want a fresh install of Ubuntu. I have checked my update settings and they seem right to me. I have attached the screen shots.
I have mounted the ISO with mount -o looop command and then tried to update but nothing happens.

[IMG]http://i40.tinypic.com/r1gcvl.jpg[/IMG]


[CENTER][IMG]http://i41.tinypic.com/143j5dx.jpg[/IMG]

[IMG]http://i39.tinypic.com/117seav.jpg[/IMG][/CENTER]

---

### Post by jamil_1 on 2010-05-08
Any help ! :mad:

---

### Post by Paul T. on 2010-05-08
on the window where it says "Release upgrade" try changing this to "Long Term Support Releases (LTS) only"
Then check for updates

---

### Post by jamil_1 on 2010-05-08
It doesn't make any difference :(

---

### Post by dearingj on 2010-05-08
Try this command, either from a terminal or using alt+F2:

```
gksudo update-manager --dist-upgrade
```

---

### Post by jamil_1 on 2010-05-08
But it says your system is upto date nothing to update :confused:

---

### Post by jamil_1 on 2010-05-08
HELP :mad:

---

