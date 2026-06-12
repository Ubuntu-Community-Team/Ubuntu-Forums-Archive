---
title: "Conky Gnome Panel Transparency"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by Spencer Caplan on 2010-12-26
I want to maximize available screen space so I moved a number of things which normally display as Gnome panel applications (the clock for example) to Conky. I want the Conky display to be visible underneath a transparent transparent Gnome panel. With the panel set to full transparency it shows the desktop as if Conky weren't there. Is there anything I can do to allow Conky to be visible under a transparent Gnome panel?

I attached a screenshot showing how Conky is blocked by the panel even when it is transparent.

Thanks for the help!

---

### Post by frustratednerd on 2010-12-27
Hmm. I'll try to help you out with this. Post your conky configuration file (conkyrc), first.

---

### Post by Spencer Caplan on 2010-12-27
Here is my Conky file.

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes

# Use double buffering (reduces flicker)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes
xftalpha 0.5
no_buffers yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 400 5
maximum_width 400

# Draw shades?
draw_shades no

# Text stuff
draw_outline no
draw_borders no
xftfont Sans:size=8.5
uppercase no

# Stippled borders?
# stippled_borders 3

# border width
border_width 5

# Default colors and also border colors
default_color white

own_window_colour brown

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 40
gap_y 15

# stuff after ‘TEXT’ will be formatted on screen
TEXT
$color
${font Sans:size=14}${time %A, %B %e, %Y} $alignr ${time %T}

${color F07746}${font Sans:size=8.5}SYSTEM ${hr 3}$color
$alignc${font size=8.5}$nodename${font}
Ubuntu 10.10 $alignr GNOME 2.32.0
$alignc$sysname $kernel on $machine
Uptime: $alignr$uptime

${color F07746}${font Sans:size=8.5}BATTERY ${hr 3}$color
${if_match "$battery" == "charged"} Fully Charged $endif ${if_match "$battery" != "charged"}Time Remaining: $alignr $battery_time
$battery $battery_bar $endif

${color F07746}${font Sans:size=8.5}CPU ${hr 3}$color
Average ${color white} $alignr${cpu cpu0}%
${cpugraph F07746 2C001E}
Core 1: ${cpu cpu1}%                           Core 2: ${cpu cpu2}% $alignr Core 3: ${cpu cpu3}%
${cpugraph cpu1 25,120 F07746 2C001E}      ${cpugraph cpu2 25,120 F07746 2C001E} ${color white}$alignr${cpugraph cpu3 25,120 F07746 2C001E}
Core 4: ${cpu cpu4}%                           Core 5: ${cpu cpu5}% $alignr Core 6: ${cpu cpu6}%
${cpugraph cpu4 25,120 F07746 2C001E}      ${cpugraph cpu5 25,120 F07746 2C001E} ${color white}$alignr${cpugraph cpu6 25,120 F07746 2C001E}
Core 7: ${cpu cpu7}% $alignr Core 8: ${cpu cpu8}%
${cpugraph cpu7 25,120 F07746 2C001E} $alignr ${cpugraph cpu8 25,120 F07746 2C001E}
CPU Frequency: $alignr$freq_g GHz

   Processes:${color white} $processes ${color white}$alignr Run:${color white} $running_processes   ${color white}
NAME 		$alignr    PID   CPU% MEM%
${top name 1} $alignr${top pid 1} ${top cpu 1}  ${top mem 1} 
${top name 2} $alignr${top pid 2} ${top cpu 2}  ${top mem 2} 
${top name 3} $alignr${top pid 3} ${top cpu 3}  ${top mem 3} 
${top name 4} $alignr${top pid 4} ${top cpu 4}  ${top mem 4} 
${top name 5} $alignr${top pid 5} ${top cpu 5}  ${top mem 5} 
${top name 6} $alignr${top pid 6} ${top cpu 6}  ${top mem 6} 
${top name 7} $alignr${top pid 7} ${top cpu 7}  ${top mem 7} 
${top name 8} $alignr${top pid 8} ${top cpu 8}  ${top mem 8} 
${top name 9} $alignr${top pid 9} ${top cpu 9}  ${top mem 9} 

${color F07746}${font Sans:size=8.5}MEMORY / DISK ${hr 3}$color
SSD Temp: $alignr ${execi 10 /home/spencer/.get_temp.sh} °C

$alignc RAM: $mem
$memperc% ${membar 6 25,120}$color
$alignc Swap: $swap
$swapperc% ${swapbar 6 25,200}$color
$alignc Root: ${fs_used /} / ${fs_size /}
${fs_used_perc /}% ${fs_bar 6 /}$color

