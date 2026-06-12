---
title: "conky keeps disappearing"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by crowhill on 2010-03-21
hi there

here is my conky.conf

> alignment top_right
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
font 6x30
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type override
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer right
show_graph_scale no
show_graph_range no

first, i get the error "can't load font '6x30'". what kind of (large) fonts are available?

second and much more important, conky keeps disappearing after firing up the system (ubuntu karmic).

how do i have to change my conky.conf to keep the above from happening?

thanks a lot in advance,
cheers,
crowhill.

---

### Post by ankspo71 on 2010-03-22
Hi I was having similar trouble with conky disappearing. My problem was conky kept running but disappeared behind the desktop (even with "own_window_type override"). I was able to solve the problem by creating a script that starts conky after a short amount of time.

1) Open a new text file, and save the code below as autostart-conky.sh
```
#!/bin/bash 
sleep 20 && conky ;
```(adjust the sleep (delay) time to suit your pc specs/performance)

2) Place this autostart-conky.sh in your home folder.

3) Then go to System > Preferences > Startup Applications, then create a startup entry for the script:
Name: Conky
Command: sh /home/crowhill/autostart-conky.sh
(remember to put the sh in front of the path to the script.)

I think the problem is if conky starts before the desktop is fully loaded, then the desktop will cover conky when it loads. If this is the problem you are having then this should help.

---

### Post by crowhill on 2010-03-22
Hi there!

Thanks a lot for the reply.

I already had a script like yours. However, my 'sleep' value was too low. Increasing it fixed the problem.

This, however, implies that loading my desktop has become slower since I first installed the system ... actually, it takes "forewer" at the moment ... and linux is supposed to be fast!?

Anyway, thanks a lot,
cheers,
crowhill.

---

