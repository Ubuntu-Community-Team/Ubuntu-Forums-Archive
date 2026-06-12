---
title: "How to check CPU temperature?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by ajk95 on 2010-05-01
How do I check the temperature of my CPU?

---

### Post by renkinjutsu on 2010-05-01
not sure if this'll work for you but..
```
cat /proc/acpi/thermal_zone/THRM/temperature
```

---

### Post by 2hot6ft2 on 2010-05-01
You can add the applet to one of the panels to keep an eye on the temps. if you want.

Here's a short version of installing them:
Just open a Terminal (Applications -> Accessories -> Terminal) and type (or copy and paste):

```
sudo apt-get install lm-sensors sensors-applet hddtemp
```

Next, run sensors-detect. Answer y to each one until finished.
```
sudo sensors-detect
```

Now you can also run
```
sudo hddtemp /dev/sda
```
Where sda is your hard drive.
and it will show the temperature of your hard drive if it can.

All temps. are in Celsius by default, but you can change it to F or Kelvin if you want.

adding hdd temp to sensors-applet
> **dcstar said:**
> ```
gksudo gedit /etc/default/hddtemp
```

Make RUN_DAEMON="true"
Save and close
Finally, restart to load all the sensors.
Once back at the desktop, right-click on the top panel and choose "Add to Panel.
Select "Hardware Sensors Monitor" and click the "Add" button, then "Close".
Right-click on all the sensors applet that appears on the top panel and choose "Preferences".
Click the "Sensors" tab. There you can select/de-select all the relevant sensors and adjust their low and high values as well as set alarms if desired.

Time to go eat.

---

### Post by srini.rg on 2010-06-18
[2hot6ft2]("http://ubuntuforums.org/member.php?u=568708"),    Your suggestion helped me and now the CPU and Motherboard temp.s are showing on my top panel in Ubuntu. Thanks for your help.
- RGS

---

### Post by zx5000 on 2010-09-20
> **renkinjutsu said:**
> not sure if this'll work for you but..
```
cat /proc/acpi/thermal_zone/THRM/temperature
```

Not on Lucid. thermal_zone is empty by default.

---

### Post by Dustin2128 on 2010-09-20
you can also use conky for constant monitoring. Here's the .conkyrc I use, monitors temperature in Celsius:
```

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
update_interval 0.5

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
gap_y 20

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
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /dev/sda3}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
```

---

