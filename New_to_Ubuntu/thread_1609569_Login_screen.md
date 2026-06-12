---
title: "Login screen"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by Janos1 on 2010-10-30
Hi to all.Any help with the login screen,if computer go to hibernate and try to work again,ask for password,what ever i try to do ask for password.Try to understand Ubuntu but don't understand why is that Security for me alone.Nobody using my computer only me,why i have-not log in for all day,and dont ask that stupid login all time.Am using ubuntu 10.10  .Thank you for your help

---

### Post by fly-by-night on 2010-10-30
[http://ubuntuforums.org/showthread.php?t=1476854](http://ubuntuforums.org/showthread.php?t=1476854)

> **P4man said:**
> press alt+f2 and run 

```
gconf-editor
```

browse to

/apps/gnome-power-manager/lock/hibernate

Disable it.

---

### Post by Janos1 on 2010-10-30
Thank you for your help,try and do not make any dif.Same thing again,when go to hibernate ask for password,i try to do anything ask for password.Right now i try to install XBMC,always ask for password.Sorry just do not understand that kind of security when only one person using my computer,that is ME.

---

### Post by bioterror on 2010-10-30
> **Janos1 said:**
> Thank you for your help,try and do not make any dif.Same thing again,when go to hibernate ask for password,i try to do anything ask for password.Right now i try to install XBMC,always ask for password.Sorry just do not understand that kind of security when only one person using my computer,that is ME.

I feel your pain with suspend, but otherwise, this is worth of reading [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

I dont have gnome system running myself in my hands atm, but in Lubuntu I removed that "ask password on resume" -feature by disabling it from screensaver settings.

Edit: I had to come to my desktop computer with Gnome DE and I checked Menu -> Preferences -> Screensaver -> uncheck box "Lock screen when screensaver is active".

---

### Post by Janos1 on 2010-10-30
Thank you for your help,am not a Linux guy so can not go that deep into that.Last time i used DOS was 1989. Since only Windows,now that is the first year i try Ubuntu.Read in the forum for newbie like me not a good solution to edit SUDO and to be root.Try to read one more time what you suggest.Thank you.




edit:Thank you i try let see what happens.

---

### Post by sisco311 on 2010-10-30
Hi Janos1,

It's unusual on a Linux system, but you may have to reboot in order the changes to take effect. See the last post here: [thread]1304705[/thread].

Remélem ez használ. (Hope this helps). :)

---

### Post by Janos1 on 2010-10-30
Thank you Sisco311,i try and it is working now.(Koszonom):Janos

---

### Post by sisco311 on 2010-10-30
> **Janos1 said:**
> Thank you Sisco311,i try and it is working now.(Koszonom):Janos

Szivesen, máskor is! (My pleasure!)

Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

Thanks.

---

### Post by Janos1 on 2010-10-30
Koszonom megegyszer.

---

### Post by Janos1 on 2010-10-30
Koszonom megegyszer.

---

