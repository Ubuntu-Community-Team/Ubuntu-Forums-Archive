---
title: "Help me with conky configuration. I&#7743; a beginner"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by skumara on 2011-05-14
Hi, I&#7743; not a programmer. I&#7743; just a user. I found conky in gnome look and it looks cool so I downloaded it. I have few problem.

1. How to make conky transparent to show my desktop wallpaper?

2. How to move conky to the left a bit like 0.5cm to left?

This is a cool program but it is not for beginners. Is there any programs to change conky setting?

I&#7743; using xubuntu 11.04. My screen shot and conkyrc file attached.

Thank you :)

---

### Post by Quackers on 2011-05-15
In your conkyrc file you have this

draw_shades no   but in my conkyrc I have
draw-shades yes

Just above that line you have
```
own_window yes
own_window_type background
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
while mine is ```
own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar
```
That may take care of transparency.

---

### Post by skumara on 2011-05-15
> **Quackers said:**
> In your conkyrc file you have this

draw_shades no   but in my conkyrc I have
draw-shades yes

Just above that line you have
```
own_window yes
own_window_type background
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```
while mine is ```
own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar
```
That may take care of transparency.


I just tried this. It didn work. Still no transparent.

---

### Post by Quackers on 2011-05-15
Ok, can you please post your new .conkyrc? You can use code tags rather than attaching a file. Select New Reply, not quick reply, then click on the # symbol in the toolbar then past .conkyrc contents in between the two code entried (where the pointer is).

---

### Post by skumara on 2011-05-15
My code as follows

```
background yes
font Bitstream Vera Sans:size=8
xftfont Bitstream Vera Sans:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
minimum_size 300
maximum_width 310
default_color white
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 5
gap_y 12
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer yes

TEXT
$alignc Hostname: $nodename
$alignc Kernel: $kernel
$alignc Uptime: $uptime

CPU:
Core1:$alignr ${cpu cpu1}%@${freq_g cpu1}GHz ${cpubar cpu1 7,76} Temp: ${hwmon 0 temp 1}°C
Core2:$alignr ${cpu cpu2}%@${freq_g cpu2}GHz ${cpubar cpu2 7,76} Temp: ${hwmon 1 temp 1}°C
Overall Usage:$alignr $cpu% $alignr${cpubar 8,182}
${cpugraph 20,}
Highest CPU $alignr CPU%   MEM%
${top name 1}$alignr${top cpu 1}     ${top mem 1}
${top name 2}$alignr${top cpu 2}     ${top mem 2}

MEM:
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 8}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 8}
Highest MEM $alignr CPU%   MEM%
${top_mem name 1}$alignr${top_mem cpu 1}     ${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}     ${top_mem mem 2}

HDD: ${alignr} HDD Temp: ${execi 1 /home/ghostrider/.conky_script_hddtemp}°C
Linux: ${alignc} ${fs_bar 8,75} ${alignr} ${fs_free /}  /   ${fs_size /} (${fs_free_perc /}%)
SDA1: ${alignc} ${fs_bar 8,75 /media/sda1} ${alignr}${fs_free /media/sda1}  /   ${fs_size /media/sda1} (${fs_free_perc /media/sda1}%)
SDA2: ${alignc} ${fs_bar 8,75 /media/sda2} ${alignr}${fs_free /media/sda2}  /  ${fs_size /media/sda2} (${fs_free_perc /media/sda2}%)
${color white}Read:                                  ${color white}Write:${color red}
${color green}${diskiograph_read 20,150} ${alignr}${color red}${diskiograph_write 20,150}${color white}
${color green}${diskio_read}/s   ${alignr}${color red}${diskio_write}/s

${color white}LAN: ${alignr}IP: ${addr eth0}
${color green}LAN Download:                  $alignr${color red}LAN Upload:
${color green}${downspeedgraph eth0 20,150} ${alignr}${color red}${upspeedgraph eth0 20,150}
${color green}${downspeed eth0} k/s                                  ${alignr}     ${color red} ${upspeed eth0} k/s
${color green}Total:${totaldown eth0}  ${alignr}${color red}Total:${totalup eth0}

${color white}WiFi:  ${alignr}IP: ${addr wlan0}
AP ESSID: [${color orange}${wireless_essid wlan0}${color white}] ${alignr}AP Bitrate: ${color orange}${wireless_bitrate wlan0}${color white}
Link quality: ${wireless_link_qual_perc wlan0}% ${alignr}${wireless_link_bar 8,185 wlan0}
${color green}WiFi Download:                  $alignr${color red}WiFi Upload:
${color green}${downspeedgraph wlan0 20,150} ${alignr}${color red}${upspeedgraph wlan0 20,150}
${color green}${downspeed wlan0}KB/s ${color red}${alignr}${upspeed wlan0}KB/s
${color green}Total:${totaldown wlan0}  ${alignr}${color red}Total:${totalup wlan0}
${color white}AP Mode: ${wireless_mode wlan0} ${alignr}AP MAC: ${wireless_ap wlan0}

