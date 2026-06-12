---
title: "getting my conky to stay in place"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by jmcgovern on 2009-12-02
Hey all

I'm having a small problem with my conky.  One of the things in my config file is to show the top 5 running processes.  The problem is, that when this portion updates, it can change the width of Conky, which causes the background behind it to get redrawn, which makes the background behind conky out of sync with the rest of the desktop and makes the image appear disjointed at the edges of conky.  anyone know how to fix this.  Can the width be fixed to something that won't resize?

here's my .conkyrc
```

use_xft yes
xftfont OpenLogos DejaVu Sans Mono:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_class Conky

minimum_size 180 0
maximum_width 400

default_color white
draw_shades no

color0 white
color1 E07A1F
color2 green

alignment top_right
gap_x 20
gap_y 40

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes

TEXT
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU: ${cpu cpu1}% ${alignr}${cpugraph cpu1 8,50}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,50}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,50}
${font StyleBats:size=16}8${font}      Update: ${alignr}${execi 600 aptitude search "~U" | wc -l | tail} package(s)
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

HDD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_used_perc /}%-${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,50 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_used_perc /home}%-${fs_used /home}/${fs_size /home} ${alignr}${fs_bar 8,50 /home}

${if_existing /proc/net/route eth0}
Networking ${hr 2}
${voffset 2}eth0${alignr}${addr eth0}
${voffset 2}Down: ${downspeed eth0} k/s
${alignr}${downspeedgraph eth0 20,150 88aadd 88aaee}
${voffset 2}Up: ${upspeed eth0} k/s
${alignr}${upspeedgraph eth0 20,150 88aadd 88aaee}
${endif}

TIME ${hr 2}
${voffset 2}${font Arial Black:size=10}${time %H:%M}${alignr}${time %d %B %Y}${font}
${voffset 1}
${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/ /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignr} /' | sed /" $DJS "/s/" $DJS "/" "'${color2}'"$DJS"'${color0}'" "/}


${color #FFFFFF}TOP 5 PROCESSES ${hr 2}$color
${color #ffccaa}NAME             ${alignr}  PID      CPU      MEM
${color white}1. ${top name 1}${alignr}${top pid 1}   ${top cpu 1}   ${top mem 1}$color
2. ${top name 2}${alignr}${top pid 2}   ${top cpu 2}   ${top mem 2}
3. ${top name 3}${alignr}${top pid 3}   ${top cpu 3}   ${top mem 3}
4. ${top name 4}${alignr}${top pid 4}   ${top cpu 4}   ${top mem 4}
5. ${top name 5}${alignr}${top pid 5}   ${top cpu 5}   ${top mem 5}

${if_existing /proc/net/route eth0}
WEATHER ${hr 2}
${voffset 2}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USKS0319  --datatype=WF}${font}
${voffset -50}${font Weather:size=40}${font} ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=UPXX0054 --datatype=HT --imperial}${font}


${voffset 0}${alignc 48}${execpi 600 conkyForecast --location=USKS0319 --datatype=DW --startday=1 --shortweekday} ${alignc 6}${execpi 600 conkyForecast --location=USKS0319 --datatype=DW --startday=2 --shortweekday} ${alignc -38}${execpi 600 conkyForecast --location=USKS0319  --datatype=DW --startday=3 --shortweekday} ${alignc -80}${execpi 600 conkyForecast --location=USKS0319 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=USKS0319 --datatype=WF --startday=1 --endday=4 --spaces=2}${font}
${voffset 0}${font DejaVu Sans:size=8}${alignc 50}${execpi 600 conkyForecast --location=USKS0319 --datatype=HT --imperial --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=RSXX0063 --datatype=LT --imperial --startday=1 --hideunits --centeredwidth=3} ${alignc -12}${execpi 600 conkyForecast --location=USKS0319 --datatype=HT --imperial --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USKS0319 --datatype=LT --imperial  --startday=2 --hideunits --centeredwidth=3} ${alignc -48}${execpi 600 conkyForecast --location=USKS0319 --datatype=HT --imperial --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=RSXX0063 --datatype=LT --imperial --startday=3 --hideunits --centeredwidth=3} ${alignr 2}${execpi 600 conkyForecast --location=USKS0319 --datatype=HT --imperial --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=USKS0319 --datatype=LT --imperial --startday=4 --hideunits --centeredwidth=3}${font}
${endif}
```

---

### Post by pbrane on 2009-12-02
try setting your minimum_size X parameter and your maximum_width to the same value.
e.g., 
```

minimum_size 400 0
maximum_width 400

```

in my .conkyrc I only use **minimum_size 5 5** (no maximum_width) and I don't have any resizing issues.

---

### Post by jmcgovern on 2009-12-02
Perfect! thanks. had to play with exactly how wide but i got it. solved

---

