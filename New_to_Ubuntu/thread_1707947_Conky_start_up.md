---
title: "Conky start up"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Chasetaylor1 on 2011-03-16
Hello,

I'm fairly new to Ubuntu and just installed Conky. I set everything the way I wanted it to be, and it was working fantastic. I also have it set to boot at startup. However, I want it to run as a transparent window. In my .conkyrc file, it is set to do this, yet when I login it doesn't go into effect. If I open .conkyrc, I don't change anything, and just save it, then it works like I want it to. Any Ideas why this might be happening and how to fix it?
:confused:

Here is what my .conkyrc file looks like, if it helps:

background yes
use_xft yes
xftfont Sans:size=8
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color orange
default_shade_color black
default_outline_color white
alignment top_right
gap_x 12
gap_y 3
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT

${font ubuntu:size=20}
CPU:1  ${cpu cpu1}% ${cpubar cpu1} 
CPU:2  ${cpu cpu2}% ${cpubar cpu2}
${font ubuntu:size=19}Memory      ${membar ram}
${font ubuntu:size=18}Disk Space  ${fs_bar /}
Power${font ubuntu:size=15} ${battery_percent}% ${font ubuntu: size=20}  ${battery_bar}

---

### Post by stinkeye on 2011-03-16
Use a sleep command in your startup to delay conky until
the window manager has loaded.
eg```
bash -c "sleep 15; conky"
```
May have to increase sleep depending on your load times.

---

### Post by Legeril on 2011-03-16
> **stinkeye said:**
> Use a sleep command in your startup to delay conky until
the window manager has loaded.
eg```
bash -c "sleep 15; conky"
```May have to increase sleep depending on your load times.

This basically, I would recommend a sleep time of around 30 seconds as this will allow more than enough time for everything to load even if your system slows down a little in the future. If you have desktop effects activated then the window manager draws a window around conky, ruining the look you are probably going for.

create an executable file .conky_start.sh in the same folder as your .conkyrc, here is an example of my code

```
#!/bin/bash
sleep 60 && conky;
```

---

### Post by Chasetaylor1 on 2011-03-16
Fantastic! Works perfectly now! Thanks! :D

---

### Post by Menoitios on 2012-06-03
You could also make your conky startup script wait for the window manager:

```

#!/bin/bash
until ps -A | grep "gtk-window-deco"> test -n 
do 
	sleep 1 
done
/usr/bin/conky --quiet --config=.conkyrc &

```

---

### Post by coffeecat on 2012-06-04
Old thread closed.

---

