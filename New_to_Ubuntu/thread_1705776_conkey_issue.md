---
title: "conkey issue"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by ECET on 2011-03-12
I copied the below code from another thread on this forum....however, I can not figure out why my conky shows up on the left side of desktop vs the right side like the original poster's pic.....I do not have the bar graphs either....can someone please give me a hand?....
```

##################################
## VinDSL | rev. 11-01-01 02:33 ##
##################################

####
## Use XFT? Required to Force UTF8 (see below).
#
use_xft yes
xftfont LiberationSans:size=8.85
xftalpha 0.7
text_buffer_size 2048

####
## Force UTF8? Requires XFT (see above).
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

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
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

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
#totally 
out_to_ncurses no
out_to_console no

####
## Text alignment.
#
alignment tr

####
## Minimum size of text area.
#
minimum_size 235 0

####
## Gap between text and screen borders.
#
gap_x 7
gap_y 26

####
## Shorten MiB/GiB to M/G in stats.
#
short_units yes

####
## Pad % symbol spacing after numbers.
#
pad_percents 0

####
## Pad spacing between text and borders.
#
border_inner_margin 4

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
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right

####
## My colors (suit yourself).
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

####
## Load Lua for shading (optional).
## Set the path to your script here.

#lua_load /home/linus/scripts/.draw_bg1.lua
#lua_load /home/linus/scripts/.bargraph_small2.lua
#lua_draw_hook_pre draw_bg
#lua_draw_hook_post main_bars

####
## Installed fonts (required).
#
# ConkyWeather (Stanko Metodiev)
# ConkyWindNESW (Stanko Metodiev)
# Cut Outs for 3D FX (Fonts & Things)
# Liberation Mono (Ascender Corp)
# Liberation Sans (Ascender Corp)
# Moon Phases (Curtis Clark)
# OpenLogos (Icoma)
# PizzaDude Bullets (Jakob Fischer)
# Radio Space (Iconian Fonts)
# StyleBats (Vinterstille)
# Ubuntu (Canonical Ltd)
# Ubuntu Title Bold (Paulo Silva)
# Weather (Jonathan Macagba)
# WenQuanYi Micro Hei (Google Corp)
 
TEXT
##################
##   WEATHER    ##
##################
${voffset 6}${font WenQuanYiMicroHei:bold:size=8.75}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 0}${goto 59}${font Weather:size=38}${color2}y${font}${voffset -33}${offset 14}${font RadioSpace:size=32}${color3}${execpi 1800 conkyForecast --imperial --location=}${font}
${voffset 0}${font Ubuntu:size=24}${color4}${alignc}${execi 1800 conkyForecast --location= --datatype=CT}${font}
${voffset 15}${goto 20}${font ConkyWindNESW:style=Bold:size=38}${color2}${execi 1800 conkyForecast --location= --datatype=BS}${font}${voffset -40}${goto 95}${font ConkyWeather:style=Bold:size=45}${execi 1800 conkyForecast --location= --datatype=WF}${font}${voffset -36}${goto 185}${font MoonPhases:size=30}${execi 1800 conkyForecast --location= --datatype=MF}${font}
${voffset 6}${goto 28}${font}${color6}${execpi 1800 conkyForecast --location= --imperial --datatype=WS | sed -e 's/calm'/'\$\{offset 2}Calm/g' -e 's/mph'/'\$\{offset 2}mph/g'}${goto 89}Feels like ${execi 1800 conkyForecast --location= --imperial --datatype=LT --centeredwidth=4 -iu}${execpi 1800 conkyForecast --location= --datatype=MP | sed -e 's/First.*'/'\$\{goto 185}First Qtr/g' -e 's/Last.*'/'\$\{goto 185}Last Qtr/g' -e 's/New.*'/'\$\{goto 190}New/g' -e 's/Full.*'/'\$\{goto 194}Full/g' -e 's/Waning.*'/'\$\{goto 185}Waning/g' -e 's/Waxing.*'/'\$\{goto 185}Waxing/g'}
${voffset 10}${goto 35}${font}${color6}${execi 1800 conkyForecast --location= --datatype=DW --startday=1 --shortweekday}${goto 89}${execi 1800 conkyForecast --location= --datatype=DW --startday=2 --shortweekday}${goto 142}${execi 1800 conkyForecast --location= --datatype=DW --startday=3 --shortweekday}${goto 196}${execi 1800 conkyForecast --location= --datatype=DW --startday=4 --shortweekday}
${voffset 0}${goto 25}${font ConkyWeather:size=32}${color2}${execi 1800 conkyForecast --location= --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${goto 25}${font}${color6}${execi 1800 conkyForecast --location= --imperial --datatype=HT --startday=1 --hideunits --centeredwidth=4 -iu}/${offset 4}${execi 1800 conkyForecast --location= --imperial --datatype=LT --startday=1 --hideunits --centeredwidth=4 -iu}${goto 79}${execi 1800 conkyForecast --location= --imperial --datatype=HT --startday=2 --hideunits --centeredwidth=4 -iu}/${offset 4}${execi 1800 conkyForecast --location= --imperial --datatype=LT --startday=2 --hideunits --centeredwidth=4 -iu}${goto 133}${execi 1800 conkyForecast --location= --imperial --datatype=HT --startday=3 --hideunits --centeredwidth=4 -iu}/${offset 4}${execi 1800 conkyForecast --location= --imperial --datatype=LT --startday=3 --hideunits --centeredwidth=4 -iu}${goto 187}${execi 1800 conkyForecast --location= --imperial --datatype=HT --startday=4 --hideunits --centeredwidth=4 -iu}/${offset 4}${execi 1800 conkyForecast --location= --imperial --datatype=LT --startday=4 --hideunits --centeredwidth=4 -iu}##################################
## VinDSL | rev. 11-01-01 02:33 ##
##################################

# config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %l:%M%p
DATE_FORMAT = %Y-%m-%d
LOCALE = en
XOAP_PARTNER_ID = 
XOAP_LICENCE_KEY = 
MAXIMUM_DAYS_FORECAST = 4
AUTO_NIGHT = False
BASE_XOAP_URL = http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=5&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
#BASE_XOAP_URL = http://xml.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
PROXY_HOST = 
PROXY_PORT = 8080
PROXY_USERNAME = 
PROXY_PASSWORD =
#!/usr/bin/env python2

import os
 
#Enter your username and password below within double quotes
# eg. username="robinhoodmp@gmail.com" and password="reformers"
domain="mail.google.com"
username="robinhoodmp"
password="reformers"
com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=msg.find("<fullcount>")
index2=msg.find("</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print "0 new"
else:
   print str(fc)+" new"
   --[[ BARGRAPH WIDGET
    v2.0 by wlourf (12.07.2010)
    this widget draws a bargraph with differe,ts effects 
    [http://u-scripts.blogspot.com/2010/07/bargraph-widget.html](http://u-scripts.blogspot.com/2010/07/bargraph-widget.html)
    
    
Parameters are :
3 parameters are mandatory
name    - the name of the conky variable to display, for example for {$cpu cpu0}, just write name="cpu"
arg        - the argument of the above variable, for example for {$cpu cpu0}, just write arg="cpu0"
          arg can be a numericla value if name=""
max        - the maximum value the above variable can reach, for example for {$cpu cpu0}, just write  max=100
    
Optional parameters:
x,y        - coordinates of the starting point of the bar, default = middle of the conky window
cap        - end of cap line, ossibles values are r,b,s (for round, butt, square), default="b"
          [http://www.cairographics.org/samples/set_line_cap/](http://www.cairographics.org/samples/set_line_cap/)
angle    - angle of rotation of the bar in degress, default = 0 (i.e. a vertical bar)
          set to 90 for an horizontal bar
skew_x    - skew bar around x axis, défaut = 0
skew_y    - skew bar around y axis, défaut = 0
blocks  - number of blocks to display for a bar (values >0) , default= 10
height    - height of a block, default=10 pixels
width    - width of a block, default=20 pixels
space    - space between 2 blocks, default=2 pixels
angle_bar    - this angle is used to draw a bar on a circular way (ok, this is no more a bar !) default=0
radius        - for cicular bars, internal radius, default=0
              with radius, parameter width has no more effect.

Colours below are defined into braces {colour in hexadecimal, alpha}
fg_colour    - colour of a block ON, default= {0x00FF00,1}
bg_colour    - colour of a block OFF, défaut = {0x00FF00,0.5}
alarm        - threshold, values after this threshold will use alarm_colour colour , default=max
alarm_colour - colour of a block greater than alarm, default=fg_colour
smooth        - (true or false), create a gradient from fg_colour to bg_colour, default=false 
mid_colour    - colours to add to gradient, with this syntax {position into the gradient (0 to1), colour hexa, alpha}
              for example, this table {{0.25,0xff0000,1},{0.5,0x00ff00,1},{0.75,0x0000ff,1}} will add
              3 colurs to gradient created by fg_colour and alarm_colour, default=no mid_colour
led_effect    - add LED effects to each block, default=no led_effect
              if smooth=true, led_effect is not used
              possibles values : "r","a","e" for radial, parallelel, perdendicular to the bar (just try!)
              led_effect has to be used with theses colours :
fg_led        - middle colour of a block ON, default = fg_colour
bg_led        - middle colour of a block OFF, default = bg_colour
alarm_led    - middle colour of a block > ALARM,  default = alarm_colour

reflection parameters, not avaimable for circular bars
reflection_alpha    - add a reflection effect (values from 0 to 1) default = 0 = no reflection
                      other values = starting opacity
reflection_scale    - scale of the reflection (default = 1 = height of text)
reflection_length   - length of reflection, define where the opacity will be set to zero
                      calues from 0 to 1, default =1
reflection            - position of reflection, relative to a vertical bar, default="b"
                      possibles values are : "b","t","l","r" for bottom, top, left, right


v1.0 (10 Feb. 2010) original release
v1.1 (13 Feb. 2010) numeric values can be passed instead conky stats with parameters name="", arg = numeric_value    
v1.2 (28 Feb. 2010) just renamed the widget to bargraph
v1.3 (03 March 2010) added parameters radius & angle_bar to draw the bar in a circular way
v2.0 (12 Jul. 2010) rewrite script + add reflection effects and parameters are now set into tables
]]

require 'cairo'

----------------START OF PARAMETERS ----------


function conky_main_bars()
    bars_settings={    
        {
            name="cpu",
            arg="cpu0",
            max=100,
            alarm=50,
            bg_colour={0xFFFFFF,0.25},
            fg_colour={0x00FF00,0.6},
            alarm_colour={0xFF0000,0.6},
            x=99,y=176,
            blocks=52,
            space=1,
            height=2,width=7,
            angle=90,
            smooth=true,
            mid_colour={{0.5,0xFFFF00,0.6}}    
            },
        {
            
                name="memperc",
            arg="",
            max=100,
            alarm=50,
            bg_colour={0xFFFFFF,0.25},
            fg_colour={0x00FF00,0.6},
            alarm_colour={0xFF0000,0.6},
            x=23,y=224,
            blocks=77,
            space=1,
            height=2,width=7,
            angle=90,
            smooth=true,
            mid_colour={{0.5,0xFFFF00,0.6}}    
            },
        {
            
                        name="fs_used_perc",
            arg="/boot",
            max=100,
            alarm=50,
            bg_colour={0xFFFFFF,0.25},
            fg_colour={0x00FF00,0.6},
            alarm_colour={0xFF0000,0.6},
            x=23,y=268,
            blocks=77,
            space=1,
            height=2,width=7,
            angle=90,
            smooth=true,
            mid_colour={{0.5,0xFFFF00,0.6}}    
            },    
        {
            name="fs_used_perc",
            arg="/root",
            max=100,
            alarm=50,
            bg_colour={0xFFFFFF,0.25},
            fg_colour={0x00FF00,0.6},
            alarm_colour={0xFF0000,0.6},
            x=23,y=296,
            blocks=77,
            space=1,
            height=2,width=7,
            angle=90,
            smooth=true,
            mid_colour={{0.5,0xFFFF00,0.6}}    
            },    
        {
            name="fs_used_perc",
            arg="/home",
            max=100,
            alarm=50,
            bg_colour={0xFFFFFF,0.25},
            fg_colour={0x00FF00,0.6},
            alarm_colour={0xFF0000,0.6},
            x=23,y=325,
            blocks=77,
            space=1,
            height=2,width=7,
            angle=90,
            smooth=true,
            mid_colour={{0.5,0xFFFF00,0.6}}    
            },    
            {
                        name="swapperc",
            arg="",
            max=100,
            alarm=50,
            bg_colour={0xFFFFFF,0.25},
            fg_colour={0x00FF00,0.6},
            alarm_colour={0xFF0000,0.6},
            x=23,y=352,
            blocks=77,
            space=1,
            height=2,width=7,
            angle=90,
            smooth=true,
            mid_colour={{0.5,0xFFFF00,0.6}}
                        },    
    
    }
-------------END OF PARAMETERS--------------


    
    if conky_window == nil then return end
    
    local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
    
    cr = cairo_create(cs)    
    --prevent segmentation error when reading cpu state
    if tonumber(conky_parse('${updates}'))>3 then
local network=tonumber(conky_parse('${if_existing /sys/class/net/wlan0/operstate up}1${else}0${endif}'))
if network==1 then 
network=1 
else
network=tonumber(conky_parse('${if_existing /sys/class/net/wlan1/operstate up}2${else}0${endif}'))
if network==2 then
network=2
else
network=0
end
end

if network==1 then
table.insert(bars_settings,{
                        name="wireless_link_qual_perc",
            arg="wlan0",
            max=100,
            alarm=40,
            bg_colour={0xFFFFFF,0.25},
            fg_colour={0xFF0000,0.6},
            alarm_colour={0x00FF00,0.6},
            x=94,y=472,
            blocks=42,
            space=1,
            height=2,width=8,
            angle=90,
            smooth=true,
            mid_colour={{0.5,0xFFFF00,0.6}}
            })
elseif network==2 then
table.insert(bars_settings,{
                        name="wireless_link_qual_perc",
            arg="wlan1",
            max=100,
            alarm=40,
            bg_colour={0xFFFFFF,0.25},
            fg_colour={0xFF0000,0.6},
            alarm_colour={0x00FF00,0.6},
            x=94,y=472,
            blocks=42,
            space=1,
            height=2,width=8,
            angle=90,
            smooth=true,
            mid_colour={{0.5,0xFFFF00,0.6}}
            })
else
end

        for i in pairs(bars_settings) do
            
            draw_multi_bar_graph(bars_settings[i])
            
        end
    end
    cairo_destroy(cr)
    cairo_surface_destroy(cs)

end



function draw_multi_bar_graph(t)
    cairo_save(cr)
    --check values
    if t.name==nil and t.arg==nil then 
        print ("No input values ... use parameters 'name' with 'arg' or only parameter 'arg' ") 
        return
    end
    if t.max==nil then
        print ("No maximum value defined, use 'max'")
        return
    end
    if t.name==nil then t.name="" end
    if t.arg==nil then t.arg="" end

    --set default values    
    if t.x == nil        then t.x = conky_window.width/2 end
    if t.y == nil        then t.y = conky_window.height/2 end
    if t.blocks == nil    then t.blocks=10 end
    if t.height == nil    then t.height=10 end
    if t.angle == nil     then t.angle=0 end
    t.angle = t.angle*math.pi/180
    --line cap style
    if t.cap==nil        then t.cap = "b" end
    local cap="b"
    for i,v in ipairs({"s","r","b"}) do 
        if v==t.cap then cap=v end
    end
    delta=0
    if t.cap=="r" or t.cap=="s" then delta = t.height end
    if cap=="s" then     cap = CAIRO_LINE_CAP_SQUARE
    elseif cap=="r" then
        cap = CAIRO_LINE_CAP_ROUND
    elseif cap=="b" then
        cap = CAIRO_LINE_CAP_BUTT
    end
    --end line cap style
    --if t.led_effect == nil    then t.led_effect="r" end
    if t.width == nil    then t.width=20 end
    if t.space == nil    then t.space=2 end
    if t.radius == nil    then t.radius=0 end
    if t.angle_bar == nil    then t.angle_bar=0 end
    t.angle_bar = t.angle_bar*math.pi/360 --halt angle
    
    --colours
    if t.bg_colour == nil     then t.bg_colour = {0x00FF00,0.5} end
    if #t.bg_colour~=2         then t.bg_colour = {0x00FF00,0.5} end
    if t.fg_colour == nil     then t.fg_colour = {0x00FF00,1} end
    if #t.fg_colour~=2         then t.fg_colour = {0x00FF00,1} end
    if t.alarm_colour == nil     then t.alarm_colour = t.fg_colour end
    if #t.alarm_colour~=2         then t.alarm_colour = t.fg_colour end

    if t.mid_colour ~= nil then    
        for i=1, #t.mid_colour do    
            if #t.mid_colour[i]~=3 then 
                print ("error in mid_color table")
                t.mid_colour[i]={1,0xFFFFFF,1} 
            end
        end
    end
    
    if t.bg_led ~= nil and #t.bg_led~=2    then t.bg_led = t.bg_colour end
    if t.fg_led ~= nil and #t.fg_led~=2    then t.fg_led = t.fg_colour end
    if t.alarm_led~= nil and #t.alarm_led~=2 then t.alarm_led = t.fg_led end
    
    if t.led_effect~=nil then
        if t.bg_led == nil then t.bg_led = t.bg_colour end
        if t.fg_led == nil     then t.fg_led = t.fg_colour end
        if t.alarm_led == nil  then t.alarm_led = t.fg_led end
    end
    

    if t.alarm==nil then t.alarm = t.max end --0.8*t.max end
    if t.smooth == nil then t.smooth = false end

    if t.skew_x == nil then 
        t.skew_x=0 
    else
        t.skew_x = math.pi*t.skew_x/180    
    end
    if t.skew_y == nil then 
        t.skew_y=0
    else
        t.skew_y = math.pi*t.skew_y/180    
    end
    
    if t.reflection_alpha==nil then t.reflection_alpha=0 end
    if t.reflection_length==nil then t.reflection_length=1 end
    if t.reflection_scale==nil then t.reflection_scale=1 end
    
    --end of default values
    

     local function rgb_to_r_g_b(col_a)
        return ((col_a[1] / 0x10000) % 0x100) / 255., ((col_a[1] / 0x100) % 0x100) / 255., (col_a[1] % 0x100) / 255., col_a[2]
    end
    
    
    --functions used to create patterns

    local function create_smooth_linear_gradient(x0,y0,x1,y1)
        local pat = cairo_pattern_create_linear (x0,y0,x1,y1)
        cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
        cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
        if t.mid_colour ~=nil then
            for i=1, #t.mid_colour do
                cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
            end
        end
        return pat
    end

    local function create_smooth_radial_gradient(x0,y0,r0,x1,y1,r1)
        local pat =  cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
        cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(t.fg_colour))
        cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(t.alarm_colour))
        if t.mid_colour ~=nil then
            for i=1, #t.mid_colour do
                cairo_pattern_add_color_stop_rgba (pat, t.mid_colour[i][1], rgb_to_r_g_b({t.mid_colour[i][2],t.mid_colour[i][3]}))
            end
        end
        return pat
    end
    
    local function create_led_linear_gradient(x0,y0,x1,y1,col_alp,col_led)
        local pat = cairo_pattern_create_linear (x0,y0,x1,y1) ---delta, 0,delta+ t.width,0)
        cairo_pattern_add_color_stop_rgba (pat, 0.0, rgb_to_r_g_b(col_alp))
        cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
        cairo_pattern_add_color_stop_rgba (pat, 1.0, rgb_to_r_g_b(col_alp))
        return pat
    end

    local function create_led_radial_gradient(x0,y0,r0,x1,y1,r1,col_alp,col_led,mode)
        local pat = cairo_pattern_create_radial (x0,y0,r0,x1,y1,r1)
        if mode==3 then
            cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_alp))                
            cairo_pattern_add_color_stop_rgba (pat, 0.5, rgb_to_r_g_b(col_led))
            cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))                
        else
            cairo_pattern_add_color_stop_rgba (pat, 0, rgb_to_r_g_b(col_led))
            cairo_pattern_add_color_stop_rgba (pat, 1, rgb_to_r_g_b(col_alp))                
        end
        return pat
    end






    local function draw_single_bar()
        --this fucntion is used for bars with a single block (blocks=1) but 
        --the drawing is cut in 3 blocks : value/alarm/background
        --not zvzimzblr for circular bar
        local function create_pattern(col_alp,col_led,bg)
            local pat
            
            if not t.smooth then
                if t.led_effect=="e" then
                    pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
                elseif t.led_effect=="a" then
                    pat = create_led_linear_gradient (t.width/2, 0,t.width/2,-t.height,col_alp,col_led)
                elseif  t.led_effect=="r" then
                    pat = create_led_radial_gradient (t.width/2, -t.height/2, 0, t.width/2,-t.height/2,t.height/1.5,col_alp,col_led,2)
                else
                    pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
                end
            else
                if bg then
                    pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
                else
                    pat = create_smooth_linear_gradient(t.width/2, 0, t.width/2,-t.height)
                end
            end
            return pat
        end
        
        local y1=-t.height*pct/100
        local y2=nil
        if pct>(100*t.alarm/t.max) then 
            y1 = -t.height*t.alarm/100
            y2 = -t.height*pct/100
            if t.smooth then y1=y2 end
        end
        
        if t.angle_bar==0 then
        
            --block for fg value
            pat = create_pattern(t.fg_colour,t.fg_led,false)
            cairo_set_source(cr,pat)
            cairo_rectangle(cr,0,0,t.width,y1)
            cairo_fill(cr)
        
            -- block for alarm value            
            if not t.smooth and y2 ~=nil then 
                pat = create_pattern(t.alarm_colour,t.alarm_led,false)
                cairo_set_source(cr,pat)
                cairo_rectangle(cr,0,y1,t.width,y2-y1)
                cairo_fill(cr)
                y3=y2
            else
                y2,y3=y1,y1
            end
            -- block for bg value
            cairo_rectangle(cr,0,y2,t.width,-t.height-y3)
            pat = create_pattern(t.bg_colour,t.bg_led,true)
            cairo_set_source(cr,pat)
            cairo_pattern_destroy(pat)
            cairo_fill(cr)
        end        
    end  --end single bar
    





    local function draw_multi_bar()
        --function used for bars with 2 or more blocks
        for pt = 1,t.blocks do 
            --set block y
            local y1 = -(pt-1)*(t.height+t.space)
            local light_on=false
            
            --set colors
            local col_alp = t.bg_colour
            local col_led = t.bg_led
            if pct>=(100/t.blocks) or pct>0 then --ligth on or not the block
                if pct>=(pcb*(pt-1))  then 
                    light_on = true
                    col_alp = t.fg_colour
                    col_led = t.fg_led
                    if pct>=(100*t.alarm/t.max) and (pcb*pt)>(100*t.alarm/t.max) then 
                        col_alp = t.alarm_colour 
                        col_led = t.alarm_led 
                    end
                end
            end

            --set colors
            --have to try to create gradients outside the loop ?
            local pat 
            
            if not t.smooth then
                if t.angle_bar==0 then
                    if t.led_effect=="e" then
                        pat = create_led_linear_gradient (-delta, 0,delta+ t.width,0,col_alp,col_led)
                    elseif t.led_effect=="a" then
                        pat = create_led_linear_gradient (t.width/2, -t.height/2+y1,t.width/2,0+t.height/2+y1,col_alp,col_led)                    
                    elseif  t.led_effect=="r" then
                        pat = create_led_radial_gradient (t.width/2, y1, 0, t.width/2,y1,t.width/1.5,col_alp,col_led,2)    
                    else
                        pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))
                    end
                else
                     if t.led_effect=="a"  then
                         pat = create_led_radial_gradient (0, 0, t.radius+(t.height+t.space)*(pt-1),
                                                         0, 0, t.radius+(t.height+t.space)*(pt),                         
                                             col_alp,col_led,3)    
                    else
                        pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(col_alp))                    
                    end
                    
                end
            else
                
                if light_on then
                    if t.angle_bar==0 then
                        pat = create_smooth_linear_gradient(t.width/2, t.height/2, t.width/2,-(t.blocks-0.5)*(t.height+t.space))
                    else
                        pat = create_smooth_radial_gradient(0, 0, (t.height+t.space),  0,0,(t.blocks+1)*(t.height+t.space),2)
                    end
                else        
                    pat = cairo_pattern_create_rgba  (rgb_to_r_g_b(t.bg_colour))
                end
            end
            cairo_set_source (cr, pat)
            cairo_pattern_destroy(pat)

            --draw a block
            if t.angle_bar==0 then
                cairo_move_to(cr,0,y1)
                cairo_line_to(cr,t.width,y1)
            else        
                cairo_arc( cr,0,0,
                    t.radius+(t.height+t.space)*(pt)-t.height/2,
                     -t.angle_bar -math.pi/2 ,
                     t.angle_bar -math.pi/2)
            end
            cairo_stroke(cr)
        end    
    end
    
    
    
    
    local function setup_bar_graph()
        --function used to retrieve the value to display and to set the cairo structure
        if t.blocks ~=1 then t.y=t.y-t.height/2 end
        
        local value = 0
        if t.name ~="" then
            value = tonumber(conky_parse(string.format('${%s %s}', t.name, t.arg)))
        else
            value = tonumber(t.arg)
        end

        if value==nil then value =0 end
        
        pct = 100*value/t.max
        pcb = 100/t.blocks
        
        cairo_set_line_width (cr, t.height)
        cairo_set_line_cap  (cr, cap)
        cairo_translate(cr,t.x,t.y)
        cairo_rotate(cr,t.angle)

        local matrix0 = cairo_matrix_t:create()
        cairo_matrix_init (matrix0, 1,t.skew_y,t.skew_x,1,0,0)
        cairo_transform(cr,matrix0)

    
        
        --call the drawing function for blocks
        if t.blocks==1 and t.angle_bar==0 then
            draw_single_bar()
            if t.reflection=="t" or t.reflection=="b" then cairo_translate(cr,0,-t.height) end
        else
            draw_multi_bar()
        end

        --dot for reminder
        --[[
        if t.blocks ~=1 then
            cairo_set_source_rgba(cr,1,0,0,1)
            cairo_arc(cr,0,t.height/2,3,0,2*math.pi)
            cairo_fill(cr)
        else
            cairo_set_source_rgba(cr,1,0,0,1)
            cairo_arc(cr,0,0,3,0,2*math.pi)
            cairo_fill(cr)
        end
]]
        --call the drawing function for reflection and prepare the mask used        
        if t.reflection_alpha>0 and t.angle_bar==0 then
            local pat2
            local matrix1 = cairo_matrix_t:create()
            if t.angle_bar==0 then
                pts={-delta/2,(t.height+t.space)/2,t.width+delta,-(t.height+t.space)*(t.blocks)}
                if t.reflection=="t" then
                    cairo_matrix_init (matrix1,1,0,0,-t.reflection_scale,0,-(t.height+t.space)*(t.blocks-0.5)*2*(t.reflection_scale+1)/2)
                    pat2 = cairo_pattern_create_linear (t.width/2,-(t.height+t.space)*(t.blocks),t.width/2,(t.height+t.space)/2)
                elseif t.reflection=="r" then
                    cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,delta+2*t.width,0)
                    pat2 = cairo_pattern_create_linear (delta/2+t.width,0,-delta/2,0)
                elseif t.reflection=="l" then
                    cairo_matrix_init (matrix1,-t.reflection_scale,0,0,1,-delta,0)
                    pat2 = cairo_pattern_create_linear (-delta/2,0,delta/2+t.width,-0)
                else --bottom
                    cairo_matrix_init (matrix1,1,0,0,-1*t.reflection_scale,0,(t.height+t.space)*(t.reflection_scale+1)/2)
                    pat2 = cairo_pattern_create_linear (t.width/2,(t.height+t.space)/2,t.width/2,-(t.height+t.space)*(t.blocks))
                end
            end
            cairo_transform(cr,matrix1)

            if t.blocks==1 and t.angle_bar==0 then
                draw_single_bar()
                cairo_translate(cr,0,-t.height/2) 
            else
                draw_multi_bar()
            end
            
            
            cairo_set_line_width(cr,0.01)
            cairo_pattern_add_color_stop_rgba (pat2, 0,0,0,0,1-t.reflection_alpha)
            cairo_pattern_add_color_stop_rgba (pat2, t.reflection_length,0,0,0,1)
            if t.angle_bar==0 then
                cairo_rectangle(cr,pts[1],pts[2],pts[3],pts[4])
            end
            cairo_clip_preserve(cr)
            cairo_set_operator(cr,CAIRO_OPERATOR_CLEAR)
            cairo_stroke(cr)
            cairo_mask(cr,pat2)
            cairo_pattern_destroy(pat2)
            cairo_set_operator(cr,CAIRO_OPERATOR_OVER)
            
        end --reflection
        
        
    end --setup_bar_graph()

    
    --start here !
    setup_bar_graph()
    cairo_restore(cr)
end
```

