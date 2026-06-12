---
title: "I messed up conky"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by dluzius on 2010-03-21
I've messed with conky, until I finally screwed it up. Now, when I type conky into terminal I get this error message  "missing text block in configuration; exiting"
Can someone show me how to corresct this, taking me, a senile old fart, thru it step by step.
Thanks, Dave

---

### Post by PPPilot on 2010-03-21
It sounds like you have been editing your conky.conf file. If that is so, you must have messed it up. I would go here:
> [http://ubuntuforums.org/showthread.php?t=281865&highlight=show+conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=show+conky)You will find all manner of conkey.conf files here. Select and Copy one you like then open a terminal. enter:
```
gksudo gedit
```Enter your password. When gedit opens select > Open>File System>etc>conky>conky.conf

When it opens erase everything and paste in the code you copied from this forum and save. It may be a good idea to now save it again under another name so you have a clean copy to go back to if you mess up the conky.conf again. I know the same thing happened to me. Conky should now work again. Now you can edit conky.conf again.

---

### Post by PPPilot on 2010-03-21
Here is my conky.conf file:

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Sans:style=Bold:size=14

# Text alpha when using Xft
xftalpha 1

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 60

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent no

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour light green

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 10

# border width
border_width 10

# Default colors and also border colors
#default_color white
#default_shade_color black
#default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 40
gap_y 40

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer yes

# mldonkey_hostname Hostname for mldonkey stuff, defaults to localhost
# mldonkey_port Mldonkey port, 4001 default
# mldonkey_login Mldonkey login, default none
# mldonkey_password Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16)
min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color black}$sysname $kernel On: $machine - $nodename 
$hr
Uptime: $uptime
$hr
${color black}Load Average: ${color 26466D}$loadavg% 
${color black}AMD Athlon CPU:   ${color 26466D}$cpu% @ ${freq} MHz 
${color black}RAM:   ${color 26466D}$memperc%  ${mem}B / ${memmax}B$color
${color black}Swap:  ${color 26466D}$swapperc%  ${swap}B / ${swapmax}B${color black}
$hr
${color black}Internet/Networking Status: (${addr eth0})${color black}
Down: ${color 26466D}${downspeedf eth0}k/s ${color black}${alignr}Up: ${color 26466D}${upspeedf eth0}k/s${color black}
${downspeedgraph eth0 25,180 000000 e7fb16} ${alignr}${upspeedgraph eth0 
25,180 000000 0effe2}
$hr
${color black}CPU Usage:     PID     CPU%   MEM%
${color black} ${top name 1} ${color 26466D}${top pid 1} ${top cpu 1} ${top mem 1}
${color black} ${top name 2} ${color 26466D}${top pid 2} ${top cpu 2} ${top mem 2}
${color black} ${top name 3} ${color 26466D}${top pid 3} ${top cpu 3} ${top mem 3}
${color black}$hr
${color black}Memory Usage:PID     CPU%   MEM%
${color black} ${top_mem name 1} ${color 26466D}${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color black} ${top_mem name 2} ${color 26466D}${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color black} ${top_mem name 3} ${color 26466D}${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
${color black}$hr
${color black}HD IO: ${color 26466D}${diskio} 
${color black}${diskiograph 000000 0077ff}
${color black}Hard Drives:
${color black} Root ${color 26466D}${fs_used /}/${fs_size /}${alignr}${color black}${fs_bar 5,120 /}
${color black} Home ${color 26466D}${fs_used /home}/${fs_size /home}${alignr}${color black}${fs_bar 5,120 /home}
${color black}$hr
#${color black}FORTUNE ${hr 2}$color
#${execi 120 fortune -s | fold -w50}
```It is pretty simple but it works well....

---

### Post by dluzius on 2010-03-21
****I did everything you said, but alas, I am still getting same error message
Has me stymied completely.
Dave

---

### Post by PPPilot on 2010-03-21
Maybe it would help to reinstall conky.

Go to: System>Administration>Synaptic Package Manager:
In the quick search box type: > conkyYou should see > conky-all with a green box to the left.

Right click on it and select Mark for Reinstallation then enter your password and select Apply.

When its done see what happens....

---

### Post by dluzius on 2010-03-21
I think we are getting closer, but still not right on the $.
I now get error message 
" missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program."

Not sure why this is turning out to be so difficult.
TIA for all your past and future help.
             Dave







QUOTE=PPPilot;9005445]Maybe it would help to reinstall conky.

Go to: System>Administration>Synaptic Package Manager:
In the quick search box type: You should see  with a green box to the left.

Right click on it and select Mark for Reinstallation then enter your password and select Apply.

When its done see what happens....[/QUOTE]

---

### Post by louieb on 2010-03-21
From ole old fart to another.
Post your .conkyrc file.

---

### Post by dluzius on 2010-03-21
Here is my conky.conf file as copied from my conky directory:

file:///etc/conky/conky.conf
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
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
hope this helps...

---

### Post by louieb on 2010-03-21
Worked just fine for me. Whats the problem?  lol the font size is a little to small for my old eyes. 
All I did was comment out line 44 to get rid of the  'border_margin' error. 

Are you sure you don't have a .conkyrc file in your home directory?  In the file browser make sure the show hidden files box is checked - in the View menu.

---

### Post by dluzius on 2010-03-22
Tks, louieb, that solved my problem.
On closer examination, on your advice, there it was.
A conkyrc file, with a little dot in front of it.
I deleted it and now I have conky!! Ta da...
Thanks again and thanks also to PPPilot.
         Dave

---

