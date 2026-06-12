---
title: "conky"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by dzon65 on 2009-09-18
I'm having an epic battle with conky.I managed to get it working in it's default appearance.
I want to customize it but I don't have a clue how to do it.For now I've uninstalled it.Could someone explain step by step how to get it,for instance,to appear like this [http://images.google.be/imgres?imgurl=http://resa.linux-hardcore.com/wp-content/uploads/2009/07/KarmicKoala-PIII-04.png&imgrefurl=http://resa.linux-hardcore.com/%3Fp%3D276&usg=__W0HwCHH9QYfnH3ia1dvVlSJwTDA=&h=768&w=1024&sz=439&hl=nl&start=5&um=1&tbnid=bcLBgxyzwDFxwM:&tbnh=113&tbnw=150&prev=/images%3Fq%3Dkarmic%2Bkoala%2Bubuntu%26hl%3Dnl%26sa%3DN%26um%3D1](http://images.google.be/imgres?imgurl=http://resa.linux-hardcore.com/wp-content/uploads/2009/07/KarmicKoala-PIII-04.png&imgrefurl=http://resa.linux-hardcore.com/%3Fp%3D276&usg=__W0HwCHH9QYfnH3ia1dvVlSJwTDA=&h=768&w=1024&sz=439&hl=nl&start=5&um=1&tbnid=bcLBgxyzwDFxwM:&tbnh=113&tbnw=150&prev=/images%3Fq%3Dkarmic%2Bkoala%2Bubuntu%26hl%3Dnl%26sa%3DN%26um%3D1) 
I've got this tar.gz conky flavors downloaded,cause I think that's the one.

---

### Post by wobin77 on 2009-09-18
choose one you like [http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

look at the src file, and you ll get it.

Also for installing it, a quick google or search here in the forums and you ll find thousands of "howto's"

---

### Post by halitech on 2009-09-18
to install it
```
sudo apt-get install conky
```

```
touch .conkyrc
```
```
gedit .conkyrc
```
then copy and paste the code below into it and save. Then press ALT + F2 and run conky

```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 4

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color grey
#default_shade_color black
#default_outline_color grey
own_window_colour grey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 35

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
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
SYSTEM ${hr 2}
${alignc 17}${font Arial Black:size=16}Resa  ${font}
${alignc}  $sysname $nodename
${voffset 2}${font openlogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font Webdings:size=16}~${font}  Battery: ${battery_percent BAT0}% ${alignr}${battery_bar 8,60 BAT0}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 17}${font Arial Black:size=16}${time %H:%M}${font}
${alignc}${time %A %d %B %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_used /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Var:
${voffset 4}${fs_used /var}/${fs_size /var} ${alignr}${fs_bar 8,60 /var}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}

PROCESSES ${hr 2}
NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5}
${top name 6} $alignr ${top pid 6} ${top cpu 6}
${top name 7} $alignr ${top pid 7} ${top cpu 7}
${top name 8} $alignr ${top pid 8} ${top cpu 8}
```

---

### Post by dzon65 on 2009-09-18
Yep,that did the job,thanks.

---

### Post by VCoolio on 2009-09-18
If you run just 'conky' it will use the system configuration file or ~/.conkyrc. If you write your own, you can point to them with 'conky -c /path/to/your/config'. You can run several conkies with this, just 'conky -c /path/to/config1' and 'conky -c /path/to/config2' etc. Have fun. Check here for some inspiration:
[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)
[http://conky.linux-hardcore.com/](http://conky.linux-hardcore.com/)
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by dzon65 on 2009-09-18
thanks,I'll have a closer look.

---

### Post by dzon65 on 2009-09-19
To Halitech.How can I add a icon shortcut for this on the panel (switch)?How can I fix this to the panel cause for now,after reboot it'll be gone.Oh yes,how can I change the letters in front of the applications,normally there's an icon for let's say HD or CPU,for now there are only letters.

---

### Post by clive littlewood on 2009-09-19
Hi

You need to start conky when you boot.

System > prefs > startup apps

Add > name(conky) > command(conky) > add

This will now be added to your startup list and conky will be on your desktop at startup.

Hope this helps

Clive

---

### Post by ecmatter on 2009-09-19
If you can make sense of any of this, it'll save a lot of trial and error and back and forth between man pages and help files.  If I remember right, I pulled the variable section from someone's conky rc.  The rest comes from the conky documentation.  No guarantees that any of this is accurate (especially entries that include **(???)**).

```

#### OUTPUT #####
# append_file (???)
    # append the file given as argument 
out_to_console B
    # Boolean
    # print text to stdout (terminal)
out_to_stderr B
    # Boolean
    # print text to stderr (terminal?)
out_to_x B
    # Boolean
    # print output to X desktop
    # When set to no, there will be no output in X
    # If set to no, make sure that it's before any other X related
    # configuration settings in .conkyrc
# overwrite_file (???)
    # Overwrite the file given as argument. 

##### PROPERTIES #####
background B
    # Boolean
    # fork conky to background
# display (???)
    # specify an X display to connect to
double_buffer B
    # Boolean
    # Uses the X server's Xdbe extension to double buffer
    # eliminates flicker in conky output to X

##### WINDOW #####
alignment position
    # position = top_left or top_right or top_middle or bottom_left or
    # bottom_right or bottom_middle or middle_left or middle_right or none
    # window position
gap_x n
    # n pixels
    # gap between window and right or left edge of screen
gap_y n
    # n pixels
    # gap between window and top or bottom of screen
maximum_width x
    # x pixels
    # maximum width of window
minimum_size x y
    # x pixels y pixels
    # minimum size of window
own_window B
    # Boolean
    # create own window to draw
    # if B = no, outputs to the desktop which can slow conky down
own_window_class name
    # name = whatever (defaults to 'Conky')
    # manually set the WM_CLASS name
own_window_colour nnnnnn
    # nnnnnn = hex. color (no leading #)
    # If own_window_transparent no, set a specified background colour
own_window_hints undecorated,below,above,sticky,skip_taskbar,skip_pager
    # undecorated,below,above,sticky,skip_taskbar,skip_pager
    # If own_window is yes, you may use these window manager hints to
    # affect the way Conky displays.
    # Use own_window_type desktop as another way to implement many of
    # these hints implicitly. If you use own_window_type override,
    # window manager hints have no meaning and are ignored.
own_window_title name
    # name = whatever (defaults to '<hostname> - conky')
    # manually set the window name
own_window_transparent B
    # Boolean
    # set transparency
own_window_type type
    # type = normal or desktop or dock or override
    # desktop windows are special windows that have no window decorations
    # are always visible on your desktop; do not appear in your pager or
    # taskbar; and are sticky across all workspaces. Override windows are
    # not under the control of the window manager. Hints are ignored

##### FORMAT #####
border_margin n
    # n pixels
    # border margin
border_width n
    # n pixels
    # border width
default_bar_size x y
    # x pixels y pixels
    default bar size
default_color nnnnnn
    # nnnnnn = hex. color (no leading #)
    # default color and border color (text, glyphs, border)
default_guage_size x y
    # x pixels y pixels
    # default guage size
default_graph_size
    # x pixels y pixels
    default graph size
default_outline_color nnnnnn
    # nnnnnn = hex. color (no leading #)
    #default outline color
default_shade_color nnnnnn
    # nnnnnn = hex. color (no leading #)
    #default shade color
draw_borders B
    # Boolean
    # draw borders around text
draw_graph_borders B
    # Boolean
    # draw borders around graphs
draw_outline B
    # Boolean
    # draw outlines
draw_shades B
    # Boolean
    # draw shades
font name
    # name = font name in X
    # sets the default font
    # type xfontsel into terminal to view available fonts
override_utf8_locale B
    # Boolean
    # override unicode characters
pad_percents n
    # n = number of decimals (0 = no padding)
    # pad percentages to this many decimals
short_units B
    # Boolean
    # shortens units to a single character
show_graph_range B
    # Boolean
    # show the time range covered by a graph
show_graph_scale B
    # Boolean
    # show the maximum value in scaled graphs
stippled_borders n
    # n pixels
    # border stippling
temperature_unit unit
    # unit = fahrenheit or celsius
    # set units for all temperature outputs
top_cpu_separate B
    # Boolean
    # If true, cpu in top will show usage of one processor's power
    # If false, cpu in top will show the usage of all processors' power
    # combined
    # see man top for more information on top
top_name_width n
    # n = number of characters (defaults to '15')
    # width for $top name value
    # see man top for more information on top
uppercase B
    # Boolean
    # uppercase text rendering
use_spacer type
    # type = left or right or none
    # adds spaces around certain objects to keep them from moving other
    # things around.  only works with mono fonts
use_xft B
    # Boolean
    # anti-aliased fonts and objects
    # use FreeType's antialiased fonts with the X Window System
xftalpha n
    # 0 <= n => 1
    # alpha of xft font
    # close to 0 = bright, close to 1 = faint
xftfont font
    # font = name of font
    # font to use with xft (use any of the fonts in xfontsel)
    # libxft2 installed in Hardy

##### VARIABLES #####
# alias (???)
    # use this to create aliases of variables. The first argument is the
    # new name, the second the old name, and the other arguments are passed
    # on to the variable. Example: If you want to use $alpha instead of
    # ${beta gamma delta} then you have to write the following:
    # alias alpha beta gamma delta . PS: Instead of creating an alias in
    # the config you can also use environment variables. Example: Start
    # conky like this: alpha="beta gamma delta" conky 
colorN nnnnnn
    # nnnnnn = hex. color (no leading #); N = numbers from 0 to 9
    # Pre-define a color for use inside TEXT segments.
# templateN (???)
    # N = number from 0-9
    # Define a template for later use inside TEXT segments.
    # The value of the variable is being inserted into the stuff below TEXT
    # at the corresponding position, but before some substitutions are
    # applied:
        # '\n' -> newline
        # '\\' -> backslash
        # '\ ' -> space
        # '\N' -> template argument N
# variables (???)

#      Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
# ${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
# ${font Verdana:size=10}as many times as I choose
# ${font Perry:size=10}Including UTF-8,
# ${font Luxi Mono:size=10}justo como este texto que o google traduz fÃªz o portuguÃªs
# stuff after 'TEXT' will be formatted on screen
# ${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}

##### TECH #####
cpu_avg_samples n
    # number
    # the number of samples to average for CPU monitoring
diskio_avg_samples n
    # number
    # the number of samples to average for disk I/O monitoring
imlib_cache_size n
    # n bytes (defaults to 4MiB; set to zero to disable the image cache)
    # IMLIB2 image cache size -- increase this value if you use $image lots
max_user_text n
    # n bytes (defaults to 16384)
    # Maximum size of user text buffer, i.e. layout below TEXT line in
    # config file 
net_avg_samples n
    # number
    # the number of samples to average for net data
no_buffers B
    # Boolean
    # subtract file system buffers from used memory
text_buffer_size n
    # n bytes (defaults to 256)
    # size of the standard text buffer
total_run_times n
    # n = number of updates ('0' makes conky run forever)
    # total times for conky to update before quitting
update_interval n
    # n seconds
    # update interval

##### SCRIPTS #####
lua_load script1 script2 etc...
    # script1 script2 are scripts to be loaded (use full pathname)
    # loads one or more lua scripts
    # lua is the programming language used to extend conky

##### NETWORK #####
# if_up_strictness type (???)
    # type = up or link or address
    # if_up ensures that a TCP/IP interface is available
    # How strict should if_up be when testing an interface for being up?
    # check for the interface being solely up, being up and having link
    # or being up, having link and an assigned IP address
# imap --see comments-- (???)
    # Arguments are: "host user pass [-i interval (in seconds)] [-f folder]
    # [-p port] [-e command] [-r retries]"
    # Default global IMAP server.  email server (like pop)
    # Default port is 143, default folder is 'INBOX', default interval is
    # 5 minutes, and default number of retries before giving up is 5.
    # If the password is supplied as '*', you will be prompted to enter
    # the password when Conky starts
# mail_spool (???)
    # mail spool for mail checking
# max_port_monitor_connections n (???)
    # n = number of connections (if 0 or not set, defaults to 256)
    # allow each port monitor to track at most this many connections 
# pop3 --see comments-- (???)
    # Arguments are: "host user pass [-i interval (in seconds)] [-p port]
    # [-e command] [-r retries]"
    # Default global POP3 server.
    # Default port is 110, default interval is 5 minutes, and default number
    # of retries before giving up is 5. If the password is supplied as '*',
    # you will be prompted to enter the password when Conky starts.

##### MUSIC #####
# mpd_host host (???)
    # host = hostname
    # Music Player Daemon (MPD) is a flexible, powerful, server-side
    # application for playing music.
# mpd_password pass (???)
    # pass = password
    # Music Player Daemon (MPD) is a flexible, powerful, server-side
    # application for playing music.
# mpd_port n (???)
    # n = port number
    # Music Player Daemon (MPD) is a flexible, powerful, server-side
    # application for playing music.
# music_player_interval n
    # n seconds (defaults to conky's update interval)
    # music player (mpd, audacious, etc...) thread update interval

```

---

### Post by dzon65 on 2009-09-19
Clive,it's in the startup menu allright.I've put a starter on the panel but that starter doen't have the ability to switchon/switch off.When I boot conky will not be displayed unless I click the icon.But clicking the icon once more won't turn it off,it'll stay there.

---

### Post by halitech on 2009-09-19
you would need to write a script to kill it. Basically I just open a terminal and run killall conky when I want to turn mine off. I'm sure there is probably a way of making it work as a launcher but I'm not sure myself how to do it.

---

### Post by VCoolio on 2009-09-19
Save this script somewhere and make a launcher with as command "sh /path/to/script" to toggle conky on / off (I found this somewhere on these forums, I take no credit):

```
#!/bin/sh
# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 conky
fi
```

---

### Post by dzon65 on 2009-09-20
VCoolio,goeiemorgen.I tried that but couldn't get it to work though.

---

### Post by halitech on 2009-09-20
did you make it executable?

---

### Post by VCoolio on 2009-09-20
> **dzon65 said:**
> VCoolio,goeiemorgen.I tried that but couldn't get it to work though.
What is the output if you run 'sh /path/to/script' in a terminal?

---

### Post by dzon65 on 2009-09-20
can't open path.Yet,it's executable.This is the file:#!/bin/sh
# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
 conky
fi

---

### Post by dzon65 on 2009-09-21
VCoolio.It's ok,working.Stupid mistake,mistyped something.Thanks and sorry for the inconvenience.

---

### Post by ben2talk on 2010-11-25
> **dzon65 said:**
> VCoolio,goeiemorgen.I tried that but couldn't get it to work though.

Just use gedit to make a text file on your desktop, then right click the text file and in properties there's 'executable'.

You can do anything with scripts. I made a launcher (right click desktop, 'create launcher')

type: application
name: conky
command: /home/ben/Admin/Scripts/restart.conky

Drag this launcher up to your panel, and then right click it and find a nice icon somewhere (you can easily download one and put it in your ~/.icons, or go searching in /usr/share/pixmaps or /usr/share/icons).

Then I made a text file (and made it executable, and put it in the folder ~/Admin/Scripts/restart.conky)

```
#!/bin/bash
#
# Script to restart conky

killall conky
sleep 0.25
conky -d -c /home/ben/Admin/CONKY/short.conky
```

You could add a line to start another conky (maybe have weather or something else in a separate conky) and the script will restart both.

Next I made a launcher (with a queue of scripts I want to open for editing at a click):
Name:     conky edit
command: gedit /home/ben/Admin/Scripts/.conky/ /home/ben/Admin/CONKY/short.conky /home/ben/Admin/Scripts/restartben.conky

If I click this, it will open all relevant scripts for editing (handy - and place the launcher on the desktop so it will be hidden when conky is running. You can do Alt F2 'killall conky' to uncover it'.

I find it handy to have a 'startup.sh' script in my scripts folder - rather than add tons of entries to my startup list, I just added '/home/ben/Admin/startup.sh' to the list of startup-applications in the preferences menu.

For any new startup now, I can add a script, or just add it to the list... currently it looks like this:

"startup.sh"
```
#!/bin/bash
nvidia-settings -a [gpu:0]/OverscanCompensation[TV-0]=70
sleep 1;
/home/ben/Admin/Scripts/trayer.sh
sleep 1;
/home/ben/Admin/Scripts/restartben.conky &
exec gksu /etc/init.d/privoxy start &
/home/ben/Admin/Scripts/terminal.sh
```

Ok, getting away from the point - don't be shy to use scripts and launchers to make life easy. For me, the terminal is nice, but most times just a click of a panel icon, or desktop icon will run or open for editing any combination of these. I can restart my conky, trayer and gnome-do at once, and even have a desktop icon to restart gnome-panel (when alt-f2 won't appear... handy).

---

### Post by Chazz44able on 2010-12-03
how do you run more than one Conky at a time??

---

