---
title: "Conky Problems"
date: 2011-08-11
forum: New to Ubuntu
---

### Post by granitesoul on 2011-08-11
Hi guys,

I recently installed conky/Lua and I have a few questions:

Everything seems to be working fine except for the swap and the net monitoring, not really sure where to start in trouble shooting this, I've searched around the net and on the forums a bit, but nothing really seems to  be the fix. I am an absoulte noob at this point, the fact that I have gotten this far is still blowing my mind, so detailed help is VERY appreciated, I want to learn and contribute to this great community :) 

Here is a picture to help show what I mean, on the left is the console with present Ifconfig output showing, as well as conky on the right hand side.

[http://www.flickr.com/photos/nine-two-five/6031957733/](http://www.flickr.com/photos/nine-two-five/6031957733/)
[IMG]http://farm7.static.flickr.com/6145/6031957733_79ae8ea7a6_z.jpg[/IMG]

Here is what my .conkyrc looks like:

# Conky settings #
background no
update_interval 1

cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
#imlib_cache_size 0

temperature_unit fahrenheit

# Window specifications #

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 200 250
maximum_width 200

alignment tr
gap_x 35
gap_y 55

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5

uppercase no

temperature_unit celsius


default_color FFFFFF

# Lua Load  #
lua_load ~/.lua/scripts/clock_rings.lua
lua_draw_hook_pre clock_rings

TEXT
${voffset 8}${color FF6600}${font caviar dreams:size=16}${time %A}${font}${voffset -8}${alignr 50}${color FFFFFF}${font caviar dreams:size=38}${time %e}${font}
${color FFFFFF}${voffset -30}${color FFFFFF}${font caviar dreams:size=18}${time %b}${font}${voffset -3} ${color FFFFFF}${font caviar dreams:size=20}${time %Y}${font}${color FF6600}${hr}
${voffset 140}${font caviar dreams:size=10}${alignr}HOME${font}
${font caviar dreams:size=12}${color FFFFFF}${alignr}${weather [http://weather.noaa.gov/pub/data/observations/metar/stations/](http://weather.noaa.gov/pub/data/observations/metar/stations/) CYXU temperature temperature 30} °C${font}
${image ~/.conky/new-ubuntu-logo.png -p 64,125 -s 70x20}

${color FFFFFF}${goto 25}${voffset 35}${cpu cpu0}%
${color FF6600}${goto 25}CPU
${color FFFFFF}${goto 50}${voffset 23}${memperc}%
${color FF6600}${goto 50}RAM
${color FFFFFF}${goto 75}${voffset 23}${swapperc}%
${color FF6600}${goto 75}Swap
${color FFFFFF}${goto 100}${voffset 23}${fs_used_perc /}%
${color FF6600}${goto 100}Disk
${color FFFFFF}${goto 125}${voffset 25}${downspeed eth0}
${color FFFFFF}${goto 125}${upspeed eth0}
${color FF6600}${goto 125}Net



${color FFFFFF}${font caviar dreams:size=8}Uptime: ${uptime_short}
${color FFFFFF}${font caviar dreams:size=8}Processes: ${processes}
${color FFFFFF}${font caviar dreams:size=8}Running: ${running_processes}


${color FF6600}${font caviar dreams:size=8}${alignr}${nodename}
${color FF6600}${font caviar dreams:size=8}${alignr}${pre_exec cat /etc/issue.net}  $machine
${color FF6600}${font caviar dreams:size=8}${alignr}Kernel: ${kernel}

-----------------------------------------------------------------------------------------------

Any and all help would be greatly appreciated. :)

---

### Post by Frogs Hair on 2011-08-11
You have done well since last night ! The .conkyrc indicates a wired connection . If have wireless it will not report . I don't know why the swap is not reporting .

---

### Post by Frogs Hair on 2011-08-11
Here is a sample from an .conkyrc with a wireless syntax (not lua) 
```
${wireless_link_qual wlan0}% 
	Ul: ${upspeed wlan0} kb/s 
	Dl: ${downspeed wlan0} kb/s 
```

My swap syntax is the same with out the brackets.```
$swapperc%
```


I should add that with my lua configuration I rarely see the net speed move Unless I'm playing music or downloading .

---

### Post by granitesoul on 2011-08-11
> **Frogs Hair said:**
> Here is a sample from an .conkyrc with a wireless syntax (not lua) 
```
${wireless_link_qual wlan0}% 
    Ul: ${upspeed wlan0} kb/s 
    Dl: ${downspeed wlan0} kb/s 
```My swap syntax is the same with out the brackets.```
$swapperc%
```

Thanks, I've been working my *** off on this to show some people what Ubuntu is all about :) 

I am however unsure what to do with this info you have posted? Where should I insert it into the .conkyrc?

---

### Post by granitesoul on 2011-08-11
I added that code into my .conkyrc file and it is now displaying my network speeds! (thank you!) The problem now, is instead of being in that little circular pie chart doo-dad, it's just text beside it :/

---

### Post by Frogs Hair on 2011-08-11
Delete the text and re-insert the text from the .rc you posted . It is a good idea to make a copy of the .conkyrc when experimenting . Rename it anything you want and save it in a folder . To make it run again right click and copy to your home and rename .conkyrc and it will move to your hidden folders and run again. Remember to remove others first.

If you do have a wireless connection , try inserting just these lines in the .conkyrc after you have restored it to its origial state .```
${upspeed wlan0}
``` 
```
${downspeed wlan0}
```

---

### Post by Frogs Hair on 2011-08-11
It should look like this .```
${color FFFFFF}${goto 125}${voffset 25}${downspeed wlan0}
${color FFFFFF}${goto 125}${upspeed wlan0}
${color FF6600}${goto 125}Net
```

The lines you want to replace are in this section of the .rc . Scroll down until you find it .

${color FFFFFF}${goto 25}${voffset 35}${cpu cpu0}%
 ${color FF6600}${goto 25}CPU
 ${color FFFFFF}${goto 50}${voffset 23}${memperc}%
 ${color FF6600}${goto 50}RAM
 ${color FFFFFF}${goto 75}${voffset 23}${swapperc}%
 ${color FF6600}${goto 75}Swap
 ${color FFFFFF}${goto 100}${voffset 23}${fs_used_perc /}%
 ${color FF6600}${goto 100}Disk
 ${color FFFFFF}${goto 125}${voffset 25}${downspeed eth0}
 ${color FFFFFF}${goto 125}${upspeed eth0}
 ${color FF6600}${goto 125}Net

---

### Post by Frogs Hair on 2011-08-11
Here is some auto start script instructions and a couple of screen shots with a lua and text style Conky.

You can autostart via script by creating a blank file and renaming it conky_start in your home directory. Right-click>Permissions>Allow Executing File as a Program>Check yes.

 Open the file, paste this inside:

Code:
#!/bin/bash
 sleep 10 && 
conky -c ~/.conkyrc;
Go to System>Startup Applications and click the + or Add button. Browse to the conky_start file (which should be in the home folder, path ~/conky_start) and click ok. Now this script should run on startup and after ten seconds start conky. This lets other things load first, such as compiz.
 If that doesn't work and you are only using a single config file .conkyrc in the home folder, try using 
Code:
#!/bin/bash
 sleep 10 && conky;
 in conky_start instead. If you do want to use more than one conky (ie, start more than one conky window) you can add start them all at the same time 
Code:
#!/bin/bash
 sleep 10 && 
conky -c ~/.conky1;
conky -c ~/.conky2;
conky -c ~/.conky3
etc. Just note that 
 a) you need to get the path to the files right (in this case they would all be in the home folder and hidden, as per the added '.') 
 b) it doesn't matter what you call the files if you use the longer versions - putting 
Code:
conky -c PATH/TO/FILENAME
 will start it up.

---

