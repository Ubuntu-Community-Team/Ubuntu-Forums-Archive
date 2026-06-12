---
title: "conky help??"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by Donjr on 2011-02-27
Just wondering if anybody can help me straighten this out. I have picked and poked different conkys and added them to mine to get what i need. 
Just wondering if anyone can tell me or send me to a site that will help organize this a little better
TYAVMIA :-)


# Conky configuration
#
# Variable definitions:

# set to yes if you want Conky to be forked in the background
background no
# Use Xft?
use_xft yes
# Xft font when Xft is enabled
xftfont sans:size=12
# Text alpha when using Xft
xftalpha 0.8
# Update interval in seconds
update_interval 1.0
# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0
# Create own window instead of using desktop (required in nautilus)
own_window yes
# If own_window is yes, you may use type normal, desktop or override
own_window_type override
# Use pseudo transparency with own_window?
#own_window_transparent yes
# If own_window_transparent is set to no, you can set the background colour    here
own_window_colour black
# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# Use double buffering (reduces flicker, may not work for everyone)
temperature_unit fahrenheit
double_buffer yes
# Minimum size of text area
minimum_size 350
# Maximum size of text area
maximum_width 450
# Draw shades?
draw_shades no
# Draw outlines?
draw_outline no # makes text too bold if yes
# Draw borders around text
draw_borders no
# Draw borders around graphs
draw_graph_borders yes
# Stippled borders?
stippled_borders 8
# border margins
border_margin 4
# border width
border_width 1
# Default colors and also border colors
default_shade_color black
default_outline_color black
# Alignment of conky window; other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none
# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 50
gap_y 50
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
override_utf8_locale no
# Add spaces to keep things from moving about? This only affects certain objects.
#use_spacer no
#
# TEXT TO SHOW:
#
# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
TEXT
${color FF6600}SYSTEM INFORMATION
${color}${pre_exec whoami} @ $nodename: $sysname 
$kernel  $machine
${hr 2}
${pre_exec sudo dmidecode --type baseboard | grep 'Product' | cut -d' ' -f3-}  ${pre_exec sudo dmidecode --type baseboard | grep 'Manufacturer' | cut -d' ' -f2-}
${color FF6600}Uptime:${color} $uptime ${color} - Load:${color}  $loadavg
${color FF6600}Driver:${color} ${execpi 3600 Driver="NVidia "`nvidia-settings -q NvidiaDriverVersion -t`; echo "$Driver"}    Resolution: ${execpi 3600 Resolution=`nvidia-settings -q FrontEndResolution -t`; echo "$Resolution"}
${color FF6600}CPU temp:${color}$alignr${hwmon temp 1}
${hr 2}
${pre_exec cat /proc/cpuinfo | grep 'model name' | cut -d' ' -f3-}
${hr 2}
${color FF6600} CPU Usage:${color} $cpu% ${cpubar}
${color} ${cpugraph 0000ff 00ec00}
${color FF6600} RAM Usage:${color} $mem/$memmax - $memperc% ${membar}
${color} ${memgraph 0000ff 00ec00}
${color FF6600}Swap Usage${color} $swap/$swapmax - $swapperc% ${swapbar}
${color FF6600}Processes${color} Running:${color}$running_processes
${color FF6600}Disks:${hr 2}${color}
${color} /dev/sdb1 ${color}(${fs_type /}) /: ${alignr} /dev/sda1 ${color}(${fs_type /home}) /home:
${fs_used /} used of ${fs_size /} ${alignr} ${fs_used /home} used of ${fs_size /home}
Disk I/O - ${diskio /dev/sdb1} ${alignr} Disk I/O - ${diskio /dev/sda1} 
${diskiograph /dev/sdb1 35,130 ff0000 0000ec}                          ${diskiograph /dev/sda1 35,130 ff0000 0000ec}
${hr 2}
${color FF6600}Processes by CPU usage${hr 2}${color}
${color} Name ${alignr} PID CPU% MEM%
${color #ec0000} ${top name 1} ${alignr} ${top pid 1} ${top cpu 1} ${top mem 1}
${color} ${top name 2} ${alignr} ${top pid 2} ${top cpu 2} ${top mem 2}
 ${top name 3} ${alignr} ${top pid 3} ${top cpu 3} ${top mem 3}
 ${top name 4} ${alignr} ${top pid 4} ${top cpu 4} ${top mem 4}
${color FF6600}Processes by mem usage${hr 2}${color}
${color} Name ${alignr} PID CPU% MEM%
${color #ec0000} ${top_mem name 1} ${alignr} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem    mem 1}
${color} ${top_mem name 2} ${alignr} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem    mem 2}
 ${top_mem name 3} ${alignr} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
 ${top_mem name 4} ${alignr} ${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}
${color FF6600}Networking:${hr 2}${color}
 IP: ${addr eth0}      Public ip: ${gw_ip eth0}
 Down:${color} ${downspeed eth0} k/s${color} ${alignr}Up:${color}    ${upspeed eth0} k/s
 ${color}${downspeedgraph eth0 35,130 ff0000 0000ec}${alignr}${upspeedgraph eth0    35,130 0000ff ec0000}
${color FF6600}Connections in:${color} ${tcp_portmon 1 32767 count}${color} Connections    out:${color} ${tcp_portmon 32768 61000 count}${color} Total:${color}    ${tcp_portmon 1 65535 count}
${hr 2}

---

### Post by davidmohammed on 2011-02-27
not sure what you mean by "organise it better" - have you tried a gui editor for conky such as [this]("http://www.webupd8.org/2009/09/gui-for-configuring-conky.html")?

---

### Post by ajgreeny on 2011-02-27
I quite like the look of all that, and apart from the colours being wrong on my wallpaper, it really is a case of asking what you want conky to show.  It is not actually very different from mine, which I show below, so feel free to pick and choose from that and add to yours, if you feel it gives you something that you like.

PS:  I have vnstat and hddtemp installed for the two last items, so they will not show properly if you don't have those available in your system, but everything else is just standard ubuntu stuff, I think.
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=11

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 250

# Maximum width
maximum_width 250

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 30
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

TEXT
${font Trebuchet MS:size=30} ${alignc}${time %k:%M}${font Trebuchet MS:size=11}
${font Trebuchet MS:size=20} ${alignc}${time %a %b %d %Y}${font Trebuchet MS:size=11}
${color #56073D}Hostname:${color #DE0084}$alignr$nodename
${color #56073D}Uptime:${color #DE0084}$alignr$uptime

${color #56073D}CPU ${color #DE0084}${cpu cpu1}% ${color #56073D}${cpubar cpu1}
${color #56073D}Processes: ${color #DE0084}$processes ${alignr}Running: $running_processes
#
#${color #56073D}CPU Usage        ${color #DE0084} $alignr PID   CPU%   MEM%
#${color #56073D} ${top name 1} ${color #DE0084} $alignr ${top pid 1}  ${top cpu 1}  ${top mem 1}

${color #56073D}sda1$alignr ${color #DE0084}${fs_used /}/${fs_size /}
${color #56073D} Root ${color #DE0084}${fs_used_perc /}% ${color #56073D}${fs_bar /}

${color #56073D}sda2$alignr ${color #DE0084}${fs_used /home}/${fs_size /home}
${color #56073D} Home ${color #DE0084}${fs_used_perc /home}% ${color #56073D}${fs_bar /home}

${color #56073D}RAM Used:$alignr${color #DE0084}$mem of $memmax ${color #DE0084}= ${color #DE0084}$memperc%
${color #56073D}Swap:${alignr}${color #DE0084}$swapperc%     $swap of $swapmax

${color #56073D}NETWORK IP:${color #DE0084} $alignr eth0 -  ${color #DE0084}${addr eth0}
${color #56073D}DOWN:${color #DE0084} ${downspeed eth0}/s ${color #56073D}$alignr TOTAL ${color #DE0084}${totaldown eth0}
${color #56073D}${downspeedgraph eth0 20,250 000000 #56073D}
${color #56073D} Up:${color #DE0084} ${upspeed eth0}/s ${color #56073D}$alignr TOTAL ${color #DE0084}${totalup eth0}
${color #56073D}${upspeedgraph eth0 20,250 000000 #56073D}
          DOWN:                    $alignr UP:          
${color #56073D}Today: ${color #DE0084}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${color #56073D}${alignr}Today: ${color #DE0084}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}  
${color #56073D}Week:  ${color #DE0084}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${color #56073D}${alignr}Week:  ${color #DE0084}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'} 
${color #56073D}Month: ${color #DE0084}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${color #56073D}${alignr}Month: ${color #DE0084}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}

${color #56073D}${font Trebuchet MS:size=12}Drive Temp: Degrees C${font Trebuchet MS:size=11}
${execi 60 hddtemp /dev/sda | cut -c 6-28} C
${execi 60 hddtemp /dev/sdb | cut -c 6-28} C

```

---

### Post by Donjr on 2011-02-27
Dont want so much as how to set it up and what to use. What i am looking for is maybe a pre-made  generic configuration that is able to just (#) what i dont want and un (#) what i do. Something that is neat and not all the place like mine. If i try to move my config around to make it look neat i seem to screw it up  :-)

---

