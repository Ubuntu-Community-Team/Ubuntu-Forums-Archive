---
title: "Another Conky Mess"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Jolzath on 2009-06-07
All right so, I am running Ubuntu (no Compiz, just ''vanilla'' ubuntu) everytime I pull firefox (or anything on top of it) it does something like this. (Image)



 [IMG]http://g.imagehost.org/view/0091/Screenshot-1[/IMG]

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
gap_y 10
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color white}SYSTEM ${hr 2}$color
$nodename system running $sysname
 
${color white}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
${color white} TOP 5 ${hr 2}$color
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${top name 5} ${top pid 5}   ${top cpu 5}    ${top mem 5}
 
${color white}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
 
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/Mobile Mars}%   ${fs_bar 6 /media/Mobile Mars}$color
 
${color white}NETWORK (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0 
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}

${color white}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

${color1}$hr
${voffset -3}$alignc CURRENT CONDITIONS 
${voffset -7}$hr $color
${execi 3600 perl ~/scripts/weather.pl 37138 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl 37138 f t}
${voffset -15}$alignr${offset -60}${font weather:size=45}${execi 3600 perl ~/scripts/weather.pl 37138 f cp}$font
${voffset -10}${color1}$hr
```

[IMG]http://g.imagehost.org/dl/167b04241df795854d2305b59534e12f/0091/Screenshot-1.png[/IMG]

---

### Post by Jolzath on 2009-06-07
Help would be nice... Please *bump*

---

### Post by H2SO_four on 2009-06-07
Not to sound rude, but I'm not really sure if you have even asked a question.  Try to explain what the unwanted behaviour is, then ask for help.

---

### Post by solitaire on 2009-06-07
> **Jolzath said:**
> Help would be nice... Please *bump*


Can you repost your images....

The didn't come through..

---

### Post by Jolzath on 2009-06-07
> **H2SO_four said:**
> Not to sound rude, but I'm not really sure if you have even asked a question.  Try to explain what the unwanted behaviour is, then ask for help.

Um...(As far as the question, I assume that it was evident that I was asking for help, on how to fix Conky to work on the GNOME desktop.)

[quote=jolzath] (Original Post) everytime I pull firefox (or anything on top of it) it does something like this. (Image) [/quote]I understand the image did not go though so I will post it again. 
[IMG]http://www.stgaming.org/imagehost/images/1244404860.png[/IMG]

---

### Post by solitaire on 2009-06-07
try changing the following:

```

# Minimum size of text area
# minimum_size 250 5
```to
```

# Max window size
maximum_width 300

# Minimum size of text area
minimum_size 250 300

```

---

### Post by Jolzath on 2009-06-07
> **solitaire said:**
> try changing the following:

```

# Minimum size of text area
# minimum_size 250 5
```to
```

# Max window size
maximum_width 300

# Minimum size of text area
minimum_size 250 300

```

Still freezes(?) and disappears.

---

### Post by solitaire on 2009-06-07
You didn't say anything about Freezing and disappearing in your posts!!

We're not mind readers!

Please explain EXACTLY what happens.

---

### Post by Jolzath on 2009-06-07
> **solitaire said:**
> You didn't say anything about Freezing and disappearing in your posts!!

We're not mind readers!

Please explain EXACTLY what happens.

Everytime I start Corky it goes well. Then I place something full screen or over that section, and then Corky freezes and disappears in that area (As the image has shown) after a while (roughly 2 min) it comes back only to repeat what has happened.

(Sorry for earlier, I was a bit angry as it worked before perfectly till now. Nothing was changed or anything)

---

### Post by psychoelf on 2009-07-01
I've been having this issue lately.  Happens mostly after using suspend, but also without.  If I watch a movie in VLC or open firefox, Conky will disappear after I close the window that covered it and then reappear after a few minutes.  

Here is my conkyrc:

```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

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
use_spacer none

