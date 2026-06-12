---
title: "conky hidden by unity bar"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by amiacamal on 2011-08-04
Just as the title says...   I realise its probably something simple but iv never used conky before!

---

### Post by zealibib slaughter on 2011-08-04
adjust the alignment or gap_x and gap_y in your conky config file (.conkyrc)
you will be looking for lines that look like this
```
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10


```

---

### Post by amiacamal on 2011-08-04
hmmmm.... i see it but what do i change it too? :)

---

### Post by zealibib slaughter on 2011-08-04
For the alignment try to change it to top_right or bottom_right, and that should move it to the top or bottom right of your screen.  the _x and _y this is measured in pixels from the alignment point assignment so if you set it to top_right then a gap_y setting of 20 is 20 pixels below the top of your screen.  Set your alignment first and save the file.  Kill conky and restart to see the change.  Then you can play around with the gap settings.
 
Here is the explanations of the conky config settings
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)
also there is a cool thread of conky configs here 
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
 
These helped me alot when I was learning about conky.

---

### Post by amiacamal on 2011-08-04
It seems to not be doing anything.... even changing the gap to like... 900 doesnt seem to help!

---

### Post by zealibib slaughter on 2011-08-04
have you killed and restarted conky
sudo killall conky to kill conky then restart conky.
 
also post your .conkyrc file

---

### Post by amiacamal on 2011-08-05
Sorry for my lack of reply last night, i fell asleep :/
Im at work now and catching a bus after that so ill post my conky file later. Its prob worth pointing out however, that its someone elses file, taken from the "post your conky" thread. i just copied one at random to get something working!

---

### Post by zealibib slaughter on 2011-08-05
Hey thats cool, in fact thats how I got my first conky setup.

---

### Post by Frogs Hair on 2011-08-05
> **amiacamal said:**
> It seems to not be doing anything.... even changing the gap to like... 900 doesnt seem to help!

You may know this , but remember to save changes to the .conkyrc . If you change a value while Conky is running and don't save it , nothing will happen.

---

### Post by hookitup on 2011-08-05
not sure if you know but when you see 

#alignment top_left 
[COLOR=Red]alignment top_right[/COLOR] 
#alignment bottom_left
#alignment bottom_right 

the one without the # sign is what is applied ,,, so simply put a # in front of the current one and delete the # in front of the position you want it to be in,,, in your case the top or botten right, then save , conky should automatically switch after saving.

in the config above the red one will be showing because it has no # sign.


hope this helps

---

### Post by amiacamal on 2011-08-05
Yup, i know how to uncomment/comment lines, and restart conky, tho that part i may be doing wrong as it doesnt seem to be doing anything! i mean the allignment never changed!

---

### Post by zealibib slaughter on 2011-08-05
did you tell conky to load your .conkyrc file instead of the one at /etc/conky/conky.conf

---

### Post by amiacamal on 2011-08-05
This is the file by the way...     ninja edit, whats the syntax for showing code? pasted it in there and it looked awful...  im starting conky using "conky -c ~/Conky/conkymain" conkymain being the file, i realise conkyrc is used by most, but the setup guide i used said that..... :/

---

### Post by zealibib slaughter on 2011-08-05
is it formatted like that?

---

### Post by amiacamal on 2011-08-05
> **zealibib slaughter said:**
> is it formatted like that?

   no its not formatted like that, i just pasted it in :/

---

### Post by zealibib slaughter on 2011-08-05
the # sign in the post message toolbar gives you "[code]" tags or type what i done and end it the same but with a / like html works to

---

### Post by zealibib slaughter on 2011-08-05
Are you using a autostart script?

---

### Post by amiacamal on 2011-08-05
Lets try this...

```
 # Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Sans:style=Bold:size=10

# Text alpha when using Xft
xftalpha 1

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 5

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 5

# border width
border_width 10

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 1000
gap_y 1000

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color white}CPU Usage:${color white} $cpu%  <->  ${color white}File systems: ${color white}${fs_used /} of ${fs_size /}   <->  ${time %l:%M %a %b %d}  <->  ${color white}RAM Usage:${color white} $mem of $memmax ${color white}= ${color white}$memperc%  
${color white}IN:${downspeed eth0}k/s  <->  ${color white}OUT:${upspeed eth0}k/s  <->  ${color white}Connections: ${tcp_portmon 1 65535 count}  
${color white}Netstat 
${color white}${execi 2 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}
```

---

### Post by amiacamal on 2011-08-05
> **zealibib slaughter said:**
> Are you using a autostart script?


god my Internet here is atrocious...

