---
title: "What do you use to constantly monitor your bandwidth &amp; Net speed/traffic?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Andy06 on 2009-07-07
I currently use the Netmonitor screenlet but I am not completely happy with it, its too basic, not entirely accurate and not very customisable. I also tried the netspeed panel applet and that is even more inaccurate.

On windows I use SFkilla's awesome Multimeter and Network Monitor gadgets [[http://thehobbylounge.com/forum/index.php?topic=5267.0](http://thehobbylounge.com/forum/index.php?topic=5267.0) and [http://thehobbylounge.com/forum/index.php?topic=5276.0]](http://thehobbylounge.com/forum/index.php?topic=5276.0]). Anything similar I can use in Ubuntu? I need it to be visible above my browser so things like conky aren't very useful. Perhaps a custom third party gadget/screenlet that I can use?

Thanks a lot

---

### Post by lukeiamyourfather on 2009-07-07
If you're using GNOME there's one built into the bar at the top or bottom of the screen. Enable the resource monitor and then disable everything except for the network traffic. I'm sure there are others out there too that are similar. Cheers!

---

### Post by starcraft.man on 2009-07-07
How about just the small firestarter window, you put it on status tab and then just make it as small as possible and to the far end of a screen. Ya can then just set it to always be on workspace/top. It displays the activity, up and down totals for your NICs.

Firestarter is a gui for the firewall configuration btw, it's in the repos. I don't monitor much anymore since I got an unlimited plan. TekSavvy if your in Canada, look em up, nice company and excellent rate at 40 CAD for unlimited 512/80 DSL line. Can't help but promote my guys, gotta get people off dreadful Bell/Rogers duopoly.

/endrant

---

### Post by lukeiamyourfather on 2009-07-07
I just came across a few. Conky, GKrellM, and Torsmo. A few years ago I used CoolMon on Windows and those look similar. Cheers!

---

### Post by Andy06 on 2009-07-08
The default GNOME panel one has only graphic representations right? Thats not enough for me.

Conky looks too hard to set up but will definitely sit down with it this weekend and figure it out. Gkrellm is too ugly hehe and I don't know anything about torsmo. Can you tell me more about it?

Typing torsmo into synaptic brings up conky. Even if I configure conky, I won't be able to keep it above the broswer window without it blocking things. 

Any good screenlet anyone knows about? Or adesklet or gdesklet or any similar gadget?

Thanks a lot

---

### Post by superprash2003 on 2009-07-08
i too use the firestarter window to monitor my usage!!

---

### Post by Andy06 on 2009-07-08
I already have Gufw installed, can I install Firestarter without any conflicts? I am reluctant to only use Firestarted as too many people have complained about it being very buggy.

Thanks

---

### Post by sharif_aly on 2009-07-14
Is Multimeter is on Ubuntu ?

---

### Post by binbash on 2009-07-15
I use conky, it is better since it is very easy to write your own script

---

### Post by Andy06 on 2009-07-15
> Is Multimeter is on Ubuntu ? 

No unfortunately it is not. And its no use trying to run it under wine since 
a) Its a sidebar app that needs the sidebar and not a standalone program
b) It pulls values from the system, so without windows, it has nothing to read.

Due to those factors, it would also be very very hard to make a Linux version for the developer, it won't be a port or an adaptation but a completely new app.

IMO, conky is worthless to noobs or power users who are relative noobs to linux and without any coding/programming background. Any normal person migrating will look at the instructions and threads of conky and have a heart attack :D

Tweaking every part of the maze that is Compiz config settings and Cairo dock settings now looks like child's play in comparison.;)

I'm still hoping that either Multimeter will eventually come to Linux (0 chance), Screenlets/gdesklets/adesklets/universal applets will amount to something (0 chance since screenlets has been discontinued and is a dormant project) or GNOME 3 introduces a new gadgets/widgets framework (I don't think its going to happen).

What about Plasma and Superkaramba, do they have good gadgets? How to run them on Ubuntu? Just install with KDE libs?

---

### Post by Student Driver on 2009-07-16
Just a question, but did you try just using a config already made with Conky?  That's what I did, and I get most of that info (and more) using it.  I don't have the totals though, but I imagine that's doable and may already be in a conky file already posted.

I couldn't use a separate screenlet/applet because I'm running this on a Dell Mini 9, so I need all the screen space I can get.  :).  I will go to it and post what I'm using.  It has both my WLAN and Bluetooth interfaces, and they can be tweaked or removed as needed.

---

### Post by Student Driver on 2009-07-16
Here's my .conkyrc file.  It shows a fairly small display, but takes up most of my fairly small display so it works out.  I also use a delay to start it after Nautilus launches, and I use that file to kick off Conky.  I can post that if needed.

