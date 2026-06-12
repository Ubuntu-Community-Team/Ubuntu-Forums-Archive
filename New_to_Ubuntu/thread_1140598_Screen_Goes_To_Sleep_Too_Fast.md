---
title: "Screen Goes To Sleep Too Fast"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by RookieUbuntuUser58 on 2009-04-27
Well yeah thats the problem on my laptop. I followed the tips and tricks on [Lesswatts.com]("http://www.lesswatts.org/projects/powertop/") and this problem started happening. I think its xset +dpms but Im not sure. I tried turning it off (through steps on google) but its not working. How should I fix this issue?

Btw the power management settings don't affect this issue. Tried changing the settings but it doesn't override these settings.

---

### Post by unutbu on 2009-04-27
Please post the output of 

```
xset q
```

To change the amount of inactivity period (in seconds) before the machine goes into "standby", "suspend" or "off" modes, run the command

```
xset dpms A B C
```

where A is the number of seconds till standy,
B is the number of seconds until suspend,
C is the number of seconds until off.

You can set any of these modes to never by setting its corresponding value to 0.

You can turn off DPMS entirely running
```

xset -dpms
```

Run 

```
man xset 
```

for all the details.

---

### Post by RookieUbuntuUser58 on 2009-04-27
The output is:

```
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

---

### Post by unutbu on 2009-04-27
Hm. Your xset settings look fine.
Did you say you also have tried setting System>Pref>Power Management and System>Pref>Screensaver ?

---

### Post by RookieUbuntuUser58 on 2009-04-27
> **unutbu said:**
> Hm. Your xset settings look fine.
Did you say you also have tried setting System>Pref>Power Management and System>Pref>Screensaver ?

Yeah Ive tried those. No luck. Im gonna reinstall 9.04.

---

### Post by Scenemaker on 2011-02-11
Resurrecting an old thread here, but I have the same issues with my laptop.  Using the GUI, the settings appear to be useless.  I tried turning dpms off with no success.  The standyby/ suspend/ off settings were already at 0 but I went ahead and reset them to 0 anyway.  Ubuntu still kicks me out in a minute or two.  While typing this, I thought maybe I should try setting the standby/suspend/off settings to 1/2 hour, hour and two hours.  Still does not work.  Anyone have any other ideas?

---

