---
title: "Conky Freezing Other Windows In Background"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by wpwend42 on 2011-08-20
I'm not sure how else to explain it, so I have attached a screengrab. I have gotten Conky to work after a lot of tinkering, but now any other window open gets "frozen" in the background when I try to minimize it. 

How do I fix this problem? Conky is really neat, but obviously this is a bit problematic :(

[IMG]http://wpwend.com/images/desktop082011.png[/IMG]

---

### Post by zealibib slaughter on 2011-08-20
Are any errors being posted when you start conky?

---

### Post by wpwend42 on 2011-08-20
When I load Conky in the terminal, I get this afterwards:

Conky: desktop window (a5) is root window
Conky: window type - desktop
Conky: drawing to created window (0x5c00001)
Conky: drawing to double buffer

and it just sits on that.

---

### Post by zealibib slaughter on 2011-08-20
Do you have conky set to own window?
post your conkyrc file.

---

### Post by wpwend42 on 2011-08-20
alignment top_right
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=12
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_class Conky
own_window_type desktop
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
${scroll 16 $nodename - $sysname $kernel on $machine | }
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} ${color grey} - Down:$color ${downspeed eth0}
$hr
${color grey}Name              PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}

---

### Post by zealibib slaughter on 2011-08-20
you have two window_type settings, one ignore and one desktop.  This may be causing the problem, try commenting out one or the other with #.

---

### Post by wpwend42 on 2011-08-20
Removing own_window_type desktop seems to have fixed it! Thanks!

---

### Post by zealibib slaughter on 2011-08-20
Cool, glad I could help.

---