```

---

### Post by Quackers on 2011-05-15
Ok thanks, I'll take another look.
In the meantime can you tell me if you open a window (say Downloads, for instance) and move the window to the right does it slide under the conky display, or does the window cover conky up?

---

### Post by Quackers on 2011-05-15
Have you gone to sleep?

---

### Post by wildmanne39 on 2011-05-15
> **Quackers said:**
> Have you gone to sleep?

Your funny:)

---

### Post by Quackers on 2011-05-15
:-) Lol.
Ok, when you wake up, try changing the first line of your conyrc from
background yes
to 
background no
then save the file. Not sure whether it will work but that's how mine is :-)
Good luck :-)

---

### Post by wildmanne39 on 2011-05-15
> **skumara said:**
> My code as follows

```
background yes
font Bitstream Vera Sans:size=8
xftfont Bitstream Vera Sans:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_class Conky
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
minimum_size 300
maximum_width 310
default_color white
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 5
gap_y 12
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer yes

TEXT
$alignc Hostname: $nodename
$alignc Kernel: $kernel
$alignc Uptime: $uptime

CPU:
Core1:$alignr ${cpu cpu1}%@${freq_g cpu1}GHz ${cpubar cpu1 7,76} Temp: ${hwmon 0 temp 1}°C
Core2:$alignr ${cpu cpu2}%@${freq_g cpu2}GHz ${cpubar cpu2 7,76} Temp: ${hwmon 1 temp 1}°C
Overall Usage:$alignr $cpu% $alignr${cpubar 8,182}
${cpugraph 20,}
Highest CPU $alignr CPU%   MEM%
${top name 1}$alignr${top cpu 1}     ${top mem 1}
${top name 2}$alignr${top cpu 2}     ${top mem 2}

MEM:
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 8}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 8}
Highest MEM $alignr CPU%   MEM%
${top_mem name 1}$alignr${top_mem cpu 1}     ${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}     ${top_mem mem 2}

HDD: ${alignr} HDD Temp: ${execi 1 /home/ghostrider/.conky_script_hddtemp}°C
Linux: ${alignc} ${fs_bar 8,75} ${alignr} ${fs_free /}  /   ${fs_size /} (${fs_free_perc /}%)
SDA1: ${alignc} ${fs_bar 8,75 /media/sda1} ${alignr}${fs_free /media/sda1}  /   ${fs_size /media/sda1} (${fs_free_perc /media/sda1}%)
SDA2: ${alignc} ${fs_bar 8,75 /media/sda2} ${alignr}${fs_free /media/sda2}  /  ${fs_size /media/sda2} (${fs_free_perc /media/sda2}%)
${color white}Read:                                  ${color white}Write:${color red}
${color green}${diskiograph_read 20,150} ${alignr}${color red}${diskiograph_write 20,150}${color white}
${color green}${diskio_read}/s   ${alignr}${color red}${diskio_write}/s

${color white}LAN: ${alignr}IP: ${addr eth0}
${color green}LAN Download:                  $alignr${color red}LAN Upload:
${color green}${downspeedgraph eth0 20,150} ${alignr}${color red}${upspeedgraph eth0 20,150}
${color green}${downspeed eth0} k/s                                  ${alignr}     ${color red} ${upspeed eth0} k/s
${color green}Total:${totaldown eth0}  ${alignr}${color red}Total:${totalup eth0}

${color white}WiFi:  ${alignr}IP: ${addr wlan0}
AP ESSID: [${color orange}${wireless_essid wlan0}${color white}] ${alignr}AP Bitrate: ${color orange}${wireless_bitrate wlan0}${color white}
Link quality: ${wireless_link_qual_perc wlan0}% ${alignr}${wireless_link_bar 8,185 wlan0}
${color green}WiFi Download:                  $alignr${color red}WiFi Upload:
${color green}${downspeedgraph wlan0 20,150} ${alignr}${color red}${upspeedgraph wlan0 20,150}
${color green}${downspeed wlan0}KB/s ${color red}${alignr}${upspeed wlan0}KB/s
${color green}Total:${totaldown wlan0}  ${alignr}${color red}Total:${totalup wlan0}
${color white}AP Mode: ${wireless_mode wlan0} ${alignr}AP MAC: ${wireless_ap wlan0}

