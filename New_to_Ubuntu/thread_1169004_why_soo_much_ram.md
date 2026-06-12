---
title: "why soo much ram?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by xsabrewulf on 2009-05-24
i have a P3 512 mb of ram

and I just opened up firefox from a fresh reboot
and this is what I get 

[COLOR="Red"]desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           497        412         84          0         15        172
-/+ buffers/cache:        224        273
Swap:         2400          4       2395[/COLOR]



all i have running is firefox and pidgin

why is it taking so much?

---

### Post by CBHedricks on 2009-05-24
I would look at a list of running processes... You can have more processes running in background that would be eating up resources.  If you only look at running (visible) applications you are not seeing the entire list.

CB

---

### Post by Didius Falco on 2009-05-24
> **xsabrewulf said:**
> i have a P3 512 mb of ram

and I just opened up firefox from a fresh reboot
and this is what I get 

[COLOR=Red]desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           497        412         84          0         15        172
-/+ buffers/cache:        224        273
Swap:         2400          4       2395[/COLOR]



all i have running is firefox and pidgin

why is it taking so much?

It's just using what it can. If it wasn't using that ram, it'd be wasted, and you'd be slowed way down by it using the swap file.

Here is my free -m results:
 >              total       used       free     shared    buffers     cached
Mem:          3276       1287       1989          0        753        276
-/+ buffers/cache:        257       3019
Swap:         1027          0       1027
All I have open is Firefox and a Terminal shell. Free RAM is wasted RAM - let it work your 512MB to the bone.

Regards,

Didius

---

### Post by khelben1979 on 2009-05-24
I think more Linux users should know the difference in how Linux handles RAM in comparison to Windows.

[Linux Howtos: Linux Memory Management]("http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm")

---

### Post by XCan on 2009-05-25
Seeing the line: "-/+ buffers/cache: 224 273" I wouldn't say that you're using that much memory considering the fact that Firefox probably is sitting around occupying 120 MB (for no apparent reason? ;) ).

---

