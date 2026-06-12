---
title: "can't run conky...."
date: 2010-02-23
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-02-23
I installed conky by:
$ sudo aptitude install conky

This appears to have installed correctly.


When I run conky:

$ conky

It keeps telling me this:
windsor@windsor-desktop:/$ conky 
Conky: border_margin is deprecated, please use window.border_inner_margin instead
localhost [127.0.0.1] 7634 (?) : Connection refused
Conky: one or more $endif's are missing
Conky: desktop window (1e000b5) is subwindow of root window (13c)
Conky: window type - override
Conky: drawing to created window (0x5200001)
Conky: drawing to double buffer
sh: sensors: not found
sh: sensors: not found
connect: Connection refused
sh: /home/windsor/.scripts/ip.sh: not found
Conky: Unable to load image '/home/windsor/.scripts/tlo.png'
Conky: Unable to load image '/home/windsor/.scripts/tlo.png'
Conky: Unable to load image '/home/windsor/.scripts/tlo.png'
sh: /home/windsor/.scripts/ip.sh: not found
Conky: Unable to load image '/home/windsor/.scripts/tlo.png'
sh: /home/windsor/.scripts/ip.sh: not found
Conky: Unable to load image '/home/windsor/.scripts/tlo.png'
^CConky: received SIGINT or SIGTERM to terminate. bye!
windsor@windsor-desktop:/$ cd /home/windsor/.scripts/
bash: cd: /home/windsor/.scripts/: No such file or directory
windsor@windsor-desktop:/$ ^C

---

### Post by davec64 on 2010-02-23
First off, can you post your .conkyrc file?

It would be interesting to see what it's trying to do!

> sh: sensors: not found
sh: sensors: not found
connect: Connection refused
sh: /home/windsor/.scripts/ip.sh: not found
Conky: Unable to load image '/home/windsor/.scripts/tlo.png'
Conky: Unable to load image '/home/windsor/.scripts/tlo.png'
Conky: Unable to load image '/home/windsor/.scripts/tlo.png'
sh: /home/windsor/.scripts/ip.sh: not found
Conky: Unable to load image '/home/windsor/.scripts/tlo.png'
sh: /home/windsor/.scripts/ip.sh: not found
Conky: Unable to load image '/home/windsor/.scripts/tlo.png'
^CConky: received SIGINT or SIGTERM to terminate. bye!
windsor@windsor-desktop:/$ cd /home/windsor/.scripts/
bash: cd: /home/windsor/.scripts/: No such file or directory

The sensors not found, I think refers to lmsensors which you probably haven't got installed.

> sh: /home/windsor/.scripts/ip.sh: not found

Appears to refer to a script called ip.sh that's located in a folder called .scripts. Have you put that script in that folder and made it executable?

I suggest before trying scripts, start with a very basic .conkyrc file just to test things out. It's then easier to add things bit by bit making sure every thing works!

I've attached a basic conky file for you to test with. Rename it ".conkyrc" (without the quotes, leave the full stop there) and save it in your home folder.

Then try conky again.

---

### Post by TurnOfTide on 2010-02-23
I am missing the ~/.scripts/ directory completely. :-k

---

### Post by TurnOfTide on 2010-02-27
Bump:


Why am I missing this ~/.scritps folder? What should I do at this point?

---

### Post by mick222 on 2010-02-27
did you trty doing what dave said . you must have a .conkyrc file to  run conky

---

### Post by alexandari on 2010-02-27
> **TurnOfTide said:**
> Bump:


Why am I missing this ~/.scritps folder? What should I do at this point?


um...make one? lol

---

### Post by mick222 on 2010-02-27
The conky file you are trying to run isn't coded properly if you post it someone will be able to help. It should be a hidden folder in your home directory

---

### Post by stinkeye on 2010-02-27
> **alexandari said:**
> um...make one? lol
You cant just grab any conky config and run it.
People use their own scripts which aren't included with conky.
Some users post their scripts as well.
You also may need to install other stuff like lm-sensors, hddtemp or curl.

I suggest you start here: 
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=5436679&postcount=1")

---

### Post by alexandari on 2010-02-27
> **stinkeye said:**
> You cant just grab any conky config and run it.
People use their own scripts which aren't included with conky.
Some users post their scripts as well.
You also may need to install other stuff like lm-sensors, hddtemp or curl.

I suggest you start here: 
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=5436679&postcount=1")


Maybe the scripts which he is trying to use are already written? But..nvm

---

### Post by rustutzman on 2010-02-27
For Conky help, info, and scripts.
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Russ

---

### Post by stinkeye on 2010-02-27
> **alexandari said:**
> Maybe the scripts which he is trying to use are already written? But..nvm
Yes, most of the scripts you need are already written but if you don't have them or there's not a download link for the scripts it's a waste of time trying to run that particular config.