```
Hi, I do see a couple of differences between yours and mine.
1.you have draw borders yes mine is no
2 you have draw shades yes mine is no
And changing the gap_X and gap_y will change the position of your conky, but you do not want to change it much sense you only want to move it a little to the left.:D

---

### Post by skumara on 2011-05-15
> **Quackers said:**
> Ok thanks, I'll take another look.
In the meantime can you tell me if you open a window (say Downloads, for instance) and move the window to the right does it slide under the conky display, or does the window cover conky up?

the window cover conky up when move it over conky

---

### Post by Quackers on 2011-05-15
Ok, thanks. That's good :-)
If you have a look at posts 9 and 10 and see if those fix your problem.

---

### Post by skumara on 2011-05-15
> **Quackers said:**
> Ok, thanks. That's good :-)
If you have a look at posts 9 and 10 and see if those fix your problem.

I did post 9 and 10 no change at all.

I noticed that if I change own_window_transparent yes to no I get black conky background and if I put yes I get brown conky background.

---

### Post by skumara on 2011-05-15
> **Quackers said:**
> Have you gone to sleep?

sorry . I&#7743; working now and I shouldn't be on-line while working. So I hope you understand why I go missing from on-line on and off....:D

---

### Post by Quackers on 2011-05-15
No problem :-) 
I can't explain what's happening with your conky background unless 000000 in
default_shade_color 000000
does not refer to black. In my conkyrc it reads default_shade_color black.
You could try that maybe.

---

### Post by skumara on 2011-05-15
i did it. Now the conky is transparent . I went to desktop setting and changed my wallpaper and conky is transparent. I don´t know why and how it happen. my final conky output is 

```
background yes
font Bitstream Vera Sans:size=8
xftfont Bitstream Vera Sans:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type background
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline yes
draw_borders yes
draw_graph_borders yes
minimum_size 300
maximum_width 310
default_color white
default_shade_color black
default_outline_color black
alignment top_right
gap_x 10
gap_y 35
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer yes

TEXT
$alignc Hostname: $nodename
$alignc Kernel: $kernel
$alignc Uptime: $uptime

CPU:
Core1:$alignr ${cpu cpu1}%@${freq_g cpu1}GHz ${cpubar cpu1 7,76} Temp: ${hwmon 0 temp 1}°C
Core2:$alignr ${cpu cpu2}%@${freq_g cpu2}GHz ${cpubar cpu2 7,76} Temp: ${hwmon 1 temp 1}°C
Overall Usage:$alignr $cpu% $alignr${cpubar 8,182}
${cpugraph 20,}
Highest CPU $alignr CPU%   MEM%
${top name 1}$alignr${top cpu 1}     ${top mem 1}
${top name 2}$alignr${top cpu 2}     ${top mem 2}

MEM:
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 8}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 8}
Highest MEM $alignr CPU%   MEM%
${top_mem name 1}$alignr${top_mem cpu 1}     ${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}     ${top_mem mem 2}

HDD: ${alignr} HDD Temp: ${execi 1 /home/saltedfish/.conky_script_hddtemp}°C
Linux: ${alignc} ${fs_bar 8,75} ${alignr} ${fs_free /}  /   ${fs_size /} (${fs_free_perc /}%)
SDA1: ${alignc} ${fs_bar 8,75 /media/sda1} ${alignr}${fs_free /media/sda1}  /   ${fs_size /media/sda1} (${fs_free_perc /media/sda1}%)
SDA2: ${alignc} ${fs_bar 8,75 /media/sda2} ${alignr}${fs_free /media/sda2}  /  ${fs_size /media/sda2} (${fs_free_perc /media/sda2}%)
${color white}Read:                                  ${color white}Write:${color red}
${color green}${diskiograph_read 20,150} ${alignr}${color red}${diskiograph_write 20,150}${color white}
${color green}${diskio_read}/s   ${alignr}${color red}${diskio_write}/s

${color white}LAN: ${alignr}IP: ${addr eth0}
${color green}LAN Download:                  $alignr${color red}LAN Upload:
${color green}${downspeedgraph eth0 20,150} ${alignr}${color red}${upspeedgraph eth0 20,150}
${color green}${downspeed eth0} k/s                                  ${alignr}     ${color red} ${upspeed eth0} k/s
${color green}Total:${totaldown eth0}  ${alignr}${color red}Total:${totalup eth0}