---

### Post by damnitdan on 2011-03-13
My conky has this text for alignment...

# Text alignment, other possible values are commented
#alignment top_left
**alignment top_right**
#alignment bottom_left
#alignment bottom_right

---

### Post by ECET on 2011-03-13
I tried this.....it did not change anything......anybody else have any ideas?......please help.....thx!

---

### Post by ECET on 2011-03-14
I could really use some help here......I just need to get this moved over to the right.....thx

---

### Post by andrewthomas on 2011-03-14
If 


```
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
```If does not work, then you then have some other issues within your conkyrc.  

There is way too much code there to wade through.  

What you need to do is create a simple code to test with

For example:
```
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Use Xft?
use_xft yes

xftfont Droid Sans:size=8
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
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 220 0
maximum_width 220

# Draw shades?
draw_shades no
default_color D6D6D6 #4D4D4D
# Draw outlines?
draw_outline no
# border width
border_width 1

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 40

TEXT
${goto 7.5}${voffset 4}${font Poky:size=15}a${font}${goto 32}${voffset -10}Highest: ${alignr 13}CPU${alignr}RAM
${goto 32}${voffset -5.5}${hr 1}
${voffset -1}${goto 32}${top name 1} ${goto 124}${top cpu 1}${alignr }${top mem 1}
${voffset -1}${goto 32}${top name 2} ${goto 124}${top cpu 2}${alignr }${top mem 2}
${voffset -1}${goto 32}${top name 3} ${goto 124}${top cpu 3}${alignr }${top mem 3}
${voffset -1}${goto 32}${top name 4} ${goto 124}${top cpu 4}${alignr }${top mem 4}
${voffset -1}${goto 32}${top name 5} ${goto 124}${top cpu 5}${alignr }${top mem 5}
${voffset -1}${goto 32}${top name 6} ${goto 124}${top cpu 6}${alignr }${top mem 6}
#${voffset -1}${goto 32}${top name 7} ${goto 124}${top cpu 7}${alignr }${top mem 7}
#${voffset -1}${goto 32}${top name 8} ${goto 124}${top cpu 8}${alignr }${top mem 8}

```

