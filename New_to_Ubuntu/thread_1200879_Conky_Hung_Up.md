---
title: "Conky Hung Up?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Doman on 2009-06-30
Whenever I try to start conky I get hung up at the following: 

```

X@X:~$ conky
Conky: $endif: no matching $if_*
Conky: forked to background, pid is 15376
X@X:~$ 
Conky: desktop window (14000a8) is subwindow of root window (ab)
Conky: window type - normal
Conky: drawing to created window (0x4c00001)
Conky: drawing to double buffer


```

What am I doing wrong?

---

### Post by m_duck on 2009-06-30
Can you post your config? From the error it just means that you have too many $endif's, one is not matched to an $if statement.

---

### Post by Doman on 2009-06-30
I pretty much copied and pasted bits from a bunch of people and tweaked it, so idk a lot of the proper syntax.

```

background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 400
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color gray
default_shade_color red
default_outline_color green
alignment top_right
gap_x 10
gap_y 10
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer right
text_buffer_size 256

TEXT

${font openlogos:size=20}U${font Arial:size=20}${color 911919}GNU${color Ivory}LINUX${font openlogos:size=20}t

${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color 911919}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}

${font Arial:bold:size=10}${color 911919}PROCESSORS ${color DarkSlateGray}${hr 2}
$font${color DimGray}CPU1  ${cpu cpu1}% ${cpubar cpu1}
${font Arial:bold:size=10}${color 911919}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar

${font Arial:bold:size=10}${color 911919}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}Root: $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}
Doman: $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

${font Arial:bold:size=10}${color 911919}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %

${font Arial:bold:size=10}${color 911919}NETWORK ${color DarkSlateGray}${hr 2}
SSID: $alignr ${wireless_essid wlan0}
Connection quality: $alignr ${wireless_link_qual_perc wlan0}%

$font${color DimGray}IP on wlan0 $alignr ${addr wlan0}
$font${color DimGray}IP on eth0 $alignr ${addr eth0}

Down $alignr ${downspeed eth0} kb/s
Up $alignr ${upspeed eth0} kb/s

Downloaded: $alignr  ${totaldown eth0}
Uploaded: $alignr  ${totalup eth0}

$endif

```

---

### Post by Doman on 2009-06-30
Edit: I've changed a lot in there and figured it out.  I still have that hanging If statement I think though.  

and 
```

$font${color DimGray}IP on wlan0 $alignr ${addr wlan0}
$font${color DimGray}IP on eth0 $alignr ${addr eth0}

```isn't working.  I assume it's because wlan0 and eth0 aren't the right variables.  I'm leaning towards the unix equiv. of ipconfig, but I don't know.  Thoughts?

Also, is there a way to make multiple columns?

---

### Post by m_duck on 2009-06-30
I think it's just hanging from the very last line **$endif** as there don't seem to be any if statements within the config, so delete that and you should be sorted as far as that error is concerned.

Check the ouput of **ifconfig** and **iwconfig** in the terminal, these will list your network devices. It is possible that your wireless interface is wrong and is something like ath0, eth1 or something (though I thought conky usually gave an error on that).

For columns there are two choices I think really. The first choice is to have 2 separate config files with different placement and size options, and launching them like:```
conky -c config1; conky -c config2
```The second option is to use the **goto** variable:```
TEXT
column1${goto 50}column2
```

Edit: for the network problem, is only one of the interfaces displaying properly as I believe only on connection can be active at a time by default so conky will only give the info for the active connection.

---