TEXT
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font Webdings:size=16}~${font}  Battery: ${battery_percent BAT0}% ${alignr}${battery_bar 8,60 BAT0}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %H:%M}${font}
${alignc}${time %A %d %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 3465A4 729FCF}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 3465A4 729FCF}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 3465A4 729FCF}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 3465A4 729FCF}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 3465A4 729FCF}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 3465A4 729FCF}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}
EMAIL ${hr 2}
${voffset -8}${font Martin Vogel's Symbols:size=19}B${font}  Gmail: ${alignr}${font DejaVu Sans:style=Bold:size=8}${execi 600 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --username=###### --password=###### --ssl}${font} New email(s)

WEATHER ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=37091 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=37091 --datatype=HT --imperial }${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=1 --shortweekday } ${alignc 8}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=2 --shortweekday } ${alignc -29}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=37091 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=4 --hideunits --centeredwidth=3}${font}
${else}${if_existing /proc/net/route eth0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=37091 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=37091 --datatype=HT --imperial }${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=37091 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=4 --hideunits --centeredwidth=3}${font}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=37091 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=37091 --datatype=HT --imperial }${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=37091 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=37091 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=37091 --datatype=HT --imperial --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=37091 --datatype=LT --imperial --startday=4 --hideunits --centeredwidth=3}${font}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Weather Unavailable
${endif}
```

---

### Post by ~sHyLoCk~ on 2009-07-01
Can you align it to another part of the desktop, say bottom_left? Does it work then?

---

### Post by psychoelf on 2009-08-09
Moved it to top_left and after 5 minutes program windows make it disappear.  If I let it sit for a bit (could be seconds could be minutes) it comes back.

Any other ideas?

Also...running an ATI HD2600 mobility and completely removed compiz (as compiz caused even more issues).

---

### Post by psychoelf on 2009-08-11
Updated my conky to 1.7.1.1 and used a new script and all seems to be fine for now. 
Not sure what happened.  Been going good for 2 whole days.

I included a screenshot and the .conkyrc.  Just replace the #####'s under email and weather with your info if you want it.

```
use_xft yes
xftfont Liberation Sans:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

minimum_size 185 0
maximum_width 185

default_color cccccc
draw_shades no

color0 white
color1 E07A1F
color2 white

alignment top_right
gap_x 25
gap_y 50

no_buffers no
net_avg_samples 2

override_utf8_locale yes

no_buffers yes

TEXT
${font Liberation Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
${voffset 2}${color0}${font OpenLogos:size=16}u${font}${color}   Kernel:  ${alignr}${color2}${kernel}${color}
${color0}${font StyleBats:size=16}A${font}${color}   CPU1: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu1}%${font} ${alignr}${voffset -2}${color0}${font Weather:size=14}y${font}${color} ${voffset -3}${font Liberation Sans:style=Bold:size=8}${color1}${execi 30 sensors -f | grep 'Core0 Temp' | cut -c14-16}°F${color}${font}  ${color2}${cpubar cpu1 8,50}${color}
${color0}${font StyleBats:size=16}A${font}${color}   CPU2: ${font Liberation Sans:style=Bold:size=8}${color1}${cpu cpu2}%${font} ${alignr}${voffset -2}${color0}${font Weather:size=14}y${font}${color} ${voffset -3}${font Liberation Sans:style=Bold:size=8}${color1}${execi 30 sensors -f | grep 'Core1 Temp' | cut -c14-16}°F${color}${font}  ${color2}${cpubar cpu2 8,50}${color}
${color0}${font StyleBats:size=16}g${font}${color}   RAM: ${font Liberation Sans:style=Bold:size=8}${color1}$memperc%${color}${font} ${alignr}${color2}${membar 8,60}${color}
${color0}${font StyleBats:size=16}j${font}${color}   SWAP: ${font Liberation Sans:style=Bold:size=8}${color1}$swapperc%${color}${font} ${alignr}${color2}${swapbar 8,60}${color}
${font Webdings:size=16}~${font}${color}  Battery: ${font Liberation Sans:style=Bold:size=8}${color1}${battery_percent BAT0}%${color}${font} ${alignr}${color2}${battery_bar 8,60 BAT0}${color}
${color0}${font StyleBats:size=16}q${font}${color}   Uptime: ${alignr}${color2}${uptime}${color}

