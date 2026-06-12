---
title: "Monitor doesn't go to sleep"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by iakov on 2009-07-02
I spent lots of time trying to figure this out, but no advice seems to fix it for me.
I have a motherboard with Intel 945G video on board. 
Initially, after Ubuntu install, setting in power management to shut down monitor after 5 minutes of inactivity worked like a charm.
Now for whatever reason it's not happening at all. No amount of tinkering works.
Even if I adjust values in GNOME-Power_Manager in Configuration Editor monitor will not shut down.
Please suggest a solution to this.

---

### Post by unutbu on 2009-07-02
What is the output of 

```
xset q
```

---

### Post by iakov on 2009-07-02
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

---

### Post by unutbu on 2009-07-02
Try:
```
xset dpms 300 600
```

This should put your monitor in standby after 5 minutes of inactivity, and suspend the monitor after 10 minutes. (Assuming the monitor is DPMS compliant).

---

### Post by Razmear on 2009-07-02
> **unutbu said:**
> Try:
```
xset dpms 300 600
```

This should put your monitor in standby after 5 minutes of inactivity, and suspend the monitor after 10 minutes. (Assuming the monitor is DPMS compliant).

I'm watching this thread because I have the opposite problem. Even tho I have power management set to Never turn off my monitor, it goes to sleep after about 20 minutes anyways. 
Is there an xset command for 'never'? 

eb

btw, if your wondering why I don't want the monitor to 'power save' I use the TV out on my vid card to my TV, which also acts as my speakers, so if I'm playing music and the monitor switches off it also kills the sound from my TV, and having to come back and whack the mouse every 20 minutes or so is a bit of a PITA.

---

### Post by unutbu on 2009-07-02
Razmear, to stop Ubuntu from blanking or suspending your monitor, try 
```

xset -dpms
```

If it works and wish to make this change permanent, 
click System>Pref>Sessions and add the command there.

---

### Post by iakov on 2009-07-02
> **unutbu said:**
> Try:
```
xset dpms 300 600
```This should put your monitor in standby after 5 minutes of inactivity, and suspend the monitor after 10 minutes. (Assuming the monitor is DPMS compliant).

