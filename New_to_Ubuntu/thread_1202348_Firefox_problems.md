---
title: "Firefox problems"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by ltwinner on 2009-07-02
This is my first time using linux and I've installed the latest ubuntu release. It came with firefox 3.0.8. Im experiencing various problems with firefox which are

1) The search bar in the top right isn't working at all.
2) The back and forward buttons are greyed out and don't work at all.
3) I changed some settings in preferences such as home page and font size and type however when I close firefox and reopen it the settings have reverted to the defaults.
4) When I logged into this forum firefox asked if I want it to remmber this password, not for this site, etc... however clicking any of these options did nothing.

Anyone able to help me out in getting these problems sorted as this is ruining my firefox experience and by extension my linux experience.

---

### Post by lovinglinux on 2009-07-02
This problem is covered in the troubleshooting section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). You basically need to delete the file *places.sqlite* from the profile folder. Everything you need to perform this task is described there.

---

### Post by nothingspecial on 2009-07-02
Not a fix in itself but you could try installing the latest firefox release.

Search for firefox-3.5 in synaptic package manager

---

### Post by lovinglinux on 2009-07-02
> **nothingspecial said:**
> Not a fix in itself but you could try installing the latest firefox release.

Search for firefox-3.5 in synaptic package manager

The solution I gave him will fix the problem.

---

### Post by ltwinner on 2009-07-02
> **lovinglinux said:**
> This problem is covered in the troubleshooting section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567"). You basically need to delete the file *places.sqlite* from the profile folder. Everything you need to perform this task is described there.

I just deleted places.sqlite but it didn't work. When I relaunched firefox after deleting it, the same problems were still there however now there are files appearing in my folder such as places.sqlite-1.corrupt, places.sqlite-2.corrupt, places.sqlite-3.corrupt, etc... Every time I go to a new page a few more of these files appear.

Edit: btw the folder I found places.sqlite in was home/.mozilla/firefox/vkuuxfit.default. There were only two files in the firefox folder - vkuuxfit.default and profiles.ini

---

### Post by lovinglinux on 2009-07-02
> **ltwinner said:**
> I just deleted places.sqlite but it didn't work. When I relaunched firefox after deleting it, the same problems were still there however now there are files appearing in my folder such as places.sqlite-1.corrupt, places.sqlite-2.corrupt, places.sqlite-3.corrupt, etc... Every time I go to a new page a few more of these files appear.

Edit: btw the folder I found places.sqlite in was home/.mozilla/firefox/vkuuxfit.default. There were only two files in the firefox folder - vkuuxfit.default and profiles.ini

Close Firefox, move the folder /home/.mozilla/firefox/vkuuxfit.default to somewhere else to avoid loosing your profile, then start Firefox again. This should solve your problem. This issue is described on the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567), from posts #3 to #7.

---

