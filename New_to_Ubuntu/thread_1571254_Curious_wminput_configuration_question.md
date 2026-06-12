---
title: "Curious wminput configuration question"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by Townley89 on 2010-09-09
Hi all,

I've got the wminput package installed, which lets me connect my wiimote to my computer via bluetooth and use it as a mouse and basic entry option. I found the configuration file for the buttons in etc/cwild/wminput/buttons.

This may sound ridiculous, but I'd like to be able to type using the wiimote. I have a shorthand my friends and I made that uses five fingers to express letters (eg "f" uses the ring and pinky fingers, q is pointer, middle and pinky, etc.) To do this on a wiimote, I'd need to chord the buttons (make pressing the A button + B button do a different action from A or B by themselves.) The configuration file I wrote to test out typing (before I ran out of buttons) is below. 

#Test buttons

Wiimote.A		= KEY_A
Wiimote.B		= KEY_B
Wiimote.A+Wiimote.B	= KEY_X
Wiimote.Up		= KEY_C
Wiimote.Down	= KEY_D
Wiimote.Left	= KEY_E
Wiimote.Right	= KEY_F
Wiimote.Minus	= KEY_G
Wiimote.Plus	= KEY_H
Wiimote.Home	= KEY_I
Wiimote.1		= KEY_J
Wiimote.2		= KEY_K

Nunchuk.C		= BTN_LEFT
Nunchuk.Z		= BTN_RIGHT

The line "Wiimote.A+Wiimote.B	= KEY_X" was an experiment to try to get that to work, which it obviously did not. Once I know this is possible, I'll rearrange the shorthand to be configurable to 6 independent buttons on the wiimote (probably +,-,A,B, up and down) 

I'd also like to know if I could set the configuration file to change some type of profile by pressing 1,2 or 1+2. The idea here is that I could enter a text entry mode by pressing 2, and then return to the navigation options (A is left click, B is right click) that are currently so helpful) by hitting 1. I could even program 1+2 to open a profile filled with commands i often use, like opening firefox, skype or a movies folder.)

Anyway, any help you guys can give towards my silly little project would be most appreciated. 

As always, many thanks.

---

### Post by Townley89 on 2010-09-18
So I've put a bit more work into the problem, and I think I can make some progress if I can figure out how to map a button on the wiimote to a modifying key like shift, ctrl or alt. That'll be helpful for people using this for compiz, google earth, etc. Any suggestions? I've tried this to no avail (note that I changed nunchuk inputs from their defaults.)

#buttons

Wiimote.A		= BTN_LEFT
Wiimote.B		= BTN_RIGHT
Wiimote.Up		= KEY_UP
Wiimote.Down	= KEY_DOWN
Wiimote.Left	= KEY_LEFT
Wiimote.Right	= KEY_RIGHT
Wiimote.Minus	= KEY_BACK
Wiimote.Plus	= KEY_FORWARD
Wiimote.Home	= KEY_HOME
Wiimote.1		= KEY_R
Wiimote.2		= KEY_S

Nunchuk.C		= KEY_Alt
Nunchuk.Z		= KEY_Control

Once again, thanks to anyone that can help.

---

### Post by pi3ch on 2010-09-20
For ALT you can use for example:
> Wiimote.A    = KEY_LEFTALT
so then you can hold A and press other keys on wiimote to get ALT + "" combination.

---

### Post by Rebelli0us on 2011-09-08
Well, did you do it? wminput doesn't make it easy to change config on the fly. But you can easily do it in Windows using GlovePIE because it works with scripts.

---