${font Liberation Sans:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -6}${goto 28}${font Arial Black:size=38}${color2}${time %H}${color}${font}${voffset -28}${font Liberation Sans:style=Bold:size=11}${color2}${time :%M}${time :%S}${color}${font}
${voffset -3}${goto 100}${font Liberation Sans:style=Bold:size=8}${color2}${time %A}${color}${font}
${voffset -1}${goto 100}${time %d %B %Y}

${font Liberation Sans:style=Bold:size=8}HD $stippled_hr${font}
${execpi 30 ~/.scripts/hd_default.py}

${font Liberation Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
${if_existing /proc/net/route wlan0}
${voffset -6}${color0}${font PizzaDude Bullets:size=14}O${font}${color}   Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} kb/s ${alignr}${upspeedgraph wlan0 8,60 E07A1F FAA546}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}U${font}${color}   Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} kb/s ${alignr}${downspeedgraph wlan0 8,60 E07A1F FAA546}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}N${font}${color}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}T${font}${color}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}Z${font}${color}   Signal: ${font Liberation Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}a${font}${color}   Local ip: ${alignr}${color2}${addr wlan0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}b${font}${color}   Public ip: ${alignr}${color2}${execi 10800 ~/.scripts/ip.sh}${color}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${color0}${font PizzaDude Bullets:size=14}O${font}${color}   Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} kb/s ${alignr}${upspeedgraph eth0 8,60 E07A1F FAA546}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}U${font}${color}   Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} kb/s ${alignr}${downspeedgraph eth0 8,60 E07A1F FAA546}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}N${font}${color}   Upload: ${alignr}${color2}${totalup eth0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}T${font}${color}   Download: ${alignr}${color2}${totaldown eth0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}a${font}${color}   Local ip: ${alignr}${color2}${addr eth0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}b${font}${color}   Public ip: ${alignr}${color2}${execi 10800 ~/.scripts/ip.sh}${color}
${endif}${else}${if_existing /proc/net/route ppp0}
${voffset -6}${color0}${font PizzaDude Bullets:size=14}O${font}${color}   Up: ${font Liberation Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} kb/s ${alignr}${upspeedgraph ppp0 8,60 E07A1F FAA546}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}U${font}${color}   Down: ${font Liberation Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} kb/s ${alignr}${downspeedgraph ppp0 8,60 E07A1F FAA546}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}N${font}${color}   Upload: ${alignr}${color2}${totalup ppp0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}T${font}${color}   Download: ${alignr}${color2}${totaldown ppp0}${color}
${voffset 4}${color0}${font PizzaDude Bullets:size=14}a${font}${color}   Local ip: ${alignr}${color2}${addr ppp0}${color}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}   Network Unavailable
${endif}
${font Liberation Sans:style=Bold:size=8}EMAIL $stippled_hr${font}
${color0}${font Webdings:size=16}ô${font}   Gmail:  ${color1}${font}${execi 600 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --username=###### --password=###### --ssl} 

${color}${font Liberation Sans:style=Bold:size=8}WEATHER $stippled_hr${font}
${if_existing /proc/net/route wlan0}
${execpi 10800 conkyForecast --location=##### -t ~/.scripts/conkyForecast.template}
${else}${if_existing /proc/net/route eth0}
${execpi 10800 conkyForecast --location=##### -t ~/.scripts/conkyForecast.template}
${endif}${else}${if_existing /proc/net/route ppp0}
${execpi 10800 conkyForecast --location=##### -t ~/.scripts/conkyForecast.template}
${endif}${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}   Weather Unavailable${endif}
```

---

### Post by psychoelf on 2009-08-11
Heres the .deb.  I don't think this was the fix as my previous script still blanked out, but thought I'd include it also.

Also, you can download the source for the script from gnome-look.  I think its the new conky colors.

---

### Post by tedrampart on 2009-08-17
yea I just noticed this issue too, just recently switched back to gnome and loaded up my old conky scripts.  I'll try the new version of conky and post back on anything.

edit - just tried it, and it worked for a few minutes, and then it went blank and didn't work

---

