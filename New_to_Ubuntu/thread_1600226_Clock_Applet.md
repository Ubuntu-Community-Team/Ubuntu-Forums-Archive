---
title: "Clock Applet"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by kamitsukai on 2010-10-18
For some reason I can't change the theme of the clock applet =[ I followed the guide on omgubuntu below

[http://www.omgubuntu.co.uk/2010/10/how-to-customize-the-clock-applet-in-ubuntu/](http://www.omgubuntu.co.uk/2010/10/how-to-customize-the-clock-applet-in-ubuntu/)

but it's still not working even after a reboot:confused:

I'm using Linux Mint 10 (Ubuntu 10.10)

Thanks in advance!

---

### Post by dondiego2 on 2010-10-18
What are you trying to change it to?  I just changed it to stacked but I could hardly read it because my bar is gray (default) and the font was kind of gray.  I changed it to blue and it works great.

---

### Post by kamitsukai on 2010-10-18
> **dondiego2 said:**
> What are you trying to change it to?  I just changed it to stacked but I could hardly read it because my bar is gray (default) and the font was kind of gray.  I changed it to blue and it works great.

I cant change it to any of them... although I'd like stacked it just stays as the default:confused:

---

### Post by dondiego2 on 2010-10-18
Try pasting this in the value box 

 <sup><span rise="3000" font_desc="ubuntu 7.5" color="#1848E5" weight="normal">%a %d %b</span></sup>%n<sub><span font_desc="ubuntu 7.5" color="#1848E5" weight="bold">%I:%M %p</span></sub>

It worked for me and font is blue with the time bold.  I had to increase the width of my tool bar a little because it was slightly cut off.

---

### Post by kamitsukai on 2010-10-18
> **dondiego2 said:**
> Try pasting this in the value box 

 <sup><span rise="3000" font_desc="ubuntu 7.5" color="#1848E5" weight="normal">%a %d %b</span></sup>%n<sub><span font_desc="ubuntu 7.5" color="#1848E5" weight="bold">%I:%M %p</span></sub>

It worked for me and font is blue with the time bold.  I had to increase the width of my tool bar a little because it was slightly cut off.

nope still nothing

---

### Post by dondiego2 on 2010-10-18
> **kamitsukai said:**
> nope still nothing


Just to make sure you are doing the same thing I am doing:

Alt-F2
type gconf-editor  <enter>
Select  apps/panel/applets/clock_screen0/prefs
In the window double click custom format
Put this 

<sup><span rise="3000" font_desc="ubuntu 7.5" color="#1848E5"  weight="normal">%a %d  %b</span></sup>%n<sub><span font_desc="ubuntu 7.5"  color="#1848E5" weight="bold">%I:%M %p</span></sub>

in the value box and hit enter 

It should immediately change.  If it doesn't there must be something else going on that I can't help with.

---

### Post by kamitsukai on 2010-10-20
someone called "ridin" hel[ed me fix the problem on the Linux Mint IRC channel basically the problem was that the info didn't go under

gconf-editor --> apps --> pannel --> applets --> clock --> prefs

where I was putting it but it goes into

gconf-editor --> apps --> pannel --> applets --> applet_2 --> prefs

the applet_2 bit being changeable

---