It did exactly what you said, but only once :(
Do I have to enter this command every time I want monitor to shut down?

---

### Post by unutbu on 2009-07-02
iakov, perhaps try clicking System>Pref>Sessions and adding the command there.
That will run the command once when you log in.

If that does not work, please do the following experiment:

Run
```

xset dpms 10 20
```

This will blank your monitor after just 10 seconds of inactivity. 
Wait for the monitor to blank.
Press a key.
Type
```

xset q
```
Look for 
```


DPMS (Energy Star):
  Standby: 10    Suspend: 20    Off: 0
  DPMS is Enabled
  Monitor is On
```

Do you see this or something else?
Wait for another 10 seconds. Does the monitor blank again?

---

### Post by iakov on 2009-07-02
Thanks alot for your help Sir.
I could not find Sessions, but will search to activate this.
The experiment you suggested does exactly what it supposed to as many times as i want to and I do have this:
DPMS (Energy Star):
  Standby: 10    Suspend: 20    Off: 0
  DPMS is Enabled
  Monitor is On

---

### Post by iakov on 2009-07-02
Interesting.
When I set this:

xset dpms 300 600


and waited 5 minutes monitor would not shut off, so I checked:
 xset q

and this is what I got:
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

Looks like something is resetting these settings.

I'll try to figure out what delay is a threshold shortly.

---

### Post by iakov on 2009-07-02
So here's what I discovered so far.

I set:
xset dpms 10 20

Monitor properly turns off in 10 seconds.
If I immediately wake it up and leave it untouched it will turn off in another 10 seconds.
If I leave monitor off for about 60 seconds, all settings get reset back to 0 like this:

DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

---

### Post by unutbu on 2009-07-02
What is the output of ```

gconftool-2  -R /apps/gnome-power-manager
```
and when you click System>Pref>Power Management, what settings do you have there?

---

### Post by iakov on 2009-07-02
~$ gconftool-2  -R /apps/gnome-power-manager
 /apps/gnome-power-manager/buttons:
  lid_battery = blank
  hibernate = hibernate
  suspend = nothing
  lid_ac = blank
  power = shutdown
 /apps/gnome-power-manager/keyboard:
  brightness_battery = 50
  brightness_ac = 100
 /apps/gnome-power-manager/actions:
  low_ups = nothing
  sleep_type_ac = suspend
  event_when_closed_battery = true
  critical_ups = shutdown
  sleep_type_battery = nothing
  critical_battery = shutdown
 /apps/gnome-power-manager/ambient:
  dim_policy = none
  correction_factor = 50
  correction_scale = 200
  poll_timeout = 60
  enable = true
 /apps/gnome-power-manager/thresholds:
  time_low = 1200
  time_critical = 300
  percentage_low = 10
  time_action = 120
  percentage_critical = 3
  percentage_action = 2
 /apps/gnome-power-manager/ui:
  show_context_menu = true
  show_actions_in_menu = true
  icon_policy = never
  enable_sound = false
 /apps/gnome-power-manager/lowpower:
  on_battery = true
  on_ups = true
  on_ac = false
 /apps/gnome-power-manager/lock:
  hibernate = true
  suspend = true
  gnome_keyring_hibernate = true
  blank_screen = false
  use_screensaver_settings = false
  gnome_keyring_suspend = false
 /apps/gnome-power-manager/timeout:
  sleep_display_ac = -6900
  sleep_computer_ac = 0
  sleep_computer_battery = 0
  sleep_display_battery = 300
 /apps/gnome-power-manager/statistics:
  graph_type = profile-charge-time
  show_events = true
  show_axis_labels = true
  smooth_data = true
  data_max_time = 21600
 /apps/gnome-power-manager/backlight:
  brightness_dim_battery = 50
  idle_dim_time = 30
  battery_reduce = true
  brightness_ac = 100
  idle_brightness = 30
  enable = false
  idle_dim_ac = false
  brightness_battery = 70
  dpms_method_ac = off
  dpms_method_battery = off
  idle_dim_battery = true
 /apps/gnome-power-manager/general:
  invalid_timeout = 500
  use_profile_time = true
  ignore_inhibit_requests = false
  check_type_cpu = false
  debug = false
  can_suspend = true
  can_hibernate = true
  use_time_for_policy = true
  network_sleep = false
  installed_schema = 3
  policy_suppression_timeout = 5
 /apps/gnome-power-manager/notify:
  discharging = true
  inhibit_lid = false
  sleep_failed = true
  low_power = true
  perhaps_recall = true
  low_capacity = true
  estimated_data = true
  fully_charged = true


Power Management:
Put computer to sleep: Never
Put display to sleep: 5 min

---

### Post by unutbu on 2009-07-02
I ran gconftool-2 -R /apps/gnome-power-manager on my system, and
compared your results with mine.

You have
```
sleep_display_ac = -6900
dpms_method_ac = off
dpms_method_battery = off
```

I have
```
sleep_display_ac = 300
dpms_method_ac = default
dpms_method_battery = default
```

These commands will change your settings to match mine:
```

gconftool-2 --type int --set /apps/gnome-power-manager/timeout/sleep_display_ac 300
gconftool-2 --type string --set /apps/gnome-power-manager/backlight/dpms_method_ac default
gconftool-2 --type string --set /apps/gnome-power-manager/backlight/dpms_method_battery default

```

PS. Instead of the above commands, you could also run
```

gconf-editor 
```

and navigate to /apps/gnome-power/manager and change the settings using the GUI.

---

### Post by iakov on 2009-07-03
None of that helped unfortunately.
Curiously, if I have Config Editor and Power Management windows open at the same time and I move slider for Display Sleep timer, "never" corresponds to "sleep_display_ac" = 0 and as I reduce time the number for "sleep_display_ac" reduces into negative territory with 1min being equal to -7140
5 min is -6900
Kind of strange, but perhaps it can point to something.

---

### Post by unutbu on 2009-07-03
Hm. When I move the sliders in System>Pref>Power Management,
I can see the numbers change in gconf-editor 
(/apps/gnome-power-manager/timeout/sleep_computer_ac and
/apps/gnome-power-manager/timeout/sleep_display_ac).

But unlike what you describe, the numbers I get are always positive or zero.

Are you running Jaunty? **If any Jaunty user is reading this, I'd appreciate it if you do the experiment above and see if you get negative or positive numbers.** Maybe there has been a change in the gnome-power-manager code between Intrepid and Jaunty... (?)

Also, are you running compiz? Perhaps just to see if it is affecting things, try again with compiz turned off.

---

### Post by iakov on 2009-07-03
Yes I'm running Jaunty.
I will have to read up on Compiz as I don't know what it is, I'm a very recent Windows defector :)

---

