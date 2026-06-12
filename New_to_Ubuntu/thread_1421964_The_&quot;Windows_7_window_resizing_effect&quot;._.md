---
title: "The &quot;Windows 7 window resizing effect&quot;. Is it possible with Compiz?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by asuastrophysics on 2010-03-04
First of all, let me stress to all Ubuntu and linux lovers that I'm not particularly fond of Window$, or Micro****. 

But, that being said, I bought a new laptop with Windows 7 pre-installed on it. When you drag a window to the left or right border of the screen, it automatically resizes to take up exactly half of the screen.

This way, you can easily view 2 windows side-by-side.

Like I said, I really don't like window$, or care for all the vulnerabilities, viruses, trojans, worms, spyware, adware and registry errors that come with it. 

However, this auto window resizing feature rocks! :D
Is there any way to enable such a feature in compiz?

---

### Post by Seq on 2010-03-04
I can't add to the compiz discussion, but when I was trying KDE SC 4.4 I noticed KWin does this.

---

### Post by l-x-l on 2010-03-05
Yes there is a way if you have compiz-fusion & compiz-config setting manager.

Here you go: _[Aero Snap in Linux]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html")_

---

### Post by asuastrophysics on 2010-03-05
> **l-x-l said:**
> Yes there is a way if you have compiz-fusion & compiz-config setting manager.

Here you go: _[Aero Snap in Linux]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html")_

awesome man, thanks! ;)

---

### Post by auh2o on 2010-03-05
Thanks for the info.

This of course conflicts with the* Edge Flip Move* option in the Rotate Cube plugin, inasmuch as that you can't then drag windows off-screen to the next desktop. There's always a trade-off. Assigning the Rotate Flip Left & Right bindings as TopLeft & TopRight might be acceptable.

---

### Post by myolbug on 2010-03-05
> **auh2o said:**
> Thanks for the info.

This of course conflicts with the* Edge Flip Move* option in the Rotate Cube plugin, inasmuch as that you can't then drag windows off-screen to the next desktop. There's always a trade-off. Assigning the Rotate Flip Left & Right bindings as TopLeft & TopRight might be acceptable.

Any idea on how to do this?  Because if I can have the best of both worlds, that would be great!  Regardless, this is cool trick! Ahh, never mind, can I drag them from workspace to workspace if I click them in the lower right hand *"current workspace?*"

---

### Post by TironN on 2010-03-05
I was just thinking about this recently as I have Windoze installed on a school laptop and really liked that snap.

---

### Post by auh2o on 2010-03-05
> **myolbug said:**
> Any idea on how to do this?  Because if I can have the best of both worlds, that would be great!  Regardless, this is cool trick! Ahh, never mind, can I drag them from workspace to workspace if I click them in the lower right hand *"current workspace?*"

If you go into the Rotate Cube settings, click on the Bindings tab, and under the Rotate Cube drop-down menu set "Rotate Flip Right" and "Rotate Flip Left" to TopRight and TopLeft respectively (or BottomRight/Left if that suits you better), you can still retain the best of both worlds. That is, if you can live with having to drag the windows in somewhat of a zig-zag fashion to move them between workspaces.

---

### Post by myolbug on 2010-04-12
Hey, thanks for this!  It works great.  I used to use Ubuntu Remix on my laptop and I couldn't use Compiz at all.  Now, I have Linux Mint 8 and I have full use of it again.

---

### Post by myolbug on 2010-07-08
Something cool that I added on is Fox Tabs in Firefox.  Seems to fit the Compiz theme!

[http://www.foxtab.com/](http://www.foxtab.com/)

---

### Post by AncientPC on 2010-09-25
> **l-x-l said:**
> Yes there is a way if you have compiz-fusion & compiz-config setting manager.

Here you go: _[Aero Snap in Linux]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html")_

Here is the updated link: [http://www.omgubuntu.co.uk/2009/11/get-aero-snap-in-ubuntu/](http://www.omgubuntu.co.uk/2009/11/get-aero-snap-in-ubuntu/)

---

### Post by TrinitronX on 2011-01-14
Edit: I've created a blog post about this...

[http://lyraphase.com/wp/projects/aero-snap-in-linux/](http://lyraphase.com/wp/projects/aero-snap-in-linux/)

I've created a script based off of this to simplify the commands to put into compiz.  It has the added benefit of working on the current command line console as well.

 How to use:

Use -l for left, -r for right, -m for maximized, and -d for a "default" sized window.  The default window geometry is configurable as a variable (WIN_DEFAULTGEOM).  If the variable is set at runtime, it will override the hardcoded value in the script.  You can use this to create however many default window sizes you need if you set them in multiple commands in compiz.   See the manpage for wmctrl for the format to specify window geometry arguments. (This is called <MVARG> in the manpage).  If you're wondering why I chose such a weird default value... it cooresponds to an 80x26 line terminal window on my resolution.

Examples:

aero-resize -l    # Snap left
aero-resize -r   # Snap right
aero-resize -m  # Maximize
aero-resize -d   # Default size (as hardcoded in script)
# You may also use whatever geometry you wish like so:
WIN_DEFAULTGEOM=0,20,80,800,600 aero-resize -d


[LIST=1]
[*]Save as "aero-resize" someplace in your PATH (I put mine in ~/bin)
[*]chmod +x aero-resize
[*]Add the commands you wish to your compiz command config, or simply use it in a terminal window to resize it.
[/LIST]


```

#!/bin/bash
# Script to emulate the Aero window-snap feature in Windows 7
#  Use the -l or -r options to tell which side to snap to
#  Use the -d flag to reset the window state to default
#
# Default window geometry to use with -d
#        Format: g,x,y,w,h
# (see <MVARG> in the man page for wmctrl for more details)
# set only if not set
: ${WIN_DEFAULTGEOM:="0,10,60,826,556"}

function usage
{
  echo ""
  echo "Usage: aero-resize [-l | -r | -m | -d]"
  echo "  -l    resize to fill left side of screen"
  echo "  -r    resize to fill right side of screen"
  echo "  -m    maximize window"
  echo "  -d    resize to default geometry"
  echo ""
  echo "Current default geometry is: $WIN_DEFAULTGEOM"
}

while getopts ":lrmd" opt; do
    case $opt in
        l)
            # Reset props (if maximized to begin with)
            wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz

            # LEFT
            WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'`
            HALF=$((($WIDTH/2)-10))
            wmctrl -r :ACTIVE: -b add,maximized_vert
            wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1 
            ;;
        r)
            # Reset props (if maximized to begin with)
            wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz

            # RIGHT
            WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'`
            HALF=$((($WIDTH/2)-12))
            HALFP=$(($WIDTH/2))
            wmctrl -r :ACTIVE: -b add,maximized_vert
            wmctrl -r :ACTIVE: -e 0,$HALFP,0,$HALF,-1 
            ;;
        m)
            # Maximize
            wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
            ;;
        d)
            # Default window size
            wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz
            wmctrl -r :ACTIVE: -e $WIN_DEFAULTGEOM
            ;;
        \?)
            echo "Invalid option: -$OPTARG" >&2
            DISP_USAGE=1
            ;;
    esac

done

if [[ "$@" == "" || $DISP_USAGE -eq 1 ]]; then
    usage
fi


```

---

