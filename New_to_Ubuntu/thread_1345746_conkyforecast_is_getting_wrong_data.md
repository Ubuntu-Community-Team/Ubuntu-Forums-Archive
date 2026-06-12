---
title: "conkyforecast is getting wrong data"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by jmcgovern on 2009-12-04
I've been using ConkyForecast to put weather information on my desktop. However,the data I've been getting is wildly inaccurate.  I use the standard conkyforecast, drawing from Weather.com.  Right now, my conky says its 52 deg F (I;m in US).   It's actually 13, as verified on TV and my 1-click weather extension for Firefox, which, oddly, draws from the same source (weather.com)  I've verified the location code just now so it's not pointing to the wrong place..

---

### Post by lackoblacko on 2009-12-04
im gonna take a wild guess that maybe it is actually 52 deg C and not F and the units are wrong.  post your conkyforecast script.

---

### Post by jmcgovern on 2009-12-04
i checked the units.  I've used the proper switches everywhere i can think of.....

my .conkyrc
```
use_xft yes
xftfont OpenLouse_xft yes
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

minimum_size 250
maximum_width 250


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
${endif}gos DejaVu Sans Mono:size=8

update_interval 1
total_run_times 0
double_buffer yes
text_buffer_size 2048

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_class Conky

minimum_size 250
maximum_width 250


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

and the config file
```

# config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = USKS0319
XOAP_PARTNER_ID = 1074448335 
XOAP_LICENCE_KEY = cdb2dd4f18df201c
MAXIMUM_DAYS_FORECAST = 7
#BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
```

---

### Post by lackoblacko on 2009-12-04
one thing i noticed in conkyForecast.py
```

LOCALE = USKS0319

```
should be
```

LOCALE = en

```

or left blank. LOCALE defines language output. see if that works and fixes it

---

### Post by jmcgovern on 2009-12-04
I tried both options. no joy.  tells me it's 48 F outside.  when it's actually about 20.  Even if it were trying to display Celsius it would be wrong because if it were it'd be a negative number.

---

### Post by lackoblacko on 2009-12-04
all i can think of is your location code might be wrong because based on the location you provided, the conversion is correct from the xoap weather.com service. your location is register as Lawrence, Kansas based on your script.

---

### Post by jmcgovern on 2009-12-05
Well, whatever was happening, it seems to be fixed, at least today...gonna mark as solved, hopefully it wont reappear.

---

### Post by fixed-gear on 2010-05-29
Apologies to chime in on an old and 'solved' thread - I'm a #! user and don't spend much time on the ubuntu forums.

@jmcgoven: there is some information missing from the last line of your config file. You're still using the generic script:

BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m

What's missing is the specific <LOCATION>, <XOAP_PARTNER_ID>, and <XOAP_LICENCE_KEY>. 

In your case these are: USKS0319, 1074448335, and cdb2dd4f18df201c respectively. Also remove the < > around each of these. For you this line should read:

BASE_XOAP_URL = [url]http://xml.weather.com/weather/local/USKS0319?cc=*&dayf=10&link=xoap&prod=xoap&par=1074448335&key=cdb2dd4f18df201c&unit=m

In truth, the --location (or -l) in .conkyrc doesn't really do anything as the script defaults to location/locale listed in the config file. Try entering a few conkyForecast commands in a terminal and you'll see. You can thus omit these from your .conkyrc entries.

Anyway, again sorry for the late post.

Happy conkying!

---

