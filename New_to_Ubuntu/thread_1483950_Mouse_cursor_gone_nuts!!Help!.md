---
title: "Mouse cursor gone nuts!!Help!"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by civillianslave on 2010-05-15
I just installed the new Ubuntu 10.04 in hope that it may resolve  this issue, which stopped me using ubuntu before. Sadly it still occurs. When i boot up the mouse cursor goes nuts, it won't click on things where i want it to, it disappears then reappears else where on the screen etc Just random behavior. Here is the weird( and irritating) bit, if i reboot after the first boot it goes back to normal.

So to sum up, on ubuntu(and mint too) i have to turn my machine on, once it boots up i then need to wrestle with the crazy behaviour of the cursor to reboot and once rebooted it goes back to normal!!

I have searched forums to no avail and asked about this when 9.10 came out and no one bothered or knew to help. I like ubuntu and want to use it, can anyone help me not have to go back to Microsoft?

P.S. - I have an Acer Aspire 5710 running the latest Ubuntu

---

### Post by civillianslave on 2010-05-15
bumping this in hope of help:confused:

---

### Post by civillianslave on 2010-05-16
anybody???:confused:

---

### Post by daimaru on 2010-05-16
sorry never heard of anything like it. have you tried using a different mouse just to see if it always happens with any mouse?

you could also try to restart the graphical desktop manager instead of rebooting. Then at least you won't have to reboot (would be a bit faster) to do that 2 ways:
Method1:
hit ctrl+alt+backspace assuming you have kill xserver enabled under Sytem->pref->keyboard --> layout tab click options on bottom left then expand the +sign where it says "Key sequence to kill the X server and tick the checkbox. 

Method2:
open terminal and type in 
```
sudo service gdm restart
```

you could also output a bit of information on your mouse hardware maybe someone can spot something there.
```
sudo hwinfo --mouse
```

---

### Post by civillianslave on 2010-05-17
thank you so much for your reply.

I have tried plugging in a mouse and the prob;em does not occur then.

The touch pad works no problem on first boot with Microsoft but not linux it seems will try what you suggested and see if it helps some what.

---

### Post by civillianslave on 2010-05-18
"sudo hwinfo --mouse"

Couldn't get this to work:(

---

### Post by daimaru on 2010-05-18
> **civillianslave said:**
> "sudo hwinfo --mouse"

Couldn't get this to work:(
you need to install hwinfo first should work then.
```
sudo apt-get install hwinfo
```

---

### Post by civillianslave on 2010-05-19
Thanks, here is the result of that -

37: ADB 00.0: 10502 Bus Mouse                                   
  [Created at input.183]
  UDI: /org/freedesktop/Hal/devices/computer_logicaldev_input_3
  Unique ID: kZYT.VdKNesd9pT6
  Hardware Class: mouse
  Model: "Macintosh mouse button emulation"
  Vendor: 0x0001 
  Device: 0x0001 "Macintosh mouse button emulation"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event4, /dev/char/13:68, /dev/char/13:32, /dev/char/13:63
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

39: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.183]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
  Unique ID: AH6Q.5+smWHVjPI3
  Hardware Class: mouse
  Model: "PS/2 Mouse"
  Vendor: 0x0002 
  Device: 0x0008 "PS/2 Mouse"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse1)
  Device Files: /dev/input/mice, /dev/input/mouse1, /dev/input/event7, /dev/char/13:71, /dev/input/by-path/platform-i8042-serio-1-event-mouse, /dev/char/13:33, /dev/input/by-path/platform-i8042-serio-1-mouse, /dev/char/13:63
  Device Number: char 13:63 (char 13:33)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

40: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.183]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input_0
  Unique ID: AH6Q.7b7iqm+3TE3
  Hardware Class: mouse
  Model: "AlpsPS/2 ALPS GlidePoint"
  Vendor: 0x0002 
  Device: 0x0008 "AlpsPS/2 ALPS GlidePoint"
  Compatible to: int 0x0210 0x0005
  Device File: /dev/input/mice (/dev/input/mouse2)
  Device Files: /dev/input/mice, /dev/input/mouse2, /dev/input/event8, /dev/char/13:72, /dev/input/by-path/platform-i8042-serio-1-event-mouse, /dev/char/13:34, /dev/input/by-path/platform-i8042-serio-1-mouse, /dev/char/13:63
  Device Number: char 13:63 (char 13:34)
  Driver Info #0:
    Buttons: 5
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
civillianslave@civillianslave-machine:~$ 
------------------------------------------------------------------------------------------------------
No idea what that means, hope it helps someone see what is wrong with my mouse pad, getting sick of having to boot then reboot every time i wanna use my laptop.

Many thanks for the help.

---

### Post by civillianslave on 2010-05-20
anyone have any idea as to what this all means?????:confused:

---

### Post by shebaw on 2010-05-20
My friend gave me his laptop to install Ubuntu for him, I had the exact problem and and his laptop was also Acer Aspire 5710, plugging a mouse would fix the problem but it's still weird.

---

### Post by civillianslave on 2010-05-20
Yeah i used a mouse for a while but it kinda removed the point of having a touch pad really, a bit of a bother if you are on the move to pull out a mouse pad etc

Surely we are not the only two who have came across this problem?

Maybe if someone can understand the info i posted on my mouse touchpad(i think that is what it is) we may have an answer.

---

### Post by civillianslave on 2010-05-20
any takers, anyone?

---

