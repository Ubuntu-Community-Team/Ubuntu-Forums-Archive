---
title: "whats wrong with my conkyrc?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by pluckypigeon on 2009-02-22
I get a segmentation fault

```


# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
#use_spacer yes
use_xft yes

# Update interval in seconds
#update_interval 3.0

# Minimum size of text area
minimum_size 300 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 0

# border margins
border_margin 0

# border width
border_width 0

# Default colors and also border colors, grey90 == #e5e5e5
default_color lightblue
default_shade_color black
default_outline_color lightblue

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 0
gap_y 4



# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=7
xftalpha 0.8

TEXT

${offset 240}${color lightblue}${time %a, } ${color }${time %e %B %G}
${offset 240}${color lightblue}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color lightblue}UpTime: ${color }$uptime

${offset 240}${color lightblue}Kern:${color }$kernel
${offset 240}${color lightblue}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,100 000000 ffffff}
${offset 240}${color lightblue}Load: ${color }$loadavg
${offset 240}${color lightblue}Processes: ${color }$processes  
${offset 240}${color lightblue}Running:   ${color }$running_processes

${offset 240}${color lightblue}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightblue} ${top name 2}${top cpu 2}
${offset 240}${color lightblue} ${top name 3}${top cpu 3}
${offset 240}${color lightblue} ${top name 4}${top cpu 4}
${offset 240}${color lightblue} ${top name 5}${top cpu 5}
${offset 240}${color lightblue} ${top name 6}${top cpu 6}
${offset 240}${color lightblue} ${top name 7}${top cpu 7}
${offset 240}${color lightblue} ${top name 8}${top cpu 8}
${offset 240}${color lightblue} ${top name 9}${top cpu 9}
${offset 240}${color lightblue} ${top name 10}${top cpu 10}

${offset 240}${color lightblue}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightblue} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightblue} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightblue} ${top_mem name 4}${top_mem mem 4}
${offset 240}${color lightblue} ${top_mem name 5}${top_mem mem 5}

${offset 240}${color lightblue}MEM:  ${color }$memperc%
${offset 240}${color }$mem
${offset 240}${color }/$memmax
${offset 240}${membar 3,100}
${offset 240}${color lightblue}SWAP: ${color }$swapperc%
${offset 240}${color }$swap
${offset 240}${color }/$swapmax
${offset 240}${swapbar 3,100}
${offset 240}${color lightblue}ROOT:    
${offset 240}${color }${fs_free /}
${offset 240}${color }/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color lightblue}HOME:  
${offset 240}${color }${fs_free /home}
${offset 240}${color }/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color lightblue}MORE MUSIC:  
${offset 240}${color }${fs_free /media/moremusic}
${offset 240}${color }/${fs_size /media/moremusic}
${offset 240}${fs_bar 3,100 /media/moremusic}
${offset 240}${color lightblue}JAUNTY:
${offset 240}${color }${fs_free /media/disk-1}
${offset 240}${color }/${fs_size /media/disk-1}
${offset 240}${fs_bar 3,100 /media/disk-1}
${offset 240}${color lightblue}MUSIC:  
${offset 240}${color }${fs_free /media/music}
${offset 240}${color }/${fs_size /media/music}
${offset 240}${fs_bar 3,100 /media/music}
${offset 240}${color lightblue}2GB:  
${offset 240}${color }${fs_free /media/disk-2}
${offset 240}${color }/${fs_size /media/disk-2}
${offset 240}${fs_bar 3,100 /media/disk-2}
${offset 240}${color lightblue}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,100 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,100 000000 ffffff}


```

thanks in advance

---

### Post by 5BallJuggler on 2009-02-22
I'm no expert, but your offset maybe too big, try setting to 0.

to get a better understanding of your problem can you post a screenshot.

---

### Post by pluckypigeon on 2009-02-22
> **5BallJuggler said:**
> 

to get a better understanding of your problem can you post a screenshot.

when it runs it runs fine but it doesn't always start. >>> > **pluckypigeon said:**
> I get a segmentation fault 

---

