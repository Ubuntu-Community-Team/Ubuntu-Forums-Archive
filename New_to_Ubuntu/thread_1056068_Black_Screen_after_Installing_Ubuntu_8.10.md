---
title: "Black Screen after Installing Ubuntu 8.10"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by reff on 2009-01-31
[B]Hello Guys
Just installed ubuntu from USB Memory stick using safe graphics mode on Fujitsu siemns 3515 but after it finished installing i have 2 issues
MP-BIOS bug: 8254 timer not connected to IO-APIC and a black screen with a running in low graphics mode then when  try to repair all i get you have to configure it manually,i really have no idea about this i'm a total n00band my laptop is compleely useless.
TIA[/B]

---

### Post by jbrown96 on 2009-01-31
I'm not sure what the mp-bios warning is, but I can probably help with the black screen problem.

1) Have you installed any video drivers? You wouldn't have done this with the initial OS installation.

2) Can you get to a terminal? Try running the following
     a) boot Ubuntu.
     b) When you think it has finished booting, try pressing Crtl+Alt+F1  (or try F1-F4 if that doesn't work)
     c) login
     d) try to identify your hardware. Run ```
lspci | grep VGA
``` if this doesn't return anything, try ```
lspci | more
``` instead and use the space bar to scroll until you find your graphics card. Post back with that information.
     e) try to reconfigure the x server. ```
sudo dpkg-reconfigure --xserver-xorg
``` I'm pretty sure that is the command or something very similar. Then try to start x. ```
startx
```

Give this a try and see where you get.

---

### Post by reff on 2009-01-31
[B]Thanks for the reply
i haven't installed anything since i just installed ubuntu there's no terminal it's just black screen and a message says that it can't configure Graphics so there's no display at all!
been searching for a long time and couldn't find anything.[/B]

---

