---
title: "command + grep + formatting"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by championboxes on 2010-02-23
Im currently messing around with conky and trying to add a command that will display what graphics card I have... so far I have 

input```
nvclock -i | grep 'Card:' | awk '{print $2 $3 $4 $5}'
``` 

this displays what I want however there are no spaces 

output```
nVidiaGeforceGo7900GS
```

this
```
nvclock -i | grep 'Card:'
``` is the info I need but i dont know how to format it...

output
```
Card: 		nVidia Geforce Go 7900GS
```

if someone could tell me what command I would need to use I would be most grateful... also if you could show me some documentation I would like to learn myself...

---

### Post by undecim on 2010-02-23
Try ```
nvclock -i | cut -f "3-"
```

cut removes part of the line. the -f "3-?, means "print everything from the third field to the end"

EDIT: A better option would be to use lspci, because that would work with any graphics card Gimme a few minutes and I'll see if I can come up with a script for that.

EDIT: The escape sequences always give me a headache. Try this command: ```
lspci | sed -n 's/.*VGA.*\[\(.*\)\]/\1/p'
```on mine, I got```
Radeon HD 3200 Graphics
```It should work with any graphics card (not just nvidia), and it will output 1 line for each graphics card present, so you can share your .conkyrc with someone else with a different graphics card and it should work.

---

### Post by championboxes on 2010-02-23
> **undecim said:**
> Try ```
nvclock -i | cut -f "3-"
```
Try this command: ```
lspci | sed -n 's/.*VGA.*\[\(.*\)\]/\1/p'
```

Thanks! both of these worked 
this
```
GeForce Go 7900 GS (rev a1)
``` was the second command output do you know of a site that shows examples of formatting like this?

here is the .conkyrc as of right now... I got it from here about a year ago and made slight mods to it... it still needs work though
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

#on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 2
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

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
#xmms_player bmp

# boinc (seti) dir
# seti_dir /opt/seti

color0 3A3835 #color of typed stuff
color1 7B573D #color of displayed stuff
color2 767573 #color of first part of graph

TEXT
${color0}$sysname $kernel $machine - $nodename 

${color0}Uptime:${color1} $uptime ${color0} Load:${color1} $loadavg

${color0}${exec cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color1}
${color0}Usage:${color0} ${color1}${cpu}% ${color0}${cpubar}
${color0}${cpugraph 767573 3A3835}
${color0}Proces:${color1} $processes  ${color0}Run:${color1} $running_processes 
${color0}Clock Speed:${color1} ${freq_dyn}Mhz ${color0}M/B Temp: ${color1}$acpitemp°C

${color0}${exec lspci | sed -n 's/.*VGA.*\[\(.*\)\]/\1/p'} ${color1}
${color0}GPU0 Temp: ${color1}${exec nvidia-settings -q [gpu:0]/gpucoretemp  |grep '):' | awk '{print $4}' |cut -b 1,2}°C ${color0}GPU1 Temp: ${color1}${exec nvidia-settings -q [gpu:1]/gpucoretemp  |grep '):' | awk '{print $4}' |cut -b 1,2}°C

${color0}RAM:${color1} $mem/$memmax - $memperc% ${alignr}${color0}${membar 5,110}
${color0}SWP:${color1} $swap/$swapmax - $swapperc% ${alignr}${color0}${swapbar 5,110}

${color0}HD Read: ${color1}${diskio_read}
${color0}${diskiograph_read 767573 3A3835}

${color0}HD Write: ${color1}${diskio_write}
${color0}${diskiograph_write 767573 3A3835}

${color0}Hard Disks:
${if_mounted /}${font dejavusansmono:size=7}${color0}${fs_free_perc /}% free on /
${color0}${fs_bar 10 /}
${color1}${voffset -12} /dev/sda6$alignr${fs_used /}/${fs_size /} ${endif}$font
${if_mounted /media/Windows}${font dejavusansmono:size=7}${color0}${fs_free_perc /media/Windows}% free on WINDOWS
${color0}${fs_bar 10 /media/Windows}
${color1}${voffset -12} /media/WINDOWS$alignr${fs_used /media/Windows}/${fs_size /media/Windows} ${endif}$font
${if_mounted /media/EXTERNAL}${font dejavusansmono:size=7}${color0}${fs_free_perc /media/EXTERNAL}% free on EXTERNAL
${color0}${fs_bar 10 /media/EXTERNAL}
${color1}${voffset -12} /media/EXTERNAL$alignr${fs_used /media/EXTERNAL}/${fs_size /media/EXTERNAL} ${endif}$font
${if_mounted /media/Media-Storage}${font dejavusansmono:size=7}${color0}${fs_free_perc /media/Media-Storage}% free on Media
${color0}${fs_bar 10 /media/Media-Storage}
${color1}${voffset -12} /media/Media-Storage$alignr${fs_used /media/Media-Storage}/${fs_size /media/Media-Storage} ${endif}$font
${if_mounted /media/CRUZER}${font dejavusansmono:size=7}${color0}${fs_free_perc /media/CRUZER}% free on CRUZER
${color0}${fs_bar 10 /media/CRUZER}
${color1}${voffset -12} /media/CRUZER$alignr${fs_used /media/CRUZER}/${fs_size /media/CRUZER} ${endif}$font

${color0}CPU Usage         PID     CPU%   MEM%
${color1} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color0} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color0} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color0} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color0}Mem Usage
${color1} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color0} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color0} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color0} ${top_mem name 4} ${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}

${color0}Network: ${color1}${addr wlan0}

${color0}Wireless Connection:${color1} ${wireless_link_qual_perc wlan0}%
${color0}Down:${color1} ${downspeed wlan0} k/s $alignr${color0} Up:${color1} ${upspeed wlan0} k/s
${color0}${downspeedgraph wlan0 27,120 767573 3A3835 180} $alignr${color0}${upspeedgraph wlan0 27,120 767573 3A3835 100}
${color1}${totaldown wlan0}           $alignr${color1}${totalup wlan0}

${color0}Port(s)${alignr}#Connections
${color0}Inbound: ${color1}${tcp_portmon 1 32767 count}  ${color0}Outbound: ${color1}${tcp_portmon 32768 61000 count}${alignr}${color0}Total: ${color1}${tcp_portmon 1 65535 count}
```

---

