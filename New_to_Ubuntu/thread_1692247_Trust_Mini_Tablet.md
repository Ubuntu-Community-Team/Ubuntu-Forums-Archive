---
title: "Trust Mini Tablet"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by chuning on 2011-02-21
Hello - 

I've just got a Trust Mini Tablet and am trying to set it up on my netbook running Ubuntu 10.10.  I've got Wizardpen etc, and it sort of works, but not very usefully, as the pen will only move the cursor when it is actually touching the tablet, which renders it pretty useless for photoshop/gimp.  Can anyone tell me how I can set it up so it works like my Wacom tablet does on my Windows machine - ie, moving the cursor with the pen just above the tablet?

Many thanks

Chris

---

### Post by Favux on 2011-02-21
Hi chuning,

What does the system see the tablet as?  In other words what does it say in the tablet line in your output of:
```
lsusb
```
in a terminal?

---

### Post by chuning on 2011-02-21
If I've picked out the right bit, it says

UC-Logic Technology Corp. Genius MousePen 4x3 Tablet/Aquila L1 Tablet

---

### Post by Favux on 2011-02-21
Hi Chris,

You are correct, that's a WizardPen tablet.  OK, find the "device name" of your stylus by entering in a terminal:
```
xinput list
```
It'll be similar.  Then find out if it is on the WizardPen driver by entering, with the quotes:
```
xinput list-props "device name"
```
Go ahead and post the output.

---

### Post by chuning on 2011-02-22
Hi - 

Thanks for the reply.

The output from the first is:

chris@chris-netbook:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP4030U                     id=13    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP4030U                     id=14    [slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP4030U                     id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

The second command, it tells me 'unable to find UC-LOGIC Tablet WP4030U

---

### Post by Favux on 2011-02-22
Not quite sure I understand that.  If the stylus is on the failsafe evdev driver I would think it would say that.

It sounds like you need to install the WizardPen driver.  The version in Synaptic Package Manager doesn't work right so use DoctorMo's version in his PPA:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

Depending on your UC-LOGIC Tablet WP4030U model the 70-wizardpen.conf in xorg.conf.d may need some modification too.

---

### Post by chuning on 2011-02-22
I've done that, and it works!

Thanks very much!

Chris

---

### Post by Favux on 2011-02-22
Good.  :)

---

