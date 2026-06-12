---
title: "Keyboard problems"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by ozzyprv on 2009-03-29
Everything was working fine with my laptop (see specs at signature) until a couple of resets ago.
Now the systems does not recognize the numbers in the extended section of my keyboard (Num Lock section).

The curious part is that the keys are recognized at the log in screen (user name and password). But once the graphic environment is loaded not anymore. I have tried OpenOffice, Notes editor, terminal, and nothing.

I am not sure what to do. Help please.

Thanks.

---

### Post by ozzyprv on 2009-03-29
> **ozzyprv said:**
> Everything was working fine with my laptop (see specs at signature) until a couple of resets ago.
Now the systems does not recognize the numbers in the extended section of my keyboard (Num Lock section).

The curious part is that the keys are recognized at the log in screen (user name and password). But once the graphic environment is loaded not anymore. I have tried OpenOffice, Notes editor, terminal, and nothing.

I am not sure what to do. Help please.

Thanks.
Right after posting, I realized that since the problem starts after initiating the graphic environment, it should be something to do with the X server.
I went and had a look at the system log. First time ever...
This is what I got, not sure if it helps, I do not know how to read it myself but for some reason it does not make sense that there are two KEYBOARD entries.

> (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event2"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
AUDIT: Sun Mar 29 10:20:58 2009: 7064 X: client 4 rejected from local host ( uid=0 gid=0 pid=7082 )
AUDIT: Sun Mar 29 10:21:08 2009: 7064 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7086 )
AUDIT: Sun Mar 29 10:21:08 2009: 7064 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7087 )
AUDIT: Sun Mar 29 10:21:08 2009: 7064 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=7088 )

---

### Post by ozzyprv on 2009-03-30
Bump...I still need help. anybody?

Thanks.

---

### Post by ozzyprv on 2009-03-30
ok, this is really odd.
Keys are back to normal...did not do anything.

---

