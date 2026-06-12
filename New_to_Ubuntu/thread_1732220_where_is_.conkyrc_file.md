---
title: "where is .conkyrc file?"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by Ditchdoc7893 on 2011-04-18
Hey guys!  I can't seem to find my .conkyrc file.  In a perfect world on a fresh install of 10.10 and fresh download of conky from the repository, where would I find it?  Much thanks!!

---

### Post by wolfen69 on 2011-04-18
First you need to run conky to create a .conkyrc file. Then you can go to your home folder and do Ctrl-H to see your hidden config files.

---

### Post by Ditchdoc7893 on 2011-04-18
did the above.  it appears not to be there.  anywhere else it could be?

---

### Post by wolfen69 on 2011-04-18
> **Ditchdoc7893 said:**
> it appears not to be there.  anywhere else it could be?

When your hidden files are showing in /home, check in .config or .local

I havn't used conky in a little while, but I know it's there.

---

### Post by Ditchdoc7893 on 2011-04-18
I assume its a text file of sorts.  That's the way I've always seen it in the past.  Am I correct in what I'm looking for?

---

### Post by nmaster on 2011-04-18
just use the find command:
```
sudo find / -iname .conkyrc
```

---

### Post by Zeno Izen on 2011-04-18
Apparently there isn't a conkyrc file after a fresh install...


