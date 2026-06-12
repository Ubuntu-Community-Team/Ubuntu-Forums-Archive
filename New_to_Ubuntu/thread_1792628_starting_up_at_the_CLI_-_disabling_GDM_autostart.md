---
title: "starting up at the CLI - disabling GDM autostart"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by kalimojo on 2011-06-28
i read you can start in the CLI and then start windows by typing startx. i read you had to alter a system upstart file. not sure which one or how to do it.

---

### Post by CaptainMark on 2011-06-28
i asked the same thing a few weeks ago [see here]("http://ubuntuforums.org/showthread.php?t=1780118")

---

### Post by FormatSeize on 2011-06-28
You are talking about starting in a different run level. GDM starts automatically due to the default run level dictated by your /etc/inittab file. If you open that file, depending on what version you are running, you will see a line that looks something like
```

id:[X]:initdefault:
```
The "X" in the brackets above will be a number, which is your default run level (the number won't be in brackets in the file). Being that this is your default run level, GDM is started automatically. If you don't want GDM started automatically, you have to change that number to 1, as GDM doesn't start automatically in run level 1. Change the number, reboot, and you should start without a desktop environment. 
```
startx
``` will get you into a desktop environment.

---

### Post by CaptainMark on 2011-06-28
the link i posted worked for me but i have a similar thought, is there a way to have gdm boot up as normal but display tty1 as default instead of tty7??

---

### Post by jerrrys on 2011-06-28
/etc/init/gdm.conf

i think if you move or rename this file it will kill gdm.

---

### Post by b@sh_n3rd on 2011-06-28
> **CaptainMark said:**
> the link i posted worked for me but i have a similar thought, is there a way to have gdm boot up as normal but display tty1 as default instead of tty7??

what exactly do you mean by this? If you meant, GDM to run in tty1, then that's a 'nahuh' coz tty1-6 is dedicated for login shells and 7-12 for xorg. And yes, that means you can have more than one X session running simultaneously--but that's another story :P

---

### Post by CaptainMark on 2011-06-28
no i mean just to display tty1 instead of tty7 as default when system starts, i googled a bit im skeptical to try what i dont know how to reverse but this may be it```
chcons -a login=enable /dev/tty1
```

---

### Post by FormatSeize on 2011-06-28
> **CaptainMark said:**
> the link i posted worked for me but i have a similar thought, is there a way to have gdm boot up as normal but display tty1 as default instead of tty7??
I am sure that there is a way. How to go about doing it, though, is beyond the scope of what I know about the initialization/boot process, though. I did some searching around, and I only found things relating to this about Fedora and Gentoo, and it also involved doing things that seemed like they can break other things, so I wouldn't feel comfortable linking to those things.
 
Out of curiosity, why do you ask?
> **b@sh_n3rd said:**
>  And yes, that means you can have more than one X session running simultaneously--but that's another story :P
I've known this, but I can't figure out how to do it. How?

---

### Post by b@sh_n3rd on 2011-06-28
Right, now I understand. Ubuntu has a strange way to do this...I did it a couple of years ago using a curses (cli) app but now I really can't remember how I did it. Sorry about that...I'll try to dig it up, and if I do, I'll report right back :)

PS: I'm on ARCH ;) full time CLI! :P So if you need stuff like, "apps used in CLI", you can always ask ;) examples are: web-browsers, im clients (not only irc), movie player's (in full quality :P) and so on...

---

### Post by b@sh_n3rd on 2011-06-28
> **FormatSeize said:**
> I've known this, but I can't figure out how to do it. How?

lol, I was waiting for someone to ask :P Well, supposing you use the ~/.xinitrc script to launch your GUI (which is the standard way), you'd issue, startx in the command line to load that WM/UI. I wouldn't advice launching say, gnome twice for instance but you can do something like, GNOME, OpenBox, Awesome, in tty7, 8 and 9 simultaneously.

To do that, I'd edit the ~/.xinitrc each time by uncommenting the relevant command for each UI. Like, "exec openbox-session" for OB or "exec awesome" for awesome (using now ;)). You follow me? If you do, here's the interesting part:

There are two ways to select the screen. With the command "xinit" or with "startx", which is simpler and what I use, but there's not much difference between the two if I remember correctly. Anyway, startx would be like;

```
$ startx -- :01
```note the double dashes and the "01" after the colon. The integer determines the screen number. If you just pass, "startx" you'd get screen one--or tty7--and if an X session already runs there, it'll stop. So, ":01" is tty8, ":02" tty9, etc. Hope that helps :)

