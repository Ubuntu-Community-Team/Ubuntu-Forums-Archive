---
title: "Intel Mobile GM965/GL960 Graphics: no compiz in 9.04?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by m_ad on 2009-04-23
I can't enable advanced desktop effects on my fresh 9.04 install. 

I remember having the same problem with my first Ubuntu install, being 7.10 (pretty sure the card was blacklisted). When I upgraded to 8.04, everything was good.

Is it blacklisted again?

```
matt@ubuntu-laptop:~$ sudo lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

Any input would be greatly appreciated.

**EDIT.**

I'm not going to use an unofficial hack to resolve this issue. I'll wait until it's officially fixed.

I love Ubuntu, but why does it seem like it's moving backwards? Why does 8.04 work perfectly out of the box while 9.04 is broken?

In other words, why is my video controller supported in 8.04 but not in 9.04?

---

### Post by crjackson on 2009-04-23
Yes you are correct. It's currently blacklisted as I understand it.

---

### Post by m_ad on 2009-04-23
Wow, how did it get 'un'blacklisted?


This means I might have to go back to 8.04.. this is frustrating

---

### Post by crjackson on 2009-04-23
> **m_ad said:**
> Wow, how did it get 'un'blacklisted?


This means I might have to go back to 8.04.. this is frustrating

Check these threads...


[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
[http://ubuntuforums.org/showthread.php?t=1076014](http://ubuntuforums.org/showthread.php?t=1076014)

---

### Post by m_ad on 2009-04-23
I should have researched this before I installed 9.04. This is very dissapointing.

Back to 8.04

---

### Post by crjackson on 2009-04-23
> **m_ad said:**
> I should have researched this before I installed 9.04. This is very dissapointing.

Back to 8.04

I know how you feel. The bottom thread was started by me while testing.

---

### Post by sam_delta on 2009-04-23
i have the same chipset, and desktop effects work out of the box on fresh install of ubuntu 9.04rc

Sam

---

### Post by m_ad on 2009-04-23
the same chipset?

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller?


are you lucky or is something not right here...?

---

### Post by m_ad on 2009-04-23
> **crjackson said:**
> I know how you feel. The bottom thread was started by me while testing.

Is it bad that I used [this]("http://ubuntuforums.org/showthread.php?p=7126480") fix to bypass this issue?

Seems to be running fine..

---

### Post by m_ad on 2009-04-24
anyone?

---

### Post by jjessew on 2009-04-24
> **sam_delta said:**
> i have the same chipset, and desktop effects work out of the box on fresh install of ubuntu 9.04rc

Sam

I have the same issue.  I did my testing with 9.04rc, and everything worked great including compiz...  So I installed a fresh copy of 9.04 final release yesterday, and now compiz doesn't work.

Should I just stick with the RC?  Or is this something that will be sorted out in the near future?

---

### Post by jackson.arw on 2009-04-26
Dude,
 try the fix listed by m_ad, I have on my IBM T61 and it works a treat.

Quote
Type in terminal sudo gedit /usr/bin/compiz

find the line 

T="$T 8086:2a02 " # Intel GM965

then put a # in front like this

#T="$T 8086:2a02 " # Intel GM965

then save then log out and back in 

then enable by right clicking on the desktop
End Quote

From this thread :-
[http://ubuntuforums.org/showthread.php?p=7126480](http://ubuntuforums.org/showthread.php?p=7126480)

---

### Post by m_ad on 2009-05-01
I'm not going to use an unofficial hack to resolve this issue. I'll wait until it's officially fixed.

I love Ubuntu, but why does it seem like it's moving backwards? Why does 8.04 work perfectly out of the box while 9.04 is broken?

In other words, why is my video controller supported in 8.04 but not in 9.04?

---

### Post by m_ad on 2009-05-02
Any comments?

---

### Post by m_ad on 2009-05-03
On more try.

---

### Post by sam_delta on 2009-05-03
from ubuntu 9.04 release notes:

> These freezes happen particularly often on the i965 chips (359392). For that reason, desktop effects were disabled by default on this chipset in the final release. They will be re-enabled in a 9.04 Update once the problem has been fixed. 

also if you'd like to install older intel drivers, heres documentation to do so:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)


Sam

---

### Post by m_ad on 2009-05-04
Thanks Sam,

I'll stick to 8.04. I don't want to retry 9.04 after I spent a lot of time reverting back to 8.04 (reinstalling, updating, configuring). Believe me, if I *knew* my graphics controller would work by installing old drivers, I would do it in a heart beat. I love having the newest version of Ubuntu.

Until the update comes and I know I'll have a working 9.04, I'll stick to 8.04.

I'm still thinking; **How does Ubuntu 8.04 support my graphics controller, but 9.04 doesn't?** Seems backwards to me.

---

### Post by pedor on 2009-05-05
m_ad: I have the same question. It seems that the driver development is going backwards . That goes for both my Intel cards. :confused:
Se also [http://ubuntuforums.org/showthread.php?t=996506](http://ubuntuforums.org/showthread.php?t=996506)

---

