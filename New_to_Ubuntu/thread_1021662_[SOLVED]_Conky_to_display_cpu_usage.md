---
title: "[SOLVED] Conky to display cpu usage"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-25
Anyone mind walking me through this?
I'd like conky to display my CPU usage (RAM, hdd, etc.) on desktop, and transparent (if possible)

---

### Post by spiderbatdad on 2008-12-25
have you seen the conky thread with hundreds of example files?
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Mine looks like this:```
background yes

use_xft yes

xftfont Bitstream Vera Sans Mono:size=9
xftalpha 0.8
update_interval 3.0
total_run_times 0

own_window yes
own_window_type override
own_window_transparent yes
own_window_colour hotpink
own_window_hints undecorated,below,skip_taskbar,sticky,skip_pager

double_buffer yes


minimum_size 280 5
draw_shades no
draw_outline no
draw_graph_borders yes
stippled_borders 8
border_margin 4

border_width 1
maximum_width 200
default_color black
default_shade_color black
default_outline_color black
alignment top_right
gap_x 10
gap_y 15
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
#use_spacer right

TEXT
${color #000000} ${alignc}${nodename} ${uptime_short}

${color #000000} CPU: ${color grey}$cpu%
${color #000000} ${cpugraph 16,140 000000 7f8ed3}
${color #000000} RAM: $color$mem/$memmax
${color #000000} ${membar 6,140}
${color #000000} Swap:$color$swap/$swapmax
${color #000000} ${swapbar 6,140}

${color #000000} ETH0 Down: $color${downspeed eth0}${alignr}
${color #000000} ${downspeedgraph eth0 16,140 000000 7f8ed3 150} k/s
${color #000000} ETH0 Up: $color${upspeed eth0}${alignr}
${color #000000} ${upspeedgraph eth0 16,140 000000 7f8ed3 18} k/s

${color #000000}  file systems:
${color #000000} / $color${fs_free /}
${color #000000} ${fs_bar 6,140 /}

${color #000000} Processes:$color $processes | $running_processes
${color} CPU usage: ${offset +55} ${color} PID:
${color #ddaa00} ${top name 1}${offset -20} ${top cpu 1} ${top pid 1}
${color #000000} ${top name 2}${offset -20} ${top cpu 2} ${top pid 2}
${color #000000} ${top name 3}${offset -20} ${top cpu 3} ${top pid 3}
${color #000000} ${top name 4}${offset -20} ${top cpu 4} ${top pid 4}

${color} MEM usage:
${color #ddaa00} ${top_mem name 1}${offset -20} ${top_mem mem 1} ${top_mem pid 1}
${color #000000} ${top_mem name 2}${offset -20} ${top_mem mem 2} ${top_mem pid 2}
${color #000000} ${top_mem name 3}${offset -20} ${top_mem mem 3} ${top_mem pid 3}
${color #000000} ${top_mem name 4}${offset -20} ${top_mem mem 4} ${top_mem pid 4}
${color} TCP Port Connections:
${color} ${tcp_portmon 6881 6999 count}


```It's pretty poor, but I haven't spent anytime trying to make it better. I almost never turn it on. What I do like about it is listing the top processes and their PID's

---

