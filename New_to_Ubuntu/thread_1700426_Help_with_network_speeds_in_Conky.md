---
title: "Help with network speeds in Conky"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by willhurley82 on 2011-03-05
Here's my problem.  I cannot get the conky configuration I'm using to give me my upload and download speeds.  I'm pretty sure I have it right, but am a novice when it comes to Linux.  I've checked around online and tried to figure this out, but lack the experience and luck to do so.  I'll post the config.  Any help would be appreciated.  :)

Dave

I'm running Ubuntu 10.10
The conky configuration is as follows:  



# Conky settings #
background no
update_interval 1


cpu_avg_samples 2
net_avg_samples 2

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048
#imlib_cache_size 0


# Window specifications #

own_window yes
on_bottom yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

border_inner_margin 0
border_outer_margin 0

minimum_size 200 250
maximum_width 200

alignment tr
gap_x 35
gap_y 55

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5

uppercase no



default_color FFFFFF

# Lua Load  #
lua_load ~/.lua/scripts/clock_rings.lua
lua_draw_hook_pre clock_rings

TEXT
${voffset 8}${color FF6600}${font caviar dreams:size=16}${time %A}${font}${voffset -8}${alignr 50}${color FFFFFF}${font caviar dreams:size=38}${time %e}${font}
${color FFFFFF}${voffset -30}${color FFFFFF}${font caviar dreams:size=18}${time %b}${font}${voffset -3} ${color FFFFFF}${font caviar dreams:size=20}${time %Y}${font}${color FF6600}${hr}
${voffset 140}${font caviar dreams:size=10}${alignr}HOME${font}
${font caviar dreams:size=12}${color FFFFFF}${alignr}${weather [http://weather.noaa.gov/pub/data/observations/metar/stations/](http://weather.noaa.gov/pub/data/observations/metar/stations/) LQBK temperature temperature 30} temperature_unit fahrenheit °F${font}

${color FFFFFF}${goto 25}${voffset 35}${cpu cpu0}%
${color FF6600}${goto 25}CPU
${color FFFFFF}${goto 50}${voffset 23}${memperc}%
${color FF6600}${goto 50}RAM
${color FFFFFF}${goto 75}${voffset 23}${swapperc}%
${color FF6600}${goto 75}Swap
${color FFFFFF}${goto 100}${voffset 23}${fs_used_perc /}%
${color FF6600}${goto 100}Disk
${color FFFFFF}${goto 125}${downspeed wlan0}
${color FFFFFF}${goto 125}${upspeed wlan0}
${color FF6600}${goto 125}Net



${color FFFFFF}${font caviar dreams:size=8}Uptime: ${uptime_short}
${color FFFFFF}${font caviar dreams:size=8}Processes: ${processes}
${color FFFFFF}${font caviar dreams:size=8}Running: ${running_processes}


${color FF6600}${font caviar dreams:size=8}${alignr}${nodename}
${color FF6600}${font caviar dreams:size=8}${alignr}${pre_exec cat /etc/issue.net}  $machine
${color FF6600}${font caviar dreams:size=8}${alignr}Kernel: ${kernel}

---

### Post by alindgr1 on 2011-03-05
This section of your config below says "wlan0" which would mean that you have a wireless internet connection.  This can be different, though, and should be checked.  Type ifconfig into the terminal (Applications, Accessories, Terminal) and you will see several sets of information.  Look for the set that has an IP address on the line that starts with "inet addr:"  Ensure that your Conky config matches the title of that set of information on the left side of the terminal window.

${color FFFFFF}${goto 125}${downspeed **wlan0**}
${color FFFFFF}${goto 125}${upspeed **wlan0**}

Hope that helps.

---

### Post by willhurley82 on 2011-03-05
I think I had it right, but the speeds are not showing.  Here's the results of ifconfig:




eth0      Link encap:Ethernet  HWaddr 00:1d:72:70:72:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12000 (12.0 KB)  TX bytes:12000 (12.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:69:25:cd:5c  
          inet addr:10.1.1.50  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:69ff:fe25:cd5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80463199 (80.4 MB)  TX bytes:16033446 (16.0 MB)

---

### Post by alindgr1 on 2011-03-05
Just out of curiosity, have you tried upspeedf and downspeedf yet?  Also, if you start Conky in a terminal, it will output status messages and errors that may help you.

---

### Post by willhurley82 on 2011-03-05
Ah, good looking out.  I have not tried uploadf and downloadf yet, wasn't aware that they existed.  I'll try those and I've done "killall conky" then "conky &", no errors show though.  Do I need to monitor it, somehow, from the Terminal?

---

### Post by Quackers on 2011-03-05
What connection are you using? Ethernet or wireless?
Here are my wireless settings in my .conkyrc
```
${font Terminus:style=bold:size=11}WIRELESS NETWORK $hr
Connection Quality: $alignr ${wireless_link_qual wlan0}%
D/L: ${downspeed wlan0}/s $alignr ${totaldown wlan0}
U/L: ${upspeed wlan0}/s $alignr ${totalup wlan0}
```
Obviously this will not work if you are using ethernet.

---

### Post by willhurley82 on 2011-03-05
I'm using wireless, and have read some of your posts, Quackers.  I checked different device managers and have changed "wlan0" around some, but to no avail.  

Here's where I'm at now, with the network code, doesn't work, but it's the direction I've been going.  I just tried upspeedf and downspeedf, but not with the if_connected parts in it, will do that now and post if sucessfull:


${color FFFFFF}${goto 125}${downspeedf wlan0}
${color FFFFFF}${goto 125}${if_connected eth0}${upspeed eth0}${else}${if_connected lo}${else}${if_connected wlan0}${upspeedf wlan0}
${color FF6600}${goto 125}Net


EDIT:  Neither upspeed or upspeedf worked with this test

---

### Post by willhurley82 on 2011-03-05
Should this be moved to a different section?  Also, I'm running this kernal, if that makes a difference 2.6.35-27

EDIT:

Going to try this:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=563401](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=563401)

---

### Post by willhurley82 on 2011-03-06
Compiling Conky failed for me.  I do not think I installed it in the correct place.  I had to reinstall Conky with Software Updater.   I'm wondering if there is a way to enable wlan in conky after installation, not during.

---

### Post by Quackers on 2011-03-06
I did have a go with the if up command but I could not get it working. I'm not a scripter :-)
Check wether your system uses wlan0, I think some systems use wlan1 or other variables perhaps.
Not sure what you mean by
"enable wlan in conky after installation, not during."

---

### Post by willhurley82 on 2011-03-06
Wlan0 comes up in my device manager and command tool outputs, for my wireless adapter.  

The enable wlan comment is from me looking at this page:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=563401](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=563401)

I'm not a programmer, by any means either, so I totally understand.  :D

---

### Post by Quackers on 2011-03-06
Try copy/pasting the last 3 lines of what I posted in post #6 into your .conkyrc file (but temporarily move your wlan section out first) and see if you get any output in your conky display from that.
I haven't needed to use anything from that post you quoted.

---

### Post by willhurley82 on 2011-03-06
You guys are going to kill me.  

I went up a directory and found another conkyrc file.  I was editing the backup file the entire time.  *facepalm*  :oops:

I am so sorry, for being so negligent.  Thank you both, very, very much, for helping me out.  Now to figure out how to mark this one solved.

---

### Post by Quackers on 2011-03-06
No problem at all. I hope everything goes well :-)
To mark the thread as solved when viewing this post, go to the top of the page and click on Thread Tools and select "Mark as solved"

---

