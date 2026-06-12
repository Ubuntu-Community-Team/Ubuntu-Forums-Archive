---
title: "after restart, my resolution has changed and nvidia settings won't work"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by damonjablons on 2009-05-11
hey forum friends,

after restarting my computer because someone swapped a new monitor onto my computer, my resolution was downgraded to 1024x768, and i wasn't given a higher option.  i tried several things, including downgrading my nvidia driver (then reupgrading), resetting my xorg.conf, and rebooting a million times.  i'm on the brink of reformatting, but i'd rather not since it'll take a full day to get all of my settings back.

any hints on how to fix this?

if i run "nvidia-settings manager" i get this error box upon opening:
```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

when i run "nvidia-xconfig" as root via the terminal, it gives me this output:
```
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

unfortunately, it doesn't seem to fix the issue upon restart.  please help, thank you :)

---

### Post by AndThenWhat on 2009-05-11
Okay if I were you I would try resetting xorg again:

```
sudo dpkg-reconfigure xserver-xorg
```

Then I would go into a terminal and try to set the old resolution with xrandr:

[http://www.perpetualpc.net/srtd_resolution.html](http://www.perpetualpc.net/srtd_resolution.html)

---

### Post by damonjablons on 2009-05-11
i did the dpkg, and then i did the resolution change via the terminal, only to get this:

```
# xrandr -s 1600x1200
Size 1600x1200 not found in available modes
```

---

### Post by AndThenWhat on 2009-05-11
Was that resolution one of the choices that xrandr gave you?

By the way, when you reset your xorg.conf file it resets the display settings to how they were when Ubuntu was first installed. So, if you check the Display app (System -> Preferences -> Display) on Jaunty or the Screen Resolution app (System -> Preferences -> Screen Resolution) on Hardy, the default options are available.

---

### Post by Didius Falco on 2009-05-11
run just ```
xrandr
``` and it will tell you what mode are available, then you can choose from them.

Regards,

Didius

---

### Post by damonjablons on 2009-05-11
when i run "xrandr" i get this output:
```
# xrandr
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1360 x 1360
VGA1 disconnected
DVI0 disconnected
VGA2 connected 1152x864+0+0 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
   680x384       119.6    119.9  
   576x432       120.1  
   512x384       120.0  
DVI1 disconnected
```

the resolution "1600x1200" is not in the list, but it's what i originally had before this issue.  any way to get that back?

---

### Post by cap'n leaky on 2009-05-11
I'm not sure I understood your post.  Did you say you used to have the higher resolution, but you don't now with a new monitor?

Are you sure the new monitor can run at the new resolution?  Just because the video card can, doesn't mean the monitor can.

---

### Post by damonjablons on 2009-05-12
here's exactly what happend, i had my current monitor.  it's a ViewSonic VP2130b.  when it was originally connected to my computer, it had 1600x1200 resolution.  then i swapped it for an apple monitor - a 20-something inch cinema display.  but the cinema display had to be given to someone else in the office doing video editing, therefore i got my old ViewSonic monitor back.  after plugging it in, it doesn't recognise the monitor and thinks that it's a generic CRT.

so how do i get it to recognise what monitor i'm using?  it's really frustrating working with 640x320 resolution haha.

---

### Post by cap'n leaky on 2009-05-13
damonjablons,

Sorry, but I'm not sure where to go next.  My PC has had lots of problems recognizing the video properly, but I'm not sure if it's the monitor or card (GeForce FX 5200 and ProView Pro-720), but I've read alot of threads with people having problems with the same card, and other threads where monitors are not recognized.

I lose my setup sometimes if I change resolution too much, or sometimes after I watch a DVD, or some other thing.  I've had to manually tweak my xorg file, and after it happened a few times, I backed up the file so I can restore it if it blows up.

I'll try searching the forums to see what I can find.

---

