---
title: "conky startup problems"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by rm06 on 2009-10-01
I posted this in the Desktop Environment without response, hoping maybe someone here can help.

My conky configuration which has been working fine for quite some time is now not auto starting. I did recently "downgrade" from 64-bit 9.04 to 32 as it was simply causing too many headaches.

I have a .conky_start.sh script:

#!/bin/bash
sleep 30 && conky;
chmod a+x .conky_start.sh

And I'm referencing the location of this file in my startup sessions manager. I can manually execute the operation from the command line via either "conky" or "sh .conky_start.sh" without issue.

From the daemon.log file I found the following:

Sep 30 19:21:17 MyComputer x-session-manager[3506]: WARNING: Application 'compiz.desktop' failed to register before timeout

Sep 30 19:21:20 MyComputer x-session-manager[3506]: WARNING: Could not launch application '.conky_start.sh.desktop': Unable to start application: Failed to execute child process "/home/me/.conky_start.sh" (Permission denied)

I've changed the permissions on the desktop file to both root and myself through gedit and using chown, neither of which results in any difference and I still receive the errors. I've googled the errors and I've found some bugs for compiz though they don't seem to relate to the issues I've been experiencing.

Obviously this is a minor inconvenience having to start from the terminal as it is usually up anyway, though I'd like to understand and learn how to fix these "bugs" as they arise.

---

### Post by aktiwers on 2009-10-02
Couldn't you just add:
```
sleep 30 && conky
```

to your startup manager? 

If that does not work, you could add it to the end of your rc.local?

I don't understand why you chmod a+x in the script?

---

### Post by rm06 on 2009-10-02
> **aktiwers said:**
> Couldn't you just add:
```
sleep 30 && conky
```

to your startup manager? 

If that does not work, you could add it to the end of your rc.local?

I don't understand why you chmod a+x in the script?

'Cause I'm a scripting idiot and grabbed the example from the 'net; I read this line of code makes it executable. I mentioned previously I've been using this as my conky startup script for quite some time, my troubles beginning when I got a new computer. 

I'm happy to try it and I'll report back with results.

No dice - what exactly do you want me to add to the rc.local? The whole script? Perhaps I'm barking up the wrong tree but this doesn't explain the errors in the system log - I'm also receiving an error when opening the log /var/log/btmp "You don't have enough permissions to read the file" though the log appears as it did before.

---

### Post by aktiwers on 2009-10-03
Are you just trying to run Conky on startup?

then just add:
```
conky
``` 

to your start-up session manager.

About the script.. 
The chmod a+x is something you only need to run 1 time on your script to make it executable. 
Obviously you can't run this inside the script, because you do not have permission to run it
in the first place (ergo, the chmod command has not ben run yet). 

Now Im wondering why you need sleep 30?

rc.local is executed on boot with root rights. You could add your script there.
But what is it exactly you are trying to do, and why are you not just adding *conky* to your startup manager?

---

### Post by rm06 on 2009-10-03
Adding 'conky' to the startup works but apparently there is some conflict with Compiz as the conky will be drawn with borders. Using the sleep line lets the Compiz start completely before executing conky.

I will try the rc.local.

---

### Post by aktiwers on 2009-10-03
Please also post your .conkyrc and a screenshot.
I have compiz and my conky looks fine

Also I believe it would be enough to just add "conky" to rc.local

---

### Post by rm06 on 2009-10-03
.conkyrc:

```
background no
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_class Conky
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 300
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
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes
text_buffer_size 256

TEXT


${font openlogos:size=20}T ${font Arial:size=20}${color Tan1}J${font Arial:size=20}${color Ivory}Hancock

${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}

${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
$font${color DimGray}CPU1  ${cpu cpu1}% ${cpubar cpu1}
CPU2  ${cpu cpu2}% ${cpubar cpu2}
CPU3  ${cpu cpu3}% ${cpubar cpu3}
CPU4  ${cpu cpu4}% ${cpubar cpu4}

${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar

${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %

${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color DimGray}IP on eth0 $alignr ${addr eth0}

Down $alignr ${downspeed eth0} kb/s
Up $alignr ${upspeed eth0} kb/s

Downloaded: $alignr  ${totaldown eth0}
Uploaded: $alignr  ${totalup eth0}

${font Arial:bold:size=10}${color Tan2}TIME ${color DarkSlateGray}${hr 2}

${color LightGray} ${font :size=30}$alignc${time %I:%M%p}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}
$endif
```

screenshot - manually started conky:

[IMG]http://i35.tinypic.com/rvvxg2.png[/IMG]

---

### Post by rm06 on 2009-10-03
I'm not sure I know what the difference is, however for the command under the startup programs I added "sh .conky_start.sh" which starts conky as referenced by my script.

Dunno, it sounds like there are quite a few ways to get this to work.  aktiwers - I appreciate the persistent assistance - sounds like a long way north to get south, though it seems to work fine:)

---

### Post by aktiwers on 2009-10-05
Glad I could help. Did you solve the problem then? :)

---

### Post by rm06 on 2009-10-05
Solved, thanks again.

---

### Post by Squideshi on 2010-05-02
> **rm06 said:**
> I'm also receiving an error when opening the log /var/log/btmp "You don't have enough permissions to read the file" though the log appears as it did before.

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/374320)

---

