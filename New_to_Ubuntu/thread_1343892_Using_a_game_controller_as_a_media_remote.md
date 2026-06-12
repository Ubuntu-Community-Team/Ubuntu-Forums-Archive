---
title: "Using a game controller as a media remote"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by ethanmadden on 2009-12-02
I have been using ubuntu (currently 9.1 karmic) for probably around 6 months now, so I guess I'm not really an absolute beginner, but oh well. Onto the question.

I have a usb game controller (Saitek Cyborg v.3 Rumble Pad) and I was wondering if there was a way to configure it so that pressing a button on the controller ran a command on the computer.

I want to eventually be able to use it to control my music without having to open my laptop. (R1 for volume up, L1 for volume down, up for play, down for pause, I think you all get the idea)

The problem is that I have no idea where to start. I googled any terms that I thought even came close to describing what I wanted and I couldn't find anything. I tried just setting them up as keyboard shortcuts, but the menu didn't recognize the controller. So now I am stuck. I don't want to give up on it, because I think it can be done, but I have no clue where to start.

Any help would be greatly appreciated. If you need any more info just ask.

---

### Post by Clopin on 2009-12-02
When I was messing with the PS3 controller for Linux gaming, I used QJoyPad. I suggest you looking at it:
[http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/)
What it does is *"...QJoyPad takes input from a gamepad or joystick and translates it into key strokes or mouse actions, letting you control any XWindows program with your game controller."*

---

### Post by Maheriano on 2009-12-02
I use my Wiimote as a remote control for my home theater. I point it at the screen where I want the mouse and I mapped left click to the A button and right click to the trigger (B) button. I'm also running BlueProximity so they automatically pair when I turn it on and then I turn it off to save the batteries when not in use.

There might be something similar for your gamepad if it's bluetooth based, but I doubt it for any type of USB controller.

---

### Post by ethanmadden on 2009-12-02
> **Clopin said:**
> When I was messing with the PS3 controller for Linux gaming, I used QJoyPad. I suggest you looking at it:
[http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/)
What it does is *"...QJoyPad takes input from a gamepad or joystick and translates it into key strokes or mouse actions, letting you control any XWindows program with your game controller."*

That looks like it might work. I will work at installing it and report back here whether or not it worked.

---

### Post by ethanmadden on 2009-12-05
Alright, I have been attempting this for the last few days, and I can't get QJoyPad to compile.

I also tried a program called joy2key, but when I try to run it I get the following error message: "Error opening /dev/js0!
Are you sure you have joystick support in your kernel?"
I have used the controller for games, so I know it works. I assume it is saving it as a different device, but I don't know what, and I don't konw how to tell joy2key to look at that file instead of /dev/js0.

Any help compiling QJoyPad or setting up joy2key would be greatly appreciated.

---

### Post by ethanmadden on 2009-12-05
Bumpity bump bump. 

If I could get either of these programs to work I would be all set.

---

### Post by gtanghookup on 2009-12-20
*"I have used the controller for games, so I know it works. I assume it is saving it as a different device, but I don't know what, and I don't konw how to tell joy2key to look at that file instead of /dev/js0."*

try using:

*joy2key -dev /dev/input/js0 ...*


The -dev flag specifies which device joy2key should use and I believe that if you're running Ubuntu, your first joystick/gamepad should be located at '/dev/input/js0' not '/dev/js0' (this is true for me running Debian).

A good way to confirm that this is your joystick's device file is to open a terminal, and type:
*cat /dev/<path to joystick>*
(i.e. *'cat /dev/input/js0'*)

then start pressing buttons; you should see a bunch of characters appear in the terminal each time you press a button or move a control axis.

What I have done in the past is to search in the /dev directory until I found a possible match, in my case /dev/input/js0. I then did the above 'cat' command and saw that my joystick was both working and what file it was assigned to. 

Dan

---

### Post by dlzerocool on 2009-12-20
sometimes linux distributions just piss me off...  can't they just make an effort to use a convention and choose between /dev/jsX and /dev/input/jsX 
Or provide tools that do automaticly the links between them. A normal user shouldn't have to do links tricks to get his joypad/stick etc. working.

---

### Post by ethanmadden on 2009-12-20
> **gtanghookup said:**
> 
try using:

*joy2key -dev /dev/input/js0 ...*


Hey thanks! I thought this was dead, but I think that this may have been what I needed to get it going! I am checking out the man page, but I am still figuring out most of the syntax by guess-n-check. If you want to give me any tips on setting buttons and axes it would be greatly appreciated!

Edit: Ok, I just keep getting "Must specify a target first!" Any ideas?

---

### Post by Halverneus on 2010-01-24
I just barely hooked up my game controller (actually, my wife's old game controller) using joy2key as follows:
installed joy2key
created file under /home/user/   called .joy2keyrc

inputted following:

COMMON
-X
-dev /dev/input/js0
-thresh -16000 16000 -16000 16000 -16000 16000 -16000 16000 -16000 16000
-16000 16000 -16000 16000 -16000 16000 -16000 16000 -16000 16000 -16000
16000 -16000 16000 -16000 16000 -16000 16000 -16000 16000 -16000 16000
-16000 16000 -16000 16000 -16000 16000 -16000 16000 -16000 16000 -16000
16000 -16000 16000 -16000 16000 -16000 16000 -16000 16000 -16000 16000
-16000 16000

START uae
-X
-buttons a b c d e f g h i j k l m n o p q r s t u v w x y z
-axis a b c d e f g h i j k l m n o p q r s t u v w x y z


the thresh values are based on 50% of full travel value of the axis (joy2key dev /dev/input/js0 -terminal)

Next, for experimentation, I opened up two terminals: one for receiving characters (gedit or any other program should work just as good) and the other to start joy2key.

in one terminal type:    joy2key -config uae

this will change your cursor to cross hairs. Click on the other terminal (or your program of choice) you can then go through your buttons and axis to figure out each buttons output. You can go back to the .joy2keyrc file and change the "-buttons" and "-axis" values to what you want. (Let me know what you use for media keys if you find out, I'm just figuring this out myself) As I understand it, you can add additional configurations for different programs by adding a new "START somename" line. Hope this helps you out.

---

### Post by ethanmadden on 2010-01-24
> **Halverneus said:**
> 
this will change your cursor to cross hairs. Click on the other terminal (or your program of choice) you can then go through your buttons and axis to figure out each buttons output. You can go back to the .joy2keyrc file and change the "-buttons" and "-axis" values to what you want. (Let me know what you use for media keys if you find out, I'm just figuring this out myself) As I understand it, you can add additional configurations for different programs by adding a new "START somename" line. Hope this helps you out.

Holy crap. I think this is exactly what I wanted. Thanks a ton. As far as media keys go, try going into keyboard shortcuts and seeing what is set up as your volume/pause/play/forward etc shortcuts.
Mine are XF86AudioMute, XF86AudioLowerVolume, XF86AudioRaiseVolume, etc.

Thanks a whole, whole lot for helping me figure this out, and I hope the media keys work for you!

---

