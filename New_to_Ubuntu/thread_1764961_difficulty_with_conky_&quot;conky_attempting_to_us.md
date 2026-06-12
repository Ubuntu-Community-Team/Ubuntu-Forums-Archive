---
title: "difficulty with conky &quot;conky attempting to use more CPUs than you have&quot;"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by Newbuntubie on 2011-05-22
Trying to install conky but it's saying that it's attempting to use more CPU's than I have.
This is the code. Any help would be really appreciated!!!

#############################
##  VinDSL | 1280x1024x24  ##
#############################
 
####
## Use XFT? Required to Force UTF8 (see below).
#
use_xft yes
xftfont LiberationSans:size=9
xftalpha 0.1
text_buffer_size 2048
 
####
## Force UTF8? Requires XFT (see above).
## Displays degree symbol, instead of &Acirc;&deg;, etc.
#
override_utf8_locale yes
 
####
## Update interval in seconds.
#
update_interval 1.5
 
####
## This is the number of times Conky will update before quitting.
## Set to zero to run forever.
#
total_run_times 0
 
####
## Create own window instead of using desktop (required in nautilus)?
#
own_window yes
own_window_type override
own_window_transparent yes
 
####
## Use double buffering? Reduces flicker.
#
double_buffer yes
 
####
## Draw shades?
#
draw_shades no
 
####
## Draw outlines?
#
draw_outline no
 
####
## Draw borders around text?
#
draw_borders no
 
####
## Draw borders around graphs?
#
draw_graph_borders no
 
####
## Print text to stdout?
## Print text in console?
#
out_to_ncurses no
out_to_console no
 
####
## Text alignment.
#
alignment top_right
 
 
####
## Minimum size of text area.
#
minimum_size 235 0
 
####
## Specify width and height for bars.
#
default_bar_size 0 4
 
####
## Gap between text and screen borders.
#
gap_x 400
gap_y 28
 
####
## Shorten MiB/GiB to M/G in stats.
#
short_units yes
 
####
## Pad % symbol spacing after numbers.
#
pad_percents 0
 
####
## Limit the length of names in &quot;Top Processes&quot;.
#
top_name_width 10
 
####
## Subtract file system -/+buffers/cache from used memory?
## Set to yes, to produce meaningful physical memory stats.
#
no_buffers yes
 
####
## Set to yes, if you want all text to be in UPPERCASE.
#
uppercase no
 
####
## Number of cpu samples to average.
## Set to 1 to disable averaging.
#
cpu_avg_samples 4
 
####
## Number of net samples to average.
## Set to 1 to disable averaging.
#
net_avg_samples 2
 
####
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right
 
####
## My colors.
#
color0 White
color1 Ivory
color2 Ivory2
color3 Ivory3
color4 Tan1
color5 Tan2
color6 Gray
color7 AntiqueWhite4
color8 DarkSlateGray
color9 Black
 
TEXT
 
