---
title: "Monitor shuts off after 10 minutes"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by bpan123 on 2010-02-11
Running 9.10 on Atom 230.  No matter what settings, monitor shuts off after 10 minutes inactivity.

I've disabled power management:
  /system/preferences/power management/
    Actions=never 
    Display=never

I've disabled screen saver
  /system/preferences/screen saver/
    regard idle=1hr
    active=false
    lock=false

Still, monitor shuts off after 10 minutes.

-----

Only reference to this I could find on the forum was a user who was confused with the "blank screen" screen saver kicking in (by default?).

I have even tried enabling a screen saver (1 minute timeout) - even the screen saver won't work.  Nothing after 1min - but the display still shuts off after 10 minutes!

I can't find any other references to this on the forum, but can't believe other users haven't run into this problem.

What is going on here???  Are settings not being updated when I set them?

This was a fresh install from .iso 9.10 32bit, no problems, onto 160GB WD 2.5" HD.

I'm a relative newbie to linux and ubuntu (with a long IT background...) and would like to migrate all my computers from windows to ubuntu - if only I can figure out why little nagging problems like this keep annoying me!  

Ubuntu seems quite stable, support seems good, apps are plenty and decent quality... so why is such a little thing like this driving me to distraction!

Hope someone can help,
Brian

---

### Post by sisco311 on 2010-02-11
Please open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
xset q
```

---

### Post by Mustard on 2010-02-11
The place to look for clues might be in the /var/log directory.  There are a number of log files in this directory that record events as they occur, so its a great place to start.

From desktop you can go to Administration and use the Log Viewer.

From terminal you can

```

#change directory to /var/log

cd /var/log

#list the directory contents in human readable form, including hidden files,
#one page at a time (press spacebar to proceed to next page).
#All the options on the end of ls are not that necessary, but I like them. :)

ls -alh | more

#print the logfiles contents to the screen
#one page at a time
#examples below show log files that are most likely to 
#be helpful

cat syslog | more
cat dmesg | more
cat messages | more
cat kern.log | more

```

From there, if you can't see any issues yourself in the logs, you could attach some as text files to a post in this thread, and others could examine your log files for you.

---

### Post by bpan123 on 2010-02-11
> **sisco311 said:**
> Please open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
xset q
```

Done:
> 
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  auto repeat delay:  660    repeat rate:  25
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  0    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On


---

### Post by Mustard on 2010-02-11
> **sisco311 said:**
> Please open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
xset q
```

Nice command. :)  

You gotta love someone who knows the right command to start troubleshooting with.

---

### Post by bpan123 on 2010-02-11
Yeah, had to do a little research before I believed this one - ;)
I think it shows a contradiction though...  

**timeout:600 [seconds] = 10 minutes**

where does THAT come from???

...but then...

[B]DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On 			 		[/B]

... could my monitor have a setting that initiates the stand-by state???
checking...

...don't find any setting that would suggest this...

Brian

---

### Post by sisco311 on 2010-02-11
> **bpan123 said:**
> Done:

The X server's screensaver timeout is set to 600s=10minutes. The easiest way to disable it is to add:
```
xset s off
```
to the startup applications (System -> Preferences -> Startup Applications).

You may have to disable DPMS as well:
```
sh -c "xset -dpms && xset s off"
```

Log out & and log back in, then run *xset q* again; the output should look like this:
```
 Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  **timeout:  0**    cycle:  600
...
DPMS (Energy Star):
  Standby: 600    Suspend: 900    Off: 1200
  **DPMS is Disabled**
  Monitor is On

```

---

### Post by bpan123 on 2010-02-11
Done.  

> Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  0    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On


Didn't run the 2nd command to shut off dpms... still wondering why the screen saver won't run (even with 1 min setting)...

Added the command to the startup as suggested (THANK YOU!)

...waiting 10 minutes before posting - to test :P

[10 minutes later]

[SIZE=4][COLOR=DarkRed]SCREEN STILL ON!  THANK YOU SISCO311!!![/COLOR][/SIZE]

...still wondering why the screen saver doesn't kick in after 1 minute (still set!)

With a default install of 9.10, why am I having these problems?
Aren't others having the same issues?

Is this a bug that should be reported?

Thanks,
Brian

---

### Post by sisco311 on 2010-02-11
> **bpan123 said:**
> 

Is this a bug that should be reported?



Yep, a very old one. It was "fixed", but some users are still affected by the BUG.

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/30969](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/30969)

---

### Post by bpan123 on 2010-02-11
registered with bugs.launchpad.net - reviewed the data...

YES.  THIS IS A BUG - and is NOT resolved.

Me thinks (from the comments) that this goes much deeper than just your quick-fix
(AND I DO THANK YOU FOR THAT!)

This problem has existed for years.  YES YEARS.
I don't know why I'm one of the few to experience it - but yes, IT DOES EXIST.

...and it has been reported... again... and again... and again...

thanks,
Brian

---

### Post by lodp on 2011-10-24
I've got the same problem here, for the life of me I can't get the screen to stay on. It even goes black when VLC is running full screen.

The solution posted above doesn't work for me (though it did under 11.04). Here's my output of "xset -q":

> Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  **timeout:  0**    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
 [B] Standby: 0    Suspend: 0    Off: 0
  DPMS is Disabled[/B]

Everything screensaver- and screen blanking-related is turned off here, right? Yet still the screen goes black after 10mins. I'd appreciate any ideas.

---

### Post by allsourav on 2012-09-08
I just wonder if I can shut my monitor off after 5 min in lubuntu(12.04),as I can not find power management.

Thank you

---

### Post by lakersforce on 2013-01-11
Any solution to this problem yet? It's driving me crazy!

---

