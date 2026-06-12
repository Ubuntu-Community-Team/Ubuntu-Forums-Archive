---
title: "Conky is Blocking Workspace"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by greendragons on 2011-06-04
Hello, i m using Ubuntu 11.04, installed conky recently but it's acting crazy..it's blocking up my desktop...
[IMG]http://imageshack.us/photo/my-images/543/screenshot1ax.png/[/IMG]
[http://imageshack.us/photo/my-images/543/screenshot1ax.png/](http://imageshack.us/photo/my-images/543/screenshot1ax.png/)
Thnx!!

---

### Post by linuxman94 on 2011-06-04
There should be an option in the config file named background.  Make sure it reads like this:
```
background yes
```

---

### Post by m_duck on 2011-06-04
I can't actually see the image.

@linuxman94: that option forks the conky *process* to the background and is not related to its display as far as I know.

The usual culprit for Conky being obnoxious is the own_window_type (and related own_window*) variable(s). If you could post your ~/.conkyrc I'm sure someone could take a look at it.

---

### Post by greendragons on 2011-06-04
Background is set to yes....as it was before when i configured the file...

---

### Post by greendragons on 2011-06-04
# Original conkyrc file by TheRob @ gnome-look.org
# [http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210](http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210)
# modifications by truckerbomb:
# wrote shuffleconky.py to shuffle certain sections in and out
# date with suffix provided by python script conkysuffix.py
# network section appears only when connection present
# detect presence of USB thumbdrive and add to Filesystem section when mounted
# added a GMail checker, gmail_parser.py
# Make the following changes below:
# replace /YOUR/PATH/TO/filename with correct paths
# replace YOURGMAILUSERNAME/PASSWORD with your info
# replace /media/YOURTHUMBDRIVE with your thumbdrives folder name in /media
# if you use wifi replace all "ppp0"'s in NETWORK section with "eth0"


background yes
text_buffer_size 2000
font Snap.se:size=8
xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 1000 1000
maximum_width 280
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 6
gap_y 25
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer none

TEXT
${font Matrix:style=Bold:pixelsize=56}${color 00CF04}${alignc}${time %H:%M:%S}${font Snap.se:size=8}

${alignc}${time %A}, ${time %B %e}${texeci 600 python /home/kodedozer/Documents/Downloads/Themes/shuffleconkyv0.1/conkysuffix.py} ${time %Y}
${font Matrix:style=Bold:pixelsize=12}SYSTEM${font Snap.se:size=8} ${hr 1 }

Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Battery:${alignr}${battery}

CPU       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph cccccc 00CF04}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
Highest CPU $alignr CPU% MEM%
${hr 1}
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${hr 1}
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

WIFI (${addr wlan0})  ${hr 1} ${fs_free /} / ${fs_size /}
${wireless_essid wlan0} ${wireless_link_bar 6 wlan0}
Down:${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 20,120 00CF04 00CF04} ${alignr}${upspeedgraph wlan0
20,120}
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${font Matrix:style=Bold:pixelsize=12}FILESYSTEM${font Snap.se:size=8} ${hr 1 }

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Storage: ${alignr}${fs_free /storage} / ${fs_size /storage}
${fs_bar 4 /storage}${if_mounted /media/YOURTHUMBDRIVE}
Thumbdrive: ${alignr}${fs_free /media/YOURTHUMBDRIVE} / ${fs_size /media/STORE'N'GO}
${fs_bar 4 /media/YOURTHUMBDRIVE}${endif}
${if_up ppp0}
${font Matrix:style=Bold:pixelsize=12}NETWORK${font Snap.se:size=8} ${hr 1 }

Interface:${alignr}ppp0
IP Address:$alignr${addr ppp0}
Down ${downspeed ppp0} k/s ${alignr}Up ${upspeed ppp0} k/s
${downspeedgraph ppp0 25,107 cccccc ffffff} ${alignr}${upspeedgraph ppp0 25,107 cccccc ffffff}
Total ${totaldown ppp0} ${alignr}Total ${totalup ppp0}{$endif}

---

### Post by greendragons on 2011-06-04
# Original conkyrc file by TheRob @ gnome-look.org
# [http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210](http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210)
# modifications by truckerbomb:
# wrote shuffleconky.py to shuffle certain sections in and out
# date with suffix provided by python script conkysuffix.py
# network section appears only when connection present
# detect presence of USB thumbdrive and add to Filesystem section when mounted
# added a GMail checker, gmail_parser.py
# Make the following changes below:
# replace /YOUR/PATH/TO/filename with correct paths
# replace YOURGMAILUSERNAME/PASSWORD with your info
# replace /media/YOURTHUMBDRIVE with your thumbdrives folder name in /media
# if you use wifi replace all "ppp0"'s in NETWORK section with "eth0"


background yes
text_buffer_size 2000
font Snap.se:size=8
xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 1000 1000
maximum_width 280
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 6
gap_y 25
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer none

TEXT
${font Matrix:style=Bold:razz:ixelsize=56}${color 00CF04}${alignc}${time %H:%M:%S}${font Snap.se:size=8}

${alignc}${time %A}, ${time %B %e}${texeci 600 python  /home/kodedozer/Documents/Downloads/Themes/shuffleconkyv0.1/conkysuffix.py}  ${time %Y}
${font Matrix:style=Bold:razz:ixelsize=12}SYSTEM${font Snap.se:size=8} ${hr 1 }

Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Battery:${alignr}${battery}

CPU       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph cccccc 00CF04}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
Highest CPU $alignr CPU% MEM%
${hr 1}
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${hr 1}
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

WIFI (${addr wlan0})  ${hr 1} ${fs_free /} / ${fs_size /}
${wireless_essid wlan0} ${wireless_link_bar 6 wlan0}
Down:${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 20,120 00CF04 00CF04} ${alignr}${upspeedgraph wlan0
20,120}
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${font Matrix:style=Bold:razz:ixelsize=12}FILESYSTEM${font Snap.se:size=8} ${hr 1 }

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Storage: ${alignr}${fs_free /storage} / ${fs_size /storage}
${fs_bar 4 /storage}${if_mounted /media/YOURTHUMBDRIVE}
Thumbdrive: ${alignr}${fs_free /media/YOURTHUMBDRIVE} / ${fs_size /media/STORE'N'GO}
${fs_bar 4 /media/YOURTHUMBDRIVE}${endif}
${if_up ppp0}
${font Matrix:style=Bold:razz:ixelsize=12}NETWORK${font Snap.se:size=8} ${hr 1 }

Interface:${alignr}ppp0
IP Address:$alignr${addr ppp0}
Down ${downspeed ppp0} k/s ${alignr}Up ${upspeed ppp0} k/s
${downspeedgraph ppp0 25,107 cccccc ffffff} ${alignr}${upspeedgraph ppp0 25,107 cccccc ffffff}
Total ${totaldown ppp0} ${alignr}Total ${totalup ppp0}{$endif}

---

### Post by Dondermans on 2011-06-04
If I am not mistaken, this is a problem with Conky not being 'transparent'. If so, please find a possible solution in message [_#5_]("http://ubuntuforums.org/showpost.php?p=10586335&postcount=5") of the thread [_'What's the proper setting for Conky's own_window_type?_]("http://ubuntuforums.org/showthread.php?t=1689954")'.

---

### Post by greendragons on 2011-06-04
Problem solved....i changed own_window_type normal
n it's working fine....

---

