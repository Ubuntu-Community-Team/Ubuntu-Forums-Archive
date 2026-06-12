---
title: "conky help"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by rm06 on 2009-02-11
Here's is a conky that I'm using which I found on the 'net:

[IMG]http://i43.tinypic.com/4t13ch.png[/IMG]

and here is the code I copied and modified to create it:

```
background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 300
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color gray
default_shade_color red
default_outline_color green
alignment top_right
gap_x 10
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes
text_buffer_size 256

TEXT

${font openlogos:size=20}${font Arial:size=20}${color Tan1}GNU${color Ivory}LINUX${font openlogos:size=20}

${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}

${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
$font${color DimGray}CPU1  ${cpu cpu1}% ${cpubar cpu1}
CPU2  ${cpu cpu2}% ${cpubar cpu2}

${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar

${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %

${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color DimGray}IP on eth0 $alignr ${addr eth0}
External IP$alignr${execi 3600 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail}

Down $alignr ${downspeed eth0} kb/s
Up $alignr ${upspeed eth0} kb/s

Downloaded: $alignr  ${totaldown eth0}
Uploaded: $alignr  ${totalup eth0}

${font Arial:bold:size=10}${color Tan2}TIME ${color DarkSlateGray}${hr 2}

${color DimGray} ${font :size=30}$alignc${time %H:%Mh}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}
$endif
```

I'd like to remove the shadow borders if possible though I don't know how - can anyone help? Also, is it possible to display the time in 12 hour format instead of 24?

---

### Post by rm06 on 2009-02-11
ttt

---

### Post by adam_kimber on 2009-02-11
I had a look around the forum. There appears to be a very long Conkyrc thread. Have a look at [this]("http://ubuntuforums.org/showpost.php?p=6648647&postcount=5513") post. That should help with your 24 hour, 12 hour problem.

---

### Post by m_duck on 2009-02-11
Check out [this link]("http://www.manpagez.com/man/3/strftime/") for help formatting the time. You probably want something like this to replace this part ${time %H:%Mh} in your .conkyrc```
${time %I:%M%p}
```Also, see [the conky site]("http://conky.sourceforge.net/variables.html") for help with all the variables. The thread mentioned by adam_kimber has loads of conky info.

As far as the shadows go, I think that the config you have would usually work without shadows, however mine has also been a bit weird with shadows recently. Firstly, if you launch conky on login, use a script to delay the launch by 20 seconds or so to allow compiz to get started first which should stop the shadows. If it still happens anyway (which it does with me), my (relevant) settings to stop it are:```
background no
own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type override
```The above works for me. Failing that, asking in the aforementioned conky thread or checking [this page]("http://conky.sourceforge.net/config_settings.html") on the conky site for various config settings to try out might help.

---

### Post by rm06 on 2009-02-11
Cool, that worked for me - thanks for the help!

---