### Post by hilltop on 2009-07-04
This problem is frustrating me to no end.  I am running jaunty 64-bit and I have an nvidia GPU driving a Dell 2408WFP flat panel.  My gnome power manager settings do not show the negative numbers reported above, but I do see the dpms settings get set back automatically.  I have played with my display's settings as well as with the proprietary nvidia driver that is running on jaunty -- but cannot make the display go into power save mode.  This must be a bug in this kernel.  I will watch this thread to see if anyone comes up with a work-around.

---

### Post by iakov on 2009-07-04
I now know what Compiz is and I'm pretty sure I'm not running it if that makes any difference.

---

### Post by hilltop on 2009-07-04
I did some digging into this problem and I think I may know what is causing my particular situation.  Because I am running:

1) an nVidia GPU
2) the nVidia proprietary driver version 180.44 which is *earlier* than 180.51 (see [this page]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14"))
3) a displayport cable/adapters between my flat panel and my GPU

I may be experiencing a problem that was stated as fixed in the nVidia driver version 180.51.  The release notes for this version are [here]("http://www.nvidia.com/object/linux_display_amd64_180.51.html") and it says:

*"Fixed a DisplayPort interaction problem with power management suspend/resume events."*

Unfortunately, I cannot find any details around what specifically this "DisplayPort interaction problem" is, but it sounds like it could be what I am experiencing.

I installed the 180.44 nVidia drivers in my jaunty 64bit via the proprietary Hardware Drivers utility, and the utility is not yet showing anything later than this version.  The latest, of course, is 185.18.14.  My next step really ought to be to uninstall the 180.44 driver and manually install the 185.18.14 driver to see if this power management display problem is resolved.  But, being a relative noob still, I am a little afraid to go outside of the Ubuntu way of updating the driver.  I have read [here]("http://ubuntuforums.org/showthread.php?p=6235436#poststop") that I need to take special steps to ensure that x.org remains functional after a kernel upgrade.  But the instructions for this are dated from before jaunty was released, and I would like to make sure that whatever I do will work on 9.04.

So, if anyone reading this thread has the "display won't go into power save mode" problem, is running the nVidia drivers 180.44 or earlier and is using a DisplayPort to connect your monitor, please reply -- we might have the same situation.  I have seen numerous threads about power management display problems but I think we may have multiple issues going on.  For now, I am going to wait for the proprietary nVidia driver to be updated in the repository.

And if I am being way too cautious about installing the driver manually, then, hey, talk me down!

;)

---

### Post by unutbu on 2009-07-04
Hello hilltop, I don't know if installing nvdia driver version 185.18 will fix the problem, but if you'd like to try, here are excellent instructions: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

---

### Post by iakov on 2009-07-04
Is there a way to update Intel driver on mu MB?

---

### Post by itzcoatl666 on 2009-07-22
Hi everyone,

I'm having a sort of similar problem plus a little bit extra issue. The output of 'xset q' is the same than Iakov's; on the GUI I have the power management set to 11 minutes in the sleep display field (AC power). After those 11 minutes you may say the monitor goes to sleep, however, it just goes black, i.e., it's sending a black image -or signal if you want to call it that way- but not turning the monitor off. In a PC this wouldn't be a problem as I can just turn it off, however, on the laptop it's not possible.

I'm also using Jaunty version. My video card, however, is an ATI Radeon HD 3400 series on a Dell Studio 1535, the drivers are up-to-date, as far as I know.

Should I open a new thread or may I get help on this one?

---

### Post by sirctseb on 2009-10-19
Regarding the large negative timeout numbers:
Check your screensaver settings.
It looks like the values are the difference between the value you choose with the slider in Power Management Preferences and the value you choose with the slider in Screensaver Preferences which is labeled "Regard the computer as idle after:"

So if the screensaver idle time is 2 hours, and the display timeout is 1 minute, you have
1*60 - 2*60*60 = 60 - 7200 = -7140.

This is a small piece of my puzzle. I'm still trying to figure out why my desktop won't suspend by timeout. I think it also has something to do with having x11vnc running and possible compiz.

---

### Post by mageus on 2010-02-17
Anyone figure this out?

I have the same problem as itzcoatl - monitor goes black but doesn't turn off.

Changing the settings in Power Management or gconftool doesn't do anything; the monitor goes to 'sleep' after 10 minutes regardless of any settings.

Using the 'xset dpms' command works, but I'd rather change my settings within gnome.

xset q shows
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

Everything was working fine in Jaunty

Here's my specs:
Ubuntu 9.10 x64 (Karmic)
Nvidia 9800GT with 195.36.03 drivers.

I'm thinking it has to do with the X screensaver settings displayed above.  In Screensaver I have 'regard computer as idle' set to 1 minute.

Any ideas?

---

