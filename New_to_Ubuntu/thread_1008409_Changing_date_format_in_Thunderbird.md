---
title: "Changing date format in Thunderbird?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by GazJ74 on 2008-12-11
I have recently installed Ubuntu 'Intrepid Ibex' and I have been very impressed with it.

But I have noticed in Thunderbird the date sent for my emails is in the American format MM/DD/YYYY.  I would like to change it to DD/MM/YYYY.

In System/Administration/Time and Date is set as 'Europe/London'.

I typed this command in a Terminal window :

locale -k LC_TIME

```
abday="Sun;Mon;Tue;Wed;Thu;Fri;Sat"
day="Sunday;Monday;Tuesday;Wednesday;Thursday;Friday;Saturday"
abmon="Jan;Feb;Mar;Apr;May;Jun;Jul;Aug;Sep;Oct;Nov;Dec"
mon="January;February;March;April;May;June;July;August;September;October;November;December"
am_pm="AM;PM"
d_t_fmt="%a %d %b %Y %r %Z"
d_fmt="%m/%d/%Y"
t_fmt="%r"
t_fmt_ampm="%I:%M:%S %p"
era=
era_year=""
era_d_fmt=""
alt_digits=
era_d_t_fmt=""
era_t_fmt=""
time-era-num-entries=0
time-era-entries="S"
week-ndays=7
week-1stday=19971130
week-1stweek=7
first_weekday=1
first_workday=2
cal_direction=1
timezone=""
date_fmt="%a %b %e %H:%M:%S %Z %Y"
time-codeset="UTF-8"
```

I noticed this line :

d_fmt="%m/%d/%Y"

is in the American date format but I have no idea how to change it.  Any ideas to solve this would be gratefully received.

---

### Post by jamesrl on 2008-12-11
NEVERMIND (orig written: The info is stored in /usr/lib/locale/en_??.utf8/ directory in a file called LC_TIME), which is true but irrelevant since it si in a binary format.

---

### Post by howefield on 2008-12-11
Sorry, misread the original posting

---

### Post by LowSky on 2008-12-11
you need to open about:config for Thunderbird, [http://kb.mozillazine.org/Date_display_format](http://kb.mozillazine.org/Date_display_format)

this link will help

---

### Post by jamesrl on 2008-12-11
Ok, try this
type in 
```
$env | grep LANG
LANG=en_US.UTF-8
GDM_LANG=en_US.UTF-8

```
this will tell you what locale settings you are using right now.  You can manually set it to something else, by typing locale -a (to see all locale options) and then say change it in the ~/.bashrc 
by adding appropriate line
like
LANG=en_GB.UTF-8
GDM_LANG=en_GB.UTF-8
if you want to be British

---

