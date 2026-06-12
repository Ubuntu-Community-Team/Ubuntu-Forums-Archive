---
title: "Microsoft wireless mouse 6000"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2010-10-24
I didnt even thing about this when I was buying the mouse.  But I would like to use all the features of the mouse.  The disc has a few .exe's and I right click tried to open with Wine, it says I cant, so I go to permissions and try to set it as an executable, wont let me.  So what do I do next?

---

### Post by jtarin on 2010-10-24
Issue this command in a terminal and post the output. ```
xinput list | grep 'id='
```

---

### Post by DarrenMR415 on 2010-10-24
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; CNF7051                                 	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® Nano Transceiver v2.0	id=13	[slave  keyboard (3)]

---

### Post by jtarin on 2010-10-24
And your using which version of Ubuntu?

---

### Post by DarrenMR415 on 2010-10-24
Sorry I ment to include that in the first post. Its 10.04.

---

### Post by jtarin on 2010-10-24
Exactly what features are you trying to implement that are not available now.

---

### Post by DarrenMR415 on 2010-10-24
It has side buttons I would like to take advantage of, and the scroller wheel does nothing when clicked.

---

### Post by jtarin on 2010-10-24
In the terminal the command```
xinput get-button-map " Microsoft Microsoft® Nano Transceiver v2.0"
```post results

---

### Post by jtarin on 2010-10-24
Is there a way to determine if X11 is responding to mouse events?Yes. 
Issue the command in a terminal
```
xev
```Then Position the cursor over the white window, move mouse and activate buttons, make sure you see MotionNotify events in the xterm where you started "xev" and for what actions..

---

### Post by DarrenMR415 on 2010-10-25
> **jtarin said:**
> In the terminal the command```
xinput get-button-map " Microsoft Microsoft® Nano Transceiver v2.0"
```post results

unable to find device  Microsoft Microsoft® Nano Transceiver v2.0

> **jtarin said:**
> Is there a way to determine if X11 is responding to mouse events?Yes. 
Issue the command in a terminal
```
xev
```Then Position the cursor over the white window, move mouse and activate buttons, make sure you see MotionNotify events in the xterm where you started "xev" and for what actions..

The xev makes a mess of my terminal, but the buttons on the sides of the mouse are moving me back and forward on this page.

---

### Post by DarrenMR415 on 2010-10-25
> **jtarin said:**
> In the terminal the command```
xinput get-button-map " Microsoft Microsoft® Nano Transceiver v2.0"
```post results

Took out the space before microsoft, I just copied what you put the first time.  The response was -

Warning: There are multiple devices named "Microsoft Microsoft® Nano Transceiver v2.0".
To ensure the correct one is selected, please use the device ID instead.

---

### Post by DarrenMR415 on 2010-10-25
bumpity

---

### Post by DarrenMR415 on 2010-10-25
One more bump, anyone know what to do next?

---

### Post by jtarin on 2010-10-25
> **DarrenMR415 said:**
> Took out the space before microsoft, I just copied what you put the first time.  The response was -

Warning: There are multiple devices named "Microsoft Microsoft® Nano Transceiver v2.0".
To ensure the correct one is selected, please use the device ID instead.We're shooting in the dark a little here as your mosue does not show with a known name so will go with the Virtual core pointer and see if we get a map of the buttons. 

Try ```
xinput get-button-map "Virtual core pointer" 
```or ```
xinput get-button-map -device 2
```

---

### Post by DarrenMR415 on 2010-10-25
> **jtarin said:**
> Try ```
xinput get-button-map "Virtual core pointer" 
```or ```
xinput get-button-map -device 2
```

X Error of failed request:  XI_BadDevice (invalid Device parameter)
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Device id in failed request: 0x17
  Serial number of failed request:  16
  Current serial number in output stream:  16




usage: xinput get-button-map <device name>

---

### Post by DarrenMR415 on 2010-10-25
Im trying every combonation of the stuff you gave me trying to get anything to work.

---

### Post by jtarin on 2010-10-25
Let's try ```
xinput list
``` to see if we can get a more definitive list. I'll have to admit wireless hardware is out of my expertise, but it should fall in lines with connected configs.

---

### Post by DarrenMR415 on 2010-10-26
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft® Nano Transceiver v2.0	id=9	[slave  keyboard (3)]
    &#8627; CNF7051                                 	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard




I really appreciate you trying to help, btw.

---

### Post by jtarin on 2010-10-26
> **DarrenMR415 said:**
> X Error of failed request:  XI_BadDevice (invalid Device parameter)
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Device id in failed request: 0x17
  Serial number of failed request:  16
  Current serial number in output stream:  16




usage: xinput get-button-map <device name>
Maybe just:
```
 xinput get-button-map "Virtual core pointer id=2"	
```might try with/without quotation marks.

---

### Post by DarrenMR415 on 2010-10-26
darren@darren-laptop:~$ xinput get-button-map virtual core pointer id=2
usage: xinput get-button-map <device name>
darren@darren-laptop:~$ xinput get-button-map "virtual core pointer id=2"
unable to find device virtual core pointer id=2

---

### Post by jtarin on 2010-10-26
> **DarrenMR415 said:**
> darren@darren-laptop:~$ xinput get-button-map virtual core pointer id=2
usage: xinput get-button-map <device name>
darren@darren-laptop:~$ xinput get-button-map "virtual core pointer id=2"
unable to find device virtual core pointer id=2
```
xinput get-button-map 2
```

---

### Post by DarrenMR415 on 2010-10-27
X Error of failed request:  XI_BadDevice (invalid Device parameter)
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Device id in failed request: 0x17
  Serial number of failed request:  16
  Current serial number in output stream:  16

---

### Post by jtarin on 2010-10-27
Mine:$ ```
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; [COLOR="DarkRed"]ImPS/2 Logitech Wheel Mouse             	id=9	[slave [/COLOR] pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=8	[slave  keyboard (3)]
```
```
xinput get-button-map 9
1 2 3 4 5 6 7
```

All I can say is try the other device ID's under pointer.

---

### Post by DarrenMR415 on 2010-10-30
Bumping this incase anyone else has any idea.  jtarian I really appreciate all your help.

---

