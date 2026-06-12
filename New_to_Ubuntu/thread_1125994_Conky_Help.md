---
title: "Conky Help"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-04-14
How can I keep my Desktop Icons while making my conky border invisible? Here is a picture of my current Desktop.

[http://i97.photobucket.com/albums/l238/lhester_12/Screenshot-1.png]("http://i97.photobucket.com/albums/l238/lhester_12/Screenshot-1.png")

And here is my code for conky:

```
alignment top_right
maximum_width 300
total_run_times 0
background yes
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
gap_x 15
gap_y 35
minimum_size 200 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer yes
alignment top_right
double_buffer yes

TEXT
${font Zekton:size=20}${alignc}${color Gray}${time %B %d}
${font Zekton:size=30}${alignc}${color Gray}${time %H:%M:%S}${alignr}${font Zekton:size=8}
${color grey}$hr
${color grey}$hr
$alignc ${color grey}OS:${color green}Ubuntu 8.10 Intrepid Ibex
$alignc ${color grey}Kernel:${color 2499ff}$sysname $kernel 
$alignc ${color grey}Architecture:${color 2499ff}$machine
$alignc ${color grey}User@Hostname:${color 2499ff}lester${color 2499ff}@${color 2499ff}$nodename
${color grey}$hr
${alignc}${color green}CPU Info:
${color grey}CPU:$alignr ${color white}${exec cat /proc/cpuinfo | grep 'model name' | sort -u | cut -c 18-59}
${color grey}Frequency (in MHz):$alignr ${color white}$freq
${color grey}Frequency (in GHz):$alignr ${color white}$freq_g
${color grey}CPU Usage:${alignr}${color white}${cpu cpu0}% ${cpubar cpu0 4,145}
${color grey}Core1 Usage:${alignr}${color white}${cpu cpu1}% ${cpubar cpu1 4,145}
${color grey}Core2 Usage:${alignr}${color white}${cpu cpu2}% ${cpubar cpu2 4,145}
${color grey}$hr
${alignc}${color green}Memory Info:
${color grey}RAM Usage:${alignr}${color white}$mem/$memmax ${membar 4,75}
${color grey}Swap Usage:${alignr}${color white}$swap/$swapmax ${swapbar 4,75}
${color grey}$hr
${alignc}${color green}Video Card Info:
${color grey}GPU Temp:$alignr${color white}+${exec nvidia-settings -q GPUCoreTemp | grep Attribute | cut -d ' ' -f 6 | cut -c 1-2}  °C
${color grey}M/B Temperature: $alignr${color white}$acpitemp°C
${color grey}$hr
${alignc}${color green}File systems:
${color grey}${color white}${fs_free /}/${fs_size /} $alignr${fs_bar 4,145 /} 
${color grey}$hr
${alignc}${color green}Networking:${color grey}
${alignc}IP:${color white}${addr ath0}
${color grey}Up:  ${color white}${upspeed ath0}Kb/s${color grey}${alignr}Down:  ${color white}${downspeed ath0}Kb/s${color grey}
${color grey}$hr
${color grey}Uptime:$alignr ${color white} $uptime
${color grey}Processes running/total:$alignr ${color white}$running_processes/$processes
${color white}Name                ${alignr 30} PID ${alignr 10} CPU% $alignr MEM%
${color grey} ${top name 1} ${alignr 30} ${top pid 1} ${alignr 10} ${top cpu 1}   $alignr ${top mem 1} 
${color grey} ${top name 2} ${alignr 30} ${top pid 2} ${alignr 10} ${top cpu 2}   $alignr ${top mem 2} 
${color grey} ${top name 3} ${alignr 30} ${top pid 3} ${alignr 10} ${top cpu 3}   $alignr ${top mem 3} 
${color grey} ${top name 4} ${alignr 30} ${top pid 4} ${alignr 10} ${top cpu 4}   $alignr ${top mem 4} 
${color grey} ${top name 5} ${alignr 30} ${top pid 5} ${alignr 10} ${top cpu 5}   $alignr ${top mem 5} 
```

Problem:
When I change the own_window to no, I lose my Desktop Icons but conky also loses its border.

I want conky to "blend in" to my Desktop...

I've seen it in someone else's Desktop. Here's an example.

[http://img379.imageshack.us/img379/2282/ubu5ys0.jpg]("http://img379.imageshack.us/img379/2282/ubu5ys0.jpg")

it's a really crappy desktop but notice the difference in the conky border?


Please advise. Thank you!

---

### Post by Sarai the Geek on 2009-04-15
> **LesterPalooza said:**
> Please advise. Thank you!

It looks like your window manager, presumably compiz, has decided that "dammit, Conky is a window, I'm gonna give it a drop shadow just like all the windows!"
When this happens to me, it's because I opened conky before my window manager finished loading, and killing it and restarting fixes the problem.

Make sure the following lines are in your .conkyrc:

```
own_window yes
own_window_transparent yes
own_window_type desktop 
```

Looking at your config file I think you're missing the third one. Add it in, save the file then restart conky ("killall conky" then "conky").

Hopefully that will fix it!

---

### Post by Sarai the Geek on 2009-04-15
Oh, also, I love your wallpaper- mind sharing? :popcorn:

---

### Post by LesterPalooza on 2009-04-15
Sure :) Here you go. :)

