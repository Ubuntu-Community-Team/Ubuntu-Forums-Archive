---
title: "How can I force a resolution?"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by TunaMloohnah on 2011-08-07
Hey, guys.  Ubuntu won't let me set my resolution past 1360x768, even though in windows I can get it to 1680x800.  How can I force it? I've tried messing with xorg, but my file is totally blank.

---

### Post by realzippy on 2011-08-07
It depends on the hardware and graphics driver you use.
Also we should know your Ubuntu version...

---

### Post by TunaMloohnah on 2011-08-07
I'm on 10.10, with an ATI Radeon XPress 1150

---

### Post by realzippy on 2011-08-07
Open a terminal,type

```
xrandr -q
```

and post ouput

---

### Post by TunaMloohnah on 2011-08-07
creen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
   1440x900_60.00   59.9

---

### Post by realzippy on 2011-08-07
So which resolution is your monitors native ?
(we try to add your desired to that list..)

---

### Post by TunaMloohnah on 2011-08-07
It's a thirty two inch TV, technically, but in windows, I use it at 1440x900 although I know it can go to 1680x1080 (preferable res :3)

---

### Post by realzippy on 2011-08-07
You get the best picture if you use your panel's native resolution.
This can be different on 32" screens,so which vendor/model is it exactly?

---

### Post by TunaMloohnah on 2011-08-07
It's a Dynex dx 32l151a11.

---

### Post by realzippy on 2011-08-07
[I]The DX-32L151A11 is a 32-inch 720-p HDTV from Dynex, which is Best Buy's in-house electronics brand. With a 16:9 aspect ratio and **native resolution of 1366 x 768**, ......
[/I]
So you want
1366x768 (best picture quality) instead of
1360x768 or you want to test something bigger?

---

### Post by TunaMloohnah on 2011-08-07
On windows 7, I can set it at 1440x900 and it's awesome, and on XP I can even set it o 1680x1080.  I'd like to set it to something higher.

---

### Post by realzippy on 2011-08-07
run these 3 commands:

```
xrandr --newmode  1440x900_60.00   106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
```

```
xrandr --addmode VGA-0  1440x900_60.00
``` 

```
xrandr --output VGA-0 --mode 1440x900_60.00
```

Does it work?If so,do not log out.

---

### Post by TunaMloohnah on 2011-08-07
brodie@ubuntu:~$ xrandr --newmode  1440x900_60.00   106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  25
  Current serial number in output stream:  25
brodie@ubuntu:~$ xrandr --addmode VGA-0  1440x900_60
xrandr: cannot find mode "1440x900_60"
brodie@ubuntu:~$ xrandr --output VGA-0 --mode 1440x900_60
xrandr: cannot find mode 1440x900_60


No dice.

---

### Post by realzippy on 2011-08-07
Bad,
But show 
```
xrandr -q
```
again,,,

---

### Post by TunaMloohnah on 2011-08-07
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
   1440x900_60.00   59.9

---

### Post by realzippy on 2011-08-07
Have you formerly run xrandr commands?

---

### Post by TunaMloohnah on 2011-08-07
Yeah, they didn't work.

---

### Post by realzippy on 2011-08-07
Not exactly.
You seem to have added to your Laptop's panel (LVDS1)
1440x900_60.00 59.9
.........................................................
Please run
```
rm ~/.config/monitors.xml
```

Reboot or restart Xserver.
Then again show output from
```
xrandr -q
```

---

### Post by TunaMloohnah on 2011-08-07
Here you go mate.


Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4

---

### Post by realzippy on 2011-08-07
Now again post #12 :)

---

### Post by TunaMloohnah on 2011-08-07
Darn.


brodie@ubuntu:~$ xrandr --newmode  1440x900_60.00   106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
brodie@ubuntu:~$ xrandr --addmode VGA-0  1440x900_60
xrandr: cannot find mode "1440x900_60"
brodie@ubuntu:~$ xrandr --output VGA-0 --mode 1440x900_60
xrandr: cannot find mode 1440x900_60

---

### Post by realzippy on 2011-08-07
??
again xrandr -q please...

---

### Post by TunaMloohnah on 2011-08-07
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
  1440x900_60.00 (0x12a)  106.5MHz
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz

---

### Post by catlover2 on 2011-08-07
Hi, I just noticed that there has been no mention of whether the proprietary drivers are in use or not?

---

### Post by TunaMloohnah on 2011-08-07
How could I help you with that?

---

