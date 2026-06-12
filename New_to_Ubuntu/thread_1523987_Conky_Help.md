---
title: "Conky Help"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by Automag05 on 2010-07-04
Hi guys, I am new to Ubuntu and have been experimenting with Conky. I've noticed many great guides to customize Conky, my only problem is when I go to my home folder, hold down CTR+H to show hidden files, .conkyrc is not there to edit! If anyone has an idea on what I can do to obtain this, or another way to edit conky through script, it would be appreciated.

Thanks in advance, 
Auto

---

### Post by RJ12 on 2010-07-04
You need to create your own .conkyrc file. Usually with your beginning config.

---

### Post by 4Orbs on 2010-07-04
When conky is first installed, it doesn't create a .conkyrc file in your home folder but instead uses the default file in the conky folder located in the root filesystem. Once you place a .conkyrc in your home folder, that new one overrides the default one... but only for your user account. If you want to use my .conkyrc, copy the below into a blank text file, then save as .conkyrc in your personal home folder. Then you can start conky and see the results and then edit the file as you please.
```
# UBUNTU-CONKY

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes
xftfont Hemi head 426:size=9
xftalpha 0.8

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 10

# Maximum width
maximum_width 250

# Default color
default_color gray

# Text alignment, other possible values are commented
alignment top_right

# Gap between borders of screen and text
gap_x 12
gap_y 42

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${alignr}${color gray}${time %a, } ${color gray}${time %b %e - } ${color gray}${time %I:%M %p}
${color gray}SYSTEM ${hr 2}$color
Name: $nodename
Kernel: $sysname $kernel

${color gray}CPU ${hr 2}$color
Uptime: ${uptime}
${freq_g}GHz Load: ${loadavg}
${cpugraph gray ffffff}
PROCESS NAME${alignr}CPU%
${top name 1}${alignr}${top cpu 1}
${top name 2}${alignr}${top cpu 2}
${top name 3}${alignr}${top cpu 3}
${top name 4}${alignr}${top cpu 4}
${top name 5}${alignr}${top cpu 5}

${color gray}MEMORY${hr 2}$color
RAM:$alignr$mem/$memmax
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

MEMORY NAME${alignr}MEM %
${top_mem name 1}${alignr}${top_mem mem 1}
${top_mem name 2}${alignr}${top_mem mem 2}
${top_mem name 3}${alignr}${top_mem mem 3}
${top_mem name 4}${alignr}${top_mem mem 4}
${top_mem name 5}${alignr}${top_mem mem 5}

${color gray}DISK SPACE USED${hr 2}$color
Root: ${fs_used_perc /}%${alignr}${fs_used /} / ${fs_size /}
Home: ${fs_used_perc /home}%${alignr}${fs_used /home} / ${fs_size /home}
DATA: ${fs_used_perc /mnt/data}%${alignr}${fs_used /mnt/data} / ${fs_size /mnt/data}

${color gray}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 18,100 000000 green} ${alignr}${upspeedgraph eth0 18,100 000000 green}$color

```
And this is how it should look on your desktop:
[ATTACH]162424[/ATTACH]

---

### Post by Automag05 on 2010-07-04
Thanks guys!

And thank you for the starting script, it rather snazzy. I will have a lot of fun playing around with it now that I have a guide to follow as well.

---

### Post by JC Cheloven on 2010-07-04
[http://ubuntuforums.org/showthread.php?t=281865&highlight=conkyrc](http://ubuntuforums.org/showthread.php?t=281865&highlight=conkyrc)

is a thread of these forums. You'll find there THOUSANDS of .conkyrc files with screenshots.

Have fun!

---

### Post by Automag05 on 2010-07-13
Wow, thanks for the link, I am having a great time!

---