[http://wiki.conky.be/index.php?title=FAQ#Where_did_the_default_.conkyrc_go.3F_I_ran_conky_and_looked_in_my_home_directory.2C_and_I_couldn.27t_find_it.21](http://wiki.conky.be/index.php?title=FAQ#Where_did_the_default_.conkyrc_go.3F_I_ran_conky_and_looked_in_my_home_directory.2C_and_I_couldn.27t_find_it.21)

---

### Post by Ditchdoc7893 on 2011-04-19
Thanks to all who have contributed!  After a lot of trial and error, I have at least figured out where I should be looking.  I do still have questions however.  As I've looked at many people's .conkyrc files that they have created and posted, I'm trying to learn how to work with conky.  I've tried several peoples' "code" for their respective desktop eye candy.  I've found something I like and worked it into what I want for my own desktop.  That being said, I would like to ask a question that for the life of me, I can't figure out how to remedy.  The output of the configuration on my desktop is a bit wider than I'd like it to be.  My primary question is how do I get it to be slimmer (as in the width specifically)? I will post my code below.  Any suggestions appreciated!  Thanks guys!!


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
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
# minimum_size 217 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
xftfont Sans Serif:size=8
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color red

own_window_colour purple
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 5
gap_y 5

# stuff after 'TEXT' will be formatted on screen

TEXT

$color
${color blue}SYSTEM ${hr 5}$color
$nodename $sysname $kernel on $machine
$uptime

${color blue}${pre_exec cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${hr 5}${color red}
${freq_dyn}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${color black}${cpugraph ff0000 5000a0}

${color blue}PROCESSES ${hr 5}$color
Process Number:  $processes       Running:  $running_processes

${color blue}HIGHEST CPU ${stippled_hr 1}$color
NAME${alignr 9}PID CPU% MEM%
${color 33ccff} {top name 1}${alignr 9}${top pid 1}${top cpu 1}    ${top mem 1}
${top name 2}${alignr 9}${top pid 2}${top cpu 2}${top mem 2}
${top name 3}${alignr 9}${top pid 3}${top cpu 3}${top mem 3}
${top name 4}${alignr 9}${top pid 4}${top cpu 4}${top mem 4}

${color 33ccff}HIGHEST MEM ${stippled_hr 1}$color
NAME${alignr 9}PID CPU% MEM%
${color 33ccff}{top_mem name 1}${alignr 9}${top_mem pid 1}${top_mem cpu 1} ${top_mem mem 1}
${top_mem name 2}${alignr 9}${top_mem pid 2}${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}${alignr 9}${top_mem pid 3}${top_mem cpu 3}${top_mem mem 3}
${top_mem name 4}${alignr 9}${top_mem pid 4}${top_mem cpu 4}${top_mem mem 4}

${color blue}RAM ${hr 5}$color
$mem / $memmax
$memperc%   ${membar 6}$color

${color blue}SWAP ${hr 5}$color
$swap / $swapmax
$swapperc%   ${swapbar 6}$color

${color blue}Networking:
${color red}Download ${color blue}Speed: ${color}${downspeed eth0} ${color red}k/s${color blue}  
${color black}${downspeedgraph eth0 32,195 ff0000 3300ff} 
${color red}Download ${color blue}Total: ${color red}${totaldown eth0}
------------------------- 
${color red}Upload   ${color blue}Speed: ${color}${upspeed eth0} ${color red}k/s
${color black}${upspeedgraph eth0 32,195 ff0000 3300ff}
${color red}Upload   ${color blue}Total: ${color red}${totalup eth0}

---

### Post by hayashi on 2011-04-19
> **Ditchdoc7893 said:**
> Thanks to all who have contributed!  After a lot of trial and error, I have at least figured out where I should be looking.  I do still have questions however.  As I've looked at many people's .conkyrc files that they have created and posted, I'm trying to learn how to work with conky.  I've tried several peoples' "code" for their respective desktop eye candy.  I've found something I like and worked it into what I want for my own desktop.  That being said, I would like to ask a question that for the life of me, I can't figure out how to remedy.  The output of the configuration on my desktop is a bit wider than I'd like it to be.  My primary question is how do I get it to be slimmer (as in the width specifically)? I will post my code below.  Any suggestions appreciated!  Thanks guys!!


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
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
# minimum_size 217 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
xftfont Sans Serif:size=8
uppercase no # set to yes if you want all text to be in uppercase

[B][U][I]# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10[/I][/U][/B]

# Default colors and also border colors, grey90 == #e5e5e5
default_color red

own_window_colour purple
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 5
gap_y 5

# stuff after 'TEXT' will be formatted on screen

TEXT

$color
${color blue}SYSTEM ${hr 5}$color
$nodename $sysname $kernel on $machine
$uptime

${color blue}${pre_exec cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${hr 5}${color red}
${freq_dyn}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${color black}${cpugraph ff0000 5000a0}

${color blue}PROCESSES ${hr 5}$color
Process Number:  $processes       Running:  $running_processes

${color blue}HIGHEST CPU ${stippled_hr 1}$color
NAME${alignr 9}PID CPU% MEM%
${color 33ccff} {top name 1}${alignr 9}${top pid 1}${top cpu 1}    ${top mem 1}
${top name 2}${alignr 9}${top pid 2}${top cpu 2}${top mem 2}
${top name 3}${alignr 9}${top pid 3}${top cpu 3}${top mem 3}
${top name 4}${alignr 9}${top pid 4}${top cpu 4}${top mem 4}

${color 33ccff}HIGHEST MEM ${stippled_hr 1}$color
NAME${alignr 9}PID CPU% MEM%
${color 33ccff}{top_mem name 1}${alignr 9}${top_mem pid 1}${top_mem cpu 1} ${top_mem mem 1}
${top_mem name 2}${alignr 9}${top_mem pid 2}${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}${alignr 9}${top_mem pid 3}${top_mem cpu 3}${top_mem mem 3}
${top_mem name 4}${alignr 9}${top_mem pid 4}${top_mem cpu 4}${top_mem mem 4}

${color blue}RAM ${hr 5}$color
$mem / $memmax
$memperc%   ${membar 6}$color

${color blue}SWAP ${hr 5}$color
$swap / $swapmax
$swapperc%   ${swapbar 6}$color

${color blue}Networking:
${color red}Download ${color blue}Speed: ${color}${downspeed eth0} ${color red}k/s${color blue}  
${color black}${downspeedgraph eth0 32,195 ff0000 3300ff} 
${color red}Download ${color blue}Total: ${color red}${totaldown eth0}
------------------------- 
${color red}Upload   ${color blue}Speed: ${color}${upspeed eth0} ${color red}k/s
${color black}${upspeedgraph eth0 32,195 ff0000 3300ff}
${color red}Upload   ${color blue}Total: ${color red}${totalup eth0}

I highlighted the areas you can try and fiddle around with for your liking! :D

Here's mine if you'd like to try it:
```
# conky configuration
# edited by Mark Buck (Kaivalagi) <m_buck@hotmail.com>

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=9

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 0
maximum_width 300

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window        yes
own_window_transparent    yes
own_window_type        override
own_window_hints    undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 10

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
use_spacer right

# colours
color1 white
# light blue
color2 6892C6
# orange
#E77320
color3 FC8820
# green
color4 78BF39
# red
color5 CC0000

text_buffer_size 2048

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT

${font openlogos:size=20}//${font font Bitstream Vera Sans Mono:style=Bold:size=20}${color Tan1}${color Ivory}linux${font openlogos:size=20}
              
${voffset -90}

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}system${font}  ${hr}${color1}
#$font${color DimGray}
$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}processors${font}  ${hr}${color1}
#$font${color DimGray}
CPU  $alignr ${cpu cpu1}% 
${cpubar cpu1}

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}memory${font}  ${hr}${color1}
#$font${color DimGray}
MEM $alignc $mem / $memmax $alignr $memperc%
$membar

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}hdd${font}  ${hr}${color1}
#$font${color DimGray}
/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
#/disk $alignc #${fs_used /media/disk} / #${fs_size /media/disk} $alignr #${fs_free_perc /media/disk}%
#${fs_bar /media/disk}
#/disk-1 $alignc #${fs_used /media/disk-1} / #${fs_size /media/disk-1} $alignr #${fs_free_perc /media/disk-1}%
#${fs_bar /media/disk-1}

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}processes${font}  ${hr}${color1}
#${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %

${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}weather${font}  ${hr}${color1}
${execpi 1800 conkyForecast --location=UKXX0085 --template=/usr/share/conkyforecast/example/conkyForecast.template}${voffset 8}${offset -5}${color3}${font StyleBats:style=CleanCut:size=12}q ${voffset -2}${font Bitstream Vera Sans Mono:style=Bold:size=11}music${font}  ${hr}${color1}
${voffset 3}${exec rhythmbox-client --print-playing --no-start}
```

---

### Post by rvchari on 2011-04-19
> **Ditchdoc7893 said:**
> Hey guys!  I can't seem to find my .conkyrc file.  In a perfect world on a fresh install of 10.10 and fresh download of conky from the repository, where would I find it?  Much thanks!!

if its not found in your home folder (hidden files are dot files which has a . prefix) easier way is to search for it in your home folder...

---

### Post by athenroy on 2011-06-13
Check your /etc/Conky folder, in it is conky.config which which will be your .conkyrc file.  You have to copy it to your home folder and re-name it .conkyrc .  That way, if you make a mistake, you still have the original in the /etc/conky folder.  Confusing, Huh??  I have been working all morning on mine!

---

