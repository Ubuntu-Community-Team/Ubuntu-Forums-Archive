---
title: "Installed Conky but it's nowhere to be found"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by xcvcx on 2010-06-06
I went into terminal, typed sudo apt-get install conky, finished downloading and installing. I checked my system and found nothing. I tried it again and it tells me "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded"


What did I do wrong?

---

### Post by 4Orbs on 2010-06-06
I don't think it shows up in the menu. Have you tried just starting Conky from the terminal?
```
conky
```

---

### Post by xcvcx on 2010-06-06
This is what shows up:


Conky: desktop window (12000af) is subwindow of root window (a3)
Conky: window type - desktop
Conky: drawing to created window (0x5400001)
Conky: drawing to single buffer

So after typing conky in terminal and closing terminal it showed up on my desktop for half a second and vanished.


Edit x2: Nvm, now it showed up but how exactly do I edit this? It keeps flashing too. I'm such a beginner.

Edit x3: Nvm, I click on the desktop and it disappears.

---

### Post by 4Orbs on 2010-06-06
Maybe you need to reboot first. If that doesn't get it showing, open your home folder and click on "View" at the top then click on "Show Hidden Files" and then look to see that you have a .conkyrc file in your home folder.

EDIT: If it closes when you close the terminal, then you might try starting it from terminal with this:
> conky &
Or you might prefer to add a new launcher on the top panel and in the launcher command put conky & which should keep it open all the time. You edit the .conkyrc file to make changes in it's appearance. There are lots of different .conkyrc files you can download from different people, already pre-customized. Here's the one I use:
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
root: ${fs_used_perc /}%${alignr}${fs_used /} / ${fs_size /}
/home: ${fs_used_perc /home}%${alignr}${fs_used /home} / ${fs_size /home}
data: ${fs_used_perc /mnt/data}%${alignr}${fs_used /mnt/data} / ${fs_size /mnt/data}
data-2: ${fs_used_perc /mnt/data-2}%${alignr}${fs_used /mnt/data-2} / ${fs_size /mnt/data-2}

${color gray}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 18,100 000000 green} ${alignr}${upspeedgraph eth0 18,100 000000 green}$color

```
and it looks like this:
[ATTACH]159566[/ATTACH]

---

### Post by xcvcx on 2010-06-06
Thanks for the help but there is no file that name.

---

### Post by halitech on 2010-06-06
because the file starts with a . it is hidden so you need to show hidden files. another way is to press ALT + F2 and type in 
```
gedit .conkyrc
```

---

### Post by sgosnell on 2010-06-06
Have you read the [Conky man page](http://conky.sourceforge.net/docs.html)?

---

### Post by xcvcx on 2010-06-06
Alright, I typed gedit .conkyrc and that worked, I also used the text orbs gave me and that works. Also, no I haven't because..... I didn't check before asking. Sorry :P

---

### Post by sgosnell on 2010-06-06
You don't have to be sorry, but reading that will be much more helpful than asking individual questions here.  Hackers get to be hackers by reading the fine manual.

---

### Post by sm4sh1t on 2010-06-06
> **sgosnell said:**
> You don't have to be sorry, but reading that will be much more helpful than asking individual questions here.  Hackers get to be hackers by reading the fine manual.

who said anything about wanting to be a hacker :lolflag:

---

