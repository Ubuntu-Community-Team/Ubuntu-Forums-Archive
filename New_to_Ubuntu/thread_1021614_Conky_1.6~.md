---
title: "Conky 1.6~"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by wynneth on 2008-12-25
I'm relatively new to Ubuntu/linux. I built and installed conky with --enable-wlan. My up and down graphs work fine, the totals work fine, but I cannot get the essid, bandwidth, signal, or bitrate functions to work. I've read on some forums that there may be issues with some wireless cards - and if that's the case ok fine, but I'd like to know for sure. Also, when I installed conky there was a default .conkyrc and although I thought I had backed it up before creating this new one apparently I did not. Does anybody have that? It has some slightly different cpu and ram information that I'd like to add back in. Here is my .conkyrc :

```
#!/bin/bash
#UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Seldon77 (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer none
use_xft no

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 20

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color white}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
Battery: ${battery_percent}% ${battery_bar}
Battery Time: ${alignr}${battery_time}

${color white}CPU ${hr 2}$color
${freq}MHz  $cpu%  Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color white}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

${if_up eth0}
${alignc}eth0
Down:   ${alignr}${downspeed eth0}KB/s Up:     ${alignr}${upspeed eth0}KB/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total:  ${alignr}${totaldown eth0} down ${alignr}${totalup eth0} up0}
$endif${if_up eth1}
${alignc}eth1
ESSID: ${alignr}${wireless_essid eth1} Bitrate: ${alignr}${wireless_bitrate eth1}
Signal: ${wireless_link_qual_perc eth1}% ${wireless_link_bar eth1}

Down:   ${alignr}${downspeed eth1}KB/s Up:     ${alignr}${upspeed eth1}KB/s
${downspeedgraph eth1 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1 
25,140 000000 00ff00}$color
Total:  ${alignr}${totaldown eth1} down ${alignr}${totalup eth1} up
$endif

Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
Connections: ${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}

${color white}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

I also tried this quality.sh script that was in a thread about conky wireless issues:

```
#!/bin/bash

# Find device used for wifi.
devlist=$(cat /proc/net/wireless | tail --lines=1) 2>/dev/null
devleft=${devlist#' '*}
devright=${devlist%%':'*}
echo $devright | grep "" > /tmp/dev_pure
device=$(cat /tmp/dev_pure)

# Get Quality
iwconfig $device | grep Link > /tmp/link
quality=$(cat /tmp/link | grep "Link")
echo $quality

```

and I get an error stating ```
iwconfig: unknown command "|"
```
I'm betting this is an issue with the way my wifi is running, because when I run iwconfig by itself the adapter listing for my wifi just shows ```
eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated
``` while currently connected.

My wifi is running off a proprietary Broadcom STA driver. Per lspci my wifi is: ```
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```


Newbie help! LOL

**************Edit***********
After some more investigating I think I have found the issue. Doing iwconfig -v tells me that for eth1 "Drive has no Wireless Extension version information". I'm betting that's where my problem lies. I also updated my .conkyrc to have a different if then based on the if_existing /proc/net/route instead of using if_up. Honestly, the main thing here is I just want Signal and ESSID to show, by whatever method. It would also be lovely to get a reply to this post.
*****************************

---

### Post by nekolyanich on 2010-11-30
Hi, i already try to solve this problem right now. Did you solve it?

---

