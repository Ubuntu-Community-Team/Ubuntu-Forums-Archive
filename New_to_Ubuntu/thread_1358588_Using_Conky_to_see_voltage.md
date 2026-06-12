---
title: "Using Conky to see voltage?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Dark Aspect on 2009-12-18
Hello,

How can I setup conky to see CPU voltage? Can I use lm-sensors with conky?

---

### Post by northern lights on 2009-12-18
Variable: voltage_mv
Argument: (n)
Returns CPU #n's voltage in mV. CPUs are counted from 1. If omitted, the parameter defaults to 1.

Variable: voltage_v
Argument: (n)
Returns CPU #n's voltage in V. Otherwise same thing.

---

### Post by Dark Aspect on 2009-12-18
> **northern lights said:**
> Variable: voltage_mv
Argument: (n)
Returns CPU #n's voltage in mV. CPUs are counted from 1. If omitted, the parameter defaults to 1.

Variable: voltage_v
Argument: (n)
Returns CPU #n's voltage in V. Otherwise same thing.

????

---

### Post by northern lights on 2009-12-18
Adding```
${voltage_mv 1}
```to your conky config file (if you haven't fiddled with it /home/user/.conky.rc) will display your first processor's voltage.

---

### Post by Dark Aspect on 2009-12-18
> **northern lights said:**
> Adding```
${voltage_mv 1}
```to your conky config file (if you haven't fiddled with it /home/user/.conky.rc) will display your first processor's voltage.

Oh ok - thanks, I only have a single core so that will work.

Edit: Didn't work

---

### Post by northern lights on 2009-12-18
Post the section of your conky configuration around which you've put the above.

---

### Post by Dark Aspect on 2009-12-18
> **northern lights said:**
> Post the section of your conky configuration around which you've put the above.

Here is the file and the last one is the section:

```

on_bottom yes
own_window yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no
own_window_colour grey
own_window_transparent yes
double_buffer yes
use_spacer yes
use_xft yes
xftfont arial:size=10
update_interval 2.0
draw_shades no
draw_outline yes
draw_borders no
uppercase no
maximum_width 400
stippled_borders 3
border_margin 9
border_width 10
default_color white
own_window_colour brown
own_window_transparent yes
own_window_type override
alignment top_right
gap_x 10
gap_y 10

TEXT
$color
${color #A1C3FF}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
Distributor ID:     Ubuntu
Description:        Ubuntu 9.10
Release:             9.10
Codename:         Karmic Koala
Date: ${time %A,%d %B}
Time: ${time %k:%M:%S}${alignr} Uptime $uptime

${color #A1C3FF}CPU AMD +3200${hr 2}$color
${freq}MHz   Load: ${loadavg}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${top name 5} ${top pid 5}   ${top cpu 5}    ${top mem 6}
${top name 6} ${top pid 6}   ${top cpu 6}    ${top mem 6}

${voltage_mv 1}

${color #A1C3FF}MEMORY ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

${color #A1C3FF}WIRELESS NETWORK (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color #A1C3FF}FILE SYSTEMS ${hr 2}$color
Hard Drive         ${fs_used /}/${fs_size /}${alignr}${fs_bar 5,120 /}

${color #A1C3FF}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}
```

I placed it in the CPU section:

```
${color #A1C3FF}CPU AMD +3200${hr 2}$color
${freq}MHz   Load: ${loadavg}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${top name 5} ${top pid 5}   ${top cpu 5}    ${top mem 6}
${top name 6} ${top pid 6}   ${top cpu 6}    ${top mem 6}

${voltage_mv 1}
```

---

