---
title: "backlight problem - is it hardware or software"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by d-osprey on 2009-04-06
On powerup, my laptop screen is black, no backlight.

I connected an external monitor to the laptop, and the external monitor works.

How can I tell if the laptop screen problem is hardware or software?

---

### Post by nandemonai on 2009-04-06
> **d-osprey said:**
> On powerup, my laptop screen is black, no backlight.

I connected an external monitor to the laptop, and the external monitor works.

How can I tell if the laptop screen problem is hardware or software?

If you're not seeing anything on bootup, ie POST, memory check or maybe vendor logo etc then it's likely it is hardware.

---

### Post by d-osprey on 2009-04-06
Hi. Thanks for your help!

It is black at powerup. Partway through the bootup process, the laptop screen comes on for about three seconds. It's red, shows the mouse pointer, then returns to black.
I also read that if I entered Ctrl+Alt+f1, then Ctrl+Alt+f7 the screen might come on. It does, but again, it's very red, and only stays on for about three seconds. 
That's why I'm confused. Is that still likely to be hardware?

---

### Post by nandemonai on 2009-04-06
> **d-osprey said:**
> Hi. Thanks for your help!

It is black at powerup. Partway through the bootup process, the laptop screen comes on for about three seconds. It's red, shows the mouse pointer, then returns to black.
I also read that if I entered Ctrl+Alt+f1, then Ctrl+Alt+f7 the screen might come on. It does, but again, it's very red, and only stays on for about three seconds. 
That's why I'm confused. Is that still likely to be hardware?

Sounding very much like a hardware problem to me, especially if you're not seeing initial boot screens (before an operating system is loaded).

Could always try getting into BIOS or booting a liveCD if you have one around to see if you have any luck that way.

I'm afraid though it sounds like the LCD is on its way out.

---

### Post by d-osprey on 2009-04-06
Thanks!

I did try a bootable cd (puppy linux) and had the same result.

I'll start trying to find parts or a repair shop.

---

### Post by d-osprey on 2009-05-13
Oh no, I purchased and replaced the backlight inverter. 
The laptop screen is still black.

But if I put a bright light against the laptop screen, I can see the contents of the screen dimly (same contents as on my auxilliary monitor).

I'm going to do a clean install of the latest Ubuntu 9.04 to see if that has any impact. 

Laptop is Toshiba Tecra A8

---

### Post by lavinog on 2009-05-13
What video card does it have?
Some nvidia laptop cards (8000 series i think) had high failure rates in the past.

---

### Post by d-osprey on 2009-05-13
The video details are:
display 15.4" TruBrite TFT LCD 128x800 wxga,
Intel Graphic Media Accelerator 950, 8MB graphics memory

---

### Post by d-osprey on 2009-05-13
An external monitor connected to the laptop works ok.
I thought that meant the video card was ok. 

Could the problem still be the video card?

---

### Post by lavinog on 2009-05-13
dunno, it could be the connector on the board that connects the lcd (small ribbon cable connection)
Sometimes jarring the laptop can cause an open on one lead (such as the power to the backlight) Pressing buttons on the keyboard might nudge the connection just enough to cause your red display...can you get the same results by tapping the bottom?

Since you replaced the inverter, it sounds like you have some experience with electronics. I would check your input voltage to the inverter (not the output, you might fry your multimeter)

---

### Post by lkraemer on 2009-05-15
Here is a suggestion that might tell you more.........
except I just noticed it is a Laptop instead of a Desktop.

With monitor powered "ON" and connected to the computer,
with a BLACK display, cycle the power button "OFF" on the
monitor, wait a minute or two, then turn it back "ON".
Do you see anything?  Maybe try again only wait 5 minutes and
try it because a Thermal problem will be hard to nail down.

Next do the same thing, but unplug the video cable going to the
Computers monitor port, leaving power applied to the monitor.
Do you see anything?

I had the same type problem, and it turned out to be a Thermal
Heat problem on an older 17" MAG LCD Monitor.  I found out that
if I put a small fan at the back of the monitor blowing air through
it, it worked just fine.  Still does, but I just bought a new
Hans-G HW191D.

I would have bet it was my onboard video card, but I was wrong.
I had to Power Down the computer for 3-5 minutes then the monitor
would work for about 1 hour and go BLACK.  Still does without a fan.

Does CNTL ALT BACKSPACE bring up a new login screen?

You might try going to this website and login and search for your
Brand and model of Laptop.

[http://www.badcaps.net](http://www.badcaps.net)
[http://www.badcaps.net/forum/](http://www.badcaps.net/forum/)

Another thing you can try is to shine a very bright flashlight onto the
LCD Display and see if you can detect any images on the display.
Most likely you have some old or possibly bad CCFL's (Backlights) and maybe
a bad power supply (or bad caps, or missing voltage, or blown fuse, or bad
transistor) or defective inverter circuit, or cold solder joint.

Use Google to search for "ANP005_AP2001.pdf" and read up on the CCFL's
and start on Page 7 of 15 for a quick overview of what you will see.

REF:
[http://en.wikipedia.org/wiki/CCFL_inverter](http://en.wikipedia.org/wiki/CCFL_inverter)
[http://en.wikipedia.org/wiki/Cold_cathode](http://en.wikipedia.org/wiki/Cold_cathode)


[http://computer.howstuffworks.com/question580.htm](http://computer.howstuffworks.com/question580.htm)
[http://www.howstuffworks.com/lcd.htm](http://www.howstuffworks.com/lcd.htm)

[http://www.ccfldirect.com/lcdtutorial.html](http://www.ccfldirect.com/lcdtutorial.html)
 
lkraemer

---

### Post by d-osprey on 2009-05-25
I don't feel confident about checking input voltage on the inverter.
However, as you point out, it might be a connection. The problem occured after I had taken the laptop for a 3 hour drive in my car over some not-so-smooth gravel roads.

I wondered about connections, too, but I haven't been able to successfully unscrew the laptop so that I can get to the mainboard to check connections. This laptop seems to have a sandwiched mainboard with short cables between each. When I saw that, I decided I'd leave disassembly to someone who knows more about laptops than I do.

I'll continue to pursue the loose connection possibility, and if that doesn't make any difference, then I'll try to order & replace fluorescent backlights (with help).

I'll post again with whatever solution I find.

---

### Post by d-osprey on 2009-05-25
deleted duplicate msg

---

### Post by lavinog on 2009-05-25
What model laptop is it? Some manufacturers offer tech manuals for dissasembling your laptop.

---