${color white}WiFi: ${color red}Don´t Show IP Address ${alignr}IP: ${addr wlan0}
AP ESSID: [${color orange}${wireless_essid wlan0}${color white}] ${alignr}AP Bitrate: ${color orange}${wireless_bitrate wlan0}${color white}
Link quality: ${wireless_link_qual_perc wlan0}% ${alignr}${wireless_link_bar 8,185 wlan0}
${color green}WiFi Download:                  $alignr${color red}WiFi Upload:
${color green}${downspeedgraph wlan0 20,150} ${alignr}${color red}${upspeedgraph wlan0 20,150}
${color green}${downspeed wlan0}KB/s ${color red}${alignr}${upspeed wlan0}KB/s
${color green}Total:${totaldown wlan0}  ${alignr}${color red}Total:${totalup wlan0}
${color white}AP Mode: ${wireless_mode wlan0} ${alignr}AP MAC: ${wireless_ap wlan0}
:D
```

---

### Post by Quackers on 2011-05-15
Aha! Excellent :-) A good result.

---

### Post by wildmanne39 on 2011-05-16
> **skumara said:**
> i did it. Now the conky is transparent . I went to desktop setting and changed my wallpaper and conky is transparent. I don´t know why and how it happen. my final conky output is 

```
background yes
font Bitstream Vera Sans:size=8
xftfont Bitstream Vera Sans:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type background
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline yes
draw_borders yes
draw_graph_borders yes
minimum_size 300
maximum_width 310
default_color white
default_shade_color black
default_outline_color black
alignment top_right
gap_x 10
gap_y 35
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer yes

TEXT
$alignc Hostname: $nodename
$alignc Kernel: $kernel
$alignc Uptime: $uptime

CPU:
Core1:$alignr ${cpu cpu1}%@${freq_g cpu1}GHz ${cpubar cpu1 7,76} Temp: ${hwmon 0 temp 1}°C
Core2:$alignr ${cpu cpu2}%@${freq_g cpu2}GHz ${cpubar cpu2 7,76} Temp: ${hwmon 1 temp 1}°C
Overall Usage:$alignr $cpu% $alignr${cpubar 8,182}
${cpugraph 20,}
Highest CPU $alignr CPU%   MEM%
${top name 1}$alignr${top cpu 1}     ${top mem 1}
${top name 2}$alignr${top cpu 2}     ${top mem 2}

MEM:
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 8}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 8}
Highest MEM $alignr CPU%   MEM%
${top_mem name 1}$alignr${top_mem cpu 1}     ${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}     ${top_mem mem 2}

HDD: ${alignr} HDD Temp: ${execi 1 /home/saltedfish/.conky_script_hddtemp}°C
Linux: ${alignc} ${fs_bar 8,75} ${alignr} ${fs_free /}  /   ${fs_size /} (${fs_free_perc /}%)
SDA1: ${alignc} ${fs_bar 8,75 /media/sda1} ${alignr}${fs_free /media/sda1}  /   ${fs_size /media/sda1} (${fs_free_perc /media/sda1}%)
SDA2: ${alignc} ${fs_bar 8,75 /media/sda2} ${alignr}${fs_free /media/sda2}  /  ${fs_size /media/sda2} (${fs_free_perc /media/sda2}%)
${color white}Read:                                  ${color white}Write:${color red}
${color green}${diskiograph_read 20,150} ${alignr}${color red}${diskiograph_write 20,150}${color white}
${color green}${diskio_read}/s   ${alignr}${color red}${diskio_write}/s

${color white}LAN: ${alignr}IP: ${addr eth0}
${color green}LAN Download:                  $alignr${color red}LAN Upload:
${color green}${downspeedgraph eth0 20,150} ${alignr}${color red}${upspeedgraph eth0 20,150}
${color green}${downspeed eth0} k/s                                  ${alignr}     ${color red} ${upspeed eth0} k/s
${color green}Total:${totaldown eth0}  ${alignr}${color red}Total:${totalup eth0}

${color white}WiFi: ${color red}Don´t Show IP Address ${alignr}IP: ${addr wlan0}
AP ESSID: [${color orange}${wireless_essid wlan0}${color white}] ${alignr}AP Bitrate: ${color orange}${wireless_bitrate wlan0}${color white}
Link quality: ${wireless_link_qual_perc wlan0}% ${alignr}${wireless_link_bar 8,185 wlan0}
${color green}WiFi Download:                  $alignr${color red}WiFi Upload:
${color green}${downspeedgraph wlan0 20,150} ${alignr}${color red}${upspeedgraph wlan0 20,150}
${color green}${downspeed wlan0}KB/s ${color red}${alignr}${upspeed wlan0}KB/s
${color green}Total:${totaldown wlan0}  ${alignr}${color red}Total:${totalup wlan0}
${color white}AP Mode: ${wireless_mode wlan0} ${alignr}AP MAC: ${wireless_ap wlan0}
:D
```
Hi, your welcome if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:)

---