### Post by smileyacid on 2010-05-20
Not a brilliant answer but cant you turn the mousepad off in bios + use normal ps2 or usb mouse for now

---

### Post by smileyacid on 2010-05-20
This wont be a massive help but cant you just turn the pad off in bios + just use a normal ps2 or usb mouse?

---

### Post by civillianslave on 2010-05-21
I have been doing so but i use my laptop on-the-go while traveling and it is such a pain to use a mouse while doing so. With Microsoft this wouldnt be a problem, it is with Ubuntu. I love Ubuntu. Thus why i am desperately seeking a resolution to the problem.

---

### Post by civillianslave on 2010-05-22
bumping towards a solution hopefully

---

### Post by jetsam on 2010-05-22
.... Have you by chance...

...never cleaned your mouse?

---

### Post by civillianslave on 2010-05-23
it is a touch pad and i am a bit OCD when it comes to keeping my laptop clean

---

### Post by jetsam on 2010-05-23
It's on the fritz.  Cover it with a bad credit card and a wad of chewing gum and buy an external wireless  mouse with a usb key.  The lil' ones are fun.

Fixing the pad requires a re-wire.

---

### Post by videodrone on 2010-05-23
Hello.

I am another noob and had the same cursor problem yesterday with fresh install of Ubuntu Lucid Lynx 10.0 with my Intel Atom 330 with built in Nvidia graphics. Notably in XBMC. Mouse cursor skipping around the screen, with a delay of about 1 or 2 seconds response delay as i moved the mouse.

I fixed it by going to System / Administration /hardware drivers

Ubuntu then searched for available drivers over the internet, and offered me an alternative proprietary driver for the Nvidia built in graphics.

I accepted this "Nvidia accelerated graphics driver", and the cursor / mouse now works OK. Ubuntu had been using a generic driver, but now using the Nvidia driver it works fine.

regards
videodrone

---

### Post by KdotJ on 2010-05-23
I have no idea if this will help, but when I had touchpad issues I fixed it by puttin this into the terminal

```
sudo echo options psmouse proto=exps => /etc/modprobe.d/psmouse.modprobe
```

---

### Post by civillianslave on 2010-05-24
> **jetsam said:**
> It's on the fritz.  Cover it with a bad credit card and a wad of chewing gum and buy an external wireless  mouse with a usb key.  The lil' ones are fun.

Fixing the pad requires a re-wire.

It works just fine with windows and on reboot after initial boot so it cant be on the fritz.

I also tried searching for hardware drivers and it found nothing.

I then tried the Sudo code offered up but it said permission denied. Tried doing it as root and nothing happened.:confused:

---

### Post by jetsam on 2010-05-24
So you're saying that everything you've done in software has been a dismal and pointless waste of time?

---

### Post by civillianslave on 2010-05-25
pretty much yeah, i have no lost all use off the touch pad for some reason#:(

---

### Post by jetsam on 2010-05-25
I'd tear it out slowly and rebuild the box.  You need line 2.

---

### Post by civillianslave on 2010-05-25
> **jetsam said:**
> I'd tear it out slowly and rebuild the box.  You need line 2.

I don't know how to do that or what you mean by line 2.

I tried using alive disc and that let my touch pad work again but it was still all over the place:mad:

---

### Post by civillianslave on 2010-05-27
so now i have a dead touch pad.

I went to the acer website for a new driver  programme thingy for my mouse touch pad but it is in a microsoft windows file so i don't know what i am suppossed to do now#:(

---

### Post by civillianslave on 2010-05-29
Ok last time i ask for help and then i guess i have to go back to feckin Windows. No option though, i need this on the go and i don't see the point in having to lose a function of my laptop that is so convenient.(though i hate microsoft with a passion so this sticks in my craw)

---

### Post by squashpup on 2010-06-01
HP DV6911 with NVidia.

Mouse "misses" a click or two, every once in a while, then more often than not.  If I don't restart X, eventually my mouse will move the cursor, but clicking won't work.

Same with scroll wheel.  Works OK, but eventually requires a lot of turns to move slightly down the page.  

Trying the NVidia 173 driver...will post if that solves it.

---

### Post by squashpup on 2010-06-02
It is much, much better, but the problem still happens.  After a couple hours of browsing, I tried to click in a search box, and it simply wouldn't click in the box...couldn't get a cursor.  Switched to another desktop and back, and it worked fine!

This is a huge problem and needs to be worked out, or I think I'm gonna try a different system.  Simply can't have my computer screwing up regularly like this!

---

### Post by squashpup on 2010-06-03
I did two things, so I'm not really sure which did the trick.

Downgraded to the original kernel, and went with the non-default nVidia driver.  

I also noticed that I didn't to any updates (kernel or otherwise) on my Acer netbook, and it doesn't have nVidia.  No issues there...everything working just fine.  

Both the kernel and the alternate driver seem to work just fine, so this is where I'll leave this thread for now.  If you're having this problem, I'd start troubleshooting with either the kernel or the video driver.

---

### Post by squashpup on 2010-06-03
Oh, and for those who don't understand how to do this, to use the older kernel, on boot, when you get the screen that lets you choose which operating system to use, choose the one with the lowest number.  

To change the video driver, go to System> Hardware Drivers.  If there are two available, choose the other one (the one NOT in use) and follow the directions.

---

### Post by Sonny_Jim on 2011-08-12
I found a solution to this, you need to add the following to your kernel parameters:
i8042.reset i8042.nomux

Hope this helps.

---

