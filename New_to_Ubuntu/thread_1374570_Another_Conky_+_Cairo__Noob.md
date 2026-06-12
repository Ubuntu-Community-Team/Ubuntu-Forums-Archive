---
title: "Another Conky + Cairo  Noob"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Apv507 on 2010-01-07
Hello Ubuntu Forums,

I'm another semi-ubuntu-literate individual hoping to take my ubuntu customization to the next level. I plan to get rid of both panels and use Cairo and Conky to meet all my needs (and look pretty slick in the process). Before I make the leap to customizing my actual Ubuntu installation I plan to play around on a VirtualBox install until I have the configuration how I want it. There are a few questions i have for the conky and cairo masters out there:

1st, I've read that conky can display RhythmBox's currently playing track, but is there any way to control RB using conky? I use music-applet more than any other applet and I don't want to give up the convenience.

2nd, I can program a TI-83 plus calculator, which uses very basic basic, that's about the extend of my programing abilities and I the code aspect of conky some what intimidating. I'm not a complete idiot when it comes to computers. it just seems like a daunting task and I'm not always sure what I'm looking at or what to put where to get the desired effects. Does anyone know of a beginner's guide to conky code? 

3rd, Does Cairo have a minimized window feature. like rocket dock on windows, or the standard dock on mac? 

4th Any tips or pointers on both would be greatly appreciated. 

Thanks in advance,
Andrew

---

### Post by tom.swartz07 on 2010-01-07
> **Apv507 said:**
> Hello Ubuntu Forums,

I'm another semi-ubuntu-literate individual hoping to take my ubuntu customization to the next level. I plan to get rid of both panels and use Cairo and Conky to meet all my needs (and look pretty slick in the process). Before I make the leap to customizing my actual Ubuntu installation I plan to play around on a VirtualBox install until I have the configuration how I want it. There are a few questions i have for the conky and cairo masters out there:

1st, I've read that conky can display RhythmBox's currently playing track, but is there any way to control RB using conky? I use music-applet more than any other applet and I don't want to give up the convenience.

2nd, I can program a TI-83 plus calculator, which uses very basic basic, that's about the extend of my programing abilities and I the code aspect of conky some what intimidating. I'm not a complete idiot when it comes to computers. it just seems like a daunting task and I'm not always sure what I'm looking at or what to put where to get the desired effects. Does anyone know of a beginner's guide to conky code? 

3rd, Does Cairo have a minimized window feature. like rocket dock on windows, or the standard dock on mac? 

4th Any tips or pointers on both would be greatly appreciated. 

Thanks in advance,
Andrew

Hey Andrew!

I used this to help me get started with Conky. [http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/](http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/)

It shows you how to look into the code and get things just how you want it. Plus, it looks friggin awesome! :D

Unfortunately, the current versions of conky dont allow you to interact. Its 'read only' text thats displayed. The next version will allow you to edit text, but thats about it.

You could learn up at [www.conkyhardcore.com](www.conkyhardcore.com)