---

### Post by jcolyn on 2011-03-14
The alignment issue can be fixed by searching for the below line in your .conkyrc file 

```
#### ## Text alignment. # alignment tr
```And change it to ```
alignment top_right
```To get the bars etc you need the lua script

If you want a lua-conky go here for more information. [http://conky.wikia.com/wiki/Conky_and_Lua](http://conky.wikia.com/wiki/Conky_and_Lua)

or here [http://www.webupd8.org/2011/02/try-this-great-looking-conky-lua.html](http://www.webupd8.org/2011/02/try-this-great-looking-conky-lua.html)

You can also google conky-lua for more sites..

---

### Post by 5149.5 on 2011-03-14
Have you seen this?
[http://www.webupd8.org/2010/06/conkywizard-gui-to-set-up-conky.html](http://www.webupd8.org/2010/06/conkywizard-gui-to-set-up-conky.html)

---

### Post by jcolyn on 2011-03-14
I never cared much for conkywizard. Instead I write my own .conkyrc and conky scripts but for the beginner it is a good starting point..

---

### Post by 5149.5 on 2011-03-14
> **jcolyn said:**
> I never cared much for conkywizard. Instead I write my own .conkyrc and conky scripts but for the beginner it is a good starting point..

Yeah its more fun to do it yourself but sometimes it makes sense to minimize the typing by just using a wizard and then going through the output of the wizard  line by line and tweaking it to make it your own.

---