##################
##     LOGO     ##
##################
${voffset -42}${font OpenLogos:size=103}${color2}v${voffset -66}${goto 178}${font UbuntuTitleBold:size=20}${color4}10.10
##################
##    SYSTEM    ##
##################
${voffset 10}${font Arial:bold:size=9.5}${color4}SYSTEM ${color8} ${hr 2}
${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font}${color6} ${sysname} ${kernel} ${alignr} ${machine}
${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font}${color6} Intel I5 ${alignr}${freq_g cpu0} GHz
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font}${color6} Uptime ${alignr}${uptime}
${voffset 2}${font StyleBats:size=10}${color2}o${voffset -1}${font}${color6} File System ${alignr}${fs_type}
##################
##  PROCESSORS  ##
##################
${voffset 5}${font Arial:bold:size=9.5}${color4}PROCESSORS ${color8}${hr 2}
${voffset 2}${font StyleBats:size=10}${color2}k${voffset -2}${font}${color6} CPU1  ${cpu cpu1}%${color7}${alignc 35}${cpubar cpu1}
${voffset 2}${font StyleBats:size=10}${color2}k${voffset -2}${font}${color6} CPU2  ${cpu cpu2}%${color7}${alignc 35}${cpubar cpu2}
${voffset 2}${font StyleBats:size=10}${color2}k${voffset -2}${font}${color6} CPU3  ${cpu cpu3}%${color7}${alignc 35}${cpubar cpu3}
${voffset 2}${font StyleBats:size=10}${color2}k${voffset -2}${font}${color6} CPU4  ${cpu cpu4}%${color7}${alignc 35}${cpubar cpu4}
##################
##    MEMORY    ##
##################
${voffset 5}${font Arial:bold:size=9.5}${color4}MEMORY ${color8}${hr 2}
${voffset 2}${font StyleBats:size=10}${color2}l${voffset -2}${font}${color6} RAM ${goto 95}${mem}/ ${memmax}${alignr}${memperc}%
${color7}${membar}
##################
##     HDD      ##
##################
${voffset 2}${font Arial:bold:size=9.5}${color4}HDD ${color8}${hr 2}
${voffset 2}${font StyleBats:size=10}${color2}x${voffset -2}${font}${color6} ROOT ${goto 95}${fs_used /} / ${fs_size /}${alignr}${fs_free_perc /}%
${color7}${fs_bar /}
${voffset 1}${font StyleBats:size=10}${color2}x${voffset -2}${font}${color6} HOME ${goto 95}${fs_used /home}/ ${fs_size /home}${alignr}${fs_free_perc /home}%
${color7}${fs_bar /home}
${voffset 1}${font StyleBats:size=10}${color2}x${voffset -2}${font}${color6} Data ${goto 95}${fs_used /data}/ ${fs_size /data}${alignr}${fs_free_perc /data}%
${color7}${fs_bar /data}
${voffset 1}${font StyleBats:size=10}${color2}4${voffset -2}${font}${color6} SWAP ${goto 95}${swap} / ${swapmax}${alignr}${swapperc}%
${color7}${swapbar}
##################
# TOP PROCESSES ##
##################
${voffset 3}${font Arial:bold:size=9.5}${color4}TOP PROCESSES ${color8}${hr 2}
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font}${color6} ${top_mem name 1}${goto 115}${top_mem mem_res 1}${alignr}${top_mem mem 1}%
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font}${color6} ${top_mem name 2}${goto 115}${top_mem mem_res 2}${alignr}${top_mem mem 2}%
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font}${color6} ${top_mem name 3}${goto 115}${top_mem mem_res 3}${alignr}${top_mem mem 3}%
${voffset 2}${font StyleBats:size=10}${color1}h${voffset -3}${font}${color6} ${top_mem name 4}${goto 115}${top_mem mem_res 4}${alignr}${top_mem mem 4}%
##################
##   NETWORK    ##
##################
${voffset 5}${font Arial:bold:size=9.5}${color4}NETWORK ${color8}${hr 2}
${voffset 2}${font PizzaDude Bullets:size=10}${color2}a${font}${color6} Private IP${alignr}${addr eth0}
${font PizzaDude Bullets:size=10}${color2}a${font}${color6} Public  IP${alignr}${execi 600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${voffset 4}${font PizzaDude Bullets:size=10}${color2}T${font}${color6} Down${alignr}${downspeed eth0}
${font PizzaDude Bullets:size=10}${color2}N${font}${color6} Up${alignr}${upspeed eth0}
${voffset 4}${font PizzaDude Bullets:size=10}${color2}T${font}${color6} Downloaded${alignr}${totaldown eth0}
${font PizzaDude Bullets:size=10}${color2}N${font}${color6} Uploaded${alignr}${totalup eth0}

---

### Post by Vaphell on 2011-05-22
what cpu do you have?

---

### Post by Frogs Hair on 2011-05-22
I appears that the script was made for a quad core processor .```
## PROCESSORS ##
 ##################
 ${voffset 5}${font Arial:bold:size=9.5}${color4}PROCESSORS ${color8}${hr 2}
 ${voffset 2}${font StyleBats:size=10}${color2}k${voffset -2}${font}${color6} CPU1 ${cpu cpu1}%${color7}${alignc 35}${cpubar cpu1}
 ${voffset 2}${font StyleBats:size=10}${color2}k${voffset -2}${font}${color6} CPU2 ${cpu cpu2}%${color7}${alignc 35}${cpubar cpu2}
 ${voffset 2}${font StyleBats:size=10}${color2}k${voffset -2}${font}${color6} CPU3 ${cpu cpu3}%${color7}${alignc 35}${cpubar cpu3}
 ${voffset 2}${font StyleBats:size=10}${color2}k${voffset -2}${font}${color6} CPU4 ${cpu cpu4}%${color7}${alignc 35}${cpubar cpu4}
 ##################
```
You could try making a backup copy of the conkyrc as it is then remove the additional unused cpu entries in your working conkyrc. 

Use Alt+F2 killall conky , change the conkyrc and then Alt+F2 conky to start. The most that will happen is it won't work and if that is the case you have a backup.

---

### Post by Dondermans on 2011-05-22
I concur with Frogs Hair. Here's a bit more on how to find out what CPU you have:

Open a terminal and enter ```
 sudo lshw -class cpu
``` If you have difficulties interpreting the results you can paste the result here. Mine looks like this:

```
~$ sudo lshw -class cpu
  *-cpu                   
       description: CPU
       product: AMD Phenom(tm) II X4 955 Processor
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: AMD Phenom(tm) II X4 955 Processor
       slot: Socket M2
       size: 800MHz
       capacity: 3200MHz
       width: 64 bits
       clock: 200MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
```The amount of cores can be deduced by deviding [capacity/size], or (in my case) 3200/800 = 4 cores. Therefore I can use four lines under the Processors category. You should remove the lines containing code for cores that are not physically present.

The following lines in the code appear to be causing the problem:
```
##################
##  PROCESSORS  ##
##################
${voffset 5}${font Arial:bold:size=9.5}${color4}PROCESSORS ${color8}${hr 2}
${voffset 2}${font StyleBats:size=10}${color2}k${voffset  -2}${font}${color6} **CPU1**  ${cpu cpu1}%${color7}${alignc 35}${cpubar  cpu1}
${voffset 2}${font StyleBats:size=10}${color2}k${voffset  -2}${font}${color6} **CPU2**  ${cpu cpu2}%${color7}${alignc 35}${cpubar  cpu2}
${voffset 2}${font StyleBats:size=10}${color2}k${voffset  -2}${font}${color6} **CPU3**  ${cpu cpu3}%${color7}${alignc 35}${cpubar  cpu3}
${voffset 2}${font StyleBats:size=10}${color2}k${voffset  -2}${font}${color6} **CPU4**  ${cpu cpu4}%${color7}${alignc 35}${cpubar  cpu4}
```Each line that starts with ${voffset 2} refers to one CPU core. I added a bit of bold to illustrate this. You probably have less than four cores. When trying to detect cores you do not have you get an error message.

The quick 'n dirty fix:
When I refer to commenting in the next bit of this message I mean adding a # before the line, uncomment is removing # before a line.

You can try to comment the last three lines under the processors header:

```
##################
##  PROCESSORS  ##
##################
${voffset 5}${font Arial:bold:size=9.5}${color4}PROCESSORS ${color8}${hr 2}
${voffset 2}${font StyleBats:size=10}${color2}k${voffset  -2}${font}${color6} **CPU1**  ${cpu cpu1}%${color7}${alignc 35}${cpubar  cpu1}
**#**${voffset 2}${font StyleBats:size=10}${color2}k${voffset  -2}${font}${color6} **CPU2**  ${cpu cpu2}%${color7}${alignc 35}${cpubar  cpu2}
**#**${voffset 2}${font StyleBats:size=10}${color2}k${voffset  -2}${font}${color6} **CPU3**  ${cpu cpu3}%${color7}${alignc 35}${cpubar  cpu3}
**#**${voffset 2}${font StyleBats:size=10}${color2}k${voffset  -2}${font}${color6} **CPU4**  ${cpu cpu4}%${color7}${alignc 35}${cpubar  cpu4}
```The script should run if you leave the CPU1 line untouched. Every time you hit the 'Save' button when editing .conky.rc Conky should update. Starting from the top, you can try to detect an additional core by removing the '#' sign preceding the line. If you get the error again, add the '#' again. The next step would be to remove the lines which cause a problem when you uncomment them.

---

