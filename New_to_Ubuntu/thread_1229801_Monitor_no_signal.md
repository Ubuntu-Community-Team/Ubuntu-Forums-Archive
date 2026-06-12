---
title: "Monitor no signal"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by FadedReality on 2009-08-02
I have a Dell Optiplex 720L with an Intel Pentium 4 3.00Ghz with 1 gig of ram and a 152 gig hard drive. Using the integrated motherboard video card. I installed Ubuntu 9.04 through Windows as an application. When I restart the computer and select Ubuntu it loads a splash screen with a skinny loading bar. Once the loading bar is full the screen goes blue on my monitor and a message saying no signal appears. I am a complete beginner to Ubuntu so if anyone can give me an easy to understand work around for this I would be very grateful. :)

---

### Post by doas777 on 2009-08-02
I have one box that does something like that. I have to either unplug the monitors power for a minute, and then plug it back in, or remember to power the monitor off as the system is shutting down. then i don;t turn it back on until after i hear the sound for login.

I think it's that the monitor doens't quite like jaunty. I didn't have this problem with any previous distro. it'll prolly be gone in karmic (but somthing else inexplicable will occure). 

hopefully that addresses your issue. good luck.

---

### Post by Sealbhach on 2009-08-02
> **FadedReality said:**
> I have a Dell Optiplex 720L with an Intel Pentium 4 3.00Ghz with 1 gig of ram and a 152 gig hard drive. Using the integrated motherboard video card. I installed Ubuntu 9.04 through Windows as an application. When I restart the computer and select Ubuntu it loads a splash screen with a skinny loading bar. Once the loading bar is full the screen goes blue on my monitor and a message saying no signal appears. I am a complete beginner to Ubuntu so if anyone can give me an easy to understand work around for this I would be very grateful. :)

OK, try this. Once the blue screen appears hit Ctrl+Alt+F1 or Ctrl+Alt+F2 (doesn't matter which).

Login with username and password.

Type this command in:

 ```
sudo dpkg-reconfigure xserver-xorg
```

If it works you will only need to do this once. Give it a try and  let us know what happens.

.

---

### Post by FadedReality on 2009-08-02
Thanks. I will try this and hopefully everything works out. :)

---

### Post by FadedReality on 2009-08-02
Tried the first one it didn't work out.

When I used Ctrl+Alt+F1:
Loading, please wait...
[   65.97D688] EXT3-fs: write access unavailable, cannot proceed.

---

### Post by doas777 on 2009-08-02
hmmm. I think that means that there were errors mounting your root partition, and it mounted as readonly.  if that is the case, and you just installed for the first time, then reinstalling is probably your best bet.

I've never used WUBI (install as a windows app), so I'm afraid the normal advice I'd give in this case prolly work out.

good luck

---

### Post by FadedReality on 2009-08-02
I reinstalled it and it allowed me to type in my username and password but it still wouldn't let me make any changes to the file.

I tried using the live cd through a normal run and it gave me a no signal message again. I then tried safe mode and it gave me a multi-colored static image and then loaded properly into ubuntu. Everything seems to work fine in this state except the processor gets overloaded just trying to play simple flash video or the sample video in the examples folder.

Any suggestions? :(

---

### Post by Sealbhach on 2009-08-02
> **FadedReality said:**
> I reinstalled it and it allowed me to type in my username and password but it still wouldn't let me make any changes to the file.

I tried using the live cd through a normal run and it gave me a no signal message again. I then tried safe mode and it gave me a multi-colored static image and then loaded properly into ubuntu. Everything seems to work fine in this state except the processor gets overloaded just trying to play simple flash video or the sample video in the examples folder.

Any suggestions? :(

OK, so the Live CD session works? 

Regarding my message above, if you can't get a login screen on F1 or F2, try F3, F4 or F5... they're all optional screens you can use to access the system - just do Ctrl+alt+F*  until you get a login screen. Then try the reconfigure command.

.

---

