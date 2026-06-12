---
title: "Conky on startup"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by scheibo on 2009-01-24
After spending a few hours perfectly my .conkyrc, I've tried to get Conky to run on startup using System -> Preferences -> Sessions and adding a program called Conky which runs the command line 'conky'. Once I log out and log in, Conky runs on startup quite nicely, but once I try to open another window, Conky covers the window instead of staying on the desktop. It's as if conky is constantly the top level window, and all the other windows I try to open are under it. If I run 'conky' from my terminal it launches the program normally (ie, it stays on my desktop and under all my other programs), it's only when i try and run it from startup.

Is there any way I can fix this? Or possible a better way to run conky than from the Sessions menu?

TIA

---

### Post by chamber on 2009-01-24
You could post your .conkyrc here.

---

### Post by scheibo on 2009-01-24
Sorry. My bad.

```

# Config Settings
#------------------------------------------------------

alignment top_left 				# Aligned position on screen
background no      				# Fork Conky to background?
border_margin 4   				# Border margin in pixels 
border_width 1    				# Border width in pixels 

color0 0077ff					# Define colour to use in TEXT area
#color1						# Define colour to use in TEXT area

cpu_avg_samples 2  				# Number of samples to average for CPU monitoring
#top_cpu_separate  				# Seperate CPUs or treat as one?

default_color white				# Default colour
default_shade_color white			# Default shade
default_outline_color white			# Default outline

double_buffer yes  				# Reduces flickering on some consoles
draw_borders no 				# Draw borders around text?
draw_graph_borders yes 				# Draw borders around text?
draw_outline no 				# Draw outlines?
draw_shades no 					# Draw shades?

#font 						# Font name in X

gap_x 15					# Gap, in pixels, between right or left border of screen
gap_y 35					# Gap, in pixels, between top or bottom border of screen

#imap						# Default IMAP global server
#mail_spool $MAIL 				# Mail spool for mail checking 
#max_port_monitor_connections 	 		# Allow each port monitor to track at most this many connections
#max_specials					# Maximum number of special things
#max_user_text					# Maximum size of user text buffer (under TEXT)
#text_buffer_size				# Size of standard buffer, defaults to 128 bytes

maximum_width 285				# Maximum width of window
minimum_size 260 5				# Minimum size of window

#mpd_host 	 				# Host of MPD server
#mpd_port 					# Port of MPD server
#mpd_password 	 				# MPD server password
#music_player_interval 				# Music player thread update interval (defaults to Conky's update interval) 

net_avg_samples 2				# Number of samples to average for network monitoring
no_buffers yes					# Substract (file system) buffers from used memory?
#override_utf8_locale 				# Force UTF8? requires XFT

own_window yes					# Boolean, create own window to draw?
#own_window_class 				# Manually set the WM_CLASS name
#own_window_colour 				# If own_window_transparent no, set a specified background colour
own_window_hints undecorated,below,skip_taskbar # Window hints to use if own_window yes
#own_window_title				# Manually set the window name
own_window_transparent yes			# Set pseudo-transparency? 
own_window_type override			# Sets type of window
out_to_console no 				# Print text to stdout?

#pad_percents 	 				# Pad percentages to this many decimals
#pop3 	 					# Default global POP3 server

short_units yes	 				# Shortens units to a single character (kiB->k, GiB->G, etc.). Default is off. 
stippled_borders no 				# Border stippling in pixels
total_run_times 0	 			# Total number of times for Conky to update before quitting
update_interval 1 				# Update interval in seconds
uppercase no 					# Render all text in uppercase?
use_spacer none 				# Add spaces to keep things from moving about?  This only affects certain objects.

use_xft yes 	 				# Use Xft (anti-aliased font and stuff) 
xftalpha 0.8 					# Alpha or Xft font (between 0 and 1)
xftfont Bitstream Vera Sans Mono:size=8 	# Xft font when Xft is enabled


# Screen Output
#------------------------------------------------------

TEXT
${color0}$sysname $kernel $machine - $nodename 

${color0}Uptime:${color lightgrey} $uptime ${color0} Load:${color lightgrey} $loadavg

${color0}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} 
${color0}Usage:${color0} ${color lightgrey}${cpu}% ${color0}${cpubar}
${color0}Process:${color lightgrey} $processes  ${color0}Run:${color lightgrey} $running_processes  ${color0}HD IO: ${color lightgrey}${diskio} 

${color0}Memory:
${color0} RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color0}${membar 5,120}
${color0} SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color0}${swapbar 5,120}
${color0} Buffers:${color lightgrey} $buffers 
${color0} Cached:${color lightgrey} $cached 

${color0}Hard Disks:
${color0} Root ${color lightgrey}${fs_used /}/${fs_size /}${alignr}${color #0077ff}${fs_bar 5,120 /}
${color0} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}
${color0} HDD1 Temp: ${color #CCCCCC}${execi 300 nc localhost 7634 | cut -c29-30 ;}C $alignc${color0} HDD2 Temp: ${color #CCCCCC}${execi 300 nc localhost 7634 | cut -c62-63 ;}C

${color0}CPU Usage         PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color0} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color0} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color0} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color0} ${top name 5} ${top pid 5} ${top cpu 5} ${top mem 5}

${color0}Mem Usage         PID     CPU%   MEM%
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color0} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color0} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color0} ${top_mem name 4} ${top_mem pid 4} ${top_mem cpu 4} ${top_mem mem 4}
${color0} ${top_mem name 5} ${top_mem pid 5} ${top_mem cpu 5} ${top_mem mem 5}

${color0}Network: ${color lightgrey}${addr wlan0}
${color0} Down:${color lightgrey} ${downspeed wlan0} k/s (${color lightgrey}${totaldown wlan0})
${color0} Up:${color lightgrey} ${upspeed wlan0} k/s (${color lightgrey}${totalup wlan0})
```

