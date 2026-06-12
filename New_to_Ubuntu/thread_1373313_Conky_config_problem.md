---
title: "Conky config problem"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Shippou on 2010-01-05
Good morning people!

Before a system upgrade, my conky works fine. But after the upgrade, it is somewhat messed up.

What my problem is that it does not properly read the config file. 

Here is my .conkyrc (on the home folder):
```

# conky configuration
#
# The list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.
#
# For ideas about how to modify conky, please see:
# http://crunchbanglinux.org/forums/topic/59/my-conky-config/
#
# For help with conky, please see:
# http://crunchbanglinux.org/forums/topic/2047/conky-help/
#
# Enjoy! :)
##############################################
#  Settings
##############################################
background yes
use_xft yes
xftfont Sans:size=8
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type dock
own_window_hints decorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 240
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color black
default_outline_color white
alignment bottom_right
gap_x 12
gap_y 12
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
##############################################
#  Output
##############################################
TEXT
SYSTEM INFO:
${hr}
Host:$alignr$nodename
Uptime:$alignr$uptime
RAM:$alignr$mem/$memmax
Swap usage:$alignr$swap/$swapmax
Disk usage:$alignr${fs_used /}/${fs_size /}
CPU usage:$alignr${cpu cpu0}%
Battery Remaining:$alignr${battery_bar 10, 50, bat1}
$laptop_mode

SHORTCUT KEYS:
${hr}
Alt+F2$alignr Run Dialog
Alt+F3$alignr Alt Menu
Super+space$alignr Main Menu
Super+tab$alignr Client Menu
Super+t$alignr Terminal
Super+f$alignr File Manager
Super+e$alignr Editor
Super+m$alignr Media Player
Super+w$alignr Web Browser
Super+c$alignr Clock
Super+l$alignr Lock Screen
Super+v$alignr Volume Control
Super+u$alignr System Update
Super+x$alignr Logout
PrtSc$alignr Screenshot


```

Attached is a screenshot of conky running.

Any suggestions?

Conky is version 1.7.1,1.

---

### Post by stoogiebuncho on 2010-01-07
what do you want it to do that it isn't doing?

---

