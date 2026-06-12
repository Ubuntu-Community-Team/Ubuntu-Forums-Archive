---
title: "Simple script to check if command returns 'true' or 'false' won't work"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by MG2R on 2011-03-21
Hi,

I'm writing a simple script to check whether the command
```
gconftool-2 --get /desktop/gnome/peripherals/touchpad/tap_to_click
```returns true or false, in both cases a different command is run.

This is what have until now:
```
if gconftool-2 --get /desktop/gnome/peripherals/touchpad/tap_to_click
then
    notify-send -t 1000 -i /usr/share/icons/Humanity/apps/48/mousepad.svg Tap-Click Enabled
else
    notify-send -t 1000 -i /usr/share/icons/Humanity/apps/48/mousepad.svg Tap-Click Disabled
fi
```But I can't get this script to behave correctly unless I just replace the expression to test with true or false...

any help?

---

### Post by asmoore82 on 2011-03-21
gconftool-2 returns the *text* "true" or "false" &#8212; you need to test for this explicitly:
```
key=[COLOR="Purple"]"/desktop/gnome/peripherals/touchpad/tap_to_click"[/COLOR]
if [ [COLOR="Red"]"$( gconftool-2 --get [COLOR="Purple"]"$key"[/COLOR] )"[/COLOR] = [COLOR="Purple"]"true"[/COLOR] ]; then
    &#8230;
else
    &#8230;
fi
```

Quotations are good :P.

---

### Post by MG2R on 2011-03-21
Thanks!

---

