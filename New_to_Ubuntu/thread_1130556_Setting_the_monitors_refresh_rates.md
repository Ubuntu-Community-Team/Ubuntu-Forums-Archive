---
title: "Setting the monitors refresh rates?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2009-04-19
Hi -

Black text seems to be flickering on my new install of ubuntu.  I'd like to modify teh xorg.conf file, but I heard entering the wrong numbers can damage the LCD.

The spec on my monitor says:
# Horizontal: 74 KHz
# Vertical: 60 Hz

Now, I see some samples that have two numbers in their "Monitor" section:
HorizSync 28-50
VertRefresh 43-75

I don't know what the 2 numbers are about...I just need to set to 74 & 60.  Any ideas?

---

### Post by nwadams on 2009-04-19
which version of ubuntu are u using?

generally you can set the refresh rate in system->preferences-> screen resolution.

---

### Post by beetlejuice_masterson on 2009-04-19
yeah, it automatically sets it to 1900x1200 & 60Hz.  That's ok with me.  I've got a 24" gateway LCD (fpd2485w).

The weird thing is i'm getting some fuzz on vertical black lines.  Bright flickery pixels dancing up and down any black lines (but not on solid black backgrounds, like terminal).  The black border of this text box for example.

Any ideas what's going on?

---

### Post by nwadams on 2009-04-19
what version of ubuntu are u using? 
what video card do you have?
can you take a screenshot of it and post it?

---

### Post by beetlejuice_masterson on 2009-04-19
8.04 x86

video card is intel chipset p.o.s. with VGA out (i have a compaq d51s)

I don't think a screenshot will capture what's happening.  basically i'm seeing little grainy bits on lines that should be a solid color (little green pixels flickering on & off)

---

### Post by nwadams on 2009-04-19
i'm using a similar intel chip in my laptop. they aren't great. are you using compiz or other desktop effects? I'm clutching at straws here, im not sure what your problem is other than it does appear to be a video problem.

---

### Post by beetlejuice_masterson on 2009-04-19
yeah, by default it had normal effects set (this is a fresh install).  i moved it down to "None" hoping it would fix but no effect.  it's very weird.  OK - so i'm looking at the text "nwadams" and the left side of the first "n" and the top left side of the "d" have the flicker.  soooo weird.  maybe this computer is just too crummy?

---

### Post by Bölvaður on 2009-04-19
Try switching to lower resolution and(/or) lower refresh rate.
If everything is the same there is more chance that this is the driver. So restart your computer, get into grub (press esc to get into grub if it asks for it) and press E on your keyboard to change the parameters which you use to boot up with.
if I remember correctly all you need to do is type **xforcevesa** (took me long time to find this)

*added*
I wasnt finished...

then Press enter and B (for boot) this will not be saved permanently.
If this is it then you might want to look into finding another driver for your graphical card.

But if it does nothing it might be your monitor or your wires... I have no idea what else could do this... except switching to xvesa instead of your x server.. but I think it isn't wise.... good luck

---

### Post by CatKiller on 2009-04-20
"Refresh rate" is really meaningless with LCD screens.

You need to be running your monitor at its native resolution. 1920x1200 is the native resolution for that monitor, according to Google.

You might want to check the subpixel options in System -> Preferences -> Appearance.

---

### Post by beetlejuice_masterson on 2009-04-21
I see that option for FONTs -- the flicker appears on things other than font elements.  Is that where I should change the "subpixel" option?  Really it's only noticeable on thin, vertical black lines.

I put my laptop thru the LCD and didn't notice any of the flicker effects...so it's not the LCD.  I put this computer thru a smaller CRT and it displays ok so i don't think it's the graphics card.

One theory -- could it have to do with video memory?  Another weird thing:  this computer plays DVDs fine on the CRT but on the LCD all I get is a blue screen w/audio.  Very weird.  Any ideas?

---

### Post by ayastona on 2009-04-21
> **beetlejuice_masterson said:**
> 8.04 x86

video card is intel chipset p.o.s. with VGA out (i have a compaq d51s)

I don't think a screenshot will capture what's happening.  basically i'm seeing little grainy bits on lines that should be a solid color (little green pixels flickering on & off)

that sounds cool as hell!

---

