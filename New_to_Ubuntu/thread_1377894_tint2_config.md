---
title: "tint2 config"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Psumi on 2010-01-10
I saw this on the wiki page of tint2 google code:

```
#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------
rounded = 1
border_width = 0
background_color = #282828 50
border_color = #000000 0

rounded = 1
border_width = 1
background_color = #ffffff 30
border_color = #ffffff 60

rounded = 5
border_width = 0
background_color = #ffffff 18
border_color = #ffffff 70

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_monitor = all
panel_position = bottom left
panel_size = 100% 38
panel_margin = 0 0
panel_padding = 7 3 7
font_shadow = 0
panel_background_id = 0
wm_menu = 0
panel_dock = 0
real_transparency = 0
panel_layer = bottom

#---------------------------------------------
# TASKBAR
#---------------------------------------------
#taskbar_mode = single_desktop
taskbar_mode = multi_desktop
taskbar_padding = 0 0 0
taskbar_background_id = 1
#taskbar_active_background_id = 0


#---------------------------------------------
# TASKS
#---------------------------------------------
task_icon = 1
task_text = 0
task_maximum_size = 45 35
task_centered = 1
task_padding = 2 1
task_font = sans bold 9
task_font_color = #ffffff 60
task_active_font_color = #ffffff 100
task_background_id = 0
task_active_background_id = 2

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
systray = 1
systray_padding = 0 4 5
systray_background_id = 0
systray_sort = left2right
systray_icon_size = 0

#---------------------------------------------
# CLOCK
#---------------------------------------------
#time1_format = %H:%M
#time1_font = sans 8
#time2_format = %A %d %B
#time2_font = sans 6
#clock_font_color = #ffffff 76
#clock_padding = 1 0
#clock_background_id = 0
#clock_lclick_command = xclock
#clock_rclick_command = orage
#clock_tooltip = %A %d %B
#time1_timezone = :US/Hawaii
#time2_timezone = :Europe/Berlin
#clock_tooltip_timezone = :/usr/share/zoneinfo/Europe/Paris

#---------------------------------------------
# BATTERY
#---------------------------------------------
battery = 0
battery_low_status = 10
battery_low_cmd = notify-send "battery low"
bat1_font = sans 8
bat2_font = sans 6
battery_font_color = #ffffff 76
battery_padding = 1 0
battery_background_id = 0

#---------------------------------------------
# TOOLTIP
#---------------------------------------------
tooltip = 0
tooltip_padding = 2 2
tooltip_show_timeout = 0.7
tooltip_hide_timeout = 0.3
tooltip_background_id = 1
tooltip_font_color = #OOOOOO 80
tooltip_font = sans 10

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = none
mouse_scroll_up = toggle
mouse_scroll_down = iconify

#---------------------------------------------
# AUTOHIDE OPTIONS
#---------------------------------------------
autohide = 0
autohide_show_timeout = 0.3
autohide_hide_timeout = 2
autohide_height = 4
strut_policy = minimum
```

but most of the options are "invalid" according to tint. Can someone fix it so it works?

---

### Post by dmillerct on 2010-01-10
> **Psumi said:**
> I saw this on the wiki page of tint2 google code:

```
#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------
rounded = 1
border_width = 0
background_color = #282828 50
border_color = #000000 0

rounded = 1
border_width = 1
background_color = #ffffff 30
border_color = #ffffff 60

rounded = 5
border_width = 0
background_color = #ffffff 18
border_color = #ffffff 70

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_monitor = all
panel_position = bottom left
panel_size = 100% 38
panel_margin = 0 0
panel_padding = 7 3 7
font_shadow = 0
panel_background_id = 0
wm_menu = 0
panel_dock = 0
real_transparency = 0
panel_layer = bottom

#---------------------------------------------
# TASKBAR
#---------------------------------------------
#taskbar_mode = single_desktop
taskbar_mode = multi_desktop
taskbar_padding = 0 0 0
taskbar_background_id = 1
#taskbar_active_background_id = 0


#---------------------------------------------
# TASKS
#---------------------------------------------
task_icon = 1
task_text = 0
task_maximum_size = 45 35
task_centered = 1
task_padding = 2 1
task_font = sans bold 9
task_font_color = #ffffff 60
task_active_font_color = #ffffff 100
task_background_id = 0
task_active_background_id = 2

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
systray = 1
systray_padding = 0 4 5
systray_background_id = 0
systray_sort = left2right
systray_icon_size = 0

#---------------------------------------------
# CLOCK
#---------------------------------------------
#time1_format = %H:%M
#time1_font = sans 8
#time2_format = %A %d %B
#time2_font = sans 6
#clock_font_color = #ffffff 76
#clock_padding = 1 0
#clock_background_id = 0
#clock_lclick_command = xclock
#clock_rclick_command = orage
#clock_tooltip = %A %d %B
#time1_timezone = :US/Hawaii
#time2_timezone = :Europe/Berlin
#clock_tooltip_timezone = :/usr/share/zoneinfo/Europe/Paris

#---------------------------------------------
# BATTERY
#---------------------------------------------
battery = 0
battery_low_status = 10
battery_low_cmd = notify-send "battery low"
bat1_font = sans 8
bat2_font = sans 6
battery_font_color = #ffffff 76
battery_padding = 1 0
battery_background_id = 0

#---------------------------------------------
# TOOLTIP
#---------------------------------------------
tooltip = 0
tooltip_padding = 2 2
tooltip_show_timeout = 0.7
tooltip_hide_timeout = 0.3
tooltip_background_id = 1
tooltip_font_color = #OOOOOO 80
tooltip_font = sans 10

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = none
mouse_scroll_up = toggle
mouse_scroll_down = iconify

#---------------------------------------------
# AUTOHIDE OPTIONS
#---------------------------------------------
autohide = 0
autohide_show_timeout = 0.3
autohide_hide_timeout = 2
autohide_height = 4
strut_policy = minimum
```

