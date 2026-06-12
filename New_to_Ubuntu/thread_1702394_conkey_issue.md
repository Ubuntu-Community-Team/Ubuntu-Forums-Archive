---
title: "conkey issue"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by ECET on 2011-03-07
Hello all, I have a small problem with my conky.....I like it....but....when I go online and open up full window, my conky stays on top....I can't read whats under, and I can't get my browser to display itself "on top" of conky....any ideas?....thanks....

---

### Post by ECET on 2011-03-07
Ttt

---

### Post by jcolyn on 2011-03-07
If you post your .conkyrc file here somebody should be able to help you..

---

### Post by wojox on 2011-03-07
Do you have:

```
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,skip_taskbar,sticky,skip_pager

```

---

### Post by ECET on 2011-03-07
I do not know how to check this...can you please advise so I can show you what I have got?....thanks, I appreciate the help.....

---

### Post by false truths on 2011-03-07
You can open your .conkyrc is here: ~/.conkyrc
The tilde means your home folder. As in: /home/USERNAME/.conkyrc
You'll need super-user permissions to edit it, and a text editor to open it.

---

### Post by jcolyn on 2011-03-07
Open a terminal and type ```
gedit .conkyrc
```

You may have to sub another text editor if you don't have gedit installed or you can ```
sudo apt-get install gedit
```

You can then copy/paste it here..

---

### Post by jcolyn on 2011-03-07
> **false truths said:**
> 
You'll need super-user permissions to edit it, and a text editor to open it.

Conky is owned by the user and does not need permission to edit.. Just simply type ```
gedit .conkyrc
``` in a terminal. Sudo is not needed..

---

### Post by false truths on 2011-03-07
It turns out you are right. For a very long time mine was owned by root. But since I last removed and reinstalled conky, it appears it's owned by me.

---

### Post by ECET on 2011-03-07
this is what I got when I typed in the code gedit . conkyrc:

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

# set to yes if you want Conky to be forked in the background
background yes

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes
xftfont Bitstream Vera Sans Mono:size=8
xftalpha 0.9

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
#font arial

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 60

# stuff after 'TEXT' will be formatted on screen


TEXT

${color white}${color green}[${color white}$nodename${color green}]:
${color white}$sysname $kernel on $machine
${color white}Uptime: $uptime
${color orange}CPU ${hr 2}$color
${freq}MHz   ${color green}Load: ${color white}${loadavg}   ${color green}Temp: ${color white}${acpitemp}F
${color green}processes: ${color white}$processes    ${color green}running: ${color white}$running_processes
$cpubar
${cpugraph 00ff00 ffffff}
${color green}NAME             PID       CPU%      MEM%${color white}
${color #ffff00}${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}${color white}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${color orange}MEMORY / DISK ${hr 2}$color
${color green}RAM:   ${color white}$memperc%   ${membar 6}
${color green}Swap:  ${color white}$swapperc%   ${swapbar 6}

${color green}Root:  ${color white}${fs_free_perc /}%   ${fs_bar 6 /}
${color green}ISO :  ${color white}${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}
${color green}APPS:  ${color white}${fs_free_perc /media/hdb1}%   ${fs_bar 6 /media/hdb1}
${color orange}NETWORK (${addr eth1}) ${hr 2}$color
${color green}Down: ${color white}${downspeed eth1}k/s ${alignr}${color green}Up: ${color white}${upspeed eth1}k/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1 
25,140 000000 00ff00}
${color green}Total: ${color white}${totaldown eth1} ${alignr}${color green}Total: ${color white}${totalup eth1}
${color green}Inbound: ${color white}${tcp_portmon 1 32767 count} ${color green}Outbound: ${color white}${tcp_portmon 32768 
61000 count}${alignr}${color green}Total: ${color white}${tcp_portmon 1 65535 count}
Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}
${color orange}BLOCKED IPs ${hr 2}$color
${execi 30 tail -n5 /var/log/moblock.log | fold -w50}

---

### Post by wojox on 2011-03-07
It's probablly compiz. Try this, open your terminal:

```
gedit .conky_start
```

Insert:

```
#!/bin/bash
sleep 5
conky &
```

Save and close. Still in the terminal:

```
chmod +x .conky_start
```

Then create an Startup Application. Under System > Preferences

Name: ConkyStart

Command:

```
/home/username/.conky_start
```

Replace username with your username. :P

Reboot.

---

### Post by Quackers on 2011-03-07
Have a look at post #11 onwards in this thread (and some of the earlier ones too). It may be of help to you.
[http://ubuntuforums.org/showthread.php?t=1558978&page=2](http://ubuntuforums.org/showthread.php?t=1558978&page=2)

Edit
See wojox's post, one up. It's the same thing :-)

---

### Post by ECET on 2011-03-07
WOJOX!....thank you my friend!!!!!......it worked!.....I truly appreciate your advice/code help....thank you sir!....everybody, thank you too!....I am slowly learning this OS and look forward to helping others someday!!!.....

---

### Post by Quackers on 2011-03-07
Nice one :-)

---

### Post by wojox on 2011-03-07
Your welcome. :P

---

### Post by jcolyn on 2011-03-07
In the section below change ```
own_window_type override
``` to ```
own_window_type normal
```Also add this line to the below section.

```
own_window_class Conky
``````
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```Save the .conkyrc file and see what happens..

---

