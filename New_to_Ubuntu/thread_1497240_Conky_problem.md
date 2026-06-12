---
title: "Conky problem"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by crazyavery4444 on 2010-05-30
anybody know how to get rid of this extra text? tried adding a dot in front of the rows of code but that didn't do anything.

---

### Post by SoFl W on 2010-05-30
That looks like part of the configuration section has been cut in pasted into the text section.  Look for those lines in the text section (under the "Fortune" header) and comment them out, if that works, remove them.

---

### Post by ankspo71 on 2010-05-30
Hi,
I think that is happening because that area of code appears below the "TEXT" line of your .conkyrc file. Anything below that area might end up in the display of conky. Here's mine so you can see what I mean below. Notice that any configurations in the TEXT area begin with a "$". I'm no expert on this, so if you post your .conkyrc other people may be able to correct it for you, or give you the best advice.

```
alignment bottom_right
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
double_buffer yes
draw_borders yes
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont Sans :size=8
gap_x 5
gap_y 60
minimum_size 160 5
net_avg_samples 2
no_buffers no
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type override
own_window_transparent yes
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
${color white}${time %I:%M %p},$color $alignr${color white}${time %a}, ${time %b} ${time %e}. ${time %Y}$color
$hr
${color white}RAM:$color $alignr${color white}$memperc%$color   ${color white}${membar 10,75}$color
${color white}Proc:$color $alignr${color white}$cpu%$color   ${color white}${cpubar 10,75}$color
${color white}CPU 1:$color $alignr${color white}${cpu cpu1}%$color   ${color white}${cpubar cpu1 10,75}$color
${color white}CPU 2:$color $alignr${color white}${cpu cpu2}%$color   ${color white}${cpubar cpu2 10,75}$color
$hr
${color white}Wireless Signal:$color $alignr${color green}${wireless_link_qual_perc wlan0}%$color
${color white}Download:$color $alignr${color white}${downspeed wlan0}$color
${color white}Upload:$color $alignr${color white}${upspeed wlan0}$color
```

Edit, I looked at your screenshot again and it looks like it might have two lines that say TEXT. I think there is only supposed to be one.

---

### Post by crazyavery4444 on 2010-05-30
I know my conky RC is a wreck, but yeah, I got rid of the displayed charectors by rebooting, but now the clock and calendar dont work right, everything is lit up.

ConkyRc...
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
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
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
gap_y 10

# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME PID CPU% MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

Root: ${fs_free_perc /}% ${fs_bar 6 /}$color
hda1: ${fs_free_perc /media/hda1}% ${fs_bar 6 /media/hda1}$color
hdb3: ${fs_free_perc /media/hdb3}% ${fs_bar 6 /media/hdb3}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

