---
title: "Karmic does no longer recognizes joystick?"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by confused_person on 2010-06-05
I have a DDR mat for PS2 and a PS2-->USB converter that I use for Stepmania. When I first got it, it worked right out of the box. I didn't even need to map the keys for it in Stepmania.

Starting approximately 3 months ago, however, Stepmania stopped recognizing the pad, although I haven't bothered troubleshooting until today. 

I know there's nothing wrong with the DDR mat or the converter because they've worked fine on friends' computers recently. 

I believe this is a Linux problem, not a Stepmania problem, because I ran Joystick using 2 different pads as well as a fully functional PS2 controller and nothing happened when I pressed buttons on any of them. So more specifically it's probably a problem with the USB converter, not the controllers themselves, although like I said, I know the hardware isn't broken because it lights up and it works on friends' computers. (I'm not sure if it's important, but the converter is an EMS Dual Shooter.)

I don't understand why Karmic has stopped recognizing my converter for seemingly no reason. Could an update be to blame? I'm at a complete loss and I don't know how to fix this. Any input would be greatly appreciated. Thanks! :)

EDIT: Wow, is there a way to change the title of a thread? Ultimate grammar fail. I have no idea what I was thinking. o_o

---

### Post by marshmallow1304 on 2010-06-05
Plug in one joystick/gamepad. Open a terminal (Applications->Accessories->Terminal) and run
```
cat /dev/input/js0
```

Move the joystick around and press a few buttons.  If you see a bunch of gibberish in the terminal window, the joystick is recognized.

---

### Post by confused_person on 2010-06-05
> **marshmallow1304 said:**
> Plug in one joystick/gamepad. Open a terminal (Applications->Accessories->Terminal) and run
```
cat /dev/input/js0
```Move the joystick around and press a few buttons.  If you see a bunch of gibberish in the terminal window, the joystick is recognized.

Some random characters popped up immediately after I entered the command, but nothing new happened after I pressed buttons.

---

### Post by greenpanner on 2010-06-06
I am a noob and saw this thread and I have the problem with jscalibrator not being found with install command. 

"sudo apt-get install joystick" worked but not "jscalibrator". if joystick is the test script then how do I set the controller up?

" chmod 666 /dev/input/js0 " show the usb joystick is recognized but I need to test it further and calibrate it.

Does any body know the steps to take for getting my usb game pad calibrated?

NOTE: I don't expect it to actually work perfectly because the controller is more complex than most but I just want to see what it will do, at least...

---

