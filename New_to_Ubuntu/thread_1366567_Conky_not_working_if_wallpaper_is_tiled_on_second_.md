---
title: "Conky not working if wallpaper is tiled on second screen."
date: 2009-12-28
forum: New to Ubuntu
---

### Post by Exadrid on 2009-12-28
This is an oddly specific problem w/ conky or something els.

THE PROBLEM: Conky is not transparent and stays black.

HOW THE PROBLEM IS CREATED: Only if conky is set on the second screen  (i have 2 screen) and i have the wallpaper on tiled (nothing els, all the other work as wanted).

THE FIX: Will EDIT if i find one.

Now i have tried everything w/ the own_window_****.

Here's my conky settings i hope someone can help me.

> background yes
font Snap.se:size=8
xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
text_buffer_size 1024
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 275 5
maximum_width 275
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 3
gap_y 3
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

---

### Post by Exadrid on 2010-01-09
Ok i found a fix for this, i just edited the wallpaper to copypast it one beside each other in gimp... this does not fix the problem but its a workaround.

---

