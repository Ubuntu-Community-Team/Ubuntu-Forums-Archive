---
title: "Conky issues ..."
date: 2009-07-17
forum: New to Ubuntu
---

### Post by crowhill on 2009-07-17
Hi there

Maybe, the answer to my question has been posted somewhere in this forum already. If so, I'm sorry for asking it again. I simply couldn't find the answer.

Okee, I'm completely new to Conky. I downloaded it, copied "conky.conf"

> 
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2007 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
# $Id: conky.conf 1193 2008-06-21 20:37:58Z ngarofil $

alignment bottom_left
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no
show_graph_scale no
show_graph_range no

TEXT
${scroll 16 $nodename - $sysname $kernel on $machine | }
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
$hr
${color grey}Name                  PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}


to the folder "conky" in my home directory, renamed it to "conky_setup", changed "use_apacer no" to "use_spacer right" and run

```

$ conky -c ~/conky/conky_setup

```

in a terminal. From this, I get (*)

```

Conky: desktop window (14000a6) is subwindow of root window (13c)
Conky: window type - normal
Conky: drawing to created window (0x3000002)
Conky: drawing to single buffer

```

in the terminal and a cute Conky popping up in the lower left corner of my screen. Closing the pop up window gives me (**)

```
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0" after 1397 requests (1329 known processed) with 0 events remaining.
```

and the terminal goes back to the command line (a "$"). Now, I want Conky to be fixed to the background (no extra window) with a transparent colour. To do so, I try to change "background no" to "background yes" in my "conky_setup". This gives (***)

```

Conky: forked to background, pid is 9416
$ 
Conky: desktop window (14000a6) is subwindow of root window (13c)
Conky: window type - normal
Conky: drawing to created window (0x3200002)
Conky: drawing to single buffer

```

in the terminal and a Conky popping up at the exact same location in an extra window. Closing Conky gives the same as above [see (**)] but this time the terminal does not go back to the "$". It's somehow stuck. I have to close and restart it in order to be able to use it. Also, note that in (***) the terminal temporarily goes back to the "$" and then continues to do the previous thing [see (*)]. **[COLOR="Red"]What is going on here?[/COLOR]**

I want Conky to be running in the desktop and not in an extra window. Also, I want its colour to be transparent. **[COLOR="Red"]How can I achieve this? What do all the error messages mean? Do I NEED Compiz to get it running in the desktop and transparent?[/COLOR]**

Some advice would be very much appreciated.

Thanks a lot in advance,
cheers,

crowhill.

---

### Post by halitech on 2009-07-17
why not install the version in the repos and then just create a .conkyrc file in your home folder?

there are 1000's of examples in this thread to help you out

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

you don't need compiz to use conky.

here's the top part of mine
```
# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 260

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 70
alignment top_right
#alignment bottom_left
#alignment bottom_right

```

---

### Post by crowhill on 2009-07-17
Here is my top part:

> alignment top_right
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_transparent yes
own_window_class Conky
own_window_type normal
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer right
show_graph_scale no
show_graph_range no

Looking at your top part, I inserted

> own_window_transparent yes

in mine. Now, the pop up window is transparent but only for a few seconds. Also, it's still in a window and not in on the desktop. I have Gnome, does it matter?

I was looking at the examples given in the thread you mentioned. They don't work for me (they refer to different systems or use software I don't need). I want it (the layout) as simple as possible: as part of the desktop and transparent. The rest (what is displayed) I can figure out myself ... I hope.

Cheers,
crowhill.

---

### Post by halitech on 2009-07-17
change this
```
own_window_type normal
```
to this
```
own_window_type override
```
add this
```
own_window_hints undecorated,below,skip_taskbar
```
and see if that makes any difference

---

### Post by ~sHyLoCk~ on 2009-07-17
```
own_window_type override
``` doesn't work for me.
```
own_window_type desktop
```however does.
Besides override windows are not under the control of the window manager. Hints are ignored.

---

### Post by crowhill on 2009-07-17
Now, my top bar looks like this

> alignment top_right
background no
border_width 1
cpu_avg_samples 2
default_color black
default_outline_color black
default_shade_color black
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window no
own_window_class Conky
own_window_transparent yes
own_window_type desktop
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer right
show_graph_scale no
show_graph_range no

Everything is fine except for that the files and folders on the desktop disappeared. When I focus on the desktop and hit <Ctrl>+<r> the files and folders show up for a few seconds and disappear again. I added 

> own_window_hints undecorated,below,skip_taskbar

but it made things worse as the desktop wallpaper vanished and the screen became all grey ...

How to keep the files on the desktop visible?

Thank you very much,
cheers,

crowhill.

---

### Post by crowhill on 2009-07-17
Figured it out. Changed

own_window no

to

own_window yes

and added

own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

and

own_window_type desktop

again. Everything is fine now.

Is it possible to have the nm-applet (network monitor) running in Conky? How about the volume control bar?

Thank you so much,
cheers,

crowhill.

---

### Post by crowhill on 2009-07-17
arr ... not everything is fine ... if I click on the desktop, Conky vanishes ...

it seems that i cannot see both the files and Conky at the same time. Using the files makes Conky vanish and with the old settings viewing Conky hides the files ...

i guess, i should not have any files on the desktop :)

cheers,
crowhill.

---

### Post by ~sHyLoCk~ on 2009-07-17
> **crowhill said:**
> arr ... not everything is fine ... if I click on the desktop, Conky vanishes ...

it seems that i cannot see both the files and Conky at the same time. Using the files makes Conky vanish and with the old settings viewing Conky hides the files ...

i guess, i should not have any files on the desktop :)

cheers,
crowhill.

Position your conky wisely! Use offsets if needed or use alignment to change conky position. If you want to learn more about conky visit the link provided above also you may wanna read [this]("http://conky.linux-hardcore.com/").

---