but most of the options are "invalid" according to tint. Can someone fix it so it works?

Are you running this on a laptop? I am guessing the option that is causing the issue is the battery section. Everything else is quite generic. 

If you are not running tint2 on a laptop try removing the batter section of the configuration. If you are on a laptop make sure the Battery ID matches what you have. I.E. BATT0

---

### Post by ankspo71 on 2010-01-10
Hi,
This is the default tint2rc from Ubuntu 10.04 (test release) with tint2_0.7.1-1_i386 from the repos installed. It seems to work fine too.

```

#---------------------------------------------
# TINT2 CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# BACKGROUND AND BORDER
#---------------------------------------------
rounded = 7
border_width = 2
background_color = #000000 60
border_color = #ffffff 18

rounded = 5
border_width = 0
background_color = #ffffff 40
border_color = #ffffff 50

rounded = 5
border_width = 0
background_color = #ffffff 18
border_color = #ffffff 70

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_monitor = all
panel_position = bottom center
panel_size = 94% 30
panel_margin = 0 0
panel_padding = 7 0
font_shadow = 0
panel_background_id = 1
wm_menu = 0

#---------------------------------------------
# TASKBAR
#---------------------------------------------
#taskbar_mode = multi_desktop
taskbar_mode = single_desktop
taskbar_padding = 2 3 2
taskbar_background_id = 0

#---------------------------------------------
# TASKS
#---------------------------------------------
task_icon = 1
task_text = 1
task_width = 140
task_centered = 1
task_padding = 6 3
task_font = sans 7
task_font_color = #ffffff 70
task_active_font_color = #ffffff 85
task_background_id = 3
task_active_background_id = 2

#---------------------------------------------
# SYSTRAYBAR
#---------------------------------------------
systray_padding = 0 4 5
systray_background_id = 0

#---------------------------------------------
# CLOCK
#---------------------------------------------
time1_format = %H:%M
time1_font = sans 8
time2_format = %A %d %B
time2_font = sans 6
clock_font_color = #ffffff 76
clock_padding = 1 0
clock_background_id = 0
#clock_lclick_command = xclock
clock_rclick_command = orage

#---------------------------------------------
# BATTERY
#---------------------------------------------
battery = 0
battery_low_status = 10
battery_low_cmd = notify-send "battery low"
bat1_font = sans 8
bat2_font = sans 6
battery_font_color = #ffffff 76
battery_padding = 1 0
battery_background_id = 0


#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = none
mouse_right = close
mouse_scroll_up = toggle
mouse_scroll_down = iconify


```

---

### Post by Psumi on 2010-01-10
> **dmillerct said:**
> Are you running this on a laptop? I am guessing the option that is causing the issue is the battery section. Everything else is quite generic. 

If you are not running tint2 on a laptop try removing the batter section of the configuration. If you are on a laptop make sure the Battery ID matches what you have. I.E. BATT0

Well, most invalid options are basically every single one of the options at the end. For example, it says autohide is not a valid option.

---

### Post by Psumi on 2010-01-11
Forget this, I'll use lxpanel -_- What a waste.

---

### Post by thil77 on 2010-01-11
The current stable release is tint2-0.8.

[http://code.google.com/p/tint2/wiki/Configure](http://code.google.com/p/tint2/wiki/Configure)
explain config option for 0.8.

autohide is only in developement version (SVN). See
[http://code.google.com/p/tint2/wiki/Configure?ts=1263233612&updated=Configure#Panel_autohide](http://code.google.com/p/tint2/wiki/Configure?ts=1263233612&updated=Configure#Panel_autohide)

---

### Post by Psumi on 2010-01-23
Can someone give me a config file that does the following then?

Window List (So I can minimize to and restore from)
Workspace Switcher (If even possible?)
systray
clock

That's all I really need. And can someone make sure it works in the tint2 that currently is in the ubuntu repos rather than SVN?

I want to get rid of as many RAM inducing things as possible, and this can help me in the right direction.

And is there a network monitor for tint2? If not, can someone give me a conky config that monitors signal strength (wifi) and network name, etc? As well as the current weather? and battery information?

And can someone PLEASE tell me WHERE to put the conky config?

---

### Post by Psumi on 2010-01-23
I'd build a debian package for it (the newest tint2) myself but:

```
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package tint2
dpkg-buildpackage: source version 0.9-rc1-1
dpkg-buildpackage: source changed by tint2 dev-team <null@dev.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
[ ! -f Makefile ] || /usr/bin/make distclean
rm -f config.sub config.guess
dh_clean 
 dpkg-source -b tint2-0.9-rc1
dpkg-source: error: source package has two conflicting values - tint2-0.9 and tint2
dpkg-buildpackage: error: dpkg-source -b tint2-0.9-rc1 gave error exit status 255
```

thanks giftwrap, for not telling me what I need to do. :| I'm not about to make from source.

And there's no tint on getdeb: [http://www.getdeb.net/updates/Ubuntu/9.10/?q=tint](http://www.getdeb.net/updates/Ubuntu/9.10/?q=tint)

---

