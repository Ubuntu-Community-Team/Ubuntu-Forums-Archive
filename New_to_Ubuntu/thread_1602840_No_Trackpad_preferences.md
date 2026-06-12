---
title: "No Trackpad preferences?"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by toomanymatts on 2010-10-21
Hi all

So I am trying to reduce the sensitivity of the trackpad on my new Dell Vostro v13 running 10.10, and...it's not there.

No tab under the mouse preferences.

I looked that up and found this:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

...which offers the following advice:

> To check if a touchpad has been detected open a [terminal]("https://help.ubuntu.com/community/UsingTheTerminal") and check the input device list given by this command: 
```
xinput list
```If one of the lines mentions a touchpad (perhaps also "Synaptics" or "ALPS"), your touchpad has been detected. 

If  one of the lines mentions an "ADB mouse", then your touchpad is old.  Use the trackpad command line tool to configure it. Here's an example to  switch on tapping and dragging: 

```
sudo trackpad show
sudo trackpad tap
sudo trackpad drag
```so...into terminal I go....xinput list reveals:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HID 413c:8161                               id=10    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_1.3M               id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```No Trackpad, nor ADB Mouse...hmmmmmmm

Anyhow, forge on and try the sudo trackpad options anyhow, and get this:

```
sudo: trackpad: command not found
```Any thoughts on how I can access these commands?  It's sensitivity is driving me crazy.

Matt

---

### Post by Chesamo on 2010-10-22
```
sudo apt-get install gpointing-device-settings
```

---

### Post by toomanymatts on 2010-10-24
thanks, did that....

So nothing has appeared under Mouse Preferences now, but I do have a G-Pointing device that will allow me to edit preferences for a PS2 Mouse, but still no trackpad :(

---

### Post by toomanymatts on 2010-10-26
shameless bump

---

### Post by chrismarx on 2011-07-29
i have the same problem, get the same output, any ideas for this?

---