### Post by realzippy on 2011-08-07
> **catlover2 said:**
> Hi, I just noticed that there has been no mention of whether the proprietary drivers are in use or not?

There are no proprietary drivers for ati xpress...

---

### Post by catlover2 on 2011-08-07
ah, I see

---

### Post by TunaMloohnah on 2011-08-07
What now? :)

---

### Post by realzippy on 2011-08-07
> **TunaMloohnah said:**
> Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
[COLOR="SeaGreen"]  1440x900_60.00 (0x12a)  106.5MHz
        h: width  1440 start 1528 end 1672 total 1904 skew    0 clock   55.9KHz
        v: height  900 start  903 end  909 total  934           clock   59.9Hz[/COLOR]

The mode is there,don 't understand why "adding" not seems to work.
Again,because I cannot believe:
```
xrandr --addmode VGA-0 1440x900_60.00
```

---

### Post by TunaMloohnah on 2011-08-07
First command, unable to find, yadda yadda.

But when I did the quotes, I got this big list: 

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

---

### Post by realzippy on 2011-08-07
Try again the 2nd.I mistyped it,corrected it,but maybe you where faster..

```
xrandr --addmode VGA-0 "1440x900_60"
```

---

### Post by TunaMloohnah on 2011-08-07
xrandr: cannot find mode "1440x900_60"

---

### Post by realzippy on 2011-08-07
try
```
xrandr --addmode VGA-0 1440x900_60.00
```

---

### Post by TunaMloohnah on 2011-08-07
It....worked... but how? What'd you do?

---

### Post by realzippy on 2011-08-07
I was an idiot.
Real sorry.
Now run:
```
xrandr --output VGA-0 --mode 1440x900_60.00
```
If it works,do not log out...

---

### Post by TunaMloohnah on 2011-08-07
Still at 1440x900
It's the same :)

---

### Post by realzippy on 2011-08-07
You mean it worked before running:
```
xrandr --output VGA-0 --mode 1440x900_60.00
```
and you have your desired resolution?

If so,fine,but we had to make it permanent,since xrandr is only for current session.

---

### Post by realzippy on 2011-08-07
> **TunaMloohnah said:**
> Still at 1440x900
It's the same :)

or did you wanted to say:
Still at 1360x768 ?

---

### Post by TunaMloohnah on 2011-08-07
It's at 1440x900, yes, but how would I make it permanant?

---

### Post by realzippy on 2011-08-07
Run:

```
gksudo gedit /etc/gdm/Init/Default
```

.
Watch out for

```
PATH=”/usr/bin:$PATH”
OLD_IFS=$IFS
```

and paste in your 3 working xrandr:

xrandr --newmode  1440x900_60.00   106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA-0  1440x900_60.00
xrandr --output VGA-0 --mode 1440x900_60.00

so it looks like:

```
.............
PATH="/usr/bin:$PATH"
OLD_IFS=$IFS

xrandr --newmode  1440x900_60.00   106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode VGA-0  1440x900_60.00
xrandr --output VGA-0 --mode 1440x900_60.00

#if [ -x '/usr/bin/xsplash' ];
#then
#        /usr/bin/xsplash --gdm-session --daemon
#fi

/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm
...........

```
close file saving changes.Reboot or restart Xserver fingers crossed...

---

### Post by TunaMloohnah on 2011-08-07
It didn't save :\

---

### Post by realzippy on 2011-08-07
What didn 't save?
The file you edited?
Or did it not work after reboot?
If so,show the file please..

---

### Post by madjr on 2011-08-07
the info given here by @realzippy is awesome, i had this issue before and i think these also might help:

[http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/](http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/)