```
# conky configuration
# originally edited by darcon@gmail.com, tweaked for Dell Mini 9 by Student Driver


# Create own window instead of using desktop (required in nautilus)
#own_window yes
#own_window_type desktop
own_window_type override
own_window_transparent yes

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

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=7

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 1000 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 4

# border margins
border_margin 2

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 450
gap_y 1

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes
#Note: doesn't work in conky 1.2 =(

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none


# Possible variables to be used:
#
#      Variable         Arguments                  Description                

# 	addr              (interface)   IP address for an interface
# 	acpiacadapter                   ACPI ac adapter state.                   
# 	acpifan                         ACPI fan state                           
# 	acpitemp                        ACPI temperature.                        
# 	adt746xcpu                      CPU temperature from therm_adt746x       
# 	adt746xfan                      Fan speed from therm_adt746x             
# 	alignr            (num)         Right-justify text, with space of N
# 	alignc                          Align text to centre
# 	battery           (num)         Remaining capasity in ACPI or APM        
# 					battery. ACPI battery number can be      
# 					given as argument (default is BAT0).     
# 	buffers                         Amount of memory buffered                
# 	cached                          Amount of memory cached                  
# 	color             (color)       Change drawing color to color            
# 	cpu                             CPU usage in percents                    
# 	cpubar            (height)      Bar that shows CPU usage, height is      
# 					bar's height in pixels                 
# 	cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
# 					CPU usage graph, with optional colours in hex,
# 					minus the #.
# 	downspeed         net           Download speed in kilobytes              
# 	downspeedf        net           Download speed in kilobytes with one     
# 					decimal                                  
# 	downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
# 					Download speed graph, colours defined in
# 					hex, minus the #.
# 	exec              shell command Executes a shell command and displays    
# 					the output in conky. warning: this      
# 					takes a lot more resources than other    
# 					variables. I'd recommend coding wanted   
# 					behaviour in C and posting a patch :-).  
# 	execbar           shell command Same as exec, except if the first value
# 					return is a value between 0-100, it
# 					will use that number for a bar.
# 					The size for the bar is currently fixed,
# 					but that may change in the future.
# 	execgraph         shell command Same as execbar, but graphs values
# 	execi             interval, shell command
#  					Same as exec but with specific interval. 
# 					Interval can't be less than              
# 					update_interval in configuration.        
#	font		  font		Specify a different font.  Only applies
#					to one line.
# 	fs_bar            (height), (fs)Bar that shows how much space is used on 
# 					a file system. height is the height in   
# 					pixels. fs is any file on that file      
# 					system.                                  
# 	fs_free           (fs)          Free space on a file system available    
# 					for users.                               
# 	fs_free_perc      (fs)          Free percentage of space on a file       
# 					system available for users.              
# 	fs_size           (fs)          File system size                         
# 	fs_used           (fs)          File system used space                   
# 	hr                (height)      Horizontal line, height is the height in 
# 					pixels                                   
# 	i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
# 					may be omitted if you have only one I2C  
# 					device. type is either in (or vol)       
# 					meaning voltage, fan meaning fan or
# 					temp/tempf (first in C, second in F)
# 					meaning temperature. n is number of the  
# 					sensor. See /sys/bus/i2c/devices/ on     
# 					your local computer.                     
# 	if_running        (process)     if PROCESS is running, display
# 					everything if_running and the matching $endif
# 	if_existing       (file)        if FILE exists, display everything between
# 					if_existing and the matching $endif
# 	if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
# 					if_mounted and the matching $endif
# 	else                            Text to show if any of the above are not true
# 	kernel                          Kernel version                          
# 	linkstatus        (interface)   Get the link status for wireless connections
# 	loadavg           (1), (2), (3) System load average, 1 is for past 1     
# 					minute, 2 for past 5 minutes and 3 for   
# 					past 15 minutes.                         
# 	machine                         Machine, i686 for example                
# 	mails                           Mail count in mail spool. You can use    
# 					program like fetchmail to get mails from 
# 					some server using your favourite         
# 					protocol. See also new_mails.            
# 	mem                             Amount of memory in use                  
# 	membar            (height)      Bar that shows amount of memory in use   
# 	memmax                          Total amount of memory                   
# 	memperc                         Percentage of memory in use
# 	
# 	metar_ob_time
# 	metar_temp
# 	metar_tempf                     Temp in F
# 	metar_windchill
# 	metar_dew_point                 There are a bunch of these
# 	metar_rh                        and they are self-explanatory
# 	metar_windspeed
# 	metar_winddir
# 	metar_swinddir
# 	metar_cloud
# 	metar_u2d_time
# 	
# 	ml_upload_counter               total session upload in mb
# 	ml_download_counter             total session download in mb
# 	ml_nshared_files                number of shared files
# 	ml_shared_counter               total session shared in mb, buggy
# 					in some mldonkey versions
# 	ml_tcp_upload_rate              tcp upload rate in kb/s
# 	ml_tcp_download_rate            tcp download rate in kb/s
# 	ml_udp_upload_rate              udp upload rate in kb/s
# 	ml_udp_download_rate            udp download rate in kb/s
# 	ml_ndownloaded_files            number of completed files
# 	ml_ndownloading_files           number of downloading files
# 	
# 	mpd_artist			Artist in current MPD song
# 					(must be enabled at compile)
# 	mpd_album			Album in current MPD song
# 	mpd_bar           (height)      Bar of mpd's progress
# 	mpd_bitrate                     Bitrate of current song
# 	mpd_status                      Playing, stopped, et cetera.
# 	mpd_title			Title of current MPD song
# 	mpd_vol				MPD's volume
# 	mpd_elapsed                     Song's elapsed time
# 	mpd_length                      Song's length
# 	mpd_percent                     Percent of song's progress
# 	new_mails                       Unread mail count in mail spool.         
# 	nodename                        Hostname                                 
# 	outlinecolor      (color)       Change outline color                     
# 	pre_exec          shell command Executes a shell command one time before 
# 					conky displays anything and puts output 
# 					as text.                                 
# 	processes                       Total processes (sleeping and running)   
# 	running_processes               Running processes (not sleeping),        
# 					requires Linux 2.6                       
# 	shadecolor        (color)       Change shading color                     
# 	stippled_hr       (space),      Stippled (dashed) horizontal line        
# 			(height)        
# 	swapbar           (height)      Bar that shows amount of swap in use     
# 	swap                            Amount of swap in use                    
# 	swapmax                         Total amount of swap                     
# 	swapperc                        Percentage of swap in use                
# 	sysname                         System name, Linux for example           
# 	offset            pixels        Move text over by N pixels
# 	tail              logfile, lines (interval)
# 					Displays last N lines of supplied text
# 					text file.  If interval is not supplied,
# 					Conky assumes 2x Conky's interval.
# 					Max of 30 lines.
# 					Max of 30 lines can be displayed.
# 	time              (format)      Local time, see man strftime to get more 
# 					information about format                 
# 	totaldown         net           Total download, overflows at 4 GB on     
# 					Linux with 32-bit arch and there doesn't 
# 					seem to be a way to know how many times  
# 					it has already done that before conky   
# 					has started.                            
# 	top               type, num     This takes arguments in the form:
# 					top <name> <number>
# 					Basically, processes are ranked from 
# 					highest to lowest in terms of cpu
# 					usage, which is what <num> represents.
# 					The types are: "name", "pid", "cpu", and
# 					"mem".
# 					There can be a max of 10 processes listed.
# 	top_mem           type, num     Same as top, except sorted by mem usage
# 					instead of cpu
# 	totalup           net           Total upload, this one too, may overflow 
# 	updates                         Number of updates (for debugging)        
# 	upspeed           net           Upload speed in kilobytes                
# 	upspeedf          net           Upload speed in kilobytes with one       
# 					decimal                                  
# 	upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
# 					Upload speed graph, colours defined in
# 					hex, minus the #.
# 	uptime                          Uptime                                   
# 	uptime_short                    Uptime in a shorter format               
# 	
# 	seti_prog                       Seti@home current progress
# 	seti_progbar      (height)      Seti@home current progress bar
# 	seti_credit                     Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

#The following list time of day, but that's redundant for my system
#${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
#${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}

#Other Logging Info normally at the bottom
#${color slate grey}/var/log/messages:
#${color}${exec tail -n4 /var/log/messages}
# stuff after 'TEXT' will be formatted on screen

TEXT



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

${offset 240}${color slate grey}ROOT:   ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}VAR:   ${color }${fs_free /var}/${fs_size /var}
${offset 240}${fs_bar 3,100 /var}
${offset 240}${color slate grey}WLAN:                                        ${color slate grey}Bluetooth:           
${offset 240}${color}Up: ${color }${upspeed eth1} k/s                                 ${color}Up: ${color }${upspeed bnep0} k/s
${offset 240}${upspeedgraph eth1 20,130 000000 ffffff}       ${upspeedgraph bnep0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth1}k/s${color}                             ${color}Down: ${color }${downspeed bnep0}k/s${color}
${offset 240}${downspeedgraph eth1 20,130 000000 ffffff}       ${downspeedgraph bnep0 20,130 000000 ffffff}


```

---

### Post by SolarOnline on 2009-08-12
[ipMonitor]("http://tinyurl.com/qjdxu5") is a good solution for up/down monitoring for network devices, servers, and applications, that sports a free trial.

Have any of you tried it?

---