This thread [**_[COLOR="DarkRed"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865") 
has over a thousand pages of conky configs.
Find one you like and if it's using any scripts make sure they're included.

---

### Post by stinkeye on 2010-02-27
For example, one of the conkys I run uses a calendar script and a script to draw a semi-transparent background.
I didn't write the scripts.
They were posted with the conky config.
Try it out.
For this to work you need to uninstall conky and install the conky-all package, through synaptic, which has support for displaying images.
Create a folder called conky in your home directory

Save this conky config as conkycal in your conky folder.
```
background yes
update_interval 30
total_run_times 0

own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
own_window_colour 0D141A
double_buffer yes
minimum_size 0 
maximum_width 260  
alignment tr

gap_x 10
gap_y 10


use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 1.0
uppercase no
override_utf8_locale yes
#use_spacer right
text_buffer_size 2048
imlib_cache_size 0

default_color 919FAA
default_shade_color 333333
default_outline_color 00ff00

draw_shades no
draw_outline no
draw_borders no

no_buffers yes
cpu_avg_samples 2
net_avg_samples 2

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

draw_graph_borders no
stippled_borders 0
border_inner_margin 5
border_outer_margin 6
short_units no

# set to yes if you want all text to be in uppercase
uppercase no

# colours
#off white
color1 BDAC88

# cream
color2 D2B16A

# grey
color3 8FA0A8

# yellow
color4 F1BC49

# red
color5 F352A9

#dark grey
color6 36505E

#grey
color7 6b6b6b

#orange
color8 E27E03

#yellow
color9 F1BC49

# calendar next month
# ${color}${font LCDMono:bold:size=8}${execpi 60 cal $(date '+%-m %-Y' --date="next month")|sed 's/^/${goto 30}/'}

# one liner
# ${font LCDMono:bold:size=17}${execpi 60 DJS=`date +%_d`; cal |tail -n +2 |sed 's/^/${color 777777}${alignc}/' |sed '1s/ 777777/2/' |sed /" $DJS "/s/" $DJS "/" "'${color2}'"$DJS"'${color 777777}'" "/}$font

lua_load ~/conky/draw_bg.lua
lua_draw_hook_pre draw_bg

TEXT
${color CC9846}${font LCDMono:bold:size=16}${alignc}${time %B %Y}
${color}${font LCDMono:bold:size=14}${pre_exec ~/conky/calendario.sh semana}
${color 4C483D}${pre_exec ~/conky/calendario.sh pasado}${color CC9846}${pre_exec ~/conky/calendario.sh hoy}${color}${pre_exec ~/conky/calendario.sh futuro}$font
``` 



Save this script as calendario.sh in your conky folder.
```
#! /bin/sh
# written by: jjgomera

#str=`echo '\033[01;32m29'`

# replace the 4 "cal |" with "cal -m |" to have the week start on Monday

DATE=`date | awk -F" " '{print $3}'`

case "$1" in
mes)
cal | head -n1
;;
semana)
cal | head -n2 | tail -n1
;;
pasado)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=0}
($1 == $0 && i==0) {print $1}($1 != $0 && i==0){i=i+1;print $1}';
;;
hoy)
echo $DATE;
;;
futuro)
cal | grep -v '[a-zA-Z]' | grep '[0-9]' | awk -F$DATE ' BEGIN {i=1}
(i==0) {print $0}($1 != $0 && i==1){i=i-1;print $2}';
;;
esac
```



Save this script as draw_bg.lua in your conky folder
```
--[[
Background by londonali1010 (2009)

This script draws a background to the Conky window. It covers the whole of the Conky window, but you can specify rounded corners, if you wish.

To call this script in Conky, use (assuming you have saved this script to ~/scripts/):
	lua_load ~/scripts/draw_bg.lua
	lua_draw_hook_pre draw_bg

Changelog:
+ v1.0 -- Original release (07.10.2009)
]]

-- Change these settings to affect your background.
-- "corner_r" is the radius, in pixels, of the rounded corners. If you don't want rounded corners, use 0.

corner_r=60

-- Set the colour and transparency (alpha) of your background.

bg_colour=0xA1948F
bg_alpha=0.3

require 'cairo'
function rgb_to_r_g_b(colour,alpha)
	return ((colour / 0x10000) % 0x100) / 255., ((colour / 0x100) % 0x100) / 255., (colour % 0x100) / 255., alpha
end

function conky_draw_bg()
	if conky_window==nil then return end
	local w=conky_window.width
	local h=conky_window.height
	local cs=cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, w, h)
	cr=cairo_create(cs)
	
	cairo_move_to(cr,corner_r,0)
	cairo_line_to(cr,w-corner_r,0)
	cairo_curve_to(cr,w,0,w,0,w,corner_r)
	cairo_line_to(cr,w,h-corner_r)
	cairo_curve_to(cr,w,h,w,h,w-corner_r,h)
	cairo_line_to(cr,corner_r,h)
	cairo_curve_to(cr,0,h,0,h,0,h-corner_r)
	cairo_line_to(cr,0,corner_r)
	cairo_curve_to(cr,0,0,0,0,corner_r,0)
	cairo_close_path(cr)
	
	cairo_set_source_rgba(cr,rgb_to_r_g_b(bg_colour,bg_alpha))
	cairo_fill(cr)
end
```

Go to your conky folder and make calendario.sh and draw_bg.lua
executable by right clicking > properties > permissions
and tick the execute box.

If you look at the conky config you will see I'm using
a font called LCDMono
Download from here [**_[COLOR="DarkRed"]http://www.dafont.com/lcd-lcd-mono.font[/COLOR]_**]("http://www.dafont.com/lcd-lcd-mono.font")
Extract and place in your home directory in your .fonts folder.
If you don't have a .fonts folder, create one.
Dot files and folders are hidden............ctrl + h to show hidden files.

In conky to call the scripts I'm using  ~/conky/ as the path
~ symbol is a shortcut for /home/username 
So if you created a conky folder in home, the paths do not need to be changed.

Now if you run in terminal 
```
conky -c ~/conky/conkycal
```
You should see a widget style conky in the top right corner.

That's the sort of process you need to go through when you download more advanced conky configs

---

