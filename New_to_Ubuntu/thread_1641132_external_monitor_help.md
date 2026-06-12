---
title: "external monitor help"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by feedmeh8 on 2010-12-08
Hey guys. Just installed ubuntu 10.10 on Lenovo t61 laptop. Its screen res is 1280x800 and when i connect it to an external monitor with 1024x768, the laptops resolution shrinks to that of the external (1024x768 ). Just wondering if there is a way to keep the laptops native resolution when plugged into the external i have.

I remember this was not a problem in windows 7, so i am hoping there is a solution here :) 

ty!

---

### Post by fatharraxman on 2010-12-08
go to System>Preferences.>Monitor

---

### Post by feedmeh8 on 2010-12-08
thanks for the reply! I have done that though and the thing is that the laptops resolution is no longer an option in the resolution droplist there once the external is connected. But as soon as the external is plugged out its back.

---

### Post by fatharraxman on 2010-12-08
Try xrandr --helpfor command line

---

### Post by feedmeh8 on 2010-12-08
This is the output for that without external connected:
```
$ xrandr --helpfor
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>

```

and this is output with it connected:
```
 $ xrandr --helpfor
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>

```

---

### Post by fatharraxman on 2010-12-08
sorry I thought you want to run it from command 
is this helpfull

---

### Post by fatharraxman on 2010-12-08
try this thread instead [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by feedmeh8 on 2010-12-08
What im trying to do is keep my laptops resolution after connecting it to an external monitor of smaller resolution. I know its possible because in windows 7 both the laptop and the monitor kept their own resolution once they were connected. Whats happening now is that the resolution on my laptop is shrinking to the external's resolution.

Screenshot of Monitor Preferences without external connected:
[IMG]http://img576.imageshack.us/img576/4258/withoutexternalconnecte.png[/IMG]

Screenshot of Monitor Preferences WITH external connected:
[IMG]http://img217.imageshack.us/img217/1469/withexternalconnected.png[/IMG]

EDIT: checked your the thread you linked me it seems like the information there is on how to change screen resolution. What im trying to do is just keep the one i already have once I connect to the external. Without it shrinking down to the resolution of the external monitor. After I connect the external monitor to my laptop, I want my laptops native resolution to remain the same, and the external monitor's native resolution to remain the same. 

Thanks for the help so far! :)

---

### Post by sandyd on 2010-12-08
> **feedmeh8 said:**
> What im trying to do is keep my laptops resolution after connecting it to an external monitor of smaller resolution. I know its possible because in windows 7 both the laptop and the monitor kept their own resolution once they were connected. Whats happening now is that the resolution on my laptop is shrinking to the external's resolution.

Screenshot of Monitor Preferences without external connected:
[IMG]http://img576.imageshack.us/img576/4258/withoutexternalconnecte.png[/IMG]

Screenshot of Monitor Preferences WITH external connected:
[IMG]http://img217.imageshack.us/img217/1469/withexternalconnected.png[/IMG]

EDIT: checked your the thread you linked me it seems like the information there is on how to change screen resolution. What im trying to do is just keep the one i already have once I connect to the external. Without it shrinking down to the resolution of the external monitor. After I connect the external monitor to my laptop, I want my laptops native resolution to remain the same, and the external monitor's native resolution to remain the same. 

Thanks for the help so far! :)
Try this...
Press Ctrl + ALT + F1

login.

type this in.
```

sudo killall gdm
sudo killall kdm
sudo X -configure
sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
gdm

```*note, save your work first.

then post output of 
```

cat /etc/X11/xorg.conf
```

---

### Post by feedmeh8 on 2010-12-08
thanks for the reply. output Im getting after that is "No such file or Directory" I have noticed that if i uncheck "Same image in all monitors" in the monitor settings once the external is connected, then they both return to their native resolutions. But what I want is to duplicate the displays for presenting video files, without having the resolution on the laptop shrink :/

thanks in advance for any more help! :)

---

### Post by Jakey_TheSnake on 2010-12-08
If you uncheck the "Mirror Screens" checkbox you can assign each monitor a resolution separately. 

Unless you needed them to mirror?

edit: missed your last post on the previous page, you could always just pull VLC/your media player of choice over onto the external and fullscreen it, it doesn't have to be mirror image'd? A less technical solution I know, but I haven't had to tamper with xorg in years and I can't remember the darnedest thing.

---

### Post by sandyd on 2010-12-08
oops.
typo.
accidentally added a period....
fixed.

---

### Post by feedmeh8 on 2010-12-09
Thanks for the help so far guys! But I need the video file to play on both monitors at the same time, on their own native resolutions. It would give me chronic sadface to have to go back to windows just because of this one problem, but I need to use this feature on a daily basis.

EDIT: starting to think maybe if I virtualbox windows7 and run the video file in it, maybe it would work?

---

