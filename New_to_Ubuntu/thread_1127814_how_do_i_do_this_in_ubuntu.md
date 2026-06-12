---
title: "how do i do this in ubuntu"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by damagedmafia on 2009-04-16
hi i installed DSL on my eeepc and on it has a cpu memory thing imbedded on the desktop here is the screenshot i found on the DSL page arm i want this on my ubuntu desktop see the arrow how do i do it and also how do i put other things into the desktop like calender and stuff, Ie i dont want them to be applets that can be moved or if they are applets how do i make them a permanent fix

[[img]http://www.picsaway.com/uploads/dsldesktop_things_i_want_on_ubuntu-5d1fdde794.png[/img]](http://www.picsaway.com/view/dsldesktop_things_i_want_on_ubuntu-5d1fdde794.png)

---

### Post by whoop on 2009-04-16
conky: [http://conky.sourceforge.net/](http://conky.sourceforge.net/)
it's in the repo's

---

### Post by taurus on 2009-04-16
That thing on the upper right corner is called conky and it should be in the repos.

---

### Post by LesterPalooza on 2009-04-16
THAT IS CONKY. Conky is a lightweight program utility that allows you to view information about pretty much anything from CPU Temperature to playing media.

Install Conky!

sudo apt-get install conky

And then go to your /etc/conky/ folder and open conky.conf and edit the contents

sudo gedit /etc/conky/conky.conf

Here's a screenshot of my conky.

[IMG]http://i97.photobucket.com/albums/l238/lhester_12/Screenshot-1.png[/IMG]

And here is my code for conky.

```
# Use Xft?
use_xft yes
xftfont Arial:size=8
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
minimum_size 250 0
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

# Force UTF8? note that UTF8 support required XFT  ${color grey}$hr
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
${font Zekton:size=20}${alignc}${color Gray}${time %B %d}
${font Zekton:size=42}${alignc}${color Gray}${time %H:%M:%S}${alignr}${font Zekton:size=8}

$alignc ${color grey}OS:${color 2499ff} Ubuntu 8.10 Intrepid Ibex
$alignc ${color grey}Kernel: ${color 2499ff}$sysname $kernel 
$alignc ${color grey}Architecture: ${color 2499ff}$machine
$alignc ${color grey}User@Hostname: ${color 2499ff}lester${color 2499ff}@${color 2499ff}$nodename

${alignc}${color 2499ff}CPU Info:
${color grey}CPU:$alignr ${color white}${exec cat /proc/cpuinfo | grep 'model name' | sort -u | cut -c 18-59}
${color grey}Frequency (in MHz):$alignr ${color white}$freq
${color grey}Frequency (in GHz):$alignr ${color white}$freq_g
${color grey}CPU Usage:${alignr}${color white}${cpu cpu0}% ${cpubar cpu0 4,145}
${color grey}Core1 Usage:${alignr}${color white}${cpu cpu1}% ${cpubar cpu1 4,145}
${color grey}Core2 Usage:${alignr}${color white}${cpu cpu2}% ${cpubar cpu2 4,145}

${alignc}${color 2499ff}Memory Info:
${color grey}RAM Usage:${alignr}${color white}$mem/$memmax ${membar 4,75}
${color grey}Swap Usage:${alignr}${color white}$swap/$swapmax ${swapbar 4,75}

${alignc}${color 2499ff}Video Card Info:
${color grey}GPU Temp:$alignr${color white}+${exec nvidia-settings -q GPUCoreTemp | grep Attribute | cut -d ' ' -f 6 | cut -c 1-2}°C
${color grey}M/B Temperature: $alignr${color white}$acpitemp°C

${alignc}${color 2499ff}File systems:
${color grey}${color white}${fs_free /}/${fs_size /} $alignr${fs_bar 4,145 /} 

${alignc}${color 2499ff}Networking:${color grey}
${alignc}IP:${color white}${addr ath0}
${color grey}Up:  ${color white}${upspeed ath0}Kb/s${color grey}${alignr}Down:  ${color white}${downspeed ath0}Kb/s${color grey}

${color grey}Uptime:$alignr ${color white} $uptime
${color grey}Processes running/total:$alignr ${color white}$running_processes/$processes
${color white}Name                ${alignr 30} PID ${alignr 10} CPU% $alignr MEM%
${color grey} ${top name 1} ${alignr 30} ${top pid 1} ${alignr 10} ${top cpu 1}   $alignr ${top mem 1} 
${color grey} ${top name 2} ${alignr 30} ${top pid 2} ${alignr 10} ${top cpu 2}   $alignr ${top mem 2} 
${color grey} ${top name 3} ${alignr 30} ${top pid 3} ${alignr 10} ${top cpu 3}   $alignr ${top mem 3} 
${color grey} ${top name 4} ${alignr 30} ${top pid 4} ${alignr 10} ${top cpu 4}   $alignr ${top mem 4} 
${color grey} ${top name 5} ${alignr 30} ${top pid 5} ${alignr 10} ${top cpu 5}   $alignr ${top mem 5}
```

---

### Post by damagedmafia on 2009-04-16
how do i insert this code to use

---

### Post by LesterPalooza on 2009-04-16
Conky works for Ubuntu. I am using Ubuntu 8.10 Intrepid Ibex. (DSL?)

You first have to install conky by typing in the terminal:

```
sudo apt-get install conky
```

and then you have to go to your conky folder which is at /etc/conky/

and then you have to edit the text inside conky.conf and from there, you insert the sample code i gave you.

to edit conky.conf type in the terminal:

```
sudo gedit /etc/conky/conky.conf
```

---

### Post by damagedmafia on 2009-04-16
ok i installed it all good i have th conky.conf up here is what mine looks like


# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2007 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#
# $Id: conky.conf 1193 2008-06-21 20:37:58Z ngarofil $

alignment bottom_left
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no
show_graph_scale no
show_graph_range no

TEXT
${scroll 16 $nodename - $sysname $kernel on $machine | }
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
$hr
${color grey}Name                  PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}


where do i insert the code then how do i make it work every time i boot up

---

### Post by LesterPalooza on 2009-04-16
That is the default code of in conky.conf

I suggest you make a backup file just in case you mess something up.

Select all of my code, and replace _everything_ in conky.conf.

Conky on startup.. Hmm... One way to do that is to make a bash shell script that you can add to the Startup programs.

Check this forum thread: [http://ubuntuforums.org/showthread.php?t=386078&highlight=conky+start]("http://ubuntuforums.org/showthread.php?t=386078&highlight=conky+start")

---

### Post by damagedmafia on 2009-04-16
ok i backed up the file and cut the old code out replaced it with the one you gave us now we need to get it running

---

### Post by LesterPalooza on 2009-04-16
> **damagedmafia said:**
> ok i backed up the file and cut the old code out replaced it with the one you gave us now we need to get it running

Go to the terminal and type:
```

conky
```

By the way, if your conky doesn't look like mine, relax. Most likely you don't have the font I used in there. I am using Zekton and you can download this font from this link:

[http://www.gnome-look.org/content/show.php/Zekton?content=50553]("http://www.gnome-look.org/content/show.php/Zekton?content=50553")

---

### Post by damagedmafia on 2009-04-16
ok i ran conky in terminal this is what i got

-laptop:~$ conky
Conky: desktop window (16000a8) is subwindow of root window (6d)
Conky: window type - override
Conky: drawing to created window (0x3800001)
Conky: drawing to double buffer
Conky: attempting to use more CPUs than you have!
obj->data.cpu_index 2 info.cpu_count 1XXXXXXXXX@XXXXXXXXX-laptop:~$ 


ive also done this 

To have conky autostart on login create a small bash script called .conky_start.sh and save it to your /home.

gedit .conky_start.sh

copy the code below and past into the file. Save and close

#!/bin/bash
sleep 10 && conky;

This would start conky after 10 seconds after you login. The delay can be changed. Some sort of delay is desirable if you autostart beryl as well since conky works best if started after beryl. Not using beryl so I changed it to sleep 2 && conky; Make sure the script is executable:

chmod a+x .conky_start.sh

Now, add it to your startup programs (menu: system->preferences->session->startup programs).Note, path to script is /home/>your user name/.conky_start.sh


not sure about this part 
Make sure the script is executable:

chmod a+x .conky_start.sh

i have an acer aspire 3000 amd 2800Mhz cpu single core

im very new to linux and by all means im ok with linux from the box as in i can install it and use it as is 

what havent i done to get this to work i have compiz installed but i havent enabled desktop effects

---

### Post by LesterPalooza on 2009-04-16
Look up this part of the conky.conf code:

```
${alignc}${color 2499ff}CPU Info:
${color grey}CPU:$alignr ${color white}${exec cat /proc/cpuinfo | grep 'model name' | sort -u | cut -c 18-59}
${color grey}Frequency (in MHz):$alignr ${color white}$freq
${color grey}Frequency (in GHz):$alignr ${color white}$freq_g
${color grey}CPU Usage:${alignr}${color white}${cpu cpu0}% ${cpubar cpu0 4,145}
${color grey}Core1 Usage:${alignr}${color white}${cpu cpu1}% ${cpubar cpu1 4,145}
${color grey}Core2 Usage:${alignr}${color white}${cpu cpu2}% ${cpubar cpu2 4,145}
```

and remove the line:

```
${color grey}Core2 Usage:${alignr}${color white}${cpu cpu2}% ${cpubar cpu2 4,145}
```

That should only display 1 CPU instead of two.

Rerun conky again and you should be left with these messages in the terminal:

```
Conky: desktop window (16000a is subwindow of root window (6d)
Conky: window type - override
Conky: drawing to created window (0x3800001)
Conky: drawing to double buffer
```

from there I just close the terminal.

By the way, I also have compiz and I am having trouble running conky on startup too. :D I've tried the site I gave you but it didn't work for me. I think if you don't have compiz installed, you can follow that guide I gave you.

---

### Post by BoneSaw on 2009-04-16
i find rather than opening a terminal, if you hit alt+f2, it brings up a run command prompt. then you can just type in "conky" and hit enter.

---

### Post by LesterPalooza on 2009-04-16
Conky is totally customizable.

Take a look at other people's code from this website:

[http://ubuntuforums.org/showthread.php?t=281865&highlight=post+con]("http://ubuntuforums.org/showthread.php?t=281865&highlight=post+con")

Design conky to suit your needs. :)

Make sure you terminate all other conky's running before you run another conky. To do this, just type:

```
killall conky
```

in the terminal.

---

### Post by damagedmafia on 2009-04-17
ok i have this messege 
Conky: statfs '/media/sda1': No such file or directory
Conky: desktop window (16000a8) is subwindow of root window (6d)
Conky: window type - override
Conky: drawing to created window (0x2000001)
Conky: drawing to double buffer
Conky: statfs '/media/sda1': No such file or directory
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)

---

### Post by damagedmafia on 2009-04-17
2. Make a configuration file in your home directory (ie. /home/bob). This is the code that describes what you want displayed on your conky desktop.
Code:

gedit /home/*XX*/.conkyrc

3. Obviously, you can put whatever you want in your .conkyrc.

this one works for me your code works when i added it to conkyrc
but i dont have nvidia so its saying not found 

any way hopefully you know a way to bring up what info i have on my computer like graphics and chip and all that so i get find out a code to use for my self

---

### Post by pastalavista on 2009-04-17
If you don't want to bother with all the configuring, the screenlets applet sysmonitor can do it for you.. here's mine.. all screenlets

---

