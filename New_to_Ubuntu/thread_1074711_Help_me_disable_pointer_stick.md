---
title: "Help me disable pointer stick"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by concerto on 2009-02-19
My pointer stick on my keyboard is broken and I can't stop the mouse cursor from moving to the corner of the screen.  how do I disable this?


thank you

---

### Post by concerto on 2009-02-19
I guess the correct name for pointer stick is touch stick.

I hope this helps

---

### Post by era86 on 2009-02-19
What kind of computer is it?  You may be able to disable it messing with xorg.conf (although this is very dangerous, so back it up!):

sudo gedit /etc/X11/xorg.conf

This is the section in my xorg.conf that configures my trackpoint

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "false"
Option "EmulateWheel" "on"
Option "EmulateWheelButton" "2"
Option "EmulateWheelTimeOut" "1" # gets rid of the annoying middle button paste
Option "EmulateWheelInertia" "20"
EndSection

You may be able to disable it by commenting it out.  Someone should verify this first.  Remember, back up this file!

---

### Post by concerto on 2009-02-19
Thanks for the input era86.  ?Does anyone know if this would work?

I will take all the help I can get.

It's an old Dell 8500 inspiron Pentium 4.

---

### Post by Gramps on 2009-02-19
My old Dell Latitude did the samething. I searched for over a year and a half to find a fix and finally I did.

What I did was removed the keyboard which on my laptop was done by removing the screws on the bottom marked K lifted the keyboard and unplugged the joystick. The directions I had said to cut the wires but it was much easier to just unplug it. Now the touch pad or external mouse works just fine.

You may have to do a search to fid out how to removed the keyboard on your Dell I know it is different for my Dell D620

---

### Post by concerto on 2009-02-19
Thats as good as solved to me Gramps!!!  I'll work on downloading diagrams now.

---

### Post by concerto on 2009-02-20
It worked!  I cut the cord and the Problem is solved!

Thanks everyone!


"THREAD SOLVED"

---

