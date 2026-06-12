---
title: "trouble with Conky"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by stalkier on 2009-09-10
I am needing help getting conky to be configured right. I am getting a box outline and I am wanting it to just be on the desktop. 

[IMG]http://godsallaroundus.com/conky.png

Here is my conkymain:

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

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

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph ath0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed ath0}k/s${color}
${offset 240}${downspeedgraph ath0 20,130 000000 ffffff}
```

---

### Post by credobyte on 2009-09-10
```
background yes

```

If it doesn't help, here's a working conky setup - just find the differences and tweak it to the state where your boarders have gone :)
```
background yes
use_xft yes
xftfont Sans:size=8
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 240
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 12
gap_y 12
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
```

---

### Post by stalkier on 2009-09-10
Ok I found the problem. I had to change to **metacity**. 

Does anyone know if conky can be run with no border with Compiz???? I really love my effects and miss them. I cannot deal with the box in Conky though.

---

### Post by RabbitWho on 2009-09-10
can i tack myself to this to avoid starting a new thread? 

When i type in Conky in the terminal it comes up fine in a little window... how do I get it onto the desktop like you did? 

Do i need to download a different version? 

What exactly did you do, was there a GUI? 

Any info or links to info would be cool, thanks! :)

---

### Post by stalkier on 2009-09-10
> **RabbitWho said:**
> can i tack myself to this to avoid starting a new thread? 

When i type in Conky in the terminal it comes up fine in a little window... how do I get it onto the desktop like you did? 

Do i need to download a different version? 

What exactly did you do, was there a GUI? 

Any info or links to info would be cool, thanks! :)

I started fusion icon. Change from Compiz to Metacity. It will reload the windows manager and conky will be on the desktop.

If you do not have fusion icon installed bring up a terminal and type:
```
sudo apt-get install fusionicon
```

---

### Post by whitethorn on 2009-09-10
I'm not quite sure, but my conky also works fine with compiz.  You have to start conky after compiz. So you'll need a script to start it conky and add sleep 10,20,30 depending on how long it takes to get your desktop loaded.  Best way to check if this is the case, is to start compiz, and restart conky afterwards.  If the box is still there then you need to tweak your script a bit, if you want I can also give you mine.

my startup script looks like this

```

#!/bin/bash
sleep 30 && conky -d -c /home/whitethorn/.conkyrc &

```

---

### Post by stalkier on 2009-09-10
> **whitethorn said:**
> I'm not quite sure, but my conky also works fine with compiz.  You have to start conky after compiz. So you'll need a script to start it conky and add sleep 10,20,30 depending on how long it takes to get your desktop loaded.  Best way to check if this is the case, is to start compiz, and restart conky afterwards.  If the box is still there then you need to tweak your script a bit, if you want I can also give you mine.

my startup script looks like this

```

#!/bin/bash
sleep 30 && conky -d -c /home/whitethorn/.conkyrc &

```

Dude Thanks a million. Worked like a charm. I was having an issue with the smaller conky box not being under all my windows. Very irritating.

---

### Post by RabbitWho on 2009-09-10
> **stalkier said:**
> I started fusion icon. Change from Compiz to Metacity. It will reload the windows manager and conky will be on the desktop.

If you do not have fusion icon installed bring up a terminal and type:
```
sudo apt-get install fusionicon
```

I didn't know i'd need fusion.. it's not really my thing. I can live without conky on my desktop. But thanks for the advice! :)

---

### Post by stalkier on 2009-09-10
How do I add temps, and other info other than what is in this pic:

[IMG]http://img197.imageshack.us/img197/8740/newconkeyresized.png[/IMG]

I can post my conky files if needed. Just let me know which ones to post. Thanks.

---

### Post by overdrank on 2009-09-10
There is great info in the [Conky ]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky")thread

---

### Post by sailthesea on 2009-09-10
> **overdrank said:**
> There is great info in the [Conky ]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky")thread

 Running up your own conky.rc is one of the best ways to get to grips with the commands and file system in ubuntu Try it And good luck!:)

---