[http://i97.photobucket.com/albums/l238/lhester_12/02.png]("http://i97.photobucket.com/albums/l238/lhester_12/02.png")

May I suggest [http://profesorul09.webs.com/apps/photos/]("http://profesorul09.webs.com/apps/photos/")

It's where I got my wallpaper.

Disclaimer: I am not advertising any websites :D

---

### Post by LesterPalooza on 2009-04-15
Hmm... I added the > own_window_type desktop but when I clicked on my Desktop, conky vanished! :( But when I checked the processes, conky is still running in the background.

There was a > own_window_type normal in my previous code and i just replaced that with ```
own_window_type desktop
```. That's when conky vanished when I clicked on my Desktop. Btw, the desktop icons did not disappear anymore. This time it's just conky. :D

Sent you a PM. :p

Edit: Added a screenshot of my Desktop showing the icons without conky and a look at my terminal.. I hope that helps.

---

### Post by kpkeerthi on 2009-04-15
> **LesterPalooza said:**
> Sure :) Here you go. :)

[http://i97.photobucket.com/albums/l238/lhester_12/02.png]("http://i97.photobucket.com/albums/l238/lhester_12/02.png")

May I suggest [http://profesorul09.webs.com/apps/photos/]("http://profesorul09.webs.com/apps/photos/")

It's where I got my wallpaper.

Disclaimer: I am not advertising any websites :D

That site has got some amazing stuffs. Glad I saw this thread. Thanks for sharing.

---

### Post by LesterPalooza on 2009-04-15
*plead bump* :)

---

### Post by halitech on 2009-04-15
here is the top lines in my .conkyrc file

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by LesterPalooza on 2009-04-15
> **halitech said:**
> here is the top lines in my .conkyrc file

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

Did that... Didn't do anything.... Sorry....

---

### Post by Sarai the Geek on 2009-04-15
Well, we can easily figure out if it's a problem with your script or something wrong with your window manager. Back up your current script and then replace it with this snippet from mine:

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
minimum_size 180 0
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

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
${font Arial:size=16}S${color B8A0C8}tatus${color}${font}

Operating System:  ${alignr}Ubuntu 8.10
Kernel:  ${alignr}${kernel}
CPU1:  ${alignr}${cpubar cpu1 8,60}
CPU2:  ${alignr}${cpubar cpu2 8,60}
RAM:  ${alignr}${membar 8,60}
SWAP:  ${alignr}${swapbar 8,60}
HDD:  ${alignr}${fs_bar 8,60 /home}
Battery:  ${alignr}${battery_bar 8,60 BAT0}
Temp:  ${alignr}${acpitemp}°C
Uptime: ${alignr}${uptime}
```

If it fixes the border problem, you can just take my settings and use them for your script.

---

### Post by LesterPalooza on 2009-04-15
**OMG YOU ARE A LIFE SAVER!! AHAHAHA! Want a UbuntuHug?** :lolflag: I owe you one. :)

Okay, what did you change? I should know what you did so I will learn from this...

---

### Post by Sarai the Geek on 2009-04-15
> **LesterPalooza said:**
> Okay, what did you change? I should know what you did so I will learn from this...

Well, it's all in the script. Your window controls said this:

```
own_window yes 
own_window_class Conky 
own_window_type normal 
own_window_transparent yes 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```Whereas mine said this:

```
own_window yes 
own_window_transparent yes 
own_window_type override 
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```Notice that I have "own_window_type override" in mine, and "own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager" is commented out. I don't know enough about conky syntax to tell you for sure which one it was that did it, but if I was a betting woman I'd say it was the override one.
Glad to hear it worked! And Ubunhugs are always welcome. ;)

---

