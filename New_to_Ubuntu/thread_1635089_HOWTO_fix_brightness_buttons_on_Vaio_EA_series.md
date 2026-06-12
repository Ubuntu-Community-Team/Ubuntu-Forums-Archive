---
title: "HOWTO: fix brightness buttons on Vaio EA series"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by sirwhiteout on 2010-12-01
There is a lot of scattered information across the internet on this issue on several laptop models. This is a crude attempt to make it easier to find a workaround for a particular laptop model: The Vaio VPCEA which uses the integrated Intel Graphics processor.

The problem: Fn+F5 and Fn+F6 don't do what they are supposed to do (adjust brightness down and up, respectively), although the power manager seems to get it right (ie. the monitor dims when on battery). If the system is able to change screen brightness but the Fn keys are being ignored, then this tutorial is for you.

The workaround: create the ACPI events which will adjust brightness and link them to the correct keystrokes.

[LIST=1]
[*]Get the [scripts]("http://paste.ubuntu.com/518967/")
 to adjust brightness (thanks to Mario Zaizar for the code) and follow the instructions written therein. Save them as brightness_up.sh and brightness_down.sh, respectively.

[*]Find out the code for the Fn+F5 and Fn+F6 keystrokes. Run command

```
acpi_listen
```

and hit the key combination. The first line should be the signal that the key has been pressed and the second line is the signal that it has been released.

My output was:

[LIST]
[*]Fn+F5: sony/hotkey SNC 00000001 00000010
[*]Fn+F6: sony/hotkey SNC 00000001 00000011
[/LIST]

[*]Create the files sony-brightness-up and sony-brightness-down on /etc/acpi/events/ Their contents should be like

```

# /etc/acpi/events/sony-brightness-up

event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/brightness_up.sh

```

and

```
# /etc/acpi/events/sony-brightness-down

event=sony/hotkey SNC 00000001 00000010
action=/etc/acpi/brightness_down.sh

```

Naturally, replace what is after "event=" with the output you got from acpi_listen. These files are now set to call the scripts you saved earlier at the destination in their instructions.

[/LIST]

This was tested on a Vaio VPCEA running Maverick 64-bit.

The caveat: This workaround skips over libnotify, so it doesn't produce the nice notifications on Gnome of brightness going up and down. If anyone knows how to get that working, I would be greatly pleased.

Hope this helps.

---