If you mean a start conky with laptop startup, then no.
so far im just starting it from terminal. as i said i just wanna get something working before messin with it too much!

Incidentally, whats the "correct" way to stop conky?

---

### Post by zealibib slaughter on 2011-08-05
The only thing I see that may cause it to be anywhere near the unity bar is the _x 1000 and _y 1000.  I would change these to 10, save and restart conky.  That way it should appear 10 pixels from the right and 10 pixels from the top of your monitor. BTW are you using dual monitors?

---

### Post by amiacamal on 2011-08-05
> **zealibib slaughter said:**
> The only thing I see that may cause it to be anywhere near the unity bar is the _x 1000 and _y 1000.  I would change these to 10, save and restart conky.  That way it should appear 10 pixels from the right and 10 pixels from the top of your monitor. BTW are you using dual monitors?


The x and y at 1000 was me trying to make something change :P

nope, just the single laptop screen.

---

### Post by zealibib slaughter on 2011-08-05
killall conky always works for me
here is a bash script you can save as startstop.sh and save it somewhere. make it executable and you can click to start or stop conky. **BTW **i didn't write this but its the script i use.
```
#!/bin/sh
   # click to start, click to stop
    
   if pidof conky | grep [0-9] > /dev/null
   then
   exec killall conky
   else
   #sleep 3  # sleep not required for xfce on startup - 30 or more for others
   conky -c ~/Conky/conkymain
    exit
   fi

```

---

### Post by zealibib slaughter on 2011-08-05
try removing the own window setting.  Comment out everything for own window and see if that helps.  IDK since it isn't technically nautilus anymore it might work.

---

### Post by amiacamal on 2011-08-05
It still refuses to move.... im using killall to stop it and the command i gave earlier to start it. im very confused... :/

---

### Post by zealibib slaughter on 2011-08-05
Ok comment out the alignment top_right and uncomment alignment none.  Then try to adjust x and y.

---

### Post by amiacamal on 2011-08-05
```
conky -c ~/Conky/conkymain
Conky: invalid configuration file '/home/simon/Conky/conkymain'

Conky: desktop window (12000be) is subwindow of root window (15a)
Conky: window type - desktop
Conky: drawing to created window (0x3c00001)
Conky: drawing to single buffer
```invalid config all of a sudden...

it still started tho! same problem

---

