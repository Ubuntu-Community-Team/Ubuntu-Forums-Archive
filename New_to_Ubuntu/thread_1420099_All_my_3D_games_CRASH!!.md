---
title: "All my 3D games CRASH!!"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by The3irikr on 2010-03-02
All my 3D games, like Warzone 2100, Saurbraten and Glest crash. When I click on them they don't even show up. There's a tab on the bottom but then that disapears.... 
My graphics card is an Intel something...
I have a HP Pavilion dv1000
Help!

---

### Post by SecretFace on 2010-03-02
I believe that is a notebook? If so, No card in there...it's a graphic chip. Not so good for gaming. That could be your problem...but what do I know.

---

### Post by NightwishFan on 2010-03-02
Give me the output of this command, run it in a terminal and pase here surrounded by code tags.
```
sudo lshw -C display
```

Disable compiz desktop effects before you play your game does that help?

---

### Post by The3irikr on 2010-03-03
ok, i'm not sure what you mean by code tags but this is what I got.....

 *-display:0             
       description: VGA compatible controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e8000000-efffffff(prefetchable) memory:e0000000-e007ffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82852/855GM Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f7ffffff(prefetchable) memory:e0080000-e00fffff



I'm a Ubuntu noob so, yea, this is greek to me. :P

---

### Post by The3irikr on 2010-03-03
Like, I could play the games before but now they don't even start. Oh and my computer effects were already turned off when I found them and when I tried to set it to normal or high it says dekstop effects cannot be activated.

---

### Post by NightwishFan on 2010-03-03
You have an Intel card, so you do not need any extra drivers. Did disabling Desktop Effects help?

---

### Post by The3irikr on 2010-03-03
Yea, I heard that Intel doesn't work with Ubuntu... but idk. My desktop effects won't turn on! When I try it says that desktop effects can't activate or something like that.

---

### Post by NightwishFan on 2010-03-03
You heard incorrectly. Intel normally does work with Ubuntu (true they can be slow on some versions, but the drivers are open source), just many Intel cards are terrible. I will try to help you out. ;)

First off, if you are on Karmic (9.10) do the following, make sure you paste the commands exactly correct! If you have any questions before you do anything feel free to ask!

When you type this in a terminal, do you see a small box with gears?
```
glxgears
```

If not, then copy paste this command into a terminal:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Reboot, and see if you can use the gears or desktop effects. If not then run this command:
```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

We shall see what happens.

---

### Post by LowSky on 2010-03-03
run the games start command from a terminal, it will tell you what errors it is having.

---

### Post by The3irikr on 2010-03-03
ok, so even with those commands that'll fix the gear thing and a reboot... still errors.... i get

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16


and how do i run a game from terminal? I've never done that.. :P

---

### Post by NightwishFan on 2010-03-03
Generally just type the name of the game. You can hit tab to autocomplete the name if you half type it. If you give me a specific game I will hunt the command (if it is not just the name).

I will do some research on your chip and get back to you. (I was busy earlier)

---

### Post by NightwishFan on 2010-03-03
Sorry for double post.

NOTE: I am assuming you are running Ubuntu 9.10 Karmic with this how-to. If not tell me what version.

Try this command on for size:
```
sudo aptitude reinstall xserver-xorg-video-intel
```

Reboot. Then try gears, games or desktop effects.

If that does not work try:
```
sudo dpkg-reconfigure xserver-xorg-video-intel
```

Reboot, and same deal. If that does not work, I am stumped for now, but it does not seem hopeless.

---

### Post by Weepleman on 2010-03-03
I had the same problem.  What happened was that I had nVidia drivers installed for soem reason, so all I had to run was ```
sudo apt-get autoremove
```  and that fixed every thing.  When you have icons for things, is there black squares around them?

---

### Post by The3irikr on 2010-03-04
i'm trying it, no, my icons look fine.

---

### Post by The3irikr on 2010-03-04
YES!!! ok so after I cleaned up the useless stuff with the autoremove command, I rebooted and tried opening a game up in terminal and it works!!! And it works when I open up games via icon. :D
the only thing now is that when I close Warzone 2100 the last ad freezes and i have to reboot but I'll fix that l8r.
THX SO MUCH FOR U GUYS HELP!!!!

---

### Post by NightwishFan on 2010-03-04
Glad you got it working, nice solution Weepleman.

---

### Post by Weepleman on 2010-03-05
Yeah, I have no idea how nVidia drivers get on there though.

---

