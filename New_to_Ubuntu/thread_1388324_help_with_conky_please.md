---
title: "help with conky please"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by nitstorm on 2010-01-23
hi i have a simple conky and i have been looking around to add the following to my conky:
1. CPU fan speed
2. Casing fan speed
2. CPU temperature
3. HDD temperature and speed
4. ACPI temperature ( jus curious what it means, i have no clue)
5. Weather conditions

this is the conky i have at present, i took one from some other site and slightly moded it. it would be great if someone could post the actual step-by-step tutorial to add the above stuff into my conky. looked up quite a few sites but nothing seems to have it step-by-step for beginners. i have a core2duo i686 architecture, 2 gb ram running karmic if you needed that info. 

Thanks for all the help in advance.

P.S: i have installed lm-sensors :)

---

### Post by nitstorm on 2010-01-23
Sorry forgot to attach my conky and screenshot

```

    background yes
    use_xft yes
    xftfont 123:size=8
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 250 5
    maximum_width 200
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
    use_spacer yes
    text_buffer_size 256

    TEXT

    ${font openlogos:size=20}${font Arial:size=20}${color Tan1}GNU${color Ivory}LINUX${font openlogos:size=20}

    ${voffset -90}
    ${color DimGray} ${font}
    ${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
   $font${color DimGray}$sysname $kernel $alignr $machine
    Uptime $alignr${uptime}
    
    ${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
   $font${color DimGray}CPU1  ${cpu cpu1}% ${cpubar cpu1}
     CPU2  ${cpu cpu2}% ${cpubar cpu2}

    ${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
   $font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
    $membar
    $font${color DimGray}SWAP $alignc $swap / $swapmax $alignr $swapperc%      
    $swapbar

    ${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
   $font${color DimGray}Filesystem $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
    ${fs_bar /home}
    Disc1 $alignc ${fs_used /media/Disk1} / ${fs_size /media/Disk1} $alignr ${fs_used_perc /media/Disk1}%
    ${fs_bar /media/Disk1}
    Disc2 $alignc ${fs_used /media/Disk2} / ${fs_size /media/Disk2} $alignr ${fs_used_perc /media/Disk2}%
    ${fs_bar /media/Disk2}
    Disc3 $alignc ${fs_used /media/Disk3} / ${fs_size /media/Disk3} $alignr ${fs_used_perc /media/Disk3}%
    ${fs_bar /media/Disk3}

    ${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
   ${color DimGray}$font${top name 1}${alignr}${top mem 1} %
    $font${top name 2}${alignr}${top mem 2} %
    $font${top name 3}${alignr}${top mem 3} %
    $font${top name 4}${alignr}${top mem 4} %
    $font${top name 5}${alignr}${top mem 5} %

    ${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
   $font${color DimGray}IP on eth0 $alignr ${addr eth0}
    
    Down $alignr ${downspeed eth0}/s 
    Up $alignr ${upspeed eth0}/s 

    Downloaded: $alignr  ${totaldown eth0}
    Uploaded: $alignr  ${totalup eth0}
   
    ${font Arial:bold:size=10}${color Tan2}TIME ${color DarkSlateGray}${hr 2}

    ${color DarkSlateGray} ${font :size=30}$alignc${time %H:%M}
    ${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
    ${font :bold:size=8}$alignc${time %A}
    

 
```

---

### Post by nitstorm on 2010-01-23
bump!

---

### Post by TironN on 2010-01-23
I'm not sure but go to:

/usr/share/doc/conky-all

and look at the greatness in there!

---

### Post by nitstorm on 2010-01-23
looked into that earlier itself... but it didnt work for me :(

---

### Post by VCoolio on 2010-01-23
The built-in weather stuff in conky doesn't work for me; try [this]("http://ubuntuforums.org/showthread.php?t=869328") or [this]("http://conky.linux-hardcore.com/?page_id=2381")

For cpu temp I use (with lm-sensors installed and detected by running sudo sensors-detect):
```
${execpi 10 sensors | grep CPU | cut --characters 15-16}°C
```
You can colorize like explained [here]("http://conky.linux-hardcore.com/?page_id=747").

---

### Post by nitstorm on 2010-01-23
tried the sudo sensors-detect, giving yes to everything , still wont work for me, got the following error

> 
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.


---

### Post by teresaejunior on 2010-01-23
All possible conky variables are here: [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

The easiest way: open your text editor (not OpenOffice!). Gedit in Ubuntu, Kate in Kubuntu. 

Click in 'Open File'. Type '.conkyrc', don't forget the DOT., leave out the quotes.

or type 'mcedit .conkyrc' in a terminal, and F2 to save, F10 to exit...

1. CPU fan speed
2. Casing fan speed
try adding a line with the following att the bottom:
fan state: ${acpifan}
in my machine fan stuff doesn't work, as shown in the /proc filesystem

2. CPU temperature
add a line with the following att the bottom:
cpu temp: ${acpitemp}°C

3. HDD temperature and speed
they say: hddtemp 	dev, (host,(port)) 	Displays temperature of a selected hard disk drive as reported by the hddtemp daemon running on host:port. Default host is 127.0.0.1, default port is 7634.

first make sure you have hddtemp installed. in a terminal type
sudo apt-get install hddtemp

and later check if it's running
pidof hddtemp

4. ACPI temperature ( jus curious what it means, i have no clue)
this is the cpu temp

5. Weather conditions
this is a big one and well explained at that page. First let me know if you've got the above.

---

### Post by nitstorm on 2010-01-23
got an installed hddtemp but *pidof hddtemp* gives no output... and tried the fan state, says no fans :S

---

### Post by teresaejunior on 2010-01-24
When hddtemp is running, pidof hddtemp should give you the pid number. Try restarting the computer, so hddtemp would start together. Or simply add the following line and see if it works, if it doesn't, reboot... or run hddtemp manually:

to your .conkyrc:

hd temp: ${hddtemp /dev/sda 127.0.0.1 7634}

/dev/sda is the disk device name, should you run 'df' in a terminal to get the name if you don't know. Despise the number which comes together (sda1 or sda2), they are partition names.

I can't help that much with fans, I could never get this to work...
i don't think lm-sensors has anything to do with conky...

Anyway, did you get the cpu temp???

---

### Post by teresaejunior on 2010-01-24
> **nitstorm said:**
> got an installed hddtemp but *pidof hddtemp* gives no output... and tried the fan state, says no fans :S

it could say "no fun" ;b

---

### Post by nitstorm on 2010-01-24
nope doesn't work. definitely becoming more drab. jus going to give up for a while on conky or something..

---

