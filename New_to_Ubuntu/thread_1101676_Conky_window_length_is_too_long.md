---
title: "Conky window length is too long"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Morrad on 2009-03-20
EDIT: Answer was provided for me in this post: [http://ubuntuforums.org/showpost.php?p=6929876&postcount=1248](http://ubuntuforums.org/showpost.php?p=6929876&postcount=1248)

As you can see from the picture attachment, I have a conky window that is longer than it should be.  I'm not sure whats causing that.  I'd like to be able to get rid of the extra space.  I'm trying to use the script created by kaivalagi here:
[http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)

The conky configuration file
```

# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 3.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 5

# Maximum width of the window
maximum_width 300

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders yes

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 0

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black
color1 white
color2 lightgrey
color3 orange

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 324
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

# Shows the maximum value in scaled graphs.
show_graph_scale no

# Shows the time range covered by a graph.
show_graph_range no

# Text Buffer size of exec commands.
text_buffer_size 1024

#############################################################################
#############################################################################

TEXT
${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}Weather${font}  ${hr}${color1}
${execpi 1800 conkyForecast -i --location=USWA0356 --template=/home/grahjm2a/.conky_scripts/conky_weather.template}

```

The template file for the conkyForcast function
```

${voffset 5}${goto 10}${font ConkyWeather:style=Bold:size=40}[--datatype=WF]${font}
${voffset 5}${goto 20}[--datatype=HT --hideunits --centeredwidth=3]/[--datatype=LT --hideunits --centeredwidth=3]
${voffset 10}${goto 10}${font ConkyWindNESW:size=40}[--datatype=BS]${font}
${voffset 5}${goto 10}[--datatype=WS --imperial] - [--datatype=WD]
${voffset -145}${goto 100}${color1}${font Bitstream Vera Sans Mono:style=Bold:size=14}[--datatype=CT]${font}
${voffset 10}${goto 100}${color3}Station: ${color1}[--datatype=OB]
${goto 100}${color3}Rain: ${color1}[--datatype=PC]
${goto 100}${color3}UV: ${color1}[--datatype=UI] - [--datatype=UT]
${goto 100}${color3}Humidity: ${color1}[--datatype=HM]
${goto 100}${color3}Dew Point: ${color1}[--datatype=DP]
${goto 100}${color3}Sunrise/Set: ${color1}[--datatype=SR] / [--datatype=SS]
${goto 100}${color3}Bar: ${color1}[--datatype=BR] - [--datatype=BD]
${goto 100}${color3}Moon: ${color1}[--datatype=MP]
${voffset 25}${goto 25}[--datatype=DW --startday=1 --shortweekday]${goto 100}[--datatype=DW --startday=2 --shortweekday]${goto 175}[--datatype=DW --startday=3 --shortweekday]${goto 250}[--datatype=DW --startday=4 --shortweekday]
${voffset 10}${goto 10}${font ConkyWeather:size=32}[--datatype=WF --startday=1 --endday=4 --spaces=3]${font}
${voffset 15}${goto 15}[--datatype=HT --startday=1 --hideunits --centeredwidth=3]/[--datatype=LT --startday=1 --hideunits --centeredwidth=3]${goto 90}[--datatype=HT --startday=2 --hideunits --centeredwidth=3]/[--datatype=LT --startday=2 --hideunits --centeredwidth=3]${goto 170}[--datatype=HT --startday=3 --hideunits --centeredwidth=3]/[--datatype=LT --startday=3 --hideunits --centeredwidth=3]${goto 245}[--datatype=HT --startday=4 --hideunits --centeredwidth=3]/[--datatype=LT --startday=4 --hideunits --centeredwidth=3]
${color3}${font Bitstream Vera Sans Mono:size=7}${alignr 20}Last Update: [--datatype=LU]${font}

```

---