[http://askubuntu.com/questions/21192/screen-resolution-higher-than-monitor-specs](http://askubuntu.com/questions/21192/screen-resolution-higher-than-monitor-specs)

---

### Post by realzippy on 2011-08-07
> **madjr said:**
> the info given here by @realzippy is awesome, i had this issue before and i think these also might help:

[http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/](http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/)

[http://askubuntu.com/questions/21192/screen-resolution-higher-than-monitor-specs](http://askubuntu.com/questions/21192/screen-resolution-higher-than-monitor-specs)

Interesting.Never heard about it,might be worth a shot..

---

### Post by TunaMloohnah on 2011-08-07
The file saved fine, but the resolution wasn't there after reboot.  I entered all of the terminal commands again and it was back up to 1440x900.

```
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH="/usr/bin:$PATH"
OLD_IFS=$IFS


randr --newmode 1440x900_60.00 106.50 1440 1528 1672 1904 900 903 909 934 -hsync +vsync
xrandr --addmode VGA-0 1440x900_60.00
xrandr --output VGA-0 --mode 1440x900_60.00


#if [ -x '/usr/bin/xsplash' ];
#then
#        /usr/bin/xsplash --gdm-session --daemon
#fi

/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=gdm

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS
  echo "$OUTPUT"
}

sysresources=/etc/X11/Xresources

# merge in defaults
if [ -f "$sysresources" ]; then
    xrdb -merge "$sysresources"
fi

sysmodmap=/etc/X11/Xmodmap

XMODMAP=`gdmwhich xmodmap`
if [ "x$XMODMAP" != "x" ] ; then
  if [ "x$GDM_PARENT_DISPLAY" = "x" ]; then
    if [ -f $sysmodmap ]; then
      $XMODMAP $sysmodmap
    fi
  else
    ( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $XMODMAP -pke ) | $XMODMAP -
  fi

  #
  # Switch Sun's Alt and Meta mod mappings
  #

  UNAME=`gdmwhich uname`
  PROCESSOR=`$UNAME -p`
  if [ "x$PROCESSOR" = "xsparc" ]; then
    if $XMODMAP | /usr/bin/grep mod4 | /usr/bin/grep Alt > /dev/null 2>/dev/null
    then
      $XMODMAP -e "clear Mod1" \
               -e "clear Mod4" \
               -e "add Mod1 = Alt_L" \
               -e "add Mod1 = Alt_R" \
               -e "add Mod4 = Meta_L" \
               -e "add Mod4 = Meta_R"
    fi
  fi
fi

SETXKBMAP=`gdmwhich setxkbmap`
if [ "x$SETXKBMAP" != "x" ] ; then
  # FIXME: is this all right?  Is this completely on crack?
  # What this does is move the xkb configuration from the GDM_PARENT_DISPLAY
  # FIXME: This should be done in code.  Or there must be an easier way ...
  if [ -n "$GDM_PARENT_DISPLAY" ]; then
    XKBSETUP=`( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $SETXKBMAP -v )`
    if [ -n "$XKBSETUP" ]; then
      XKBKEYMAP=`echo "$XKBSETUP" | grep '^keymap' | awk '{ print $2 }'`
      XKBTYPES=`echo "$XKBSETUP" | grep '^types' | awk '{ print $2 }'`
      XKBCOMPAT=`echo "$XKBSETUP" | grep '^compat' | awk '{ print $2 }'`
      XKBSYMBOLS=`echo "$XKBSETUP" | grep '^symbols' | awk '{ print $2 }'`
      XKBGEOMETRY=`echo "$XKBSETUP" | grep '^geometry' | awk '{ print $2 }'`
      if [ -n "$XKBKEYMAP" ]; then
        $SETXKBMAP -keymap "$XKBKEYMAP"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" -a -n "$XKBGEOMETRY" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS" -geometry "$XKBGEOMETRY"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS"
      elif [ -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -symbols "$XKBSYMBOLS"
      fi
    fi
  fi
fi

exit 0
```

---

### Post by realzippy on 2011-08-07
you forgot the x at the first command...
it is xrandr,not randr

---

### Post by realzippy on 2011-08-07
> **madjr said:**
> the info given here by @realzippy is awesome, i had this issue before and i think these also might help:

[http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/](http://www.omgubuntu.co.uk/2010/11/set-your-screen-resolution-higher-than-you-should-with-newrez/)

[http://askubuntu.com/questions/21192/screen-resolution-higher-than-monitor-specs](http://askubuntu.com/questions/21192/screen-resolution-higher-than-monitor-specs)


It does not seem to work on intel i915driver.
It also can't set valid (smaller) resolutions.
But nice idea.

---

### Post by TunaMloohnah on 2011-08-07
> **realzippy said:**
> you forgot the x at the first command...
it is xrandr,not randr

HERPDERP

Holy gosh you are the coolest guy.  It works.

---

### Post by realzippy on 2011-08-07
Glad you made it,sorry for the not-instantly-working-addmode-command,but
I made a typo in post #12:
created a mod xxxxxxxxxxxxxxxxxxxxx _60.00
and called xxxxxxxxxxxxxxxxxxxx _60
This cannot work (of course).....it is not easy to concentrate on typing when a hungry cat walks across the keyboard demanding food..meanwhile I fed her  :-)
Have fun and set thread as solved please (threadtools).

---

