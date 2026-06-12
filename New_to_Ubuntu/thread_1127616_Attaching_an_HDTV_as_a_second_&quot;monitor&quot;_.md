---
title: "Attaching an HDTV as a second &quot;monitor&quot; help"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by SumthingWicked5 on 2009-04-16
I'm trying to set up my system with a regular 19" monitor as my main X screen, and then have my 27" HDTV (SANYO VIZON) as a second screen. 

I'm running Intrepid, I've got a GeForce 8600GT vid card. I've got the cable that plugs into the back of my card (Forget what the connection is called) and converts to an HDMI jack.

First, all I did was plug it in, and obviously nothing happened. 

Then, I went into my NVidia X Server Settings and went to X Display Configurations and got it to recognize that the TV was there, but it's disabled. So I hit Configure, and activate it as a Separate X screen. When I hit apply and it comes up with a window with five bullet points as to why it can't do it, and tells me if I want to do it, I have to "save configuration changes to X Config files and restart X server"

When I hit the button that claims to do that, I get an error "Unable to create new X Config backup file"

I'm absolutely a beginner, so any help, explained in great detail, would make my whole day!

---

### Post by northern lights on 2009-04-16
Run```
gksu nvidia-settings
```

---

