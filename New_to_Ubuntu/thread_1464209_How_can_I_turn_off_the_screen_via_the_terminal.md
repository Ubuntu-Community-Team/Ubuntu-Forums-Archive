---
title: "How can I turn off the screen via the terminal?"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by soulspit on 2010-04-27
Hi everyone,

I like to leave my laptop on overnight when downloading torrents, etc, but the brightness of the screen, obviously, can be annoying.  I can't close my laptop because it overheats.  So I was wondering if there was a way to turn off the screen very easily.  Turning on a (blank) screensaver doesn't really cut it, because even a black screen shines out quite a lot of light compared to the screen being off.

I could change my power management profiles to have the screen go blank after 1 minute of idle time, but that's not a setting I want to be on all the time, and going in to the settings to change it whenever I want to turn my screen off is a pain.

Is there any way to do this really easily, like with a command from the terminal?  I've had a look around but can't find anything.

Thanks for any help!

---

### Post by Zintha on 2010-04-28
Most laptops turn their own screens off due to a mechanical switch that activates when the lid closes.

If you have clips on the laptop that clip when you close it then try poking something in the holes they go into to see if they trigger it. Older laptops usually have that.

Newer ones however have them in the parts where it twists and its hard to get around that as much, personally I just throw a thick shirt over the screen.

---

### Post by soulspit on 2010-04-28
I actually kept looking and found something, but thanks!  Yeah, my laptop detects the lid closing by some magical and unknown mechanism.

So, I don't know if this works on all machines, but there is apparently a list of shell scripts in /etc/acpi that do things like sleep or lock the computer as well as test out media buttons.  /etc/acpi/screenblank.sh is the script that turns off the screen, so I've set that to a hotkey and I'm all good!

---

### Post by solitaire on 2010-04-28
there's usually a "fn" key to switch monitors between internal and external feeds.
I've used that on occasions to turn of a monitor screen.

It looks like "IOI" (usually "f4" key) Try using that see if that toggles the screen on and off.

---

### Post by Kellemora on 2010-04-29
When I first started using Ubuntu, there was a small program that made the upper left hand corner of your screen a sleep now hot spot.
I thought it made the screensaver pop-up, but it made the monitor actually turn off, which is what I did not want at the time as my screen saver was just a blank screen, so I uninstalled it and drat, don't remember the name of it anymore either.  That was a few years back now.

Many of my keyboards have a sleep now button, but for some reason it just crashes Ubuntu.  A drop of super glue stopped that problem, button can't be accidentally pressed now!  hi hi.....

Maybe someone remembers the name of that program?

TTUL
Gary

---

### Post by priyadarshianu on 2013-01-01
customized solution is the best we can get. n that is what linux is for :)

---

### Post by howefield on 2013-01-01
Old thread closed.

---