Tried to keep it fairly neat and tidy.

---

### Post by damis648 on 2009-01-24
I think that conky is starting before your window manager has time to, so it causes this. Try changing the command to
```
sleep 5; conky
```
or 10 or something. That is what I do, or else compiz draws shadows around my conky.

---

### Post by emarkd on 2009-01-24
It's probably not related to the conky configuration.  It happens to me sometimes too and I think it's related to the order things start up.  If conky is started too early in the process of getting your desktop and compositing started, it winds up in a higher "layer" somehow.  One solution may be to write a script that pauses a few seconds and then starts conky.  Call that script from your sessions settings instead of calling conky directly.  Maybe something like:

```

#!/bin/bash

sleep 10
conky &

```

This would sleep for 10 seconds, launch conky and exit itself.  Maybe that'll help.

---

### Post by scheibo on 2009-01-24
creating the script to run worked perfectly. thank you

---

### Post by emarkd on 2009-01-24
Glad it helped.  damis648 actually posted the same solution and you could do it that way too if you wanted to keep things "cleaner".  I immediately thought script because that's how I do it.  I have a startup.sh script that is called from the sessions manager and i just add things to it that i need to happen on every login, including starting conky after a 10 second delay.

---

### Post by jirwin on 2009-09-07
> **emarkd said:**
> It's probably not related to the conky configuration.  It happens to me sometimes too and I think it's related to the order things start up.  If conky is started too early in the process of getting your desktop and compositing started, it winds up in a higher "layer" somehow.  One solution may be to write a script that pauses a few seconds and then starts conky.  Call that script from your sessions settings instead of calling conky directly.  Maybe something like:

```

#!/bin/bash

sleep 10
conky &

```

This would sleep for 10 seconds, launch conky and exit itself.  Maybe that'll help.

PERFECT!  Works great now, thanks!

---

### Post by terdon on 2009-12-04
I had the same problem and no amount of sleep would fix it. The autostart entry was ignored even with 60s waiting. 

I finally got it to start by running conky from my $HOME/profile:```
sleep 60 && conky &
```

---

### Post by yuanfangcan on 2011-07-24
This works perfectly for me! Thanks

---

