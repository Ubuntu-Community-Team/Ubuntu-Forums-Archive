---
title: "Standard CPU Speed Setting?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by pablolie on 2010-06-23
For some reason Ubuntu starts up in performance mode for a desktop user I defined. I have to go manually change the setting to OnDemand so that the CPU frequency and power utilization is optimized. Of course to do so I have to enter the administrative password, which I don't want that dekstop user to be able to do.

So - where do I define the standard CPU start-up mode for a user in Ubuntu 10.04?

---

### Post by khelben1979 on 2010-06-23
Isn't Ubuntu able to save the setting and keep it after the system has been rebooted?

---

### Post by pablolie on 2010-06-23
> **khelben1979 said:**
> Isn't Ubuntu able to save the setting and keep it after the system has been rebooted?

Unfortunately that is not the case. Not for the desktop user I defined. The system restarts every time in Performance mode. It does not keep the setting I define -via CPU frequency scaling monitor panel- after entering the administrative password, which is strange.

---

### Post by pablolie on 2010-06-23
I assume the setting is in some system file. Anyone know what file in which location stores the standard CPU setting?

---

### Post by khelben1979 on 2010-06-23
How about giving your desktop user more permissions, so he/she can change the cpu speed setting without letting the user being able to get logged in as root?

I guess it might compromise some security by the above, but have you thought about it?

---

### Post by mc4man on 2010-06-23
It's usually useful for these things  to mention what version of ubuntu you're using.
For lucid (and karmic - but d. check path and filename), simply go
```
gksu gedit /usr/share/polkit-1/actions/org.gnome.cpufreqselector.policy 
```

Scroll down near end of file (around line 142) and change from this
```
<defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR="Blue"]auth_admin_keep[/COLOR]</allow_active>
    </defaults>
  </action>

```

To
```
<defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR="Blue"]yes[/COLOR]</allow_active>
    </defaults>
  </action>

```
blue is the edit needed

(there is another way or two but this is fairly straightforward and simple

---

### Post by pablolie on 2010-06-23
thanks a lot, i will try this out. 

i did mention that this is with 10.04 ubuntu towards the end of my message. :)

---

### Post by mc4man on 2010-06-23
> i did mention that this is with 10.04 ubuntu towards the end of my message.

That you did - my mistake

---

### Post by pablolie on 2010-06-24
thanks so much - it works great now.

---

