---
title: "Conky in Karmic. Fail :("
date: 2010-03-05
forum: New to Ubuntu
---

### Post by zosolm on 2010-03-05
I found a conky code i really like on the internet.
I have saved it as conky.conf in /etc/conky/ (i don't think that's the problem)
It is supposed to display the song i'm playing in the top left corner of the desktop and be transparent. 
Instead, running

 ```
sudo conky
```

returns this:

```

Conky: forked to background, pid is 25218
X@X-desktop:~$ 
Conky: desktop window (7c00033) is subwindow of root window (1a7)
Conky: window type - desktop
Conky: drawing to created window (0x8c00001)
Conky: drawing to double buffer
sh: mocp: not found
```and nothing happens.

Another thing i can't understand is 
```
sh: mocp: not found
```repeats indefinitely.


Here's the code.

code:

```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Museo:size=8
xftfont Basicdots:size=7
#font edges.se

# Text alpha when using Xft
xftalpha 1

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
    own_window yes
    own_window_transparent yes
    own_window_type desktop
    own_window_hints undecorated, below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

text_buffer_size 1024

# Minimum size of text area
minimum_size 220 50

# Maximum width
maximum_width 220

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text


# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
stippled_borders 0

border_inner_margin 3
border_width 0
draw_borders no

default_color 000000
#default_color D1E2B4
default_shade_color black
default_outline_color white
own_window_colour 555555

color2 111111
color3 303030

alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment bottom_middle
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y -60

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

TEXT
${color2}${font CKAS:size=45}j${color}
${voffset -96}${offset 70}${font}${execpi 1 mocp -Q %state}
${offset 70}What: ${execpi 1 mocp -Q %song}
${offset 70}Who: ${execpi 1 mocp -Q %artist}
${offset 70}Where: ${execpi 1 mocp -Q %album}
${offset 70}How long: ${execpi 1 mocp -Q %tl} / ${execpi 1 mocp -Q %tt}
```i'm not very experienced, so sorry if it's obvious :/

I'm running a gnome shell , but it does the same thing on a  normal Karmic desktop, anyway.

thanks

---

### Post by Apollo87 on 2010-03-05
The mocp error is because you don't have music on console installed:

```
sudo apt-get install moc
```

and as for the conky file, the only problem is the y gap is set to -60 so its displaying off the screen. Heres the changed version:

```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Museo:size=8
xftfont Basicdots:size=7
#font edges.se

# Text alpha when using Xft
xftalpha 1

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
    own_window yes
    own_window_transparent yes
    own_window_type desktop
    own_window_hints undecorated, below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

text_buffer_size 1024

# Minimum size of text area
minimum_size 220 50

# Maximum width
maximum_width 220

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text


# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
stippled_borders 0

border_inner_margin 3
border_width 0
draw_borders no

default_color 000000
#default_color D1E2B4
default_shade_color black
default_outline_color white
own_window_colour 555555

color2 111111
color3 303030

alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment bottom_middle
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y 0

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

TEXT
${color2}${font CKAS:size=45}j${color}
${voffset -96}${offset 70}${font}${execpi 1 mocp -Q %state}
${offset 70}What: ${execpi 1 mocp -Q %song}
${offset 70}Who: ${execpi 1 mocp -Q %artist}
${offset 70}Where: ${execpi 1 mocp -Q %album}
${offset 70}How long: ${execpi 1 mocp -Q %tl} / ${execpi 1 mocp -Q %tt}
```

---