**EDIT: You shouldn't have multiple (uncommented) "exec" lines in the ~/.xinitrc, it'll just break.** I'm not really sure how you get the ~/.xinitrc in ubuntu, but it should be there, it's a standard.

**EDIT #1:** If you need a template ~/.xinitrc, it might be in something like, /etc/skel...(hidden of course, so, ls -a)

**EDIT #2: **[https://help.ubuntu.com/community/CustomXSession](https://help.ubuntu.com/community/CustomXSession) <= That says it all ;) :P

---

### Post by JKyleOKC on 2011-06-28
> **FormatSeize said:**
> You are talking about starting in a different run level. GDM starts automatically due to the default run level dictated by your /etc/inittab file.This was true of older Red Hat derived systems, but for several years now (ever since introducing upstart to replace SysV initialization) Ubuntu has not had an /etc/inittab file by default. Even when it did, runlevels 2 through 5 were all identical.

Adding the "text" modifier to the GRUB options is the simplest way to get what the OP is looking for. The other thread linked in post #2 above also notes that with Unity, introduced in 11.04, simple "startx" no longer works...

---

### Post by CaptainMark on 2011-06-28
> **FormatSeize said:**
> IOut of curiosity, why do you ask?
Just that, curiosity, im like an ever evolving ubuntu sponge

---

### Post by JKyleOKC on 2011-06-28
> **CaptainMark said:**
> the link i posted worked for me but i have a similar thought, is there a way to have gdm boot up as normal but display tty1 as default instead of tty7??I don't think it's possible without rewriting GDM at least. The system will start up in tty1 by default, and launch GDM from there. When GDM launches the graphic screen, it will assign the first unused tty number to it.

You can make it use tty6 instead of tty7 by reconfiguring the system to have only 5 virtual consoles instead of the normal 6. You could even make it use tty2, I suspect, by giving the system just one VT as tty1. However this would eliminate a safety valve that's nice to have when the wheels fall off, as happens from time to time.

One of my systems, for reasons I've not yet discovered, uses TTY8 for the GUI rather than TTY7. Caused me all sorts of confusion until I discovered the situation; I was having to reboot to get the GUI back after going to TTY2! An old Mandrake system that I ran for years put copies of the dmesg output and syslog on TTY8 and TTY9 (as I recall) to make it easy to monitor them without disrupting operations on the main window. The entire VT system is a bit of a mystery to most of us...

---

### Post by CaptainMark on 2011-06-28
I don't mean to load gdm on tty1, I mean just to drop to terminal login on tty1 by default and to switch to tty7 when the GUI is needed

---

### Post by JKyleOKC on 2011-06-28
In that case, setting the GRUB options to "text" should do the trick. However using "startx" will only work with Gnome WMs, not with Unity as of the current release.

With my old Mandrake 8.1 system, I wrote a small script that would let me launch any of half a dozen window managers. I used it to try them all out and finally settle on my favorite, which for that system with only 80 MiB of RAM, was an early version of the Ice WM coupled with RoxFiler. It didn't use startx itself for any of them; instead, each option used essentially the code within startx, optimized with arguments specific to each WM. I'm sure the same could be done for Ubuntu and upstart if one wanted to spend the effort...

EDIT: On that system, I did change inittab to start in runlevel 3 rather than runlevel 5, and did almost exactly what you're asking for. Using the "text" option for GRUB prevents GDM from loading, just as changing the runlevel did for Red Hat-based systems. Debian and its derivatives, on the other hand, have never distinguished between runlevels 2 through 5, and default to 2.

---

### Post by kalimojo on 2011-06-28
> **FormatSeize said:**
> You are talking about starting in a different run level. GDM starts automatically due to the default run level dictated by your /etc/inittab file. If you open that file, depending on what version you are running, you will see a line that looks something like
```

id:[X]:initdefault:
```The "X" in the brackets above will be a number, which is your default run level (the number won't be in brackets in the file). Being that this is your default run level, GDM is started automatically. If you don't want GDM started automatically, you have to change that number to 1, as GDM doesn't start automatically in run level 1. Change the number, reboot, and you should start without a desktop environment. 
```
startx
``` will get you into a desktop environment.

i dont have an /etc/inittab file. i am running 11.04. 

edit : just read the other post about 11.04 not having an /etc/inittab file

---

### Post by sisco311 on 2011-06-28
In 11.04 you have to create a .override file. See: [http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

---

