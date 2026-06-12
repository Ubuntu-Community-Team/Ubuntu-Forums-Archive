---
title: "conky and desktop icons"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by nick_goodfate on 2010-06-19
hello. how can i change the default position of new icons on desktop ? for example , when i download something, its placed at top left of desktop. i want it to be placed at top right. And that because i have my conky top left, and it covers any icon to that corner ... except there is an other solution, for example can i make conky go below icons ?
Here is my .conkyrc file in case you need it:
> # UBUNTU-CONKY
# A comprehensive conky script, configubrown for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (requibrown in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (brownuces flicker, may not work for everyone)
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
default_color white
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 70
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color brown}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
 
${color brown}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
 
${color brown}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
 
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color brown}NETWORK (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0 
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color brown}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
 
${color brown}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

---

### Post by gvhools on 2010-06-19
if you change this line: 
```
alignment top_left
```
 
with this :
 
```
alignment top_right
```
 
the conky she must be go on the right side in your desktop.

---

### Post by nick_goodfate on 2010-06-19
> **gvhools said:**
> if you change this line: 
```
alignment top_left
```
 
with this :
 
```
alignment top_right
```
 
the conky she must be go on the right side in your desktop.

i know ... but i want conky on the left side:p thnx pantws !

---

### Post by nick_goodfate on 2010-06-19
if i could make conky "part" of my wallpaper would be perfect. anyone know how ?

---

### Post by nick_goodfate on 2010-06-19
any idea ?

---

### Post by Windows Nerd on 2010-06-19
I'm afraid you'll probably have to move your conky to the right side. Just access anything hidden by your conky on your desktop through your filemanager. If you MUST have it on the left side (I like having it on the right and think it looks better that way, though that is my opinions) then I have no idea...I tried Google and [this]("http://www.linuxquestions.org/questions/programming-9/nautilus-desktop-icons-righ-to-left-402227/") one guy had the same problem you...nothing really showed up on this forum.

Scott

---

### Post by 4Orbs on 2010-06-19
```
# Gap between borders of screen and text
gap_x 10
gap_y 70
```

Open your .conkyrc in the text editor and locate the above section. Change these numbers to move conky to the left or right, or up and down. These are the number of pixels of empty space (gap). Save the file after each change, then restart conky to see the change.

---

### Post by nick_goodfate on 2010-06-19
thank you for your replies ! after 15 hours of conky configuring i didnt find any solution to that ... at least now i can write a conkyrc file from scratch, exactly as i want it (except from making it part of my wallpaper) ! :p

---