Heres a blog to keep you up to date with conky news: [http://mylittledesktop.blogspot.com/](http://mylittledesktop.blogspot.com/)

I used to program on my TI 83+ and my TI 89. Once you get into conky, its just like a TI calculator. Trust me!

Im not too sure about cairo-dock, but I know Avant Window Navigator (a less-resource-hungry version of cairo) allows you do do what youve described.



Oh, and heres a gratuitous pic of my current desktop:
[IMG]http://lh6.ggpht.com/_tORug_uHNu4/S0QcUlqn4BI/AAAAAAAAAKw/BlkWrwXTKqY/s800/Screenshot-1.png[/IMG]

Hope this helps!

---

### Post by Apv507 on 2010-01-07
Thanks for the quick and reply. So AWN is the way to go, noted. Your desktop looks great. Does AWN allow for control of RhythmBox? I DOUBT it but I thought I would ask.. If worse comes to worse Ill just use the controls on my keyboard. (Lazy I know) Thanks again for the links. All other suggestions are still welcome.

---

### Post by tom.swartz07 on 2010-01-07
> **Apv507 said:**
> Thanks for the quick and reply. So AWN is the way to go, noted. Your desktop looks great. Does AWN allow for control of RhythmBox? I DOUBT it but I thought I would ask.. If worse comes to worse Ill just use the controls on my keyboard. (Lazy I know) Thanks again for the links. All other suggestions are still welcome.

the newest version of awn (you need to add their ppa for awn-trunk) will let you control rhythmbox from the dock. That's what the icon in my screenie does! ;)

you could also look into Docky- that's the one I have on the left. Google "omg!ubuntu docky" for some really good guides on the omg! Ubuntu blog. 

Have fun!

---

### Post by fabounet on 2010-01-07
of course Cairo-Dock has thumbail ability, the option is in the Taskbar module.
and is very light too, depend on what you put indside of course...

---

### Post by Apv507 on 2010-01-07
I couldn't get the Weather or Gmail to work.. But I think thats due to the fact that I was in virtualbox. Do you know what text I need to insert to show CPU Temp and GPU Temp, Assuming I have installed lm-sensor and ran sensors-detect?

Thanks again for your help, its not that much different from HTML.

---

### Post by tom.swartz07 on 2010-01-07
> **Apv507 said:**
> I couldn't get the Weather or Gmail to work.. But I think thats due to the fact that I was in virtualbox. Do you know what text I need to insert to show CPU Temp and GPU Temp, Assuming I have installed lm-sensor and ran sensors-detect?

Thanks again for your help, its not that much different from HTML.

Certainly! im glad to help!

I think your trouble comes from the fact that its being run in Virtualbox. I cant say for certain, but its the most likely case. Virtualbox 'fibs' to the virtual OS about what kind of hardware your computer is using, and that might cause the discrepancy.


Once you fully implement it on a HDD install, it should be all good

AS A SIDE NOTE: you could always see what the sensors program is returning: you might just have something spelled wrong, an incorrect path or something:

```
sensors -f
```
returns the temp (in degrees F)

my return output: 
```
tom@ubuntu-karmic:~$ sensors -f
acpitz-virtual-0
Adapter: Virtual device
temp1:      +126.5°F  (crit = +203.0°F)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp: +116.6°F                                    
Core1 Temp: +120.2°F                                    


```

You should have a line in your .conkyrc that says sensors | grep core0, or something similar- just change it to what the sensors program returns


If you want, I could send you my .conkyrc file for you to look at and tweak. Just PM me and ill send it your way along with any of the scripts i have.


Good luck!

---

### Post by Apv507 on 2010-01-09
I still can't get the weather to work, I get an icon and then it says "F / (box) U.S. Regional F"  (it actually displays a little square where I typed box). Also I was unable to find the grep part of the code, but here is my sensors -f out put and my .conkyrc code.    The big things I want are Weather, Gpu temp, Core0 and Core 1 Temp and Core 0 and 1 usage, memory usage, computer runtime and the clock, So far I have the last three working. Anywhere here is my conkyrc code and a screen shot.

use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58



TEXT

${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}


  
   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Computer Runtime:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}



:~$ sensors -f
acpitz-virtual-0
Adapter: Virtual device
temp1:      +131.0°F  (crit = +210.2°F)                  
temp2:       +80.2°F  (crit = +221.0°F)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:     +120.2°F  (crit = +212.0°F)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:     +125.6°F  (crit = +212.0°F)

---

### Post by tom.swartz07 on 2010-01-09
> **Apv507 said:**
> I still can't get the weather to work, I get an icon and then it says "F / (box) U.S. Regional F"  (it actually displays a little square where I typed box). Also I was unable to find the grep part of the code, but here is my sensors -f out put and my .conkyrc code.    The big things I want are Weather, Gpu temp, Core0 and Core 1 Temp and Core 0 and 1 usage, memory usage, computer runtime and the clock, So far I have the last three working. Anywhere here is my conkyrc code and a screen shot.

use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58



TEXT

${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}


  
   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Computer Runtime:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}



:~$ sensors -f
acpitz-virtual-0
Adapter: Virtual device
temp1:      +131.0°F  (crit = +210.2°F)                  
temp2:       +80.2°F  (crit = +221.0°F)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:     +120.2°F  (crit = +212.0°F)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:     +125.6°F  (crit = +212.0°F)

using that code- i have the same (we traded sources). You need to have an empty file in your home folder named 'weather'. 
Just open your home folder, right click the background of the window, hit create document>empty file. Name it weather and re-run conky. You could grep any of the information from that file.

Currently, Mine has ```
Current conditions as of 2:53 pm MDT

Partly Cloudy

Feels Like:
    59°
Barometer:
    29.85 in and steady
Humidity:
    53%
Visibility:
    10 mi
Dewpoint:
    42°
Wind:
    NW 9 mph
Sunrise:
    8:03 am
Sunset:
    6:55 pm

59°
```

That should do it- I know the code for the one is written in polish (i think), when i translated it with google it seems that you could uncomment some of the lines in 'pogodynka' and it will return some of the results found in the weather file.

---

