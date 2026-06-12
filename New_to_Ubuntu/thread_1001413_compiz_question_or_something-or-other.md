---
title: "compiz question or something-or-other"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by moose4204l on 2008-12-03
Yesterday I downloaded and installed an update from the update manager on Hardy Heron. I didn't pay attention to this update because I usually trust all that come through it. However, after the update, the next day when I was paying closer attention to my laptop I noticed that Pidgin was asking me for an SSL acceptance, nexus.passport.com ( something to do with msn and I am not sure if this is connected through the update ). Also, none of the CCSM effects are working either. They are all enabled, and I even tried to disable/enable, uninstall/install, nothing works, still get no effects. So then I started to get a laggy screen when I dragged a web browser screen. It would redraw itself downwards very slowly making it choppy like. The regular drag and drop icons would redrawn as normal on the desktop. So, I figured I would upgrade to 8.10 in hopes to fix all this. I downloaded and installed the upgrade from the update manager and I know have 8.10. This fixed the browser problem, ( probably an update on firefox conflicted, idk ) however the CCSM still doesn't work. I am not sure if this was all due to that update(s) that i did or what but any ideas on how to get CCSM to work again and if anyone had similar issues.?

Thanks

Your neighborhood question asker,
MOOSE

---

### Post by overdrank on 2008-12-03
It sounds as some updates may have effected the graphics drivers. What is the model of the graphics card?
Have you tried using the command in the terminal
```
compiz --replace
```

---

### Post by moose4204l on 2008-12-03
lshw -C display
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: Mobility Radeon HD 3400 Series
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
-------------------------------------------------

when I checked my System -> Administrator -> Hardware Drivers I have a proprietary driver called ATI.AMD propreitary FGLRX graphics driver that isn't enabled. When I enabled it, I got that choppy redraw of firefox browser and no ccsm effecs. I just deactivated it and restarted and the choppy effect is gone. In Hardy I never had that problem.

---

### Post by overdrank on 2008-12-03
> **moose4204l said:**
> lshw -C display
 *-display UNCLAIMED     
       description: VGA compatible controller
       product: Mobility Radeon HD 3400 Series
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
-------------------------------------------------

when I checked my System -> Administrator -> Hardware Drivers I have a proprietary driver called ATI.AMD propreitary FGLRX graphics driver that isn't enabled. When I enabled it, I got that choppy redraw of firefox browser and no ccsm effecs. I just deactivated it and restarted and the choppy effect is gone. In Hardy I never had that problem.

I helped a user recently with the graphics card and what worked for them is after enabling the driver, boot into recovery mode and used the xfix option. Recovery mode is usually the second choice from the grub.

---

### Post by moose4204l on 2008-12-04
well i enabled it. loaded regular first and it was choppy. then i rebooted and did the xfix and then rebooted normally. i deactivated the ATI/AMD driver and thats it. none of the compiz effects work. I wish I could test the problem on something else rather than CCSM because even though those things are cool and helpful, I oculd do without them. I just dont want this problem to effect something else too, thats why I want to fix the problem.

---

