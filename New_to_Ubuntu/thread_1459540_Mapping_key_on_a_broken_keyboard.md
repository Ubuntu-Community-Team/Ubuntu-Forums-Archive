---
title: "Mapping key on a broken keyboard"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by gravender on 2010-04-21
Hello there,

I am running Ubuntu 9.10 (32 bit) on an ageing laptop which has suffered from some rather energetic typing! The keyboard is very much on the way out, and the Z key has failed completely. I would like to squeeze a few more months use out of it. 

Is there any way to map the Caps Lock key - or another key - to make it a replacement Z key? I would ideally want a solution which would allow for Alt-Z and Shift-Z combinations as well.

I have searched in the usual places but can mostly only find keyboard shortcuts and app launchers. There must be a way to do this, mustn't there?

---

### Post by tgalati4 on 2010-04-21
zzzzzzzzzzzzzzzmanzzzzzzzzzzzzzzzzzzz zzzzzzzzzzzzzzxmodmapzzzzzzzzzzzzzzzzzzz

zzzzzzzzzzzmyzzzzzzzzzzz zzzzzzzzzzzzzzzz zzzzzzzzzzzzzkeyzzzzzzzzzzzzz zzzzzzzzzzzstickszzzzzzzzzzz

Use xev to get the key symbol.  It will look something like:

KeyPress event, serial 33, synthetic NO, window 0x1200001,
    root 0x84, subw 0x0, time 50853551, (-256,726), root:(404,751),
    state 0x0, keycode 52 (keysym 0x7a, z), same_screen YES,
    XLookupString gives 1 bytes: (7a) "z"
    XmbLookupString gives 1 bytes: (7a) "z"
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x1200001,
    root 0x84, subw 0x0, time 50853718, (-256,726), root:(404,751),
    state 0x0, keycode 52 (keysym 0x7a, z), same_screen YES,
    XLookupString gives 1 bytes: (7a) "z"
    XFilterEvent returns: False

Make a file .xmodmaprc in your home directory:

cd
nano .xmodmaprc

Put in your new keymapping.

You can search the forums for complete .xmodmaprc files but you just need one or two lines:


.
.
.
keycode  50 = Shift_L
keycode  51 = backslash bar
keycode  52 = z Z
keycode  53 = x X
keycode  54 = c C
keycode  55 = v V
keycode  56 = b B
keycode  57 = n N
keycode  58 = m M
keycode  59 = comma less
keycode  60 = period greater
keycode  61 = slash question
keycode  62 = Shift_R
keycode  63 = KP_Multiply XF86_ClearGrab
keycode  64 = Alt_L Meta_L
keycode  65 = space
keycode  66 = Caps_Lock
.
.
.

Something like:

keycode 52 = Caps_Lock Alt_X

Log out or reboot and the new keymapping should be in effect.

---

### Post by gravender on 2010-04-21
Brilliant, thanks for the speedy reply! I will let you know if I run into any problems.

---