${color F07746}${font Sans:size=8.5}NETWORK ${hr 3}$color
${if_empty ${exec cat /proc/net/arp | grep eth0}}${if_empty ${exec cat /proc/net/arp | grep wlan0}}No Network connection
${else}WLAN IP: ${addr wlan0} $alignr ${wireless_mode wlan0} and ${wireless_bitrate wlan0}
SSID: ${wireless_essid wlan0} $alignr Range: ${wireless_link_qual_perc wlan0} % / ${wireless_link_qual_max wlan0} %
${wireless_link_bar 6,240 wlan0}
Down: ${downspeed wlan0} k/s ${alignr} Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 20,115 000000 ff0000} $alignr ${upspeedgraph wlan0 20,115 000000 00ff00}
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}${endif}
${else}LAN IP: $alignr ${addr eth0}
Down: ${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 20,115 000000 ff0000} $alignr ${upspeedgraph eth0 20,115 000000 00ff00}
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${endif}

${color F07746}${font Sans:size=8.5}WEATHER ${hr 3}$color
${offset 160}${font Sans:size=14}${execi 60 conkyForecast --location=19403 --datatype=CT}${font}
${offset 100}${font ConkyWeather:style=Bold:size=40}${execi 60 conkyForecast --location=19403 --datatype=WF} ${offset 50}${font ConkyWindNESW:size=40}${execi 60 conkyForecast --location=19403 --datatype=BS}${font}
${offset 97}${execi 60 conkyForecast --location=19403 -i --datatype=HT --centeredwidth=4}/${execi 60 conkyForecast --location=19403 -i --datatype=LT --centeredwidth=4}  ${offset 40}${execi 60 conkyForecast --location=19403 --datatype=WS --imperial} - ${execi 60 conkyForecast --location=19403 --datatype=WD}
Humidity: ${execi 60 conkyForecast --location=19403 --datatype=HM} $alignr Barometer: ${execi 60 conkyForecast --location=19403 --datatype=BR} and ${execi 60 conkyForecast --location=19403 --datatype=BD}
UV Index: ${execi 60 conkyForecast --location=19403 --datatype=UT} $alignr Sunrise and set: ${execi 60 conkyForecast --location=19403 --datatype=SR} / ${execi 60 conkyForecast --location=19403 --datatype=SS}

---

### Post by frustratednerd on 2010-12-27
You should play around with the "gap_y" setting, until the top of your conky is no longer obstructed by the top panel. Or try changing the alignment to "bottom_right".

Does your conky extend all the way to the bottom of your desktop?

---

### Post by Spencer Caplan on 2010-12-27
I know that I could move Conky down out of the way of the Gnome panel. I want the time to display, which I have at the top of Conky, underneath the Gnome panel in the top right. I would think that since I have the Gnome panel at full transparency that when I move Conky underneath that it would remain visible, but the panel simply shows the desktop as if Conky is not under it. So I think the issue most likely rests with configuring the Gnome Panel correctly. Any other thoughts?

---

### Post by frustratednerd on 2010-12-27
Oh. So are you saying that you want the clock to be visible underneath the panel rather than it being blocked by it? If so, I'm not really sure how to do that.

Sorry that I wasn't able to help you solve your problem.

---

### Post by Spencer Caplan on 2010-12-27
Yes, that's what I want.

Screenshot1 shows what happens now: Conky is written to appear where I want it but the supposedly "transparent" Gnome panel writes over it.

Screenshot shows how Conky would look if the Gnome panel were actually transparent (It's not correct though because I simply unexpanded the panel)

No problem, I'll keep poking around and something should work

---

### Post by mcduck on 2010-12-27
Gnome-panel doesn't support true transparency, so no setting will give you that.

The only way to make things actually show under the panel is to force some true transparency using the "Opacity, Brightness and Saturation"-plugin frok Compiz. But that approach can't make difference between panel background and it's contents, making everything in the panel transparent instead. So you really can't use it for more than just a slight transparency before it makes all the icons and menus hard to see...

---

### Post by Spencer Caplan on 2010-12-27
Hm, are there any alternative panels that I could use?

---

### Post by mcduck on 2010-12-27
Plenty. But of course they won't support Gnome-panel's applets... (well, I think xfce4-panel actually *does* support them, although they need to be contained inside some special applet which was rather annoying...)

If you want, you could try using *Avant Window Navigator* as your top panel. It does support true transparency, and has plugins for creating menus, and hosting indicator applets and notification icons. It wouldn't be exactly like gnome-panel, but you should definitely be able to create a decent panel using it.

---

### Post by Stainesy on 2010-12-27
Have you thought about restricting the size (length across the screen) of your panel?  In the panel properties you could deselect the expand option.

---

### Post by Spencer Caplan on 2010-12-28
Well, that helps fix the visibility issue, but it's not perfectly what I want. Oh, well I'll probably just have to wait until Gnome Panel support true transparency to achieve exactly what I want.

Thanks to everyone though.

---

