---
title: "Graphics Configuration Concepts...Xorg, xrandr..."
date: 2009-04-03
forum: New to Ubuntu
---

### Post by rjcoolpix880 on 2009-04-03
I have a computer hooked up to my TV where the TV is the only monitor. That is unless i cant configure it to come on, when i am forced to add a real monitor on the side. My card is an ati 9500.

With Ubuntu 8.10, all i had to do was grab the proprietary drivers somewhere and install them. I think i remember 8.10 telling me that i needed to install them in a pop-up... after that i just had to restart, and either it automatically cloned my desktop onto the TV from the S-video or i had to go into the ati configuration that it installed and turn it on. (The GUI one)

But now i installed 9.04 and the proprietary ati drivers are not supported. Which i dont care about because i just watch TV on it. But i cant get it to clone my desktop onto my TV. I have searched Google and the forums, and have read alot of things and tried alot of things...

Now, the questions:
**xorg**: This is the graphics driver right? so in theory that is how/where i would configure the other monitor. But i have no idea how to tinker with the config using the terminal. it is just foreign to me and i dont feel like i can do anything except copy and paste things from other people. is there a gui way to do it?

**xrandr**: what is this? What is this for? i typed in something yesterday that i found here and got my TV to be a clone (somewhat) of my screen, so i know that everything works... But once i restart, i have to type in the command again to bring up the TV. Once again, since i dont really do well with the terminal in terms of trouble shooting and learning from it, i dont know what to do.

Feel free to add any conceptual words of wisdom about configuring graphics cards and monitors. that will help me really understand what the heck i am doing! :)

---

### Post by Hospadar on 2009-04-03
First off "driver" is a much abused word in the computer science world.  It is often used to describe all the software associated with something.  The plague of the windows "driver cd" has only made this misconception worse.
In linux (and most other os's for that matter) a driver in the strictest sense is a kernel module and nothing else.  The kernel is the lowest software level of the operating system.  It handles all hardware access and process switching.  a kernel module, generally used to control hardware, although it can do other things, provides a basic and uniform interface to the kernel for hardware.

Anyways,
xorg, probably more correctly referred to as X11 is the program that handles most (not OpenGL 3d stuff) of the graphical business in linux, it does all the drawing.  X11 will talk to your video driver and tell it what to put on the screen.

xrandr is a program used to change things around on the screen as you've noticed.  It does rotating, dual monitors, etc.  Xrandr has (multiple) graphical frontends, one I know of off the top of my head is grandr, which I believe you can install in synaptic.

I'm sure you can set up your /etc/X11/xorg.conf to do your cloning on bootup, but it might be easier to just run whatever xrandr command does the trick when you log in.  If you go to preferences->sessions (I think?) you can set startup programs that get run when you log in.  You could just put the xrandr command in there whenever you log in.

---

