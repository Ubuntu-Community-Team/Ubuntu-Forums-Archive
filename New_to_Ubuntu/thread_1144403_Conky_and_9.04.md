---
title: "Conky and 9.04"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by mr-woof on 2009-04-30
Hi all,

I've got an old laptop that i use for trying out distro's etc, it's a 1.5 celeron with 512mb ram, nothing special but does the job. It's been running 8.10 for a couple of months now with conky set to start up in the sessions, working fine no problems.

I upgraded to 9.04 at the weekend, conky won't start up now. If i do alt-f2 and conky it works ok, I've re-added it in the sessions but still won't have it. :(

Anyone else having any problems?

---

### Post by abhiroopb on 2009-04-30
Might be a compiz issue. I personally don't have any problems, but if you are running compiz then I suggest you add the following into your conkrc file. these work for me...

```

    background yes
    use_xft yes
    xftfont Arial:size=10
    xftalpha 0.1
    update_interval 1.0
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 350 5
    maximum_width 400
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color gray
    default_shade_color red
    default_outline_color Green
    alignment top_right
    gap_x 12
    gap_y 12
    no_buffers no
    uppercase no
    cpu_avg_samples 2
    net_avg_samples 1
    override_utf8_locale yes
    text_buffer_size 256
    no_buffers yes

```

---

### Post by Efros on 2009-04-30
I have this little piece of code in conky_start.sh which I call from Startup Applications.

```
#!/bin/bash
sleep 45 && conky;
```

Seems compiz can cause all sorts of issues on startup if things aren't executed at the right time.

---

### Post by wizard10000 on 2009-04-30
> **Efros said:**
> I have this little piece of code in conky_start.sh which I call from Startup Applications.

```
#!/bin/bash
sleep 45 && conky;
```

Yup.

compiz has to be running before you start conky - I do the same thing but use a sleep 15 as that seems to be all I need.

---

### Post by mr-woof on 2009-05-01
Thanks guys, is this a new thing for 9.04? As i don't use compiz on this desktop as Ubuntu doesn't like my ATI card. 

But on the laptop in visual effects, I've enabled normal affects and it now working from start up

---

### Post by spikoley on 2009-05-01
> **mr-woof said:**
> Thanks guys, is this a new thing for 9.04? As i don't use compiz on this desktop as Ubuntu doesn't like my ATI card. 

But on the laptop in visual effects, I've enabled normal affects and it now working from start up

I started using Conky with Feisty and had this issue back then.

---

### Post by steve101101 on 2009-05-02
no. i have had the issue with the startup wait time in earlier disruptions as well.

---

