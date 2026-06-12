---
title: "Conkey with new kernal 2.6.31-18"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by stalkier on 2010-01-10
I just updated my kernal to 2.6.31-18 and it messed my settings up somehow on my Conkey. The Conkey window is OVER other maximized windows. Here is my conkeymain

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 20
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
 
${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
 
${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
 
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 

```

---

### Post by dmillerct on 2010-01-10
> **stalkier said:**
> I just updated my kernal to 2.6.31-18 and it messed my settings up somehow on my Conkey. The Conkey window is OVER other maximized windows. Here is my conkeymain

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 20
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
 
${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
 
${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
 
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 

```

Change: ```
own_window_type override
```

To: ```
own_window_type desktop
```

In the future if you have a question regarding conky you can post it here: [ubuntuforums.org/showthread.php?t=281865&goto=newpost]("ubuntuforums.org/showthread.php?t=281865&goto=newpost")

There is an army of people just waiting to help out with conky problems or questions.

---

### Post by stalkier on 2010-01-10
> **dmillerct said:**
> Change: ```
own_window_type override
```

To: ```
own_window_type desktop
```

In the future if you have a question regarding conky you can post it here: [ubuntuforums.org/showthread.php?t=281865&goto=newpost]("ubuntuforums.org/showthread.php?t=281865&goto=newpost")

There is an army of people just waiting to help out with conky problems or questions.

Thanks so much. It has just been a long day at work and then the conkey problem. Worked like a charm. Thanks again.

---

### Post by dmillerct on 2010-01-10
> **stalkier said:**
> Thanks so much. It has just been a long day at work and then the conkey problem. Worked like a charm. Thanks again.

Not a problem, anytime.  ):P

---

