---
title: "Dual Monitors"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by SwiftDestiny on 2010-02-27
Hey,

I'm trying to become a Linux user for work and leave my Window's partition solely for games, after enjoying using it so much in my University.

What I'm struggling with now is I have 2 monitors, and if I use the NVidia control panel to set TwinView all works great but on next boot it's back to one monitor again :(

I tried pressing "Save to X configuration file" but it just tells me it "Failed to parse /x11/....".

Any suggestions?

For reference I have dual NVidia GTX 275's, but both monitors are plugged into the first card so it can be set as a SLi focus card as this rig is used for a lot of gaming.

My primary monitor is a BenQ G2222HDL (1920*1080) and my secondary monitor is a BenQ G2220HD (1920*1080).

---

### Post by alexandari on 2010-02-27
are you opening the NVidia control panel via **sudo**? I've had trouble with saving the settings because of that.

---

### Post by SwiftDestiny on 2010-02-27
Kinda just using the menu at the top of gnome.

What's the terminal command for the nvidia control panel so I can invoke it as sudo?

Cheers

---

### Post by alexandari on 2010-02-27
try **sudo nvidia-settings** 

I think that was the command,sorry if I'm mistaking I'm using ATI at the moment...

---

### Post by SwiftDestiny on 2010-02-27
Thanks a lot pal! Sounds like just what I was looking for.

I'm in my Windows part at the mo downloading Steam games while my flat mate's asleep and doesnt want the internet so have to test it later :)
:KS

---

### Post by alexandari on 2010-02-27
I hope everything goes well! 
Cheers

---

### Post by Bartender on 2010-02-27
I've got 

```
gksudo nvidia-settings
```

in my notes.  That should take you to the same Nvidia GUI that you saw before, but when you ask it to save changes, the changes should actually be saved.

---

### Post by hyperdude111 on 2010-02-27
Actually I used to have the same problem, sudo and gksu didn't fix it. I managed to get it to work by looking going parse then choosing to look at a preview of the x file.

Then copy the contents of that file

Then open nautilus as root with "gksu nautilus"

Then go etc/X11/ and look for xorg.conf paste and ovewrite the contents into xorg. 

If you have no xorg.conf create one with a blank text file.

---

### Post by themusicalduck on 2010-02-27
Also, only if when you run it with the sudo command, you still get an error. Then try running this command in a terminal ```
sudo nvidia-xconfig
``` then reboot, then try again.

---

### Post by xpod on 2010-02-27
I use Dual screens myself with an Nvidia card and have always had the same issues trying to set twinview via the Nvida-settings utility.

Instead, i still just put the twinview entry in manually. You can do this by using either the Terminal or ALT-F2 to open up the minimal xorg.conf you should have like so....

```
gksudo gedit /etc/X11/xorg.conf
```

Enter your password and when the file opens locate the Screen section and put the twinview option in there something like this.
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        **Option          "twinview"**
	DefaultDepth	24
EndSection
```

Save and then log out and back in.

---

### Post by Vegar on 2010-02-27
Hello, this just fixed my problem aswell. But, I'd really like to flip one of my screens 90 degrees and still use twinview, you think it's possible?

---

### Post by xpod on 2010-02-27
> **Vegar said:**
> Hello, this just fixed my problem aswell. But, I'd really like to flip one of my screens 90 degrees and still use twinview, you think it's possible?

Not with twinview it wont be i dont think. There is a rotation option in the Nvidia-Settings manager but that will just rotate both screens with twinview enabled.
You`ll need to use separate X screens with the Xinerama option enabled for that i think. Either that or figure out how to use xrandr for configuring your screens, which is more than i was ever able to do.

EDIT: This is an older guide but it might get you going in the right direction.
[http://www.chrisamiller.com/blog/2008/05/11/rotating-one-monitor-with-ubuntu/](http://www.chrisamiller.com/blog/2008/05/11/rotating-one-monitor-with-ubuntu/)

---

### Post by xpod on 2010-02-28
Ended up having a go myself and as long as you can do without Compiz it`s actually quite easy. 
I have plain old 19" & 22" Belinea VGA screens, with the smaller usually sitting on a slightly higher platform to raise it level with the 22" for twinview.
Setting it vertical though was indeed as simple as using the Nvidia-settings manager to adjust the "X Server Display Configuration". 
Hit the "configure" button to set your screens to "Separate X Screens" and also enable the Xinerama check box. 
You then choose to "Save to X Configuration File" but as someone already mentioned you need to choose the "Show Preview" option and copy that Xorg.conf preview over in place or your original xorg.conf, after backing the original up of course.

Before saving the new xorg.conf find the relevant "Monitor" section and add the rotation settings like so
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Maxdata (RogenTech) B1925S1W"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    [B]Option "RandRRotation" "on"
    Option "Rotate" "CCW"[/B]
EndSection

```

Save, exit and log out & back in. Change the "CCW" to "CW" for clockwise rather than anticlockwise.
The only issue i had was sticking the rotation options in the wrong monitor section to begin with.


Right....back to twinview now. :p

---

### Post by SwiftDestiny on 2010-03-01
Oh wow!

I was just about to reply saying sudo didnt help and there's loads more answers here waiting for me :)

Cheers people, I'll work through the new replies and scream if I'm still stuck :P

---

### Post by SwiftDestiny on 2010-03-01
Okay! I'm getting there but no quite.

I changed my X11 as you said and added the twin view line, but when I booted my right display was my primary one, and when I moved my mouse of the right of my right screen it reappeard on my left, if that makes sense :P

I couldn't put it right with Nvidia so I removed the line to make it go back to how I want.

This is a copy of my X11 if you could possibly help:
```


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```Shouldn't I be seeing 2 monitors?

"VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen"."

Is the error that the nvidia-settings throws at me

---

### Post by thecook57 on 2010-03-01
Hi All,

I'm a newby on Ubuntu, I have a triple monitor display. All monitors are the same Samsung Synchmaster 19".

For now I only have 1 monitor functionning? I've read many threads and tried their solutions, but it still doesn't work.. Humm I have two Nvidia cards on my computer (twin head each)

Any help to get this thing working is much appriciated. 

Don't dispair, i'm a fast learner.

Thanks for your help


Here is the X server file :

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: unknown, VertRefresh source: unknown
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       0.0 - 0.0
    VertRefresh     0.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: unknown, VertRefresh source: unknown
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       0.0 - 0.0
    VertRefresh     0.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GTS"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GTS"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by SwiftDestiny on 2010-03-01
Have you tried what was said at the start of the post, where you add option "TwinView" manually to the X file.

That said though I haven't got the foggiest how it will interact with 3 :P

---