### Post by zealibib slaughter on 2011-08-05
Well, undo the last change you made and make sure it works.  Then save it as something like conkybackup.  Now change your conkymain to this since I know it appears on the right side of my screen, if it shows up in the right place then we can get your script to act right if it doesn't then I am at a loss.
```
# Use Xft?
use_xft yes
xftfont OFL Sorts Mill Goudy:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
own_window_class conky
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 310 0 
#maximum_width 320

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_inner_margin 5

# border width
border_width 1

# Default colors and also border colors
#default_color white



# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 60

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 8

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

imlib_cache_size 0

color1 Ivory
color2 Ivory2
color3 Ivory3
color4 Tan1
color5 white
color6 Gray
color7 AntiqueWhite4
color8 DarkSlateGray
color9 Black
TEXT
##################
##     TIME     ##
##################
#${goto 85}${font OpenLogos:size=40}${color black} t ${goto 150}${font OpenLogos:size=40} T 
${font Arial:bold:size=12}${color4}Time ${color8}${hr 2}${color2}
${voffset 4}${font RadioSpace:size=32}${alignc 5}${time %R}
${voffset -10}${font RadioSpace:bold:size=18}${alignc}${time %A}, ${offset 5}${time %d %b}
##################
##     Email   ##
#################
${voffset 5}${if_up wlan0}${font Arial:bold:size=12}${color4}Mails ${color8}${hr 2}${color2}

${voffset -10}${goto 70}${font RadioSpace:bold:size=20}new Mails: ${font RadioSpace:bold:size=20}${execi 300 conkyEmail --servertype=IMAP --servername=YOUR IMAP --username=YOUR EMAIL --password=YOUR PASSWORD --ssl}
${endif}
##################
##     System   ##
##################

${voffset -70}${font Arial:bold:size=12}${color4}System ${color8}${hr 2}${color2}${font} 

${voffset 4}${color5}${font OpenLogos:size=16}u${font Arial:bold:size=11}${color2}   ${goto 45}${voffset -4}Ubuntu:   ${alignr}${kernel}
${voffset 4}${color5}${font OpenLogos:size=16}T${font Arial:bold:size=11}${color2}   ${goto 45}${voffset -4}Uptime:  ${alignr}${uptime}
${voffset 4}${color5}${font StyleBats:size=16}A${font Arial:bold:size=11}${color2}   ${goto 45}${voffset -4}CPU:  ${goto 108}${cpu cpu}% ${alignr} ${cpugraph cpu1 13,155 000000 000000}
${voffset 4}${color5}${font StyleBats:size=16}g${font Arial:bold:size=11}${color2}   ${goto 45}${voffset -4}RAM:  ${goto 108}$memperc% ${alignr} ${memgraph 13,155 000000 000000}
${voffset 4}${color5}${font PizzaDude Bullets:size=16}D${font Arial:bold:size=11}${color2}  ${goto 45}${voffset -4}CPU Temperature: ${alignr}${hwmon temp 1}${font Arial:bold:size=11} °C
${voffset 4}${color5}${font PizzaDude Bullets:size=16}A${font Arial:bold:size=11}${color2}  ${goto 45}${voffset -4}GPU Temperature:${alignr}${font Arial:bold:size=11}${color1} ${font Arial:bold:size=11}${exec nvidia-settings -q GPUCoreTemp | grep Attribute | cut -d ' ' -f 6 | cut -c 1-2} °C
##################
##     Network  ##
##################
${voffset 10}${if_up wlan0}${font Arial:bold:size=12}${color4}Network ${color8}${hr 2}${color2}
${voffset 10}${color5}${font PizzaDude Bullets:size=14}T ${color2}${font Arial:bold:size=11}${voffset -1}Down: ${goto 100}${downspeedf wlan0} KB ${alignr}${downspeedgraph wlan0 13,150 000000 000000}
${voffset 8}${color5}${font PizzaDude Bullets:size=14}N ${color2}${font Arial:bold:size=11}${voffset -1}Up: ${goto 100}${upspeedf wlan0} KB ${alignr}${upspeedgraph wlan0 13,150 000000 000000}
${voffset 8}${color5}${font PizzaDude Bullets:size=14}Z ${color2}${font Arial:bold:size=11}SSID:  ${wireless_essid wlan0}: ${alignr}${wireless_link_qual wlan0}%
##################
##   WEATHER    ##
##################
${voffset 5}${font Arial:bold:size=12}${color4}Weather ${color8}${hr 2}
${goto 100}${font Weather:size=49}${color1}y${voffset -8}${font RadioSpace:size=38}${color3} ${execpi 600 conkyForecast --location=GMXX0303}
${voffset -20}${font Radiospace:size=25}${color4}${alignc}${execi 600 conkyForecast --location=GMXX0303 --datatype=CT}
${voffset 0}${font Arial:bold:size=14}${color4}${goto 115}Chance of Rain: ${execi 600 conkyForecast --location=GMXX0303 --datatype=PC --startday=0}
${font Arial:bold:size=14}${color4}${goto 115}Feels like: ${execi 600 conkyForecast --location=GMXX0303 --datatype=LT}
${goto 20}${voffset -50}${font ConkyWeather:size=60}${color2}${execi 600 conkyForecast --location=GMXX0303 --datatype=WF}
${voffset -50}${goto 43}${font Arial:bold:size=12}${color2}${execi 600 conkyForecast --location=GMXX0303 --datatype=DW --startday=1 --endday=3 --shortweekday --spaces=18} 
${goto 30}${font}${color2}${font ConkyWeather:size=43}${execi 600 conkyForecast --location=GMXX0303 --datatype=WF --startday=1 --endday=3 --spaces=3}
${goto 45}${voffset -30}${font Arial:bold:size=12}${color2}${execi 3600 conkyForecast --location=GMXX0303 --datatype=PC --startday=1}${goto 145}${execi 3600 conkyForecast --location=GMXX0303 --datatype=PC --startday=2}${goto 245}${execi 3600 conkyForecast --location=GMXX0303 --datatype=PC --startday=3}
${goto 40}${voffset 5}${font Arial:bold:size=12}${color2}${execi 600 conkyForecast --location=GMXX0303 --datatype=HT --startday=1 --hideunits}/${execi 600 conkyForecast --location=GMXX0303 --datatype=LT --startday=1 --hideunits}${goto 140}${execi 600 conkyForecast --location=GMXX0303 --datatype=HT --startday=2 --hideunits}/${execi 600 conkyForecast --location=GMXX0303 --datatype=LT --startday=2 --hideunits}${goto 240}${execi 600 conkyForecast --location=GMXX0303 --datatype=HT --startday=3 --hideunits}/${execi 600 conkyForecast --location=GMXX0303 --datatype=LT --startday=3 --hideunits}
${voffset 5}${goto 15}${color4}${font Arial:bold:size=12}Wind:  ${goto 97}${color2}${execi 1200 conkyForecast --location=GMXX0303  --datatype=WS}   ${color4}${execi 1200 conkyForecast --location=GMXX0303  --datatype=WD}
${goto 15}${color4}${font Arial:bold:size=12}Humidity:  ${goto 97}${color2}${execi 1200 conkyForecast --location=GMXX0303  --datatype=HM}
${goto 15}${color4}${font Arial:bold:size=12}Bar:         ${goto 97}${color2}${execi 1200 conkyForecast --location=GMXX0303  --datatype=BR}  -  ${color4}${execi 1200 conkyForecast --location=GMXX0303  --datatype=BD}
${goto 15}${color4}${font Arial:bold:size=12}DayLight:  ${goto 97}${color2}${execi 1200 conkyForecast --location=GMXX0303  --datatype=DL}${goto 147}${color4}${font Arial:size=11}Rise${color2} ${execi 1200 conkyForecast --location=GMXX0303  --datatype=SR}  ${color4}Set ${color2} ${execi 1200 conkyForecast --location=GMXX0303  --datatype=SS}
${voffset 10}${goto 15}${font MoonPhases:size=41}${color6}${execi 600 conkyForecast --location=GMXX0303 --datatype=MF}${font Arial:bold:size=12}${goto 97}${voffset -25}${color4}${execi 1200 conkyForecast --location=GMXX0303  --datatype=MP}${endif}
```

