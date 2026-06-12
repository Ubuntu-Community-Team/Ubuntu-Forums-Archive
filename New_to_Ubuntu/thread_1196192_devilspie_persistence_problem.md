---
title: "devilspie persistence problem"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by Spaceman.Spiff on 2009-06-24
I'm running Ubuntu 9.04 with an NVIDIA GeForce 9800 GTX graphics card (latest drivers, 180) with two screens (i.e. monitors; second screen configured as a separate X screen, with Xinerama enabled, in X Server). On startup, I would like to load two separate browser windows--one in each screen, and each in fullscreen. To accomplish this I'm using "Startup Applications" to launch firefox with the chosen URIs (and it works without any problems) and devilspie to identify these browser windows and place them fullscreen on the appropriate screen (which I'm having a problem with).

When Ubuntu starts devilspie doesn't load my .ds files. I've added devilspie to Startup Applications list and can see it runnings as a process in the system monitor, but it doesn't seem to do anything.

However, if I open up the terminal (I'm actually using Konsole) and type "devilspie" then my .ds files are read and the two browser windows move to the separate screens (each fullscreen) just as I want them. Then, on my primary screen (the one with the panels) I can use the browser just fine and it behaves as I would expect it. However, if I at any time click on the browser on the second screen it immediately moves to the primary screen, covering the other browser. It then remains there, and can be used in that monitor, without any problems.

So the problems I'm trying to solve are 1) getting the devilspie .ds files to be read (executed) on boot and 2) to keep the second browser in the second screen (i.e. to keep it from jumping to the primary screen when it receives focus).

I've tried adding "devilspie ~/.devilspie/*.ds &" to both ~/.xinitrc and /etc/X11/xinit/xinitrc, but it doesn't seem to work.

Any help would be greatly appreciated. The contents of my .ds files are

Fullscreen1.ds:

; Open up firefox in the top display
(if
    (and 
        (is (application_name) "Firefox")
        (is (window_name) "Gmail: Email from Google - Mozilla Firefox")
    )
    (begin
        (above)
        (undecorate)
        (geometry "1360x768+0+0")
    )
)

and Fullscreen2.ds:

; Open up firefox in the bottom display
(if
    (and 
        (is (application_name) "Firefox")
        (is (window_name) "Google - Mozilla Firefox")
    )
    (begin
        (above)
        (undecorate)
        (geometry "1024x768+0+768")
    )
)


*Note: For other reasons I had to change the X Server configuration to TwinView. Doing this fixed the problem of the second browser monitor jumping into the first screen when it received focus. So, now my only problem is making sure that devilspie is persistent and that it will run my .ds files on boot.*

---