${color}I T ${color1}L ${color}I S ${color1}A S T I M E
${if_match ${exec date +"%M"} < 35}${if_match ${exec date +"%M"} >= 15}${if_match ${exec date +"%M"} < 20}${color}${endif}${endif}A ${color1}C ${if_match ${exec date +"%M"} >= 15}${if_match ${exec date +"%M"} < 20}${color}${endif}${endif}Q U A R T E R ${color1}D C
${if_match ${exec date +"%M"} >= 20}${if_match ${exec date +"%M"} < 30}${color}${endif}${endif}T W E N T Y ${if_match ${exec date +"%M"} >= 25}${if_match ${exec date +"%M"} < 30}${color}${endif}${else}${color1}${endif}${if_match ${exec date +"%M"} >= 5}${if_match ${exec date +"%M"} < 10}${color}${endif}${endif}F I V E ${color1}X
${if_match ${exec date +"%M"} >= 30}${if_match ${exec date +"%M"} < 35}${color}${endif}${endif}H A L F ${color1}B ${if_match ${exec date +"%M"} >= 10}${if_match ${exec date +"%M"} < 15}${color}${endif}${endif}T E N ${color1}F T O
${else}${if_match ${exec date +"%M"} >= 45}${if_match ${exec date +"%M"} < 50}${color}${endif}${endif}A ${color1}C ${if_match ${exec date +"%M"} >= 45}${if_match ${exec date +"%M"} < 50}${color}${endif}${endif}Q U A R T E R ${color1}D C
${if_match ${exec date +"%M"} >= 35}${if_match ${exec date +"%M"} < 45}${color}${endif}${endif}T W E N T Y ${if_match ${exec date +"%M"} < 40}${if_match ${exec date +"%M"} >= 35}${color}${endif}${else}${color1}${endif}${if_match ${exec date +"%M"} >= 55}${color}${endif}F I V E ${color1}X
H A L F B ${if_match ${exec date +"%M"} >= 50}${if_match ${exec date +"%M"} < 55}${color}${endif}${endif}T E N ${color1}F ${color}T O${color1}
${endif}${if_match ${exec date +"%M"} < 35}${if_match ${exec date +"%M"} >= 5}${color}${endif}${endif}P A S T ${color1}E R U ${if_match ${exec date +"%M"} < 35}${if_match ${exec date +"%I"} == 9}${color}${else}${color1}${endif}N I N E
${if_match ${exec date +"%I"} == 1}${color}${else}${color1}${endif}O N E ${if_match ${exec date +"%I"} == 6}${color}${else}${color1}${endif}S I X ${if_match ${exec date +"%I"} == 3}${color}${else}${color1}${endif}T H R E E
${if_match ${exec date +"%I"} == 4}${color}${else}${color1}${endif}F O U R ${if_match ${exec date +"%I"} == 5}${color}${else}${color1}${endif}F I V E ${if_match ${exec date +"%I"} == 2}${color}${else}${color1}${endif}T W O
${if_match ${exec date +"%I"} == 8}${color}${else}${color1}${endif}E I G H T ${if_match ${exec date +"%I"} == 11}${color}${else}${color1}${endif}E L E V E N
${if_match ${exec date +"%I"} == 7}${color}${else}${color1}${endif}S E V E N ${if_match ${exec date +"%I"} == 12}${color}${else}${color1}${endif}T W E L V E
${if_match ${exec date +"%I"} == 10}${color}${else}${color1}${endif}T E N ${else}${if_match ${exec date +"%I"} == 8}${color}${else}${color1}${endif}N I N E
${if_match ${exec date +"%I"} == 12}${color}${else}${color1}${endif}O N E ${if_match ${exec date +"%I"} == 5}${color}${else}${color1}${endif}S I X ${if_match ${exec date +"%I"} == 2}${color}${else}${color1}${endif}T H R E E
${if_match ${exec date +"%I"} == 3}${color}${else}${color1}${endif}F O U R ${if_match ${exec date +"%I"} == 4}${color}${else}${color1}${endif}F I V E ${if_match ${exec date +"%I"} == 1}${color}${else}${color1}${endif}T W O
${if_match ${exec date +"%I"} == 7}${color}${else}${color1}${endif}E I G H T${if_match ${exec date +"%I"} == 10}${color}${else}${color1}${endif} E L E V E N
${if_match ${exec date +"%I"} == 6}${color}${else}${color1}${endif}S E V E N${if_match ${exec date +"%I"} == 11}${color}${else}${color1}${endif} T W E L V E
${if_match ${exec date +"%I"} == 9}${color}${else}${color1}${endif}T E N ${endif}${color1}S E ${if_match ${exec date +"%M"} < 5}${color}${endif}O C L O C K
ON${color1}V${if_match ${exec date +"%u"} == 1}${color}${else}${color1}${endif}MONDAY${if_match ${exec date +"%u"} == 5}${color}${else}${color1}${endif}FRIDAY${if_match ${exec date +"%u"} == 4}${color}${else}${color1}${endif}THURSDAY${if_match ${exec date +"%u"} == 2}${color}${else}${color1}${endif}TUESDAY
${if_match ${exec date +"%u"} == 3}${color}${else}${color1}${endif}WEDNESDAY${if_match ${exec date +"%u"} == 7}${color}${else}${color1}${endif}SUNDAY${if_match ${exec date +"%u"} == 6}${color}${else}${color1}${endif}SATURDAY${color1}Q${if_match ${exec date +"%d"} >= 30}${color}${else}${color1}${endif}THIRTY
${if_match ${exec date +"%d"} >= 20}${if_match ${exec date +"%d"} < 30}${color}${endif}${endif}TWENTY${if_match ${exec date +"%d"} == 17}${color}SEVENTEEN${else}${if_match ${exec date +"%d"} == 7}${color}SEVEN${color1}TEEN${else}${if_match ${exec date +"%d"} == 27}${color}SEVEN${color1}TEEN${else}${color1}SEVENTEEN${endif}${endif}${endif}${if_match ${exec date +"%d"} == 14}${color}FOURTEEN${else}${if_match ${exec date +"%d"} == 4}${color}FOUR${color1}TEEN${else}${if_match ${exec date +"%d"} == 24}${color}FOUR${color1}TEEN${else}${color1}FOURTEEN${endif}${endif}${endif}${if_match ${exec date +"%d"} == 16}${color}SIXTEEN${else}${if_match ${exec date +"%d"} == 6}${color}SIX${color1}TEEN${else}${if_match ${exec date +"%d"} == 26}${color}SIX${color1}TEEN${else}${color1}SIXTEEN${endif}${endif}${endif}
${if_match ${exec date +"%d"} == 11}${color}${else}${color1}${endif}ELEVEN${if_match ${exec date +"%d"} == 13}${color}${else}${color1}${endif}THIRTEEN${color1}<${if_match ${exec date +"%d"} == 18}${color}EIGHTEEN${else}${if_match ${exec date +"%d"} == 8}${color}EIGHT${color1}EEN${else}${if_match ${exec date +"%d"} == 28}${color}EIGHT${color1}EEN${else}${color1}EIGHTEEN${endif}${endif}${color1}O${if_match ${exec date +"%d"} == 12}${color}${else}${color1}${endif}TWELVE
${if_match ${exec date +"%d"} == 10}${color}${else}${color1}${endif}TEN${if_match ${exec date +"%d"} == 3}${color}THREE${else}${if_match ${exec date +"%d"} == 23}${color}THREE${else}${color1}THREE${endif}${endif}${if_match ${exec date +"%d"} == 2}${color}TWO${else}${if_match ${exec date +"%d"} == 22}${color}TWO${else}${color1}TWO${endif}${endif}${color1}L${if_match ${exec date +"%d"} == 1} ${color}ONE${else}${if_match ${exec date +"%d"} ==21}${color}ONE${else}${if_match ${exec date +"%d"} == 31}${color}ONE${else}${color1}ONE${endif}${endif}${endif}${if_match ${exec date +"%d"} == 15}${color}${else}${color1}${endif}FIFTEEN${if_match ${exec date +"%d"} == 19}${color}NINETEEN${else}${if_match ${exec date +"%d"} == 9}${color}NINE${color1}TEEN${else}${if_match ${exec date +"%d"} == 29}${color}NINE${color1}TEEN${else}${color1}NINETEEN${endif}${endif}${endif}
${if_match ${exec date +"%d"} == 5}${color}${else}${if_match ${exec date +"%d"}== 25}${color}FIVE${else}${if_match ${exec date +"%d"} == 25}${color}FIVE${else}${color1}FIVE${endif}${endif}${color1}%${if_match ${exec date +"%m"} == 10}${color}${else}${color1}${endif}OCTOBER${if_match ${exec date +"%m"} == 5}${color}${else}${color1}${endif}MAY${if_match ${exec date +"%m"} == 1}${color}${else}${color1}${endif}JANUARY${if_match ${exec date +"%m"} == 7}${color}${else}${color1}${endif}JULY${if_match ${exec date +"%m"} == 6}${color}${else}${color1}${endif}JUNE
${if_match ${exec date +"%m"} == 9}${color}${else}${color1}${endif}SEPTEMBER${color1}Z${if_match ${exec date +"%m"} == 4}${color}${else}${color1}${endif}APRIL${if_match ${exec date +"%m"} == 3}${color}${else}${color1}${endif}MARCH${color1}I${if_match ${exec date +"%m"} == 11}${color}${else}${color1}${endif}NOVEMBER${color1}G
${if_match ${exec date +"%m"} == 8}${color}${else}${color1}${endif}AUGUST${color1}@${if_match ${exec date +"%m"} == 12}${color}${else}${color1}${endif}DECEMBER${color1}ONTHEYEAR${color}TWO${color1}G
${color}THOUSAND${color1}-${color}AND${color1}+${if_match ${exec date +"%y"} == 11}${color}${else}${color1}${endif}ELEVEN${color1}X${if_match ${exec date +"%y"} == 10}${color}${else}${color1}${endif}TEN${color1}T${if_match ${exec date +"%y"} == 9}${color}${else}${color1}${endif}NINE
```

---