---

### Post by amiacamal on 2011-08-05
So is it fair to say that the script you gave me should look considerably different to mine...?

---

### Post by zealibib slaughter on 2011-08-05
Yes it should look way different.  Should have weather and all.

---

### Post by amiacamal on 2011-08-05
ok then im defo loading the wrong config file somehow! It seems to just be loading the default!

copied your code into a new txt file and got this 
```
/home/Conky$ conky -c ~/Conky/conkymainNew
Conky: invalid configuration file '/home/simon/Conky/conkymainNew'

```

---

### Post by zealibib slaughter on 2011-08-05
where are you saving your conkymain? Did you create it to be hidden?

---

### Post by amiacamal on 2011-08-05
i dont believe its saved as hidden, its a text file in /home/Conky

---

### Post by zealibib slaughter on 2011-08-05
Try cd ing to that directory and see if it shows up with ls.  Also try to specify the full pathway (no ~) when you start conky.

---

### Post by amiacamal on 2011-08-05
shows up with regular ls 

it almost seems like conky reads the config as invalid and just loads the default one instead

---

### Post by zealibib slaughter on 2011-08-05
that may be whats going on.  I would try some simple conky configs from the post your conky files and see what I get.  
here is one thats very simple that you may want to try.  I don't know why the first one you was using would be invalid but I'm gonna look at it again.
```
[I][FONT=Courier New]background no
font Sans:size=6
#xftfont Sans:size=8
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 180
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 5
gap_y 32
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase
TEXT
${color white}
${alignc}$sysname kernel $kernel
${alignc}${exec cat /etc/issue.net} on $machine host $nodename
${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'}${freq_dyn}Mhz
Processes: ${alignr}$processes ($running_processes running)
Uptime: $alignr$uptime
CPU ${alignr}${cpu cpu1}%
${cpugraph 000000 ff0000}$color
${cpubar 4 cpu1}
Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}
Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}
Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}
${color white}Filesystem ${hr 1}${color}
Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}
[/FONT][/I]
```

---

### Post by amiacamal on 2011-08-05
does the line ```
conky -c /home/Conky/conkymainNew
``` seem right to start it?

---

### Post by zealibib slaughter on 2011-08-05
home/Yourname... but yeah that should be it

---

### Post by amiacamal on 2011-08-05
ok, so i ran it with the new file you gave me, it seems that i had named them as .txt files, and didnt put .txt in the start call. however now its started, but not showing on screen...

---

### Post by amiacamal on 2011-08-05
Succcess! sort of... the one you gave me (with weather and what not) HAS sort of worked. its now on the right side of the screen, but is sort of messed up...

terminal cries that it cant find the weather and email files

---

### Post by zealibib slaughter on 2011-08-05
Good, you need to download the weather scripts and email scripts
see this thread for the needed stuff: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)
 
Just keep playing with it and googling stuff to get it the way you want it. :)
 
Just remember to keep a good copy saved as backup somewhere.

---

### Post by amiacamal on 2011-08-05
This damn thing is gonna keep me busy for a whiiiile :) thanks for all your help!

---

### Post by zealibib slaughter on 2011-08-05
Yes it will make you loose massive sleep.  And you are welcome.  Happy coding.

---

